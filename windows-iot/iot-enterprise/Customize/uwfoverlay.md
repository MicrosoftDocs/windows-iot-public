---
title: Overlay for Unified Write Filter (UWF)
description: Overlay for Unified Write Filter (UWF)
MS-HAID:
- 'p\_embedded.overlay\_for\_unified\_write\_filter\_\_UWF_\_blue'
- 'p\_enterprise\_customizations.overlay\_for\_unified\_write\_filter\_uwf'
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: baaf34ad-e859-4f8a-9ae1-5b5675d4b2e7
author: TerryWarwick
ms.author: twarwick
ms.prod: windows-iot
ms.technology: iot
ms.date: 10/02/2018
ms.topic: article


---
# Unified Write Filter (UWF) overlay location and size

The Unified Write Filter (UWF) protects the contents of a volume by intercepting write attempts to a protected volume and redirects those write attempts to a virtual overlay.

You can choose where the overlay is stored (RAM or disk), how much space is reserved, and what happens when the overlay fills up.

To increase uptime, set up monitoring to check if your overlay is filling up. At certain levels, your device can warn users and/or reboot the device.

## RAM overlay vs. disk overlay

- **RAM overlay (default)**: The virtual overlay is stored in RAM, and is cleared after a reboot.

  - By writing to RAM, you can reduce the wear on write-sensitive media like solid-state drives.
  - RAM is often more limited than drive space. As the drive overlay fills up the available RAM, device performance could be reduced, and users will eventually be prompted to reboot the device. If your users are expected to make many large writes to the overlay, consider using a disk overlay instead.

- **Disk overlay**: The virtual overlay is stored in a temporary location on the drive. By default, the overlay is cleared on reboot.

  - You can use [freespace passthrough](#freespace-passthrough-recommended) to use additional free space on the drive beyond the reserved virtual overlay space.
  - On Windows 10, version 1803, you can use [persistent overlay](#persistent-overlay) to allow users to save work in the virtual overlay even after a reboot.

## Overlay size

- Default=1024MB. Set with:
  - [CMD](uwfmgrexe.md): `uwfmgr overlay set-size`
  - [CSP](/windows/client-management/mdm/unifiedwritefilter-csp): `NextSession/MaximumOverlaySize`
  - [WMI](uwf-overlayconfigsetmaximumsize.md): `UWF\Overlay.SetMaximumSize`

When planning device rollouts, we recommend optimizing the overlay size to fit your needs.

For RAM overlays, you'll need to budget some RAM for the system. For example, if the OS requires 2 GB of RAM, and your device has 4 GB of RAM, set the maximum size of the overlay to 2048MB (2 GB) or less.

We recommend enabling UWF on a test device, installing the necessary apps, and putting the device through usage simulations. You can use this Powershell script to find out which files are consuming space:

```powershell
$wmiobject = get-wmiobject -Namespace "root\standardcimv2\embedded" -Class UWF_Overlay 
$files = $wmiobject.GetOverlayFiles("c:") 
$files.OverlayFiles | select-object -Property FileName,FileSize  | export-csv -Path D:\output.csv 
```

The amount of overlay used will depend on:

- Device usage patterns.
- Apps that can be accessed. (Some apps have high write volumes and will fill up the overlay faster.)
- Time between resets.
- When files are deleted, UWF removes them from the overlay and returns the freed resources to the available pool.

### Warnings and critical events

As the drive overlay fills up the available space, you can warn your users that they're running out of space, and prompt them to reboot the device or to run a script to clear the overlay.

1. Set warning levels and critical levels (optional). When the overlay is filled to this value, UWF writes an Event Tracing for Windows (ETW) message.

   - **Warning level**: Default=512MB. Set with:
     - [CMD](uwfmgrexe.md): `uwfmgr overlay set-warningthreshold`
     - [CSP](/windows/client-management/mdm/unifiedwritefilter-csp): `NextSession/WarningOverlayThreshold`
     - [WMI](uwf-overlaysetwarningthreshold.md): `UWF_Overlay.SetWarningThreshold`
   - **Critical level**: Default=1024MB. Set with:
     - [CMD](uwfmgrexe.md): `uwfmgr overlay set-criticalthreshold`
     - [CSP](/windows/client-management/mdm/unifiedwritefilter-csp): `NextSession/CriticalOverlayThreshold`
     - [WMI](uwf-overlaysetcriticalthreshold.md): `UWF_Overlay.SetCriticalThreshold`

   Note, these settings will take affect after the next reboot.

1. Use Task Scheduler to detect the ETW message and to warn users to wrap up their work on the device so they do not lose their content before the overlay is cleared. You can also provide a link to script to clear the contents of the overlay.

   Create tasks that trigger on the event that the **System** log receives an event ID from **uwfvol**:

   | Overlay usage       | Source  |  Level      | Event ID |
   |---------------------|---------|-------------|----------|
   | Warning threshold   | uwfvol  | Warning     | 1        |
   | Critical threshold  | uwfvol  | Error       | 2        |
   | Back to normal      | uwfvol  | Information | 3        |

1. Reboot the device.

### Freespace passthrough (recommended)

On devices with a disk overlay, you can use freespace passthrough to access your drive's additional free space.

You'll still need to reserve some space on the disk for the overlay. This space is used to manage the overlay, and to store overwrites, such as system updates. All other writes are sent to free space on disk. Over time, the reserved overlay will grow slower and slower, because overwrites will just keep replacing one another.

On devices with a RAM overlay, you can also use freespace passthrough to access your drive's additional free space to reduce  overlay usage.
However, freespace passthrough is not recommended for use with a RAM overlay because it does not reduce wear on write-sensitive media like solid-state drives.

- [CMD](uwfmgrexe.md): uwfmgr overlay set-passthrough (on|off)

### Persistent overlay

> [!NOTE]
> This mode is experimental, and we recommend thoroughly testing it before deploying to multiple devices. This option is not used by default.

On devices with a disk overlay, you can choose to keep working using the overlay data, even after a reboot. This can be helpful in situations where your guest users may need to access for longer periods, and may need to power off the device between uses.

This option gives your IT department more control over when the overlay is reset. You can also provide your users with scripts that will help them reset the overlay on demand.

To turn persistent overlay on or off:

- [CMD](uwfmgrexe.md): uwfmgr overlay set-persistent (on|off)

To reset the overlay:

- [CMD](uwfmgrexe.md): `uwfmgr overlay reset-persistentstate on`

### Overlay exhaustion

If the size of the overlay is close to or equal to the maximum overlay size, any write attempts will fail, returning an error indicating that there is not enough space to complete the operation. If the overlay on your device reaches this state, your device may become unresponsive and sluggish, and you may need to restart your device.

When Windows shuts down, it attempts to write a number of files to the disk. If the overlay is full, these write attempts fail, causing Windows to attempt to rewrite the files repeatedly until UWF can determine that the device is trying to shut down and resolve the issue. Attempting to shut down by using normal methods when the overlay is full or near to full can result in the device taking a long time, in some cases up to an hour or longer, to shut down.

You can often avoid this issue by using UWF to automatically initiate the shut down or restart:

- **Shut down**:
  - [CMD](uwfmgrexe.md): `uwfmgr shutdown`
  - [CSP](/windows/client-management/mdm/unifiedwritefilter-csp): `ShutdownSystem`
  - [WMI](uwf-filtershutdownsystem.md): `UWF\Filter.ShutdownSystem`

- **Restart**:
  - [CMD](uwfmgrexe.md): `uwfmgr restart`
  - [CSP](/windows/client-management/mdm/unifiedwritefilter-csp): `RestartSystem`
  - [WMI](uwf-filterrestartsystem.md): `UWF\Filter.RestartSystem`

Windows 10 19H1 and later will automatically restart if the maximum size of the overlay is exceeded.

## Related topics

- [Unified Write Filter](unified-write-filter.md)
