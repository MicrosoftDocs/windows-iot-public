---
title: Package - 3D Audio HRTF Data
titleSuffix: Windows IoT Enterprise
author: TerryWarwick
ms.author: twarwick
ms.date: 05/22/2024
ms.topic: reference
ms.service: windows-iot
ms.subservice: iot
description: Removable Package Details for 3D Audio HRTF Data
keywords: IoT Enterprise, removable packages, storage
---

# 3D Audio HRTF Data

Applies to:  
✅ Windows 11 IoT Enterprise LTSC 2024  
⛔ Windows 10 IoT Enterprise LTSC 2021

## Package Description

Package: **Microsoft-Windows-3DAudio-HrtfData** </br>  3D Audio Head-related transfer function (HRTF) also known as Spatial Sound. For more information, see [Spatial Sound for App Developers](/windows/win32/coreaudio/spatial-sound).

> [!IMPORTANT]
>
> This feature is only supported on the Windows IoT Enterprise LTSC edition.  If you choose to remove any of this package from Windows IoT Enterprise, you must ensure that your solution does not rely on functionality of the removed package. You cannot restore the package without a full reinstall of Windows IoT Enterprise LTSC.  
> For more information, see [Removable Packages System Requirements](../Removable-Packages.md#system-requirements).

## Package Removal

1. To remove a specific package from the image type:

   ```powershell
   Dism.exe /Online /NoRestart /Disable-Feature /FeatureName:Microsoft-Windows-3DAudio-HrtfData /PackageName:@Package
   ````

   To remove a package from an offline image mounted at `c:\offline` type:

   ```powershell
   Dism.exe /Image:c:\offline  /Disable-Feature /FeatureName:Microsoft-Windows-3DAudio-HrtfData /PackageName:@Package
   ```

1. Optional: Use DISM /GetFeatureInfo to get the status of a removable package type:

   ```powershell
   Dism.exe /Online /Get-FeatureInfo /FeatureName:Microsoft-Windows-3DAudio-HrtfData /PackageName:@Package
   ````

## Package Details

### Package Size

| Release                             |   x64     |    ARM64    |
|-------------------------------------|:---------:|:-----------:|
| Windows 11 IoT Enterprise LTSC 2024 | 6,171 KB  | 6,171 KB    |

### File List

| File Name | Installed Location |
|-----------|--------------------|
| averageroom.bin | %windir%\system32\averageroom.bin |
| baselinehrtfs.bin | %windir%\system32\defaulthrtfs.bin |
| dynamiclong.bin | %windir%\system32\dynamiclong.bin |
| dynamicmedium.bin | %windir%\system32\dynamicmedium.bin |
| dynamicshort.bin | %windir%\system32\dynamicshort.bin |
| largeroom.bin | %windir%\system32\largeroom.bin |
| mediumroom.bin | %windir%\system32\mediumroom.bin |
| outdooraudioenvironment.bin | %windir%\system32\outdooraudioenvironment.bin |
| smallroom.bin | %windir%\system32\smallroom.bin |

## Related Content

- [Removable Packages](/windows/iot/iot-enterprise/Optimize-Your-Device/Removable-Packages)
- [Reduce Disk Footprint](/windows/iot/iot-enterprise/Optimize-Your-Device/Reduce-Disk-Footprint)
- [Device Optimization Overview](/windows/iot/iot-enterprise/Optimize-Your-Device/Overview)
