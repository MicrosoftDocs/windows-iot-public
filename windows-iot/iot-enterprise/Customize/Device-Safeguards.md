---
title: Device Safeguards
author: TerryWarwick
ms.author: twarwick
ms.date: 02/07/2024
ms.topic: article
ms.service: windows-iot
ms.subservice: iot
description: Learn about the Device Safeguard features of Windows IoT Enterprise.
keywords: Filtering and Controlling, USB Access
---

# Device Safeguards

Windows IoT Enterprise provides you, the device administrator, certain policies to protect your IoT devices from tampering, malware infections, data loss, or preventing peripherals from gaining access to your device. Windows IoT Enterprise gives you the power to create a customized experience that safeguards against these threats.

In a Windows IoT device restrictions profile, most configurable settings are deployed at the device level using device groups.

The following guide reviews the various policies that can be configured to create a safe and secure device usage experience.

## Device Installation - Group Policy

If your organization manages devices through group policy, we recommend you follow this [Step-By-Step Guide](/previous-versions/dotnet/articles/bb530324(v=msdn.10)).

## Control removable media using Microsoft Defender for Endpoint

Microsoft recommends [a layered approach to securing removable media](https://aka.ms/devicecontrolblog), and Microsoft Defender for Endpoint provides multiple monitoring and control features to help prevent threats in unauthorized peripherals from compromising your devices:

1. [Discover plug and play connected events for peripherals in Microsoft Defender for Endpoint advanced hunting](/windows/security/threat-protection/device-control/control-usb-devices-using-intune#discover-plug-and-play-connected-events). Identify or investigate suspicious usage activity.

1. Configure to allow or block only certain removable devices and prevent threats.
   1. [Allow or block removable devices](/windows/security/threat-protection/device-control/control-usb-devices-using-intune#allow-or-block-removable-devices) based on granular configuration to deny write access to removable disks and approve or deny devices by using USB device IDs.

   1. [Prevent threats from removable storage](/windows/security/threat-protection/device-control/control-usb-devices-using-intune#prevent-threats-from-removable-storage) introduced by removable storage devices by enabling:  

      - Microsoft Defender Antivirus real-time protection (RTP) to scan removable storage for malware.  
      - The Attack Surface Reduction (ASR) USB rule to block untrusted and unsigned processes that run from USB.  
      - Direct Memory Access (DMA) protection settings to mitigate DMA attacks, including Kernel DMA Protection for Thunderbolt and blocking DMA until a user signs in.  

1. [Create customized alerts and response actions](/windows/security/threat-protection/device-control/control-usb-devices-using-intune#create-customized-alerts-and-response-actions) to monitor usage of removable devices based on these plug and play events. You can also monitor other Microsoft Defender for Endpoint events with [custom detection rules](/windows/security/threat-protection/microsoft-defender-atp/custom-detection-rules).

1. [Respond to threats](/windows/security/threat-protection/device-control/control-usb-devices-using-intune#respond-to-threats) from peripherals in real-time based on properties reported by each peripheral.

>[!NOTE]
>
>These threat reduction measures help prevent malware from coming into your environment. To protect enterprise data from leaving your environment, you can also configure data loss prevention measures. For example, on Windows 10 devices you can configure [BitLocker](/windows/security/information-protection/bitlocker/bitlocker-overview) and [Windows Information Protection](/windows/security/information-protection/windows-information-protection/create-wip-policy-using-intune-azure), which will encrypt company data even if it is stored on a personal device, or use the [Storage/RemovableDiskDenyWriteAccess CSP](/windows/client-management/mdm/policy-csp-storage#storage-removablediskdenywriteaccess) to deny write access to removable disks. Additionally, you can [classify and protect files on Windows devices](/windows/security/threat-protection/windows-defender-atp/information-protection-in-windows-overview) (including their mounted USB devices) by using Microsoft Defender for Endpoint and Azure Information Protection.

## Device Installation Settings - MDM

If your organization manages devices through mobile device management, we recommend you review the following [device installation policies](/windows/client-management/mdm/policy-csp-deviceinstallation):

- [Allow Installation Of Matching Device IDs](/windows/client-management/mdm/policy-csp-deviceinstallation#deviceinstallation-allowinstallationofmatchingdeviceids)
- [Allow Installation Of Matching Device Instance IDs](/windows/client-management/mdm/policy-csp-deviceinstallation#deviceinstallation-allowinstallationofmatchingdeviceinstanceids)
- [Allow Installation Of Matching Device Setup Classes](/windows/client-management/mdm/policy-csp-deviceinstallation#deviceinstallation-allowinstallationofmatchingdevicesetupclasses)
- [Prevent Device Metadata From Network](/windows/client-management/mdm/policy-csp-deviceinstallation#deviceinstallation-preventdevicemetadatafromnetwork)
- [Prevent Installation Of Devices Not Described By Other Policy Settings](/windows/client-management/mdm/policy-csp-deviceinstallation#deviceinstallation-preventinstallationofdevicesnotdescribedbyotherpolicysettings)
- [Prevent Installation Of Matching Device IDs](/windows/client-management/mdm/policy-csp-deviceinstallation#deviceinstallation-preventinstallationofmatchingdeviceids)
- [Prevent Installation Of Matching Device Instance IDs](/windows/client-management/mdm/policy-csp-deviceinstallation#deviceinstallation-preventinstallationofmatchingdeviceinstanceids)
- [Prevent Installation Of Matching Device Setup Classes](/windows/client-management/mdm/policy-csp-deviceinstallation#deviceinstallation-preventinstallationofmatchingdevicesetupclasses)

## Look up device ID

You can use Device Manager to look up a device ID.

1. Open Device Manager.
1. Select **View** and select **Devices by connection**.
1. From the tree, right-click the device and select **Properties**.
1. In the dialog box for the selected device, select the **Details** tab.
1. Select the **Property** drop-down list and select **Hardware Ids**.
1. Right-click the top ID value and select **Copy**.

For information about Device ID formats, see [Standard USB Identifiers](/windows-hardware/drivers/install/standard-usb-identifiers).

For information on vendor IDs, see [USB members](https://www.usb.org/members).

Use the following PowerShell script to look up a device vendor ID or product ID (which is part of the device ID).

```powershell
PowerShell
Get-WMIObject -Class Win32_DiskDrive |
Select-Object -Property *
```

## Related articles

- [Policy CSP - DeviceInstallation](/windows/client-management/mdm/policy-csp-deviceinstallation)
- [Defender/AllowFullScanRemovableDriveScanning](/windows/client-management/mdm/policy-csp-defender#defender-allowfullscanremovabledrivescanning)
- [Device Control Power BI Template for custom reporting](https://github.com/microsoft/MDATP-PowerBI-Templates)
- [Windows Information Protection](/windows/security/information-protection/windows-information-protection/create-wip-policy-using-intune-azure)
