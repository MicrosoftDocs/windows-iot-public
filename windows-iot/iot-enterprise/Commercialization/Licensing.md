---
title: Windows IoT Enterprise Licensing
author: TerryWarwick
ms.author: twarwick
ms.date: 03/31/2023
ms.topic: article
ms.service: windows-iot
ms.subservice: iot
description: Learn about licensing for Windows IoT Enterprise.
keywords: IoT Enterprise, OEM, Licensing, LTSC, Servicing
---

# Licensing

Licenses for Windows IoT Enterprise are available through both [OEM Licensing](#oem-licensing) and [Volume Licensing](#volume-licensing).  

This table provides a snapshot of the license applicability for these two options followed by more detail to help you determine which option is right for you.

| Requirement   | [OEM License](#oem-licensing) | [Volume License](#volume-licensing) |
|:--------------|:-----------:|:--------------:|
| New Device                |✅Yes|⛔No|
| Upgrade Existing Device   |✅Yes|✅Yes|
| Transferrable License     |✅Yes|⛔No|
| Activation methods        | OA3.0, ePKEA, PKEA | KMS, MAK |

**Definitions**  

- **OEM**: Original Equipment Manufacturer
- **LTSC**: Long-Term Servicing Channel
- **OA3.0**: OEM Activation 3.0
- **ePKEA**: Embedded Product Key Entry Activation
- **PKEA**: Product Key Entry Activation
- **KMS**: Key Management Service
- **MAK**: Multiple Activation Key

[!INCLUDE [Feedback](../includes/incl-feedback.md)]

## OEM Licensing

An OEM license is required for device makers that preinstall the operating system on new devices for sale to an end-customer. OEMs can also obtain upgrade licenses for existing devices, originally produced with a previous version of the operating system, and offer full solution upgrades to the end-customer. An OEM License must be transferred to an end-customer purchasing a new device from the OEM.

For additional information about Windows IoT Enterprise OEM licenses and terms of use, contact one of our [authorized distributors](../windows-iot-distributors.md) for assistance.

Windows IoT Enterprise devices produced by OEMs must be enabled for activation before leaving the factory. For information about enabling your devices for activation, see:
    
- [OA 3.0 Activation Guide](/windows-hardware/manufacture/desktop/oem-activation-3)
- [ePKEA Activation Guide](activation-guide.md)

## Volume Licensing

A volume license is available for end-customers to upgrade existing systems with a qualifying operating system to a new version.  A volume license is nontransferrable.

Volume licenses for Windows IoT Enterprise LTSC are available through the following Volume License programs:

- [Microsoft Customer Agreement](https://www.microsoft.com/licensing/terms/productoffering/WindowsDesktopOperatingSystem/MCA)
- [Microsoft Product and Services Agreement (MPSA)](https://www.microsoft.com/licensing/terms/productoffering/WindowsDesktopOperatingSystem/MPSA)
- [Select/Select Plus program](https://www.microsoft.com/licensing/terms/productoffering/WindowsDesktopOperatingSystem/SS)

For information regarding volume license activation options for Windows IoT Enterprise LTSC, see [Volume activation for Windows](/windows/deployment/volume-activation/volume-activation-windows).

Additional information specific to the deployment of Windows IoT Enterprise LTSC using volume licensing, see [Windows IoT Enterprise in Volume License](../Deployment/Volume-License.md)

## End User License Agreement

For details about the use restrictions of Windows IoT Enterprise, see [Windows IoT Enterprise End-User License Agreement](../EULA/End-User-License-Agreement.md)

## More Resources

- [What is Windows IoT Enterprise?](../Overview.md)
- [Release History](../whats-new/Release-History.md)
- [System Requirements](../Hardware/System_Requirements.md)
- [Processor Requirements](../Hardware/Processor_Requirements.md)
- [Hardware Component Guidelines](/windows-hardware/design/component-guidelines/components)
- [Windows Manufacturing](/windows-hardware/manufacture/desktop)
