---
title: Package - Shell Accessories
titleSuffix: Windows IoT Enterprise
author: twarwick
ms.author: twarwick
ms.date: 01/31/2024
ms.topic: article
ms.service: windows-iot
ms.subservice: iot
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

> [!IMPORTANT]
>
> This feature is only supported on the Windows IoT Entrprise LTSC edition.  If you choose to remove any of this package from Windows IoT Enterprise, you must ensure that your solution does not rely on functionality of the removed package. You cannot restore the package without a full reinstall of Windows IoT Enterprise LTSC.  
> For more information, see [Removable Packages System Requirements](../Removable-Packages.md#system-requirements).

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

- [Removable Packages](../Removable-Packages.md)
- [Device Optimization Overview](../Overview.md)
