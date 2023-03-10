---
title: Screen Swipe Policy
author: TerryWarwick
ms.author: twarwick
ms.date: 03/09/2023
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: Learn about the Edge Swipe Policy Feature in Windows IoT Enterprise.
keywords: Lockdown, Edge Swipe
---
# Screen Swipe Policy
If your Windows IoT device has a touchscreen, users have the option to swipe from the edge of a screen to invoke a system user interface. Depending on the direction of the swipe, the action center, tablet mode or taskbar can appear.

## How to Enable/Disable Screen Swipe via Group Policy
One of the ways you can go about managing the screen edge swipe functionality in Windows IoT Enterprise is by using the Group Policy Editor.

The following steps outline how to enable/disable the policy:
1. Launch the Local Group Policy Editor for the Device
2. On the navigation pane, select **Computer Configuration** > **Administrative Templates** > **Windows Components** > **Edge UI**
3. Select **Edit Policy Setting**
4. Choose if you would like to **enable** or **disable** this policy.
5. For this change of policy to go into effect, restart the device.

> [!NOTE]
>
> By disabling this policy setting, users will not be able to invoke any system UI by swiping in from any screen edge.
>
> If you enable or do not configure this policy setting, users will be able to invoke system UI by swiping in from the screen edges.

## Verify Lockdown Policy
The easiest way to verify if the policy is in effect is to restart the explorer process or to reboot after the policy is applied. Try to swipe from the right edge of the screen and evaluate the behavior. The desired result is for Action Center to not be invoked by the swipe. You can also enter tablet mode and attempt to swipe from the top of the screen to rearrange, that functionality will also be disabled.

## Additional Resources
* [LockDown/AllowEdgeSwipe](/windows/client-management/mdm/policy-csp-lockdown#lockdown-allowedgeswipe)
