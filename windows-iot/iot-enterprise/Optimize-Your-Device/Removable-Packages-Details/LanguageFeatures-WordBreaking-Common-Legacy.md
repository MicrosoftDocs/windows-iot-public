---
title: Package - Language Word Breaking Legacy
author: twarwick
ms.author: twarwick
ms.date: 1/12/2023
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: Removable Package Details for LanguageFeatures_WordBreaking_Common_Legacy
keywords: IoT Enterprise, removable packages, storage
---

| Applies to                          |  Version            |
|:------------------------------------|:--------------------|
| Windows 10 IoT Enterprise LTSC 2021 | 19044.1741 or later |

# Package: Language Word Breaking Legacy

## Description
Legacy neutral word breaker, should only be needed in occasional application compatibility scenarios.

**Package Name:** LanguageFeatures-WordBreaking-Common-legacy  

**Size:** Approximately 1542 KB


## To remove a package using DISM

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
- [Removable Packages](/windows/iot/iot-enterprise/Optimize-Your-Device/Removable-Packages)
- [Reduce Disk Footprint](/windows/iot/iot-enterprise/Optimize-Your-Device/Reduce-Disk-Footprint)
- [Device Optimization Overview](/windows/iot/iot-enterprise/Optimize-Your-Device/Overview)
