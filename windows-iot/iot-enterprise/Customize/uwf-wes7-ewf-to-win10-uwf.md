---
title: Windows Embedded Systems7 Enhanced Write Filter to Windows 10 Unified Write Filter
description: Migration of WES7 EWF to Win10 UWF
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 
author: TerryWarwick
ms.author: twarwick
ms.service: windows-iot
ms.subservice: iot
ms.date: 05/20/2024
ms.topic: article


---
# Windows Embedded Systems 7 Enhanced Write Filter to Windows 10 Unified Write Filter

**Allowing UWF swapfile (aka. DISK Overlay) to be created and used on any volume**</br>We added ability for Overlay in DISK mode to use file on any available volume unrelated to whether the volume is protected or not. The main purpose for the change is to allow booting from devices susceptible to wear by writings (such as Flash/SD/SSD devices) while redirecting the DISK overlay to less “precious” media. Prior to that change, DISK mode Overlay was exclusively restricted to OS (aka C:) volume.

:::image type="content" source="images/administratorcommandprompt.png" alt-text="This is a administrator command prompt":::

New subcommand “create-swapfile” was introduced under “uwfmgr.exe volume” to allow user control over the location of the DISK mode Overlay swapfile. This command requires  volume DOS name (such as C:, D:, and so on.) or volume GUID as argument. The initial size of the file is deduced from the size of the Overlay at the time and may be later changed by issuing “uwfmgr.exe overlay set-size” subcommand.
The new subcommand “create-swapfile” is only allowed  when UWF filter is disabled and UWF Overlay is in DISK mode.

## Read Only Media mode

Read Only Mode allows elimination of all and any writes to the physical storage device, even metadata writes that does not have any effect on a files content. Read Only Media mode can be easily configured using UWF to get into it and out of it. The new functionality supports many popular scenarios that users of legacy WES7 EWF volume-based filter used.
The new subcommand "set-rom-mode" was introduced under "uwfmgr.exe. overlay" to allow the user to enable/disable Read-Only Media mode.

:::image type="content" source="images/administratorcompactprompt.png" alt-text="This is a administrator compact prompt":::

This subcommand requires "on" or "off" argument. Read-Only Media mode can be enabled only when UWF is currently disabled. The mode can be disabled, if UWF is currently enabled, but after “off” command is issued there is no way to re-enable Read-Only Media mode until the next reboot. Also, UWF can be enabled/disabled while in Read-Only Media mode, but such “state change” will result in files and/or metadata to be changed on physical device protected by UWF.

> [!NOTE]
>
>- After enabling Read-Only Media mode, all writes will be filtered out as earlier as next reboot, so anything that is written until then may cause changes on the physical device.
>- All existing exclusions are ignored (nonfunctional) and no file/registry commits are possible in Read Only Media mode. See "*Full Volume Commit*" in this document).
>- Enabling Read Only Media mode is only possible when UWF is configured to use RAM overlay.

:::image type="content" source="images/overlaysettings.png" alt-text="This is a overlay settings":::

UWF CSP provider was updated by allowing setting new bit (0x4) in CFG_DATATYPE_INTEGER UnifiedWriteFilter\NextSession\OverlayFlags property.

After the implementation of Read-Only Media mode we were able to make HORM mode transitions significantly more consistent, safe, and reliable. To enable HORM mode, UWF must be configured and booted into Read Only Media mode, which eliminates the need for user to care about exclusions and situation where HORM enablement is not possible by other reasons.

### Full Volume Commit in Read-Only Media mode

After introduction of Read-Only Media mode, we were able to implement ability to commit entire state of the UWF protected volumes to the physical disk at once, which was architecturally impossible before in presence of active file/registry exclusions.

The new subcommand “commit” was introduced under "uwfmgr.exe overlay" to allow the user to commit all accumulated changes since, previous boot and all following changes until next reboot to the underlying physical device. After successful “full volume commit” and until the next reboot OS behaves like being totally unprotected. Protection is restored on the next reboot.

:::image type="content" source="images/administratorprompt.png" alt-text="This is a administrator prompt":::

> [!NOTE]
>
>- UWF must be enabled and configured in Read-Only Media mode
>- UWF must not be in HORM mode:  
> HORM mode cannot be enabled after Full Volume Commit and before the next reboot.
>
>- UWF can be disabled after Full Volume Commit

UWF CSP provider was updated by adding read/write CFG_DATATYPE_BOOLEAN “UnifiedWriteFilter\CurrentSession\OverlayCommit” property, which indicates if Full Overlay Commit was issued after the last boot. Setting that property from zero (FALSE) to non-zero value (TRUE) causes immediate Full Volume Commit to be performed. Setting this property to zero (FALSE) if its current value is non-zero (TRUE) is not allowed.

Customer can easily determine "Full Volume Commit" state by checking current configuration (for example, uwfmgr get-config):

:::image type="content" source="images/fullvolumecommit.png" alt-text="This is a full volume commit":::
