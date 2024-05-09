---
title: Package - Boot Environment DVD
titleSuffix: Windows IoT Enterprise
author: TerryWarwick
ms.author: twarwick
ms.date: 04/29/2024
ms.topic: reference
ms.service: windows-iot
ms.subservice: iot
description: Removable Package Details for Microsoft-Windows-BootEnvironment-Dvd
keywords: IoT Enterprise, removable packages, storage
---

# Boot Environment DVD

Applies to:  
✅ Windows 11 IoT Enterprise LTSC 2024  
✅ Windows 10 IoT Enterprise LTSC 2021 (19044.1741 or later)  

## Package Description  

Package: **Microsoft-Windows-BootEnvironment-Dvd** </br> Boot from DVD.

> [!IMPORTANT]
>
> This feature is only supported on the Windows IoT Entrprise LTSC edition.  If you choose to remove any of this package from Windows IoT Enterprise, you must ensure that your solution does not rely on functionality of the removed package. You cannot restore the package without a full reinstall of Windows IoT Enterprise LTSC.  
> For more information, see [Removable Packages System Requirements](../Removable-Packages.md#system-requirements).

## Package Removal

1. To remove a specific package from the image type:

   ```powershell
   Dism.exe /Online /NoRestart /Disable-Feature /FeatureName:Microsoft-Windows-BootEnvironment-Dvd /PackageName:@Package
   ````

   To remove a package from an offline image mounted at `c:\offline` type:

   ```powershell
   Dism.exe /Image:c:\offline  /Disable-Feature /FeatureName:Microsoft-Windows-BootEnvironment-Dvd /PackageName:@Package
   ```

1. Optional: Use DISM /GetFeatureInfo to get the status of a removable package type:

   ```powershell
   Dism.exe /Online /Get-FeatureInfo /FeatureName:Microsoft-Windows-BootEnvironment-Dvd /PackageName:@Package
   ````

## Package Details

### Package Size

| Release                             |   x64     |    ARM64    |
|-------------------------------------|:---------:|:-----------:|
| Windows 11 IoT Enterprise LTSC 2024 | 6,224 KB  | 3,112 KB    |
| Windows 10 IoT Enterprise LTSC 2021 | 9.108 KB  |             |

### File List

| File Name | Installed Location |
|-----------|--------------------|
| bcd                 | %windir%\boot\dvd\efi\bcd |
| efisys.bin          | %windir%\boot\dvd\efi\en-us\efisys.bin |
| efisys_noprompt.bin | %windir%\boot\dvd\efi\en-us\efisys_noprompt.bin |
| bcd                 | %windir%\boot\dvd\pcat\bcd |
| boot.sdi            | %windir%\boot\dvd\pcat\boot.sdi |
| etfsboot.com        | %windir%\boot\dvd\pcat\etfsboot.com |

## Related Content

- [Removable Packages](../Removable-Packages.md)
- [Device Optimization Overview](../Overview.md)
