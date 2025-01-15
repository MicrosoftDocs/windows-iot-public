---
description: Configure policy settings on IoT devices to better control the devices
title: Configure policy settings on IoT devices
author: TerryWarwick
ms.author: twarwick
ms.service: windows-iot
ms.subservice: iot
ms.date: 09/27/2024
ms.topic: article
---

# Lab 3: Configure policy settings on IoT Devices

In lab 2, we enabled device lockdown features on our custom image. In addition to the Windows IoT Enterprise lockdown features, device partners can use a mix of Group Policies and feature customizations to achieve the desired user experience.

In this lab, we recommend some common configuration settings that IoT device partners tend to use. Consider whether each individual configuration setting applies to your device scenario.

## Control Windows Updates

One of the most common requests from device partners is centered around controlling automatic updates on Windows IoT devices. The nature of IoT devices is such that unexpected disruptions, through something like an unplanned update, can create a bad device experience. Questions that you should ask when considering how to control Windows updates:

- Is the device scenario such that any disruption of the workflow is unacceptable?
- How are updates validated prior to deployment?
- What is the update user experience on the device itself?

If you have a device where disruption of the user experience isn't acceptable, you should:

- Consider limiting updates to only certain hours
- Consider disabling automatic updates
- Consider deploying updates either manually or through a controlled third party solution.

### Limit reboots from updates

You can use the Active Hours Group Policy, Mobile device management (MDM), or registry setting to limit updates to only certain hours.

1. Open the Group Policy Editor (gpedit.msc) and navigate to **Computer Configuration\Administrative Templates\Windows Components\Windows Update\Manage end user experience** and open the **Turn off auto-restart for updates during active hours** policy setting.
1. Set the policy to **Enabled**.
1. Set the **Start** and **End** time to the Active Hours window. For example, set Active Hours to start at 4:00AM and end 2:00AM. This allows the system to reboot from updates between the hours of 2:00 AM and 4:00 AM.

### Control UI notifications from the Windows Update client

A device can be configured in a way to hide the UI experience for Windows Update while letting the service itself run in the background and update the system. The Windows Update client still honors the policies set for configuring Automatic Updates, this policy controls the UI portion of that experience.

1. Open the Group Policy Editor (gpedit.msc) and navigate to **Computer Configuration\Administrative Templates\Windows Components\Windows Update\Manage end user experience** and open the **Display options for update notifications** policy setting.
1. Set the policy to **Enabled**.
1. Set **Specify the update notifications display options** to **1 - Disable all notifications, excluding restart warnings**  or **2 - Disable all notifications, including restart warnings**.

### Completely disable automatic Windows Updates

Security and stability are at the core of a successful IoT project, and Windows Update provides updates to ensure Windows IoT Enterprise has the latest applicable security and stability updates.  You might, however, have a device scenario where updating Windows has to be handled manually. For this type of scenario, we recommend disabling automatic updating through Windows Update. In previous versions of Windows device partners could stop and disable the Windows Update service, but this is no longer the supported method for disabling automatic updates. Windows has many policies that allow you to configure Windows Updates in several ways.

To completely disable automatic updating of Windows with Windows Update:

1. Open the Group Policy Editor (gpedit.msc) and navigate to **Computer Configuration\Administrative Templates\Windows Components\Windows update\Manage end user experience** and open the **Configure Automatic Updates** policy setting.
1. Explicitly set the policy to **Disabled**. When this setting is set to Disabled, any available updates from Windows Update must be downloaded and installed manually, which you can do in the Settings app under **Windows Update**.

### Disable access to the Windows Update user experience

In some scenarios, configuring Automatic Updates isn't enough to preserve a desired device experience. For example, an end user may still have access to the Windows Update settings, which would allow manual updates via Windows Update. You can configure Group policy to prohibit access to Windows Update through settings.

To prohibit access to Windows update:

1. Open the Group Policy Editor (gpedit.msc) and navigate to **Computer Configuration\Administrative Templates\Windows Components\Windows update\Manage end user experience** and open the **Remove access to use all Windows update features** policy setting.
1. Set this policy to **Enabled** to prevent the "Check for updates" option for users. Note: Any background update scans, downloads, and installations continue to work as configured. This policy simply prevents the user from accessing the manual check through settings. Use the steps in the [previous section](#completely-disable-automatic-windows-updates) to also disable scans, downloads and installations.

> [!IMPORTANT]
> Be sure to have a well-designed servicing strategy for your device. Disabling Windows Update capabilities leaves the device in a vulnerable state if your device isn't getting updates in another way.

### Prevent drivers from being installed via Windows Update

Sometimes drivers installed from Windows Update can cause issues with a device experience. The following steps prohibit Windows Update from downloading and installing new drivers on the device.

1. Open the Group Policy Editor (gpedit.msc) and navigate to **Computer Configuration\Administrative Templates\Windows Components\Windows update\Manage updates offered from Windows Update** and open the **Do not include drivers with Windows Updates** policy setting.
1. **Enable** this policy, which tells Windows to not include drivers with Windows quality updates.

### Windows Update Summary

You can configure Windows Update in several ways, and not all policies are applicable to all devices. As a general rule, IoT devices require special attention to the servicing and management strategy to be used on the devices. If your servicing strategy is to disable all Windows Update features through policy, the following steps provide a combined list of policies to configure.

1. Open the Group Policy Editor (gpedit.msc) and navigate to **Computer Configuration\Administrative Templates\System\Device Installation** and set the following policies:
   1. **Specify the search server for device driver updates** to **Enabled**, with **Select update server** set to **Search Managed Server**
   1. **Specify search order for device driver source locations** to **Enabled**, with **Select search order** set to **Do not search Windows Update**
1. In the Group Policy Editor, navigate to **Computer Configuration\Administrative Templates\Windows Components\Windows Update** and set the following policies:
   1. **Configure Automatic Updates** to **Disabled**
   2. **Do not include drivers with Windows Updates** to **Enabled**
1. In the Group Policy Editor, navigate to **Computer Configuration\Administrative Templates\System\Internet Communication Management\Internet Communication settings** and set **Turn off access to all Windows Update features** to **Enabled**
1. In the Group Policy Editor, navigate to **Computer Configuration\Administrative Templates\Windows Components\Windows Update\Display options for update notifications** and set the policy to **Enabled** with **Specify the update notifications display options** to **2**

## Configure the system to hide blue screens

Bugchecks on the system (Blue Screen or BSOD) can happen for many reasons. For IoT devices, it's important to hide these errors if they occur. The system can still collect a memory dump for debugging, but the user experience should avoid showing the bugcheck error screen itself. You can configure the system to replace "blue screen" with a blank screen for OS errors.

1. Open Registry Editor on the IoT device and navigate to **Computer\HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\CrashControl**
2. Add a new registry named *DisplayDisabled* as DWORD (32-bit) type with a value data of 1.

## Configure notifications, toasts, and popups

IoT devices typically suppress common Windows dialogs that make sense in PC scenarios but could disrupt the user experience of an IoT device. The simplest way to disable unwanted dialogs is to use a custom shell using [Shell Launcher](/windows/configuration/shell-launcher) or [Assigned Access](/windows/configuration/shell-launcher/single-app-kiosk). If custom shell isn't the right choice, you can set a combination of policies, settings, and registry tweaks that can disable unwanted popups and notifications.

### Notifications

Disabling individual notifications is beneficial in some scenarios. For example, if the device is a tablet device, the Battery Saver notification may be something the user should see, while other notifications such as OneDrive or Photos should be hidden. You might also decide that your device should suppress all notifications, regardless of the OS component that's providing them.

### Hide all notifications

One method to disable notifications is to use Windows' Quiet Hours feature. Quiet Hours works similarly to features found on many smartphones that suppress notifications during certain hours, usually during the overnight hours. In Windows, Quiet Hours can be set to 24x7 so that notifications are never shown.

#### Enable 24x7 Quiet Hours

1. Open the Group Policy Editor (gpedit.msc) and navigate to **User Configuration\Administrative Templates\Start Menu and Taskbar\Notifications**
1. Enable the policy for **Set the time Quiet Hours begins each day**, and set the value to **0**
1. Enable the policy for **Set the time Quiet Hours ends each day**, and set the value to **1439** (there are 1440 minutes per day)

> [!TIP]
> There are other policies in User Configuration\Administrative Templates\Start Menu and Taskbar\Notifications that allow you to get more granular on the exact notifications to disable. These options may be useful in some device scenarios.

#### Message Box Default Reply

This is a registry change that disables MessageBox class boxes from popping up, by having the system automatically select the default button on the dialog (OK or Cancel). This can be useful if third party applications, which the device partner doesn't control, show MessageBox style dialogs. You can learn about this registry value at [Message Box Default Reply](/previous-versions/windows/embedded/aa940743(v=winembedded.5)).

##### Enable MessageBox Default Reply

1. Open the Registry Editor as administrator
1. Create a new Dword registry value under **HKLM\System\CurrentControlSet\Control\Error Message Instrument**, with a value named **EnableDefaultReply**
1. Set the data for the EnableDefaultReply value to 1
1. Test the scenario to ensure it's working as expected

## Security Baseline

Starting with the first release of Windows, an accompanying set of policies called the Security Baseline have been provided with each Windows release. A security baseline is a group of Microsoft-recommended configuration settings based on feedback from Microsoft security engineering teams, product groups, partners, and customers. The Security Baseline is a good way to quickly enable recommended security settings on IoT devices.

> [!NOTE]
> Devices requiring certification such as STIG would benefit from using the Security Baseline as a starting point. The security baseline is delivered as part of the [Security Compliance Toolkit](/windows/security/threat-protection/security-compliance-toolkit-10)

You can download the [Security Compliance Toolkit](https://www.microsoft.com/download/details.aspx?id=55319) from the Download Center.

1. Select **Download** on the link above. Select the *Windows Version xxxx Security Baseline.zip* and the *LGPO.zip*. Be sure to choose the version that matches the version of Windows you're deploying.

1. Extract the *Windows Version xxxx Security Baseline.zip* file and the *LGPO.zip* file on the IoT device.

1. Copy *LGPO.exe* to the *Scripts\Tools* folder of the *Windows Version xxxx Security Baseline*. LGPO is needed by the security baseline installation script but must be downloaded separately.

1. From an Administrative Command Prompt run:

   ```cmd
   Client_Install_NonDomainJoined.cmd
   ```

    or, if the IoT device will be part of an Active Directory domain:

   ```cmd
   Client_Install_DomainJoined.cmd
   ```

1. Press Enter when prompted to run the script and then reboot the IoT device.

### What you can expect

Many settings are included as part of the security baseline. In the Documentation folder, you find an Excel spreadsheet that outlines all the policies set by the baseline. You'll immediately notice that user account password complexity has been changed from its default, so you may need to update user account passwords on the system or as part of your deployment. Additionally, policies are configured for USB drive data access. Copying data from the system is protected by default now. Continue to explore the other settings added by the security baseline.

## Microsoft Defender

Anti-virus protection is required in many IoT device scenarios, especially devices that are more fully featured and running an operating system like Windows IoT Enterprise. For devices such as kiosks, retail POS, ATM, etc. Microsoft Defender is included and enabled by default as part of the Windows IoT Enterprise installation. You may have a scenario where you want to modify the default Microsoft Defender user experience. For example, disabling notifications about scans performed, or even disabling scheduled deep scans in favor of only using real-time scanning. The policies below are useful for preventing unwanted UI to be created by Microsoft Defender.

1. Open the Group Policy Editor (gpedit.msc) and navigate to **Computer Configuration\Administrative Templates\Windows Components\Microsoft Defender Antivirus\Scan** and set:
   1. **Check for the latest virus and spyware definitions before running a schedule scan** to **Disabled**
   1. **Specify the maximum percentage of CPU utilization during a scan** to **5**
   1. **Turn on catch up full scan** to **Disabled**
   1. **Turn on catch up quick scan** to **Disabled**
   1. **Create a system restore point** to **Disabled**
   1. **Define the number of days after which a catch-up scan is forced** to **20** (this is a "just in case setting" and shouldn't be needed if catch-up scans are enabled)
   1. **Specify the scan type to use for a scheduled scan** to **Quick scan**
   1. **Specify the day of the week to run a scheduled scan** to **0x8 (never)**

1. In Group Policy Editor navigate to **Computer Configuration\Administrative Templates\Windows Components\Microsoft Defender Antivirus\Security Intelligence Updates** and set:
   1. **Define the number of days before spyware security intelligence is considered out of date** to **30**
   1. **Define the number of days before virus security intelligence is considered out of date** to **30**
   1. **Turn on scan after security intelligence update** to **Disabled**
   1. **Initiate security intelligence update on startup** to **Disabled**
   1. **Specify day of the week to check for security intelligence updates** to **0x8 (never)**
   1. **Define the number of days after which a catch-up security intelligence update is required** to **30**

**Windows Components\Microsoft Defender Antivirus** has additional policies, check each setting description to see if it applies to your IoT device.

## Next steps

Now that you've created an image that's tailored to your desired user experience, you can capture your image so it can be deployed to as many devices as you'd like. Lab 4 covers how to prepare an image for capture, and then deploy it to a device.

>[!div class="nextstepaction"]
>[Go to lab 4](iot-ent-sysprep-capture-deploy.md)
