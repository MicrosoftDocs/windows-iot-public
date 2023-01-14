---
title: Removable Package Microsoft-Windows-SensorDataService
author: twarwick
ms.author: twarwick
ms.date: 1/12/2023
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: Removable Package Details for Microsoft-Windows-SensorDataService
keywords: IoT Enterprise, removable packages, storage
---

# Removable Package: Microsoft-Windows-SensorDataService
## Microsoft-Windows-SensorDataService
A component of the [Media Feature Pack](/windows/win32/wmdm/windows-media-device-manager-architecture) supporting data acquisition from various sensors.  Supports Windows Hello.

Approximate on-disk footprint: 1,367 KB

## Removing Package

### Online Servicing 
Use the [DISM command-line tool](/windows-hardware/manufacture/desktop/what-is-dism) with the ```/Online``` command-line parameter to remove a single package via online servicing.

```powershell
Dism.exe /Online /LogPath:%WINDIR%\Temp\Microsoft-Windows-SensorDataService.log /NoRestart /Disable-Feature /FeatureName:Microsoft-Windows-SensorDataService /PackageName:@Package
````
### Offline Servicing
Use the [DISM command-line tool](/windows-hardware/manufacture/desktop/what-is-dism) with the ```/Image:<image path>``` command-line parameter to remove a single package via offline servicing.

```powershell
Dism.exe /Image:c:\offline /LogPath:%WINDIR%\Temp\Microsoft-Windows-SensorDataService.log /NoRestart /Disable-Feature /FeatureName:Microsoft-Windows-SensorDataService /PackageName:@Package
````

## File List
| File Name | Installed Location |
|-----------|--------------------|
| mediafoundation.defaultperceptionprovider.dll | %windir%\system32\mediafoundation.defaultperceptionprovider.dll |
| sensordataservice.exe                         | %windir%\system32\sensordataservice.exe |

## More Resources
- [Removable Packages](/windows/iot/iot-enterprise/Optimize-Your-Device/Removable-Packages)
- [Reduce Disk Footprint](/windows/iot/iot-enterprise/Optimize-Your-Device/Reduce-Disk-Footprint)
- [Device Optimization Overview](/windows/iot/iot-enterprise/Optimize-Your-Device/Overview)
