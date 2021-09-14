---
title: Layout Control
author: rsameser
ms.author: riameser
ms.date: 2/2/2021
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: Learn about the Layout Control Features of Windows 10 IoT Enterprise.
keywords: Branding, Layout Control, Start, Taskbar, Secondary Tiles
---
# Layout Control
In Windows 10 IoT Enterprise, organizations can deploy a [customized Start and Taskbar](https://docs.microsoft.com/windows/configuration/windows-10-start-layout-options-and-policies) configuration to their devices. We know how important it is for your devices to maintain your brand and customized user-experience.

## Configure Start Layout
A standard, customized [Start layout](https://docs.microsoft.com/windows/configuration/customize-and-export-start-layout) can be useful on devices that are common to multiple users and devices that are locked down for specialized purposes.

The easiest method for creating a [customized Start layout](https://docs.microsoft.com/windows/configuration/customize-and-export-start-layout) to apply to other Windows 10 devices is to set up the Start screen on a test computer and then export the layout.

After you export the layout, decide whether you want to apply a full Start layout or a partial Start layout.

When a full Start layout is applied, the users cannot pin, unpin, or uninstall apps from Start. Users can view and open all apps in the All Apps view, but they cannot pin any apps to Start.

When a [partial Start layout](https://docs.microsoft.com/windows/configuration/customize-and-export-start-layout#configure-a-partial-start-layout) is applied, the contents of the specified tile groups cannot be changed, but users can move those groups, and can also create and customize their own groups.

You can deploy the resulting .xml file to devices using one of the following methods:

* [Group Policy](https://docs.microsoft.com/windows/configuration/customize-windows-10-start-screens-by-using-group-policy)
* [Windows Configuration Designer provisioning package](https://docs.microsoft.com/windows/configuration/customize-windows-10-start-screens-by-using-provisioning-packages-and-icd)
* [Mobile device management (MDM)](https://docs.microsoft.com/windows/configuration/customize-windows-10-start-screens-by-using-mobile-device-management)

### Secondary Tiles
[Secondary tiles](https://docs.microsoft.com/windows/uwp/design/shell/tiles-and-notifications/secondary-tiles) allow users to pin specific content and deep links from your app onto their Start menu, providing easy future access to the content within your app.

By adding secondary tiles to your app, you help the user re-engage quickly and efficiently with your app, encouraging them to return more often, thanks to the easy access that secondary tiles provide.

![Screenshot of secondary tiles](media/secondarytiles.png)


## Configure Windows 10 taskbar
Configuring the [taskbar layout](https://docs.microsoft.com/windows/configuration/configure-windows-10-taskbar) allows an organization to pin useful apps and to remove apps that are pinned by default to provide a specified user experience.

The only aspect of the taskbar that can currently be configured by the layout modification XML file is the layout. You can also specify different taskbar configurations based on device locale and region. There is no limit on the number of apps that you can pin. You specify apps using the [Application User Model ID (AUMID)](https://go.microsoft.com/fwlink/p/?LinkId=614867) or Desktop Application Link Path (the local path to the application).

If you specify an app to be pinned that is not provisioned for the user on the computer, the pinned icon won't appear on the taskbar.

The order of apps in the XML file dictates the order of pinned apps on the taskbar from left to right, to the right of any existing apps pinned by the user.

To configure the taskbar:
1. Create the XML file.
* If you are also customizing the Start layout, use ```Export-StartLayout``` to create the XML, and then add the ```<CustomTaskbarLayoutCollection>``` section from [the following sample](https://docs.microsoft.com/windows/configuration/configure-windows-10-taskbar#sample-taskbar-configuration-added-to-start-layout-xml-file) to the file.
* If you are only configuring the taskbar, use [the following sample](https://docs.microsoft.com/windows/configuration/configure-windows-10-taskbar#sample-taskbar-configuration-xml-file) to create a layout modification XML file.

2. Edit and save the XML file. You can use [AUMID](https://go.microsoft.com/fwlink/p/?LinkId=614867) or Desktop Application Link Path to identify the apps to pin to the taskbar.
* Add ```xmlns:taskbar="http://schemas.microsoft.com/Start/2014/TaskbarLayout"``` to the first line of the file, before the closing >.
* Use ```<taskbar:UWA>``` and AUMID to pin Universal Windows Platform apps.
* Use ```<taskbar:DesktopApp>``` and Desktop Application Link Path to pin desktop applications.

3. Apply the layout modification XML file to devices using [Group Policy](https://docs.microsoft.com/windows/configuration/customize-windows-10-start-screens-by-using-group-policy) or a [provisioning package created in Windows Imaging and Configuration Designer (Windows ICD)](https://docs.microsoft.com/windows/configuration/customize-windows-10-start-screens-by-using-provisioning-packages-and-icd).

> [!IMPORTANT]
>
> If you use a provisioning package or import-startlayout to configure the taskbar, your configuration will be reapplied each time the explorer.exe process restarts. If your configuration pins an app and the user then unpins that app, the user's change will be overwritten the next time the configuration is applied. To apply a taskbar configuration that allows users to make changes that will persist, apply your configuration by using Group Policy.
>
> If you use Group Policy and your configuration only contains a taskbar layout, the default Windows tile layout will be applied and cannot be changed by users. If you use Group Policy and your configuration includes taskbar and a full Start layout, users can only make changes to the taskbar. If you use Group Policy and your configuration includes taskbar and a partial Start layout, users can make changes to the taskbar and to tile groups not defined in the partial Start layout.

### Tips for finding AUMID and Desktop Application Link Path
In the layout modification XML file, you will need to add entries for applications in the XML markup. In order to pin an application, you need either its AUMID or Desktop Application Link Path.

The easiest way to find this data for an application is to:

1. Pin the application to the Start menu on a reference or testing PC.
2. Open Windows PowerShell and run the ```Export-StartLayout``` cmdlet.
3. Open the generated XML file.
4. Look for an entry corresponding to the app you pinned.
5. Look for a property labeled ```AppUserModelID``` or ```DesktopApplicationLinkPath```.


## Additional Resources
* [Customize the Start screen on your test computer](https://docs.microsoft.com/windows/configuration/customize-and-export-start-layout#customize-the-start-screen-on-your-test-computer)
* [Export the Start layout](https://docs.microsoft.com/windows/configuration/customize-and-export-start-layout#export-the-start-layout)
* [Configure a partial Start layout](https://docs.microsoft.com/windows/configuration/customize-and-export-start-layout#configure-a-partial-start-layout)
* [Remove default apps](https://docs.microsoft.com/windows/configuration/configure-windows-10-taskbar#remove-default-apps)
* [Remove default apps and add your own](https://docs.microsoft.com/windows/configuration/configure-windows-10-taskbar#remove-default-apps-and-add-your-own)
* [Configure taskbar by country or region](https://docs.microsoft.com/windows/configuration/configure-windows-10-taskbar#configure-taskbar-by-country-or-region)
* [Layout Modification Template schema definition](https://docs.microsoft.com/windows/configuration/configure-windows-10-taskbar#layout-modification-template-schema-definition)
* [Secondary tile guidance](https://docs.microsoft.com/windows/uwp/design/shell/tiles-and-notifications/secondary-tiles-guidance)
* [Pin secondary tiles](https://docs.microsoft.com/windows/uwp/design/shell/tiles-and-notifications/secondary-tiles-pinning)
* [Add image for secondary Microsoft Edge tiles](https://docs.microsoft.com/windows/configuration/start-secondary-tiles)
