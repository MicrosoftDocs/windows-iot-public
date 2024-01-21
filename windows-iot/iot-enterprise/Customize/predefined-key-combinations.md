---
title: Predefined key combinations
description: Predefined key combinations
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 9fc86f03-6d9e-4899-a4b7-fa8ad7835c65
author: TerryWarwick
ms.author: twarwick
ms.service: windows-iot
ms.subservice: iot
ms.date: 10/17/2017
ms.topic: article


---
# Predefined key combinations

This topic lists a set of key combinations that are predefined by a keyboard filter.  You can list the value of the WEKF_PredefinedKey.Id to get a complete list of key combinations defined by a keyboard filter.

You can use the values in the WEKF_PredefinedKey.Id column to configure the Windows Management Instrumentation (WMI) class [WEKF_PredefinedKey](wekf-predefinedkey.md).

## Accessibility keys

The following table contains predefined key combinations for accessibility:

| Key combination                      | WEKF_PredefinedKey.Id     | Blocked behavior            |
|:-------------------------------------|:--------------------------|:----------------------------|
| Left Alt + Left Shift + Print Screen | **LShift+LAlt+PrintScrn** | Open High Contrast.         |
| Left Alt + Left Shift + Num Lock     | **LShift+LAlt+NumLock**   | Open Mouse Keys.            |
| Windows logo key + U                 | **Win+U**                 | Open Ease of Access Center. |

## Application keys

The following table contains predefined key combinations for controlling application state:

| Key combination       | WEKF_PredefinedKey.Id | Blocked behavior   |
|:----------------------|:----------------------|:-------------------|
| Alt + F4              | **Alt+F4**            | Close application. |
| Ctrl + F4             | **Ctrl+F4**           | Close window.      |
| Windows logo key + F1 | **Win+F1**            | Open Windows Help. |

## Shell keys

The following table contains predefined key combinations for general UI control:

| Key combination                        | WEKF_PredefinedKey.Id | Blocked behavior                                                                                                                     |
|:---------------------------------------|:----------------------|:-------------------------------------------------------------------------------------------------------------------------------------|
| Alt + Spacebar                         | **Alt+Space**         | Open shortcut menu for the active window.                                                                                            |
| Ctrl + Esc                             | **Ctrl+Esc**          | Open the Start screen.                                                                                                               |
| Ctrl + Windows logo key + F            | **Ctrl+Win+F**        | Open Find Computers.                                                                                                                 |
| Windows logo key + Break               | **Win+Break**         | Open System dialog box.                                                                                                              |
| Windows logo key + E                   | **Win+E**             | Open Windows Explorer.                                                                                                               |
| Windows + F                            | **Win+F**             | Open Search.                                                                                                                         |
| Windows logo key + P                   | **Win+P**             | Cycle through Presentation Mode. Also blocks the Windows logo key + Shift + P and the Windows logo key + Ctrl + P key combinations.  |
| Windows logo key + R                   | **Win+R**             | Open Run dialog box.                                                                                                                 |
| Alt + Tab                              | **Alt+Tab**           | Switch task. Also blocks the Alt + Shift + Tab key combination.                                                                      |
| Ctrl + Tab                             | **Ctrl+Tab**          | Switch window.                                                                                                                       |
| Windows logo key + Tab                 | **Win+Tab**           | Cycle through Microsoft Store apps. Also blocks the Windows logo key + Ctrl + Tab and Windows logo key + Shift + Tab key combinations. |
| Windows logo key + D                   | **Win+D**             | Show desktop.                                                                                                                        |
| Windows logo key + M                   | **Win+M**             | Minimize all windows.                                                                                                                |
| Windows logo key + Home                | **Win+Home**          | Minimize or restore all inactive windows.                                                                                            |
| Windows logo key + T                   | **Win+T**             | Set focus on taskbar and cycle through programs.                                                                                     |
| Windows logo key + B                   | **Win+B**             | Set focus in the notification area.                                                                                                  |
| Windows logo key + Minus Sign          | **Win+-**             | Zoom out.                                                                                                                            |
| Windows logo key + Plus Sign           | **Win++**             | Zoom in.                                                                                                                             |
| Windows logo key + Esc                 | **Win+Esc**           | Close Magnifier application.                                                                                                         |
| Windows logo key + Up Arrow            | **Win+Up**            | Maximize the active window.                                                                                                          |
| Windows logo key + Down Arrow          | **Win+Down**          | Minimize the active window.                                                                                                          |
| Windows logo key + Left Arrow          | **Win+Left**          | Snap the active window to the left half of screen.                                                                                   |
| Windows logo key + Right Arrow         | **Win+Right**         | Snap the active window to the right half of screen.                                                                                  |
| Windows logo key + Shift + Up Arrow    | **Win+Shift+Up**      | Maximize the active window vertically.                                                                                               |
| Windows logo key + Shift + Down Arrow  | **Win+Shift+Down**    | Minimize the active window.                                                                                                          |
| Windows logo key + Shift + Left Arrow  | **Win+Shift+Left**    | Move the active window to left monitor.                                                                                              |
| Windows logo key + Shift + Right Arrow | **Win+Shift+Right**   | Move the active window to right monitor.                                                                                             |
| Windows logo key + Spacebar            | **Win+Space**         | Switch layout.                                                                                                                       |
| Windows logo key + O                   | **Win+O**             | Lock device orientation.                                                                                                             |
| Windows logo key + Page Up             | **Win+PageUp**        | Move a Microsoft Store app to the left monitor.                                                                                        |
| Windows logo key + Page Down           | **Win+PageDown**      | Move a Microsoft Store app to right monitor.                                                                                           |
| Windows logo key + Period              | **Win+.**             | Snap the current screen to the left or right gutter. Also blocks the Windows logo key + Shift + Period key combination.              |
| Windows logo key + C                   | **Win+C**             | Activate Cortana in listening mode (after user has enabled the shortcut through the UI).                                                                                                                         |
| Windows logo key + I                   | **Win+I**             | Open Settings charm.                                                                                                                 |
| Windows logo key + K                   | **Win+K**             | Open Connect charm.                                                                                                                  |
| Windows logo key + H                   | **Win+H**             | Start dictation.                                                                                                                  |
| Windows logo key + Q                   | **Win+Q**             | Open Search charm.                                                                                                                   |
| Windows logo key + W                   | **Win+W**             | Open Windows Ink workspace.                                                                                                         |
| Windows logo key + Z                   | **Win+Z**             | Open app bar.                                                                                                                        |
| Windows logo key + /                   | **Win+/**             | Open input method editor (IME).                                                                                                      |
| Windows logo key + J                   | **Win+J**             | Swap between snapped and filled applications.                                                                                        |
| Windows logo key + Comma               | **Win+,**             | Peek at the desktop.                                                                                                                 |
| Windows logo key + V                   | **Win+V**             | Cycle through toasts in reverse order.                                                                                               |

## Modifier keys

The following table contains predefined key combinations for modifier keys (such as Shift and Ctrl):

| Key combination  | WEKF_PredefinedKey.Id | Blocked key            |
|:-----------------|:----------------------|:-----------------------|
| Alt              | **Alt**               | Both Alt keys          |
| Application      | **Application**       | Application key        |
| Ctrl             | **Ctrl**              | Both Ctrl keys         |
| Shift            | **Shift**             | Both Shift keys        |
| Windows logo key | **Windows**           | Both Windows logo keys |

## Security keys

The following table contains predefined key combinations for OS security:

| Key combination        | WEKF_PredefinedKey.Id | Blocked behavior                  |
|:-----------------------|:----------------------|:----------------------------------|
| Ctrl + Alt + Delete    | **Ctrl+Alt+Del**      | Open the Windows Security screen. |
| Ctrl + Shift + Esc     | **Shift+Ctrl+Esc**    | Open Task Manager.                |
| Windows logo key + L   | **Win+L**             | Lock the device.                  |

## Extended shell keys

The following table contains predefined key combinations for extended shell functions (such as automatically opening certain apps):

| Key combination     | WEKF_PredefinedKey.Id | Blocked key             |
|:--------------------|:----------------------|:------------------------|
| LaunchMail          | **LaunchMail**        | Start Mail key          |
| LaunchMediaSelect   | **LaunchMediaSelect** | Select Media key        |
| LaunchApp1          | **LaunchApp1**        | Start Application 1 key |
| LaunchApp2          | **LaunchApp2**        | Start Application 2 key |

## Browser keys

The following table contains predefined key combinations for controlling the browser:

| Key combination  | WEKF_PredefinedKey.Id | Blocked key                |
|:-----------------|:----------------------|:---------------------------|
| BrowserBack      | **BrowserBack**       | Browser Back key           |
| BrowserForward   | **BrowserForward**    | Browser Forward key        |
| BrowserRefresh   | **BrowserRefresh**    | Browser Refresh key        |
| BrowserStop      | **BrowserStop**       | Browser Stop key           |
| BrowserSearch    | **BrowserSearch**     | Browser Search key         |
| BrowserFavorites | **BrowserFavorites**  | Browser Favorites key      |
| BrowserHome      | **BrowserHome**       | Browser Start and Home key |

## Media keys

The following table contains predefined key combinations for controlling media playback:

| Key combination | WEKF_PredefinedKey.Id | Blocked key          |
|:----------------|:----------------------|:---------------------|
| VolumeMute      | **VolumeMute**        | Volume Mute key      |
| VolumeDown      | **VolumeDown**        | Volume Down key      |
| VolumeUp        | **VolumeUp**          | Volume Up key        |
| MediaNext       | **MediaNext**         | Next Track key       |
| MediaPrev       | **MediaPrev**         | Previous Track key   |
| MediaStop       | **MediaStop**         | Stop Media key       |
| MediaPlayPause  | **MediaPlayPause**    | Play/Pause Media key |

## Microsoft Surface keyboard keys

The following table contains predefined key combinations for Microsoft Surface devices:

| Key combination               | WEKF_PredefinedKey.Id | Blocked key  |
|:------------------------------|:----------------------|:-------------|
| Left Alt + Windows logo key   | **AltWin**            | Share key    |
| Left Ctrl + Windows logo key  | **CtrlWin**           | Devices key  |
| Left Shift + Windows logo key | **ShiftWin**          | Search key   |
| F21                           | **F21**               | Settings key |

## Related topics

[Keyboard filter](keyboardfilter.md)
