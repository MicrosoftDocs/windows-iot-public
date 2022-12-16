---
title: Removable Package Fonts_DesktopFonts_NonLeanSupplement
author: twarwick
ms.author: twarwick
ms.date: 12/7/2022
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: Removable Package Details for Fonts_DesktopFonts_NonLeanSupplement
keywords: IoT Enterprise, removable packages, storage
---

# Removable Package: Fonts_DesktopFonts_NonLeanSupplement
## Fonts_DesktopFonts_NonLeanSupplement
Fonts: [Malgun Gothic](/typography/font-list/malgun-gothic), [Microsoft JhengHei](/typography/font-list/microsoft-jhenghei), [Microsoft YaHei](/typography/font-list/microsoft-yahei), [Yu Gothic](/typography/font-list/yu-gothic)

Approximate on-disk footprint: 113,251 KB  

## Removing Package

### Online Servicing 
Use the [DISM command-line tool](/windows-hardware/manufacture/desktop/what-is-dism) with the ```/Online``` command-line parameter to remove a single package via online servicing .

```powershell
Dism.exe /Online /LogPath:%WINDIR%\Temp\Fonts_DesktopFonts_NonLeanSupplement.log /NoRestart /Disable-Feature /FeatureName:Fonts_DesktopFonts_NonLeanSupplement /PackageName:@Package
````
### Offline Servicing
Use the [DISM command-line tool](/windows-hardware/manufacture/desktop/what-is-dism) with the ```/Image:<image path>``` command-line parameter to remove a single package via offline servicing.

```powershell
Dism.exe /Image:c:\offline /LogPath:%WINDIR%\Temp\Fonts_DesktopFonts_NonLeanSupplement.log /NoRestart /Disable-Feature /FeatureName:Fonts_DesktopFonts_NonLeanSupplement /PackageName:@Package
````

## File List
| File Name     | Installed Location |
|---------------|--------------------|
| malgunbd.ttf  | %windir%\fonts\malgunbd.ttf | 
| malgunsl.ttf  | %windir%\fonts\malgunsl.ttf | 
| msjhbd.ttc    | %windir%\fonts\msjhbd.ttc | 
| msjhl.ttc     | %windir%\fonts\msjhl.ttc  |
| msyhbd.ttc    | %windir%\fonts\msyhbd.ttc | 
| msyhl.ttc     | %windir%\fonts\msyhl.ttc  |
| yugothb.ttc   | %windir%\fonts\yugothb.ttc  |
| yugothl.ttc   | %windir%\fonts\yugothl.ttc | 
| yugothr.ttc   | %windir%\fonts\yugothr.ttc |
