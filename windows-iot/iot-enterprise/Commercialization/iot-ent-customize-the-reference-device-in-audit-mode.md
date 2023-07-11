---
description: Customize the reference device in Audit mode
title: Customize the reference device in Audit mode
ms.date: 12/10/2018
ms.topic: article
author: TerryWarwick
ms.author: twarwick
ms.prod: windows-iot
ms.technology: iot

---

# Lab 1b: Customize the reference device in Audit Mode

In [Lab 1a](iot-ent-create-a-basic-image.md), you installed Windows 10 IoT Enterprise onto an IoT device and booted into audit mode. In this lab, we'll show you how to customize your device from audit mode.

>[!Tip]
>Most customizations in this lab can be made to an offline mounted Windows image, as well as in Audit mode. See [Modify a Windows image using DISM](/windows-hardware/manufacture/desktop/mount-and-modify-a-windows-image-using-dism) for more information.

## What is Audit Mode?

[Audit Mode](iot-ent-audit-mode-overview.md) allows you to customize Windows to image capture. Common audit mode customizations include installing Features on Demand (FODs), Drivers, Language Packs, and OEM software. This lab describes how to complete some of these common audit mode customizations. 

Audit mode isn't necessarily the only way to implement these customizations. If the examples below do not fit into your workflow, explore the desktop deployment documentation for other alternatives. 

For a fully automated approach to these steps consider using the [Windows 10 IoT Enterprise deployment framework](https://github.com/ms-iot/windows-iotent-deploy).

## Prerequisites

The image that you created in [Lab 1a: Create a basic image](iot-ent-create-a-basic-image.md) installed on an IoT device.

## Customize the device

The steps in this lab are optional. Most OEM devices will require at least one of the customizations in this lab, but if you don't see the need to make any audit mode customizations, you don't have to. 

This section covers how to add:
- [Features on Demand](#add-a-feature-on-demand-fod-in-audit-mode)
- [Device drivers](#install-drivers-in-audit-mode)
- [Languages](#add-a-language-in-audit-mode)
- [Updates](#add-a-cumulative-update-in-audit-mode)
- [OEM software](#install-oem-software-in-audit-mode)

### Add a Feature on Demand (FOD) in Audit Mode 

Features on Demand (FODs) are Windows feature packages that can be added at any time. Common features include language resources like handwriting recognition or other features like the .NET Framework (.NetFx3).
 
Device partners will often include FODs in Windows images. A commonly added feature is .NET Framework 3.5 to support scenarios where the device is running an OEM application and that needs .NET Framework 3.5 support. 

To add a Feature on Demand in audit mode, you'll need the FOD ISO either on a USB drive, or copied to your IoT device. Once you've finished installing FODs, you can remove the ISO from your IoT device or remove the USB drive.

1. Mount the Feature on Demand (FOD) ISO on the Technician PC. 
2. Locate the cab file for the FOD you're going to install. In this example we'll use .NET Framework 3.5. The cab is named `Microsoft-Windows-NetFx3-OnDemand-Package~31bf3856ad364e35~amd64~~.cab`. You can view all the FOD .cab names at [Available Features on Demand](/windows-hardware/manufacture/desktop/features-on-demand-non-language-fod).
3. Copy the cab file to the IoT device in a folder called C:\FoD. 
4. Add the FOD. From an Administrative Command Prompt:

    ```
    DISM.exe /online /add-package /packagepath:C:\FoD\Microsoft-Windows-NetFx3-OnDemand-Package~31bf3856ad364e35~amd64~~.cab 
    ```
5. Verify that the FOD is part of the image:

    ```
    DISM.exe /online /get-capabilities /format:table
    ```

    The output indicates the installation status for all FODs. Verify that the FODs you installed show as **Installed**.

    ```
    -------------------------------------------------------- | -----------
    Capability Identity                                      | State
    -------------------------------------------------------- | -----------
    ...                                                      |
    NetFX3~~~~                                               | Installed
    ...     	                                             |
    ```

See [Features on Demand](/windows-hardware/manufacture/desktop/features-on-demand-v2--capabilities.md) to learn more about Features on Demand, including how to add them to an offline mounted image.

### Install drivers in Audit Mode 

Device partners may need to install additional drivers for Windows in order to support the hardware of the IoT device. There are numerous ways to install drivers. Two options below show how to do a simple installation using the driver vendors supplied setup package and an advanced method to add the driver using DISM. 

To add a driver, you'll have to have a driver supplied from a hardware vendor. The driver package could be distributed as an .msi, .exe, or .inf file. The process of adding a driver depends on how the driver is distributed.

#### Simple method - manual installation

Use this method if the driver supplied by the independent hardware vendor (IHV) is a simple MSI or EXE package. If you want auto driver installation, you can use unattend files or through scripting. The steps below outline a simple installation. 

1. Gather the driver installer package provided by the IHV. This is often an installation MSI or EXE package. 
2. Copy the package to a temporary location on the IoT device. In audit mode, the system is logged in locally as the local Administrator account. Run the installation MSI or EXE and follow the prompts. 
2. **Optional** Remove the installation package from the temporary location.  

#### Advanced method 

To use this method, the driver supplied by the IHV has to already be extracted out into INF, SYS, CAT, etc. files, or be an MSI or EXE package that can be extracted. This method can also be used to [add drivers to an offline mounted image](/windows-hardware/manufacture/desktop/add-and-remove-drivers-to-an-offline-windows-image).

1. If the driver is distributed as an MSI or EXE, copy the driver package provided by the IHV into a folder on the IoT device (we'll use C:\Drivers in our example). If the driver package is an .msi or .exe, extract the contents into a folder.

2. Open an Administrative Command Prompt and use DISM to add all the drivers in the folder.

    ```
    Dism /online /add-driver /driver:C:\Drivers /recurse
    ```

    The `/recurse` option will add all the drivers located in the C:\Drivers folder and its subfolders.
 
3. Reboot the device if prompted. When the PC reboots, make sure it reboots into audit mode.

### Add a language in Audit Mode

Device partners may need to add additional languages to an image to enable a user to change launguages. This is particularly important for devices that may not have a persistent internet connection to download and install a language with the Settings app. 

You can add additional languages to your custom image by using DISM to install a language pack and the related Features on Demand. You can add languages in audit mode or to an offline mounted image. See [Languages overview](/windows-hardware/manufacture/desktop/add-language-packs-to-windows) for more information.

1. Mount the Feature on Demand ISO on your Technician PC. This might still be mounted if you added a FOD earlier in the lab.
2. Mount the Language Pack ISO on your Technician PC. 
3. Add a language pack to your image. In this example, we'll use French (fr-FR). From an Administrative Command Prompt:

    ```
    Dism /Add-Package /online /packagepath:"E:\x64\langpacks\Microsoft-Windows-Client-Language-Pack_x64_fr-fr.cab
    ```

    Where E: is the mounted Language Pack ISO    
 
4. Install the language FODs for your language pack.
    
    ```
    DISM /online /add-package /packagepath:D:Microsoft-Windows-LanguageFeatures-Basic-fr-fr-Package~31bf3856ad364e35~amd64~~.cab /packagepath:D:Microsoft-Windows-LanguageFeatures-OCR-fr-fr-Package~31bf3856ad364e35~amd64~~.cab /packagepath:D:Microsoft-Windows-LanguageFeatures-Handwriting-fr-fr-Package~31bf3856ad364e35~amd64~~.cab /packagepath:D:Microsoft-Windows-LanguageFeatures-TextToSpeech-fr-fr-Package~31bf3856ad364e35~amd64~~.cab /packagepath:D:Microsoft-Windows-LanguageFeatures-Speech-fr-fr-Package~31bf3856ad364e35~amd64~~.cab 
    ```
    Where D: is the mounted FOD ISO

### Add a cumulative update in Audit Mode

Device partners may need to update the OS image with the latest cumulative update (LCU) as part of the initial image build process. The update can be applied offline using DISM or online using DISM or running the MSU package directly. Two options below show how to do a simple installation using the MSU or an advanced installation using DISM.  

To add an update, you first download the most recent LCU from the Microsoft Update Catalog: https://www.catalog.update.microsoft.com/Home.aspx, and then install it. You can install the update through the GUI or the command line.

Below, we'll show you how to install an LCU using an .msu from the Microsoft Update catalog. 

#### Download an update

These steps can be performed on the Technician PC if the IoT device does not have internet connectivity, or if the device scenario requires never connecting to the internet.

1. Visit [Windows 10 Update History](https://support.microsoft.com/en-us/help/4464619) to see which updates are available for your Windows image.
2. In the upper left of the page select your Windows 10 build. Click on, for example, Windows 10, version 1809. 
3. In the left-hand navigation, you'll see a section called **In this release**. This section shows the most recent LCU's KB number. Click on the latest KB name, which will take you to a KB article with some information about the release.
4. On the KB article page, locate the link for the Microsoft Update Catalog and click the link. This will take you to the download page in the catalog. 
5. Download the MSU package from the catalog and save it to C:\Packages on the IoT device.

#### Install an update, simple method

After you've downloaded an update, double click the update in File Explorer to start the installation.

#### Install an update, advanced method 

You can install an LCU using DISM. This can be helpful if you're scripting the installation of the update. You can also use this method to add the update to an offline mounted image. See [Add updates to a Windows image](/windows-hardware/manufacture/desktop/servicing-the-image-with-windows-updates-sxs) for more information.

Use DISM to install the LCU:

From an Administrative Command Prompt:

```
Dism /online /add-package /packagepath:C:\Packages\<package.msu>
```

### Install OEM software in Audit Mode 

Device partners may need to install software in audit mode. This software might be Line of Business applications, tools, utilities, or any type of software that needs to be on the device prior to shipping. You can use Audit Mode to install software using methods that are available from the Windows desktop, and device partners should use the method that best aligns with their workflow. See 

Some things to consider: 
 
- If an installed application is to become the shell experience for the device, follow the steps in lab #5 to setup Shell Launcher or Assigned Access. The features used depend on the type of application that will become the shell. 
    - Shell Launcher is used if a Win32 or .NET application will be used as the shell. 
    - Assigned Access is used if a UWP application will be used as the shell.
- If the device experience is more like a customized desktop experience (for example, a hotel kiosk) where users are able to have access to the desktop, there are customization steps that can make it easier to ensure your device layout is preserved. For example, icon layout on the desktop and start menu can be preserved as part of the Sysprep process.  
- This type of installation has to be done in audit mode, and can't be done on an offline mounted image.

## Next steps

With your image customized in audit mode, you can further customize the device experience. Lab 2 covers how to enable device lockdown features.

>[!div class="nextstepaction"]
>[Go to lab 2](iot-ent-device-lockdown-features.md)