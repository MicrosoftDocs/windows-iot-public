---
title: uwfmgr.exe
description: uwfmgr.exe
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: f833b9e7-54e4-4615-9eed-22ab805a218b
author: TerryWarwick
ms.author: twarwick
ms.prod: windows-iot
ms.technology: iot
ms.date: 10/02/2018
ms.topic: article


---
# uwfmgr.exe

The UWFMgr tool can be used at the command-line or in PowerShell to configure and retrieve settings for [Unified Write Filter (UWF)](unified-write-filter.md).

> [!Important]
> Users with standard accounts can use commands that retrieve information, but only users who have administrator accounts can use commands that change the configuration settings.

## Syntax

```powershell
uwfmgr.exe
    Help | ?
    Get-Config
    Filter
        Help | ?
        Enable
        Disable
        Reset-Settings
        Shutdown
        Restart
    Volume
        Help | ?
        Get-Config {<volume> | all}
        Protect {<volume> | all}
        Unprotect <volume>
    File
        Help | ?
        Get-Exclusions {<volume> | all}
        Add-Exclusion <file>
        Remove-Exclusion <file>
        Commit <file>
        Commit-Delete <file>
    Registry
        Help | ?
        Get-Exclusions
        Add-Exclusion <key>
        Remove-Exclusion <key>
        Commit <key> [<value>]
        Commit-Delete <key> [<value>]
    Overlay
        Help | ?
        Get-Config
        Get-AvailableSpace
        Get-Consumption
        Set-Size <size>
        Set-Type {RAM | DISK}
        Set-WarningThreshold <size>
        Set-CriticalThreshold <size>
        Set-Passthrough <on/off>
        Set-Persistent <on/off>
        Reset-PersistentState <on/off>
    Servicing
        Enable
        Disable
        Update-Windows
        Get-Config
        Help
```

## Location

**Uwfmgr** can be found under the %WINDIR%\\System32\\ folder.

## Command-line options and parameters

The following list describes the options and sub-options that are available to use in **uwfmgr.exe**, and it lists the corresponding WMI class or method for each command-line option and sub-option (if available).

* **Help | ?**
  * Displays command-line help for basic parameters for **uwfmgr.exe**.
* **Get-Config**
  * Displays UWF configuration settings for the current and next session.
* **Filter**
  * Configures basic UWF settings.
  * [UWF\_Filter](uwf-filter.md)
  * *Enable*
    * Enables UWF protection for the next session after a system restart.
    * [UWF\_Filter.Enable](uwf-filterenable.md)
  * *Disable*
    * Disables UWF protection for the next session after a system restart.
    * [UWF\_Filter.Disable](uwf-filterdisable.md)
  * *Reset-Settings*
    * Restores UWF settings to the original state.<br/>If you added UWF to your image by using **Turn Windows features on or off** or by using DISM, the original state is the state of UWF settings when UWF was first enabled. <br/>If you added UWF to your image by using SMI settings in an unattend file, the original state is the state of UWF settings when Windows was installed on the device. **Starting in Windows 10, this command is no longer supported.**
    * [UWF\_Filter.ResetSettings](uwf-filterresetsettings.md)
  * *Shutdown*
    * Shuts down the device immediately, even if the overlay is full or near full. Administrator-level permissions are required to use this command.
    * [UWF\_Filter.ShutdownSystem](uwf-filtershutdownsystem.md)
  * *Restart*
    * Shuts down the device immediately and restarts, even if the overlay is full or near full. Administrator-level permissions are required to use this command.
    * [UWF\_Filter.RestartSystem](uwf-filterrestartsystem.md)
* **Volume**
  * Configures settings for volumes protected by UWF. If the *&lt;volume&gt;* argument is needed, you can specify a drive letter (for example, `uwfmgr.exe volume protect C:`), or else you can specify all volumes (for example, `uwfmgr.exe volume get-config all`).
  * [UWF\_Volume](uwf-volume.md)
  * *Help | ?*
    * Displays command-line help for the `uwfmgr.exe volume` command.
  * *Get-Config* {*&lt;volume&gt;* | all}
    * Displays configuration settings and file exclusions for the specified volume, or all volumes if **all** is specified. Displays information for both the current and the next session.
    * [UWF\_Volume](uwf-volume.md)
  * *Protect* {*&lt;volume&gt;* | all}
    * Adds the specified volume to the list of volumes that are protected by UWF. UWF starts protecting the volume after the next system restart if UWF filtering is enabled.
    * [UWF\_Volume.Protect](uwf-volumeprotect.md)
  * *Unprotect* *&lt;volume&gt;*
    * Removes the specified volume from the list of volumes that are protected by UWF. UWF stops protecting the volume after the next system restart.
    * [UWF\_Volume.Unprotect](uwf-volumeunprotect.md)
* **File**
  * Configures file exclusion settings for UWF. If you use the *&lt;file&gt;* argument, it must be fully qualified, including the volume and path. **uwfmgr.exe** uses the volume specified in the *&lt;file&gt;* argument to determine which volume contains the file exclusion list for the file.
  * [UWF\_Volume](uwf-volume.md)
  * *Help | ?*
    * Displays command-line help for the `uwfmgr.exe file` command.
  * *Get-Exclusions* {*&lt;volume&gt;* | all}
    * Displays all files and directories in the exclusion list for the specified volume (for example, `uwfmgr.exe file Get-Exclusions C:`), or all volumes if **all** is specified. Displays information for both the current and the next session.
    * [UWF\_Volume.GetExclusions](uwf-volumegetexclusions.md)
  * *Add-Exclusion* *&lt;file&gt;*
    * Adds the specified file to the file exclusion list of the volume protected by UWF. UWF starts excluding the file from filtering after the next system restart.
    * [UWF\_Volume.AddExclusion](uwf-volumeaddexclusion.md)
  * *Remove-Exclusion* *&lt;file&gt;*
    * Removes the specified file from the file exclusion list of the volume protected by UWF. UWF stops excluding the file from filtering after the next system restart.
    * [UWF\_Volume.RemoveExclusion](uwf-volumeremoveexclusion.md)
  * *Commit* *&lt;file&gt;*
    * Commits changes to a specified file to overlay for a UWF-protected volume. Administrator-level permissions are required to use this command.
    * [UWF\_Volume.CommitFile](uwf-volumecommitfile.md)
  * *Commit-Delete* *&lt;file&gt;*
    * Deletes the specified file from both the overlay and the physical volume. Administrator-level permissions are required to use this command.
    * [UWF\_Volume.CommitFileDeletion](uwf-volumecommitfiledeletion.md)
* **Registry**
  * Configures registry key exclusion settings for UWF.
  * [UWF\_RegistryFilter](uwf-registryfilter.md)
  * *Help | ?*
    * Displays command-line help for the `uwfmgr.exe registry` command.
  * *Get-Exclusions*
    * Displays all registry keys in the registry exclusion list. Displays information for both the current and the next session.
    * [UWF\_RegistryFilter.GetExclusions](uwf-registryfiltergetexclusions.md)
  * *Add-Exclusion&lt;key&gt;*
    * Adds the specified registry key to the registry exclusion list for UWF. UWF starts excluding the registry key from filtering after the next system restart.
    * [UWF\_RegistryFilter.AddExclusion](uwf-registryfilteraddexclusion.md)
  * *Remove-Exclusion* *&lt;key&gt;*
    * Removes the specified registry key from the registry exclusion list for UWF. UWF stops excluding the registry key from filtering after the next system restart.
    * [UWF\_RegistryFilter.RemoveExclusion](uwf-registryfilterremoveexclusion.md)
  * *Commit* *&lt;key&gt; &lt;value&gt;*
    * Commits changes to the specified key and value. Administrator-level permissions are required to use this command.
    * [UWF\_RegistryFilter.CommitRegistry](uwf-registryfiltercommitregistry.md)
  * *Commit-Delete* *&lt;key&gt; \[&lt;value&gt;\]*
    * Deletes the specified registry key and value and commits the deletion. Deletes all values and subkeys if the value is empty, and commits the deletion. Administrator-level permissions are required to use this command.
    * [UWF\_RegistryFilter.CommitRegistryDeletion](uwf-registryfiltercommitregistrydeletion.md)
* **Overlay**
  * Configures settings for the UWF overlay.
  * [UWF\_Overlay](uwf-overlay.md) and [UWF\_OverlayConfig](uwf-overlayconfig.md)
  * *Help | ?*
    * Displays command-line help for the `uwfmgr.exe overlay` command.
  * *Get-Config*
    * Displays configuration settings for the UWF overlay. Displays information for both the current and the next session.
    * [UWF\_Overlay](uwf-overlay.md) and [UWF\_OverlayConfig](uwf-overlayconfig.md)
  * *Get-AvailableSpace*
    * Displays the amount of space remaining that is available for the UWF overlay.
    * [UWF\_Overlay](uwf-overlay.md)
  * *Get-Consumption*
    * Displays the amount of space currently used by the UWF overlay.
    * [UWF\_Overlay](uwf-overlay.md)
  * *Set-Size* *&lt;size&gt;*
    * Sets the maximum size of the UWF overlay, in megabytes, for the next session after a system restart.
    * [UWF\_OverlayConfig.SetMaximumSize](uwf-overlayconfigsetmaximumsize.md)
  * *Set-Type* {*RAM | DISK*}
    * Sets the type of the overlay storage to RAM-based or disk-based. UWF must be disabled in the current session to set the overlay type to disk-based.
    * [UWF\_OverlayConfig.SetType](uwf-overlayconfigsettype.md)
  * *Set-WarningThreshold* *&lt;size&gt;*
    * Sets the overlay size, in megabytes, at which the driver issues warning notifications for the current session.
    * [UWF\_Overlay.SetWarningThreshold](uwf-overlaysetwarningthreshold.md)
  * *Set-CriticalThreshold* *&lt;size&gt;*
    * Sets the overlay size, in megabytes, at which the driver issues critical notifications for the current session.
    * [UWF\_Overlay.SetCriticalThreshold](uwf-overlaysetcriticalthreshold.md)
  * *Set-Passthrough* *<on/off>*
    * Turns the [freespace passthrough](uwfoverlay.md#freespacepassthrough) on or off, allowing UWF to use free space outside of the reserved space when available.
  * *Set-Persistent* *<on/off>*
    * Sets the overlay as a [persistent overlay](uwfoverlay.md#persistentoverlay), allowing users to keep using their data after a reboot.
  * *Reset-PersistentState* *<on/off>*
    * Clears a persistent overlay on the next boot (on/off).

* **Servicing**
  * Configures settings for UWF servicing mode.
  * [UWF\_Servicing](uwf-servicing.md)
  * *Enable*
    * Enables servicing mode in the next session after a restart. Administrator-level permissions are required to use this command.
    * [UWF\_Servicing.Enable](uwf-servicingenable.md)
  * *Disable*
    * Disables UWF servicing mode in the next session after a restart. Administrator-level permissions are required to use this command.
    * [UWF\_Servicing.Disable](uwf-servicingdisable.md)
  * *Update-Windows*
    * Stand-alone command to apply Windows updates to a device. Called by the master servicing script that is called by the `uwfmgr.exe servicing enable` command. We recommend that you use the `uwfmgr.exe servicing enable` command to service your UWF–protected device whenever possible. Administrator-level permissions are required to use this command.
    * [UWF\_Servicing.UpdateWindows](uwf-servicingupdatewindows.md)
  * *Get-Config*
    * Displays UWF servicing mode information for the current session and the next session.
    * [UWF\_Servicing](uwf-servicing.md)
  * *Help*
    * Displays command-line help for the `uwfmgr.exe servicing` command.

## Unsupported WMI methods

The following list contains the UWF WMI provider methods that are not currently supported by the **uwfmgr.exe** tool:

* [UWF\_Overlay.GetOverlayFiles](uwf-overlaygetoverlayfiles.md)
* [UWF\_RegistryFilter.FindExclusion](uwf-registryfilterfindexclusion.md)
* [UWF\_Volume.FindExclusion](uwf-volumefindexclusion.md)
* [UWF\_Volume.RemoveAllExclusions](uwf-volumeremoveallexclusions.md)
* [UWF\_Volume.SetBindByDriveLetter](uwf-volumesetbindbydriveletter.md)

## Related topics

[Unified Write Filter](unified-write-filter.md)
