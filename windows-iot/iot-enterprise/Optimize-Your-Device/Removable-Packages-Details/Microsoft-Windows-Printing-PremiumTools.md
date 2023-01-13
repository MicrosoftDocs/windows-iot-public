---
title: Removable Package Microsoft-Windows-Printing-PremiumTools
author: twarwick
ms.author: twarwick
ms.date: 12/20/2022
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: Removable Package Details for Microsoft-Windows-Printing-PremiumTools
keywords: IoT Enterprise, removable packages, storage
---

# Removable Package: Microsoft-Windows-Printing-PremiumTools
## Microsoft-Windows-Printing-PremiumTools
Print services migration command-line tool printbrm.exe

Approximate on-disk footprint: 381 KB

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
- [Removable Packages](/windows/iot/iot-enterprise/Optimize-Your-Device/Removable-Packages-Details/Removable-Packages.md)
- [Reduce Disk Footprint](/windows/iot/iot-enterprise/Optimize-Your-Device/Reduce-Disk-Footprint.md)
- [Device Optimization Overview](/windows/iot/iot-enterprise/Optimize-Your-Device/Overview.md)
