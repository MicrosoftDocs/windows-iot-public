---
title: Removable Package Details for Microsoft-Windows-RecoveryDrive
author: twarwick
ms.author: twarwick
ms.date: 12/7/2022
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: Removable Package Details for Microsoft-Windows-RecoveryDrive
keywords: IoT Enterprise, removable packages, storage
---

# Removable Package: Microsoft-Windows-RecoveryDrive
## Microsoft-Windows-RecoveryDrive
Create a recovery drive user experience invoked from Control Panel - Recovery

Approximate on-disk footprint: 1041 KB

## Removing Package

### Online Servicing 
Use the [DISM command-line tool](/windows-hardware/manufacture/desktop/what-is-dism) with the ```/Online``` command-line parameter to remove a single package via online servicing .

```powershell
Dism.exe /Online /LogPath:%WINDIR%\Temp\Microsoft-Windows-RecoveryDrive.log /NoRestart /Disable-Feature /FeatureName:Microsoft-Windows-RecoveryDrive /PackageName:@Package
````
### Offline Servicing
Use the [DISM command-line tool](/windows-hardware/manufacture/desktop/what-is-dism) with the ```/Image:<image path>``` command-line parameter to remove a single package via offline servicing.

```powershell
Dism.exe /Image:c:\offline /LogPath:%WINDIR%\Temp\Microsoft-Windows-RecoveryDrive.log /NoRestart /Disable-Feature /FeatureName:Microsoft-Windows-RecoveryDrive /PackageName:@Package
````

## File List
| File Name | Installed Location |
|-----------|--------------------|
| recoverydrive.lnk | %programdata%\microsoft\windows\start menu\programs\administrative tools\recoverydrive.lnk |
| recovery.dll      | %windir%\system32\recovery.dll |
| recoverydrive.exe | %windir%\system32\recoverydrive.exe |
