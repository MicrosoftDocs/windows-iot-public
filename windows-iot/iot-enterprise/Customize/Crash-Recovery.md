---
title: Suppress Crash Screens
description: Suppress Crash Screens
author: TerryWarwick
ms.author: twarwick
ms.service: windows-iot
ms.subservice: iot
ms.date: 09/10/2024
ms.topic: How-To


---
# Suppress Crash Screens

Windows for IoT offers several methods to protect your branding on public-facing devices by suppressing crash screens and boot errors. 

> [!NOTE]
> BCDEdit is the primary tool for editing the startup configuration and is on your development computer in the %WINDIR%\System32 folder. You have administrator rights for it. BCDEdit is included in a typical Windows Preinstallation Environment (Windows PE) 4.0. You can download it from the [BCDEdit Commands for Boot Environment](/previous-versions/windows/hardware/design/dn653986(v=vs.85)) in the Microsoft Download Center if needed.

## Errors During Boot Phase

The **noerrordisplay** switch takes care of exhaustively suppressing all error display during the boot phase.
For example, if **noerrordisplay** is on, and if the boot manager hits a *WinLoad Error* or *Bad Disk Error*, the system displays a black screen and require manual reset.
1. Open a command prompt as an administrator.
1. Run the following command to suppress error display during boot.

   ```cmd
   bcdedit.exe -set {bootmgr} noerrordisplay on
   ```

## Exception Error

To ensure that there's no crash screen if Windows encounters an error that it can't recover from, enable the [DisplayDisabled](/windows-hardware/customize/desktop/unattend/microsoft-windows-embedded-bootexp-displaydisabled) setting using [Unattend](/windows-hardware/customize/enterprise/unbranded-boot#configure-unbranded-boot-using-unattend).

You can also configure the Unattend settings in the **Microsoft-Windows-Embedded-BootExp** component to add Unbranded Boot features to your image during the design or imaging phase. You can manually create an Unattend answer file or use [Windows System Image Manager (Windows SIM)](/windows-hardware/customize/desktop/wsim/windows-system-image-manager-technical-reference) to add the appropriate settings to your answer file. For more information about the Unbranded Boot settings and XML examples, see the settings in [Microsoft-Windows-Embedded-BootExp](/windows-hardware/customize/desktop/unattend/microsoft-windows-embedded-bootexp).

## Related articles

- [Unbranded Boot](unbranded-boot.md)
