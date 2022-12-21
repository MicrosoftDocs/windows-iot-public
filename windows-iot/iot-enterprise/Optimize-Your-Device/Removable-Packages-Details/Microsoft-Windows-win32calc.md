---
title: Removable Package Microsoft-Windows-win32calc
author: twarwick
ms.author: twarwick
ms.date: 12/20/2022
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: Removable Package Details for Microsoft-Windows-win32calc
keywords: IoT Enterprise, removable packages, storage
---

# Removable Package: Microsoft-Windows-win32calc
## Microsoft-Windows-win32calc
Legacy calculator application

Approximate on-disk footprint: 1,394 KB


## Removing Package

### Online Servicing 
Use the [DISM command-line tool](/windows-hardware/manufacture/desktop/what-is-dism) with the ```/Online``` command-line parameter to remove a single package via online servicing .

```powershell
Dism.exe /Online /LogPath:%WINDIR%\Temp\Microsoft-Windows-win32calc.log /NoRestart /Disable-Feature /FeatureName:Microsoft-Windows-win32calc /PackageName:@Package
````
### Offline Servicing
Use the [DISM command-line tool](/windows-hardware/manufacture/desktop/what-is-dism) with the ```/Image:<image path>``` command-line parameter to remove a single package via offline servicing.

```powershell
Dism.exe /Image:c:\offline /LogPath:%WINDIR%\Temp\Microsoft-Windows-win32calc.log /NoRestart /Disable-Feature /FeatureName:Microsoft-Windows-win32calc /PackageName:@Package
````

## File List
| File Name | Installed Location |
|-----------|--------------------|
| calculator.lnk | %programdata%\microsoft\windows\start menu\programs\accessories\calculator.lnk  |
| win32calc.exe  | %windir%\system32\win32calc.exe |
