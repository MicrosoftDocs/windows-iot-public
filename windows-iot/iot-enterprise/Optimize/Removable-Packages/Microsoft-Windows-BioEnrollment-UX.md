---
title: Package - Bio Enrollment Experience
titleSuffix: Windows IoT Enterprise
author: twarwick
ms.author: twarwick
ms.date: 03/30/2023
ms.topic: article
ms.service: windows-iot
ms.subservice: iot
description: Removable Package Details for Microsoft-Windows-BioEnrollment-UX
keywords: IoT Enterprise, removable packages, storage
---

# Bio Enrollment Experience

Applies to:  
✅ Windows 11 IoT Enterprise LTSC 2024  
✅ Windows 10 IoT Enterprise LTSC 2021 (19044.1741 or later)  

## Package Description  

Package: **Microsoft-Windows-BioEnrollment-UX** </br> For a complete description, see [Windows Hello](/windows-hardware/design/device-experiences/windows-hello).

## Package Removal

1. To remove a specific package from the image type:

   ```powershell
   Dism.exe /Online /NoRestart /Disable-Feature /FeatureName:Microsoft-Windows-BioEnrollment-UX /PackageName:@Package
   ````

   To remove a package from an offline image mounted at `c:\offline` type:

   ```powershell
   Dism.exe /Image:c:\offline  /Disable-Feature /FeatureName:Microsoft-Windows-BioEnrollment-UX /PackageName:@Package
   ```

1. Optional: Use DISM /GetFeatureInfo to get the status of a removable package type:

   ```powershell
   Dism.exe /Online /Get-FeatureInfo /FeatureName:Microsoft-Windows-BioEnrollment-UX /PackageName:@Package
   ````

## Package Details

### Package Size

| Release                             |   x64     |    ARM64    |
|-------------------------------------|:---------:|:-----------:|
| Windows 11 IoT Enterprise LTSC 2024 | 3,470 KB  | 4,867 KB    |
| Windows 10 IoT Enterprise LTSC 2021 | 3,589 KB  |             |

### File List

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

- [Removable Packages](../Removable-Packages.md)
- [Device Optimization Overview](../Overview.md)
