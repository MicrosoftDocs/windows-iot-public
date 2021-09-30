---
title: Guidance on disabling system services on Windows IoT Enterprise
author: rsameser
ms.author: riameser
ms.date: 9/28/2021
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: Security guidelines for disabling services in Windows IoT Enterprise
keywords: IoT Enterprise, Security, services
---
# Guidance on disabling system services on Windows IoT Enterprise

>Applies to: Windows 10 IoT Enterprise, Windows 11 IoT Enterprise

The Windows operating system includes many system services that provide important functionality. Different services have different default startup policies: some are started by default (automatic), some when needed (manual), and some are disabled by default and must be explicitly enabled before they can run. These defaults were chosen carefully for each service to balance performance, functionality, and security for typical customers.

However, some IoT customers may prefer a more security-focused balance for their Windows IoT devices, one that reduces their attack surface to the absolute minimum, and may therefore wish to fully disable all services that are not needed in their specific environments. For those customers, Microsoft&reg; is providing the accompanying guidance regarding which services can safely be disabled for this purpose.

The guidance is only for Windows IoT Enterprise customers. Each service on the system is categorized as follows:

- **Should Disable:** A security-focused enterprise will most likely prefer to disable this service and forego its functionality (see additional details below).
- **OK to Disable:** This service provides functionality that is useful to some but not all enterprises, and security-focused enterprises that don't use it can safely disable it.
- **Do Not Disable:** Disabling this service will impact essential functionality or prevent specific roles or features from functioning correctly. Therefore it should not be disabled.
- **(No guidance):** The impact of disabling these services has not been fully evaluated. Therefore, the default configuration of these services should not be changed.

Customers can configure their Windows IoT devices to disable selected services using the Security Templates in their Group Policies or using PowerShell automation. In some cases, the guidance includes specific Group Policy settings that disable the service's functionality directly, as an alternative to disabling the service itself.

Microsoft recommends that customers disable the following services and their respective scheduled tasks on Windows IoT Enterprise:

Services:
1. Xbox Live Auth Manager
2. Xbox Live Game Save

Scheduled tasks:
1. \Microsoft\XblGameSave\XblGameSaveTask
2. \Microsoft\XblGameSave\XblGameSaveTaskLogon


### Disabling services not installed by default

Microsoft recommends against applying policies to disable services that are not installed by default.
- The service is usually needed if the feature is installed. Installing the service or the feature requires administrative rights. Disallow the feature installation, not the service startup.
- Blocking the Microsoft Windows service doesn't stop an admin (or non-admin in some cases) from installing a similar third-party equivalent, perhaps one with a higher security risk.
- A baseline or benchmark that disables a non-default Windows service (for example, W3SVC) will give some auditors the mistaken impression that the technology (for example, IIS) is inherently insecure and should never be used.
- If the feature (and service) is never installed, this just adds unnecessary bulk to the baseline and to verification work.

For all system services listed in this document, the two tables that follow offer an explanation of columns and Microsoft recommendations for enabling and disabling system services in Windows IoT Enterprise.

### Explanation of columns

| Name | Description |
|--|--|
| **Service name** | Key (internal) name of the service |
| **Description** | The service's description, from sc.exe description. |
| **Installation** | *Always installed*: Service is installed on Windows IoT Enterprise. |
| **Startup type** | Service Startup type on Windows IoT Enterprise |
| **Recommendation** | Microsoft recommendation/advice about disabling this service on Windows IoT Enterprise in a typical, well-managed deployment. |
| **Comments** | Additional explanation |

### Explanation of Microsoft recommendations

| Name | Description |
|--|--|
| **Do not disable** | This service should not be disabled |
| **OK to disable** | This service can be disabled if the feature it supports is not being used. |
| **Already disabled** | This service is disabled by default; no need to enforce with policy |
| **Should be disabled** | This service should never be enabled on a well-managed enterprise system. |

The following tables offer Microsoft guidance on disabling system services on Windows IoT Enterprise:

## ActiveX Installer (AxInstSV)

| Name | Description |
|--|--|
| **Service name** | AxInstSV |
| **Description** | Provides User Account Control validation for the installation of ActiveX controls from the Internet and enables management of ActiveX control installation based on Group Policy settings. This service is started on demand and if disabled the installation of ActiveX controls will behave according to default browser settings. |
| **Installation** | Always installed |
| **Startup type** | Manual |
| **Recommendation** | OK to disable |
| **Comments** | OK to disable if feature not needed |

## AllJoyn Router Service

| Name | Description |
|--|--|
| **Service name** | AJRouter |
| **Description** | Routes AllJoyn messages for the local AllJoyn clients. If this service is stopped the AllJoyn clients that do not have their own bundled routers will be unable to run. |
| **Installation** | Always installed |
| **Startup type** | Manual |
| **Recommendation** | OK to disable |
| **Comments** | None |

## App Readiness

| Name | Description |
|--|--|
| **Service name** | AppReadiness |
| **Description** | Gets apps ready for use the first time a user signs in to this device and when adding new apps. |
| **Installation** | Always installed |
| **Startup type** | Manual |
| **Recommendation** | Do not disable |
| **Comments** | None |

## Application Identity

| Name | Description |
|--|--|
| **Service name** | AppIDSvc |
| **Description** | Determines and verifies the identity of an application. Disabling this service will prevent AppLocker from being enforced. |
| **Installation** | Always installed |
| **Startup type** | Manual |
| **Recommendation** | Do not disable |
| **Comments** | None |

## Application Information

| Name | Description |
|--|--|
| **Service name** | Appinfo |
| **Description** | Facilitates the running of interactive applications with additional administrative privileges. If this service is stopped, users will be unable to launch applications with the additional administrative privileges they may require to perform desired user tasks. |
| **Installation** | Always installed |
| **Startup type** | Manual |
| **Recommendation** | Do not disable |
| **Comments** | None |

## Application Layer Gateway Service

| Name | Description |
|--|--|
| **Service name** | ALG |
| **Description** | Provides support for third-party protocol plug-ins for Internet Connection Sharing |
| **Installation** | Always installed |
| **Startup type** | Manual |
| **Recommendation** | OK to disable |
| **Comments** | None |

## Application Management

| Name | Description |
|--|--|
| **Service name** | AppMgmt |
| **Description** | Processes installation, removal, and enumeration requests for software deployed through Group Policy. If the service is disabled, users will be unable to install, remove, or enumerate software deployed through Group Policy. If this service is disabled, any services that explicitly depend on it will fail to start. |
| **Installation** | Always installed |
| **Startup type** | Manual |
| **Recommendation** | OK to disable |
| **Comments** | None |

## AppX Deployment Service (AppXSVC)

| Name | Description |
|--|--|
| **Service name** | AppXSvc |
| **Description** | Provides infrastructure support for deploying Store applications. This service is started on demand and if disabled Store applications will not be deployed to the system, and may not function properly. |
| **Installation** | Always installed |
| **Startup type** | Manual |
| **Recommendation** | OK to disable |
| **Comments** | None |


## AssignedAccessManager Servce


## Auto Time Zone Updater

| Name | Description |
|--|--|
| **Service name** | tzautoupdate |
| **Description** | Automatically sets the system time zone. |
| **Installation** | Always installed |
| **Startup type** | Disabled |
| **Recommendation** | Already disabled |
| **Comments** | None |

## AVCTP Service

## Background Intelligent Transfer Service

| Name | Description |
|--|--|
| **Service name** | BITS |
| **Description** | Transfers files in the background using idle network bandwidth. If the service is disabled, then any applications that depend on BITS, such as Windows Update or MSN Explorer, will be unable to automatically download programs and other information. |
| **Installation** | Always installed |
| **Startup type** | Manual |
| **Recommendation** | OK to disable |
| **Comments** | None |

## Background Tasks Infrastructure Service

| Name | Description |
|--|--|
| **Service name** | BrokerInfrastructure |
| **Description** | Windows infrastructure service that controls which background tasks can run on the system. |
| **Installation** | Always installed |
| **Startup type** | Automatic |
| **Recommendation** | Do not disable |
| **Comments** | None |

## Base Filtering Engine

| Name | Description |
|--|--|
| **Service name** | BFE |
| **Description** | The Base Filtering Engine (BFE) is a service that manages firewall and Internet Protocol security (IPsec) policies and implements user mode filtering. Stopping or disabling the BFE service will significantly reduce the security of the system. It will also result in unpredictable behavior in IPsec management and firewall applications. |
| **Installation** | Always installed |
| **Startup type** | Automatic |
| **Recommendation** | Do not disable |
| **Comments** | None |


## BitLocker Drive Encryption Service

## Block Level Backup Engine Service (no guidance)

## Bluetooth Audio Gateway Service

## Bluetooth Support Service

| Name | Description |
|--|--|
| **Service name** | bthserv |
| **Description** | The Bluetooth service supports discovery and association of remote Bluetooth devices. Stopping or disabling this service may cause already installed Bluetooth devices to fail to operate properly and prevent new devices from being discovered or associated. |
| **Installation** | Only with Desktop Experience |
| **Startup type** | Manual |
| **Recommendation** | OK to disable |
| **Comments** | OK to disable if not used. Another disabling mechanism: [Disabling Bluetooth and Infrared Beaming](/previous-versions/tn-archive/dd252791(v=technet.10)) |

## Bluetooth User Support Service

## BranchCache

## Capability Access Manager Service

## CaptureService

## CDPUserSvc

| Name | Description |
|--|--|
| **Service name** | CDPUserSvc |
| **Description** | This user service is used for Connected Devices Platform scenarios |
| **Installation** | ? |
| **Startup type** | Automatic |
| **Recommendation** | OK to disable |
| **Comments** | User service template |

## Certificate Propagation

| Name | Description |
|--|--|
| **Service name** | CertPropSvc |
| **Description** | Copies user certificates and root certificates from smart cards into the current user's certificate store, detects when a smart card is inserted into a smart card reader, and if needed, installs the smart card Plug and Play minidriver. |
| **Installation** | Always installed |
| **Startup type** | Manual |
| **Recommendation** | Do not disable |
| **Comments** | None |

## Client License Service (ClipSVC)

| Name | Description |
|--|--|
| **Service name** | ClipSVC |
| **Description** | Provides infrastructure support for the Microsoft Store. This service is started on demand and if disabled applications bought using Microsoft Store will not behave correctly. |
| **Installation** | Always installed |
| **Startup type** | Manual |
| **Recommendation** | OK to disable |
| **Comments** | None |

## Clipboard User Service

## CNG Key Isolation

| Name | Description |
|--|--|
| **Service name** | KeyIso |
| **Description** | The CNG key isolation service is hosted in the LSA process. The service provides key process isolation to private keys and associated cryptographic operations as required by the Common Criteria. The service stores and uses long-lived keys in a secure process complying with Common Criteria requirements. |
| **Installation** | Always installed |
| **Startup type** | Manual |
| **Recommendation** | Do not disable |
| **Comments** | None |

## COM+ Event System

| Name | Description |
|--|--|
| **Service name** | EventSystem |
| **Description** | Supports System Event Notification Service (SENS), which provides automatic distribution of events to subscribing Component Object Model (COM) components. If the service is stopped, SENS will close and will not be able to provide logon and logoff notifications. If this service is disabled, any services that explicitly depend on it will fail to start. |
| **Installation** | Always installed |
| **Startup type** | Automatic |
| **Recommendation** | Do not disable |
| **Comments** | None |

## COM+ System Application

| Name | Description |
|--|--|
| **Service name** | COMSysApp |
| **Description** | Manages the configuration and tracking of Component Object Model (COM)+-based components. If the service is stopped, most COM+-based components will not function properly. If this service is disabled, any services that explicitly depend on it will fail to start. |
| **Installation** | Always installed |
| **Startup type** | Manual |
| **Recommendation** | Do not disable |
| **Comments** | None |

## Computer Browser

| Name | Description |
|--|--|
| **Service name** | Browser |
| **Description** | Maintains an updated list of computers on the network and supplies this list to computers designated as browsers. If this service is stopped, this list will not be updated or maintained. If this service is disabled, any services that explicitly depend on it will fail to start. |
| **Installation** | Always installed |
| **Startup type** | Disabled |
| **Recommendation** | No guidance |
| **Comments** | None |

## Connected Devices Platform Service

| Name | Description |
|--|--|
| **Service name** | CDPSvc |
| **Description** | This service is used for Connected Devices and Universal Glass scenarios |
| **Installation** | Only with Desktop Experience |
| **Startup type** | Automatic |
| **Recommendation** | OK to disable |
| **Comments** | None |

## Connected Devices Platform User Service

## Connected User Experiences and Telemetry

| Name | Description |
|--|--|
| **Service name** | DiagTrack |
| **Description** | The Connected User Experiences and Telemetry service enables features that support in-application and connected user experiences. Additionally, this service manages the event-driven collection and transmission of diagnostic and usage information (used to improve the experience and quality of the Windows Platform) when the diagnostics and usage privacy option settings are enabled under Feedback and Diagnostics. |
| **Installation** | Always installed |
| **Startup type** | Automatic |
| **Recommendation** | OK to disable |
| **Comments** | None |


## ConsentUX

## Contact Data

| Name | Description |
|--|--|
| **Service name** | PimIndexMaintenanceSvc |
| **Description** | Indexes contact data for fast contact searching. If you stop or disable this service, contacts might be missing from your search results. |
| **Installation** | Always installed |
| **Startup type** | Manual |
| **Recommendation** | OK to disable |
| **Comments** | User service template |

## CoreMessaging

| Name | Description |
|--|--|
| **Service name** | CoreMessagingRegistrar |
| **Description** | Manages communication between system components. |
| **Installation** | Always installed |
| **Startup type** | Automatic |
| **Recommendation** | OK to disable |
| **Comments** | None |

## Credential Manager

| Name | Description |
|--|--|
| **Service name** | VaultSvc |
| **Description** | Provides secure storage and retrieval of credentials to users, applications and security service packages. |
| **Installation** | Always installed |
| **Startup type** | Manual |
| **Recommendation** | No guidance |
| **Comments** | None |

## Cryptographic Services

| Name | Description |
|--|--|
| **Service name** | CryptSvc |
| **Description** | Provides three management services: Catalog Database Service, which confirms the signatures of Windows files and allows new programs to be installed; Protected Root Service, which adds and removes Trusted Root Certification Authority certificates from this computer; and Automatic Root Certificate Update Service, which retrieves root certificates from Windows Update and enable scenarios such as SSL. If this service is stopped, these management services will not function properly. If this service is disabled, any services that explicitly depend on it will fail to start. |
| **Installation** | Always installed |
| **Startup type** | Automatic |
| **Recommendation** | Do not disable |
| **Comments** | None |

## Data Sharing Service

| Name | Description |
|--|--|
| **Service name** | DsSvc |
| **Description** | Provides data brokering between applications. |
| **Installation** | Always installed |
| **Startup type** | Manual |
| **Recommendation** | Do not disable |
| **Comments** | None |

## Data Usage

## DataCollectionPublishingService

| Name | Description |
|--|--|
| **Service name** | DcpSvc |
| **Description** | The DCP (Data Collection and Publishing) service supports first-party apps to upload data to cloud. |
| **Installation** | Only with Desktop Experience |
| **Startup type** | Manual |
| **Recommendation** | No guidance |
| **Comments** | None |

## DCOM Server Process Launcher

| Name | Description |
|--|--|
| **Service name** | DcomLaunch |
| **Description** | The DCOMLAUNCH service launches COM and DCOM servers in response to object activation requests. If this service is stopped or disabled, programs using COM or DCOM will not function properly. It is strongly recommended that you have the DCOMLAUNCH service running. |
| **Installation** | Always installed |
| **Startup type** | Automatic |
| **Recommendation** | Do not disable |
| **Comments** | None |

## Delivery Optimization

## Device Association Service

| Name | Description |
|--|--|
| **Service name** | DeviceAssociationService |
| **Description** | Enables pairing between the system and wired or wireless devices. |
| **Installation** | Only with Desktop Experience |
| **Startup type** | Manual |
| **Recommendation** | OK to disable |
| **Comments** | None |

## Device Install Service

| Name | Description |
|--|--|
| **Service name** | DeviceInstall |
| **Description** | Enables a computer to recognize and adapt to hardware changes with little or no user input. Stopping or disabling this service will result in system instability. |
| **Installation** | Always installed |
| **Startup type** | Manual |
| **Recommendation** | Do not disable |
| **Comments** | None |

## Device Management Enrollment Service

| Name | Description |
|--|--|
| **Service name** | DmEnrollmentSvc |
| **Description** | Performs Device Enrollment Activities for Device Management |
| **Installation** | Always installed |
| **Startup type** | Manual |
| **Recommendation** | No guidance |
| **Comments** | None |

## Device Management Wireless Application Protocol (WAP) Push message Routing Service

## Device Setup Manager

| Name | Description |
|--|--|
| **Service name** | DsmSvc |
| **Description** | Enables the detection, download and installation of device-related software. If this service is disabled, devices may be configured with outdated software, and may not work correctly. |
| **Installation** | Always installed |
| **Startup type** | Manual |
| **Recommendation** | Do not disable |
| **Comments** | None |

## DevicePicker

## DevicesFlow

## DevQuery Background Discovery Broker

| Name | Description |
|--|--|
| **Service name** | DevQueryBroker |
| **Description** | Enables apps to discover devices with a backgroud task |
| **Installation** | Always installed |
| **Startup type** | Manual |
| **Recommendation** | Do not disable |
| **Comments** | None |

## DHCP Client

| Name | Description |
|--|--|
| **Service name** | Dhcp |
| **Description** | Registers and updates IP addresses and DNS records for this computer. If this service is stopped, this computer will not receive dynamic IP addresses and DNS updates. If this service is disabled, any services that explicitly depend on it will fail to start. |
| **Installation** | Always installed |
| **Startup type** | Automatic |
| **Recommendation** | Do not disable |
| **Comments** | None |

## Diagnostic Execution Service

## Diagnostic Policy Service

| Name | Description |
|--|--|
| **Service name** | DPS |
| **Description** | The Diagnostic Policy Service enables problem detection, troubleshooting and resolution for Windows components. If this service is stopped, diagnostics will no longer function. |
| **Installation** | Always installed |
| **Startup type** | Automatic |
| **Recommendation** | Do not disable |
| **Comments** | None |

## Diagnostic Service Host

| Name | Description |
|--|--|
| **Service name** | WdiServiceHost |
| **Description** | The Diagnostic Service Host is used by the Diagnostic Policy Service to host diagnostics that need to run in a Local Service context. If this service is stopped, any diagnostics that depend on it will no longer function. |
| **Installation** | Always installed |
| **Startup type** | Manual |
| **Recommendation** | No guidance |
| **Comments** | None |

## Diagnostic System Host

| Name | Description |
|--|--|
| **Service name** | WdiSystemHost |
| **Description** | The Diagnostic System Host is used by the Diagnostic Policy Service to host diagnostics that need to run in a Local System context. If this service is stopped, any diagnostics that depend on it will no longer function. |
| **Installation** | Always installed |
| **Startup type** | Manual |
| **Recommendation** | Do not disable |
| **Comments** | None |

## DisplayEnhancementService


## Distributed Link Tracking Client

| Name | Description |
|--|--|
| **Service name** | TrkWks |
| **Description** | Maintains links between NTFS files within a computer or across computers in a network. |
| **Installation** | Always installed |
| **Startup type** | Automatic |
| **Recommendation** | OK to disable |
| **Comments** | None |

## Distributed Transaction Coordinator

| Name | Description |
|--|--|
| **Service name** | MSDTC |
| **Description** | Coordinates transactions that span multiple resource managers, such as databases, message queues, and file systems. If this service is stopped, these transactions will fail. If this service is disabled, any services that explicitly depend on it will fail to start. |
| **Installation** | Always installed |
| **Startup type** | Automatic |
| **Recommendation** | No guidance |
| **Comments** | None |

## dmwappushsvc

| Name | Description |
|--|--|
| **Service name** | dmwappushservice |
| **Description** | WAP Push Message Routing Service |
| **Installation** | Only with Desktop Experience |
| **Startup type** | Manual |
| **Recommendation** | OK to disable |
| **Comments** | Service required on client devices for Intune, MDM and similar management technologies, and for Unified Write Filter. Not needed for Server. |

## DNS Client

| Name | Description |
|--|--|
| **Service name** | Dnscache |
| **Description** | The DNS Client service (dnscache) caches Domain Name System (DNS) names and registers the full computer name for this computer. If the service is stopped, DNS names will continue to be resolved. However, the results of DNS name queries will not be cached and the computer's name will not be registered. If the service is disabled, any services that explicitly depend on it will fail to start. |
| **Installation** | Always installed |
| **Startup type** | Automatic |
| **Recommendation** | Do not disable |
| **Comments** | None |

## Downloaded Maps Manager

| Name | Description |
|--|--|
| **Service name** | MapsBroker |
| **Description** | Windows service for application access to downloaded maps. This service is started on-demand by application accessing downloaded maps. Disabling this service will prevent apps from accessing maps. |
| **Installation** | Always installed |
| **Startup type** | Automatic |
| **Recommendation** | OK to disable |
| **Comments** | Disabling breaks apps that rely on the service; OK to disable if apps not relying on it |

## Embedded Mode

| Name | Description |
|--|--|
| **Service name** | embeddedmode |
| **Description** | The Embedded Mode service enables scenarios related to Background Applications. Disabling this service will prevent Background Applications from being activated. |
| **Installation** | Always installed |
| **Startup type** | Manual |
| **Recommendation** | Do not disable |
| **Comments** | None |

## Encrypting File System (EFS)

| Name | Description |
|--|--|
| **Service name** | EFS |
| **Description** | Provides the core file encryption technology used to store encrypted files on NTFS file system volumes. If this service is stopped or disabled, applications will be unable to access encrypted files. |
| **Installation** | Always installed |
| **Startup type** | Manual |
| **Recommendation** | Do not disable |
| **Comments** | None |

## Enterprise App Management Service

| Name | Description |
|--|--|
| **Service name** | EntAppSvc |
| **Description** | Enables enterprise application management. |
| **Installation** | Only with Desktop Experience |
| **Startup type** | Manual |
| **Recommendation** | OK to disable |
| **Comments** | None |

## Extensible Authentication Protocol

| Name | Description |
|--|--|
| **Service name** | EapHost |
| **Description** | The Extensible Authentication Protocol (EAP) service provides network authentication in such scenarios as 802.1x wired and wireless, VPN, and Network Access Protection (NAP). EAP also provides application programming interfaces (APIs) that are used by network access clients, including wireless and VPN clients, during the authentication process. If you disable this service, this computer is prevented from accessing networks that require EAP authentication. |
| **Installation** | Always installed |
| **Startup type** | Manual |
| **Recommendation** | OK to disable |
| **Comments** | None |


## Fax

## File History Service

## Function Discovery Provider Host

| Name | Description |
|--|--|
| **Service name** | fdPHost |
| **Description** | The FDPHOST service hosts the Function Discovery (FD) network discovery providers. These FD providers supply network discovery services for the Simple Services Discovery Protocol (SSDP) and Web Services - Discovery (WS-D) protocol. Stopping or disabling the FDPHOST service will disable network discovery for these protocols when using FD. When this service is unavailable, network services using FD and relying on these discovery protocols will be unable to find network devices or resources. |
| **Installation** | Always installed |
| **Startup type** | Manual |
| **Recommendation** | OK to disable |
| **Comments** | None |

## Function Discovery Resource Publication

| Name | Description |
|--|--|
| **Service name** | FDResPub |
| **Description** | Publishes this computer and resources attached to this computer so they can be discovered over the network. If this service is stopped, network resources will no longer be published and they will not be discovered by other computers on the network. |
| **Installation** | Always installed |
| **Startup type** | OK to disable |
| **Recommendation** | No guidance |
| **Comments** | None |

## GameDVR and Broadcast User Service

## Geolocation Service

| Name | Description |
|--|--|
| **Service name** | lfsvc |
| **Description** | This service monitors the current location of the system and manages geofences (a geographical location with associated events). If you turn off this service, applications will be unable to use or receive notifications for geolocation or geofences. |
| **Installation** | Only with Desktop Experience |
| **Startup type** | Manual |
| **Recommendation** | OK to disable |
| **Comments** | Disabling breaks apps that rely on the service; OK to disable if apps not relying on it |

## GraphicsPerfSvc

## Group Policy Client

| Name | Description |
|--|--|
| **Service name** | gpsvc |
| **Description** | The service is responsible for applying settings configured by administrators for the computer and users through the Group Policy component. If the service is disabled, the settings will not be applied and applications and components will not be manageable through Group Policy. Any components or applications that depend on the Group Policy component might not be functional if the service is disabled. |
| **Installation** | Always installed |
| **Startup type** | Automatic |
| **Recommendation** | Do not disable |
| **Comments** | None |

## Human Interface Device Service

| Name | Description |
|--|--|
| **Service name** | hidserv |
| **Description** | Activates and maintains the use of hot buttons on keyboards, remote controls, and other multimedia devices. It is recommended that you keep this service running. |
| **Installation** | Always installed |
| **Startup type** | Manual |
| **Recommendation** | Do not disable |
| **Comments** | None |

## HV Host Service

| Name | Description |
|--|--|
| **Service name** | HvHost |
| **Description** | Provides an interface for the Hyper-V hypervisor to provide per-partition performance counters to the host operating system. |
| **Installation** | Always installed |
| **Startup type** | Manual |
| **Recommendation** | OK to disable |
| **Comments** | Performance enhancers for guest VMs. Not used today except for explicitly populated VMs, but will be used in Application Guard |

## Hyper-V Data Exchange Service

| Name | Description |
|--|--|
| **Service name** | vmickvpexchange |
| **Description** | Provides a mechanism to exchange data between the virtual machine and the operating system running on the physical computer. |
| **Installation** | Always installed |
| **Startup type** | Manual |
| **Recommendation** | OK to disable |
| **Comments** | See HvHost |

## Hyper-V Guest Service Interface

| Name | Description |
|--|--|
| **Service name** | vmicguestinterface |
| **Description** | Provides an interface for the Hyper-V host to interact with specific services running inside the virtual machine. |
| **Installation** | Always installed |
| **Startup type** | Manual |
| **Recommendation** | OK to disable |
| **Comments** | See HvHost |

## Hyper-V Guest Shutdown Service

| Name | Description |
|--|--|
| **Service name** | vmicshutdown |
| **Description** | Provides a mechanism to shut down the operating system of this virtual machine from the management interfaces on the physical computer. |
| **Installation** | Always installed |
| **Startup type** | Manual |
| **Recommendation** | OK to disable |
| **Comments** | See HvHost |

## Hyper-V Heartbeat Service

| Name | Description |
|--|--|
| **Service name** | vmicheartbeat |
| **Description** | Monitors the state of this virtual machine by reporting a heartbeat at regular intervals. This service helps you identify running virtual machines that have stopped responding. |
| **Installation** | Always installed |
| **Startup type** | Manual |
| **Recommendation** | OK to disable |
| **Comments** | See HvHost |


## Hyper-V PowerShell Direct Service

| Name | Description |
|--|--|
| **Service name** | vmicvmsession |
| **Description** | Provides a mechanism to manage virtual machine with PowerShell via VM session without a virtual network. |
| **Installation** | Always installed |
| **Startup type** | Manual |
| **Recommendation** | OK to disable |
| **Comments** | See HvHost |


## Hyper-V Remote Desktop Virtualization Service

| Name | Description |
|--|--|
| **Service name** | vmicrdv |
| **Description** | Provides a platform for communication between the virtual machine and the operating system running on the physical computer. |
| **Installation** | Always installed |
| **Startup type** | Manual |
| **Recommendation** | OK to disable |
| **Comments** | See HvHost |

## Hyper-V Time Synchronization Service

| Name | Description |
|--|--|
| **Service name** | vmictimesync |
| **Description** | Synchronizes the system time of this virtual machine with the system time of the physical computer. |
| **Installation** | Always installed |
| **Startup type** | Manual |
| **Recommendation** | OK to disable |
| **Comments** | See HvHost |

## Hyper-V Volume Shadow Copy Requestor

| Name | Description |
|--|--|
| **Service name** | vmicvss |
| **Description** | Coordinates the communications that are required to use Volume Shadow Copy Service to back up applications and data on this virtual machine from the operating system on the physical computer. |
| **Installation** | Always installed |
| **Startup type** | Manual |
| **Recommendation** | OK to disable |
| **Comments** | See HvHost |

## IKE and AuthIP IPsec Keying Modules

| Name | Description |
|--|--|
| **Service name** | IKEEXT |
| **Description** | The IKEEXT service hosts the Internet Key Exchange (IKE) and Authenticated Internet Protocol (AuthIP) keying modules. These keying modules are used for authentication and key exchange in Internet Protocol security (IPsec). Stopping or disabling the IKEEXT service will disable IKE and AuthIP key exchange with peer computers. IPsec is typically configured to use IKE or AuthIP; therefore, stopping or disabling the IKEEXT service might result in an IPsec failure and might compromise the security of the system. It is strongly recommended that you have the IKEEXT service running. |
| **Installation** | Always installed |
| **Startup type** | Manual |
| **Recommendation** | Do not disable |
| **Comments** | None |

## Infrared monitor service

## Intel(R) Content Protection HDCP Service

## Intel(R) Content Protection HECI Service

## Intel(R) Dynamic Platform and Thermal Framework service

## Intel(R) HD Graphics Control Panel Service

## Interactive Services Detection

| Name | Description |
|--|--|
| **Service name** | UI0Detect |
| **Description** | Enables user notification of user input for interactive services, which enables access to dialogs created by interactive services when they appear. If this service is stopped, notifications of new interactive service dialogs will no longer function and there might not be access to interactive service dialogs. If this service is disabled, both notifications of and access to new interactive service dialogs will no longer function. |
| **Installation** | Only with Desktop Experience |
| **Startup type** | Manual |
| **Recommendation** | No guidance |
| **Comments** | None |

## Internet Connection Sharing (ICS)

| Name | Description |
|--|--|
| **Service name** | SharedAccess |
| **Description** | Provides network address translation, addressing, name resolution and/or intrusion prevention services for a home or small office network. |
| **Installation** | Always installed |
| **Startup type** | Manual |
| **Recommendation** | OK to disable |
| **Comments** | Required for clients used as WiFi hotspots, and also on both ends of Miracast projection. ICS can be blocked with GPO setting, "Prohibit use of Internet Connection Sharing on your DNS domain network" |

## IP Helper

| Name | Description |
|--|--|
| **Service name** | iphlpsvc |
| **Description** | Provides tunnel connectivity using IPv6 transition technologies (6to4, ISATAP, Port Proxy, and Teredo), and IP-HTTPS. If this service is stopped, the computer will not have the enhanced connectivity benefits that these technologies offer. |
| **Installation** | Always installed |
| **Startup type** | Automatic |
| **Recommendation** | OK to disable |
| **Comments** | None |

## IP Translation Configuration Service

## IPsec Policy Agent

| Name | Description |
|--|--|
| **Service name** | PolicyAgent |
| **Description** | Internet Protocol security (IPsec) supports network-level peer authentication, data origin authentication, data integrity, data confidentiality (encryption), and replay protection. This service enforces IPsec policies created through the IP Security Policies snap-in or the command-line tool "netsh ipsec". If you stop this service, you may experience network connectivity issues if your policy requires that connections use IPsec. Also, remote management of Windows Firewall is not available when this service is stopped. |
| **Installation** | Always installed |
| **Startup type** | Manual |
| **Recommendation** | Do not disable |
| **Comments** | None |

## KDC Proxy Server service (KPS)

| Name | Description |
|--|--|
| **Service name** | KPSSVC |
| **Description** | KDC Proxy Server service runs on edge servers to proxy Kerberos protocol messages to domain controllers on the corporate network. |
| **Installation** | Always installed |
| **Startup type** | Manual |
| **Recommendation** | No guidance |
| **Comments** | None |



## KtmRm for Distributed Transaction Coordinator

| Name | Description |
|--|--|
| **Service name** | KtmRm |
| **Description** | Coordinates transactions between the Distributed Transaction Coordinator (MSDTC) and the Kernel Transaction Manager (KTM). If it is not needed, it is recommended that this service remain stopped. If it is needed, both MSDTC and KTM will start this service automatically. If this service is disabled, any MSDTC transaction interacting with a Kernel Resource Manager will fail and any services that explicitly depend on it will fail to start. |
| **Installation** | Always installed |
| **Startup type** | Manual |
| **Recommendation** | Do not disable |
| **Comments** | None |


## Language Experience Service

## Link-Layer Topology Discovery Mapper

| Name | Description |
|--|--|
| **Service name** | lltdsvc |
| **Description** | Creates a Network Map, consisting of PC and device topology (connectivity) information, and metadata describing each PC and device. If this service is disabled, the Network Map will not function properly. |
| **Installation** | Always installed |
| **Startup type** | Manual |
| **Recommendation** | OK to disable |
| **Comments** | OK to disable if no dependencies on Network Map |

## Local Profile Assistance Service

## Local Session Manager

| Name | Description |
|--|--|
| **Service name** | LSM |
| **Description** | Core Windows Service that manages local user sessions. Stopping or disabling this service will result in system instability. |
| **Installation** | Always installed |
| **Startup type** | Automatic |
| **Recommendation** | Do not disable |
| **Comments** | None |

## MessagingService

## Microsoft (R) Diagnostics Hub Standard Collector

| Name | Description |
|--|--|
| **Service name** | diagnosticshub.standardcollector.service |
| **Description** | Diagnostics Hub Standard Collector Service. When running, this service collects real time ETW events and processes them. |
| **Installation** | Always installed |
| **Startup type** | Manual |
| **Recommendation** | Do not disable |
| **Comments** | None |

## Microsoft Account Sign-in Assistant

| Name | Description |
|--|--|
| **Service name** | wlidsvc |
| **Description** | Enables user sign-in through Microsoft account identity services. If this service is stopped, users will not be able to log on to the computer with their Microsoft account. |
| **Installation** | Always installed |
| **Startup type** | Manual |
| **Recommendation** | OK to disable |
| **Comments** | Microsoft Accounts are N/A on Windows Server |

## Microsoft App-V Client

| Name | Description |
|--|--|
| **Service name** | AppVClient |
| **Description** | Manages App-V users and virtual applications |
| **Installation** | Always installed |
| **Startup type** | Disabled |
| **Recommendation** | Already disabled |
| **Comments** | None |

## Microsoft iSCSI Initiator Service

| Name | Description |
|--|--|
| **Service name** | MSiSCSI |
| **Description** | Manages Internet SCSI (iSCSI) sessions from this computer to remote iSCSI target devices. If this service is stopped, this computer will not be able to login or access iSCSI targets. If this service is disabled, any services that explicitly depend on it will fail to start. |
| **Installation** | Always installed |
| **Startup type** | Manual |
| **Recommendation** | OK to disable |
| **Comments** | Our diagnostic data indicates this is used on client as well as server. No benefit to disabling this. |

## Microsoft Passport

| Name | Description |
|--|--|
| **Service name** | NgcSvc |
| **Description** | Provides process isolation for cryptographic keys used to authenticate to a user's associated identity providers. If this service is disabled, all uses and management of these keys will not be available, which includes machine logon and single-sign on for apps and websites. This service starts and stops automatically. It is recommended that you do not reconfigure this service. |
| **Installation** | Always installed |
| **Startup type** | Manual |
| **Recommendation** | OK to disable |
| **Comments** | Needed for PIN/Hello logons, which aren't supported on Server |


## Microsoft Passport Container

| Name | Description |
|--|--|
| **Service name** | NgcCtnrSvc |
| **Description** | Manages local user identity keys used to authenticate user to identity providers as well as TPM virtual smart cards. If this service is disabled, local user identity keys and TPM virtual smart cards will not be accessible. It is recommended that you do not reconfigure this service. |
| **Installation** | Only with Desktop Experience |
| **Startup type** | Manual |
| **Recommendation** | OK to disable |
| **Comments** | None |

## Microsoft Software Shadow Copy Provider

| Name | Description |
|--|--|
| **Service name** | swprv |
| **Description** | Manages software-based volume shadow copies taken by the Volume Shadow Copy service. If this service is stopped, software-based volume shadow copies cannot be managed. If this service is disabled, any services that explicitly depend on it will fail to start. |
| **Installation** | Always installed |
| **Startup type** | Manual |
| **Recommendation** | OK to disable |
| **Comments** | None |

## Microsoft Storage Spaces SMP

| Name | Description |
|--|--|
| **Service name** | smphost |
| **Description** | Host service for the Microsoft Storage Spaces management provider. If this service is stopped or disabled, Storage Spaces cannot be managed. |
| **Installation** | Always installed |
| **Startup type** | Manual |
| **Recommendation** | OK to disable |
| **Comments** | Storage management APIs fail without this service. Example: "Get-WmiObject -class MSFT_Disk -Namespace Root\Microsoft\Windows\Storage". |

## Microsoft Store Install Service

## Microsoft Windows SMS Router Service

## Natural Authentication

## Net.Tcp Port Sharing Service

| Name | Description |
|--|--|
| **Service name** | NetTcpPortSharing |
| **Description** | Provides ability to share TCP ports over the net.tcp protocol. |
| **Installation** | Always installed |
| **Startup type** | Disabled |
| **Recommendation** | Already disabled |
| **Comments** | None |

## Netlogon

| Name | Description |
|--|--|
| **Service name** | Netlogon |
| **Description** | Maintains a secure channel between this computer and the domain controller for authenticating users and services. If this service is stopped, the computer may not authenticate users and services and the domain controller cannot register DNS records. If this service is disabled, any services that explicitly depend on it will fail to start. |
| **Installation** | Always installed |
| **Startup type** | Manual |
| **Recommendation** | OK to disable |
| **Comments** | None |

## Network Connected Devices Auto-Setup

## Network Connection Broker

| Name | Description |
|--|--|
| **Service name** | NcbService |
| **Description** | Brokers connections that allow Microsoft Store Apps to receive notifications from the internet. |
| **Installation** | Always installed |
| **Startup type** | Manual |
| **Recommendation** | OK to disable |
| **Comments** | None |

## Network Connections

| Name | Description |
|--|--|
| **Service name** | Netman |
| **Description** | Manages objects in the Network and Dial-Up Connections folder, in which you can view both local area network and remote connections. |
| **Installation** | Always installed |
| **Startup type** | Manual |
| **Recommendation** | Do not disable |
| **Comments** | None |


## Network Connectivity Assistant

| Name | Description |
|--|--|
| **Service name** | NcaSvc |
| **Description** | Provides DirectAccess status notification for UI components |
| **Installation** | Always installed |
| **Startup type** | Manual |
| **Recommendation** | OK to disable |
| **Comments** | None |

## Network List Service

| Name | Description |
|--|--|
| **Service name** | netprofm |
| **Description** | Identifies the networks to which the computer has connected, collects and stores properties for these networks, and notifies applications when these properties change. |
| **Installation** | Always installed |
| **Startup type** | Manual |
| **Recommendation** | No guidance |
| **Comments** | None |


## Network Location Awareness

| Name | Description |
|--|--|
| **Service name** | NlaSvc |
| **Description** | Collects and stores configuration information for the network and notifies programs when this information is modified. If this service is stopped, configuration information might be unavailable. If this service is disabled, any services that explicitly depend on it will fail to start. |
| **Installation** | Always installed |
| **Startup type** | Automatic |
| **Recommendation** | OK to disable |
| **Comments** | None |

## Network Setup Service

| Name | Description |
|--|--|
| **Service name** | NetSetupSvc |
| **Description** | The Network Setup Service manages the installation of network drivers and permits the configuration of low-level network settings. If this service is stopped, any driver installations that are in-progress may be cancelled. |
| **Installation** | Always installed |
| **Startup type** | Manual |
| **Recommendation** | Do not disable |
| **Comments** | None |



## Network Store Interface Service

| Name | Description |
|--|--|
| **Service name** | nsi |
| **Description** | This service delivers network notifications (e.g. interface addition/deleting etc.) to user mode clients. Stopping this service will cause loss of network connectivity. If this service is disabled, any other services that explicitly depend on this service will fail to start. |
| **Installation** | Always installed |
| **Startup type** | Automatic |
| **Recommendation** | No guidance |
| **Comments** | None |

## Offline Files

| Name | Description |
|--|--|
| **Service name** | CscService |
| **Description** | The Offline Files service performs maintenance activities on the Offline Files cache, responds to user logon and logoff events, implements the internals of the public API, and dispatches interesting events to those interested in Offline Files activities and changes in cache state. |
| **Installation** | Only with Desktop Experience |
| **Startup type** | Disabled |
| **Recommendation** | Already disabled |
| **Comments** | None |

## OpenSSH Authentication Agent


## Optimize drives

| Name | Description |
|--|--|
| **Service name** | defragsvc |
| **Description** | Helps the computer run more efficiently by optimizing files on storage drives. |
| **Installation** | Always installed |
| **Startup type** | Manual |
| **Recommendation** | OK to disable |
| **Comments** | None |

## Parental Controls

## Payments and NFC/SE Manager

## Peer Name Resolution Protocol

## Peer Networking Grouping

## Peer Networking Identity Manager


## Performance Counter DLL Host

| Name | Description |
|--|--|
| **Service name** | PerfHost |
| **Description** | Enables remote users and 64-bit processes to query performance counters provided by 32-bit DLLs. If this service is stopped, only local users and 32-bit processes will be able to query performance counters provided by 32-bit DLLs. |
| **Installation** | Always installed |
| **Startup type** | Manual |
| **Recommendation** | No guidance |
| **Comments** | None |



## Performance Logs & Alerts

| Name | Description |
|--|--|
| **Service name** | pla |
| **Description** | Performance Logs and Alerts Collects performance data from local or remote computers based on preconfigured schedule parameters, then writes the data to a log or triggers an alert. If this service is stopped, performance information will not be collected. If this service is disabled, any services that explicitly depend on it will fail to start. |
| **Installation** | Always installed |
| **Startup type** | Manual |
| **Recommendation** | No guidance |
| **Comments** | None |



## Phone Service

| Name | Description |
|--|--|
| **Service name** | PhoneSvc |
| **Description** | Manages the telephony state on the device |
| **Installation** | Only with Desktop Experience |
| **Startup type** | Manual |
| **Recommendation** | OK to disable |
| **Comments** | Used by modern VoIP apps |



## Plug and Play

| Name | Description |
|--|--|
| **Service name** | PlugPlay |
| **Description** | Enables a computer to recognize and adapt to hardware changes with little or no user input. Stopping or disabling this service will result in system instability. |
| **Installation** | Always installed |
| **Startup type** | Manual |
| **Recommendation** | No guidance |
| **Comments** | None |



## Portable Device Enumerator Service

| Name | Description |
|--|--|
| **Service name** | WPDBusEnum |
| **Description** | Enforces group policy for removable mass-storage devices. Enables applications such as Windows Media Player and Image Import Wizard to transfer and synchronize content using removable mass-storage devices. |
| **Installation** | Only with Desktop Experience |
| **Startup type** | Manual |
| **Recommendation** | No guidance |
| **Comments** | None |



## Power

| Name | Description |
|--|--|
| **Service name** | Power |
| **Description** | Manages power policy and power policy notification delivery. |
| **Installation** | Always installed |
| **Startup type** | Automatic |
| **Recommendation** | No guidance |
| **Comments** | None |



## Print Spooler

| Name | Description |
|--|--|
| **Service name** | Spooler |
| **Description** | This service spools print jobs and handles interaction with the printer. If you turn off this service, you won't be able to print or see your printers. |
| **Installation** | Always installed |
| **Startup type** | Automatic |
| **Recommendation** | OK to disable if not a print server or a DC |
| **Comments** | On a domain controller, the installation of the DC role adds a thread to the spooler service that is responsible for performing print pruning – removing the stale print queue objects from the Active Directory. If the spooler service is not running on at least one DC in each site, then the AD has no means to remove old queues that no longer exist. ["Disabling Unnecessary Services? A Word to the Wise" - Microsoft Tech Community - Ask The Performance Team Blog](https://techcommunity.microsoft.com/t5/ask-the-performance-team/disabling-unnecessary-services-a-word-to-the-wise/ba-p/373444). |



## Printer Extensions and Notifications

| Name | Description |
|--|--|
| **Service name** | PrintNotify |
| **Description** | This service opens custom printer dialog boxes and handles notifications from a remote print server or a printer. If you turn off this service, you won't be able to see printer extensions or notifications. |
| **Installation** | Always installed |
| **Startup type** | Manual |
| **Recommendation** | OK to disable if not a print server |
| **Comments** | None |



## Problem Reports and Solutions Control Panel Support

| Name | Description |
|--|--|
| **Service name** | wercplsupport |
| **Description** | This service provides support for viewing, sending and deletion of system-level problem reports for the Problem Reports and Solutions control panel. |
| **Installation** | Only with Desktop Experience |
| **Startup type** | Manual |
| **Recommendation** | No guidance |
| **Comments** | None |



## Program Compatibility Assistant Service

| Name | Description |
|--|--|
| **Service name** | PcaSvc |
| **Description** | This service provides support for the Program Compatibility Assistant (PCA). PCA monitors programs installed and run by the user and detects known compatibility problems. If this service is stopped, PCA will not function properly. |
| **Installation** | Only with Desktop Experience |
| **Startup type** | Automatic |
| **Recommendation** | OK to disable |
| **Comments** | None |
