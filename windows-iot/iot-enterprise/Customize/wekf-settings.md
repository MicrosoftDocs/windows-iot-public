---
title: WEKF_Settings
description: WEKF_Settings
author: TerryWarwick
ms.author: twarwick
ms.service: windows-iot
ms.subservice: iot
ms.date: 05/20/2024
ms.topic: article


---
# WEKF_Settings

Enables or disables settings for Keyboard Filter.

## Syntax

```powershell
class WEKF_Settings {
  [Key] string Name;
  [Read, Write] string Value;
};
```

## Members

The following tables list any methods and properties that belong to this class.

### Properties

| Property | Data&nbsp;type | Qualifiers | Description |
|----------|----------------|------------|-------------|
| **Name** | string | [key] | Indicates the name of the Keyboard Filter setting that this object represents. See the Remarks section for a list of valid setting names. |
| **Value** | string | [read,&nbsp;write] | Represents the value of the **Name** setting. The value is not case-sensitive. </br> See the Remarks section for a list of valid values for each setting. |

### Remarks

You must be signed in to an administrator account to make any changes to this class.

Each **WEKF_Settings** object represents a single Keyboard Filter setting. You can enumerate across all **WEKF_Settings** objects to see the value of all Keyboard Filter settings.

The following table lists all settings available for Keyboard Filter.

| Setting name | Description |
|--------------|-------------|
| **DisableKeyboardFilterForAdministrators** | This setting specifies whether Keyboard Filter is enabled or disabled for administrator accounts. Set to **true** to disable Keyboard Filter for administrator accounts; otherwise, set to **false**. Set to **true** by default. |
| **ForceOffAccessibility** | This setting specifies whether Keyboard Filter blocks users from enabling Ease of Access features. Set to **true** to force disabling the Ease of Access features. Set to **false** to allow enabling the Ease of Access features. Set to **false** by default.</br>Changing this setting to **false** does not automatically enable Ease of Access features; you must manually enable them. |
| **BreakoutKeyScanCode** | This setting specifies the scan code of the key that enables a user to break out of an account that is locked down with Keyboard Filter. A user can press this key consecutively five times to switch to the Welcome screen.</br>By default, the BreakoutKeyScanCode is set to the scan code for the left Windows logo key. |

One instance of the **WEKF_Settings** class exists for each valid setting.

Changes to the **DisableKeyboardFilterForAdministrator** setting are applied when an administrator account signs in, and applies to all applications run during the user session. If a user without an administrator account runs an application as an administrator, Keyboard Filter is still enabled, regardless of the **DisableKeyboardFilterForAdministrator** setting.

Changes to the **BreakoutKeyScanCode** setting do not take effect until you restart the device.

If the **BreakoutKeyScanCode** is set to the scan code for either the left Windows logo key or the right Windows logo key, both Windows Logo keys will work as the breakout key.

The **BreakoutKeyScanCode** setting only applies to accounts where Keyboard Filter is active. If the scan code is set to a value that does not map to any key, such as 0 (zero), then you must use another method to access the Welcome screen if you need to service the device, such as remotely connecting, or restarting the device if automatic sign-in is not enabled.

> [!IMPORTANT]
> On some devices, if the breakout key is pressed too rapidly, the key presses may not register. We recommend that you include a slight pause between each breakout key press.

> [!WARNING]
> When setting the **BreakoutKeyScanCode**, be sure to use the scan code of the key, and not the virtual key value.

### Example

The following Windows PowerShell script demonstrates how to use this class to modify the breakout mode key for Keyboard Filter. This example sets the **BreakoutKeyScanCode** setting to the scan code for the Home key on a standard keyboard.

```powershell
#---Define variables---

$COMPUTER = "localhost"
$NAMESPACE = "root\standardcimv2\embedded"

# Define the decimal scan code of the Home key

$HomeKeyScanCode = 71

# Get the BreakoutKeyScanCode setting from WEKF_Settings

$BreakoutMode = get-wmiobject -class wekf_settings -namespace $NAMESPACE | where {$_.name -eq "BreakoutKeyScanCode"}

# Set the breakout key to the Home key.

$BreakoutMode.value = $HomeKeyScanCode

# Push the change into the WMI configuration. You must restart your device before this change takes effect.

$BreakoutMode.put()
```

## Requirements

| Windows Edition        | Supported |
|:-----------------------|:---------:|
| Windows Home           | No        |
| Windows Pro            | No        |
| Windows Enterprise     | Yes       |
| Windows Education      | Yes       |
| Windows IoT Enterprise | Yes       |

## Related topics

[Keyboard Filter WMI provider reference](keyboardfilter-wmi-provider-reference.md)

[Keyboard Filter](keyboardfilter.md)
