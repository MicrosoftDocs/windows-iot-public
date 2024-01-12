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

| Applies to                          |  Version            |
|:------------------------------------|:--------------------|
| Windows 10 IoT Enterprise LTSC 2021 | 19044.1741 or later |

## Description

Print services migration command-line tool printbrm.exe

**Package Name:** Microsoft-Windows-Printing-PremiumTools

**Size:**  Approximately 381 KB

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

- [Removable Packages](../Removable-Packages.md)
- [Device Optimization Overview](../Overview.md)
