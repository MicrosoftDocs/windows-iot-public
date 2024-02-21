---
title: Package - Bio Enrollment Experience
titleSuffix: Windows IoT Enterprise
author: twarwick
ms.author: twarwick
ms.date: 01/31/2024
ms.topic: article
ms.service: windows-iot
ms.subservice: iot
description: Removable Package Details for Microsoft-Windows-BioEnrollment-UX
keywords: IoT Enterprise, removable packages, storage
---

# Bio Enrollment Experience

| Applies to                          |  Version            |
|:------------------------------------|:--------------------|
| Windows 10 IoT Enterprise LTSC 2021 | 19044.1741 or later |

## Description  

See [Windows Hello](/windows-hardware/design/device-experiences/windows-hello) enrollment experience for a detailed description of this Windows feature.

**Package Name:** Microsoft-Windows-BioEnrollment-UX

**Size:** Approximately 3,589 KB

> [!IMPORTANT]
>
> This feature is only supported on the Windows IoT Entrprise LTSC edition.  If you choose to remove any of this package from Windows IoT Enterprise, you must ensure that your solution does not rely on functionality of the removed package. You cannot restore the package without a full reinstall of Windows IoT Enterprise LTSC.  
> For more information, see [Removable Packages System Requirements](../Removable-Packages.md#system-requirements).

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

- [Removable Packages](../Removable-Packages.md)
- [Device Optimization Overview](../Overview.md)
