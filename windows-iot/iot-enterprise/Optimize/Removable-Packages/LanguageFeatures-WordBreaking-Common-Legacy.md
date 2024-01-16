---
title: Package - Language Word Breaking Legacy
author: twarwick
ms.author: twarwick
ms.date: 03/30/2023
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: Removable Package Details for LanguageFeatures_WordBreaking_Common_Legacy
keywords: IoT Enterprise, removable packages, storage
---

# Language Word Breaking Legacy

Applies to:  
✅ Windows 11 IoT Enterprise LTSC 2024  
✅ Windows 10 IoT Enterprise LTSC 2021 (19044.1741 or later)  

## Package Description  

Package: **LanguageFeatures-Wordbreaking-Common-legacy** </br> Legacy neutral word breaker should only be needed in occasional application compatibility scenarios.

## Package Removal

1. To remove a specific package from the image type:

   ```powershell
   Dism.exe /Online /NoRestart /Disable-Feature /FeatureName:LanguageFeatures-WordBreaking-Common-legacy /PackageName:@Package
   ````

   To remove a package from an offline image mounted at `c:\offline` type:

   ```powershell
   Dism.exe /Image:c:\offline  /Disable-Feature /FeatureName:LanguageFeatures-WordBreaking-Common-legacy /PackageName:@Package
   ```

1. Optional: Use DISM /GetFeatureInfo to get the status of a removable package type:

   ```powershell
   Dism.exe /Online /Get-FeatureInfo /FeatureName:LanguageFeatures-WordBreaking-Common-legacy /PackageName:@Package
   ````

## Package Details

### Package Size

| Release                             |   x64     |    ARM64    |
|-------------------------------------|:---------:|:-----------:|
| Windows 11 IoT Enterprise LTSC 2024 | 1,568 KB  | 1,765 KB    |
| Windows 10 IoT Enterprise LTSC 2021 | 1542 KB   |             |

### File List

| File Name | Installed Location |
|-----------|--------------------|
| nlsdata0000.dll | %windir%\system32\nlsdata0000.dll |

## More Resources

- [Removable Packages](../Removable-Packages.md)
- [Device Optimization Overview](../Overview.md)
