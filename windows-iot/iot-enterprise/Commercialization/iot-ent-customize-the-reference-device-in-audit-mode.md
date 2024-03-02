---
description: Customize the reference device in Audit mode
title: Customize the reference device in Audit mode
ms.date: 12/10/2018
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

[Audit Mode](iot-ent-audit-mode-overview.md) allows you to customize Windows to image capture. Common audit mode customizations include installing Features on Demand (FODs), Drivers, Language Packs, and OEM software. This lab describes how to complete some of these common audit mode customizations.

Audit mode isn't necessarily the only way to implement these customizations. If the following examples don't fit into your workflow, explore the desktop deployment documentation for other alternatives.

For a fully automated approach to these steps, consider using the [Windows IoT Enterprise deployment framework](https://github.com/ms-iot/windows-iotent-deploy).

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

### Add a Feature on Demand (FOD) in Audit Mode

Features on Demand (FODs) are Windows feature packages that can be added at any time. Common features include language resources like handwriting recognition or other features like the .NET Framework (.NetFx3).

Device partners often include FODs in Windows images. A commonly added feature is .NET Framework 3.5 to support scenarios where the device is running an OEM application and that needs .NET Framework 3.5 support.

To add a Feature on Demand in audit mode, you need the FOD ISO either on a USB drive, or copied to your IoT device. Once you've finished installing FODs, you can remove the ISO from your IoT device or remove the USB drive.

1. Mount the Feature on Demand (FOD) ISO on the Technician PC.
1. Locate the cab file for the FOD you're going to install. In this example, we use .NET Framework 3.5. The cab is named `Microsoft-Windows-NetFx3-OnDemand-Package~31bf3856ad364e35~amd64~~.cab`. You can view all the FOD .cab names at [Available Features on Demand](/windows-hardware/manufacture/desktop/features-on-demand-non-language-fod).
1. Copy the cab file to the IoT device in a folder called C:\FoD.
1. Add the FOD. From an Administrative Command Prompt:

   ```cmd
   DISM.exe /online /add-package /packagepath:C:\FoD\Microsoft-Windows-NetFx3-OnDemand-Package~31bf3856ad364e35~amd64~~.cab 
   ```

1. Verify that the FOD is part of the image:

   ```cmd
    DISM.exe /online /get-capabilities /format:table
    ```

    The output indicates the installation status for all FODs. Verify that the FODs you installed show as **Installed**.

    ```text
    -------------------------------------------------------- | -----------
    Capability Identity                                      | State
    -------------------------------------------------------- | -----------
    ...                                                      |
    NetFX3~~~~                                               | Installed
    ...                                                      |
    ```

See [Features on Demand](/windows-hardware/manufacture/desktop/features-on-demand-v2--capabilities) to learn more about Features on Demand, including how to add them to an offline mounted image.

### Install drivers in Audit Mode

Device partners may need to install more drivers for Windows in order to support the hardware of the IoT device. There are numerous ways to install drivers. The following two options show how to do an installation using the driver vendors supplied setup package and an advanced method to add the driver using DISM.

To add a driver, you have to have a driver supplied from a hardware vendor. The driver package could be distributed as an .msi, .exe, or .inf file. The process of adding a driver depends on how the driver is distributed.

#### Simple method - manual installation

Use this method if the driver supplied by the independent hardware vendor (IHV) is a simple MSI or EXE package. If you want auto driver installation, you can use an unattend file or scripting. The following steps outline an installation.

1. Gather the driver installer package provided by the IHV. A driver installer package is typically an MSI or EXE package.
1. Copy the package to a temporary location on the IoT device. In audit mode, the system is logged in locally as the local Administrator account. Run the installation MSI or EXE and follow the prompts.
1. **Optional** Remove the installation package from the temporary location.  

#### Advanced method

To use this method, the driver supplied by the IHV has to already be extracted out into INF, SYS, CAT, etc. files, or be an MSI or EXE package that can be extracted. This method can also be used to [add drivers to an offline mounted image](/windows-hardware/manufacture/desktop/add-and-remove-drivers-to-an-offline-windows-image).

1. If the driver is distributed as an MSI or EXE, copy the driver package provided by the IHV into a folder on the IoT device (we use C:\Drivers in our example). If the driver package is a .msi or .exe, extract the contents into a folder.

1. Open an Administrative Command Prompt and use DISM to add all the drivers in the folder.

   ```cmd
   Dism /online /add-driver /driver:C:\Drivers /recurse
   ```

    The `/recurse` option adds all the drivers located in the C:\Drivers folder and its subfolders.

1. Reboot the device if prompted. When the PC reboots, make sure it reboots into audit mode.

### Add a language in Audit Mode

Device partners may need to add more languages to an image to enable a user to change languages. Adding languages during Audit mode is important for devices that may not have a persistent internet connection to download and install a language with the Settings app.

You can add more languages to your custom image by using DISM to install a language pack and the related Features on Demand. You can add languages in audit mode or to an offline mounted image. For more information, see [Languages overview](/windows-hardware/manufacture/desktop/add-language-packs-to-windows).

1. Mount the Feature on Demand ISO on your Technician PC. Your ISO might still be mounted if you added a FOD earlier in the lab.
1. Mount the Language Pack ISO on your Technician PC.
1. Add a language pack to your image. In this example, we use French (fr-FR). From an Administrative Command Prompt:

   ```cmd
   Dism /Add-Package /online /packagepath:"E:\x64\langpacks\Microsoft-Windows-Client-Language-Pack_x64_fr-fr.cab"
   ```

    Where E: is the mounted Language Pack ISO

1. OPTIONAL Install the supporting language components for your language pack.

    ```cmd
    DISM /online /add-package /packagepath:D:Microsoft-Windows-LanguageFeatures-Basic-fr-fr-Package~31bf3856ad364e35~amd64~~.cab
    ```

1. (enter description)

   ```cmd
   DISM /online /add-package /packagepath:D:Microsoft-Windows-LanguageFeatures-OCR-fr-fr-Package~31bf3856ad364e35~amd64~~.cab 
   ```
1. (enter description)
   ```cmd
   DISM /online /add-package /packagepath:D:Microsoft-Windows-LanguageFeatures-Handwriting-fr-fr-Package~31bf3856ad364e35~amd64~~.cab 
   ```
1. (enter description)
   ```cmd
   DISM /online /add-package /packagepath:D:Microsoft-Windows-LanguageFeatures-TextToSpeech-fr-fr-Package~31bf3856ad364e35~amd64~~.cab
   ```
1. (enter description)
    ```cmd
    DISM /online /add-package /packagepath:D:Microsoft-Windows-LanguageFeatures-Speech-fr-fr-Package~31bf3856ad364e35~amd64~~.cab 
    ```

    Where D: is the mounted FOD ISO

1. (enter description)

   ```powershell
   $OldList = Get-WinUserLanguageList
   $OldList.Add("fr-FR")
   Set-WinUserLanguageList -LanguageList $OldList   
   ```
   For more information, see [Set-WinUserLanuageList](/powershell/module/international/set-winuserlanguagelist)

### Add a cumulative update in Audit Mode

Device partners may need to update the OS image with the latest cumulative update (LCU) as part of the initial image build process. The update can be applied offline using DISM or online using DISM or running the MSU package directly. The following two options show how to do an installation using the MSU or an advanced installation using DISM.  

To add an update, you first download the most recent LCU from the [Microsoft Update Catalog](https://www.catalog.update.microsoft.com/Home.aspx), and then install it. You can install the update through the GUI or the command line.

In the following steps, we show you how to install an LCU using a .msu from the Microsoft Update catalog.

#### Download an update

These steps can be performed on the Technician PC if the IoT device doesn't have internet connectivity, or if the device scenario requires never connecting to the internet.

1. Visit [Windows Update History](https://support.microsoft.com/help/4464619) to see which updates are available for your Windows image.
1. In the upper left of the page, select your Windows build. Select on, for example, Windows, version 1809.
1. In the left-hand navigation, you see a section called **In this release**. This section shows the most recent LCU's KB number. Select on the latest KB name, which takes you to a KB article with some information about the release.
1. On the KB article page, locate the link for the Microsoft Update Catalog and select the link to open the download page in the catalog.
1. Download the MSU package from the catalog and save it to C:\Packages on the IoT device.

#### Install an update, simple method

After you've downloaded an update, double select the update in File Explorer to start the installation.

#### Install an update, advanced method

You can install an LCU using DISM, which can be helpful if you're scripting the installation of the update. You can also use this method to add the update to an offline mounted image. For more information, see [Add updates to a Windows image](/windows-hardware/manufacture/desktop/servicing-the-image-with-windows-updates-sxs).

Use DISM to install the LCU:

From an Administrative Command Prompt:

```cmd
Dism /online /add-package /packagepath:C:\Packages\<package.msu>
```

### Install OEM software in Audit Mode

Device partners may need to install software in audit mode. This software might be Line of Business applications, tools, utilities, or any type of software that needs to be on the device prior to shipping. You can use Audit Mode to install software using methods that are available from the Windows desktop, and device partners should use the method that best aligns with their workflow.

Some things to consider:

- If an installed application is to become the shell experience for the device, follow the steps in lab #5 to set up Shell Launcher or Assigned Access. The features used depend on the type of application used for the shell.
  - Shell Launcher is used if a Win32 or .NET application is used as the shell.
  - Assigned Access is used if a UWP application is used as the shell.
- If the device experience is more like a customized desktop experience (for example, a hotel kiosk) where users are able to have access to the desktop, there are customization steps that can make it easier to ensure your device layout is preserved. For example, icon layout on the desktop and start menu can be preserved as part of the Sysprep process.  
- This type of installation has to be done in audit mode, and can't be done on an offline mounted image.

## Next steps

With your image customized in audit mode, you can further customize the device experience. Lab 2 covers how to enable device lockdown features.

>[!div class="nextstepaction"]
>[Go to lab 2](iot-ent-device-lockdown-features.md)
