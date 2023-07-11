---
title: UWF master servicing script
description: UWF master servicing script
MS-HAID:
- 'p\_embedded.uwf\_master\_servicing\_script\_blue'
- 'p\_enterprise\_customizations.uwf\_master\_servicing\_script'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 62687446-2009-4ca9-a9ba-c85172c2b47f


ms.date: 05/02/2017
ms.topic: article


---
# UWF master servicing script

The UWF master servicing script (UwfServicingMasterScript.cmd) is located in the \\Windows\\System32 folder.

## UwfServicingMasterScript.cmd

The full UWF master servicing script follows:

```powershell
REM servicing of the device with UWF installed. The script will
REM call UWF manager application to update the system with the
REM latest available updates.
REM The script will detect whether the update operation
REM ended successfully or requires a reboot.
REM
REM The script will change the "SERVICING" state of the device
REM only when the update operation results in a "SUCCESS".
REM A state change of the device requires a reboot.
REM
REM If the update operation requires a "REBOOT" the script will
REM reboot device without changing the "SERVICING" state. The
REM Will then run again on the following reboot until
REM the update operation either return a "SUCCESS" or a "ERROR"
REM
REM Any third-party script that needs to run before the state
REM change should run in the UPDATE_SUCCESS block
REM
REM Environment :
REM It is expected that UWF is turned "OFF", "SERVICING" mode
REM enabled and all other preconditions
REM for servicing are in place.
REM
REM
REM


echo UpdateAgent starting.
uwfmgr servicing update-windows
if ERRORLEVEL 3010 goto UPDATE_REBOOT
if ERRORLEVEL 0 goto UPDATE_SUCCESS
echo UpdateAgent returned error =%ERRORLEVEL%

:UPDATE_ERROR
uwfmgr servicing disable
echo Restarting system
goto UPDATE_EXIT

:UPDATE_REBOOT
echo UpdateAgent requires a reboot.
echo UpdateAgent restarting system
goto UPDATE_EXIT

:UPDATE_SUCCESS
echo UpdateAgent returned success.
REM
REM echo UpdateAgent executing OEM script
REM OEM can call their custom scripts
REM at this point through a "call".
REM
REM The OEM script should hand control
REM back to this script once it is done.
REM
REM Any error recovery for OEM script
REM should be handled outside of this script
REM post a reboot.
REM
uwfmgr servicing disable
echo Restarting system
goto UPDATE_EXIT

:UPDATE_EXIT
echo UpdateAgent exiting.
shutdown -r -t 5
EXIT /B
```

## Related topics

[Service UWF-protected devices](service-uwf-protected-devices.md)

[Unified Write Filter](unified-write-filter.md)
