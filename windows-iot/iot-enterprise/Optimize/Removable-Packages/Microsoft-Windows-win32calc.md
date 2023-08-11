---
title: Package - Legacy Calculator App
author: twarwick
ms.author: twarwick
ms.date: 03/30/2023
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: Removable Package Details for Microsoft-Windows-win32calc
keywords: IoT Enterprise, removable packages, storage
---

# Legacy Calculator App

> [!WARNING]
> THIS IS AN IN-PROGRESS ROUGH DRAFT. The wording and feature list may change before publishing.

| Applies to   |  Version            |
|:-------------|:--------------------|
| Windows 10 IoT Enterprise LTSC 2021 | 19044.1741 or later |
| Windows 11 IoT Enterprise LTSC 2024 | |

## Description

Legacy calculator application

| Package Name | LTSC&nbsp;2021 | LTSC&nbsp;2024  |
|--------------|---------------:|----------------:|
| `Microsoft-Windows-win32calc`  | 1,394&nbsp;KB | TBD |

## Package Removal

1. To remove a specific package from the image type:

   ```powershell
   Dism.exe /Online /NoRestart /Disable-Feature /FeatureName:Microsoft-Windows-win32calc /PackageName:@Package
   ````

   To remove a package from an offline image mounted at `c:\offline` type:

   ```powershell
   Dism.exe /Image:c:\offline  /Disable-Feature /FeatureName:Microsoft-Windows-win32calc /PackageName:@Package
   ```

1. Optional: Use DISM /GetFeatureInfo to get the status of a removable package type:

   ```powershell
   Dism.exe /Online /Get-FeatureInfo /FeatureName:Microsoft-Windows-win32calc /PackageName:@Package
   ````

## File List

| File Name | Installed Location |
|-----------|--------------------|
| calculator.lnk | %programdata%\microsoft\windows\start menu\programs\accessories\calculator.lnk  |
| win32calc.exe  | %windir%\system32\win32calc.exe |

## More Resources

- [Removable Packages](../Removable-Packages.md)
- [Reduce Disk Footprint](../Reduce-Disk-Footprint.md)
- [Device Optimization Overview](../Overview.md)
