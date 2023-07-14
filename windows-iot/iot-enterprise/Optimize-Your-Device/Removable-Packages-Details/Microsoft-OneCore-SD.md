---
title: Package - SD
author: twarwick
ms.author: twarwick
ms.date: 03/30/2023
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: Removable Package Details for SD
keywords: IoT Enterprise, removable packages, storage
---

# SD

**Applies to:**

- Windows&nbsp;11&nbsp;IoT&nbsp;Enterprise&nbsp;LTSC&nbsp;vNext

## Description

<fill in the blank>

**Package Name:** Microsoft-OneCore-SD

**Size:** Approximately <fill in the blank>

## Package Removal

1. To remove a specific package from the image type:

   ```powershell
   Dism.exe /Online /NoRestart /Disable-Feature /FeatureName:<fill in the blank> /PackageName:@Package
   ````

   To remove a package from an offline image mounted at `c:\offline` type:

   ```powershell
   Dism.exe /Image:c:\offline  /Disable-Feature /FeatureName:<fill in the blank> /PackageName:@Package
   ```

1. Optional: Use DISM /GetFeatureInfo to get the status of a removable package type:

   ```powershell
   Dism.exe /Online /Get-FeatureInfo /FeatureName:<fill in the blank> /PackageName:@Package
   ````

## File List

| File Name | Installed Location |
|-----------|--------------------|
| <fill in the blank>| <fill in the blank>  |

## More Resources

- [Removable Packages](/windows/iot/iot-enterprise/Optimize-Your-Device/Removable-Packages)
- [Reduce Disk Footprint](/windows/iot/iot-enterprise/Optimize-Your-Device/Reduce-Disk-Footprint)
- [Device Optimization Overview](/windows/iot/iot-enterprise/Optimize-Your-Device/Overview)
