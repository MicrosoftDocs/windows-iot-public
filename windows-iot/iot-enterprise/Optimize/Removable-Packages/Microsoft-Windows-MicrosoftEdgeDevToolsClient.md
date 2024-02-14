---
title: Package - Microsoft Edge Developer Tools Client
titleSuffix: Windows IoT Enterprise
author: TerryWarwick
ms.author: twarwick
ms.date: 02/12/2024
ms.topic: article
ms.service: windows-iot
ms.subservice: iot
description: Removable Package Details for Microsoft Edge Developer Tools Client
keywords: IoT Enterprise, removable packages, storage
---

# Microsoft Edge Developer Tools Client

> [!WARNING]
> THIS IS AN IN-PROGRESS ROUGH DRAFT. The wording and feature list may change before publishing.

Applies to:  
✅ Windows 11 IoT Enterprise LTSC 2024  
⛔ Windows 10 IoT Enterprise LTSC 2021

## Package Description

Package: **Microsoft-Windows-MicrosoftEdgeDevToolsClient** </br>  Microsoft Edge developer tools.  For more information, see [Microsoft Edge DevTools documentation](/microsoft-edge/devtools-guide-chromium/landing/).

## Package Removal

1. To remove a specific package from the image type:

   ```powershell
   $Arch = $env:PROCESSOR_ARCHITECTURE
   $OSVer = (Get-ItemProperty -Path 'HKLM:\SOFTWARE\Microsoft\Windows NT\CurrentVersion').LCUVer
   Dism.exe /Online /NoRestart /Disable-Feature /FeatureName:Microsoft-Windows-MicrosoftEdgeDevToolsClient /PackageName:Microsoft-Windows-Desktop-Required-ClientOnly-removable-Package~31bf3856ad364e35~$Arch~~$OSVer
   ````

   To remove a package from an offline image mounted at `c:\offline` type:

   ```powershell
   $OfflinePath = "C:\Offline"
   $Arch = dism /image:$OfflinePath /Get-DriverInfo /driver:hal.inf | findstr Architecture
   $Arch = $Arch.Split(':')[1]
   $Arch = $Arch.Trim()
   $OSVer = (Get-Command $OfflinePath\windows\system32\ntdll.dll).FileVersionInfo.ProductVersion
   Dism.exe /Image:$OfflinePath  /Disable-Feature /FeatureName:Microsoft-Windows-MicrosoftEdgeDevToolsClient /PackageName:Microsoft-Windows-Desktop-Required-ClientOnly-removable-Package~31bf3856ad364e35~$Arch~~$OSVer
   ```

1. Optional: Use DISM /GetFeatureInfo to get the status of a removable package type:

   ```powershell
   $Arch = $env:PROCESSOR_ARCHITECTURE
   $OSVer = (Get-ItemProperty -Path 'HKLM:\SOFTWARE\Microsoft\Windows NT\CurrentVersion').LCUVer
   Dism.exe /Online /Get-FeatureInfo /FeatureName:Microsoft-Windows-MicrosoftEdgeDevToolsClient /PackageName:Microsoft-Windows-Desktop-Required-ClientOnly-removable-Package~31bf3856ad364e35~$Arch~~$OSVer
   ````

## Package Details

### Package Size

| Release                             |   x64     |    ARM64    |
|-------------------------------------|:---------:|:-----------:|
| Windows 11 IoT Enterprise LTSC 2024 | 10,811 KB | 10,792 KB   |

### File List

| File Name | Installed Location |
|-----------|--------------------|
| microsoftedgedevtools.exe | %windir%\system32\microsoftedgedevtools.exe |
| assert.js | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\assert.js |
| button.css | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\button.css |
| common.bundle.js | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\common.bundle.js |
| common.css | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\common.css |
| commonmerged.js | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\commonmerged.js |
| controls.css | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\controls\controls.css |
| listcontrol.css | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\controls\listcontrol\listcontrol.css |
| cssutilities.js | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\cssutilities.js |
| cutcopypastecontextmenu.js | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\cutcopypastecontextmenu.js |
| datatreeview.css | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\datatreeview.css |
| daytonaoptout.js | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\daytonaoptout.js |
| dmbp.css | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\dommutations\dmbp.css |
| domdeleteallbreakpoints.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\dommutations\images\domdeleteallbreakpoints.png |
| domselectallbreakpoints.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\dommutations\images\domselectallbreakpoints.png |
| editor.css | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\editor\editor.css |
| editordefinitions.js | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\editor\editordefinitions.js |
| f12nls.js | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\editor\f12nls.js |
| encodingutilities.js | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\encodingutilities.js |
| jstreegridcontrol.js | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\external\jstreegridcontrol.js |
| base64.js | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\formatter\base64.js |
| cssemitter.js | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\formatter\css\cssemitter.js |
| cssformatter.js | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\formatter\css\cssformatter.js |
| cssformatworker.js | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\formatter\css\cssformatworker.js |
| cssparser.js | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\formatter\css\cssparser.js |
| formattedtextmapping.js | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\formatter\formattedtextmapping.js |
| formatter.js | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\formatter\formatter.js |
| formatteroptions.js | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\formatter\formatteroptions.js |
| formatworker.js | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\formatter\formatworker.js |
| htmlemitter.js | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\formatter\html\htmlemitter.js |
| htmlformatter.js | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\formatter\html\htmlformatter.js |
| htmlformatworker.js | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\formatter\html\htmlformatworker.js |
| htmlparser.js | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\formatter\html\htmlparser.js |
| htmltokenizer.js | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\formatter\html\htmltokenizer.js |
| htmlscriptfinder.js | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\formatter\htmlscriptfinder.js |
| iformatservice.js | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\formatter\iformatservice.js |
| position.js | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\formatter\position.js |
| sourcemapmappings.js | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\formatter\sourcemapmappings.js |
| sourcemapparser.js | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\formatter\sourcemapparser.js |
| sourcemapparserworker.js | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\formatter\sourcemapparserworker.js |
| sourcespan.js | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\formatter\sourcespan.js |
| sourcespanbuilder.js | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\formatter\sourcespanbuilder.js |
| statemachine.js | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\formatter\statemachine.js |
| formattertypescriptservices.js | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\formatter\typescript\formattertypescriptservices.js |
| formattertypescriptservices.nls.keys.js | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\formatter\typescript\formattertypescriptservices.nls.keys.js |
| unmappedtextmapping.js | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\formatter\unmappedtextmapping.js |
| workermessaging.js | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\formatter\workermessaging.js |
| commongridcontrol.css | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\grid\commongridcontrol.css |
| gridcelleditcontrol.js | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\grid\gridcelleditcontrol.js |
| gridcontrol.js | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\grid\gridcontrol.js |
| htmltreeview.css | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\htmltreeview.css |
| add_row.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\images\add_row.png |
| checkmark.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\images\checkmark.png |
| alphacolorbar.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\images\colorpicker\alphacolorbar.png |
| checkeredbackground.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\images\colorpicker\checkeredbackground.png |
| huecolorbar.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\images\colorpicker\huecolorbar.png |
| lightnesscolorbar.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\images\colorpicker\lightnesscolorbar.png |
| saturationcolorbar.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\images\colorpicker\saturationcolorbar.png |
| sliderbutton.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\images\colorpicker\sliderbutton.png |
| columnmove.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\images\columnmove.png |
| common_icons.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\images\common_icons.png |
| commonclose.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\images\commonclose.png |
| commonhelp.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\images\commonhelp.png |
| critical.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\images\critical.png |
| debuggernexttab.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\images\debuggernexttab.png |
| debuggerprevtab.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\images\debuggerprevtab.png |
| difficon.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\images\difficon.png |
| f12logo.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\images\f12logo.png |
| filepicker.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\images\filepicker.png |
| forcestoragecapstate.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\images\forcestoragecapstate.png |
| i_delete.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\images\i_delete.png |
| i_filtering_options.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\images\i_filtering_options.png |
| i_next.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\images\i_next.png |
| i_previous.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\images\i_previous.png |
| i_warning.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\images\i_warning.png |
| itemcollapsedicon.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\images\itemcollapsedicon.png |
| itemexpandedicon.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\images\itemexpandedicon.png |
| maximize.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\images\maximize.png |
| minimize.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\images\minimize.png |
| misc_icons.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\images\misc_icons.png |
| options.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\images\options.png |
| previewtabclose.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\images\previewtabclose.png |
| previewtabicon.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\images\previewtabicon.png |
| refresh.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\images\refresh.png |
| refreshstate.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\images\refreshstate.png |
| restore.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\images\restore.png |
| tabclose.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\images\tabclose.png |
| toggleprettyprint.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\images\toggleprettyprint.png |
| togglewordwrap.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\images\togglewordwrap.png |
| tree_icons.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\images\tree_icons.png |
| intellisense\intellisenselistbox.css | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\intellisense\intellisenselistbox.css |
| intellisense\intellisenseremotehelpers.js | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\intellisense\intellisenseremotehelpers.js |
| isdebugbuild.js | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\isdebugbuild.js |
| jquery\jquery.event.drag-2.2.js | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\jquery\jquery.event.drag-2.2.js |
| jquery\jquery-2.1.1.min.js | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\jquery\jquery-2.1.1.min.js |
| listbox.css | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\listbox.css |
| mediatypemanager.js | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\mediatypemanager.js |
| messagethrottle.js | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\messagethrottle.js |
| expandinglistview.css | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\modelview\expandinglistview.css |
| workermain.js | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\monaco-editor\min\vs\base\worker\workermain.js |
| coffee.js | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\monaco-editor\min\vs\basic-languages\src\coffee.js |
| csharp.js | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\monaco-editor\min\vs\basic-languages\src\csharp.js |
| css.js | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\monaco-editor\min\vs\basic-languages\src\css.js |
| html.js | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\monaco-editor\min\vs\basic-languages\src\html.js |
| less.js | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\monaco-editor\min\vs\basic-languages\src\less.js |
| scss.js | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\monaco-editor\min\vs\basic-languages\src\scss.js |
| xml.js | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\monaco-editor\min\vs\basic-languages\src\xml.js |
| editor.main.css | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\monaco-editor\min\vs\editor\editor.main.css |
| editor.main.js | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\monaco-editor\min\vs\editor\editor.main.js |
| editor.main.nls.js | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\monaco-editor\min\vs\editor\editor.main.nls.js |
| cssmode.js | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\monaco-editor\min\vs\language\css\cssmode.js |
| cssworker.js | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\monaco-editor\min\vs\language\css\cssworker.js |
| htmlmode.js | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\monaco-editor\min\vs\language\html\htmlmode.js |
| htmlworker.js | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\monaco-editor\min\vs\language\html\htmlworker.js |
| jsonmode.js | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\monaco-editor\min\vs\language\json\jsonmode.js |
| jsonworker.js | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\monaco-editor\min\vs\language\json\jsonworker.js |
| typescriptservices.js | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\monaco-editor\min\vs\language\typescript\lib\typescriptservices.js |
| mode.js | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\monaco-editor\min\vs\language\typescript\src\mode.js |
| worker.js | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\monaco-editor\min\vs\language\typescript\src\worker.js |
| loader.js | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\monaco-editor\min\vs\loader.js |
| monacoresolver.js | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\monacoresolver.js |
| objecttreeview.css | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\objectview\objecttreeview.css |
| common.f12.css | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\perftools\common.f12.css |
| commonplugin.css | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\perftools\commonplugin.css |
| gridcontrol.css | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\perftools\controls\gridcontrol.css |
| hubcontrols.js | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\perftools\controls\hubcontrols.js |
| menucontrol.css | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\perftools\controls\menucontrol.css |
| multilinegraph.css | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\perftools\controls\multilinegraph.css |
| renderer.css | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\perftools\controls\renderer.css |
| ruler.css | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\perftools\controls\ruler.css |
| scrollbar.css | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\perftools\controls\scrollbar.css |
| swimlane.css | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\perftools\controls\swimlane.css |
| custommark5_18x.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\perftools\images\custommark5_18x.png |
| i_appevent.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\perftools\images\i_appevent.png |
| i_checkered_background.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\perftools\images\i_checkered_background.png |
| i_open.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\perftools\images\i_open.png |
| i_save.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\perftools\images\i_save.png |
| i_sort_down.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\perftools\images\i_sort_down.png |
| i_sort_up.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\perftools\images\i_sort_up.png |
| i_start.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\perftools\images\i_start.png |
| i_stop.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\perftools\images\i_stop.png |
| i_usermark.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\perftools\images\i_usermark.png |
| perfremotehelpers.js | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\perftools\perfremotehelpers.js |
| tokenextractor.css | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\perftools\tokenextractor.css |
| etw.js | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\remote\etw.js |
| remotediagnostics.js | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\remote\remotediagnostics.js |
| rpc.js | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\remote\rpc.js |
| remoteeditstack.js | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\remoteeditstack.js |
| remotehelpers.js | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\remotehelpers.js |
| resourcesview.css | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\resourcesview\resourcesview.css |
| plugins\slick.rowselectionmodel.js | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\slickgrid\plugins\slick.rowselectionmodel.js |
| slick.core.js | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\slickgrid\slick.core.js |
| slick.dataview.js | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\slickgrid\slick.dataview.js |
| slick.editors.js | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\slickgrid\slick.editors.js |
| slick.formatters.js | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\slickgrid\slick.formatters.js |
| slick.grid.css | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\slickgrid\slick.grid.css |
| slick.grid.js | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\slickgrid\slick.grid.js |
| sharedtabcontrol.css | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\tabcontrol\sharedtabcontrol.css |
| toolwindow.css | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\toolwindow.css |
| toolwindow.f12.css | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\toolwindow.f12.css |
| trace.js | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\trace.js |
| uri.js | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\common\uri.js |
| console.html | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\console\console.html |
| global.css | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\console\global.css |
| breakpoints\breakpoints.css | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\debugger\breakpoints\breakpoints.css |
| addeventbreakpoint.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\debugger\breakpoints\images\addeventbreakpoint.png |
| addeventtracepoint.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\debugger\breakpoints\images\addeventtracepoint.png |
| addxhrbreakpoint.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\debugger\breakpoints\images\addxhrbreakpoint.png |
| breakpointdisabled.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\debugger\breakpoints\images\breakpointdisabled.png |
| breakpointglyph.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\debugger\breakpoints\images\breakpointglyph.png |
| breakpointunbound.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\debugger\breakpoints\images\breakpointunbound.png |
| conditionalbreakpoint.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\debugger\breakpoints\images\conditionalbreakpoint.png |
| deleteallbreakpoints.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\debugger\breakpoints\images\deleteallbreakpoints.png |
| editcurrentbreakpoint.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\debugger\breakpoints\images\editcurrentbreakpoint.png |
| eventbreakpoint.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\debugger\breakpoints\images\eventbreakpoint.png |
| eventbreakpointconditional.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\debugger\breakpoints\images\eventbreakpointconditional.png |
| eventbreakpointdisabled.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\debugger\breakpoints\images\eventbreakpointdisabled.png |
| eventbreakpointunbound.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\debugger\breakpoints\images\eventbreakpointunbound.png |
| eventtracepoint.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\debugger\breakpoints\images\eventtracepoint.png |
| eventtracepointdisabled.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\debugger\breakpoints\images\eventtracepointdisabled.png |
| eventtracepointunbound.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\debugger\breakpoints\images\eventtracepointunbound.png |
| selectallbreakpoints.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\debugger\breakpoints\images\selectallbreakpoints.png |
| tracepointbreakpoint.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\debugger\breakpoints\images\tracepointbreakpoint.png |
| xhrbreakpoint.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\debugger\breakpoints\images\xhrbreakpoint.png |
| xhrbreakpointdisabled.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\debugger\breakpoints\images\xhrbreakpointdisabled.png |
| xhrbreakpointunbound.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\debugger\breakpoints\images\xhrbreakpointunbound.png |
| activeframeglyph.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\debugger\callstack\images\activeframeglyph.png |
| instructionpointerglyph.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\debugger\callstack\images\instructionpointerglyph.png |
| currentlocationarrow.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\debugger\cursor\images\currentlocationarrow.png |
| debugger.bundle.js | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\debugger\debugger.bundle.js |
| debugger.css | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\debugger\debugger.css |
| debugger.html | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\debugger\debugger.html |
| breakall.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\debugger\images\breakall.png |
| breakonexceptions.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\debugger\images\breakonexceptions.png |
| breakworker.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\debugger\images\breakworker.png |
| contentscriptengineicon.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\debugger\images\contentscriptengineicon.png |
| continue.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\debugger\images\continue.png |
| copytoclipboard.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\debugger\images\copytoclipboard.png |
| cssfileicon.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\debugger\images\cssfileicon.png |
| difftabicon.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\debugger\images\difftabicon.png |
| disconnecticon.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\debugger\images\disconnecticon.png |
| filesnodeicon.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\debugger\images\filesnodeicon.png |
| functionicon.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\debugger\images\functionicon.png |
| functioniconmapped.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\debugger\images\functioniconmapped.png |
| htmlfileicon.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\debugger\images\htmlfileicon.png |
| librarycodeicon.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\debugger\images\librarycodeicon.png |
| notafunctionicon.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\debugger\images\notafunctionicon.png |
| notafunctioniconmapped.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\debugger\images\notafunctioniconmapped.png |
| redirecticon.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\debugger\images\redirecticon.png |
| returnvalue.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\debugger\images\returnvalue.png |
| saveicon.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\debugger\images\saveicon.png |
| scriptfileicon.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\debugger\images\scriptfileicon.png |
| search.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\debugger\images\search.png |
| stepinto.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\debugger\images\stepinto.png |
| stepout.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\debugger\images\stepout.png |
| stepover.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\debugger\images\stepover.png |
| togglesourcemap.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\debugger\images\togglesourcemap.png |
| toolbarmycodeicon.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\debugger\images\toolbarmycodeicon.png |
| tsfileicon.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\debugger\images\tsfileicon.png |
| clearresults.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\debugger\languageservice\images\clearresults.png |
| debuggerclose.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\debugger\languageservice\images\debuggerclose.png |
| findresults.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\debugger\languageservice\images\findresults.png |
| nextresult.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\debugger\languageservice\images\nextresult.png |
| pin.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\debugger\languageservice\images\pin.png |
| previousresult.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\debugger\languageservice\images\previousresult.png |
| unpin.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\debugger\languageservice\images\unpin.png |
| debuggerdiagremote.js | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\debugger\remote\debuggerdiagremote.js |
| debuggerremote.js | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\debugger\remote\debuggerremote.js |
| addwatch.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\debugger\watches\images\addwatch.png |
| deleteall.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\debugger\watches\images\deleteall.png |
| watches.css | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\debugger\watches\watches.css |
| dom.html | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\dom\dom.html |
| domexplorer.css | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\dom\domexplorer.css |
| domexplorer.f12.css | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\dom\domexplorer.f12.css |
| domexplorermerged.js | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\dom\domexplorermerged.js |
| domexplorerremote.js | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\dom\domexplorerremote.js |
| domtree.css | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\dom\domtree\domtree.css |
| events.css | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\dom\events.css |
| accessibility.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\dom\images\accessibility.png |
| addnewruleicon.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\dom\images\addnewruleicon.png |
| breadcrumbscrollleft.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\dom\images\breadcrumbscrollleft.png |
| breadcrumbscrolllefthover.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\dom\images\breadcrumbscrolllefthover.png |
| breadcrumbscrollright.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\dom\images\breadcrumbscrollright.png |
| breadcrumbscrollrighthover.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\dom\images\breadcrumbscrollrighthover.png |
| checkered_background.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\dom\images\checkered_background.png |
| eventscollapseall.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\dom\images\eventscollapseall.png |
| i_error.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\dom\images\i_error.png |
| i_inspect.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\dom\images\i_inspect.png |
| i_just_my_code.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\dom\images\i_just_my_code.png |
| i_refresh.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\dom\images\i_refresh.png |
| i_show_layout.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\dom\images\i_show_layout.png |
| i_show_pseudo_classes.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\dom\images\i_show_pseudo_classes.png |
| red_squiggly.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\dom\images\red_squiggly.png |
| inspect.html | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\dom\inspect.html |
| layout.css | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\dom\layout.css |
| changesview.css | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\dom\styles\changesview\changesview.css |
| styleview.css | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\dom\styles\styleview\styleview.css |
| winningstyles.css | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\dom\styles\winningview\winningstyles.css |
| emulation.bundle.js | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\emulation\emulation.bundle.js |
| emulation.css | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\emulation\emulation.css |
| emulation.html | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\emulation\emulation.html |
| i_persistsettings.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\emulation\i_persistsettings.png |
| i_resetsettings.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\emulation\i_resetsettings.png |
| infobutton.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\emulation\infobutton.png |
| emulationremote.bundle.js | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\emulation\remote\emulationremote.bundle.js |
| f12host.css | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\f12host\f12host.css |
| f12host.html | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\f12host\f12host.html |
| f12host.js | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\f12host\f12host.js |
| pluginhostshim.bundle.js | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\f12host\pluginhostshim.bundle.js |
| popupwindow.bundle.js | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\f12host\popupwindow.bundle.js |
| uwp.bundle.js | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\f12host\uwp.bundle.js |
| console.bundle.js | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\frontend\console.bundle.js |
| closeerrorbox.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\frontend\host\api\data\closeerrorbox.png |
| f12.css | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\frontend\host\api\data\f12.css |
| helperrorbox.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\frontend\host\api\data\helperrorbox.png |
| i_alerterror.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\frontend\host\api\data\i_alerterror.png |
| i_alertinfo.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\frontend\host\api\data\i_alertinfo.png |
| plugin.css | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\frontend\host\api\data\plugin.css |
| header.css | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\header\header.css |
| header.html | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\header\header.html |
| headermerged.js | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\header\headermerged.js |
| badgealert.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\header\images\badgealert.png |
| badgebreak.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\header\images\badgebreak.png |
| badgeinfo.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\header\images\badgeinfo.png |
| badgerunning.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\header\images\badgerunning.png |
| console.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\header\images\console.png |
| dockh.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\header\images\dockh.png |
| dockv.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\header\images\dockv.png |
| emulation.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\header\images\emulation.png |
| emulationcombo.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\header\images\emulationcombo.png |
| feedback.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\header\images\feedback.png |
| foreground.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\header\images\foreground.png |
| headerbadgeerror.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\header\images\headerbadgeerror.png |
| headercheckmark.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\header\images\headercheckmark.png |
| headerclose.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\header\images\headerclose.png |
| headerhelp.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\header\images\headerhelp.png |
| headermaximize.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\header\images\headermaximize.png |
| headerminimize.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\header\images\headerminimize.png |
| headerrestore.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\header\images\headerrestore.png |
| navoverflow_break.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\header\images\navoverflow_break.png |
| navoverflow_info.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\header\images\navoverflow_info.png |
| navoverflow_start.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\header\images\navoverflow_start.png |
| navoverflow_warning.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\header\images\navoverflow_warning.png |
| nexttab.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\header\images\nexttab.png |
| overflow.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\header\images\overflow.png |
| prevtab.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\header\images\prevtab.png |
| undock.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\header\images\undock.png |
| headerremote.js | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\header\remote\headerremote.js |
| i_foldin.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\memoryanalyzer\images\i_foldin.png |
| i_info.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\memoryanalyzer\images\i_info.png |
| i_snapshot.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\memoryanalyzer\images\i_snapshot.png |
| i_table_options.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\memoryanalyzer\images\i_table_options.png |
| status_heap_decrease.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\memoryanalyzer\images\status_heap_decrease.png |
| status_heap_increase.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\memoryanalyzer\images\status_heap_increase.png |
| takesnapshot.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\memoryanalyzer\images\takesnapshot.png |
| memoryanalyzer.bundle.js | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\memoryanalyzer\memoryanalyzer.bundle.js |
| memoryanalyzer.css | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\memoryanalyzer\memoryanalyzer.css |
| memoryanalyzer.f12.css | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\memoryanalyzer\memoryanalyzer.f12.css |
| memoryanalyzer.html | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\memoryanalyzer\memoryanalyzer.html |
| memoryanalyzerremote.bundle.js | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\memoryanalyzer\memoryanalyzerremote.bundle.js |
| snapshottileview.css | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\memoryanalyzer\snapshottileview.css |
| tabcontrol.css | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\memoryanalyzer\tabcontrol.css |
| i_bypassserviceworkers.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\network\images\i_bypassserviceworkers.png |
| i_clearcache.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\network\images\i_clearcache.png |
| i_clearcookies.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\network\images\i_clearcookies.png |
| i_clearonnavigate.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\network\images\i_clearonnavigate.png |
| i_clearsession.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\network\images\i_clearsession.png |
| i_refreshserver.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\network\images\i_refreshserver.png |
| networkbadgeerror.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\network\images\networkbadgeerror.png |
| networkstatus-error.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\network\images\networkstatus-error.png |
| networkstatus-ok.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\network\images\networkstatus-ok.png |
| networkstatus-warning.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\network\images\networkstatus-warning.png |
| network.bundle.js | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\network\network.bundle.js |
| network.html | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\network\network.html |
| remote\networkremote.bundle.js | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\network\remote\networkremote.bundle.js |
| remote\networkremotehelpers.bundle.js | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\network\remote\networkremotehelpers.bundle.js |
| styles\network.css | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\network\styles\network.css |
| styles\networkgrid.css | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\network\styles\networkgrid.css |
| styles\networkruler.css | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\network\styles\networkruler.css |
| popup.css | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\popup\popup.css |
| popup.html | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\popup\popup.html |
| console.remote.bundle.js | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\remote\console\console.remote.bundle.js |
| serviceworkericon.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\serviceworker\images\serviceworkericon.png |
| serviceworkerremote.bundle.js | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\serviceworker\remote\serviceworkerremote.bundle.js |
| serviceworker.bundle.js | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\serviceworker\serviceworker.bundle.js |
| serviceworker.css | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\serviceworker\serviceworker.css |
| serviceworker.html | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\serviceworker\serviceworker.html |
| cacheicon.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\storage\images\cacheicon.png |
| clearcookies.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\storage\images\clearcookies.png |
| clearsessioncookies.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\storage\images\clearsessioncookies.png |
| cookies.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\storage\images\cookies.png |
| gridheaderhttponly.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\storage\images\gridheaderhttponly.png |
| gridheadersecure.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\storage\images\gridheadersecure.png |
| localstorage.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\storage\images\localstorage.png |
| storageremote.bundle.js | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\storage\remote\storageremote.bundle.js |
| storage.bundle.js | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\storage\storage.bundle.js |
| storage.css | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\storage\storage.css |
| storage.html | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\storage\storage.html |
| datacategorystyles.css | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\visualprofiler\datacategorystyles.css |
| i_chartselection_clear.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\visualprofiler\images\i_chartselection_clear.png |
| i_chartselection_clear_disabled.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\visualprofiler\images\i_chartselection_clear_disabled.png |
| i_chartzoom_in.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\visualprofiler\images\i_chartzoom_in.png |
| i_chartzoom_in_disabled.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\visualprofiler\images\i_chartzoom_in_disabled.png |
| i_chartzoom_reset.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\visualprofiler\images\i_chartzoom_reset.png |
| i_chartzoom_reset_disabled.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\visualprofiler\images\i_chartzoom_reset_disabled.png |
| i_f12_chartselection_clear.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\visualprofiler\images\i_f12_chartselection_clear.png |
| i_f12_chartzoom_in.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\visualprofiler\images\i_f12_chartzoom_in.png |
| i_f12_chartzoom_reset.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\visualprofiler\images\i_f12_chartzoom_reset.png |
| i_f12_context_chartselection_clear.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\visualprofiler\images\i_f12_context_chartselection_clear.png |
| i_f12_context_chartselection_clear_disabled.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\visualprofiler\images\i_f12_context_chartselection_clear_disabled.png |
| i_f12_context_chartzoom_in.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\visualprofiler\images\i_f12_context_chartzoom_in.png |
| i_f12_context_chartzoom_in_disabled.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\visualprofiler\images\i_f12_context_chartzoom_in_disabled.png |
| i_f12_context_chartzoom_reset.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\visualprofiler\images\i_f12_context_chartzoom_reset.png |
| i_f12_context_chartzoom_reset_disabled.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\visualprofiler\images\i_f12_context_chartzoom_reset_disabled.png |
| i_frame_grouping.png | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\visualprofiler\images\i_frame_grouping.png |
| divider.css | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\visualprofiler\js\controls\divider.css |
| cpuusagetreegrid.css | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\visualprofiler\js\cpuusage\cpuusagetreegrid.css |
| grid.css | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\visualprofiler\js\cpuusage\grid.css |
| messageoverlaycontrol.css | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\visualprofiler\js\cpuusage\messageoverlaycontrol.css |
| stackedbarchart.css | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\visualprofiler\js\hubgraphs\stackedbarchart.css |
| visualprofiler.bundle.js | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\visualprofiler\visualprofiler.bundle.js |
| visualprofiler.css | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\visualprofiler\visualprofiler.css |
| visualprofiler.f12.css | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\visualprofiler\visualprofiler.f12.css |
| visualprofiler.html | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\23\visualprofiler\visualprofiler.html |
| appxblockmap.xml | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\appxblockmap.xml |
| appxmanifest.xml | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\appxmanifest.xml |
| appxsignature.p7x | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\appxsignature.p7x |
| resources.pri | %windir%\systemapps\microsoft.microsoftedgedevtoolsclient_8wekyb3d8bbwe\resources.pri |

## More Resources

- [Removable Packages](/windows/iot/iot-enterprise/Optimize-Your-Device/Removable-Packages)
- [Reduce Disk Footprint](/windows/iot/iot-enterprise/Optimize-Your-Device/Reduce-Disk-Footprint)
- [Device Optimization Overview](/windows/iot/iot-enterprise/Optimize-Your-Device/Overview)
