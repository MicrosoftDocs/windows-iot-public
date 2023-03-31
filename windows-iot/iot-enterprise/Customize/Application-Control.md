---
title: Application Control
author: TerryWarwick
ms.author: twarwick
ms.date: 03/09/2023
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: Learn about Application Control features, such as Windows Defender Application Control (WDAC) and AppLocker, in Windows IoT Enterprise.
keywords: Lockdown, AppLocker, Windows Defender
---

# Application Control

Application control is a crucial scenario that enables an organization to create a lockdown experience. Windows IoT Enterprise, includes two technologies, [Windows Defender Application Control (WDAC) and AppLocker](/windows/security/threat-protection/windows-defender-application-control/wdac-and-applocker-overview), which can be used for application control to meet your organization's specific scenarios and requirements.

> [!NOTE]
> When it comes to [choosing between WDAC or AppLocker](/windows/security/threat-protection/windows-defender-application-control/wdac-and-applocker-overview#choose-when-to-use-wdac-or-applocker) it is generally recommended that customers who are able to implement application control using WDAC rather than AppLocker, do so. WDAC is undergoing continual improvements and will be getting added support from Microsoft management platforms. Although AppLocker will continue to receive security fixes, it will not undergo new feature improvements.

## Windows Defender Application Control (WDAC)

WDAC was introduced with Windows 10 and allows organizations to control which drivers and applications are allowed to run on their Windows devices. WDAC is designed as a security feature under the [servicing criteria](https://www.microsoft.com/msrc/windows-security-servicing-criteria) defined by the Microsoft Security Response Center (MSRC). To learn more about if WDAC can work for your organization, check out the following [documentation](/windows/security/threat-protection/windows-defender-application-control/windows-defender-application-control-deployment-guide).

## AppLocker

[AppLocker](/windows/security/threat-protection/windows-defender-application-control/applocker/what-is-applocker) advances the app control features and functionality of Software Restriction Policies. AppLocker contains new capabilities and extensions that allow you to create rules to allow or deny apps from running based on unique identities of files and to specify which users or groups can run those apps. Since AppLocker rules specify which apps are allowed to run on the device, you can leverage AppLocker to create a [Windows IoT kiosk](/windows/configuration/lock-down-windows-10-applocker) that runs multiple apps. AppLocker is ideal for organizations that currently use Group Policy to manage their PCs. To learn more about if AppLocker can work for your organization, check out the following [documentation](/windows/security/threat-protection/windows-defender-application-control/applocker/applocker-overview).

## Additional Resources

* [WDAC and AppLocker feature availability](/windows/security/threat-protection/windows-defender-application-control/feature-availability)
