---
title: Package - Defragmentation User Experience
author: twarwick
ms.author: twarwick
ms.date: 03/30/2023
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: Removable Package Details for Defragmentation User Experience
keywords: IoT Enterprise, removable packages, storage
---

# Defragmentation User Experience

> [!WARNING]
> THIS IS AN IN-PROGRESS ROUGH DRAFT. The wording and feature list may change before publishing.

| Applies to   |  Version            |
|:-------------|:--------------------|
| Windows 11 IoT Enterprise LTSC 2024 | |

## Description

<fill in the blank>

| Package Name | LTSC&nbsp;2021 | LTSC&nbsp;2024  |
|--------------|---------------:|----------------:|
| `Microsoft-Windows-Defrag-UI` | TBD | TBD |

## Package Removal

1. To remove a specific package from the image type:

   ```powershell
   Dism.exe /Online /NoRestart /Disable-Feature /FeatureName:Microsoft-Windows-Defrag-UI /PackageName:@Package
   ````

   To remove a package from an offline image mounted at `c:\offline` type:

   ```powershell
   Dism.exe /Image:c:\offline  /Disable-Feature /FeatureName:Microsoft-Windows-Defrag-UI /PackageName:@Package
   ```

1. Optional: Use DISM /GetFeatureInfo to get the status of a removable package type:

   ```powershell
   Dism.exe /Online /Get-FeatureInfo /FeatureName:Microsoft-Windows-Defrag-UI /PackageName:@Package
   ````

## File List

| File Name | Installed Location |
|-----------|--------------------|
| <fill in the blank>| <fill in the blank>  |

## More Resources

- [Removable Packages](/windows/iot/iot-enterprise/Optimize-Your-Device/Removable-Packages)
- [Reduce Disk Footprint](/windows/iot/iot-enterprise/Optimize-Your-Device/Reduce-Disk-Footprint)
- [Device Optimization Overview](/windows/iot/iot-enterprise/Optimize-Your-Device/Overview)
