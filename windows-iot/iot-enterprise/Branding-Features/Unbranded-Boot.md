---
title: Unbranded Boot and Errors
author: rsameser
ms.author: riameser
ms.date: 2/2/2021
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: Learn about the Unbranded Boot Feature in Windows 10 IoT Enterprise.
keywords: Branding, Unbranded Boot
---

# Unbranded Boot and Errors
[Unbranded Boot](https://docs.microsoft.com/windows-hardware/customize/enterprise/unbranded-boot) enables you to suppress Windows elements that appear when Windows starts or resumes and can suppress the crash screen when Windows encounters an error that it cannot recover from.

## Turn on Unbranded Boot settings
Unbranded Boot is an optional component and is not enabled by default in Windows 10. It must be enabled prior to configuring. You can turn on Unbranded Boot by using [Control Panel](https://docs.microsoft.com/windows-hardware/customize/enterprise/unbranded-boot#turn-on-unbranded-boot-by-using-control-panel).

> [!NOTE]
>
> If Windows has already been installed you cannot apply a provisioning package to configure Unbranded Boot; instead you must use BDCEdit to configure Unbranded boot if Windows is installed.
>
> BCDEdit is the primary tool for editing the startup configuration and is on your development computer in the %WINDIR%\System32 folder. You have administrator rights for it. BCDEdit is included in a typical Windows Preinstallation Environment (Windows PE) 4.0. You can download it from the [BCDEdit Commands for Boot Environment](https://docs.microsoft.com/previous-versions/windows/hardware/design/dn653986(v=vs.85)) in the Microsoft Download Center if needed.

## Configure Unbranded Boot
There are multiple ways to configure Unbranded Boot. Use the method that is appropriate for your organization.

* [BCDEdit](https://docs.microsoft.com/windows-hardware/customize/enterprise/unbranded-boot#configure-unbranded-boot-settings-at-runtime-using-bcdedit)
* [Unattend](https://docs.microsoft.com/windows-hardware/customize/enterprise/unbranded-boot#configure-unbranded-boot-using-unattend)
* [Deployment Image Servicing and Management (DISM)](https://docs.microsoft.com/windows-hardware/customize/enterprise/unbranded-boot#customize-the-boot-screen-using-windows-configuration-designer-and-deployment-image-servicing-and-management-dism)
* [Microsoft-Windows-Embedded-BootExp](https://docs.microsoft.com/windows-hardware/customize/desktop/unattend/microsoft-windows-embedded-bootexp)

## Suppress Crash Screens
Microsoft offers Windows 10 IoT Enterprise customers methods to manage crash screens.

### Errors During Boot Phase
The **noerrordisplay** switch takes care of exhaustively suppressing all error display during the boot phase.

For example, if **noerrordisplay** to on, and if the boot manager hits a *WinLoad Error* or *Bad Disk Error*, the system will sit at a black screen and require manual reset.

Review [Configure Unbranded Boot settings at runtime using BCDEdit](https://docs.microsoft.com/windows-hardware/customize/enterprise/unbranded-boot#configure-unbranded-boot-settings-at-runtime-using-bcdedit) to enable the **noerrordisplay** setting.

> [!NOTE]
>
> BCDEdit is the primary tool for editing the startup configuration and is on your development computer in the %WINDIR%\System32 folder. You have administrator rights for it. BCDEdit is included in a typical Windows Preinstallation Environment (Windows PE) 4.0. You can download it from the [BCDEdit Commands for Boot Environment](https://docs.microsoft.com/previous-versions/windows/hardware/design/dn653986(v=vs.85)) in the Microsoft Download Center if needed.


### Exception Error
To ensure that there is no crash screen if Windows encounters an error it cannot recover from, enable the [DisplayDisabled](https://docs.microsoft.com/windows-hardware/customize/desktop/unattend/microsoft-windows-embedded-bootexp-displaydisabled) setting using [Unattend](https://docs.microsoft.com/windows-hardware/customize/enterprise/unbranded-boot#configure-unbranded-boot-using-unattend).

You can also configure the Unattend settings in the Microsoft-Windows-Embedded-BootExp component to add Unbranded Boot features to your image during the design or imaging phase. You can manually create an Unattend answer file or use Windows System Image Manager (Windows SIM) to add the appropriate settings to your answer file. For more information about the Unbranded Boot settings and XML examples, see the settings in [Microsoft-Windows-Embedded-BootExp](https://docs.microsoft.com/windows-hardware/customize/desktop/unattend/microsoft-windows-embedded-bootexp).

## Additional Resources
* [Replace the startup logo](https://docs.microsoft.com/windows-hardware/customize/enterprise/unbranded-boot#replace-the-startup-logo)
* [Configure Components and Settings in an Answer File](https://docs.microsoft.com/windows-hardware/customize/desktop/wsim/configure-components-and-settings-in-an-answer-file).
