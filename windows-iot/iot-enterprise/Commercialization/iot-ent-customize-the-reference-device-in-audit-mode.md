---
description: Customize the reference device in Audit mode.
title: Customize the reference device in Audit mode
ms.date: 09/27/2024
ms.topic: article
author: TerryWarwick
ms.author: twarwick
ms.service: windows-iot
ms.subservice: iot

---

# Lab 1b: Customize the reference device in Audit Mode

In [Lab 1a](iot-ent-create-a-basic-image.md), you installed Windows IoT Enterprise onto an IoT device and booted into audit mode. In this lab, we show you how to customize your device from audit mode.

> [!TIP]
> Most customizations in this lab can be made to an offline mounted Windows image, as well as in Audit mode. For more information, see [Modify a Windows image using DISM](/windows-hardware/manufacture/desktop/mount-and-modify-a-windows-image-using-dism).

## What is Audit Mode?

Most of our solutions are customized by our OEM partners. OEM software plays a significant role in the functionality of the IoT Device. Windows IoT Enterprise supports OEM customization and allows for a custom-built device to be run on top of the operating system.

To assist our OEM customers, we offer [Audit Mode](/windows-hardware/manufacture/desktop/audit-mode-overview) that allows administrators to boot directly to the desktop before you get to the Windows Welcome screen, giving them the opportunity to install Windows Updates, drivers, and other software as needed.

## Benefits of using Audit Mode

When Windows boots, it starts in either Out-Of-Box Experience (OOBE) mode or in audit mode. OOBE is the default out-of-box experience that allows end users to enter their account information, select language, accept the Microsoft Terms of Service, and set up networking. In audit mode, you can:

- Bypass OOBE. You can access the desktop as quickly as possible. You don't have to configure default settings such as a user account, location, and time zone.
- Install applications, add device drivers, and run scripts. You can connect to a network and access more installation files and scripts. You can also install more language packs and device drivers.
- Test the validity of a Windows installation. Before you deploy the system to end users, you can perform tests on the system without creating a user account. Then you can prepare the system to start in OOBE on the next boot.
- Add more customizations to a reference image. This reduces the number of images that you have to manage. For example, you can create a single reference image that contains the basic customizations that you want to apply to all Windows images. You can then boot the reference image to audit mode and make more changes that are specific to the computer. These changes can be customer-requested applications or specific device drivers.

For more information see [Audit mode overview](/windows-hardware/manufacture/desktop/audit-mode-overview).

## Prerequisites

The image that you created in [Lab 1a: Create a basic image](iot-ent-create-a-basic-image.md) installed on an IoT device.

## Customize the device

The steps in this lab are optional. Most OEM devices require at least one of the customizations in this lab, but it isn't required.

This section covers how to add:

- [Features on Demand](#add-a-feature-on-demand-fod-in-audit-mode)
- [Device drivers](#install-drivers-in-audit-mode)
- [Languages](#add-a-language-in-audit-mode)
- [Updates](#add-a-cumulative-update-in-audit-mode)
- [OEM software](#install-oem-software-in-audit-mode)

<!-- We will need two sections. One for over the air. Another using DISM. Only folks with a License agreement can download Languages and Optional Features ISO. See: https://learn.microsoft.com/en-us/windows-hardware/manufacture/desktop/languages-overview?view=windows-11&preserve-view=true#get-language-resources-languages-and-optional-features-iso -->
### Add a Feature on Demand (FOD) in Audit Mode

Features on Demand (FODs) are Windows feature packages that can be added at any time. Common features include language resources like handwriting recognition or other features like the .NET Framework (.NetFx3).

Device partners often include FODs in Windows images. A commonly added feature is .NET Framework 3.5 to support scenarios where the device is running an OEM application and that needs .NET Framework 3.5 support.

To add a Feature on Demand in audit mode, you need the FOD ISO either on a USB drive, or copied to your IoT device. Once you finish installing FODs, you can remove the ISO from your IoT device or remove the USB drive.

1. Mount the Feature on Demand (FOD) ISO on the Technician PC.
1. Locate the cab file for the FOD you're going to install. In this example, we use .NET Framework 3.5. The cab is named *Microsoft-Windows-NetFx3-OnDemand-Package~31bf3856ad364e35~amd64~~.cab*. You can view all the FOD .cab names at [Available Features on Demand](/windows-hardware/manufacture/desktop/features-on-demand-non-language-fod).
1. Copy the cab file to the IoT device in a folder called *C:\FOD*.
1. Add the FOD, from an Administrative Command Prompt:

   ```cmd
   Dism /online /add-package /packagepath:C:\FOD\Microsoft-Windows-NetFx3-OnDemand-Package~31bf3856ad364e35~amd64~~.cab 
   ```

1. Verify that the FOD is part of the image:

   ```cmd
    Dism /online /get-capabilities /format:table
    ```

    The output indicates the installation status for all FODs. Verify that the FODs you installed show as **Installed**.

    ```output
    -------------------------------------------------------- | -----------
    Capability Identity                                      | State
    -------------------------------------------------------- | -----------
    ...                                                      |
    NetFX3~~~~                                               | Installed
    ...                                                      |
    ```

See [Features on Demand](/windows-hardware/manufacture/desktop/features-on-demand-v2--capabilities) to learn more about Features on Demand, including how to add them to an offline mounted image.

### Install drivers in Audit Mode

Device partners might need to install more drivers for Windows in order to support the hardware of the IoT device. There are numerous ways to install drivers. The following two options show how to do an installation using the driver vendors supplied setup package and how to add the driver using DISM.

To add a driver, you have to have a driver supplied from a hardware vendor. The driver package could be distributed as an .msi, .exe, or .inf file. The process of adding a driver depends on how the driver is distributed.

#### Add the driver using vendors supplied setup package

Use this method if the driver supplied by the independent hardware vendor (IHV) is a simple MSI or EXE package. If you want auto driver installation, you can use an unattend file or scripting. The following steps outline an installation.

1. Gather the driver installer package provided by the IHV. A driver installer package is typically an MSI or EXE package.
1. Copy the package to a temporary location on the IoT device. In audit mode, the system is logged in locally as the local Administrator account. Run the installation MSI or EXE and follow the prompts.
1. **Optional** Remove the installation package from the temporary location.  

#### Add the driver using DISM

To use this method, the driver supplied by the IHV has to already be extracted out into INF, SYS, CAT, etc. files, or be an MSI or EXE package that can be extracted. This method can also be used to [add drivers to an offline mounted image](/windows-hardware/manufacture/desktop/add-and-remove-drivers-to-an-offline-windows-image).

1. If the driver is distributed as an MSI or EXE, copy the driver package provided by the IHV into a folder on the IoT device (we use *C:\Drivers* in our example). If the driver package is an .msi* or *.exe*, extract the contents into a folder.

1. Open an Administrative Command Prompt and use DISM to add all the drivers in the folder.

   ```cmd
   Dism /online /add-driver /driver:C:\Drivers /recurse
   ```

    The `/recurse` option adds all the drivers located in the *C:\Drivers* folder and its subfolders.

1. Reboot the device if prompted. When the PC reboots, make sure it reboots into audit mode.

### Add a language in Audit Mode

Device partners might need to add more languages to an image to enable a user to change languages. Adding languages during Audit mode is important for devices that don't have a persistent internet connection to download and install a language with the Settings app.

You can add more languages to your custom image by using DISM to install a language pack and the related Features on Demand. You can add languages in audit mode or to an offline mounted image. For more information, see [Languages overview](/windows-hardware/manufacture/desktop/add-language-packs-to-windows).

1. Mount the FOD ISO on your Technician PC. Your ISO might still be mounted if you added a FOD earlier in the lab.
1. Locate the cab file for the language pack you're going to install. In this example, we use French (fr-FR). The cab is named *Microsoft-Windows-Client-Language-Pack_x64_fr-fr.cab*.
1. Copy the cab file to the IoT device folder *C:\FOD*.
1. Add the language pack, from an Administrative Command Prompt:

   ```cmd
   Dism /online /add-package /packagepath:C:\FOD\Microsoft-Windows-Client-Language-Pack_x64_fr-fr.cab
   ```

1. **(OPTIONAL)** Locate the supporting language components for your language pack and copy them to *C:\FOD*. In this example, the cab files are:
   - *Microsoft-Windows-LanguageFeatures-Basic-fr-fr-Package~31bf3856ad364e35~amd64~~.cab*
   - *Microsoft-Windows-LanguageFeatures-OCR-fr-fr-Package~31bf3856ad364e35~amd64~~.cab*
   - *Microsoft-Windows-LanguageFeatures-Handwriting-fr-fr-Package~31bf3856ad364e35~amd64~~.cab*
   - *Microsoft-Windows-LanguageFeatures-TextToSpeech-fr-fr-Package~31bf3856ad364e35~amd64~~.cab*
   - *Microsoft-Windows-LanguageFeatures-Speech-fr-fr-Package~31bf3856ad364e35~amd64~~.cab*

    1. Add the FODs for your language pack:

    - *Microsoft-Windows-LanguageFeatures-Basic-fr-fr-Package~31bf3856ad364e35~amd64~~.cab*:

        ```cmd
        Dism /online /add-package /packagepath:C:\FOD\Microsoft-Windows-LanguageFeatures-Basic-fr-fr-Package~31bf3856ad364e35~amd64~~.cab
        ```

    - *Microsoft-Windows-LanguageFeatures-OCR-fr-fr-Package~31bf3856ad364e35~amd64~~.cab*:

       ```cmd
       Dism /online /add-package /packagepath:C:\FOD\Microsoft-Windows-LanguageFeatures-OCR-fr-fr-Package~31bf3856ad364e35~amd64~~.cab
       ```

    - *Microsoft-Windows-LanguageFeatures-Handwriting-fr-fr-Package~31bf3856ad364e35~amd64~~.cab*:

        ```cmd
        Dism /online /add-package /packagepath:C:\FOD\Microsoft-Windows-LanguageFeatures-Handwriting-fr-fr-Package~31bf3856ad364e35~amd64~~.cab
        ```

    - *Microsoft-Windows-LanguageFeatures-TextToSpeech-fr-fr-Package~31bf3856ad364e35~amd64~~.cab*:

        ```cmd
        Dism /online /add-package /packagepath:C:\FOD\Microsoft-Windows-LanguageFeatures-TextToSpeech-fr-fr-Package~31bf3856ad364e35~amd64~~.cab
        ```

    - *Microsoft-Windows-LanguageFeatures-Speech-fr-fr-Package~31bf3856ad364e35~amd64~~.cab*:

        ```cmd
        Dism /online /add-package /packagepath:C:\FOD\Microsoft-Windows-LanguageFeatures-Speech-fr-fr-Package~31bf3856ad364e35~amd64~~.cab
        ```

1. Add the new language to the language list in Windows, from an Administrative Windows PowerShell Prompt:

   ```powershell
   $OldList = Get-WinUserLanguageList
   $OldList.Add("fr-FR")
   Set-WinUserLanguageList -LanguageList $OldList   
   ```

   For more information, see [Set-WinUserLanguageList](/powershell/module/international/set-winuserlanguagelist)

### Add a cumulative update in Audit Mode

Device partners might need to update the OS image with the latest cumulative update (LCU) as part of the initial image build process. The update can be applied offline or online using DISM, or running the Microsoft Servicing Update (MSU) package directly.

#### Download an update

To add an update, you first download the most recent LCU from the [Microsoft Update Catalog](https://www.catalog.update.microsoft.com/Home.aspx). These steps can be performed on the Technician PC if the IoT device doesn't have internet connectivity, or if the device scenario requires never connecting to the internet.

1. Visit [Windows 11 Update History](https://support.microsoft.com/topic/windows-11-version-23h2-update-history-59875222-b990-4bd9-932f-91a5954de434) to see which updates are available for your Windows image.
1. In the upper left of the page, select your Windows build.
1. The left-hand navigation shows the most recent LCU's KB number. Select the latest KB name, which takes you to a KB article with some information about the release.
1. On the KB article page, locate the link for the Microsoft Update Catalog and select the link to open the download page in the catalog.
1. Download the MSU package from the catalog and save it to *C:\Packages* on the IoT device.

#### Install the update using the GUI

On the IoT device, select the Microsoft Servicing Update (MSU) package in File Explorer to start the installation and follow the steps provided on the GUI.

#### Install the update using DISM

You can install an LCU using DISM, which can be helpful if you're scripting the installation of the update. You can also use this method to add the update to an offline mounted image. For more information, see [Add updates to a Windows image](/windows-hardware/manufacture/desktop/servicing-the-image-with-windows-updates-sxs).

1. Use DISM to install the LCU on the IoT device, from an Administrative Command Prompt:

    ```cmd
    Dism /online /add-package /packagepath:C:\Packages\<package.msu>
    ```

### Install OEM software in Audit Mode

Device partners might need to install software in audit mode. This software can be Line of Business applications, tools, utilities, or any type of software that needs to be on the device before shipping. You can use Audit Mode to install software using methods that are available from the Windows desktop, and device partners should use the method that best aligns with their workflow.

Some things to consider:

- If an installed application is to become the shell experience for the device, follow the steps in lab #5 to set up Shell Launcher or Assigned Access. The features used depend on the type of application used for the shell.
  - Shell Launcher is used if a Win32 or .NET application is used as the shell.
  - Assigned Access is used if a UWP application is used as the shell.
- If the device experience is more like a customized desktop experience (for example, a hotel kiosk) where users are able to have access to the desktop, there are customization steps that can make it easier to ensure your device layout is preserved. For example, icon layout on the desktop and start menu can be preserved as part of the Sysprep process.  

## Next steps

With your image customized in audit mode, you can further customize the device experience. Lab 2 covers how to enable device lockdown features.

>[!div class="nextstepaction"]
>[Go to lab 2](iot-ent-device-lockdown-features.md)
