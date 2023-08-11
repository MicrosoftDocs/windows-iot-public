---
title: Package - Printer Drivers
author: twarwick
ms.author: twarwick
ms.date: 03/30/2023
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: Removable Package Details for Microsoft-Windows-Printer-Drivers
keywords: IoT Enterprise, removable packages, storage
---

# Printer Drivers

| Applies to                          |  Version            |
|:------------------------------------|:--------------------|
| Windows 10 IoT Enterprise LTSC 2021 | 19044.1741 or later |

## Description

Generic / Text Only, Generic IBM Graphics 9-pin, Generic IBM Graphics 9-pin wide, MS Publisher Color Printer, MS Publisher Imagesetter, Microsoft Shared Fax Driver

**Package Name:**  Microsoft-Windows-Printer-Drivers

**Size:** Approximately 8,200 KB

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

## File List

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
| prnge001.inf | prnge001.inf |
| prnms002.inf | prnms002.inf |

## More Resources

- [Removable Packages](../Removable-Packages.md)
- [Reduce Disk Footprint](../Reduce-Disk-Footprint.md)
- [Device Optimization Overview](../Overview.md)
