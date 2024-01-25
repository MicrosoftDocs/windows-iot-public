---
title: Complementary features to Custom Logon
description: Complementary features to Custom Logon
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 0BA4997C-86D3-49C1-9634-F6C47EBDBE8F
author: TerryWarwick
ms.author: twarwick
ms.service: windows-iot
ms.subservice: iot
ms.date: 05/02/2017
ms.topic: article


---
# Complementary features to Custom Logon

You may want to use or change some of the following features in conjunction with Custom Logon to complete the user experience.

> [!TIP]
> We recommend that you remove the power button from the Welcome screen and block the physical power button so that a user cannot turn off the device when using assigned access or Shell Launcher.
>
> Go to **Power Options** &gt; **Choose what the power button does**, change the setting to **Do nothing**, and then **Save changes**.

## Remove buttons from Welcome screen

To remove buttons from the Welcome screen, set the appropriate value for **BrandingNeutral** in the following registry key:

```text
HKLM\\Software\\Microsoft\\Windows Embedded\\EmbeddedLogon
```

The following table shows the possible values. To disable multiple Welcome screen UI elements, combine these values using bitwise exclusive-or logic.

| Action | Registry value |
|--------|----------------|
| Disable all Welcome screen UI elements | `static const DWORD EMBEDDED_DISABLE_LOGON_ANCHOR_ALL = 0x1` |
| Disable the Power button | `static const DWORD EMBEDDED_DISABLE_LOGON_ANCHOR_SHUTDOWN = 0x2` |
| Disable the Language button | `static const DWORD EMBEDDED_DISABLE_LOGON_ANCHOR_LANGUAGE = 0x4` |
| Disable the Ease of Access button | `static const DWORD EMBEDDED_DISABLE_LOGON_ANCHOR_EASEOFACCESS = 0x8` |
| Disable the Switch user button | `static const DWORD EMBEDDED_DISABLE_BACK_BUTTON = 0x10` |
|Disable the Blocked Shutdown Resolver (BSDR) screen so that restarting or shutting down the system causes the OS to immediately force close any open applications that are blocking system shut down. No UI is displayed, and users are not given a chance to cancel the shutdown process | `static const DWORD EMBEDDED_DISABLE_BSDR= 0x20` |

In the following image of the `[ctrl + alt + del]` screen, you can see the Switch user button highlighted by a light green outline, the Language button highlighted by an orange outline, the Ease of Access button highlighted by a red outline, and the power button highlighted by a yellow outline. If you disable these buttons, they are hidden from the UI.

![custom logon screen](images/customlogoncad.jpg)

You can remove the Wireless UI option from the Welcome screen by using Group Policy.

## Remove Wireless UI from Welcome screen

You use the following steps to remove Wireless UI from the Welcome screen

1. From a command prompt, run gpedit.msc to open the Local Group Policy Editor.
1. In the Local Group Policy Editor, under **Computer Configuration**, expand **Administrative Templates**, expand **System**, and then tap or click **Logon**.
1. Double-tap or click **Do not display network selection UI**.

## Related topics

- [Custom Logon](custom-logon.md)
- [Troubleshooting Custom Logon](troubleshooting-custom-logon.md)
