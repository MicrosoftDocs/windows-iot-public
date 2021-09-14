---
title: Reset and Recovery
author: rsameser
ms.author: riameser
ms.date: 3/5/2021
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: Learn about how to reset and recover your Windows 10 IoT Enterprise.
keywords: IoT Enterprise, Device Management, Reset, Recovery
---
# Device Reset and Recovery
This article will give you an overview on [Device Reset](#device-reset) and [Device Recovery](#device-recovery) features.

## Device Reset
Device reset is a process to restore the device to its initial conditions (with all user data removed). This is useful when you want to wipe out the user data/enterprise provisioning data and bring the device back to its pristine state.

Device reset includes the following key operations:
* Formats the data partition (all data stored there are lost)
* OEM custom packages should not store files/data in the data partition if they want to use device reset.
* Restores all registry settings to the initial values specified in the packaging
* Removes extraneous files in the Main OS partition excluding the files specified in the packaging
* Restores Microsoft Store Apps to the version packaged in the Image (via PPKG)
* Store apps updates performed via the Microsoft Store will be reverted back
* All changes to BCD settings performed at run-time will **remain intact**
* All OS/OEM updates applied to the device will **remain intact**

> [!NOTE]
>
> The Recovery process will also roll back the updates and put the device back to the factory condition.

##### Factory Reset
[Factory reset](https://support.microsoft.com/windows/how-to-refresh-reset-or-restore-your-pc-51391d9a-eb0a-84a7-69e4-c2c1fbceb8dd) restores the state of the device back to its first-boot state plus any update packages. The reset will **not** return device to the original factory state. To return the device to the original factory state, you must flash it with the original factory image. All the provisioning applied to the device by the enterprise will be lost and will need to be re-applied if needed.

##### Reset using Mobile Device Management
Device reset can be triggered using the [RemoteWipe CSP](https://docs.microsoft.com/windows/client-management/mdm/remotewipe-csp)

##### Reset using Azure Device Management
Device reset can also be triggered using the Azure Device Management using [Remote Wipe API](https://github.com/ms-iot/iot-core-azure-dm-client/blob/master/docs/remote-wipe.md).

> [!NOTE]
>
> The reset through this API performs additional functionality such as resetting the TPM.


## Device Recovery
Device recovery is a process to recover inoperable devices due to incorrect or bad storage state. This is done by booting into a known safe OS or recovery OS and re-flash the storage media.

The three key elements of recovery are:
1. **Safe OS**: This OS can be configured to launch on boot without UI. And in this state it can run a flashing app to apply a recovery image from a predefined location.
2. **Recovery SW**: SW Image used to re-flash the devices
3. **Recovery design choice**: Based on the location of the Safe OS and the recovery software, various design choices are available, see the various options below.

>[!NOTE]
>
> This process does not recover from hardware failures of storage (e.g. catastrophic media failure).

### Recovery using bootable USB
In this method, we boot the device from USB (with bootable safe OS and the FFU) and flash the device with the FFU present in the USB.
* [WinPE: Create USB bootable drive](https://docs.microsoft.com/windows-hardware/manufacture/desktop/winpe-create-usb-bootable-drive) provides information on creating a bootable USB drive.
* [Deploy Windows using Full Flash Update(FFU)](https://docs.microsoft.com/windows-hardware/manufacture/desktop/deploy-windows-using-full-flash-update--ffu) provides information on storing FFU files in USB.

Hardware Requirements:
* Requires device to have an USB port
* May require hardware key (or key combination) to trigger this

BSP Changes:
* Requires changes to respond to HW trigger (key/key combinations) to boot from USB
* Alternative design choice could be to prioritize boot from USB always, this way there is no explicit need to trigger this. However, this also means anytime a bootable USB is detected the device will enter this state.

### Recovery using built-in safe OS
In this method, the device contains a safe OS in a separate partition. Based on the location of the recovery SW, there can be few options. They are detailed below.

###### Recovery SW from USB device/ SD card
In this option, the Recovery SW is picked up from the attached USB device/ SD card.

Hardware Requirements:
* Requires either SD card interface or USB port (mass storage)
* May require hardware key (or key combination) to trigger

BSP Changes:
* Requires changes to respond to HW trigger (key/key combinations) to boot into the safe OS in separate partition
* Drivers for USB device / SD card interfaces may need to be added to Safe OS
* Device layout changes to store safe OS (size can be smaller to accommodate only the safe OS)
* Flashing tool to update only the main OS and Data partitions and skip updating the safe OS partition. This is essential to preserve the safe OS to be able to retry recovery if there is a power loss during a recovery process.

###### Recovery SW from recovery partition
This option is like earlier option, with only difference of storing the Recovery SW in the recovery partition itself. The device layout for this approach may differ in the size of the recovery partition (larger to accommodate the Recovery SW and potentially a backup Recovery SW).

> [!TIP]
>
> A Recovery SW present in the device will become outdated over time and the OS version after the recovery may fall-off the update train. One way to mitigate this issue is to refresh the Recovery SW image on the device using the BSP update path on a yearly cadence.

###### Recovery SW from cloud
In this option, the Recovery SW is downloaded from a predefined cloud service/web location. The cloud service needs to be setup so that it can securely offer the Recovery SW to the device. To realize this option, the safe OS must support network connectivity, so Wi-Fi drivers need to be added to the safe OS and in addition to that, the Wi-Fi profile in the main OS should be also made available for safe OS to connect to the network.


## Additional Resources:
* [Windows 10 Recovery Options](https://support.microsoft.com/windows/recovery-options-in-windows-10-31ce2444-7de3-818c-d626-e3b5a3024da5)
