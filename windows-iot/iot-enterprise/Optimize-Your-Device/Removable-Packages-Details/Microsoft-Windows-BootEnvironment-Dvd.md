---
title: Package - Boot Environment DVD
author: twarwick
ms.author: twarwick
ms.date: 1/12/2023
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: Removable Package Details for Microsoft-Windows-BootEnvironment-Dvd
keywords: IoT Enterprise, removable packages, storage
---

# Package: Boot Environment DVD

## Description 
This package enables **Boot from DVD** functionality in Windows.

**Package Name:** Microsoft-Windows-BootEnvironment-Dvd

**Size:** Approximately 9,108 KB

## Removing Package

### Online Servicing 
Use the [DISM command-line tool](/windows-hardware/manufacture/desktop/what-is-dism) with the ```/Online``` command-line parameter to remove a single package via online servicing.

```powershell
Dism.exe /Online /LogPath:%WINDIR%\Temp\Microsoft-Windows-BootEnvironment-Dvd.log /NoRestart /Disable-Feature /FeatureName:Microsoft-Windows-BootEnvironment-Dvd /PackageName:@Package
````
### Offline Servicing
Use the [DISM command-line tool](/windows-hardware/manufacture/desktop/what-is-dism) with the ```/Image:<image path>``` command-line parameter to remove a single package via offline servicing.

```powershell
Dism.exe /Image:c:\offline /LogPath:%WINDIR%\Temp\Microsoft-Windows-BootEnvironment-Dvd.log /NoRestart /Disable-Feature /FeatureName:Microsoft-Windows-BootEnvironment-Dvd /PackageName:@Package
````

## File List
| File Name | Installed Location |
|-----------|--------------------|
| bcd                 | %windir%\boot\dvd\efi\bcd |
| efisys.bin          | %windir%\boot\dvd\efi\en-us\efisys.bin |
| efisys_noprompt.bin | %windir%\boot\dvd\efi\en-us\efisys_noprompt.bin |
| bcd                 | %windir%\boot\dvd\pcat\bcd |
| boot.sdi            | %windir%\boot\dvd\pcat\boot.sdi |
| etfsboot.com        | %windir%\boot\dvd\pcat\etfsboot.com |

## More Resources
- [Removable Packages](/windows/iot/iot-enterprise/Optimize-Your-Device/Removable-Packages)
- [Reduce Disk Footprint](/windows/iot/iot-enterprise/Optimize-Your-Device/Reduce-Disk-Footprint)
- [Device Optimization Overview](/windows/iot/iot-enterprise/Optimize-Your-Device/Overview)
