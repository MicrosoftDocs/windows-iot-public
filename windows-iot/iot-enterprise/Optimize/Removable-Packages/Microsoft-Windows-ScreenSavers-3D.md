---
title: Package - 3D Screensavers
author: twarwick
ms.author: twarwick
ms.date: 03/30/2023
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: Removable Package Details for Microsoft-Windows-ScreenSavers-3d
keywords: IoT Enterprise, removable packages, storage
---

# 3D  Screensavers

| Applies to                          |  Version            |
|:------------------------------------|:--------------------|
| Windows 10 IoT Enterprise LTSC 2021 | 19044.1741 or later |

## Description

Screensavers: 3D Text, Bubbles, Mystify and Ribbons

**Package Name:** Microsoft-Windows-ScreenSavers-3d

**Size:** Approximately 1,312 KB

## Package Removal

1. To remove a specific package from the image type:

   ```powershell
   Dism.exe /Online /NoRestart /Disable-Feature /FeatureName:Microsoft-Windows-ScreenSavers-3d /PackageName:@Package
   ````

   To remove a package from an offline image mounted at `c:\offline` type:

   ```powershell
   Dism.exe /Image:c:\offline  /Disable-Feature /FeatureName:Microsoft-Windows-ScreenSavers-3d /PackageName:@Package
   ```

1. Optional: Use DISM /GetFeatureInfo to get the status of a removable package type:

   ```powershell
   Dism.exe /Online /Get-FeatureInfo /FeatureName:Microsoft-Windows-ScreenSavers-3d /PackageName:@Package
   ````

## File List

| File Name    | Installed Location |
|-----------   |--------------------|
| bubbles.scr  | %windir%\system32\bubbles.scr |
| mystify.scr  | %windir%\system32\mystify.scr |
| ribbons.scr  | %windir%\system32\ribbons.scr |
| sstext3d.scr | %windir%\system32\sstext3d.scr |

## More Resources

- [Removable Packages](../Removable-Packages.md)
- [Device Optimization Overview](../Overview.md)
