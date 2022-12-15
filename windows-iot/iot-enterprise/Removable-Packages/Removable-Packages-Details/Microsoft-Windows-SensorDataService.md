---
title: Removable Packages
author: twarwick
ms.author: twarwick
ms.date: 12/7/2022
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: Removable Package Details for Microsoft-Windows-SensorDataService
keywords: IoT Enterprise, removable packages, storage
---

# Removable Package: Microsoft-Windows-SensorDataService
## Microsoft-Windows-SensorDataService
ensor Data Service delivers data from a variety of sensors.  Supports Windows Hello.

Approximate on-disk footprint: 1367 KB

## Removing Package

### Online Servicing (audit mode)
Use the [DISM command-line tool](/windows-hardware/manufacture/desktop/what-is-dism) with the ```/Online``` command-line parammeter to remove a single package via online servicing (audit mode).

```powershell
Dism.exe /Online /LogPath:%TEMP%\Microsoft-Windows-SensorDataService.log /NoRestart /Disable-Feature /FeatureName:Microsoft-Windows-SensorDataService /PackageName:@Package
````
### Offline Servicing
Use the [DISM command-line tool](/windows-hardware/manufacture/desktop/what-is-dism) with the ```/Image:<image path>``` command-line parameter to remove a single package via offline servicing.

```powershell
Dism.exe /Image:c:\offline /LogPath:%TEMP%\Microsoft-Windows-SensorDataService.log /NoRestart /Disable-Feature /FeatureName:Microsoft-Windows-SensorDataService /PackageName:@Package
````

## File List
| File Name | Installed Location |
|-----------|--------------------|
| mediafoundation.defaultperceptionprovider.dll | %windir%\system32\mediafoundation.defaultperceptionprovider.dll |
| sensordataservice.exe                         | %windir%\system32\sensordataservice.exe |