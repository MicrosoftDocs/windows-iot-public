---
title: Package - Printer Drivers
titleSuffix: Windows IoT Enterprise
author: TerryWarwick
ms.author: twarwick
ms.date: 05/22/2024
ms.topic: reference
ms.service: windows-iot
ms.subservice: iot
description: Removable Package Details for Microsoft-Windows-Printer-Drivers
keywords: IoT Enterprise, removable packages, storage
---

# Printer Drivers

Applies to:  
✅ Windows 11 IoT Enterprise LTSC 2024  
✅ Windows 10 IoT Enterprise LTSC 2021 (19044.1741 or later)  

## Package Description

Package: **Microsoft-Windows-Printer-Drivers** </br> Generic / Text Only, Generic IBM Graphics 9pin, Generic IBM Graphics 9-pin wide, MS Publisher Color Printer, MS Publisher Imagesetter, Microsoft Shared Fax Driver.

> [!IMPORTANT]
>
> This feature is only supported on the Windows IoT Entrprise LTSC edition.  If you choose to remove any of this package from Windows IoT Enterprise, you must ensure that your solution does not rely on functionality of the removed package. You cannot restore the package without a full reinstall of Windows IoT Enterprise LTSC.  
> For more information, see [Removable Packages System Requirements](../Removable-Packages.md#system-requirements).

## Package Removal

1. To remove a specific package from the image type:

   ```powershell
   Dism.exe /Online /NoRestart /Disable-Feature /FeatureName:Microsoft-Windows-Printer-Drivers /PackageName:@Package
   ````

   To remove a package from an offline image mounted at `c:\offline` type:

   ```powershell
   Dism.exe /Image:c:\offline  /Disable-Feature /FeatureName:Microsoft-Windows-Printer-Drivers /PackageName:@Package
   ```

1. Optional: Use DISM /GetFeatureInfo to get the status of a removable package type:

   ```powershell
   Dism.exe /Online /Get-FeatureInfo /FeatureName:Microsoft-Windows-Printer-Drivers /PackageName:@Package
   ````

## Package Details

### Package Size

| Release                             |   x64     |    ARM64    |
|-------------------------------------|:---------:|:-----------:|
| Windows 11 IoT Enterprise LTSC 2024 | 8,592 KB  | 99 KB       |
| Windows 10 IoT Enterprise LTSC 2021 | 8,200 KB  |             |

### File List

| File Name | Installed Location |
|-----------|--------------------|
| prnge001.cat | %windir%\system32\drivers\prnge001.cat |
| prnms002.cat | %windir%\system32\drivers\prnms002.cat |
| fxsapi.dll   | %windir%\system32\spool\drivers\x64\3\amd64\fxsapi.dll |
| fxsdrv.dll   | %windir%\system32\spool\drivers\x64\3\amd64\fxsdrv.dll |
| fxsres.dll   | %windir%\system32\spool\drivers\x64\3\amd64\fxsres.dll |
| fxstiff.dll  | %windir%\system32\spool\drivers\x64\3\amd64\fxstiff.dll |
| fxsui.dll    | %windir%\system32\spool\drivers\x64\3\amd64\fxsui.dll |
| fxswzrd.dll  | %windir%\system32\spool\drivers\x64\3\amd64\fxswzrd.dll |
| genibm9.gpd  | %windir%\system32\spool\drivers\x64\3\amd64\genibm9.gpd |
| genibm9w.gpd | %windir%\system32\spool\drivers\x64\3\amd64\genibm9w.gpd |
| msgenbw.ppd  | %windir%\system32\spool\drivers\x64\3\amd64\msgenbw.ppd |
| msgencol.ppd | %windir%\system32\spool\drivers\x64\3\amd64\msgencol.ppd |
| ok9ibres.dll | %windir%\system32\spool\drivers\x64\3\amd64\ok9ibres.dll |
| tty.dll      | %windir%\system32\spool\drivers\x64\3\amd64\tty.dll |
| tty.gpd      | %windir%\system32\spool\drivers\x64\3\amd64\tty.gpd |
| tty.ini      | %windir%\system32\spool\drivers\x64\3\amd64\tty.ini |
| ttyres.dll   | %windir%\system32\spool\drivers\x64\3\amd64\ttyres.dll |
| ttyui.dll    | %windir%\system32\spool\drivers\x64\3\amd64\ttyui.dll |
| ttyui.hlp    | %windir%\system32\spool\drivers\x64\3\amd64\ttyui.hlp |
| prnge001.inf | %windir%\system32\driverstore\filerepository\prnge001.inf_amd64_93ef6743cd62907a\prnge001.inf |
| prnms002.inf | %windir%\system32\driverstore\filerepository\prnms002.inf_amd64_44e969b6d0899fdd\prnms002.inf |

## Related Content

- [Removable Packages](../Removable-Packages.md)
- [Device Optimization Overview](../Overview.md)
