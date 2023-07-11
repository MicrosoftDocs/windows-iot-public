---
title: Apply OEM updates to UWF-protected devices
description: Apply OEM updates to UWF-protected devices
MS-HAID:
- 'p\_embedded.apply\_oem\_updates\_to\_uwf\_protected\_devices\_blue'
- 'p\_enterprise\_customizations.apply\_oem\_updates\_to\_uwf\_protected\_devices'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: cc94c9ec-406d-494b-bc7a-ab8af320f835


ms.date: 05/02/2017
ms.topic: article


---
# Apply OEM updates to UWF-protected devices

To apply OEM updates on a Unified Write Filter (UWF)-protected Windows 10 device, you can modify the UPDATE\_SUCCESS block of UWF master servicing script (UwfServicingMasterScript.cmd) to call a custom OEM script that applies any required OEM updates. The OEM script should return control back to the UWF Master Servicing Script when finished.

The UWF Master Servicing Script (UwfServicingMasterScript.cmd) is located in the \\Windows\\System32 folder.

## <a href="" id="update-success--uwfservicingmasterscript-cmd-"></a>UPDATE\_SUCCESS (UwfServicingMasterScript.cmd)

The UPDATE\_SUCCESS block of the UWF master servicing script follows:

```powershell
:UPDATE_SUCCESS
echo UpdateAgent returned success.
REM
REM echo UpdateAgent executing OEM script
REM OEM can call their custom scripts
REM at this point through a "call".
REM
REM The OEM script should hand control
REM back to this script once it’s done.
REM
REM Any error recovery for OEM script
REM should be handled outside of this script
REM post a reboot.
REM
uwfmgr servicing disable
echo Restarting system
goto UPDATE_EXIT
```

## Related topics

[Service UWF-protected devices](service-uwf-protected-devices.md)

[UWF master servicing script](uwf-master-servicing-script.md)

[Unified Write Filter](unified-write-filter.md)
