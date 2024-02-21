---
title: Package - Legacy Calculator App
titleSuffix: Windows IoT Enterprise
author: twarwick
ms.author: twarwick
ms.date: 01/31/2024
ms.topic: article
ms.service: windows-iot
ms.subservice: iot
description: Removable Package Details for Microsoft-Windows-win32calc
keywords: IoT Enterprise, removable packages, storage
---

# Legacy Calculator App

| Applies to                          |  Version            |
|:------------------------------------|:--------------------|
| Windows 10 IoT Enterprise LTSC 2021 | 19044.1741 or later |

## Description

Legacy calculator application

**Package Name:** Microsoft-Windows-win32calc

**Size:** Approximately 1,394 KB

> [!IMPORTANT]
>
> This feature is only supported on the Windows IoT Entrprise LTSC edition.  If you choose to remove any of this package from Windows IoT Enterprise, you must ensure that your solution does not rely on functionality of the removed package. You cannot restore the package without a full reinstall of Windows IoT Enterprise LTSC.  
> For more information, see [Removable Packages System Requirements](../Removable-Packages.md#system-requirements).

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
- [Device Optimization Overview](../Overview.md)
