---
title: Windows IoT Enterprise LTSC in Volume License
author: vanloke323-Microsoft
ms.author: vlokeshwar
ms.date: 02/26/2026
ms.topic: article
ms.service: windows-iot
ms.subservice: iot
description: How to deploy Windows 11 IoT Enterprise LTSC in Volume License
keywords: IoT Enterprise, Installation
zone_pivot_groups: Windows11-Windows10
---

# Windows IoT Enterprise LTSC in Volume License

Applies to:  

:::zone pivot="windows11"

✅ Windows 11 IoT Enterprise LTSC 2024  

::: zone-end

:::zone pivot="windows10"

✅ Windows 10 IoT Enterprise LTSC 2021

::: zone-end

## Introduction

Windows IoT Enterprise LTSC is now available as an **upgrade license** for fixed-function, specialized devices through [Volume Licensing](/partner-center/support-resources-licensing) programs including:

- [Microsoft Product and Services Agreement (MPSA)](https://www.microsoft.com/licensing/terms/productoffering/WindowsDesktopOperatingSystem/MPSA)
- [Microsoft Customer Agreement (MCA)](https://www.microsoft.com/licensing/terms/productoffering/WindowsDesktopOperatingSystem/MCA)
- [Select Plus](https://www.microsoft.com/licensing/terms/productoffering/WindowsDesktopOperatingSystem/SS)

For more information, see [Windows Desktop Operating System Program Terms](https://www.microsoft.com/licensing/terms/productoffering/WindowsDesktopOperatingSystem/all)

> [!IMPORTANT]
> Windows IoT Enterprise LTSC is intended for use for fixed-function specialized devices only and cannot be used as a replacement of Windows desktop for general purpose computing.

## Planning

Volume activation provides two ways to complete volume activations. You can use either key types to activate systems in their organization:

- [Key Management Service (KMS)](/windows/deployment/volume-activation/activate-windows-10-clients-vamt#how-key-management-service-works) allows organizations to activate systems within their own network.
- [Multiple Activation Key (MAK)](/windows/deployment/volume-activation/activate-windows-10-clients-vamt#how-multiple-activation-key-works) activates systems on a one-time basis, using Microsoft hosted activation services.

For more information, see [Plan for Volume Activation](/windows/deployment/volume-activation/plan-for-volume-activation-client).

## Prerequisites

To deploy Windows IoT Enterprise LTSC with volume activation, you need the following assets from your [Volume License Administrator](/licensing/administrator-faq), typically associated with the procurement process.

:::zone pivot="windows11"

> [!div class="checklist"]
>
> - Windows 11 IoT Enterprise LTSC 2024 (x64) installation media or ISO
> - Multiple Activation Key (MAK) if you are not using an on-prem Key Management Service (KMS)

::: zone-end

:::zone pivot="windows10"

> [!div class="checklist"]
>
> - Windows 10 Enterprise LTSC 2021 (x64) installation media or ISO
> - Multiple Activation Key (MAK) if you are not using an on-prem Key Management Service (KMS)

::: zone-end

## Getting Started

:::zone pivot="windows11"

In this section, you install **Windows 11 IoT Enterprise LTSC 2024** and prepare for activation using either KMS or MAK.

1. **Install Windows 11 IoT Enterprise LTSC 2024**</br> Using the media for Windows 11 IoT Enterprise LTSC 2024 acquired through your Volume license Service Center or Visual Studio Subscription.

1. **Start PowerShell with Administrator privileges.**</br>
   You use this instance of PowerShell to verify the target operating system meets requirements then perform the transformation.  
    - Select **Start**
    - Type PowerShell
    - Right-click **Windows PowerShell**
    - Select **Run as administrator**

1. **Install a product key**</br>
   By default Windows 11 IoT Enterprise LTSC 2024 is configured to automatically activation using an on-premises key management service (KMS). You don't need to install a product key if you plan to keep the device in an environment where it can reach the KMS server regularly.

   Skip the following step if you don't intend to use MAK activation.

   - **Multiple Activation Key (MAK)**</br>
     In this step you use the command line utility `slmgr.vbs /ipk` to install a Multiple Activation Key that you acquired through the Volume License Service Center.</br>

      ```cmd
      slmgr /ipk XXXXX-XXXXX-XXXXX-XXXXX-XXXXX
      ```

      Where XXXXX-XXXXX-XXXXX-XXXXX-XXXXX is your Multiple Activation Key (MAK)

1. **Check activation status**

   ```cmd
   slmgr /dli
   ```

   1. If not activated, requestion activation

      ```cmd
      slmgr /ato
      ```

1. **Confirm activation expiry**
   Run the following command at the PowerShell command prompt to verify the expiry of your volume license activation.

   ```cmd
   slmgr /xpr
   ```

   If you're using MAK activation, a message indicating that the machine is permanently activated appears.

   If you're using KMS client activation, a message appears with a date that your current volume activation expires. Your device attempts to sync with the on-premises Key Management Service and renew its activation periodically.

::: zone-end

:::zone pivot="windows10"

In this section, you install **Windows 10 Enterprise LTSC 2021** then transform it into **Windows 10 IoT Enterprise LTSC 2021** using a 5-by-5 volume activation key associated with the activation model that best suits your needs.

1. **Install Windows 10 Enterprise LTSC 2021**</br>
   Using the media for Windows 10 Enterprise LTSC 2021 acquired through your Volume License Service Center or Visual Studio Subscription.

1. **Install Latest Cumulative Updates**</br>
   The activation keys for Windows 10 IoT Enterprise LTSC 2021 require the installation of 2023-05 Cumulative update (10.0.19044.2905) or a more recent successor.
   - Select **Start**
   - Select **Settings**
   - Select **Windows Update**
   - Select **Check for Updates**
   - Install all available updates

   Alternatively, you can install the update and its prerequisites manually using the 2023-05 Cumulative Update for Windows 10 Version 21H2 or a more recent successor. For more information about this update, see [KB5026361](https://support.microsoft.com/topic/may-9-2023-kb5026361-os-builds-19042-2965-19044-2965-and-19045-2965-3edafffe-c3cc-4010-af43-2097c84c9437).

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
   Upon successfully installing the product key associated with your volume license activation model, the operating system edition changes to `IoTEnterpriseS`. Run the following command at the PowerShell prompt to confirm.

   ```powershell
   Dism /Online /Get-CurrentEdition
   ```

   You should now see the same ImageVersion but the Current Edition changed to `IoTEnterpriseS` as follows:

   - `ImageVersion : 10.0.19044.2905` _or later_</br>
   - `Current Edition : IoTEnterpriseS`

1. **Check activation status**

   ```cmd
   slmgr /dli
   ```

   1. If not activated, requestion activation

      ```cmd
      slmgr /ato
      ```

1. **Confirm activation expiry**
   Run the following command at the PowerShell command prompt to verify the expiry of your volume license activation.

   ```cmd
   slmgr /xpr
   ```

   If you're using MAK activation, a message indicating that the machine is permanently activated appears.

   If you're using KMS client activation, a message appears with a date that your current volume activation expires. Your device attempts to sync with the on-premises Key Management Service and renew its activation periodically.

::: zone-end

## Related articles

### Deployment

- [Plan for Volume Activation](/windows/deployment/volume-activation/plan-for-volume-activation-client)
- [Volume Activation for Windows 10](/windows/deployment/volume-activation/volume-activation-windows-10)
- [Monitor Activation Count](/windows/deployment/volume-activation/monitor-activation-client)
- [Slmgr.vbs Command Line Activation Utility](/windows-server/get-started/activation-slmgr-vbs-options)
- [Volume Activation Management Tool (VAMT)](/windows/deployment/volume-activation/use-the-volume-activation-management-tool-client)
- [KMS client activation and product keys](/windows-server/get-started/kms-client-activation-keys)
- [Using Edition Configuration and Product ID Files during Windows Installation](/windows-hardware/manufacture/desktop/windows-setup-edition-configuration-and-product-id-files--eicfg-and-pidtxt)

### Licensing & Procurement

For organizations purchasing IoT Enterprise LTSC through a via volume license agreement, consult your [Volume License Administrator](/licensing/administrator-faq) for assistance. The software download and volume license keys are found in the Downloads and Keys section of Volume Licensing Service Center or Microsoft 365 admin center.

- [Volume License Service Center (VLSC) - Downloads FAQ](/licensing/downloads-faq)
- [Volume License Service Center (VLSC) - Product Keys FAQ](/licensing/products-keys-faq)
- [Microsoft 365 admin center - Volume License Product Keys FAQ](/microsoft-365/commerce/licenses/product-keys-faq)
- [Microsoft 365 admin center - Downloads FAQ](/microsoft-365/commerce/licenses/downloads-faq)
