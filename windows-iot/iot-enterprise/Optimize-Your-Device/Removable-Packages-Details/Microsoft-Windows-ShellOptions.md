---
title: Package - Shell Accessories
author: twarwick
ms.author: twarwick
ms.date: 2/6/2023
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: Removable Package Details for Microsoft-Windows-ShellOptions
keywords: IoT Enterprise, removable packages, storage
---

# Shell Accessories

| Applies to                          |  Version            |
|:------------------------------------|:--------------------|
| Windows 10 IoT Enterprise LTSC 2021 | 19044.1741 or later |


## Description

Modern Calculator, Character Map, More Icons DLL

**Package Name:** Microsoft-Windows-ShellOptions

**Size:** Approximately 657 KB

## Package Removal

1. To remove a specific package from the image type:
   ```powershell
   Dism.exe /Online /NoRestart /Disable-Feature /FeatureName:Microsoft-Windows-ShellOptions /PackageName:@Package
   ````

   To remove a package from an offline image mounted at `c:\offline` type:
   ```powershell
   Dism.exe /Image:c:\offline  /Disable-Feature /FeatureName:Microsoft-Windows-ShellOptions /PackageName:@Package
   ```

1. Optional: Use DISM /GetFeatureInfo to get the status of a removable package type:
   ```powershell
   Dism.exe /Online /Get-FeatureInfo /FeatureName:Microsoft-Windows-ShellOptions /PackageName:@Package
   ````

## File List
| File Name | Installed Location |
|-----------|--------------------|
| character map.lnk | %programdata%\microsoft\windows\start menu\programs\accessories\system tools\character map.lnk |
| bopomofo.uce      | %windir%\system32\bopomofo.uce |
| calc.exe          | %windir%\system32\calc.exe |
| charmap.exe       | %windir%\system32\charmap.exe |
| gb2312.uce        | %windir%\system32\gb2312.uce |
| getuname.dll      | %windir%\system32\getuname.dll |
| ideograf.uce      | %windir%\system32\ideograf.uce |
| kanji_1.uce       | %windir%\system32\kanji_1.uce |
| kanji_2.uce       | %windir%\system32\kanji_2.uce |
| korean.uce        | %windir%\system32\korean.uce |
| moricons.dll      | %windir%\system32\moricons.dll |
| shiftjis.uce      | %windir%\system32\shiftjis.uce |
| subrange.uce      | %windir%\system32\subrange.uce |
| moricons.dll.mun  | %windir%\systemresources\moricons.dll.mun  |

## More Resources
- [Removable Packages](/windows/iot/iot-enterprise/Optimize-Your-Device/Removable-Packages)
- [Reduce Disk Footprint](/windows/iot/iot-enterprise/Optimize-Your-Device/Reduce-Disk-Footprint)
- [Device Optimization Overview](/windows/iot/iot-enterprise/Optimize-Your-Device/Overview)
