---
title: Package - PrintBrm Command-Line tool
author: twarwick
ms.author: twarwick
ms.date: 1/12/2023
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: Removable Package Details for Microsoft-Windows-Printing-PremiumTools
keywords: IoT Enterprise, removable packages, storage
---

# Package: PrintBrm Command-Line tool

## Description
Print services migration command-line tool printbrm.exe

**Package Name:** Microsoft-Windows-Printing-PremiumTools

**Size:**  Approximately 381 KB

## Removing Package

### Online Servicing 
Use the [DISM command-line tool](/windows-hardware/manufacture/desktop/what-is-dism) with the ```/Online``` command-line parameter to remove a single package via online servicing.

```powershell
Dism.exe /Online /LogPath:%WINDIR%\Temp\Microsoft-Windows-Printing-PremiumTools.log /NoRestart /Disable-Feature /FeatureName:Microsoft-Windows-Printing-PremiumTools /PackageName:@Package
````
### Offline Servicing
Use the [DISM command-line tool](/windows-hardware/manufacture/desktop/what-is-dism) with the ```/Image:<image path>``` command-line parameter to remove a single package via offline servicing.

```powershell
Dism.exe /Image:c:\offline /LogPath:%WINDIR%\Temp\Microsoft-Windows-Printing-PremiumTools.log /NoRestart /Disable-Feature /FeatureName:Microsoft-Windows-Printing-PremiumTools /PackageName:@Package
````

## File List
| File Name | Installed Location |
|-----------|--------------------|
| printbrmui.exe     | %windir%\system32\printbrmui.exe |
| printbrm.exe       | %windir%\system32\spool\tools\printbrm.exe |
| printbrmengine.exe | %windir%\system32\spool\tools\printbrmengine.exe |
| printbrmps.dll     | %windir%\system32\spool\tools\printbrmps.dll |

## More Resources
- [Removable Packages](/windows/iot/iot-enterprise/Optimize-Your-Device/Removable-Packages)
- [Reduce Disk Footprint](/windows/iot/iot-enterprise/Optimize-Your-Device/Reduce-Disk-Footprint)
- [Device Optimization Overview](/windows/iot/iot-enterprise/Optimize-Your-Device/Overview)
