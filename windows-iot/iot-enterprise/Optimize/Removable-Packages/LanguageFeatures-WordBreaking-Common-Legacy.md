---
title: Package - Language Word Breaking Legacy
titleSuffix: Windows IoT Enterprise
author: twarwick
ms.author: twarwick
ms.date: 01/31/2024
ms.topic: article
ms.service: windows-iot
ms.subservice: iot
description: Removable Package Details for LanguageFeatures_WordBreaking_Common_Legacy
keywords: IoT Enterprise, removable packages, storage
---

# Language Word Breaking Legacy

| Applies to                          |  Version            |
|:------------------------------------|:--------------------|
| Windows 10 IoT Enterprise LTSC 2021 | 19044.1741 or later |

## Description  

Legacy neutral word breaker, should only be needed in occasional application compatibility scenarios.

**Package Name:** LanguageFeatures-WordBreaking-Common-legacy  

**Size:** Approximately 1542 KB

> [!IMPORTANT]
>
> This feature is only supported on the Windows IoT Entrprise LTSC edition.  If you choose to remove any of this package from Windows IoT Enterprise, you must ensure that your solution does not rely on functionality of the removed package. You cannot restore the package without a full reinstall of Windows IoT Enterprise LTSC.  
> For more information, see [Removable Packages System Requirements](../Removable-Packages.md#system-requirements).

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

## File List

| File Name | Installed Location |
|-----------|--------------------|
| nlsdata0000.dll | %windir%\system32\nlsdata0000.dll |

## More Resources

- [Removable Packages](../Removable-Packages.md)
- [Device Optimization Overview](../Overview.md)
