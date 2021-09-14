---
title: Keyboard Filter
author: rsameser
ms.author: riameser
ms.date: 1/31/2021
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: Learn about the Keyboard Filter Feature in Windows 10 IoT Enterprise.
keywords: Lockdown, Keyboard Filter
---

# Keyboard Filter
If your device is being use for a dedicated purpose, it may make sense to ensure that key combinations like 'Ctrl+Alt+Delete' do not alter the operation of the device by locking the screen or using Task Manager to close a running application. Windows 10 IoT Enterprise provides a feature called [Keyboard Filter](https://docs.microsoft.com/windows-hardware/customize/enterprise/keyboardfilter#:~:text=Keyboard%20Filter.%20You%20can%20use%20Keyboard%20Filter%20to,using%20Task%20Manager%20to%20close%20a%20running%20application.) that allows you to suppress undesirable key presses or key combinations.

## Keyboard Filter Features
Keyboard Filter has the following features:
* It supports hardware keyboards, the standard Windows on-screen keyboard, and the touch keyboard (TabTip.exe).
* It also suppresses key combinations even when they come from multiple keyboards.
    *For example, if a user presses the Ctrl key and the Alt key on a hardware keyboard, while at the same time pressing Delete on a software keyboard, Keyboard Filter can still detect and suppress the Ctrl+Alt+Delete functionality.*
* Supports numeric keypads and keys designed to access media player and browser functionality.
* Can configure a key to breakout of a locked down user session to return to the Welcome screen.
* Automatically handles dynamic layout changes.
* Can be enabled or disabled for administrator accounts.
* Can force disabling of Ease of Access functionality.
* Can block physical hardware keys.
* Supports x86 and x64 architectures.

## Turn on Keyboard Filter
There are multiple ways to turn on Keyboard Filter:
* [Control Panel](https://docs.microsoft.com/windows-hardware/customize/enterprise/keyboardfilter#turn-on-keyboard-filter-by-using-control-panel)
* [Unattend](https://docs.microsoft.com/windows-hardware/customize/enterprise/keyboardfilter#configure-keyboard-using-unattend)
* [Windows Configuration Designer](https://docs.microsoft.com/windows-hardware/customize/enterprise/keyboardfilter#turn-on-and-configure-keyboard-filter-using-windows-configuration-designer)
* [DISM](https://docs.microsoft.com/windows-hardware/customize/enterprise/keyboardfilter#turn-on-and-configure-keyboard-filter-by-using-dism)

> [!NOTE]
>
> Turning on an off Keyboard Filter requires that you restart your device. Keyboard Filter is automatically enabled after the restart.

## Additional Resources
* [Keyboard Filter](https://docs.microsoft.com/windows-hardware/customize/enterprise/keyboardfilter#turn-on-keyboard-filter)
* [Predefined Key Combinations](https://docs.microsoft.com/windows-hardware/customize/enterprise/predefined-key-combinations)
* [Keyboard Filter WMI provider reference](https://docs.microsoft.com/windows-hardware/customize/enterprise/keyboardfilter-wmi-provider-reference)
* [Windows PowerShell script samples for Keyboard Filter](https://docs.microsoft.com/windows-hardware/customize/enterprise/keyboardfilter-powershell-script-samples)
