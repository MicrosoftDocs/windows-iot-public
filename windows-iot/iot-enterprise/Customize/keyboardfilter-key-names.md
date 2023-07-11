---
title: Keyboard Filter key names
description: Keyboard Filter key names
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 5f3772bb-fdd2-4816-9994-bd2523099400


ms.date: 05/02/2017
ms.topic: article


---
# Keyboard Filter key names

You can configure Keyboard Filter to block keys or key combinations. A key combination consists of one or more modifier keys, separated by a plus sign (+), and either a key name or a key scan code. In addition to the keys listed in the tables below, you can also use the predefined key combinations names as custom key combinations, but we recommend using the predefined key settings when enabling or disabling predefined key combinations.

The key names are grouped as follows:

* [Modifier keys](#modkey)
* [System keys](#syskey)
* [Cursor and math keys](#curkey)
* [State keys](#stakey)
* [OEM keys](#oemkey)
* [Function keys](#funkey)

## <a href="" id="modkey"></a>Modifier keys

You can use the modifier keys listed in the following table when you configure keyboard filter. Multiple modifiers must be separated by a plus sign (+). You can also configure Keyboard Filter to block any modifier key even if it’s not part of a key combination..

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>Modifier key name</th>
<th>Virtual key</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Ctrl</strong></p></td>
<td><p>VK_CONTROL</p></td>
<td><p>The Ctrl key</p></td>
</tr>
<tr class="even">
<td><p><strong>LCtrl</strong></p></td>
<td><p>VK_LCONTROL</p></td>
<td><p>The left Ctrl key</p></td>
</tr>
<tr class="odd">
<td><p><strong>RCtrl</strong></p></td>
<td><p>VK_RCONTROL</p></td>
<td><p>The right Ctrl key</p></td>
</tr>
<tr class="even">
<td><p><strong>Control</strong></p></td>
<td><p>VK_CONTROL</p></td>
<td><p>The Ctrl key</p></td>
</tr>
<tr class="odd">
<td><p><strong>LControl</strong></p></td>
<td><p>VK_LCONTROL</p></td>
<td><p>The left Ctrl key</p></td>
</tr>
<tr class="even">
<td><p><strong>RControl</strong></p></td>
<td><p>VK_RCONTROL</p></td>
<td><p>The right Ctrl key</p></td>
</tr>
<tr class="odd">
<td><p><strong>Alt</strong></p></td>
<td><p>VK_MENU</p></td>
<td><p>The Alt key</p></td>
</tr>
<tr class="even">
<td><p><strong>LAlt</strong></p></td>
<td><p>VK_LMENU</p></td>
<td><p>The left Alt key</p></td>
</tr>
<tr class="odd">
<td><p><strong>RAlt</strong></p></td>
<td><p>VK_RMENU</p></td>
<td><p>The right Alt key</p></td>
</tr>
<tr class="even">
<td><p><strong>Shift</strong></p></td>
<td><p>VK_SHIFT</p></td>
<td><p>The Shift key</p></td>
</tr>
<tr class="odd">
<td><p><strong>LShift</strong></p></td>
<td><p>VK_LSHIFT</p></td>
<td><p>The left Shift key</p></td>
</tr>
<tr class="even">
<td><p><strong>RShift</strong></p></td>
<td><p>VK_RSHIFT</p></td>
<td><p>The right Shift key</p></td>
</tr>
<tr class="odd">
<td><p><strong>Win</strong></p></td>
<td><p>VK_WIN</p></td>
<td><p>The Windows logo key</p></td>
</tr>
<tr class="even">
<td><p><strong>LWin</strong></p></td>
<td><p>VK_LWIN</p></td>
<td><p>The left Windows logo key</p></td>
</tr>
<tr class="odd">
<td><p><strong>RWin</strong></p></td>
<td><p>VK_RWIN</p></td>
<td><p>The right Windows logo key</p></td>
</tr>
<tr class="even">
<td><p><strong>Windows</strong></p></td>
<td><p>VK_WIN</p></td>
<td><p>The Windows logo key</p></td>
</tr>
<tr class="odd">
<td><p><strong>LWindows</strong></p></td>
<td><p>VK_LWIN</p></td>
<td><p>The left Windows logo key</p></td>
</tr>
<tr class="even">
<td><p><strong>RWindows</strong></p></td>
<td><p>VK_RWIN</p></td>
<td><p>The right Windows logo key</p></td>
</tr>
</tbody>
</table>

## <a href="" id="syskey"></a>System keys

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>Key name</th>
<th>Virtual key</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Backspace</strong></p></td>
<td><p>VK_BACK</p></td>
<td><p>The Backspace key</p></td>
</tr>
<tr class="even">
<td><p><strong>Back</strong></p></td>
<td><p>VK_BACK</p></td>
<td><p>The Backspace key</p></td>
</tr>
<tr class="odd">
<td><p><strong>Tab</strong></p></td>
<td><p>VK_TAB</p></td>
<td><p>The Tab key</p></td>
</tr>
<tr class="even">
<td><p><strong>Clear</strong></p></td>
<td><p>VK_CLEAR</p></td>
<td><p>The Clear key</p></td>
</tr>
<tr class="odd">
<td><p><strong>Enter</strong></p></td>
<td><p>VK_RETURN</p></td>
<td><p>The Enter key</p></td>
</tr>
<tr class="even">
<td><p><strong>Return</strong></p></td>
<td><p>VK_RETURN</p></td>
<td><p>The Enter key</p></td>
</tr>
<tr class="odd">
<td><p><strong>Pause</strong></p></td>
<td><p>VK_PAUSE</p></td>
<td><p>The Pause key</p></td>
</tr>
<tr class="even">
<td><p><strong>Esc</strong></p></td>
<td><p>VK_ESCAPE</p></td>
<td><p>The Esc key</p></td>
</tr>
<tr class="odd">
<td><p><strong>Escape</strong></p></td>
<td><p>VK_ESCAPE</p></td>
<td><p>The Esc key</p></td>
</tr>
<tr class="even">
<td><p><strong>Space</strong></p></td>
<td><p>VK_SPACE</p></td>
<td><p>The Spacebar</p></td>
</tr>
<tr class="odd">
<td><p><strong>Break</strong></p></td>
<td><p>VK_BREAK</p></td>
<td><p>The Break key</p></td>
</tr>
<tr class="even">
<td><p><strong>Select</strong></p></td>
<td><p>VK_SELECT</p></td>
<td><p>The Select key</p></td>
</tr>
<tr class="odd">
<td><p><strong>PrintScreen</strong></p></td>
<td><p>VK_PRINT</p></td>
<td><p>The Print Screen key</p></td>
</tr>
<tr class="even">
<td><p><strong>PrintScrn</strong></p></td>
<td><p>VK_PRINT</p></td>
<td><p>The Print Screen key</p></td>
</tr>
<tr class="odd">
<td><p><strong>Print</strong></p></td>
<td><p>VK_PRINT</p></td>
<td><p>The Print Screen key</p></td>
</tr>
<tr class="even">
<td><p><strong>Execute</strong></p></td>
<td><p>VK_EXECUTE</p></td>
<td><p>The Execute key</p></td>
</tr>
<tr class="odd">
<td><p><strong>Snapshot</strong></p></td>
<td><p>VK_SNAPSHOT</p></td>
<td><p>The Print Screen key</p></td>
</tr>
<tr class="even">
<td><p><strong>Help</strong></p></td>
<td><p>VK_HELP</p></td>
<td><p>The Help key</p></td>
</tr>
</tbody>
</table>

## <a href="" id="curkey"></a>Cursor and edit keys

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>Key name</th>
<th>Virtual key</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>PageUp</strong></p></td>
<td><p>VK_PRIOR</p></td>
<td><p>The Page Up key</p></td>
</tr>
<tr class="even">
<td><p><strong>Prior</strong></p></td>
<td><p>VK_PRIOR</p></td>
<td><p>The Page Up key</p></td>
</tr>
<tr class="odd">
<td><p><strong>PgUp</strong></p></td>
<td><p>VK_PRIOR</p></td>
<td><p>The Page Up key</p></td>
</tr>
<tr class="even">
<td><p><strong>PageDown</strong></p></td>
<td><p>VK_NEXT</p></td>
<td><p>The Page Down key</p></td>
</tr>
<tr class="odd">
<td><p><strong>PgDown</strong></p></td>
<td><p>VK_NEXT</p></td>
<td><p>The Page Down key</p></td>
</tr>
<tr class="even">
<td><p><strong>Next</strong></p></td>
<td><p>VK_NEXT</p></td>
<td><p>The Page Down key</p></td>
</tr>
<tr class="odd">
<td><p><strong>End</strong></p></td>
<td><p>VK_END</p></td>
<td><p>The End key</p></td>
</tr>
<tr class="even">
<td><p><strong>Home</strong></p></td>
<td><p>VK_HOME</p></td>
<td><p>The Home key</p></td>
</tr>
<tr class="odd">
<td><p><strong>Left</strong></p></td>
<td><p>VK_LEFT</p></td>
<td><p>The Left Arrow key</p></td>
</tr>
<tr class="even">
<td><p><strong>Up</strong></p></td>
<td><p>VK_UP</p></td>
<td><p>The Up Arrow key</p></td>
</tr>
<tr class="odd">
<td><p><strong>Right</strong></p></td>
<td><p>VK_RIGHT</p></td>
<td><p>The Right Arrow key</p></td>
</tr>
<tr class="even">
<td><p><strong>Down</strong></p></td>
<td><p>VK_DOWN</p></td>
<td><p>The Down Arrow key</p></td>
</tr>
<tr class="odd">
<td><p><strong>Insert</strong></p></td>
<td><p>VK_INSERT</p></td>
<td><p>The Insert key</p></td>
</tr>
<tr class="even">
<td><p><strong>Delete</strong></p></td>
<td><p>VK_DELETE</p></td>
<td><p>The Delete key</p></td>
</tr>
<tr class="odd">
<td><p><strong>Del</strong></p></td>
<td><p>VK_DELETE</p></td>
<td><p>The Delete key</p></td>
</tr>
<tr class="even">
<td><p><strong>Separator</strong></p></td>
<td><p>VK_SEPARATOR</p></td>
<td><p>The Separator key</p></td>
</tr>
</tbody>
</table>
 
## <a href="" id="stakey"></a>State keys

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>Key name</th>
<th>Virtual key</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>NumLock</strong></p></td>
<td><p>VK_NUMLOCK</p></td>
<td><p>The Num Lock key</p></td>
</tr>
<tr class="even">
<td><p><strong>ScrollLock</strong></p></td>
<td><p>VK_SCROLL</p></td>
<td><p>The Scroll Lock key</p></td>
</tr>
<tr class="odd">
<td><p><strong>Scroll</strong></p></td>
<td><p>VK_SCROLL</p></td>
<td><p>The Scroll Lock key</p></td>
</tr>
<tr class="even">
<td><p><strong>CapsLock</strong></p></td>
<td><p>VK_CAPITAL</p></td>
<td><p>The Caps Lock key</p></td>
</tr>
<tr class="odd">
<td><p><strong>Capital</strong></p></td>
<td><p>VK_CAPITAL</p></td>
<td><p>The Caps Lock key</p></td>
</tr>
</tbody>
</table>

## <a href="" id="oemkey"></a>OEM keys

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>Key Name</th>
<th>Virtual Key</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>KeypadEqual</strong></p></td>
<td><p>VK_OEM_NEC_EQUAL</p></td>
<td><p>The Equal Sign (=) key on the numeric keypad (OEM-specific)</p></td>
</tr>
<tr class="even">
<td><p><strong>Dictionary</strong></p></td>
<td><p>VK_OEM_FJ_JISHO</p></td>
<td><p>The Dictionary key (OEM-specific)</p></td>
</tr>
<tr class="odd">
<td><p><strong>Unregister</strong></p></td>
<td><p>VK_OEM_FJ_MASSHOU</p></td>
<td><p>The Unregister Word key (OEM-specific)</p></td>
</tr>
<tr class="even">
<td><p><strong>Register</strong></p></td>
<td><p>VK_OEM_FJ_TOUROKU</p></td>
<td><p>The Register Word key (OEM-specific)</p></td>
</tr>
<tr class="odd">
<td><p><strong>LeftOyayubi</strong></p></td>
<td><p>VK_OEM_FJ_LOYA</p></td>
<td><p>The Left OYAYUBI key (OEM-specific)</p></td>
</tr>
<tr class="even">
<td><p><strong>RightOyayubi</strong></p></td>
<td><p>VK_OEM_FJ_ROYA</p></td>
<td><p>The Right OYAYUBI key (OEM-specific)</p></td>
</tr>
<tr class="odd">
<td><p><strong>OemPlus</strong></p></td>
<td><p>VK_OEM_PLUS</p></td>
<td><p>For any country/region, the Plus Sign (+’) key</p></td>
</tr>
<tr class="even">
<td><p><strong>OemComma</strong></p></td>
<td><p>VK_OEM_COMMA</p></td>
<td><p>For any country/region, the Comma (,) key</p></td>
</tr>
<tr class="odd">
<td><p><strong>OemMinus</strong></p></td>
<td><p>VK_OEM_MINUS</p></td>
<td><p>For any country/region, the Minus Sign (-) key</p></td>
</tr>
<tr class="even">
<td><p><strong>OemPeriod</strong></p></td>
<td><p>VK_OEM_PERIOD</p></td>
<td><p>For any country/region, the Period (.) key</p></td>
</tr>
<tr class="odd">
<td><p><strong>Oem1</strong></p></td>
<td><p>VK_OEM_1</p></td>
<td><p>Varies by keyboard</p></td>
</tr>
<tr class="even">
<td><p><strong>Oem2</strong></p></td>
<td><p>VK_OEM_2</p></td>
<td><p>Varies by keyboard</p></td>
</tr>
<tr class="odd">
<td><p><strong>Oem3</strong></p></td>
<td><p>VK_OEM_3</p></td>
<td><p>Varies by keyboard</p></td>
</tr>
<tr class="even">
<td><p><strong>Oem4</strong></p></td>
<td><p>VK_OEM_4</p></td>
<td><p>Varies by keyboard</p></td>
</tr>
<tr class="odd">
<td><p><strong>Oem5</strong></p></td>
<td><p>VK_OEM_5</p></td>
<td><p>Varies by keyboard</p></td>
</tr>
<tr class="even">
<td><p><strong>Oem6</strong></p></td>
<td><p>VK_OEM_6</p></td>
<td><p>Varies by keyboard</p></td>
</tr>
<tr class="odd">
<td><p><strong>Oem7</strong></p></td>
<td><p>VK_OEM_7</p></td>
<td><p>Varies by keyboard</p></td>
</tr>
<tr class="even">
<td><p><strong>Oem8</strong></p></td>
<td><p>VK_OEM_8</p></td>
<td><p>Varies by keyboard</p></td>
</tr>
<tr class="odd">
<td><p><strong>OemAX</strong></p></td>
<td><p>VK_OEM_AX</p></td>
<td><p>The AX key on a Japanese AX keyboard</p></td>
</tr>
<tr class="even">
<td><p><strong>Oem102</strong></p></td>
<td><p>VK_OEM_102</p></td>
<td><p>Either the angle bracket key or the backslash key on the RT 102-key keyboard</p></td>
</tr>
</tbody>
</table>

## <a href="" id="funkey"></a>Function keys

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>Key name</th>
<th>Virtual key</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>F1</strong></p></td>
<td><p>VK_F1</p></td>
<td><p>The F1 key</p></td>
</tr>
<tr class="even">
<td><p><strong>F2</strong></p></td>
<td><p>VK_F2</p></td>
<td><p>The F2 key</p></td>
</tr>
<tr class="odd">
<td><p><strong>F3</strong></p></td>
<td><p>VK_F3</p></td>
<td><p>The F3 key</p></td>
</tr>
<tr class="even">
<td><p><strong>F4</strong></p></td>
<td><p>VK_F4</p></td>
<td><p>The F4 key</p></td>
</tr>
<tr class="odd">
<td><p><strong>F5</strong></p></td>
<td><p>VK_F5</p></td>
<td><p>The F5 key</p></td>
</tr>
<tr class="even">
<td><p><strong>F6</strong></p></td>
<td><p>VK_F6</p></td>
<td><p>The F6 key</p></td>
</tr>
<tr class="odd">
<td><p><strong>F7</strong></p></td>
<td><p>VK_F7</p></td>
<td><p>The F7 key</p></td>
</tr>
<tr class="even">
<td><p><strong>F8</strong></p></td>
<td><p>VK_F8</p></td>
<td><p>The F8 key</p></td>
</tr>
<tr class="odd">
<td><p><strong>F9</strong></p></td>
<td><p>VK_F9</p></td>
<td><p>The F9 key</p></td>
</tr>
<tr class="even">
<td><p><strong>F10</strong></p></td>
<td><p>VK_F10</p></td>
<td><p>The F10 key</p></td>
</tr>
<tr class="odd">
<td><p><strong>F11</strong></p></td>
<td><p>VK_F11</p></td>
<td><p>The F11 key</p></td>
</tr>
<tr class="even">
<td><p><strong>F12</strong></p></td>
<td><p>VK_F12</p></td>
<td><p>The F12 key</p></td>
</tr>
<tr class="odd">
<td><p><strong>F13</strong></p></td>
<td><p>VK_F13</p></td>
<td><p>The F13 key</p></td>
</tr>
<tr class="even">
<td><p><strong>F14</strong></p></td>
<td><p>VK_F14</p></td>
<td><p>The F14 key</p></td>
</tr>
<tr class="odd">
<td><p><strong>F15</strong></p></td>
<td><p>VK_F15</p></td>
<td><p>The F15 key</p></td>
</tr>
<tr class="even">
<td><p><strong>F16</strong></p></td>
<td><p>VK_F16</p></td>
<td><p>The F16 key</p></td>
</tr>
<tr class="odd">
<td><p><strong>F17</strong></p></td>
<td><p>VK_F17</p></td>
<td><p>The F17 key</p></td>
</tr>
<tr class="even">
<td><p><strong>F18</strong></p></td>
<td><p>VK_F18</p></td>
<td><p>The F18 key</p></td>
</tr>
<tr class="odd">
<td><p><strong>F19</strong></p></td>
<td><p>VK_F19</p></td>
<td><p>The F19 key</p></td>
</tr>
<tr class="even">
<td><p><strong>F20</strong></p></td>
<td><p>VK_F20</p></td>
<td><p>The F20 key</p></td>
</tr>
<tr class="odd">
<td><p><strong>F21</strong></p></td>
<td><p>VK_F21</p></td>
<td><p>The F21 key</p></td>
</tr>
<tr class="even">
<td><p><strong>F22</strong></p></td>
<td><p>VK_F22</p></td>
<td><p>The F22 key</p></td>
</tr>
<tr class="odd">
<td><p><strong>F23</strong></p></td>
<td><p>VK_F23</p></td>
<td><p>The F23 key</p></td>
</tr>
<tr class="even">
<td><p><strong>F24</strong></p></td>
<td><p>VK_F24</p></td>
<td><p>The F24 key</p></td>
</tr>
</tbody>
</table>

## Numeric keypad keys

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>Key name</th>
<th>Virtual key</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Numpad0</strong></p></td>
<td><p>VK_NUMPAD0</p></td>
<td><p>The 0 key on the numeric keypad</p></td>
</tr>
<tr class="even">
<td><p><strong>Numpad1</strong></p></td>
<td><p>VK_NUMPAD1</p></td>
<td><p>The 1 key on the numeric keypad</p></td>
</tr>
<tr class="odd">
<td><p><strong>Numpad2</strong></p></td>
<td><p>VK_NUMPAD2</p></td>
<td><p>The 2 key on the numeric keypad</p></td>
</tr>
<tr class="even">
<td><p><strong>Numpad3</strong></p></td>
<td><p>VK_NUMPAD3</p></td>
<td><p>The 3 key on the numeric keypad</p></td>
</tr>
<tr class="odd">
<td><p><strong>Numpad4</strong></p></td>
<td><p>VK_NUMPAD4</p></td>
<td><p>The 4 key on the numeric keypad</p></td>
</tr>
<tr class="even">
<td><p><strong>Numpad5</strong></p></td>
<td><p>VK_NUMPAD5</p></td>
<td><p>The 5 key on the numeric keypad</p></td>
</tr>
<tr class="odd">
<td><p><strong>Numpad6</strong></p></td>
<td><p>VK_NUMPAD6</p></td>
<td><p>The 6 key on the numeric keypad</p></td>
</tr>
<tr class="even">
<td><p><strong>Numpad7</strong></p></td>
<td><p>VK_NUMPAD7</p></td>
<td><p>The 7 key on the numeric keypad</p></td>
</tr>
<tr class="odd">
<td><p><strong>Numpad8</strong></p></td>
<td><p>VK_NUMPAD8</p></td>
<td><p>The 8 key on the numeric keypad</p></td>
</tr>
<tr class="even">
<td><p><strong>Numpad9</strong></p></td>
<td><p>VK_NUMPAD9</p></td>
<td><p>The 9 key on the numeric keypad</p></td>
</tr>
<tr class="odd">
<td><p><strong>Multiply</strong></p></td>
<td><p>VK_MULTIPLY</p></td>
<td><p>The Multiply (*) key on the numeric keypad</p></td>
</tr>
<tr class="even">
<td><p><strong>Add</strong></p></td>
<td><p>VK_ADD</p></td>
<td><p>The Add (+) key on the numeric keypad</p></td>
</tr>
<tr class="odd">
<td><p><strong>Subtract</strong></p></td>
<td><p>VK_SUBTRACT</p></td>
<td><p>The Subtract (-) key on the numeric keypad</p></td>
</tr>
<tr class="even">
<td><p><strong>Decimal</strong></p></td>
<td><p>VK_DECIMAL</p></td>
<td><p>The Decimal (.) key on the numeric keypad</p></td>
</tr>
<tr class="odd">
<td><p><strong>Divide</strong></p></td>
<td><p>VK_DIVIDE</p></td>
<td><p>The Divide (/) key on the numeric keypad</p></td>
</tr>
</tbody>
</table>

## Related topics

[Keyboard filter](keyboardfilter.md)
