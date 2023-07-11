---
title: Troubleshooting Unified Write Filter (UWF)
description: Troubleshooting Unified Write Filter (UWF)
MS-HAID:
- 'p\_embedded.troubleshooting\_unified\_write\_filter\_\_uwf\_\_blue'
- 'p\_enterprise\_customizations.troubleshooting\_unified\_write\_filter\_uwf'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: d9f0f26f-3545-46c3-887e-be21895bff66


ms.date: 05/02/2017
ms.topic: article


---
# Troubleshooting Unified Write Filter (UWF)

Review the log files and error message information locations for Unified Write Filter (UWF) on your Windows 10 Enterprise device.

If you are having difficulties configuring Unified Write Filter (UWF) on your device, see the following information about how to find event log and error message information for troubleshooting problems with UWF.

## Event logs

UWF uses Windows Event Log to log events, errors and messages.

* Events related to overlay consumption are sent by UWF kernel mode components and are logged in the **Windows Logs\\System** event log.
* Event related to configuration changes and servicing logs are sent by UWF user mode components:
  * Error messages are logged in the **Applications and Services Logs\\Microsoft\\Windows\\UnifiedWriteFilter\\Admin** event log.
  * Informational messages are logged in the **Applications and Services Logs\\Microsoft\\Windows\\UnifiedWriteFilter\\Operational** event log.

## Related topics

[Unified Write Filter](unified-write-filter.md)

[Common write filter exclusions](uwfexclusions.md)

[Service UWF-protected devices](service-uwf-protected-devices.md)

[Unified Write Filter WMI provider reference](uwf-wmi-provider-reference.md)

[uwfmgr.exe](uwfmgrexe.md)
