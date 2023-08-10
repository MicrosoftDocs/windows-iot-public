---
title: Package - PrintBrm Command-Line tool
author: twarwick
ms.author: twarwick
ms.date: 03/30/2023
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: Removable Package Details for Microsoft-Windows-Printing-PremiumTools
keywords: IoT Enterprise, removable packages, storage
---

# PrintBRM Command-Line tool

> [!WARNING]
> THIS IS AN IN-PROGRESS ROUGH DRAFT. The wording and feature list may change before publishing.

| Applies to   |  Version            |
|:-------------|:--------------------|
| Windows 10 IoT Enterprise LTSC 2021 | 19044.1741 or later |
| Windows 11 IoT Enterprise LTSC 2024 | |

## Description

Print services migration command-line tool printbrm.exe

| Package Name | LTSC&nbsp;2021 | LTSC&nbsp;2024  |
|--------------|---------------:|----------------:|
| `Microsoft-Windows-Printing-PremiumTools`  | 381&nbsp;KB | TBD |

## Package Removal

1. To remove a specific package from the image type:

   ```powershell
   Dism.exe /Online /NoRestart /Disable-Feature /FeatureName:Microsoft-Windows-Printing-PremiumTools /PackageName:@Package
   ````

   To remove a package from an offline image mounted at `c:\offline` type:

   ```powershell
   Dism.exe /Image:c:\offline  /Disable-Feature /FeatureName:Microsoft-Windows-Printing-PremiumTools /PackageName:@Package
   ```

1. Optional: Use DISM /GetFeatureInfo to get the status of a removable package type:

   ```powershell
   Dism.exe /Online /Get-FeatureInfo /FeatureName:Microsoft-Windows-Printing-PremiumTools /PackageName:@Package
   ````

## File List

| File Name | Installed Location |
|-----------|--------------------|
| printbrmui.exe     | %windir%\system32\printbrmui.exe |
| printbrm.exe       | %windir%\system32\spool\tools\printbrm.exe |
| printbrmengine.exe | %windir%\system32\spool\tools\printbrmengine.exe |
| printbrmps.dll     | %windir%\system32\spool\tools\printbrmps.dll |

## More Resources

- [Removable Packages](/windows/iot/iot-enterprise/Optimize-Your-Device/Removable-Packages)
- [Reduce Disk Footprint](/windows/iot/iot-enterprise/Optimize-Your-Device/Reduce-Disk-Footprint)
- [Device Optimization Overview](/windows/iot/iot-enterprise/Optimize-Your-Device/Overview)
