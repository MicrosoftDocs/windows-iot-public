---
title: UWF servicing screen saver
description: UWF servicing screen saver
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 869ccd86-08db-44ec-ac8e-938476e3a1da


ms.date: 05/02/2017
ms.topic: article


---
# UWF servicing screen saver

The default settings for the Unified Write Filter (UWF) servicing screen saver can be changed through the Windows registry to use custom text, title, font, and color settings.

The UWF servicing screen saver (UwfServicingScr.scr) is located in the \\Windows\\System32 folder.

> [!Important]
> When UWF is installed on your device, when you right-click on the **Desktop**, and then click **Personalize** &gt; **Screen Saver**, the UWF servicing screen saver will appear in the list of available screen savers in the **Screen Saver Settings** dialog box.

Do not select **UwfServicingScr** as the screen saver and then click **Preview**, as you will not be able to exit the UWF servicing screen saver by moving the mouse or pressing a key. The only way to exit the UWF servicing screen saver in this case is by pressing the Ctrl+Alt+Delete keys.

## Modify the default registry settings for the UWF servicing screen saver

1. To modify the default registry settings for the UWF servicing screen saver, from the example shown here, change the values in a text editor, and then save as a .reg file (for example, Overridescreensaver.reg).

   ```powershell
   Windows Registry Editor Version 5.00
   [HKEY_LOCAL_MACHINE\Software\Microsoft\Windows Embedded\ServicingScreenSaver]
   "ColorBackground"=dword:000000ff
   "ColorText"=dword:0000ff00
   "ColorProgress"=dword:00ff0000
   "ScreenSaverTitle"="Device"
   "ScreenSaverSubTitle"="Servicing device…"
   "HideScreenSaverText"=dword:00000000
   "HideScreenSaverProgress"=dword:00000000
   "Font"="Algerian"
   ```

1. On the device, open a command prompt as an administrator. For Windows Shell, to open a command prompt, do the following:
   1. In Windows Explorer, move to \\Windows\\System32, right-click **cmd.exe**, and then click **Run as Administrator**.
   1. Accept the UAC prompt.
1. To apply the custom registry settings for the screen saver to the device, type the following command:

   ```powershell
   regedit.exe /s overridescreensaver.reg
   ```

The next time the device enters UWF servicing mode, the UwfServicingScr.scr screen saver will use the custom settings.

## Related topics

[Service UWF-protected devices](service-uwf-protected-devices.md)

[Unified Write Filter](unified-write-filter.md)
