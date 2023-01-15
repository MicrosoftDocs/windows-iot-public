---
title: Package - Bio Enrollment Experience
author: twarwick
ms.author: twarwick
ms.date: 1/12/2023
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: Removable Package Details for Microsoft-Windows-BioEnrollment-UX
keywords: IoT Enterprise, removable packages, storage
---

# Package: Bio Enrollment Experience

## Description
See [Windows Hello](/windows-hardware/design/device-experiences/windows-hello) enrollment experience for a detailed description of this Windows feature.

**Package Name:** Microsoft-Windows-BioEnrollment-UX

**Size:** Approximately 3,589 KB

## Removing Package

### Online Servicing 
Use the [DISM command-line tool](/windows-hardware/manufacture/desktop/what-is-dism) with the ```/Online``` command-line parameter to remove a single package via online servicing.

```powershell
Dism.exe /Online /LogPath:%WINDIR%\Temp\Microsoft-Windows-BioEnrollment-UX.log /NoRestart /Disable-Feature /FeatureName:Microsoft-Windows-BioEnrollment-UX /PackageName:@Package
````
### Offline Servicing
Use the [DISM command-line tool](/windows-hardware/manufacture/desktop/what-is-dism) with the ```/Image:<image path>``` command-line parameter to remove a single package via offline servicing.

```powershell
Dism.exe /Image:c:\offline /LogPath:%WINDIR%\Temp\Microsoft-Windows-BioEnrollment-UX.log /NoRestart /Disable-Feature /FeatureName:Microsoft-Windows-BioEnrollment-UX /PackageName:@Package
````

## File List

| File Name | Installed Location |
|-----------|--------------------|
| appxblockmap.xml      | %windir%\systemapps\microsoft.bioenrollment_cw5n1h2txyewy\appxblockmap.xml |
| appxmanifest.xml      | %windir%\systemapps\microsoft.bioenrollment_cw5n1h2txyewy\appxmanifest.xml |
| appxsignature.p7x     | %windir%\systemapps\microsoft.bioenrollment_cw5n1h2txyewy\appxsignature.p7x |
| bioenrollmenthost.exe | %windir%\systemapps\microsoft.bioenrollment_cw5n1h2txyewy\bioenrollmenthost.exe |
| bioenrollmentui.dll   | %windir%\systemapps\microsoft.bioenrollment_cw5n1h2txyewy\bioenrollmentui.dll |
| biomdl2.ttf           | %windir%\systemapps\microsoft.bioenrollment_cw5n1h2txyewy\fonts\biomdl2.ttf |
| resources.pri         | %windir%\systemapps\microsoft.bioenrollment_cw5n1h2txyewy\resources.pri |

## More Resources
- [Removable Packages](/windows/iot/iot-enterprise/Optimize-Your-Device/Removable-Packages)
- [Reduce Disk Footprint](/windows/iot/iot-enterprise/Optimize-Your-Device/Reduce-Disk-Footprint)
- [Device Optimization Overview](/windows/iot/iot-enterprise/Optimize-Your-Device/Overview)
