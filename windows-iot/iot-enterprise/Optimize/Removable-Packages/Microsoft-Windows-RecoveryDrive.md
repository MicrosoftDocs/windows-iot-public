---
title: Package - Recovery Drive
titleSuffix: Windows IoT Enterprise
author: TerryWarwick
ms.author: twarwick
ms.date: 04/29/2024
ms.topic: reference
ms.service: windows-iot
ms.subservice: iot
description: Removable Package Details for Microsoft-Windows-RecoveryDrive
keywords: IoT Enterprise, removable packages, storage
---

# Recovery Drive

Applies to:  
✅ Windows 11 IoT Enterprise LTSC 2024  
✅ Windows 10 IoT Enterprise LTSC 2021 (19044.1741 or later)  

## Package Description

Package: **Microsoft-Windows-RecoveryDrive** </br> Create a recovery drive user experience invoked from Control Panel - Recovery.

> [!IMPORTANT]
>
> This feature is only supported on the Windows IoT Entrprise LTSC edition.  If you choose to remove any of this package from Windows IoT Enterprise, you must ensure that your solution does not rely on functionality of the removed package. You cannot restore the package without a full reinstall of Windows IoT Enterprise LTSC.  
> For more information, see [Removable Packages System Requirements](../Removable-Packages.md#system-requirements).

## Package Removal

1. To remove a specific package from the image type:

   ```powershell
   Dism.exe /Online /NoRestart /Disable-Feature /FeatureName:Microsoft-Windows-RecoveryDrive /PackageName:@Package
   ````

   To remove a package from an offline image mounted at `c:\offline` type:

   ```powershell
   Dism.exe /Image:c:\offline  /Disable-Feature /FeatureName:Microsoft-Windows-RecoveryDrive /PackageName:@Package
   ```

1. Optional: Use DISM /GetFeatureInfo to get the status of a removable package type:

   ```powershell
   Dism.exe /Online /Get-FeatureInfo /FeatureName:Microsoft-Windows-RecoveryDrive /PackageName:@Package
   ````

## Package Details

### Package Size

| Release                             |   x64     |    ARM64    |
|-------------------------------------|:---------:|:-----------:|
| Windows 11 IoT Enterprise LTSC 2024 | 473 KB    | 451 KB      |
| Windows 10 IoT Enterprise LTSC 2021 | 1.041 KB  |             |

### File List

| File Name | Installed Location |
|-----------|--------------------|
| recoverydrive.lnk | %programdata%\microsoft\windows\start menu\programs\administrative tools\recoverydrive.lnk |
| recovery.dll      | %windir%\system32\recovery.dll |
| recoverydrive.exe | %windir%\system32\recoverydrive.exe |
| windlp.dll | %windir%\system32\windlp.dll |

## More Resources

- [Removable Packages](../Removable-Packages.md)
- [Device Optimization Overview](../Overview.md)
