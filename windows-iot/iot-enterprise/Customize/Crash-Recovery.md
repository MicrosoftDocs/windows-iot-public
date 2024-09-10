---
title: Suppress Blue Screens
description: Suppress Blue Screens
author: TerryWarwick
ms.author: twarwick
ms.service: windows-iot
ms.subservice: iot
ms.date: 09/10/2024
ms.topic: How-To


---
# Suppress Blue Screens

Windows IoT Enterprise enables you to suppress Blue Screen errors to protect your branding on public-facing devices. Suppressing Blue Screen errors will hide the Blue Screen and automatically reboot the device.

## Suppress Blue Screens through Unattend

To suppress Blue Screens through the Unattend method, enable the **DisplayDisabled** setting of the **Microsoft-Windows-Embedded-BootExp** component in the [unattend.xml answer file](/windows-hardware/manufacture/desktop/update-windows-settings-and-scripts-create-your-own-answer-file-sxs) applied by Windows during installation. 

You can use [Windows System Image Manager (Windows SIM)](/windows-hardware/customize/desktop/wsim/windows-system-image-manager-technical-reference) to help create your answer file with the DisplayDisabled setting enabled. 

For XML examples, see the reference on the [DisplayDisabled](/windows-hardware/customize/desktop/unattend/microsoft-windows-embedded-bootexp-displaydisabled) Unattend setting.

## Suppress Blue Screens through Registry

You can also suppress Blue Screens on a device by setting the ```HKLM\System\CurrentControlSet\Control\CrashControl\DisplayDisabled``` registry key on the device:

1. Open a Command Prompt with Administrator privileges
2. Enter the command below: 

```cmd
reg add HKLM\System\CurrentControlSet\Control\CrashControl /v DisplayDisabled /t REG_DWORD /d 0
```

## Related articles

- [Unbranded Boot](unbranded-boot.md)
