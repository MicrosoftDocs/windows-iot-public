---
title: Removable Package Microsoft-Windows-AppManagment-UEV
author: twarwick
ms.author: twarwick
ms.date: 12/20/2022
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: Removable Package Details for Microsoft-Windows-AppManagment-UEV
keywords: IoT Enterprise, removable packages, storage
---

# Removable Package: Microsoft-Windows-AppManagment-UEV
## Microsoft-Windows-AppManagment-UEV
See [User Experience Virtualization](/windows/configuration/ue-v/uev-for-windows) for a detailed description of this Windows feature.

Approximate on-disk footprint: 13,752 KB

## Removing Package

### Online Servicing 
Use the [DISM command-line tool](/windows-hardware/manufacture/desktop/what-is-dism) with the ```/Online``` command-line parameter to remove a single package via online servicing .

```powershell
Dism.exe /Online /LogPath:%WINDIR%\Temp\Microsoft-Windows-AppManagment-UEV.log /NoRestart /Disable-Feature /FeatureName:Microsoft-Windows-AppManagment-UEV /PackageName:@Package
````
### Offline Servicing
Use the [DISM command-line tool](/windows-hardware/manufacture/desktop/what-is-dism) with the ```/Image:<image path>``` command-line parameter to remove a single package via offline servicing.

```powershell
Dism.exe /Image:c:\offline /LogPath:%WINDIR%\Temp\Microsoft-Windows-AppManagment-UEV.log /NoRestart /Disable-Feature /FeatureName:Microsoft-Windows-AppManagment-UEV /PackageName:@Package
````

## File List

| File Name | Installed Location |
|-----------|--------------------|
| desktopsettings2013.xml                    | %programdata%\microsoft\uev\inboxtemplates\desktopsettings2013.xml | 
| easeofaccesssettings2013.xml               | %programdata%\microsoft\uev\inboxtemplates\easeofaccesssettings2013.xml |
| microsoftinternetexplorer2013.xml          | %programdata%\microsoft\uev\inboxtemplates\microsoftinternetexplorer2013.xml |
| microsoftinternetexplorer2013backup.xml    | %programdata%\microsoft\uev\inboxtemplates\microsoftinternetexplorer2013backup.xml |
| microsoftlync2010.xml                      | %programdata%\microsoft\uev\inboxtemplates\microsoftlync2010.xml |
| microsoftlync2013win32.xml                 | %programdata%\microsoft\uev\inboxtemplates\microsoftlync2013win32.xml |
| microsoftlync2013win64.xml                 | %programdata%\microsoft\uev\inboxtemplates\microsoftlync2013win64.xml |
| microsoftnotepad.xml                       | %programdata%\microsoft\uev\inboxtemplates\microsoftnotepad.xml |
| microsoftoffice2010win32.xml               | %programdata%\microsoft\uev\inboxtemplates\microsoftoffice2010win32.xml |
| microsoftoffice2010win64.xml               | %programdata%\microsoft\uev\inboxtemplates\microsoftoffice2010win64.xml |
| microsoftoffice2013backupwin32.xml         | %programdata%\microsoft\uev\inboxtemplates\microsoftoffice2013backupwin32.xml |
| microsoftoffice2013backupwin64.xml         | %programdata%\microsoft\uev\inboxtemplates\microsoftoffice2013backupwin64.xml |
| microsoftoffice2013office365win32.xml      | %programdata%\microsoft\uev\inboxtemplates\microsoftoffice2013office365win32.xml |
| microsoftoffice2013office365win64.xml      | %programdata%\microsoft\uev\inboxtemplates\microsoftoffice2013office365win64.xml |
| microsoftoffice2013win32.xml               | %programdata%\microsoft\uev\inboxtemplates\microsoftoffice2013win32.xml |
| microsoftoffice2013win64.xml               | %programdata%\microsoft\uev\inboxtemplates\microsoftoffice2013win64.xml |
| microsoftoffice2016backupwin32.xml         | %programdata%\microsoft\uev\inboxtemplates\microsoftoffice2016backupwin32.xml |
| microsoftoffice2016backupwin64.xml         | %programdata%\microsoft\uev\inboxtemplates\microsoftoffice2016backupwin64.xml |
| microsoftoffice2016win32.xml               | %programdata%\microsoft\uev\inboxtemplates\microsoftoffice2016win32.xml |
| microsoftoffice2016win64.xml               | %programdata%\microsoft\uev\inboxtemplates\microsoftoffice2016win64.xml |
| microsoftoutlook2013cawin32.xml            | %programdata%\microsoft\uev\inboxtemplates\microsoftoutlook2013cawin32.xml |
| microsoftoutlook2013cawin64.xml            | %programdata%\microsoft\uev\inboxtemplates\microsoftoutlook2013cawin64.xml |
| microsoftoutlook2016cawin32.xml            | %programdata%\microsoft\uev\inboxtemplates\microsoftoutlook2016cawin32.xml |
| microsoftoutlook2016cawin64.xml            | %programdata%\microsoft\uev\inboxtemplates\microsoftoutlook2016cawin64.xml |
| microsoftskypeforbusiness2016win32.xml     | %programdata%\microsoft\uev\inboxtemplates\microsoftskypeforbusiness2016win32.xml |
| microsoftskypeforbusiness2016win64.xml     | %programdata%\microsoft\uev\inboxtemplates\microsoftskypeforbusiness2016win64.xml |
| microsoftwordpad.xml                       | %programdata%\microsoft\uev\inboxtemplates\microsoftwordpad.xml |
| networkprinters.xml                        | %programdata%\microsoft\uev\inboxtemplates\networkprinters.xml |
| roamingcredentialsettings.xml              | %programdata%\microsoft\uev\inboxtemplates\roamingcredentialsettings.xml |
| themesettings2013.xml                      | %programdata%\microsoft\uev\inboxtemplates\themesettings2013.xml |
| vdistate.xml                               | %programdata%\microsoft\uev\inboxtemplates\vdistate.xml |
| registerinboxtemplates.ps1                 | %programdata%\microsoft\uev\scripts\registerinboxtemplates.ps1 |
| settingslocationtemplate.xsd               | %programdata%\microsoft\uev\templates\settingslocationtemplate.xsd |
| settingslocationtemplate2013.xsd           | %programdata%\microsoft\uev\templates\settingslocationtemplate2013.xsd |
| settingslocationtemplate2013a.xsd          | %programdata%\microsoft\uev\templates\settingslocationtemplate2013a.xsd |
| userexperiencevirtualization.admx          | %windir%\policydefinitions\userexperiencevirtualization.admx |
| agentservice.exe                           | %windir%\system32\agentservice.exe |
| applysettingstemplatecatalog.exe           | %windir%\system32\applysettingstemplatecatalog.exe |
| uevagentdriver.sys                         | %windir%\system32\drivers\uevagentdriver.sys |
| microsoft.uev.agentdriverevents.dll        | %windir%\system32\microsoft.uev.agentdriverevents.dll |
| microsoft.uev.appagent.dll                 | %windir%\system32\microsoft.uev.appagent.dll |
| microsoft.uev.cabutil.dll                  | %windir%\system32\microsoft.uev.cabutil.dll |
| microsoft.uev.cmutil.dll                   | %windir%\system32\microsoft.uev.cmutil.dll |
| microsoft.uev.common.dll                   | %windir%\system32\microsoft.uev.common.dll |
| microsoft.uev.common.winrt.dll             | %windir%\system32\microsoft.uev.common.winrt.dll |
| microsoft.uev.commonbridge.dll             | %windir%\system32\microsoft.uev.commonbridge.dll |
| microsoft.uev.configwrapper.dll            | %windir%\system32\microsoft.uev.configwrapper.dll |
| microsoft.uev.cscunpintool.exe             | %windir%\system32\microsoft.uev.cscunpintool.exe |
| microsoft.uev.eventlogmessages.dll         | %windir%\system32\microsoft.uev.eventlogmessages.dll |
| microsoft.uev.localsyncprovider.dll        | %windir%\system32\microsoft.uev.localsyncprovider.dll |
| microsoft.uev.managedeventlogging.dll      | %windir%\system32\microsoft.uev.managedeventlogging.dll |
| microsoft.uev.management.dll               | %windir%\system32\microsoft.uev.management.dll |
| microsoft.uev.management.wmiaccess.dll     | %windir%\system32\microsoft.uev.management.wmiaccess.dll |
| microsoft.uev.modernappagent.dll           | %windir%\system32\microsoft.uev.modernappagent.dll |
| microsoft.uev.modernappcore.dll            | %windir%\system32\microsoft.uev.modernappcore.dll |
| microsoft.uev.modernappdata.winrt.dll      | %windir%\system32\microsoft.uev.modernappdata.winrt.dll |
| microsoft.uev.modernsync.dll               | %windir%\system32\microsoft.uev.modernsync.dll |
| microsoft.uev.monitorsyncprovider.dll      | %windir%\system32\microsoft.uev.monitorsyncprovider.dll |
| microsoft.uev.office2010customactions.dll  | %windir%\system32\microsoft.uev.office2010customactions.dll |
| microsoft.uev.office2013customactions.dll  | %windir%\system32\microsoft.uev.office2013customactions.dll |
| microsoft.uev.printercustomactions.dll     | %windir%\system32\microsoft.uev.printercustomactions.dll |
| microsoft.uev.smbsyncprovider.dll          | %windir%\system32\microsoft.uev.smbsyncprovider.dll
| microsoft.uev.synccommon.dll               | %windir%\system32\microsoft.uev.synccommon.dll |
| microsoft.uev.syncconditions.dll           | %windir%\system32\microsoft.uev.syncconditions.dll |
| microsoft.uev.synccontroller.exe           | %windir%\system32\microsoft.uev.synccontroller.exe |
| uevagentpolicygenerator.exe                | %windir%\system32\uevagentpolicygenerator.exe |
| uevappmonitor.exe                          | %windir%\system32\uevappmonitor.exe |
| uevappmonitor.exe.config                   | %windir%\system32\uevappmonitor.exe.config |
| uevcustomactiontypes.tlb                   | %windir%\system32\uevcustomactiontypes.tlb |
| uevtemplatebaselinegenerator.exe           | %windir%\system32\uevtemplatebaselinegenerator.exe |
| uevtemplateconfigitemgenerator.exe         | %windir%\system32\uevtemplateconfigitemgenerator.exe |
| agentwmi.mof                               | %windir%\system32\wbem\agentwmi.mof |
| agentwmiuninstall.mof                      | %windir%\system32\wbem\agentwmiuninstall.mof |
| microsoft.uev.agentwmi.dll                 | %windir%\system32\wbem\microsoft.uev.agentwmi.dll |
| microsoft.uev.managedagentwmi.mof          | %windir%\system32\wbem\microsoft.uev.managedagentwmi.mof |
| microsoft.uev.managedagentwmiuninstall.mof | %windir%\system32\wbem\microsoft.uev.managedagentwmiuninstall.mof |
| microsoft.uev.commands.dll                 | %windir%\system32\windowspowershell\v1.0\modules\uev\microsoft.uev.commands.dll |
| uev.psd1                                   | %windir%\system32\windowspowershell\v1.0\modules\uev\uev.psd1 |
| uev.types.ps1xml                           | %windir%\system32\windowspowershell\v1.0\modules\uev\uev.types.ps1xml |
| microsoft.uev.managedagentwmi.dll          | microsoft.uev.managedagentwmi.dll |
| microsoft.uev.managedagentwmi.winrt.dll    | microsoft.uev.managedagentwmi.winrt.dll |

## More Resources
- [Removable Packages](/windows/iot/iot-enterprise/Optimize-Your-Device/Removable-Packages-Details/Removable-Packages.md)
- [Reduce Disk Footprint](/windows/iot/iot-enterprise/Optimize-Your-Device/Reduce-Disk-Footprint.md)
- [Device Optimization Overview](/windows/iot/iot-enterprise/Optimize-Your-Device/Overview.md)
