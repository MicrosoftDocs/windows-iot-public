---
description: Sysprep capture and deploy
title: Sysprep capture and deploy
ms.date: 12/10/2018
ms.topic: article
author: TerryWarwick
ms.author: twarwick
ms.service: windows-iot
ms.subservice: iot

---

# Lab 4: Sysprep - Capture - Deploy

Now that the reference IoT device has been customized with software and settings, the system is prepared for mass deployment using Sysprep and then captured to a WIM image using DISM. This image is used during manufacturing to deploy to new systems.

> [!NOTE]
>The following steps use a combination of WinPE and DISM to complete the capture process. These tools are freely available from Microsoft. Some tools, like DISM, are included with all Windows installations.

For a fully automated approach to these steps, consider using the [Windows IoT Enterprise deployment framework](https://github.com/ms-iot/windows-iotent-deploy).

## Prerequisites

- Complete at least [Lab 1a](iot-ent-create-a-basic-image.md). This lab covers how to capture the image you created.
- The ADK with the WinPE add-on installed on your technician PC. For more information, see [Get the tools you need](iot-ent-get-the-tools-you-need.md).

## Run Sysprep to complete the Audit process

In [lab 1a](iot-ent-create-a-basic-image.md), you put the system into audit mode, which is a special setup mode where a device maker can preinstall software and configure settings on a reference IoT device. When you've made your customizations in audit mode, you can capture an image of your customized reference device. While audit mode isn't required, it does provide a scenario where the IoT device can be customized online prior to OOBE.

### Sysprep the reference IoT device

While booted into audit mode on the reference IoT device, run Sysprep from an Administrative Command Prompt to prepare the image for capture:

```cmd
C:\Windows\System32\Sysprep> sysprep.exe /generalize /oobe /shutdown
```

After Sysprep prepares the image, the reference device will shut down. The next time the device boots, it will boot into OOBE.

> [!CAUTION]
> Don't power the reference IoT device back on until you're ready to capture an image. If the device boots, you'll have to go through the Sysprep process again.
  
## Capture your device image

### Create a WinPE USB drive

In this section, we show you how to create a bootable WinPE USB drive. We'll create multiple partitions on the USB drive. This allows you to have a FAT32 partition for WinPE and an NTFS partition for the captured WIM file. You can use this USB drive for both capturing and deploying your image.

1. Insert a USB drive into the Technician PC.

   > [!NOTE]
   >Use a USB drive that's at least 8GB.

1. Open the **Deployment and Imaging Tools Environment** as administrator. You can find a shortcut to the Deployment and Imaging Tools under Windows Kits in the Start Menu.

1. Run Diskpart:

    ```cmd
    diskpart
    ```

1. Use Diskpart to reformat the drive and create two new partitions for WinPE and for your images:

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

    Where *P:* is the USB drive with the WinPE Partition. This command formats the partition and erase any data that's on it.

1. Move the USB flash drive from the Technician PC to the reference IoT device.

### Boot the IoT reference device to WinPE and capture the Windows IoT Enterprise OS image

The following steps capture a WIM image from the reference IoT device's hard drive. This WIM can be used in development or in production. It's common to capture OS images during different stages of the development process. For example, the following steps could be used to capture a base image of the OS with default apps installed. A later image could be captured with more end customer apps installed.

1. Boot the reference IoT device from the bootable WinPE USB flash drive. The sequence to select which media to boot from is different from device to device. Consult the documentation for the IoT reference device in order to determine which key to press during boot in order to select the USB flash device as the boot target.

    > [!IMPORTANT]
    > Don't boot your device until you know which key brings up the device's boot menu. The imaged IoT device is in a Sysprepped state and should not be allowed to boot back into Windows IoT Enterprise.

    The system boots to the WinPE, where you see a Command prompt.

    > [!TIP]
    > If you have a different keyboard layout, you can change the keyboard layout by running `wpeutil setKeyboardLayout 0816:00000816` where the *language:keyboard* pair list for your desired layout can be found in [input locales](/windows-hardware/manufacture/desktop/default-input-locales-for-windows-language-packs). Then run `winpeshl.exe` from the WinPE Command Prompt to ensure the new layout is applied to the current session.

1. From the WinPE Command prompt run Diskpart:

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

    In this example, *Partition 3* is of *Type Primary* and is where Windows IoT Enterprise is installed. Letters *C*, *D* and *E* are assigned to the *WinPE*, *Images* and *DVD-ROM* volumes respectively.

1. Select Partition 3 and assign a drive letter that is not already in use:

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
    Dism /capture-image /imagefile:D:\IoTOS.wim /CaptureDir:W:\ /Name:"Windows IoT Enterprise"
    ```

    DISM captures an image of the OS partition and store it on D: drive.

    > [!NOTE]
    > Your device will have more than one partition, but you only need to capture the Windows partition. Refer to the deployment lab steps on how to re-create the system partition dynamically during deployment.

## Deploy the captured WIM image from WinPE

In this section, we show you how to deploy a WIM image from WinPE. The reference IoT device that we've been creating in these labs should already be in a deployed state; it's been captured in a Sysprepped state and, when deployed, boot into OOBE. Use the following steps to image a clean system. For this lab series, you can move on to [lab 5](iot-ent-shell-launcher-app-launcher.md) from here, since the reference IoT device is powered on and OOBE completed.

### Use the WinPE USB drive to deploy to new systems

1. Boot the reference IoT device from the bootable WinPE USB flash drive.

1. Format the device. From the WinPE command prompt:

    ```cmd
    diskpart
    list disk
    select disk X    (where X is the disk of your reference IoT device)
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

1. Deploy the WIM image to the W: drive created in the previous step. From the WinPE command prompt:

    ```cmd
    Dism /Apply-Image /ImageFile:D:\IoTOS.wim /ApplyDir:W:\ /Index:1
    ```

    Where *D:\IoTOS.wim* is the path to the WIM file you captured in the previous section, and that was stored in the Images partition of the USB drive.

1. Configure the default BCD on the system, which is a required step as the disk was freshly partitioned and formatted which requires a new BCD. From the WinPE Command Prompt:

    ```cmd
    W:\Windows\System32\bcdboot W:\Windows /s S:
    ```

1. Remove the USB drive and reboot the system at the WinPE Command Prompt.

    ```cmd
    wpeutil reboot
    ```

    The IoT device reboots into OOBE.

## Next steps

Now that you've captured and deployed a Windows image, you can configure Windows to launch to a custom Shell. Lab 5 covers how to configure Shell launcher or Assigned Access.

>[!div class="nextstepaction"]
>[Go to lab 5](iot-ent-shell-launcher-app-launcher.md)
