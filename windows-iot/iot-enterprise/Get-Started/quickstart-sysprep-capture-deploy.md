---
title: "Quickstart: Sysprep and capture the reference device image and deploy to a new device"
description: "Sysprep and capture the reference device image of Windows IoT Enterprise to a WIM using DISM. Then deploy the WIM image to a new device"
author: asergaz
ms.author: sergaz
ms.service: windows-iot
ms.subservice: iot
ms.topic: quickstart
ms.date: 09/27/2024

#customer intent: As a beginner, I want to learn the basics on how to sysprep, capture and deploy Windows IoT Enterprise.

---

# Quickstart: Sysprep and capture the reference device image, and deploy to a new device

In this quickstart, you sysprep and capture the reference device image of Windows IoT Enterprise to a Windows Imaging Format (WIM) file using the Deployment Image Servicing and Management (DISM) tool. Then, you deploy the WIM image to a new device.

## Prerequisites

- Complete [Quickstart: Prepare your lab environment](quickstart-pepare-lab-environment.md) before you begin this quickstart.

## Sysprep the reference device sample

After you make your customizations in audit mode, you can capture an image of your customized reference device. While audit mode isn't required, it does provide a scenario where the device can be customized online before going into the Out of Box experience (OOBE).

This section provides steps to sysprep the reference device and apply to both physical device and virtual machine:

1. Select **Cancel** on the System Preparation Tool to close it, then run Sysprep from a Command Prompt with Administrator privileges to prepare the image for capture:

    > [!NOTE]
    > If you completed [Quickstart: Customize a reference device in Audit mode](quickstart-customize-reference-device.md) and configured *powershell.exe* as your custom shell, run the following command to open Command Prompt with Administrator privileges: `Start-Process cmd -Verb RunAs`

    ```cmd
    C:\Windows\System32\Sysprep\sysprep.exe /generalize /oobe /shutdown
    ```

    :::image type="content" source="../Get-Started/media/quickstart-sysprep-capture-deploy/sysprep-powershell-shell.png" alt-text="Screenshot that shows the sysprep command with Powershell as the default system shell":::

After Sysprep prepares the image, the reference device will shut down. The next time the device boots, it will boot into OOBE.

> [!CAUTION]
> Don't power the reference device back on until you're ready to capture an image. If the device boots, you'll have to go through the Sysprep process again.

## Create a bootable WinPE drive

Windows PE (WinPE) is a small operating system used to install, deploy, and repair Windows desktop editions, Windows Server, and other Windows operating systems. It's an add-on to the Windows Assessment and Deployment Kit (ADK) that you previously installed in your technician PC.

In your **technician PC**, follow the steps to create a bootable WinPE drive:

### [Physical Device](#tab/physicaldevice)

In this section, you create a bootable WinPE USB drive with multiple partitions. Having multiple partitions allows you to have a FAT32 partition for WinPE and an NTFS partition for the captured WIM file. You can use this USB drive for both capturing and deploying your image.

> [!TIP]
> You can use the same USB drive where you created the bootable Windows IoT Enterprise installation media in the previous quickstart.

1. Insert the USB drive into the Technician PC.

1. Open the **Deployment and Imaging Tools Environment** as administrator. You can find a shortcut to the Deployment and Imaging Tools under Windows Kits in the Start Menu.

1. Run Diskpart:

    ```cmd
    diskpart
    ```

1. Use Diskpart to format the drive and create two new partitions for WinPE and for your images:

    ```cmd
    List disk
    select disk X    (where X is your USB drive)
    clean
    create partition primary size=2048
    active
    format fs=FAT32 quick label="WINPE"
    assign letter=P
    create partition primary
    format fs=NTFS quick label="Images"
    assign letter=I  
    Exit
    ```

1. Copy the WinPE files to a working folder:

    ```cmd
    copype amd64 C:\WinPE 
    ```

    This command copies the 64-bit WinPE files to C:\WinPE. The destination folder is created automatically.

1. Copy the WinPE files to your USB key.

    ```cmd
    makewinpemedia /ufd C:\WinPE P:
    ```

    Where *P:* is the USB drive with the WinPE Partition. This command formats the partition and erases any data that's on it.

1. Move the USB flash drive from the technician PC to the reference device.

### [Virtual Machine](#tab/virtualmachine)

In this section, you create a bootable WinPE virtual hard disk drive (VHD) and a second VHD to store the captured WIM file. You use WinPE for both capturing and deploying your image.

1. Open Hyper-V Manager.
1. Right-click on the Virtual Machine and select **Settings**.
1. In the left pane, select **SCSI Controller**.
1. In the right pane, select **Hard Drive** and then **Add**.
1. Select **New** to create a VHD.
1. Follow the wizard to create a new VHD, for WinPE you can define a size of *4 GB*.
1. Repeat the steps to create another VHD to store the WIM file. You can define the size as *8 GB*.
1. At the end, select **Apply** and **OK** to create the VHDs.

Mount the VHDs on your **technician PC**

1. Press <kbd>Windows</kbd> + <kbd>R</kbd>, type *diskmgmt.msc*, and press **Enter**.
1. In Disk Management, select **Action** in the menu bar.
1. Select **Attach VHD**.
1. In the dialog that appears, select *Browse*, and navigate to the location of your VHD file.
1. Select the VHD file and select **OK**.
1. The VHD shows as a new disk in Disk Management.
1. Initialize the VHD by right-clicking on the disk and selecting **Initialize Disk**.
1. Create a volume by right-clicking on the unallocated space and selecting **New Simple Volume...**.
1. Follow the wizard to create a new volume, letting *FAT32* as the file system for WinPE.
1. Repeat the steps for the VHD where you will store the WIM file, letting *NTFS* as the file system.
1. You can now access the VHD from File Explorer as if it were a regular drive.

Add WinPE files to the VHD:

1. Open the **Deployment and Imaging Tools Environment** as administrator. You can find a shortcut to the Deployment and Imaging Tools under Windows Kits in the Start Menu.

1. Copy the WinPE files to a working folder:

    ```cmd
    copype amd64 C:\WinPE 
    ```

    This command copies the 64-bit WinPE files to C:\WinPE. The destination folder is created automatically.

1. Copy the WinPE media files to the VHD

    ```cmd
    xcopy "C:\WinPE\media\*" "P:\" /E /H 
    ```

    Where *P:* is the WinPE VHD.

Unmount the VHDs from your **technician PC**:

1. Press <kbd>Windows</kbd> + <kbd>R</kbd>, type *diskmgmt.msc*, and press **Enter**.
1. Detach the VHDs by right-clicking on the disk and selecting **Detach VHD**.

---

## Boot the reference device to WinPE and capture the Windows IoT Enterprise OS image

In this section, you capture a WIM image from the reference device's hard drive. This WIM can be used in development or in production. It's common to capture OS images during different stages of the development process. For example, the following steps could be used to capture a base image of the OS with default apps installed. A later image could be captured with more end customer apps installed.

In your **reference device sample**, follow the steps to capture a WIM image:

### [Physical Device](#tab/physicaldevice)

1. Boot the reference device from the bootable WinPE USB flash drive.

    > [!IMPORTANT]
    > Don't boot your device until you know which key brings up the device's boot menu. The device is in a Sysprepped state and should not be allowed to boot back into Windows IoT Enterprise.

    The system boots to the WinPE, where you see a Command prompt.

    :::image type="content" source="../Get-Started/media/quickstart-sysprep-capture-deploy/winpe-command-prompt.png" alt-text="Screenshot that shows the WinPE command prompt":::

    > [!TIP]
    > If you have a different keyboard layout, you can change the keyboard layout by running `wpeutil setKeyboardLayout 0816:00000816` where the *language:keyboard* pair list for your desired layout can be found in [input locales](/windows-hardware/manufacture/desktop/default-input-locales-for-windows-language-packs). Then run `winpeshl.exe` from the WinPE Command Prompt to ensure the new layout is applied to the current session.

1. From the WinPE Command prompt, run Diskpart:

   ```cmd
   diskpart
   ```

1. Use Diskpart to list the disks so you can identify the disk where Windows IoT Enterprise is installed:

   ```cmd
   list disk
   ```

   You should see something like:

   ```output
   Disk ###  Status          Size     Free     Dyn  Gpt
   --------  -------------   -------  -------  ---  ---
   Disk 0    Online            63 GB      0 B        *
   Disk 1    Online            14 GB      0 B
   ```

   In this example, *Disk 0* size represents the disk where we installed Windows IoT Enterprise.

1. Select Disk 0 and then list the partitions and volumes:

    ```cmd
    select Disk 0
    list partition
    list volume
    ```

   You should see something like:

    ```output
    DISKPART> select disk 0

    Disk 0 is now the selected disk.

    DISKPART> list partition

        Partition ###  Type              Size     Offset
        -------------  ----------------  -------  -------
        Partition 1    System             100 MB  1024 KB
        Partition 2    Reserved            16 MB   101 MB
        Partition 3    Primary             63 GB   117 MB
        Partition 4    Recovery           602 MB    63 GB
    
    DISKPART> list volume

        Volume ###  Ltr  Label        Fs     Type        Size     Status     Info
        ----------  ---  -----------  -----  ----------  -------  ---------  --------
        Volume 0     E                UDF    DVD-ROM     4236 MB  Healthy    
        Volume 1                      NTFS   Partition     63 GB  Healthy    
        Volume 2                      FAT32  Partition    100 MB  Healthy    Hidden
        Volume 3                      NTFS   Partition    602 MB  Healthy    Hidden
        Volume 4     C   WINPE        FAT32  Partition   2048 MB  Healthy
        Volume 5     D   Images       NTFS   Partition     14 GB  Healthy           
    ```

    In this example, *Partition 3* is of *Type Primary* and is where Windows IoT Enterprise is installed. Letters *C*, *D*, and *E* are assigned to the *WinPE*, *Images*, and *DVD-ROM* volumes respectively.

1. Select Partition 3 and assign a drive letter that isn't already in use:

    ```cmd
    select partition 3
    assign letter=W
    ```

    If you list volume again, you should see the Windows IoT Enterprise partition now has a drive letter assigned:

    ```output
    Volume ###  Ltr  Label        Fs     Type        Size     Status     Info
    ----------  ---  -----------  -----  ----------  -------  ---------  --------
    Volume 0     E                UDF    DVD-ROM     4236 MB  Healthy    
    Volume 1     W                NTFS   Partition     63 GB  Healthy    
    Volume 2                      FAT32  Partition    100 MB  Healthy    Hidden
    Volume 3                      NTFS   Partition    602 MB  Healthy    Hidden
    Volume 4     C   WINPE        FAT32  Partition   2048 MB  Healthy
    Volume 5     D   Images       NTFS   Partition     14 GB  Healthy       
    ```

1. Exit Diskpart:

    ```cmd
    exit
    ```

1. From the WinPE Command prompt, use DISM to capture an image of the Windows partition:

    ```cmd
    Dism /capture-image /imagefile:D:\WindowsIoTEnterprise.wim /CaptureDir:W:\ /Name:"Windows IoT Enterprise"
    ```

    DISM captures an image of the OS partition and store it on D: drive.

    :::image type="content" source="../Get-Started/media/quickstart-sysprep-capture-deploy/winpe-dism-capture-image.png" alt-text="Screenshot that shows the success capture of the image using dism":::

    > [!NOTE]
    > Your device will have more than one partition, but you only need to capture the Windows partition.

1. Shutdown the virtual machine:

    ```cmd
    wpeutil shutdown
    ```

### [Virtual Machine](#tab/virtualmachine)

Select WinPE VHD as the first in boot order:

1. Open Hyper-V Manager
1. Right-click on the Virtual Machine and select **Settings**.
1. In the left pane, select **Firmware**.
1. In the right pane, move WinPE VHD to the top.
1. At the end, select **Apply** and **OK**
1. Start the Virtual machine

The system boots to the WinPE, where you see a Command prompt.

:::image type="content" source="../Get-Started/media/quickstart-sysprep-capture-deploy/winpe-command-prompt.png" alt-text="Screenshot that shows the WinPE command prompt":::

> [!TIP]
> If you have a different keyboard layout, you can change the keyboard layout by running `wpeutil setKeyboardLayout 0816:00000816` where the *language:keyboard* pair list for your desired layout can be found in [input locales](/windows-hardware/manufacture/desktop/default-input-locales-for-windows-language-packs). Then run `winpeshl.exe` from the WinPE Command Prompt to ensure the new layout is applied to the current session.

1. From the WinPE Command prompt, run Diskpart:

   ```cmd
   diskpart
   ```

1. Use Diskpart to list the disks so you can identify the disk where Windows IoT Enterprise is installed:

   ```cmd
   list disk
   ```

   You should see something like:

   ```output
   Disk ###  Status          Size     Free     Dyn  Gpt
   --------  -------------   -------  -------  ---  ---
   Disk 0    Online            64 GB      0 B        *
   Disk 1    Online            16 GB      0 B
   Disk 2    Online          4096 MB      0 B
   ```

   In this example, *Disk 0* size represents the disk where we installed Windows IoT Enterprise.

1. Select Disk 0 and then list the partitions and volumes:

    ```cmd
    select Disk 0
    list partition
    list volume
    ```

   You should see something like:

    ```output
    DISKPART> select disk 0

    Disk 0 is now the selected disk.

    DISKPART> list partition

        Partition ###  Type              Size     Offset
        -------------  ----------------  -------  -------
        Partition 1    System             100 MB  1024 KB
        Partition 2    Reserved            16 MB   101 MB
        Partition 3    Primary             63 GB   117 MB
        Partition 4    Recovery           602 MB    63 GB
    
    DISKPART> list volume

        Volume ###  Ltr  Label        Fs     Type        Size     Status     Info
        ----------  ---  -----------  -----  ----------  -------  ---------  --------
        Volume 0     E                UDF    DVD-ROM     4236 MB  Healthy    
        Volume 1                      NTFS   Partition     63 GB  Healthy    
        Volume 2                      FAT32  Partition    100 MB  Healthy    Hidden
        Volume 3                      NTFS   Partition    602 MB  Healthy    Hidden
        Volume 4     C   WINPE        FAT32  Partition   4078 MB  Healthy
        Volume 5     D   Images       NTFS   Partition     16 GB  Healthy           
    ```

    In this example, *Partition 3* is of *Type Primary* and is where Windows IoT Enterprise is installed. Letters *C*, *D*, and *E* are assigned to the *WinPE*, *Images*, and *DVD-ROM* volumes respectively.

1. Select Partition 3 and assign a drive letter that isn't already in use:

    ```cmd
    select partition 3
    assign letter=W
    ```

    If you list volume again, you should see the Windows IoT Enterprise partition now has a drive letter assigned:

    ```output
    Volume ###  Ltr  Label        Fs     Type        Size     Status     Info
    ----------  ---  -----------  -----  ----------  -------  ---------  --------
    Volume 0     E                UDF    DVD-ROM     4236 MB  Healthy    
    Volume 1     W                NTFS   Partition     63 GB  Healthy    
    Volume 2                      FAT32  Partition    100 MB  Healthy    Hidden
    Volume 3                      NTFS   Partition    602 MB  Healthy    Hidden
    Volume 4     C   WINPE        FAT32  Partition   4078 MB  Healthy
    Volume 5     D   Images       NTFS   Partition     16 GB  Healthy       
    ```

1. Exit Diskpart:

    ```cmd
    exit
    ```

1. From the WinPE Command prompt, use DISM to capture an image of the Windows partition:

    ```cmd
    Dism /capture-image /imagefile:D:\WindowsIoTEnterprise.wim /CaptureDir:W:\ /Name:"Windows IoT Enterprise"
    ```

    DISM captures an image of the OS partition and store it on D: drive.

    :::image type="content" source="../Get-Started/media/quickstart-sysprep-capture-deploy/winpe-dism-capture-image.png" alt-text="Screenshot that shows the success capture of the image using dism":::

    > [!NOTE]
    > Your device will have more than one partition, but you only need to capture the Windows partition.

1. Shutdown the virtual machine:

    ```cmd
    wpeutil shutdown
    ```

---

## Deploy the captured WIM image from WinPE

In this section, you deploy a WIM image from WinPE. The reference device sample that you create in these quickstarts is already in a deployed state since it was captured in a Sysprepped state and, when deployed, boots into OOBE. This section provides steps to deploy the captured WIM image to a new device, though you can also use this process to deploy the image to the same device you captured it from.

### [Physical Device](#tab/physicaldevice)

In your **new device**, follow the steps to deploy the WIM image:

1. Boot the device from the bootable WinPE USB flash drive.

1. From the WinPE Command prompt, run Diskpart:

   ```cmd
   diskpart
   ```

1. List and then select the disks of your device:

   ```cmd
   list disk
   select disk X    (where X is the disk of your device)
   ```

1. Format the device::

    ```cmd
    clean 
    convert gpt 
    create partition efi size=100 
    format quick fs=fat32 label="System" 
    assign letter="S" 
    create partition msr size=16 
    create partition primary 
    format quick fs=ntfs label="Windows" 
    assign letter="W" 
    ```

    > [!NOTE]
    > The above Diskpart commands don't create a recovery partition. If you need to configure a recovery partition, see [Configure UEFI/GPT-based hard drive partitions](/windows-hardware/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions).

1. Use Diskpart to identify the volume where the WIM file is stored:

    ```cmd
    list volume
    ```

    You should see something like:

    ```output
    Volume ###  Ltr  Label        Fs     Type        Size     Status     Info
    ----------  ---  -----------  -----  ----------  -------  ---------  -------- 
    Volume 0     W   Windows      NTFS   Partition     63 GB  Healthy    
    Volume 1     S   System       FAT32  Partition    100 MB  Healthy    Hidden
    Volume 2     C   WINPE        FAT32  Partition   4078 MB  Healthy
    Volume 3     D   Images       NTFS   Partition     16 GB  Healthy       
    ```

    In this example, *Volume 3* with the letter *D* is where the WIM file is stored.

1. Exit Diskpart:

    ```cmd
    exit
    ```

1. From the WinPE command prompt, deploy the WIM image to the W: drive created in the previous step:

    ```cmd
    Dism /Apply-Image /ImageFile:D:\WindowsIoTEnterprise.wim /ApplyDir:W:\ /Index:1
    ```

    :::image type="content" source="../Get-Started/media/quickstart-sysprep-capture-deploy/winpe-dism-apply-image.png" alt-text="Screenshot that shows the success apply of the image using dism":::

1. From the WinPE Command Prompt, configure the default BCD on the system, which is a required step as the disk was freshly partitioned and formatted:

    ```cmd
    W:\Windows\System32\bcdboot W:\Windows /s S:
    ```

1. Remove the USB drive and reboot the system at the WinPE Command Prompt.

    ```cmd
    wpeutil reboot
    ```

The device reboots into OOBE with the Windows IoT Enterprise image you previously customized and captured.

### [Virtual Machine](#tab/virtualmachine)

Create the **new** Virtual Machine:

1. Open Hyper-V Manager.
1. In the Hyper-V Manager, select **New** in the **Actions pane**, then select **Virtual Machine**.
1. Follow the wizard to create a new virtual machine.
1. When prompted to specify the generation, choose **Generation 1** or **Generation 2** based on your requirements.
1. Assign a minimum of *2 GB* of memory to the virtual machine.
1. Leave the virtual machine with no connection to the network.
1. When you reach the **Connect Virtual Hard Disk** step, select **Create a virtual hard disk**.
1. Specify the name, location, and size of the Virtual Hard Disk (VHD). For example, set the size to *64 GB*.
1. When you reach the **Installation Options** step, select **Install an operating system later**.
1. Review the settings in the **Summary** step and select **Finish** to create the virtual machine.

Configure the Number of Processors:

1. After the virtual machine is created, right-click on it in the Hyper-V Manager and select **Settings**.
1. In the left pane, select **Processor**.
1. In the right pane, specify a minimum of *two virtual processors*.

Select WinPE VHD as the first in boot order:

1. Right-click on the Virtual Machine and select **Settings**.
1. In the left pane, select **SCSI Controller**.
1. Add a **Hard Drive** and browse the *VHD where you stored the WIM file*.
1. Add another **Hard Drive** and browse the *WinPE VHD*.
1. Select **Apply**.
1. In the left pane, select **Firmware**.
1. In the right pane, move WinPE VHD to the top.
1. At the end, select **Apply** and **OK**
1. Start the Virtual machine

The system boots to the WinPE, where you see a Command prompt.

1. From the WinPE Command prompt, run Diskpart:

   ```cmd
   diskpart
   ```

1. List and then select the disks of your device:

   ```cmd
   list disk
   select disk X    (where X is the disk of your device)
   ```

1. Format the device::

    ```cmd
    clean 
    convert gpt 
    create partition efi size=100 
    format quick fs=fat32 label="System" 
    assign letter="S" 
    create partition msr size=16 
    create partition primary 
    format quick fs=ntfs label="Windows" 
    assign letter="W" 
    ```

    > [!NOTE]
    > The above Diskpart commands don't create a recovery partition. If you need to configure a recovery partition, see [Configure UEFI/GPT-based hard drive partitions](/windows-hardware/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions).

1. Use Diskpart to identify the volume where the WIM file is stored:

    ```cmd
    list volume
    ```

    You should see something like:

    ```output
    Volume ###  Ltr  Label        Fs     Type        Size     Status     Info
    ----------  ---  -----------  -----  ----------  -------  ---------  -------- 
    Volume 0     W   Windows      NTFS   Partition     63 GB  Healthy    
    Volume 1     S   System       FAT32  Partition    100 MB  Healthy    Hidden
    Volume 2     C   WINPE        FAT32  Partition   4078 MB  Healthy
    Volume 3     D   Images       NTFS   Partition     16 GB  Healthy       
    ```

    In this example, *Volume 3* with the letter *D* is where the WIM file is stored.

1. Exit Diskpart:

    ```cmd
    exit
    ```

1. From the WinPE command prompt, deploy the WIM image to the W: drive created in the previous step:

    ```cmd
    Dism /Apply-Image /ImageFile:D:\WindowsIoTEnterprise.wim /ApplyDir:W:\ /Index:1
    ```

    :::image type="content" source="../Get-Started/media/quickstart-sysprep-capture-deploy/winpe-dism-apply-image.png" alt-text="Screenshot that shows the success apply of the image using dism":::

1. From the WinPE Command Prompt, configure the default BCD on the system, which is a required step as the disk was freshly partitioned and formatted:

    ```cmd
    W:\Windows\System32\bcdboot W:\Windows /s S:
    ```

1. Turn off the Virtual Machine:

    ```cmd
    wpeutil shutdown
    ```

1. In the Virtual Machine settings, set the VHD where you installed the WIM file as the first in boot order.

1. Start the Virtual Machine.

The device starts into OOBE with the Windows IoT Enterprise image you previously customized and captured.

---

## Related content

- [Customization](../Customize/customize-overview.md)
- [Optimization](../Optimize/Overview.md)
- [Deployment](../Deployment/index.md)