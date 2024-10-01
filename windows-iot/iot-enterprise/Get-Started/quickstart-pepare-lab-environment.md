---
title: "Quickstart: Prepare your lab environment"
description: "Get your technician PC ready to start building Windows IoT Enterprise images and prepare the reference device sample"
author: asergaz
ms.author: sergaz
ms.service: windows-iot
ms.subservice: iot
ms.topic: quickstart
ms.date: 09/27/2024

#customer intent: As a beginner, I want to know how to prepare my environment to build Windows IoT Enterprise images.

---

# Quickstart: Prepare your lab environment

In this quickstart, you prepare the technician PC to then install a basic Windows IoT Enterprise image onto a reference device sample. At the end of this quickstart, you have a technician PC ready to start building Windows IoT Enterprise images, and a reference device sample with Windows IoT Enterprise installed.

The lab environment created during this exercise is used in the successor quickstarts: [Quickstart: Customize a reference device in Audit mode](quickstart-customize-reference-device.md) and [Quickstart: Sysprep and capture the reference device image, and deploy to a new device](quickstart-sysprep-capture-deploy.md).

In this series of quickstarts, you can opt by using a **Virtual Machine** as your reference device sample. In a true development or production environment, you would start by choosing a **Physical Device** that meets the [Minimum System Requirements for Windows IoT Enterprise](../Hardware/System_Requirements.md).

> [!TIP]
> You can also use the lab environment created during this exercise, to complete other tutorials under [Customization](../Customize/customize-overview.md), [Optimization](../Optimize/Overview.md) and [Deployment](../Deployment/index.md).

## Prerequisites

To prepare your **technician PC (your work PC)**, you need:

- Windows 11 with the latest updates.
- Have at least 15 GB of free space for installing the software and for modifying Windows IoT Enterprise images.
- Have [Windows Assessment and Deployment Kit (ADK)](/windows-hardware/get-started/adk-install) with Deployment Tools, Configuration Designer, and the Windows PE add-on installed.
- Have a Windows 11 IoT Enterprise Long-Term Servicing Channel (LTSC) 2024 ISO.
    [!INCLUDE [Latest LTSC](../../includes/incl-latest-ltsc-release.md)]

To prepare your **reference device sample**, you need:

### [Physical Device](#tab/physicaldevice)

- A physical device that meets the [Minimum System Requirements for Windows IoT Enterprise](../Hardware/System_Requirements.md).
- An external keyboard, mouse, and a monitor (depending on the device).
- A USB key that's at least 8 GB in size and that can have all information removed from it.

### Create a bootable Windows IoT Enterprise installation media

The typical way to install Windows in a physical device is to create a bootable USB flash drive, and then copy the Windows installation files onto the flash drive. Once you have the files on the flash drive, you can insert it into the device and boot from the flash drive. To learn more, see [Install Windows from a USB flash drive](/windows-hardware/manufacture/desktop/install-windows-from-a-usb-flash-drive).

Follow these steps to prepare the installation flash drive:

1. Insert a flash drive into your Technician PC.
1. Open Command Prompt with Administrator privileges and run `diskpart`:

   ```cmd
   diskpart
   ```

1. Use `diskpart` to list the disks so you can identify the flash drive:

   ```cmd
   list disk
   ```

   You should see something like:

   ```cmd
   Disk ###  Status         Size     Free     Dyn  Gpt
   --------  -------------  -------  -------  ---  ---
   Disk 0    Online          238  GB     0 B        *
   Disk 1    Online          8192 MB     0 B      
   ```

   In this example, Disk 1 is our flash drive, because the size represents the size of the flash drive that we're using.

1. When you identify the disk number of your flash drive, use `diskpart` to prepare the drive so you can use it as a bootable installation drive:

    > [!WARNING]
    >The following commands will erase everything on the flash drive.

    Enter the following commands from within `diskpart`, where Disk 1 is the flash drive:

    ```cmd
    Select disk 1
    clean
    create partition primary
    select partition 1
    active
    Format fs=fat32 quick
    assign
    exit
    ```

1. Mount the Windows IoT Enterprise ISO on your Technician PC by double clicking the ISO and copy the entire contents onto the root of the flash drive. You can use File explorer to manually copy the files.

### Boot the device to Windows Setup:

1. Move the USB flash drive from the **technician PC** to the powered down **physical device**.
1. Turn on your physical device and enter the device's boot menu. Your device has a specific button combination or keyboard key to press to get to the boot menu. You might need to consult your hardware documentation if you aren't familiar with how to get to your device's boot menu.  
1. From the boot menu, select the flash drive to boot from. Your device boots from the flash drive and enter into the Windows Setup.

### [Virtual Machine](#tab/virtualmachine)

- A virtual machine that meets the [Minimum System Requirements for Windows IoT Enterprise](../Hardware/System_Requirements.md).

    > [!IMPORTANT]
    > This series of quickstarts focuses on using Hyper-V with Windows 11. First, confirm that you can [install Hyper-V](/virtualization/hyper-v-on-windows/quick-start/enable-hyper-v) on your **technician PC**. If Hyper-V is not suitable for your setup, consider using alternative virtualization technologies.

### A virtual machine booting to Windows IoT Enterprise ISO

Create the Virtual Machine in Hyper-V:

1. Open Hyper-V Manager.
1. In the Hyper-V Manager, select **New** in the **Actions pane**, then select **Virtual Machine**.
1. Follow the wizard to create a new virtual machine.
1. When prompted to specify the generation, choose **Generation 1** or **Generation 2** based on your requirements.
1. Assign a minimum of *2 GB* of memory to the virtual machine.
1. Leave the virtual machine with no connection to the network.
1. When you reach the **Connect Virtual Hard Disk** step, select **Create a virtual hard disk**.
1. Specify the name, location, and size of the Virtual Hard Disk (VHD). For example, set the size to *64 GB*.
1. In the **Installation Options** step, select **Install an operating system from a bootable CD/DVD-ROM**.
1. Choose **Image file (.iso)** and browse to the location of your Windows IoT Enterprise ISO file.
1. Review the settings in the **Summary** step and select **Finish** to create the virtual machine.

Configure the Number of Processors:

1. After the virtual machine is created, right-click on it in the Hyper-V Manager and select **Settings**.
1. In the left pane, select **Processor**.
1. In the right pane, specify a minimum of *two virtual processors*.

Start the Virtual Machine:

1. In the Hyper-V Manager, right-click on the Virtual Machine and select **Connect**.
1. Select **Start** to power on the virtual machine.
1. Your device boots from the CD/DVD-ROM ISO and enter into the Windows Setup.

---

## Install Windows IoT Enterprise on your reference device sample

This section covers how to install Windows IoT Enterprise on your reference device sample using Windows Setup. The steps apply to both **physical device** and **virtual machine**.

> [!TIP]
> We recommend not having your device connected to any network during Windows Setup. Network connectivity could cause it to come out of the deferred activation state.

Install Windows with Windows Setup:

1. Step through the Windows Setup menus, providing the requested information. Choose the settings, such as language, time and currency, and keyboard options that apply to your device and proceed to the next screen.

1. Select **Install Windows 11**.

1. On the **Activate Windows** screen, insert a valid product key. This screen won't show if you are using an evaluation or volume license edition.

1. On the **Applicable notices and license terms** screen, select **Accept** if you agree with the terms.

1. On the **Select location to install Windows 11** screen, if the device has existing partitions, we recommend deleting the partitions so you have a single block on unallocated space to start from, then select **Next** to start the installation.

1. Your device restarts a couple of times during the operating system installation. Wait until the device enters Out Of Box Experience (OOBE) and is showing a screen that says **Is this the right country or region?**.

    :::image type="content" source="../Get-Started/media/quickstart-pepare-lab-environment/country-region-oobe-screen.png" alt-text="Screenshot that shows the  OOBE screen Is this the right country or region.":::

> [!NOTE]
> When at the **Is this the right country or region?** OOBE screen don't continue the setup as you will need to enter Audit mode at this point. In the event that you started the setup of an account by mistake, you can open Command Prompt with Administrator privileges and run `C:\Windows\System32\Sysprep\sysprep.exe /audit` to enter Audit mode and continue the steps.

## Enter Audit Mode

Windows is installed on your reference device sample and you have a basic image that's ready to be customized in Audit mode.

1. From the first OOBE screen that says **Is this the right country or region?**, use the <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>F3</kbd> combination on your keyboard to enter Audit mode.

1. Your device should restart in Audit mode. You know you're in Audit mode when you see a System Preparation Tool window.

1. Every time you reboot the system you see the System Preparation Tool, also called Sysprep. Select **Cancel** on the System Preparation Tool to close it.

    :::image type="content" source="../Get-Started/media/quickstart-pepare-lab-environment/audit-mode-sysprep-tool.png" alt-text="Screenshot of Audit Mode screen showing System Preparation Tool.":::

> [!TIP]
> If you're in Audit mode and a password-protected screen saver starts, you can't log back on to the system. The built-in administrator account that's used to log on to Audit mode is immediately disabled after logon. Disable the screen saver by either changing the power plan in the Settings app, or configure and deploy a custom plan. For more information, see [Create a Custom Power Plan](/windows-hardware/manufacture/desktop/create-a-custom-power-plan-technicalreference).

## Next step

> [!div class="nextstepaction"]
> [Quickstart: Customize a reference device in Audit mode](quickstart-customize-reference-device.md)
