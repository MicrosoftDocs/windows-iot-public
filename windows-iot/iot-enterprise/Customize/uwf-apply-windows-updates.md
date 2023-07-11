---
title: Apply Windows updates to UWF-protected devices
description: Apply Windows updates to UWF-protected devices
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 050d1202-0b38-4f9d-a85b-27b070098ae4


ms.date: 05/02/2017
ms.topic: article


---
# Apply Windows updates to UWF-protected devices

When a device is protected with Unified Write Filter (UWF), you must use UWF servicing mode commands to service the device and apply updates to an image.

UWF servicing mode uses the following files to when it applies Windows updates to your device:

* UWFMgr.exe command-line tool
* UwfServicingScr.scr screen saver
* UwfServicingMasterScript.cmd script

> [!NOTE]
> The master servicing script can be modified to service third-party applications, service custom OEM applications, or call custom OEM servicing scripts.

UWF servicing supports the following types of Windows updates:

* Critical updates
* Security updates
* Driver updates

## Apply Windows updates to UWF-protected devices

1. To apply Windows updates to your device, at an administrator command prompt, type the following command:

   ```cmd
   uwfmgr.exe servicing enable
   ```

1. Restart the device. Use either command.

   ```cmd
   uwfmgr.exe filter restart
   ```

   ```cmd
   shutdown /r /t 0
   ```

On restart, the device will automatically sign in to the servicing account and servicing will start.

> [!IMPORTANT]
> The default servicing account that is automatically created and used for servicing is named **UWF-Servicing**. It is important that you do not have a user account that has that same name on a device before starting UWF servicing.

Once servicing has started, no user interaction is required. The system may restart if it is required by the Windows updates that are installing. If a restart is required, the system will re-enter servicing mode on restart and continue until all updates have been installed.

While servicing is underway, the UwfServicingScr.scr screen saver displays on the device.

> [!NOTE]
> The UwfServicingScr.scr screen saver that is included with Windows 10 Enterprise is a standard Windows screen saver and can be replaced by a custom OEM screen saver if required.

When Windows update servicing is finished, the system will disable UWF servicing and restart the system with UWF-protection enabled and all file and registry exclusions restored to their original pre-servicing state.

> [!NOTE]
> Be aware that during UWF servicing in Windows 10 Enterprise, Windows Update automatically accepts all Microsoft Software License Terms.

> [!NOTE]
> If Windows updates cannot be installed or return an error, servicing will be disabled and the system will restart with UWF-protection re-enabled and all file and registry exclusions restored to their original pre-servicing state.

## Related topics

[Unified Write Filter](unified-write-filter.md)

[UWF master servicing script](uwf-master-servicing-script.md)

[UWF servicing screen saver](uwf-servicing-screen-saver.md)
