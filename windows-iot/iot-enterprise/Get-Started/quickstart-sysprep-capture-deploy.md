---
title: "Quickstart: Sysprep and capture the reference device image and deploy to a new device"
description: "Sysprep and capture the reference device image of Windows IoT Enterprise to a WIM using DISM. Then deploy the WIM image to a new device"
author: asergaz
ms.author: sergaz
ms.service: windows-iot
ms.subservice: iot
ms.topic: quickstart
ms.date: 06/28/2024

#customer intent: As a beginner, I want to learn the basics on how to sysprep, capture and deploy Windows IoT Enterprise.

---

# Quickstart: Sysprep and capture the reference device image, and deploy to a new device

In this quickstart, you sysprep and capture the reference device image of Windows IoT Enterprise to a Windows Imaging Format (WIM) file using the Deployment Image Servicing and Management (DISM) tool. Then, you deploy the WIM image to a new device.

## Prerequisites

- Complete [Quickstart: Prepare your lab environment](quickstart-pepare-lab-environment.md) before you begin this quickstart.

## Sysprep the reference device sample

When you've made your customizations in audit mode, you can capture an image of your customized reference device. While audit mode isn't required, it does provide a scenario where the device can be customized online prior to OOBE.

This section provides steps to sysprep the reference device and apply to both physical device and virtual machine:

1. While booted into audit mode on the reference device, run Sysprep from an Administrative Command Prompt to prepare the image for capture:

    ```cmd
    C:\Windows\System32\Sysprep> sysprep.exe /generalize /oobe /shutdown
    ```

> [!NOTE]
> If you completed [Quickstart: Customize a reference device in Audit mode](quickstart-customize-reference-device.md) and left *powershell.exe* as your custom shell, run the following command to open an Administrative Command Prompt: `Start-Process cmd -Verb RunAs`

<!-- TODO: Confirm the command above, is this working? -->

After Sysprep prepares the image, the reference device will shut down. The next time the device boots, it will boot into OOBE.

> [!CAUTION]
> Don't power the reference IoT device back on until you're ready to capture an image. If the device boots, you'll have to go through the Sysprep process again.

## Create a bootable WinPE drive

Windows PE (WinPE) is a small operating system used to install, deploy, and repair Windows desktop editions, Windows Server, and other Windows operating systems. It is an add-on to the Windows Assessment and Deployment Kit (ADK) that you previously installed in your technician PC.

In your **technician PC** follow the steps to create a bootable WinPE drive:

### [Physical Device](#tab/physicaldevice)

In this section, you create a bootable WinPE USB drive. You will create multiple partitions on the USB drive. This allows you to have a FAT32 partition for WinPE and an NTFS partition for the captured WIM file. You can use this USB drive for both capturing and deploying your image.

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

    This command copies the 64-bit WinPE files to C:\WinPE. Note that the destination folder is created automatically.

1. Copy the WinPE files to your USB key.

    ```cmd
    makewinpemedia /ufd C:\WinPE P:
    ```

    Where *P:* is the USB drive with the WinPE Partition. This command formats the partition and erase any data that's on it.

1. Move the USB flash drive from the technician PC to the reference device.

### [Virtual Machine](#tab/virtualmachine)

In this section, you create a bootable WinPE virtual hard disk drive (VHD) and a second VHD to store the captured WIM file. You use WinPE for both capturing and deploying your image.

1. Open Hyper-V Manager.
1. Right-click on the Virtual Machine and select **Settings**.
1. In the left pane, select **SCSI Controller**.
1. In the right pane, select **Hard Drive** and then **Add**.
1. Select **New** to create a VHD.
1. Follow the wizard to create a new VHD. For WinPE you can define a size of *4 GB*.
1. Repeat the steps to create another VHD to store the WIM file. You can define the size as *8 GB*.
1. At the end select **Apply** and **OK** to create the VHDs.

Select WinPE VHD as the first in boot order:

1. Right-click on the Virtual Machine and select **Settings**.
1. In the left pane, select **Firmware**.
1. In the right pane, move WinPE VHD to the top.
1. At the end select **Apply** and **OK**

Mount the VHDs on your **technician PC**

1. Press <kbd>Windows</kbd> + <kbd>R</kbd>, type *diskmgmt.msc*, and press **Enter**.
1. In Disk Management, select **Action** in the menu bar.
1. Select **Attach VHD**.
1. In the dialog that appears, select *Browse* and navigate to the location of your VHD file.
1. Select the VHD file and select **OK**.
1. The VHD will now appear as a new disk in Disk Management.
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

    This command copies the 64-bit WinPE files to C:\WinPE. Note that the destination folder is created automatically.

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

## Deploy the captured WIM image from WinPE

### Use the WinPE USB drive to deploy to new systems

## Related content

- [Customization](../Customize/customize-overview.md)
- [Optimization](../Optimize/Overview.md)
- [Deployment](../Deployment/index.md)