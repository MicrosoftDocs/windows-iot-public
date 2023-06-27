---
title: Windows IoT Enterprise LTSC in Volume License
author: TerryWarwick
ms.author: twarwick
ms.date: 06/26/2023
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: Windows IoT Enterprise LTSC in Volume License
keywords: IoT Enterprise, Installation
---

# Windows IoT Enterprise LTSC in Volume License

**Applies to:**

- Windows 10 IoT Enterprise LTSC 2021

## Introduction

Windows IoT Enterprise LTSC is now available through [Volume Licensing](https://www.microsoft.com/licensing/how-to-buy/how-to-buy) in addition to original equipment manufacturer preinstallation on a specialized device. Volume licensing is available to customers who purchase software under various volume programs (such as [Open](https://www.microsoft.com/Licensing/licensing-programs/open-license) and [Select](https://www.microsoft.com/Licensing/licensing-programs/select)).  Licenses for Windows IoT Enterprise provided through volume licensing cover upgrades only.

> [!NOTE]
> Windows IoT Enterprise LTSC is intended for use for fixed-function specialized devices only and cannot be used as a replacement of Windows desktop for general purpose computing.

## Getting Started

In this section, you install **Windows 10 Enterprise LTSC 2021** then transform it into **Windows 10 IoT Enterprise LTSC 2021** using a 5-by-5 volume activation key associated with the activation model that best suits your needs.

>[!TIP]
>If you are new to volume activation and need a little more background before proceeding, see see [Plan for volume activation](/windows/deployment/volume-activation/plan-for-volume-activation-client).

1. **Install Windows 10 Enterprise LTSC 2021**</br>
   Using the media for Windows 10 Enterprise LTSC 2021 acquired through your Volume License Service Center or Visual Studio Subscription

1. **Install Latest Cumulative Updates**
   The activation keys required to enable Windows 10 IoT Enterprise LTSC 2021 requires the installation of 2023-05 Cumulative update or a more recent successor.
   - Select **Start**
   - Select **Settings**
   - Select **Windows Update**
   - Select **Check for Updates**
   - Install all available updates

1. **Start PowerShell with Administrator privileges.**</br>
   You use this instance of PowerShell to verify the target operating system meets requirements then perform the transformation.  
    - Select **Start**
    - Type PowerShell
    - Right-click **Windows PowerShell**
    - Select **Run as administrator**

1. **Verify the Windows version and edition**</br>
   Run the following command from the PowerShell prompt to retrieve the version and edition information.

   ```powershell
   Dism /Online /Get-CurrentEdition
   ```

   The following properties are required to continue to the next step:

   - `ImageVersion : 10.0.19044.2905` _or later_</br>
   - `Current Edition : EnterpriseS`

1. **Install a product key**</br>
   In this step you use the command line utility `slmgr.vbs /ipk` to install a product key associated with your desired activation model.

   1. **KMS Client**</br>
      Install the Generic Volume License Key (GVLK) for Windows IoT Enterprise LTSC if you plan to activate using an on-premises key management service.</br>
      GVLK: `KBN8V-HFGQ4-MGXVD-347P6-PDQGT`

      ```cmd
      slmgr /ipk KBN8V-HFGQ4-MGXVD-347P6-PDQGT
      ```

   1. **Multiple Activation Key (MAK)**</br>
      Install the Multiple Activation Key that you acquired through the Volume License Service Center.</br>

      ```cmd
      slmgr /ipk XXXXX-XXXXX-XXXXX-XXXXX-XXXXX
      ```

      Where XXXXX-XXXXX-XXXXX-XXXXX-XXXXX is your Multiple Activation Key (MAK)

1. **Verify transformation**</br>
   Upon successfully installing the product key associated with your volume license activation model, the operating system edition changes to `IoTEnterpriseS`.  Run the following command at the PowerShell prompt to confirm.

   ```powershell
   Dism /Online /Get-CurrentEdition
   ```

   You should now see the same ImageVersion but the Current Edition has changed to `IoTEnterpriseS` as follows:

   - `ImageVersion : 10.0.19044.2905` _or later_</br>
   - `Current Edition : IoTEnterpriseS`

1. **Confirm activation expiry**
   Run the following command at the PowerShell command prompt to verify the expiry of your volume license activation.

   ```cmd
   slmgr /xpr
   ```

   If you're using MAK activation, a message indicating that the machine is permanently activated appears.

   If you're using KMS client activation, a message appears with a date that your current volume activation expires. Your device attempts to sync with the on-premises Key Management Service and renew its activation periodically.

## Related articles

- [Plan for volume activation](/windows/deployment/volume-activation/plan-for-volume-activation-client)
- [Volume Activation for Windows 10](/windows/deployment/volume-activation/volume-activation-windows-10)
- [Monitor activation](/windows/deployment/volume-activation/monitor-activation-client)
- [Using the Volume Activation Management Tool (VAMT)](/windows/deployment/volume-activation/use-the-volume-activation-management-tool-client)
- [Key Management Services (KMS) client activation and product keys](/windows-server/get-started/kms-client-activation-keys)
- [Slmgr.vbs Command Line Utility](/windows-server/get-started/activation-slmgr-vbs-options)
