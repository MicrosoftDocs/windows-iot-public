---
title: Settings Page Visibility
author: rsameser
ms.author: riameser
ms.date: 1/31/2021
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: Learn about the Page Visibility Features of Windows 10 IoT Enterprise.
keywords: Branding, Settings Page Visibility
---

# Settings Page Policy: Page Visibility
[Page Visibility](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-settings#settings-pagevisibilitylist) is a feature that allows you to further customize the visibility of pages in the System Settings app.

## Configure the Page Visibility Policy
Added in Windows 10, version 1703, the page visibility policy can prevent specific pages in the System Settings app from being visible or accessible, or to do so for all pages except those specified.

The mode will be specified by the policy string beginning with either the string **showonly** or **hide**.

Pages are identified by a shortened version of their already [published URIs](https://docs.microsoft.com/windows/uwp/launch-resume/launch-settings-app#ms-settings-uri-scheme-reference), which is the URI minus the "ms-settings:" prefix. Multiple page identifiers are separated by semicolons.

*For example, if the URI for a settings page is "ms-settings:bluetooth", the page identifier used in the policy will be just "bluetooth".*  

* [Enable Page Visibility Policy](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-settings#settings-pagevisibilitylist)


## Additional Resources
* [Page Visibility List](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-settings#settings-pagevisibilitylist)
* [Policy CSP - Settings](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-settings)
* [Policy CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-configuration-service-provider)
* [ms-settings: URI scheme reference](https://docs.microsoft.com/windows/uwp/launch-resume/launch-settings-app#ms-settings-uri-scheme-reference)
