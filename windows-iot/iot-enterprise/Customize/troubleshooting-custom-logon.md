---
title: Troubleshooting Custom Logon
description: Troubleshooting Custom Logon
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 5763E187-D09E-415D-B73C-BDD6BAB67E04


ms.date: 05/02/2017
ms.topic: article


---
# Troubleshooting Custom Logon

This section highlights some common issues that you may encounter when using Custom Logon.

## When automatic sign-in is enabled, the device asks for a password when resuming from sleep or hibernate

This can occur when your device is configured to require a password when waking up from a sleep state.

### To disable password protection on wake up

1. If you have write filters enabled on your device, perform the following steps to disable them so that you can save setting changes:

   1. At an administrator command prompt, type the following command:

      ```cmd
      uwfmgr.exe filter disable
      ```
   1. To restart the device, type the following command:

      ```cmd
      uwfmgr.exe restart
      ```

1. In **Contol Panel**, search for **Power Options** , and then click the Power Options heading.

1. Under the **Power Options** heading, click **Require a password on wakeup**.

1. On the **Define power buttons and turn on password protection** page, under **Password protection on wakeup**, select **Don’t require a password**.

1. If you disabled write filters, perform the following steps to enable them again:

   1. At an administrator command prompt, type the following command:

      ```cmd
      uwfmgr.exe filter enable
      ```
   1. To restart the device, type the following command:

      ```cmd
      uwfmgr.exe restart
      ```

## The device displays a black screen during setup

Set the **HideAutoLogonUI** and **AnimationDisabled** settings to **0** (zero). The device will then display a default screen during setup.

## The device displays a black screen when Ctrl+Alt+Del is pressed

**HideAutoLogonUI** and**ForceAutoLogon** have known issues when used together. To avoid a black screen, we recommend you use Keyboard Filter to block this key combination.

## The device displays a black screen when Windows key + L is used to lock the device

**HideAutoLogonUI** and **ForceAutoLogon** have known issues when used together. To avoid a black screen, we recommend you use Keyboard Filter to block this key combination.

### The device displays a black screen when Notepad is opened, any characters are typed and the current user signs out, or the device is rebooted, or the device is shut down

**HideAutoLogonUI** and **ForceAutoLogon** have known issues when used together. To avoid a black screen, we recommend you disable the Blocked Shutdown Resolver Screen (BSDR).

> [!Warning]
> When the BSDR screen is disabled, restarting or shutting down the device causes the OS to immediately force close any open applications that are blocking system shutdown. No UI is displayed, and users are not given a chance to cancel the shutdown process. This can result in lost data if any open applications have unsaved data.

## The device displays a black screen when the device is suspended and then resumed

**HideAutoLogonUI** and **ForceAutoLogon** have known issues when used together. To avoid a black screen, we recommend you disable the password protection on wakeup.

### To disable password protection on wakeup

1. In **Control Panel**, click **Power Options**.

1. In the **Power Options** item, click **Require a password on wakeup**.

1. On the **Define power buttons and turn on password protection** page, under **Password protection on wakeup**, select **Don’t require a password**.

### The device displays a black screen when a password expiration screen is displayed

**HideAutoLogonUI** has a known issue. To avoid a black screen, we recommend you set the password to never expire.

### To set a password to never expire on an individual user account

1. On your device, open a command prompt with administrator privileges.

1. Type the following, replacing *&lt;accountname&gt;* with the name of the account you want to remove the password expiration from.

   ```cmd
   net accounts <accountname> /expires:never
   ```

### To set passwords to never expire on all user accounts

1. On your device, open a command prompt with administrator privileges.

1. Type the following

   ```cmd
   net accounts /MaxPWAge:unlimited
   ```

## Related topics

[Custom Logon](custom-logon.md)

[Complementary features to Custom Logon](complementary-features-to-custom-logon.md)
