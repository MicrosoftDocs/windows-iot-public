---
title: Removable Packages
author: twarwick
ms.author: twarwick
ms.date: 12/7/2022
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: Removable Package Details for LanguageFeatures_WordBreaking_Common_Legacy
keywords: IoT Enterprise, removable packages, storage
---

# Removable Package: LanguageFeatures_WordBreaking_Common_Legacy
## LanguageFeatures_WordBreaking_Common_Legacy
Legacy neutral word breaker, should only be needed in very rare app compat scenarios

Approximate on-disk footprint: 1542 KB

## Removing Package

### Online Servicing (audit mode)
Use the [DISM command-line tool](/windows-hardware/manufacture/desktop/what-is-dism) with the ```/Online``` command-line parammeter to remove a single package via online servicing (audit mode).

```powershell
Dism.exe /Online /LogPath:%TEMP%\LanguageFeatures_WordBreaking_Common_Legacy.log /NoRestart /Disable-Feature /FeatureName:LanguageFeatures_WordBreaking_Common_Legacy /PackageName:@Package
````
### Offline Servicing
Use the [DISM command-line tool](/windows-hardware/manufacture/desktop/what-is-dism) with the ```/Image:<image path>``` command-line parameter to remove a single package via offline servicing.

```powershell
Dism.exe /Image:c:\offline /LogPath:%TEMP%\LanguageFeatures_WordBreaking_Common_Legacy.log /NoRestart /Disable-Feature /FeatureName:LanguageFeatures_WordBreaking_Common_Legacy /PackageName:@Package
````

## File List
| File Name | Installed Location |
|-----------|--------------------|
| nlsdata0000.dll | %windir%\system32\nlsdata0000.dll |