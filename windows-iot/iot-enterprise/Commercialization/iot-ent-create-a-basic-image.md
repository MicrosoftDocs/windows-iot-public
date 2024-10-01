---
description: Create a basic image that you can further customize
title: Create a basic Iot Enterprise image
ms.date: 09/27/2024
ms.topic: article
author: TerryWarwick
ms.author: twarwick
ms.service: windows-iot
ms.subservice: iot
---


# Lab 1a: Create a basic image (iot-ent-create-a-basic-image)

To get started, we walk through installing a basic Windows IoT Enterprise image onto a device to make sure everything is working before we move on to adding customizations. This lab is a prerequisite  for completing all of the other labs in this section, as the other labs build on this first basic image.

## What you need to complete this series of labs

See [Get the tools you need to create an IoT Enterprise image](iot-ent-get-the-tools-you-need.md) and make sure you have everything you need. Once you have everything, you can move on to the next section.

## Create your basic image

### Install Windows onto a reference device

This section covers how to create bootable Windows installation flash drive for use during installation.

#### Create a bootable flash drive

The typical way to install Windows is to create a bootable flash drive, and then copy the Windows installation files onto the flash drive. Once you have the files on the flash drive, you can insert it into the IoT device and boot from the flash drive. See [Install Windows from a USB flash drive](/windows-hardware/manufacture/desktop/install-windows-from-a-usb-flash-drive) to learn more.

Here's how to prepare the installation flash drive:

1. Insert a flash drive into your Technician PC
1. Open an Administrative Command Prompt and run `diskpart`:

   ```console
   diskpart
   ```

1. Use `diskpart` to list the disks so you can identify the flash drive:

   ```console
   list disk
   ```

   You should see something like:

   ```console
   Disk ###  Status         Size     Free     Dyn  Gpt
   --------  -------------  -------  -------  ---  ---
   Disk 0    Online          238 GB      0 B        *
   Disk 1    Online          3822 MB     0 B      
   ```

   In this example, Disk 1 is our flash drive, because the size represents the size of the flash drive that we're using.

1. When you've identified the disk number of your flash drive, use `diskpart` to prepare the drive so you can use it as a bootable installation drive:

    > [!WARNING]
    >The following commands will erase everything on the flash drive.

    Enter the following commands from within `diskpart`, where Disk 1 is the flash drive:

    ```diskpart
    Select disk 1
    clean
    create partition primary
    select partition 1
    active
    Format fs=fat32 quick
    assign
    exit
    ```

1. Copy the entire contents of the Windows IoT Enterprise ISO or DVD onto the root of the flash drive. You can use File explorer to manually copy the files.  

#### Install Windows from the flash drive onto your IoT device and boot into Audit mode

This section covers how to use the Windows installation flash to install Windows onto your IoT device using Windows Setup.

We recommend not having your device connected to any network during Windows Setup. Network connectivity could cause it to come out of the deferred activation state.  

##### Boot the device to Windows Setup

1. Move the flash drive from the Technician PC to the powered down IoT device.
1. Turn on your IoT device and enter the device's boot menu. Your device has a specific button combination or keyboard key to press to get to the boot menu. You may need to consult your hardware documentation if you aren't familiar with how to get to your device's boot menu.  
1. From the boot menu, select the flash drive to boot from. Your device boots from the flash drive and enter into the Windows Setup.

##### Install Windows with Windows Setup

1. Step through the Windows Setup menus, providing the requested information. Choose the settings, such as language, time and currency, and keyboard options that apply to your device and select to the next screen.
1. On the "Install now" screen, select on **Install now**.
1. On the Activate Windows screen, insert a valid product key.  Select **I don't have a product key** if you don't have a product key.  
1. On the Application notices and license terms screen, if the terms are acceptable check the checkbox that you accept the license terms and then select **Next**.  
1. On the "Which type of installation do you want" screen, select **Custom: Install Windows only**. This option starts a clean installation
1. In the "Where do you want to install Windows?" screen, if the device has existing partitions, we recommend deleting the partitions so you have a single block on unallocated space to start from, then select **Next** to start the installation.
1. Your device restarts a couple of times during the operating system installation. Wait until the IoT device has entered OOBE (Out Of Box Experience) and is showing a screen that says **Let's start with region.**.

> [!NOTE]
> When at the **Let's start with region** OOBE screen don't continue the setup as you will need to enter Audit mode at this point. In the event that you started the setup of an account by mistake, you can open a Command Prompt with Administrator privileges and run `sysprep /audit` to enter Audit mode and continue the steps.

##### Enter Audit Mode

1. From the first OOBE screen, use the **CTRL+SHIFT+F3** combination on your keyboard to enter Audit mode.
1. Your device should restart in Audit mode. You know you're in Audit mode when you see a System Preparation Tool window. Select **Cancel** on the System Preparation Tool to close it.
1. Every time you reboot the system you see the System Preparation Tool, also called Sysprep.  In a future lab, you invoke the Sysprep utility to get the system out of Audit mode. For more information on Audit mode, see [Lab 1b - Customize a reference device in Audit mode](iot-ent-customize-the-reference-device-in-audit-mode.md).

> [!TIP]
> If you're in Audit mode and a password-protected screen saver starts, you can't log back on to the system. The built-in administrator account that's used to log on to Audit mode is immediately disabled after logon. Disable the screen saver by either changing the power plan in the Settings app, or configure and deploy a custom plan. For more information, see [Create a Custom Power Plan](/windows-hardware/manufacture/desktop/create-a-custom-power-plan-technicalreference).

## Next steps

Windows is installed on your reference device and you have a basic image that's ready to be customized. In lab 1b, we take the basic image and use Audit mode to customize it.

>[!div class="nextstepaction"]
>[Go to lab 1b](iot-ent-customize-the-reference-device-in-audit-mode.md)
