---
title: Removable Package Microsoft-Windows-Printer-Drivers
author: twarwick
ms.author: twarwick
ms.date: 12/7/2022
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: Removable Package Details for Microsoft-Windows-Printer-Drivers
keywords: IoT Enterprise, removable packages, storage
---

# Removable Package: Microsoft-Windows-Printer-Drivers
## Microsoft-Windows-Printer-Drivers
Generic / Text Only, Generic IBM Graphics 9pin, Generic IBM Graphics 9-pin wide, MS Publisher Color Printer, MS Publisher Imagesetter, Microsoft Shared Fax Driver

Approximate on-disk footprint: 8,200 KB

## Removing Package

### Online Servicing (audit mode)
Use the [DISM command-line tool](/windows-hardware/manufacture/desktop/what-is-dism) with the ```/Online``` command-line parameter to remove a single package via online servicing (audit mode).

```powershell
Dism.exe /Online /LogPath:%WINDIR%\Temp\Microsoft-Windows-Printer-Drivers.log /NoRestart /Disable-Feature /FeatureName:Microsoft-Windows-Printer-Drivers /PackageName:@Package
````
### Offline Servicing
Use the [DISM command-line tool](/windows-hardware/manufacture/desktop/what-is-dism) with the ```/Image:<image path>``` command-line parameter to remove a single package via offline servicing.

```powershell
Dism.exe /Image:c:\offline /LogPath:%WINDIR%\Temp\Microsoft-Windows-Printer-Drivers.log /NoRestart /Disable-Feature /FeatureName:Microsoft-Windows-Printer-Drivers /PackageName:@Package
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
