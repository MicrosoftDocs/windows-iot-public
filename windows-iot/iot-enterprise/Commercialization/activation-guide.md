---
title: Windows IoT Enterprise OEM Activation using ePKEA
description: OEMs use Embedded Product Key Entry Activation (ePKEA) to enable activation of Windows IoT Enterprise for a predetermined number of specialized devices.
author: terrywarwick
ms.author: twarwick
ms.service: windows-iot
ms.subservice: iot
ms.topic: reference
ms.date: 05/22/2024
---

# OEM Activation

As a device maker, you can install and use the Windows IoT Enterprise operating system to develop and test prototype customer systems. Any images installed without a product key or using the default manufacturing key won't function for more than 30 days after the first boot of an image on a prototype system.

Activation is the process of registering Windows IoT Enterprise with Microsoft to ensure the product is genuine and reduce piracy to ensure customers receive the product quality that they expect from a Windows-based operating system.

> [!IMPORTANT]
>Windows IoT Enterprise devices produced by OEMs must be enabled for activation before leaving the factory.

Windows IoT Enterprise provides three options for enabling activation, including:

| Activation&nbsp;Model | Description |
|:----------------:| ----------- |
| PKEA | **Product Key Entry Activation** </br> Requires a unique 5 by 5 product key to be applied to each device produced.  |
| ePKEA | **Embedded Product Key Entry Activation**  </br> ePKEA is designed exclusively for OEMs building specialized devices base on Windows IoT Enterprise. A single ePKEA product key comes with the ability to activate a predetermined number of devices. Each successful activation via internet connection or by telephone decrements the available activation count associated with the OEMs ePKEA. Request a new ePKEA before fully depleting the available activations associated with your current ePKEA to prevent activation failures. |
| OA 3.0 | **OEM Activation 3.0 (OA3)** </br> The OA 3.0 system enables OEMs to develop an internal inventory management system to manage the ordering and receiving of Windows product keys and the creation and reporting process for the Computer Build Report. You must include an edition specific Default Product Key in each golden image of Windows IoT Enterprise. The default product key can't activate Windows, but rather instructs Windows to search for an OA 3.0 product key that stored in the device’s firmware. |

This article focuses on using ePKEA to enable activation for Windows IoT Enterprise based devices. For more information about OA 3.0, see  [OEM Activation 3.0 system](/windows-hardware/manufacture/desktop/oem-activation-3).

## Managing your ePKEA Product Keys

> [!IMPORTANT]
> An ePKEA product key should be handled confidentially to prevent piracy from depleting your available activation count resulting in your customers being unable to activate the devices they purchased from you.
>
> You should also monitor the remaining activation count monitored to ensure that the consumed activations match the number of devices produced.

### Protect your Product Key

Remove your ePKEA from the registry to prevent disclosure attack where malicious code extracts your product key from the image. If a bad operator can extract the product key from your devices it could be used to enable activation on their own devices, draining the available activations associated with your ePKEA.
  
You should run `SLMGR.vbs /cpky` before finalizing your image to remove the product key from the registry to avoid your ePKEA from a disclosure attack and ensure that your ePKEA activation allotment isn't depleted.

```powershell
Slmgr.vbs /cpky
```

For more information, see [Slmgr.vbs Options](/windows-server/get-started/activation-slmgr-vbs-options).

### Monitor activations remaining for ePKEA product keys

ePKEA product keys are similar to MAK product keys that the Volume Activation Management Tool (VAMT) was designed to support, therefore it also works with ePKEA product keys. You can use the Volume Activation Management Tool (VAMT) to monitor the number of activations remaining for your ePKEA keys. Just add your ePKEA keys to VAMT and select Product key data online to retrieve the number of remaining activations for the ePKEA.

For more information, see [Using VAMT to Manage Product Keys](/windows/deployment/volume-activation/add-remove-product-key-vamt).

## Manufacturing Process

You should be familiar with the Windows desktop manufacturing process before you can enable activation. There are several different methods to deploy and customize your Windows IoT Enterprise image. After selecting your manufacturing process, you can incorporate a compatible approach to enable activation using your ePKEA based product key.

For more information, see [Windows Manufacturing Overview](/windows-hardware/manufacture).

## Enable Activation

You can install your production ePKEA product key using any of the following four methods:

<!--markdownlint-disable-next-line -->
# [Interactive Setup](#tab/Interactive-Setup)

If you choose to create your image using the interactive setup experience, you can supply your production ePKEA, the default manufacturing key or skip the product key entry step, however only your production ePKEA enables activation. The following table explains each scenario.

| When prompted for Product Key | Result |
| ----------- | -----------|
| Enter your production ePKEA           | Production image is fully enabled for activation |
| Enter the 'default manufacturing key' | Your device isn't enabled for activation and you must install your production ePKEA during Audit Mode. |
| Skip the product key entry screen     | You must select either Windows IoT Enterprise or Windows IoT Enterprise LTSC to proceed. Your device isn't enabled for activation when setup is complete and you must install your production ePKEA during Audit Mode. |

For more information on interactive setup, see [Boot and install Windows](/windows-hardware/manufacture/desktop/boot-and-install-windows).

<!--markdownlint-disable-next-line -->
# [Unattended Setup](#tab/Unattended-Setup)

Similarly to Interactive Setup, you can supply either your production ePKEA or the default manufacturing key using the [ProductKey](/windows-hardware/customize/desktop/unattend/microsoft-windows-shell-setup-productkey) setting of the unattend.xml answer file. The same applies that only supplying your production ePKEA fulfills the requirement to enable activation.

For more information, see [Windows Setup Automation Overview](/windows-hardware/manufacture/desktop/windows-setup-automation-overview).

<!--markdownlint-disable-next-line -->
# [Audit Mode](#tab/Audit-Mode)

Audit mode allows you to make more changes to your Windows IoT Enterprise image before you send the computer to a customer or capture the image for replication during the manufacturing process. Using audit mode, you can install drivers including a driver package, install applications, or make other updates to the operating system while it's running, including enabling activation.
For more information on getting started with Audit mode, see [Audit Mode Overview](/windows-hardware/manufacture/desktop/audit-mode-overview).
While you are in Audit mode, you can apply your production ePKEA to your image using the graphical user interface provided by Settings > Activation or the command line utility SLMGR.vbs.

- **Method 1: Settings > Activation graphical user interface**

  Access the activation graphical user interface using one of the following options:

  1. Select Start then begin typing Activation and select Activation settings once it appears
  1. Select Start > Settings > System > Activation
  1. Select Start > All Apps > Settings > System > Activation
  1. Press <kbd>Windows</kbd> + <kbd>R</kbd> and type ```slui.exe``` into the **Run** dialog and press <kbd>Enter</kbd>.

- **Method 2: Command Line | SLMGR.vbs**

  To inject the product key into Windows IoT Enterprise, open a Windows PowerShell instance as an Administrator then execute the following command using your ePKEA product key.

  ```powershell
  Slmgr.vbs /ipk XXXXX-XXXXX-XXXXX-XXXXX-XXXXX
  ```

  This command can be incorporated into a larger script while applying other configuration settings by prepending cscript to the command as follows.

  ```powershell
  cscript c:\windows\system32\Slmgr.vbs /ipk XXXXX-XXXXX-XXXXX-XXXXX-XXXXX
  ```

  For more information, see [Slmgr.vbs Options](/windows-server/get-started/activation-slmgr-vbs-options).

> [!IMPORTANT]
> While you are still running in Audit Mode, remove your ePKEA from the registry to prevent disclosure attack where malicious code extracts your product key from the image by running the following command line from an elevated command shell.
>
> ```cmd
> slmgr.vbs /cpky
> ```

> [!TIP]
> Be sure to finalize your image using the generalize option of Sysprep to boot into the Out of Box Experience (oobe) for your customer's first experience.
>
> For more information on finalizing your image for replication, see [Sysprep Process Overview](/windows-hardware/manufacture/desktop/sysprep-process-overview).

<!--markdownlint-disable-next-line -->
# [Offline Image](#tab/Offline-Image)

### Offline image

You can also make changes to an offline mounted Windows image without booting into the operating system you’re going to modify. For more information about servicing an offline image, see [Modify a Windows Image Using DISM](/windows-hardware/manufacture/desktop/mount-and-modify-a-windows-image-using-dism).

You can install your ePKEA into the offline image using either `Set-WindowsProductKey` or `DISM /SetProductKey` by running either command from an elevated PowerShell command window.

- To apply your ePKEA to an offline image using **Set-WindowsProductKey** from PowerShell.

   ```powershell
   Set-WindowsProductKey -Path “c:\offline” -ProductKey “XXXXX-XXXXX-XXXXX-XXXXX-XXXXX”
   ```

   For more information, see [Set-WindowsProductKey](/powershell/module/dism/set-windowsproductkey).

- To apply your ePKEA to an offline image using **DISM /SetProductKey** from PowerShell.

   ```powershell
   Dism /Image:C:\offline /Set-ProductKey:XXXXX-XXXXX-XXXXX-XXXXX-XXXXX
   ```

   For more information, see [DISM /SetProductKey](/windows-hardware/manufacture/desktop/dism-windows-edition-servicing-command-line-options#set-productkey).

> [!TIP]
> Once you complete the customizations that are required for your offline image, you must commit the changes and dismount the image.
>
> For more information, see Modify a [Windows Image Using DISM](/windows-hardware/manufacture/desktop/mount-and-modify-a-windows-image-using-dism).

---

## Activate your device

A Windows IoT Enterprise device that is enabled for activation is fully operational without an internet connection. Being fully operational without an internet connection is useful for devices deployed in disconnected environments. Activation is deferred until the device is connected to a network that can access the Microsoft Activation Servers. If the device believes it can get to the Microsoft Activation Servers, Windows IoT Enterprise automatically attempts to activate resulting in either a successful activation or a failed activation. Windows IoT Enterprise can't return to a deferred activation state once activation is attempted. You can activate your production ePKEA product key using any of the following three methods:

<!--markdownlint-disable-next-line -->
# [Internet Connection](#tab/Internet-Connection)

Windows IoT Enterprise attempts to activate automatically if you have an internet connection. You can confirm your activation status in Settings or using the Windows Software Licensing Management Tool (SLMGR.VBS).

- **Settings**  

   To view your activation status in Settings, select **Start** > **Settings** > **System** > **Activation**.

   If your device shows that it isn't activated, you can trigger an activation attempt by selecting **Activate Windows now**.

- **Windows Software Licensing Management Tool (SLMGR.VBS)**

   Using the keyboard on your device press <kbd>Windows</kbd> + <kbd>R</kbd> and type one of the following commands into the "Run" dialog.

   | Information Level | Command          |
   | ----------------- |  --------------- |
   | Abbreviated       | `slmgr.vbs /dli` |
   | Verbose           | `slmgr.vbs /dlv` |

   Note: If you prefer, these commands can also be run from a PowerShell command prompt.

   A result of **License Status:Licensed** indicates the device is activated If your device shows that it isn't activated, you can also trigger an activation attempt using `slmgr.vbs /ato`.

   For more information, see [Slmgr.vbs Options](/windows-server/get-started/activation-slmgr-vbs-options).

<!--markdownlint-disable-next-line -->
# [Telephone](#tab/Telephone)

You can activate your device by using a telephone to call the Microsoft Product Activation Center. The automated phone system asks for your installation ID (IID) then provide you with a 48-digit confirmation ID.

1. Using the keyboard on your device press <kbd>Windows</kbd> + <kbd>R</kbd> and type the following command into the "Run" dialog.

   ```text
   SLUI 4
   ```

1. Call the Microsoft Activation Center using the number on your screen.
1. Follow the automated instructions and, when prompted, provide the 63-digit Installation ID.
1. Enter the confirmation ID provided by the phone activation system then select **Activate Windows**.

<!--markdownlint-disable-next-line -->
# [Volume Activation Managmenet Tool (VAMT)](#tab/VAMT)

You can use the Volume Activation Management Tool (VAMT) to perform activation for Windows IoT Enterprise devices that don't have Internet access. Just like a Multiple activation Key (MAK), Embedded Product Key Entry Activation (ePKEA) is eligible for proxy activation.

For information on using VAMT to activate your Windows IoT Enterprise devices that don't have Internet access, see [Using Volume Activation Management Tool to Perform Proxy Activation](/windows/deployment/volume-activation/proxy-activation-vamt).

---

## Frequently asked questions

- **How do I acquire a ePKEA that I can use for my devices?**

  **Answer:**  You need to have a valid Client License Agreement (CLA) in place with Microsoft and then you would fill out and submit the Special Key Request form. To acquire an ePKEA product key, contact your Windows IoT Distributor, or your Microsoft Account Manager.

- **Are there any logs where can I tell that my device has attempted to activate?**

  **Answer:**  In the System Event Viewer, look for a 118 event in the Client Licensing Event Log. The 118 event indicates that the device could access the Microsoft Activation Servers. This would cause the device to come out of Deferred activation and attempted to activate.

- **How do I ensure that activation occurs at a specific time?**

  **Answer:**  Configure Windows to attempt to activate on the next reboot by adding SLMGR.vbs /ato to the RunOnce registry key using the following PowerShell command.

  ```powershell
  Reg add HkLm\Software\microsoft\Windows\CurrentVersion\RunOnce /v autoactivate /t REG_SZ /d “C:\windows\system32\slmgr.vbs /ato”
  ```

- **How do I check my activation status?**

  **Answer:** You can check your activation status using Settings or the Software Licensing Management Tool.
  
  - To check your activation status using Settings, using your keyboard, press <kbd>Windows</kbd> + <kbd>R</kbd>, then type ```slui.exe``` into the **Run** dialog and press <kbd>Enter</kbd>.
  - To check your activation status using the Software Licensing Management Tool, using your keyboard, press <kbd>Windows</kbd> + <kbd>R</kbd>, then type ```slmgr.vbs /dlv``` into the **Run** dialog and press <kbd>Enter</kbd>.

- **What causes a device to require reactivation?**

  **Answer:**  Anytime a hardware change is made to an active device, the device is classified as either *in-tolerance* or *out-of-tolerance*. A minor change such as adding memory or changing the hard drive would typically be considered *in-tolerance* and not require reactivation. Major hardware changes, such as changing the motherboard, can cause a device to be considered *out-of-tolerance*, which sets the device back to a not activated state. A large number of small hardware changes made at the same time can also push the device into an *out-of-tolerance* state.

- **Why does my device show *Activate Windows* in the lower right corner of the display?**

  **Answer:**  When a device requires reactivation, a watermark is displayed in the lower-right corner of each attached display indicating that the device isn't activated. As a result you can't change the Windows personalization settings, such as desktop background or the lock screen background until the device is reactivated.

- **How do I confirm the product key used to enable activation?**

  **Answer:** You can retrieve the last five digits of the product key used to enable activation using the following PowerShell command.

  ```powershell
  slmgr.vbs /dli
  ```

  The last five digits of the product key used to enable activation can be found after the *Partial Product Key:* value in the output.
  
- **How does the use of Unified Write Filer (UWF) impact activation?**

  **Answer:** Windows activates as expected. However, if Unified Write Filter (UWF) is enabled when Windows is activated, restarting the device resets the activation state and you must reactivate the device. Although the device doesn't stay activated, UWF is doing exactly what is it supposed to do. You must activate Windows before enabling UWF, or suspend UWF before attempting to activate in order for the activation state to be retained.

- **I'm having problems with my ePKEA who can I contact for help?**

  **Answer:** To get help with the PKEA, contact your Windows IoT Distributor, or your Microsoft Account Manager.

- **I have more questions on activation, deploying the ePKEA or using VAMT who can I reach out to for help?**

  **Answer:**  To get more help with Activation contact your Windows IoT Distributor, or your Microsoft Account Manager.
  
## Related content

- [Volume Activation Management Tool (VAMT)](/windows/deployment/volume-activation/introduction-vamt)
- [Desktop Manufacturing Overview](/windows-hardware/manufacture/desktop/)
- [Software Licensing Management Tool (SLMGR)](/windows-server/get-started/activation-slmgr-vbs-options)
- [Modify a Windows Image](/windows-hardware/manufacture/desktop/modify-an-image)
- [Audit Mode Overview](/windows-hardware/manufacture/desktop/audit-mode-overview)
- [Windows boot and installation overview](/windows-hardware/manufacture/desktop/boot-and-install-windows)
- [Sysprep (System Preparation) Overview](/windows-hardware/manufacture/desktop/sysprep--system-preparation--overview)
- [Windows Setup Automation using an Unattend.xml](/windows-hardware/customize/desktop/unattend/)
- [Get help with Windows activation errors](https://support.microsoft.com/windows/get-help-with-windows-activation-errors-09d8fb64-6768-4815-0c30-159fa7d89d85)
- [Manufacturing Windows Engineering Guide (WEG)](/windows-hardware/manufacture/desktop/manufacturing-windows-engineering-guide)
- [OEM 3.0 Activation System](/windows-hardware/manufacture/desktop/manufacturing-windows-engineering-guide)
