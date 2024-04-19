---
title: Windows IoT Enterprise OEM Activation using ePKEA
description: OEMs use Embedded Product Key Entry Activation (ePKEA) to enable activation of Windows IoT Enterprise for a predetermined number of specialized devices.
author: terrywarwick
ms.service: windows-iot
ms.subservice: iot
ms.topic: article `
ms.date: 04/18/2024
---

# OEM Activation

As a device maker, you can install and use the Windows IoT Enterprise operating system to develop and test prototype customer systems. Any images installed without a product key or using the default manufacturing key won't function for more than 30 days after the first boot of an image on a prototype system.

Activation is the process of registering Windows IoT Enterprise with Microsoft to ensure the product is genuine. Activation is used to reduce software piracy, protect the software industry, corporate intellectual property, software development investments, and product quality to ensure customers receive the product quality that they expect from a Windows-based operating system.

All Windows IoT Enterprise devices that are distributed to your customers must be enabled for activation before leaving the factory so that the customer isn't prompted for a product key during the out of box experience or encountering degraded functionality caused by being unable to activate their device.

Windows IoT Enterprise provides three options for enabling activation, including:

| Activation&nbsp;Model | Description |
|:----------------:| ----------- |
| PKEA | **Product Key Entry Activation** </br> Requires a unique 5 by 5 product key to be applied to each device produced.  |
| ePKEA | **Embedded Product Key Entry Activation**  </br> ePKEA is designed exclusively for OEMs building specialized devices base on Windows IoT Enterprise. A single ePKEA product key comes with the ability to activate a predetermined number of devices. Each successful activation via internet connection or by telephone decrements the available activation count associated with the OEMs ePKEA. You need to request a new ePKEA before fully depleating the available activations associated with your current ePKEA to prevent activation failures. |
| OA 3.0 | **OEM Activation 3.0 (OA3)** </br> The OA 3.0 system enables OEMs to develop an internal inventory management system to manage the ordering and receiving of Windows product keys and the creation and reporting process for the Computer Build Report. You're required to include an edition specific Default Product Key in each golden image of Windows IoT Enterprise. The default product key can't activate Windows, but rather instructs Windows to search for an OA 3.0 product key that stored in the device’s firmware. |

This article focuses on using ePKEA to enable activation for Windows IoT Enterprise based devices. For more information about OA 3.0, see  [OEM Activation 3.0 system](/windows-hardware/manufacture/desktop/oem-activation-3).

> [!IMPORTANT]
>As an OEM receiving an ePKEA based product key, your ePKEA should be handled confidentially to prevent piracy from depleating your available activation count resulting in your customers being unable to activate the devices they purchased from you.

## Manufacturing Process

Before you can enable your device to activate you need to be familiar with the Windows desktop manufacturing process. There are several different methods to deploy and customize your Windows IoT Enterprise image. Once you select the manufacturing process which includes both a deployment and customization strategy that best suits your production requirements you can incorporate a compatible approach to enable activation using your ePKEY based product key. If you aren't familiar with the Windows desktop manufacturing process, see [Windows Manufacturing Overview](/windows-hardware/manufacture).

## Enable Activation

You can install your production ePKEA product key using any of the following methods:

### Interactive Setup

If you choose to start your journey by creating a golden image using interactive setup, which is run when booting from installation media, you are prompted to supply your product key. You can supply your production ePKEA, the default manufacturing key or skip the product key entry step.

| When prompted for Product Key | Result |
| ----------- | -----------|
| Enter your production ePKEA           | Production image is fully enabled for activation |
| Enter the 'default manufacturing key' | Your device isn't enabled for activation and you must install your production ePKEA during Audit Mode. |
| Skip the product key entry screen     | You must select either Windows IoT Enterprise or Windwos IoT Enterprise LTSC to proceed.the OS edition want to install. Your device isn't enabled for activation when setup is complete and you must install your production ePKEA during Audit Mode. |

For more information on interactive setup, see [Boot and install Windows](/windows-hardware/manufacture/desktop/boot-and-install-window).

### Unattended Setup

Similarly to Interactive Setup, you can supply either your production ePKEA or the default manufacturing key using an unattend answer file. The same applies that only supplying your production ePKEA fulfills the requirement to enable activation.
For more information, see [Windows Setup Automation Overview](/windows-hardware/manufacture/desktop/windows-setup-automation-overview).

### Audit Mode

Audit mode allows you to make more changes to your Windows IoT Enterprise image before you send the computer to a customer or capture the image for replication during the manufacturing process. Using audit mode, you can install drivers including a driver package, install applications, or make other updates to the operating system while it's running, including enabling activation.
For more information on getting started with Audit mode, see Audit mode overview.
While you are in Audit mode, you can apply your production ePKEA to your image using the graphical user interface provided by Settings > Activation or the command line utility SLMGR.vbs.

Method 1: Settings > Activation graphical user interface
Access the activation graphical user interface using one of the following options:

- Select Start then begin typing Activation and select Activation settings once it appears
- Select Start > Settings > System > Activation
- Select Start > All Apps > Settings > System > Activation
- Right select Start > Run then type slui.exe

Method 2: Command Line | SLMGR.vbs
Open a Windows PowerShell instance as an Administrator then execute the following command replacing the Xs with your ePKEA to inject the product key into Windows IoT Enterprise

```powershell
Slmgr.vbs /ipk XXXXX-XXXXX-XXXXX-XXXXX-XXXXX
```

You can also use the SLMGR.vbs command from a Windows PowerShell instance that can be incorporated into a larger script that is used to perform other configuration tasks by prepending the above command with cscript, but you must provide a fully qualified path to slmgr.vbs as follows.

```powershell
cscript c:\windows\system32\Slmgr.vbs /ipk XXXXX-XXXXX-XXXXX-XXXXX-XXXXX
```

For more information, see Slmgr.vbs command line reference
IMPORTANT: Once you complete the customizations that are required for your device, you must finalize your image for replication by configuring the device to boot into the out of box experience for the end customer. For more information on finalizing your image for replication, see Sysprep Process Overview.

### Offline image

You can also make changes to an offline mounted Windows image without booting into the operating system you’re going to modify. To learn more about servicing an offline image, see Modify a Windows Image Using DISM.
Once you have successfully mounted an offline image you can install your ePKEA into the offline image using either Set-WindowsProductKey or DISM /SetProductKey by running either command from an elevated PowerShell command window.
Set-WindowsProductKey

```powershell
Set-WindowsProductKey -Path “c:\offline” -ProductKey “XXXXX-XXXXX-XXXXX-XXXXX-XXXXX”
```

For more information, see [Set-WindowsProductKey.](/powershell/module/dism/set-windowsproductkey)

DISM /SetProductKey

```powershell
Dism /Image:C:\offline /Set-ProductKey:XXXXX-XXXXX-XXXXX-XXXXX-XXXXX
```

For more information, see [DISM /SetProductKey](/windows-hardware/manufacture/desktop/dism-windows-edition-servicing-command-line-options#set-productkey).

IMPORTANT: Once you complete the customizations that are required for your offline image, you must commit the changes and dismount the image. For more information, see Modify a Windows Image Using DISM.

## Protect your Product Key

Consider your ePKEA as confidential
Your ePKEA can activate a large number of Windows IoT Enterprise devices. You should consider your ePKEA as highly confidential to avoid it from getting into the hands of a bad operator that could result in the use of your ePKEA as a tool for piracy and drain the available activations associated with your ePKEA.
Remove your ePKEA from the registry
To prevent disclosure attack where malicious code extracts your product key from the image. Once a bad operator has extracted the product key from your devices it can be used to enable activation on their own devices, draining the available activations associated with your ePKEA.  
For Windows IoT Enterprise installations using ePKEA, it's best practice to run SLMGR.vbs /cpky before finalizing your image to remove the product key from the registry to avoid this situation and ensure that your ePKEA activation allotment isn't depleated.

```powershell
Slmgr.vbs /cpky
```

For more information, see [Slmgr.vbs Advanced Options](/windows-server/get-started/activation-slmgr-vbs-options).

## Activation

### To activate using an internet connection

Windows IoT Enterprise attempts to activate automatically if you're connected to the internet, you can confirm your activation status by selecting **Start** > **Settings** > **System** > **Activation**.

### To activate by phone

1. Select **Start** > **Settings** > **System** > **Activation**
1. Under **Activate Windows Now section**, select **Activate by Phone**
