---
title: Keyboard Filter key names
description: Keyboard Filter key names
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 5f3772bb-fdd2-4816-9994-bd2523099400
author: TerryWarwick
ms.author: twarwick
ms.prod: windows-iot
ms.technology: iot
ms.date: 05/02/2017
ms.topic: article


---
# Keyboard Filter key names

You can configure Keyboard Filter to block keys or key combinations. A key combination consists of one or more modifier keys, separated by a plus sign (+), and either a key name or a key scan code. In addition to the keys listed in the following tables, you can use the predefined key combinations names as custom key combinations. However, we recommend using the predefined key settings when enabling or disabling predefined key combinations.

The key names are grouped as follows:

- [Modifier keys](#modifier-keys)
- [System keys](#system-keys)
- [Cursor and edit keys](#cursor-and-edit-keys)
- [State keys](#state-keys)
- [OEM keys](#oem-keys)
- [Function keys](#function-keys)
- [Numeric keypad keys](#numeric-keypad-keys)

## Modifier keys

You can use the modifier keys listed in the following table when you configure keyboard filter. Multiple modifiers are separated by a plus sign (+). You can also configure Keyboard Filter to block any modifier key even if it’s not part of a key combination.

| Modifier key name | Virtual key | Description |
| ----------------- | ----------- | ----------- |
| `Ctrl`     | VK_CONTROL  | The <kbd>Ctrl</kbd> key |
| `LCtrl`    | VK_LCONTROL | The left <kbd>Ctrl</kbd> key |
| `RCtrl`    | VK_RCONTROL | The right <kbd>Ctrl</kbd> key |
| `Control`  | VK_CONTROL  | The <kbd>Ctrl</kbd> key |
| `LControl` | VK_LCONTROL | The left <kbd>Ctrl</kbd> key |
| `RControl` | VK_RCONTROL | The right <kbd>Ctrl</kbd> key |
| `Alt`      | VK_MENU     | The <kbd>Alt</kbd> key |
| `LAlt`     | VK_LMENU    | The left <kbd>Alt</kbd> key |
| `RAlt`     | VK_RMENU    | The right <kbd>Alt</kbd> key |
| `Shift`    | VK_SHIFT    | The <kbd>Shift</kbd> key |
| `LShift`   | VK_LSHIFT   | The left <kbd>Shift</kbd> key |
| `RShift`   | VK_RSHIFT   | The right <kbd>Shift</kbd> key |
| `Win`      | VK_WIN      | The <kbd>Windows</kbd> logo key |
| `LWin`     | VK_LWIN     | The left <kbd>Windows</kbd> logo key |
| `RWin`     | VK_RWIN     | The right <kbd>Windows</kbd> logo key |
| `Windows`  | VK_WIN      | The <kbd>Windows</kbd> logo key |
| `LWindows` | VK_LWIN     | The left <kbd>Windows</kbd> logo key |
| `RWindows` | VK_RWIN     | The right <kbd>Windows</kbd> key |

## System keys

| Modifier key name | Virtual key | Description |
| ----------------- | ----------- | ----------- |
| `Ctrl`     | VK_CONTROL   | The <kbd>Ctrl</kbd> key |
| `LCtrl`    | VK_LCONTROL  | The left <kbd>Ctrl</kbd> key |
| `RCtrl`    | VK_RCONTROL  | The right <kbd>Ctrl</kbd> key |
| `Control`  | VK_CONTROL   | The <kbd>Ctrl</kbd> key |
| `LControl` | VK_LCONTROL  | The left <kbd>Ctrl</kbd> key |
| `RControl` | VK_RCONTROL  | The right <kbd>Ctrl</kbd> key |
| `Alt`      | VK_MENU      | The <kbd>Alt</kbd> key |
| `LAlt`     | VK_LMENU     | The left <kbd>Alt</kbd> key |
| `RAlt`     | VK_RMENU     | The right <kbd>Alt</kbd> key |
| `Shift`    | VK_SHIFT     | The <kbd>Shift</kbd> key |
| `LShift`   | VK_LSHIFT    | The left <kbd>Shift</kbd> key |
| `RShift`   | VK_RSHIFT    | The right <kbd>Shift</kbd> key |
| `Win`      | VK_WIN       | The <kbd>Windows</kbd> logo key |
| `LWin`     | VK_LWIN      | The left <kbd>Windows</kbd> logo key |
| `RWin`     | VK_RWIN      | The right <kbd>Windows</kbd> logo key |
| `Windows`  | VK_WIN       | The <kbd>Windows</kbd> logo key |
| `LWindows` | VK_LWIN      | The left <kbd>Windows</kbd> logo key |
| `RWindows` | VK_RWIN      | The right <kbd>Windows</kbd> logo key

## Cursor and edit keys

| Key name | Virtual key | Description |
| ----------------- | ----------- | ----------- |
| `PageUp`   | VK_PRIOR     | The <kbd>Page Up</kbd> key |
| `Prior`    | VK_PRIOR     | The <kbd>Page Up</kbd> key |
| `PgUp`     | VK_PRIOR     | The <kbd>Page Up</kbd> key |
| `PageDown` | VK_NEXT      | The <kbd>Page Down</kbd> key |
| `PgDown`   | VK_NEXT      | The <kbd>Page Down</kbd> key |
| `Next`     | VK_NEXT      | The <kbd>Page Down</kbd> key |
| `End`      | VK_END       | The <kbd>End</kbd> key |
| `Home`     | VK_HOME      | The <kbd>Home</kbd> key |
| `Left`     | VK_LEFT      | The <kbd>Left Arrow</kbd> key |
| `Up`       | VK_UP        | The <kbd>Up Arrow</kbd> key |
| `Right`    | VK_RIGHT     | The <kbd>Right Arrow</kbd> key |
| `Down`     | VK_DOWN      | The <kbd>Down Arrow</kbd> key |
| `Insert`   | VK_INSERT    | The <kbd>Insert</kbd> key |
| `Delete`   | VK_DELETE    | The <kbd>Delete</kbd> key |
| `Del`      | VK_DELETE    | The <kbd>Delete</kbd> key |
| `Separator` | VK_SEPARATOR | The <kbd>Separator</kbd> key |

## State keys

| Key name | Virtual key | Description |
| ----------------- | ----------- | ----------- |
| `NumLock`       | VK_NUMLOCK  | The <kbd>Num Lock</kbd> key |
| `ScrollLock`    | VK_SCROLL   | The <kbd>Scroll Lock</kbd> key |
| `Scroll`        | VK_SCROLL   | The <kbd>Scroll Lock</kbd> key |
| `CapsLock`      | VK_CAPITAL  | The <kbd>Caps Lock</kbd> key |
| `Capital`       | VK_CAPITAL  | The <kbd>Caps Lock</kbd> key |

## OEM keys

| Key name | Virtual key | Description |
| ----------------- | ----------- | ----------- |
| `KeypadEqual`   | VK_OEM_NEC_EQUAL  | The <kbd>Equals (=)</kbd> key on the numeric keypad (OEM-specific) |
| `Dictionary`    | VK_OEM_FJ_JISHO   | The Dictionary key (OEM-specific) |
| `Unregister`    | VK_OEM_FJ_MASSHOU | The Unregister Word key (OEM-specific) |
| `Register`      | VK_OEM_FJ_TOUROKU | The Register Word key (OEM-specific) |
| `LeftOyayubi`   | VK_OEM_FJ_LOYA    | The Left OYAYUBI key (OEM-specific) |
| `RightOyayubi`  | VK_OEM_FJ_ROYA    | The Right OYAYUBI key (OEM-specific) |
| `OemPlus`       | VK_OEM_PLUS       | For any country/region, the <kbd>Plus Sign (+)</kbd> key |
| `OemComma`      | VK_OEM_COMMA      | For any country/region, the <kbd>Comma (,)</kbd> key |
| `OemMinus`      | VK_OEM_MINUS      | For any country/region, the <kbd>Minus Sign (-)</kbd> key |
| `OemPeriod`     | VK_OEM_PERIOD     | For any country/region, the <kbd>Period (.)</kbd> key |
| `Oem1`          | VK_OEM_1          | Varies by keyboard |
| `Oem2`          | VK_OEM_2          | Varies by keyboard |
| `Oem3`          | VK_OEM_3          | Varies by keyboard |
| `Oem4`          | VK_OEM_4          | Varies by keyboard |
| `Oem5`          | VK_OEM_5          | Varies by keyboard |
| `Oem6`          | VK_OEM_6          | Varies by keyboard |
| `Oem7`          | VK_OEM_7          | Varies by keyboard |
| `Oem8`          | VK_OEM_8          | Varies by keyboard |
| `OemAX`         | VK_OEM_AX         | The <kbd>AX</kbd> key on a Japanese AX keyboard |
| `Oem102`        | VK_OEM_102        | Either the angle bracket key or the backslash key on the RT 102-key keyboard |

## Function keys

| Key name | Virtual key | Description |
| ----------------- | ----------- | ----------- |
| `F1`  | VK_F1   | The <kbd>F1</kbd> key |
| `F2`  | VK_F2   | The <kbd>F2</kbd> key |
| `F3`  | VK_F3   | The <kbd>F3</kbd> key |
| `F4`  | VK_F4   | The <kbd>F4</kbd> key |
| `F5`  | VK_F5   | The <kbd>F5</kbd> key |
| `F6`  | VK_F6   | The <kbd>F6</kbd> key |
| `F7`  | VK_F7   | The <kbd>F7</kbd> key |
| `F8`  | VK_F8   | The <kbd>F8</kbd> key |
| `F9`  | VK_F9   | The <kbd>F9</kbd> key |
| `F10` | VK_F10  | The <kbd>F10</kbd> key |
| `F11` | VK_F11  | The <kbd>F11</kbd> key |
| `F12` | VK_F12  | The <kbd>F12</kbd> key |
| `F13` | VK_F13  | The <kbd>F13</kbd> key |
| `F14` | VK_F14  | The <kbd>F14</kbd> key |
| `F15` | VK_F15  | The <kbd>F15</kbd> key |
| `F16` | VK_F16  | The <kbd>F16</kbd> key |
| `F17` | VK_F17  | The <kbd>F17</kbd> key |
| `F18` | VK_F18  | The <kbd>F18</kbd> key |
| `F19` | VK_F19  | The <kbd>F19</kbd> key |
| `F20` | VK_F20  | The <kbd>F20</kbd> key |
| `F21` | VK_F21  | The <kbd>F21</kbd> key |
| `F22` | VK_F22  | The <kbd>F22</kbd> key |
| `F23` | VK_F23  | The <kbd>F23</kbd> key |
| `F24` | VK_F24  | The <kbd>F24</kbd> key |

## Numeric keypad keys

| Key name | Virtual key | Description |
| ----------------- | ----------- | ----------- |
| `Numpad0`   | VK_NUMPAD0  | The <kbd>0</kbd> key on the numeric keypad |
| `Numpad1`   | VK_NUMPAD1  | The <kbd>1</kbd> key on the numeric keypad |
| `Numpad2`   | VK_NUMPAD2  | The <kbd>2</kbd> key on the numeric keypad |
| `Numpad3`   | VK_NUMPAD3  | The <kbd>3</kbd> key on the numeric keypad |
| `Numpad4`   | VK_NUMPAD4  | The <kbd>4</kbd> key on the numeric keypad |
| `Numpad5`   | VK_NUMPAD5  | The <kbd>5</kbd> key on the numeric keypad |
| `Numpad6`   | VK_NUMPAD6  | The <kbd>6</kbd> key on the numeric keypad |
| `Numpad7`   | VK_NUMPAD7  | The <kbd>7</kbd> key on the numeric keypad |
| `Numpad8`   | VK_NUMPAD8  | The <kbd>8</kbd> key on the numeric keypad |
| `Numpad9`   | VK_NUMPAD9  | The <kbd>9</kbd> key on the numeric keypad |
| `Multiply`  | VK_MULTIPLY | The <kbd>Multiply (*)</kbd> key on the numeric keypad |
| `Add`       | VK_ADD      | The <kbd>Add (+)</kbd> key on the numeric keypad |
| `Subtract`  | VK_SUBTRACT | The <kbd>Subtract (-)</kbd> key on the numeric keypad |
| `Decimal`   | VK_DECIMAL  | The <kbd>Decimal (.)</kbd> key on the numeric keypad |
| `Divide`    | VK_DIVIDE   | The <kbd>Divide (/)</kbd> key on the numeric keypad |

## Related articles

- [Keyboard filter](keyboardfilter.md)
