---
title: Unified Write Filter (UWF) feature (uwf-turnonuwf)
description: Unified Write Filter (UWF) feature (uwf-turnonuwf)
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
author: TerryWarwick
ms.author: twarwick
ms.prod: windows-iot
ms.technology: iot
ms.date: 10/02/2018
ms.topic: article
ms.custom: RS5
---
# Use the Unified Write Filter (UWF) feature

The Unified Write Filter (UWF) is an Windows 10 optional feature. 

To use UWF, you'll first need to install the feature.

Next, you'll enable (and optionally configure) the feature. The first time you enable UWF on your device, UWF makes the following changes to your system to improve the performance of UWF:
   * Paging files are disabled.
   * System restore is disabled.
   * SuperFetch (aka "SysMain" service) is disabled.
   * File indexing service is turned off.
   * Fast boot is disabled.
   * Defragmentation service (aka "Optimize drives" service) is turned off.
   * BCD setting **bootstatuspolicy** is set to **ignoreallfailures**.

After UWF is enabled, you can finally select a drive to protect and start using UWF. If you'll disable after enable it, features above will not be turned on automatically. 

You can install UWF for running PCs and devices, prepare it for customized Windows images, or manage it remotely using CSP or WMI.

## Turn on UWF on a running PC

1. Install the feature:

   1. Click Start, type **Turn Windows features on or off**.

   1. In the **Windows Features** window, expand the **Device Lockdown** node, and check **Unified Write Filter** > **OK**.  

      The **Windows Features** window indicates Windows is searching for required files and displays a progress bar. Once found, the window indicates Windows is applying the changes. When completed, the window indicates the requested changes are completed.

   1. Click **Close** to close the **Windows Features** window.

2. Enable the filter:

   ```cmd
   uwfmgr filter enable
   ```
   > [!Note]
   > After you run this command, restart the computer and exit the servicing mode, the following things are disabled:
   > - Windows Update (by setting HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows\WindowsUpdate\AU\NoAutoUpdate.)
   > - Windows Store Update (by setting HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\WindowsStore\AutoDownload.)
   > - Registry Reorganization (by setting HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\Session Manager\Configuration Manager\RegistryReorganizationLimitDays.)
   > - Maintenance Hour (by setting HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Schedule\Maintenance\MaintenanceDisabled.)
   >
   > After you run `uwfmgr filter disable`, restart the computer and enter the serving mode, the changes will be reverted.   

3. Enable write protection for a drive:

   ```cmd
   uwfmgr.exe volume protect C:
   ```

4. Restart your computer.

5. Confirm that UWF is running:

   ```cmd
   uwfmgr.exe get-config
   ```

## Install UWF on a customized Windows image

1. Open a command prompt with administrator privileges.
1. Copy install.wim to a temporary folder on hard drive (in the following steps, we'll assume it's called C:\\wim).
1. Create a new directory.

   ```cmd
   md c:\wim
   ```

1. Mount the image.

   ```cmd
   dism /mount-wim /wimfile:c:\bootmedia\sources\install.wim /index:1 /MountDir:c:\wim
   ```

1. Enable the feature.

   ```cmd
   dism /image:c:\wim /enable-feature /featureName:Client-UnifiedWriteFilter
   ```

1. Commit the change.

   ```cmd
   dism /unmount-wim /MountDir:c:\wim /Commit
   ```

To activate UWF, you can use a command-line script, CSP, or WMI: 
  * [CMD](uwfmgrexe.md): `uwfmgr filter enable`, then `uwfmgr.exe volume protect C:`
  * [CSP](/windows/client-management/mdm/unifiedwritefilter-csp): `CurrentSession/FilterEnabled`, then `CurrentSession/Volume`
  * [WMI](uwf-wmi-provider-reference.md): `UWF\Filter.Enable`, then `UWF\Volume`.

## Install the UWF feature by using Windows Configuration Designer

1. Create a provisioning package in Windows Configuration Designer by following the instructions in [Create a provisioning package](/windows/configuration/provisioning-packages/provisioning-create-package).

   > [!Note]
   > When setting the file exclusion in Windows Configuration Designer, you do not need to specify the drive letter since that is already input via the Volume protection setting. For example, if the file being excluded is `C:\testdir\test.txt`, after adding a drive in Volume protection, you only need to input `\testdir\test.txt` to add this file exclusion.

1. In the Available customizations page, select **Runtime settings** &gt; **SMISettings** and then set the value for the Unified Write Filter setting.

1. Once you have finished configuring the settings and building the provisioning package, you can apply the package to the image deployment time or runtime. See [Apply a provisioning package](/windows/configuration/provisioning-packages/provisioning-apply-package) for more information.

To activate UWF, you can use a command-line script, CSP, or WMI: 
  * [CMD](uwfmgrexe.md): `uwfmgr filter enable`, then `uwfmgr.exe volume protect C:`
  * [CSP](/windows/client-management/mdm/unifiedwritefilter-csp): `CurrentSession/FilterEnabled`, then `CurrentSession/Volume`
  * [WMI](uwf-wmi-provider-reference.md): `UWF\Filter.Enable`, then `UWF\Volume`.

## Install the UWF feature by using Windows Management Instrumentation (WMI)

If Windows has already been installed and you do not want to use a provisioning package, you can also configure UWF by using the Windows Management Instrumentation (WMI) providers. To turn on UWF using WMI, you can use the [UWF_Filter](uwf-filter.md) function, specifically the [UWF_Filter.Enable](uwf-filterenable.md) method. You can do this in one of the following ways:

* Use the WMI providers directly in a PowerShell script.
* Use the WMI providers directly in an application.
* Use the command line tool, [uwfmgr.exe](uwfmgrexe.md).

You must restart your device after you turn on or turn off UWF before the change takes effect.


You can change these settings after you turn on UWF if you want to. For example, you can move the page file location to an unprotected volume and re-enable paging files.

> [!Important]
> If you add UWF to your image by using SMI settings in an unattend.xml file, turning on UWF only sets the **bootstatuspolicy** BCD setting and turns off the defragmentation service. In this case, you must manually turn off the other features and services if you want to increase the performance of UWF.

All configuration settings for UWF are stored in the registry. UWF automatically excludes these registry entries from filtering.

UWF maintains configuration settings in the registry for the current session and for the next session after a device restart. Static configuration changes do not take effect until after a device restart, and these changes are saved in the registry entries for the next session. Dynamic configuration changes occur immediately and persist after a device restart.


## Related topics

[Unified Write Filter](unified-write-filter.md)

[Unified Write Filter WMI provider reference](uwf-wmi-provider-reference.md)

UWF Command-line tool: [uwfmgr.exe](uwfmgrexe.md)
