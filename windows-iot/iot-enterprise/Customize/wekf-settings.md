---
title: WEKF\_Settings
description: WEKF\_Settings
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 976a98c4-9ca9-4ac9-b1d5-842bc0ffe396


ms.date: 05/02/2017
ms.topic: article


---
# WEKF\_Settings

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

### <a href="" id="pro"></a>Properties

<table>
<colgroup>
<col width="25%" />
<col width="25%" />
<col width="25%" />
<col width="25%" />
</colgroup>
<thead>
<tr class="header">
<th>Property</th>
<th>Data type</th>
<th>Qualifiers</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Name</strong></p></td>
<td><p>string</p></td>
<td><p>[key]</p></td>
<td><p>Indicates the name of the Keyboard Filter setting that this object represents. See the Remarks section for a list of valid setting names.</p></td>
</tr>
<tr class="even">
<td><p><strong>Value</strong></p></td>
<td><p>string</p></td>
<td><p>[read, write]</p></td>
<td><p>Represents the value of the <strong>Name</strong> setting. The value is not case-sensitive.</p>
<p>See the Remarks section for a list of valid values for each setting.</p></td>
</tr>
</tbody>
</table>

### Remarks

You must be signed in to an administrator account to make any changes to this class.

Each **WEKF\_Settings** object represents a single Keyboard Filter setting. You can enumerate across all **WEKF\_Settings** objects to see the value of all Keyboard Filter settings.

The following table lists all settings available for Keyboard Filter.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Setting name</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>DisableKeyboardFilterForAdministrators</strong></p></td>
<td><p>This setting specifies whether Keyboard Filter is enabled or disabled for administrator accounts. Set to <strong>true</strong> to disable Keyboard Filter for administrator accounts; otherwise, set to <strong>false</strong>. Set to <strong>true</strong> by default.</p></td>
</tr>
<tr class="even">
<td><p><strong>ForceOffAccessibility</strong></p></td>
<td><p>This setting specifies whether Keyboard Filter blocks users from enabling Ease of Access features. Set to <strong>true</strong> to force disabling the Ease of Access features. Set to <strong>false</strong> to allow enabling the Ease of Access features. Set to <strong>false</strong> by default.</p>
<p>Changing this setting to <strong>false</strong> does not automatically enable Ease of Access features; you must manually enable them.</p></td>
</tr>
<tr class="odd">
<td><p><strong>BreakoutKeyScanCode</strong></p></td>
<td><p>This setting specifies the scan code of the key that enables a user to break out of an account that is locked down with Keyboard Filter. A user can press CTRL+ALT+DELETE to switch to the Welcome screen.</p>
<p>Set to the scan code for the left Windows logo key by default.</p></td>
</tr>
</tbody>
</table>

One instance of the **WEKF\_Settings** class exists for each valid setting.

Changes to the **DisableKeyboardFilterForAdministrator** setting are applied when an administrator account signs in, and applies to all applications run during the user session. If a user without an administrator account runs an application as an administrator, Keyboard Filter is still enabled, regardless of the **DisableKeyboardFilterForAdministrator** setting.

Changes to the **BreakoutKeyScanCode** setting do not take effect until you restart the device.

If the **BreakoutKeyScanCode** is set to the scan code for either the left Windows logo key or the right Windows logo key, both Windows Logo keys will work as the breakout key.

The **BreakoutKeyScanCode** setting only applies to accounts where Keyboard Filter is active. If the scan code is set to a value that does not map to any key, such as 0 (zero), then you must use another method to access the Welcome screen if you need to service the device, such as remotely connecting, or restarting the device if automatic sign-in is not enabled.

**Important**  
On some devices, if the breakout key is pressed too rapidly, the key presses may not register. We recommend that you include a slight pause between each breakout key press.

> [!Warning]
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

| Windows Edition       | Supported |
|:----------------------|:----------|
| Windows 10 Home       | No        |
| Windows 10 Pro        | No        |
| Windows 10 Enterprise | Yes       |
| Windows 10 Education  | Yes       |

## Related topics

[Keyboard Filter WMI provider reference](keyboardfilter-wmi-provider-reference.md)

[Keyboard Filter](keyboardfilter.md)
