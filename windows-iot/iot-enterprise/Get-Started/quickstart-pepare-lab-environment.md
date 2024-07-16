---
title: "Quickstart: Prepare your lab environment"
description: "Get your technician PC ready to start building Windows IoT Enterprise images and prepare the reference device sample"
author: asergaz
ms.author: sergaz
ms.service: windows-iot
ms.subservice: iot
ms.topic: quickstart
ms.date: 06/28/2024

#customer intent: As a beginner, I want to know how to prepare my environment to build Windows IoT Enterprise images.

---

# Quickstart: Prepare your lab environment

In this quickstart, we walk you through preparing the technician PC to then install a basic Windows IoT Enterprise image onto a reference device sample. At the end of this quickstart, you have a technician PC ready to start building Windows IoT Enterprise images, and a reference device sample with Windows IoT Enterprise installed.

The following quicsktarts in this series build on this one to customize the device in audit mode and then sysprep and capture the reference device image. Alternatively, you can use the lab environment prepared in this quickstart to follow other tutorials under [Customization](../Customize/customize-overview.md), [Optimization](../Optimize/Overview.md) and [Deployment](../Deployment/index.md).

> [!TIP]
> This series of quickstarts is intended to help you get started with Windows IoT Enterprise as quickly as possible, and that is why we provide you steps to test it in a Virtual Machine. In a true development or production environment, you would start by choosing a **physical device** that meets the [Minimum System Requirements for Windows IoT Enterprise](../Hardware/System_Requirements.md). You would then build base images for this device and test it. Next, you would modify the base images to create designs for different audiences, including branding, logos, languages, and apps.

## Prerequisites

To prepare your **technician PC (your work PC)**, you need:

- Have at least 15 GB of free space for installing the software and for modifying Windows IoT Enterprise images. We recommend using Windows 11 with the latest updates.
- Have [Windows ADK](/windows-hardware/get-started/adk-install) with Deployment Tools, Configuration Designer, and the Windows PE add-on installed.
- Have a Windows 11 IoT Enterprise LTSC 2024 ISO.
    [!INCLUDE [Latest LTSC](../../includes/incl-latest-ltsc-release.md)]

<!--TODO: Confirm that we don't need to demonstrate Language and Feature installation in this Getting Started
 - Have the [Languages and Optional Features ISO](/windows-hardware/manufacture/desktop/languages-overview?view=windows-11&preserve-view=true). If you can't download the ISO we will provide you the alternative steps to customize the device using network connection. -->

To prepare your **reference device sample**, you need:

### [Physical Device](#tab/physicaldevice)

- A physical device that meets the [Minimum System Requirements for Windows IoT Enterprise](../Hardware/System_Requirements.md).
- Depending on the device you may need an external keyboard, mouse and a monitor.
- A USB key that's at least 8 GB in size and that can have all information removed from it.

### [Virtual Machine](#tab/virtualmachine)

- A virtual machine that meets the [Minimum System Requirements for Windows IoT Enterprise](../Hardware/System_Requirements.md).

    > [!IMPORTANT]
    > This series of quickstarts focuses on using Hyper-V with Windows 11. First, confirm that you can [install Hyper-V](/virtualization/hyper-v-on-windows/quick-start/enable-hyper-v) on your **technician PC**. If Hyper-V is not suitable for your setup, consider using alternative virtualization technologies.

---

## Create a bootable media

This section provides steps to create a bootable Windows IoT Enterprise installation media for use during installation on the reference device sample.

### [Physical Device](#tab/physicaldevice)

The typical way to install Windows in a physical device is to create a bootable USB flash drive, and then copy the Windows installation files onto the flash drive. Once you have the files on the flash drive, you can insert it into the device and boot from the flash drive. See [Install Windows from a USB flash drive](/windows-hardware/manufacture/desktop/install-windows-from-a-usb-flash-drive) to learn more.

Follow these steps to prepare the installation flash drive:

1. Insert a flash drive into your Technician PC.
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
   Disk 0    Online          238  GB     0 B        *
   Disk 1    Online          8192 MB     0 B      
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

1. Copy the entire contents of the Windows IoT Enterprise ISO onto the root of the flash drive. You can use File explorer to manually copy the files.  

### [Virtual Machine](#tab/virtualmachine)

Create the Virtual Machine and a bootable CD/DVD-ROM in Hyper-V:

1. Open Hyper-V Manager.
1. In the Hyper-V Manager, click on **New** in the **Actions pane**, then select **Virtual Machine**.
1. Follow the wizard to create a new virtual machine.

Configure the Virtual Machine:

1. When prompted to specify the generation, choose **Generation 1** or **Generation 2** based on your requirements.
1. Assign a minimum of *2 GB* of memory to the virtual machine.
1. Leave the virtual machine with no connection to the network.
1. When you reach the **Connect Virtual Hard Disk** step, select **Create a virtual hard disk**.
1. Specify the name, location, and size of the VHD. For example, set the size to *64 GB*.

Attach the Windows IoT Enterprise ISO:

1. In the **Installation Options** step, select **Install an operating system from a bootable CD/DVD-ROM**.
1. Choose **Image file (.iso)** and browse to the location of your Windows IoT Enterprise ISO file.

Configure the Number of Processors:

1. After the virtual machine is created, right-click on it in the Hyper-V Manager and select **Settings**.
1. In the left pane, select **Processor**.
1. In the right pane, specify a minimum of *2 virtual processors*.

---

## Install Windows IoT Enterprise on your reference device sample

This section covers how to install Windows IoT Enterprise on your reference device sample using Windows Setup.

> [!TIP]
> We recommend not having your device connected to any network during Windows Setup. Network connectivity could cause it to come out of the deferred activation state.

### [Physical Device](#tab/physicaldevice)

Boot the device to Windows Setup:

1. Move the USB flash drive from the **technician PC** to the powered down **physical device**.
1. Turn on your physical device and enter the device's boot menu. Your device has a specific button combination or keyboard key to press to get to the boot menu. You may need to consult your hardware documentation if you aren't familiar with how to get to your device's boot menu.  
1. From the boot menu, select the flash drive to boot from. Your device boots from the flash drive and enter into the Windows Setup.

Install Windows with Windows Setup:

1. Step through the Windows Setup menus, providing the requested information. Choose the settings, such as language, time and currency, and keyboard options that apply to your device and proceed to the next screen.
1. Select **Install now**.
1. On the **Activate Windows screen**, insert a valid product key.  Select **I don't have a product key** if you don't have a product key.  
1. On the **Application notices and license terms** screen, if the terms are acceptable check the checkbox that you accept the license terms and then select **Next**.  
1. On the **Which type of installation do you want** screen, select **Custom: Install Windows only**. This option starts a clean installation
1. In the **Where do you want to install Windows?** screen, if the device has existing partitions, we recommend deleting the partitions so you have a single block on unallocated space to start from, then select **Next** to start the installation.
1. Your device restarts a couple of times during the operating system installation. Wait until the device has entered OOBE (Out Of Box Experience) and is showing a screen that says **Let's start with region.**.

<!-- TODO: Screenshot of Let's start with region -->

> [!NOTE]
> When at the **Let's start with region** OOBE screen don't continue the setup as you will need to enter Audit mode at this point. In the event that you started the setup of an account by mistake, you can open an Administrative Command Prompt and run `sysprep /audit` to enter Audit mode and continue the steps.

### [Virtual Machine](#tab/virtualmachine)

Start the Virtual Machine:

1. Once the virtual machine is created, right-click on it in the Hyper-V Manager and select **Connect**.
1. Click **Start** to power on the virtual machine.
1. Your device boots from the CD/DVD-ROM ISO and enter into the Windows Setup.

Install Windows with Windows Setup:

1. Step through the Windows Setup menus, providing the requested information. Choose the settings, such as language, time and currency, and keyboard options that apply to your device and proceed to the next screen.
1. Select **Install now**.
1. On the **Activate Windows screen**, insert a valid product key.  Select **I don't have a product key** if you don't have a product key.  
1. On the **Application notices and license terms** screen, if the terms are acceptable check the checkbox that you accept the license terms and then select **Next**.  
1. On the **Which type of installation do you want** screen, select **Custom: Install Windows only**. This option starts a clean installation
1. In the **Where do you want to install Windows?** screen, if the device has existing partitions, we recommend deleting the partitions so you have a single block on unallocated space to start from, then select **Next** to start the installation.
1. Your device restarts a couple of times during the operating system installation. Wait until the device has entered OOBE (Out Of Box Experience) and is showing a screen that says **Let's start with region.**.

<!-- TODO: Screenshot of Let's start with region -->

> [!NOTE]
> When at the **Let's start with region** OOBE screen don't continue the setup as you will need to enter Audit mode at this point. In the event that you started the setup of an account by mistake, you can open an Administrative Command Prompt and run `sysprep /audit` to enter Audit mode and continue the steps.

---

## Enter Audit Mode

Windows is installed on your reference device sample and you have a basic image that's ready to be customized in Audit mode.

1. From the first OOBE screen, use the <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>F3</kbd> combination on your keyboard to enter Audit mode.
1. Your device should restart in Audit mode. You know you're in Audit mode when you see a System Preparation Tool window. Select **Cancel** on the System Preparation Tool to close it.
1. Every time you reboot the system you see the System Preparation Tool, also called Sysprep.

<!-- TODO: Screenshot of Audit Mode screen showing "System Preparation Tool" -->

> [!TIP]
> If you're in Audit mode and a password-protected screen saver starts, you can't log back on to the system. The built-in administrator account that's used to log on to Audit mode is immediately disabled after logon. Disable the screen saver by either changing the power plan in the Settings app, or configure and deploy a custom plan. For more information, see [Create a Custom Power Plan](/windows-hardware/manufacture/desktop/create-a-custom-power-plan-technicalreference).

## Next step

> [!div class="nextstepaction"]
> [Quickstart: Customize a reference device in Audit mode](quickstart-customize-reference-device.md)