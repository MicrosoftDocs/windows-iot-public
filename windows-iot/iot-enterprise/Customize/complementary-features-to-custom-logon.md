---
title: Complementary features to Custom Logon
description: Complementary features to Custom Logon
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 0BA4997C-86D3-49C1-9634-F6C47EBDBE8F
author: TerryWarwick
ms.author: twarwick
ms.prod: windows-iot
ms.technology: iot
ms.date: 05/02/2017
ms.topic: article


---
# Complementary features to Custom Logon

You may want to use or change some of the following features in conjunction with Custom Logon to complete the user experience.

> [!TIP]
> We recommend that you remove the power button from the Welcome screen and block the physical power button so that a user cannot turn off the device when using assigned access or Shell Launcher.
>
> Go to **Power Options** &gt; **Choose what the power button does**, change the setting to **Do nothing**, and then **Save changes**.

## Remove buttons from Logon screen

To remove buttons from the Welcome screen, set the appropriate value for **BrandingNeutral** in the following registry key:

```text
HKLM\Software\Microsoft\Windows Embedded\EmbeddedLogon
```

1. Make sure you have enabled Custom Logon following the instructions on the [Custom Logon](Custom-Logon.md) page.
1. In the Windows search bar, type "Registry Editor" to open the **Registry Editor** window.
1. Use the file navigation in the left pane to access **HKLM\Software\Microsoft\Windows Embedded\EmbeddedLogon**.
1. In the right pane, right click on **BrandingNeutral** and select **Modify**.
1. Select the correct **Base** and enter the value for your desired customizations according to the following table, and click **OK** to apply the changes.

> [!NOTE]
> Changing the **Base** of **BrandingNeutral** will automatically convert the value field to the selected base. To ensure you are getting the correct value, select the base before entering the value. 

The following table shows the possible values. To disable multiple Logon screen UI elements, you can select the **Decimal** base when modifying the **BrandingNeutral** value, and combine actions by adding the decimal values of the desired actions and inputting the sum as the value of **BrandingNeutral**. For example, to disable the Power button and the Language button, select the decimal option for the base, then add the decimal values of each, in this case 2 and 4 respectively, and input the total (6) as the value for **BrandingNeutral**.

| Action |Description| Registry value (Hexadecimal) | Registry value (Decimal)|
|--------|------------|----|---|
| Disable all Logon screen UI elements |Disables the Power, Language, and Ease of Access buttons on the Logon and Ctrl+Alt+Del screens. |`0x1` | 1|
| Disable the Power button |Disables the Power button on the Logon and Ctrl+Alt+Del screens.|`0x2` |2|
| Disable the Language button |Disables the Language button on the Logon and Ctrl+Alt+Del screens.|`0x4` |4|
| Disable the Ease of Access button |Disables the Ease of Access button on the Logon and Ctrl+Alt+Del screens.|`0x8` |8|
| Disable the Switch user button |Disables the Switch User button from the Ctrl+Alt+Del screen, preventing a user from switching accounts. | `0x10` |16|
|Disable the Blocked Shutdown Resolver (BSDR) screen|Disables the Blocked Shutdown Resolver (BSDR) screen so that restarting or shutting down the system causes the OS to immediately force close any open applications that are blocking system shut down. No UI is displayed, and users aren't given a chance to cancel the shutdown process. | `0x20` |32|

In the following image of the `[ctrl + alt + del]` screen, you can see the Switch user button highlighted by a light green outline, the Language button highlighted by an orange outline, the Ease of Access button highlighted by a red outline, and the power button highlighted by a yellow outline. If you disable these buttons, they're hidden from the UI.

![custom logon screen](images/customlogoncad.jpg)

You can remove the Wireless UI option from the Welcome screen by using Group Policy.

## Remove Wireless UI from Logon screen

You use the following steps to remove Wireless UI from the Welcome screen

1. From a command prompt, run gpedit.msc to open the Local Group Policy Editor.
1. In the Local Group Policy Editor, under **Computer Configuration**, expand **Administrative Templates**, expand **System**, and then tap or click **Logon**.
1. Double-tap or click **Do not display network selection UI**.

## Additional Customizations

The following table shows additional customizations that can be made using registry keys. 

|Action  |Path  |Registry Key and Value |
|---------|---------|---------|
|Hide Autologon UI   |HKEY_LOCAL_MACHINE\Software\Microsoft\Windows Embedded\EmbeddedLogon  |`HideAutoLogonUI = 1`|
|Hide First Logon Animation    |HKEY_LOCAL_MACHINE\Software\Microsoft\Windows Embedded\EmbeddedLogon  |`HideFirstLogonAnimation = 1`   |
|Disable Authentication Animation  |HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Authentication\LogonUI   |`AnimationDisabled = 1`    |
|Disable Lock Screen   | HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows\Personalization |`NoLockScreen = 1`   |


## Related topics

- [Custom Logon](custom-logon.md)
- [Troubleshooting Custom Logon](troubleshooting-custom-logon.md)
