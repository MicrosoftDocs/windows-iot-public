---
title: Guidance on configuring system services
titleSuffix: Windows IoT Enterprise
author: TerryWarwick
ms.author: twarwick
ms.date: 01/03/2024
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: Security guidelines for disabling services in Windows IoT Enterprise
keywords: IoT Enterprise, Security, services
---
# Guidance on disabling system services on Windows IoT Enterprise

**Applies to:**

Applies to:  
✅ Windows 11 IoT Enterprise
✅ Windows 10 IoT Enterprise
✅ Windows 10 IoT Enterprise LTSC 2021

##

The Windows operating system includes many system services that provide important functionality. Different services have different default startup policies: some are started by default (automatic), some when needed (manual), and some are disabled by default and must be explicitly enabled before they can run. These defaults were chosen carefully for each service to balance performance, functionality, and security for typical customers.

However, some IoT customers may prefer a more security-focused balance for their Windows IoT devices, one that reduces their attack surface to the absolute minimum, and may therefore wish to fully disable all services that are not needed in their specific environments. For those customers, Microsoft&reg; is providing the accompanying guidance regarding which services can safely be disabled for this purpose.

The guidance is only for Windows IoT Enterprise customers.

Customers can configure their Windows IoT devices to disable selected services using the Security Templates in their Group Policies or using PowerShell automation. In some cases, the guidance includes specific Group Policy settings that disable the service's functionality directly, as an alternative to disabling the service itself.

Microsoft recommends that customers disable the following services and their respective scheduled tasks on Windows IoT Enterprise:

Services:

1. Xbox Live Auth Manager
2. Xbox Live Game Save

Scheduled tasks:

1. \Microsoft\XblGameSave\XblGameSaveTask
2. \Microsoft\XblGameSave\XblGameSaveTaskLogon

## Guidance descriptions

For all system services listed in this document, Microsoft provides guidance for enabling and disabling system services in Windows IoT Enterprise.

- **🟡 No guidance:** The impact of disabling these services has not been fully evaluated. Therefore, the default configuration of these services should not be changed.
- **⛔ Do not disable:** Disabling this service will impact essential functionality or prevent specific roles or features from functioning correctly. Therefore it should not be disabled.
- **🟢 OK to disable:** This service provides functionality that is useful to some but not all enterprises, and security-focused enterprises that don't use it can safely disable it.
- **✅&nbsp;Already&nbsp;disabled:** This service is disabled by default; no need to enforce with policy.
- **🔵&nbsp;Should&nbsp;be&nbsp;disabled:** This service should never be enabled on a well-managed enterprise system.

## Service Startup Guidance

The following table offer Microsoft guidance on disabling system services on Windows IoT Enterprise:

| Name | Service Name | Startup&nbsp;Type</br>(Default)| Recommendation |
|--|--|--|--|
| ActiveX Installer                       | AxInstSV                                 | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| Agent Activation runtime                | AarSvc                                   | Manual    | ⛔&nbsp;Do&nbsp;not&nbsp;disable     |
| AllJoyn Router Service                  | AJRouter                                 | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| App Readiness                           | AppReadiness                             | Manual    | ⛔&nbsp;Do&nbsp;not&nbsp;disable     |
| Application Identity                    | AppIDSvc                                 | Manual    | ⛔&nbsp;Do&nbsp;not&nbsp;disable     |
| Application Information                 | Appinfo                                  | Manual    | ⛔&nbsp;Do&nbsp;not&nbsp;disable     |
| Application Layer Gateway Service       | ALG                                      | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| Application Management                  | AppMgmt                                  | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| AppX Deployment Service (AppXSVC)       | AppXSvc                                  | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| AssignedAccessManager Service           | AssignedAccessManagerSvc                 | Manual    | ⛔&nbsp;Do&nbsp;not&nbsp;disable     |
| Auto Time Zone Updater                  | tzautoupdate                             | Disabled  | ✅&nbsp;Already&nbsp;disabled   |
| AVCTP Service                           | BthAvctpSvc                              | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| Background Intelligent Transfer Service | BITS                                     | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| Background Tasks Infrastructure Service | BrokerInfrastructure                     | Automatic | ⛔&nbsp;Do&nbsp;not&nbsp;disable     |
| Base Filtering Engine                   | BFE                                      | Automatic | ⛔&nbsp;Do&nbsp;not&nbsp;disable     |
| BitLocker Drive Encryption Service      | BDESVC                                   | Manual    | ⛔&nbsp;Do&nbsp;not&nbsp;disable     |
| Block Level Backup Engine Service       | wbengine                                 | Manual    | 🟡&nbsp;No&nbsp;guidance       |
| Bluetooth Audio Gateway Service         | BTAGService                              | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| Bluetooth Support Service               | bthserv                                  | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| Bluetooth User Support Service          | BluetoothUserService                     | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| BranchCache                             | PeerDistSvc                              | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| Capability Access Manager Service       | camsvc                                   | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| Capture Service                         | CaptureService                           | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| Cellular Time                           | autotimesvc                              | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| Certificate Propagation                 | CertPropSvc                              | Manual    | ⛔&nbsp;Do&nbsp;not&nbsp;disable     |
| Client License Service (ClipSVC)        | ClipSVC                                  | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| Clipboard User Service                  | cbdhsvc                                  | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| CNG Key Isolation                       | KeyIso                                   | Manual    | ⛔&nbsp;Do&nbsp;not&nbsp;disable     |
| COM+ Event System                       | EventSystem                              | Automatic | ⛔&nbsp;Do&nbsp;not&nbsp;disable     |
| COM+ System Application                 | COMSysApp                                | Manual    | ⛔&nbsp;Do&nbsp;not&nbsp;disable     |
| Connected Devices Platform Service      | CDPSvc                                   | Automatic | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| Connected Devices Platform User Service | CDPUserSvc                               | Automatic | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| Connected User Experiences and Telemetry | DiagTrack                               | Automatic | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| ConsentUX                                | ConsentUxUserSvc                        | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| Contact Data                             | PimIndexMaintenanceSvc                  | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| CoreMessaging                            | CoreMessagingRegistrar                  | Automatic | ⛔&nbsp;Do&nbsp;not&nbsp;disable     |
| Credential Manager                       | VaultSvc                                | Manual    | ⛔&nbsp;Do&nbsp;not&nbsp;disable     |
| Credential Enrollment Manager            |CredentialEnrollmentManagerUserSvc       | Manual    | ⛔&nbsp;Do&nbsp;not&nbsp;disable     |
| Cryptographic Services                   | CryptSvc                                | Automatic | ⛔&nbsp;Do&nbsp;not&nbsp;disable     |
| Data Sharing Service                     | DsSvc                                   | Manual    | ⛔&nbsp;Do&nbsp;not&nbsp;disable     |
| Data Usage                               | DusmSvc                                 | Automatic | ⛔&nbsp;Do&nbsp;not&nbsp;disable     |
| DCOM Server Process Launcher             | DcomLaunch                              | Automatic | ⛔&nbsp;Do&nbsp;not&nbsp;disable     |
| Delivery Optimization                    | DoSvc                                   | Automatic | ⛔&nbsp;Do&nbsp;not&nbsp;disable     |
| Device Association Service               | DeviceAssociationService                | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| Device Install Service                   | DeviceInstall                           | Manual    | ⛔&nbsp;Do&nbsp;not&nbsp;disable     |
| Device Management Enrollment Service     | DmEnrollmentSvc                         | Manual    | 🟡&nbsp;No&nbsp;guidance       |
| Device Management Wireless Application Protocol (WAP) Push message Routing Service | dmwappushservic | Manual    | 🟡&nbsp;No&nbsp;guidance|
| Device Setup Manager                     | DsmSvc                                  | Manual    | ⛔&nbsp;Do&nbsp;not&nbsp;disable     |
| DevicePicker                             | DevicePickerUserSvc                     | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| DevicesFlow                              | DevicesFlowUserSvc                      | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| DevQuery Background Discovery Broker     | DevQueryBroker                          | Manual    | ⛔&nbsp;Do&nbsp;not&nbsp;disable     |
| DHCP Client                              | Dhcp                                    | Automatic | ⛔&nbsp;Do&nbsp;not&nbsp;disable     |
| Diagnostic Execution Service             | diagsvc                                 | Manual    | ⛔&nbsp;Do&nbsp;not&nbsp;disable     |
| Diagnostic Policy Service                | DPS                                     | Automatic | ⛔&nbsp;Do&nbsp;not&nbsp;disable     |
| Diagnostic Service Host                  | WdiServiceHost                          | Manual    | ⛔&nbsp;Do&nbsp;not&nbsp;disable     |
| Diagnostic System Host                   | WdiSystemHost                           | Manual    | ⛔&nbsp;Do&nbsp;not&nbsp;disable     |
| Dialog Blocking Service                  | DialogBlockingService                   | Disabled  | ✅&nbsp;Already&nbsp;disabled   |
| Display Enhancement Service              | DisplayEnhancementService               | Manual    | ⛔&nbsp;Do&nbsp;not&nbsp;disable     |
| Display Policy Service                   | DispBrokerDesktopSvc                    | Automatic | ⛔&nbsp;Do&nbsp;not&nbsp;disable     |
| Distributed Link Tracking Client         | TrkWks                                  | Automatic | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| Distributed Transaction Coordinator      | MSDTC                                   | Automatic | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| DNS Client                               | Dnscache                                | Automatic | ⛔&nbsp;Do&nbsp;not&nbsp;disable     |
| Downloaded Maps Manager                  | MapsBroker                              | Automatic | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| Embedded Mode                            | embeddedmode                            | Manual    | ⛔&nbsp;Do&nbsp;not&nbsp;disable     |
| Encrypting File System (EFS)             | EFS                                     | Manual    | ⛔&nbsp;Do&nbsp;not&nbsp;disable     |
| Enterprise App Management Service        | EntAppSvc                               | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| Extensible Authentication Protocol       | EapHost                                 | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| Fax                                      | Fax                                     | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| File History Service                     | fhsvc                                   | Manual    | ⛔&nbsp;Do&nbsp;not&nbsp;disable     |
| Function Discovery Provider Host         | fdPHost                                 | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| Function Discovery Resource Publication  | FDResPub                                | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| GameDVR and Broadcast User Service       | BcastDVRUserService                     | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| Geolocation Service                      | lfsvc                                   | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| GraphicsPerfSvc                          | GraphicsPerfSvc                         | Manual    | ⛔&nbsp;Do&nbsp;not&nbsp;disable     |
| Group Policy Client                      | gpsvc                                   | Automatic | ⛔&nbsp;Do&nbsp;not&nbsp;disable     |
| Human Interface Device Service           | hidserv                                 | Manual    | ⛔&nbsp;Do&nbsp;not&nbsp;disable     |
| HV Host Service                          | HvHost                                  | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| Hyper-V Data Exchange Service            | vmickvpexchange                         | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| Hyper-V Guest Service Interface          | vmicguestinterface                      | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| Hyper-V Guest Shutdown Service           | vmicshutdown                            | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| Hyper-V Heartbeat Service                | vmicheartbeat                           | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| Hyper-V PowerShell Direct Service        | vmicvmsession                           | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| Hyper-V Remote Desktop Virtualization Service | vmicrdv                            | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| Hyper-V Time Synchronization Service     | vmictimesync                            | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| Hyper-V Volume Shadow Copy Requestor     | vmicvss                                 | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| IKE and AuthIP IPsec Keying Modules      | IKEEXT                                  | Manual    | ⛔&nbsp;Do&nbsp;not&nbsp;disable     |
| Internet Connection Sharing (ICS)        | SharedAccess                            | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| IP Helper                                | iphlpsvc                                | Automatic | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| IP Translation Configuration Service     | IpxlatCfgSvc                            | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| IPsec Policy Agent                       | PolicyAgent                             | Manual    | ⛔&nbsp;Do&nbsp;not&nbsp;disable     |
| KtmRm for Distributed Transaction Coordinator| KtmRm                               | Manual    | ⛔&nbsp;Do&nbsp;not&nbsp;disable     |
| Language Experience Service              | LxpSvc                                  | Manual    | ⛔&nbsp;Do&nbsp;not&nbsp;disable     |
| Link-Layer Topology Discovery Mapper     | lltdsvc                                 | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| Local Profile Assistance Service         | wlpasvc                                 | Automatic | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| Local Session Manager                    | LSM                                     | Automatic | ⛔&nbsp;Do&nbsp;not&nbsp;disable     |
| Messaging Service                        | MessagingService                        | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| Microsoft (R) Diagnostics Hub Standard Collector| diagnosticshub.standardcollector.service | Manual    | ⛔&nbsp;Do&nbsp;not&nbsp;disable   |
| Microsoft Account Sign-in Assistant      | wlidsvc                                 | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| Microsoft App-V Client                   | AppVClient                              | Disabled  | ✅&nbsp;Already&nbsp;disabled   |
| Microsoft Defender Antivirus Network Inspection Service | WdNisSvc                 | Manual    | ⛔&nbsp;Do&nbsp;not&nbsp;disable     |
| Microsoft Defender Antivirus Service     | WinDefend                               | Automatic | ⛔&nbsp;Do&nbsp;not&nbsp;disable     |
| Microsoft Edge Elevation Service         | MicrosoftEdgeElevationService           | Automatic | 🟡&nbsp;No&nbsp;guidance       |
| Microsoft Edge Update Service            | edgeupdate                              | Automatic (Delayed Start) | ⛔&nbsp;Do&nbsp;not&nbsp;disable   |
| Microsoft Edge Update Service (edgeupdatem)| edgeupdatem                           | Manual    | ⛔&nbsp;Do&nbsp;not&nbsp;disable     |
| Microsoft iSCSI Initiator Service        | MSiSCSI                                 | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| Microsoft Keyboard Filter                | MsKeyboardFilter                        | Manual    | 🟡&nbsp;No&nbsp;guidance       |
| Microsoft Passport                       | NgcSvc                                  | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| Microsoft Passport Container             | NgcCtnrSvc                              | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| Microsoft Software Shadow Copy Provider  | swprv                                   | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| Microsoft Storage Spaces SMP             | smphost                                 | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| Microsoft Store Install Service          | InstallService                          | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| Microsoft Windows SMS Router Service     | SmsRouter                               | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| Natural Authentication                   | NaturalAuthentication                   | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| Net.Tcp Port Sharing Service             | NetTcpPortSharing                       | Disabled  | ✅&nbsp;Already&nbsp;disabled   |
| Netlogon                                 | Netlogon                                | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| Network Connected Devices Auto-Setup     | NcdAutoSetup                            | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| Network Connection Broker                | NcbService                              | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| Network Connections                      | Netman                                  | Manual    | ⛔&nbsp;Do&nbsp;not&nbsp;disable     |
| Network Connectivity Assistant           | NcaSvc                                  | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| Network List Service                     | netprofm                                | Manual    | 🟡&nbsp;No&nbsp;guidance       |
| Network Location Awareness               | NlaSvc                                  | Automatic | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| Network Setup Service                    | NetSetupSvc                             | Manual    | ⛔&nbsp;Do&nbsp;not&nbsp;disable     |
| Network Store Interface Service          | nsi                                     | Automatic | 🟡&nbsp;No&nbsp;guidance       |
| Offline Files                            | CscService                              | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| OpenSSH Authentication Agent             | ssh-agent                               | Disabled  | ✅&nbsp;Already&nbsp;disabled   |
| Optimize drives                          | defragsvc                               | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| Parental Controls                        | WpcMonSvc                               | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| Payments and NFC/SE Manager              | SEMgrSvc                                | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| Peer Name Resolution Protocol            | PNRPsvc                                 | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| Peer Networking Grouping                 | p2psvc                                  | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| Peer Networking Identity Manager         | p2pimsvc                                | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| Performance Counter DLL Host             | PerfHost                                | Manual    | ⛔&nbsp;Do&nbsp;not&nbsp;disable     |
| Performance Logs & Alerts                | pla                                     | Manual    | ⛔&nbsp;Do&nbsp;not&nbsp;disable     |
| Phone Service                            | PhoneSvc                                | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| Plug and Play                            | PlugPlay                                | Manual    | 🟡&nbsp;No&nbsp;guidance       |
| PNRP Machine Name Publication Service    | PNRPAutoReg                             | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| Portable Device Enumerator Service       | WPDBusEnum                              | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| Power                                    | Power                                   | Automatic | ⛔&nbsp;Do&nbsp;not&nbsp;disable     |
| Print Spooler                            | Spooler                                 | Automatic | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| Printer Extensions and Notifications     | PrintNotify                             | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| Problem Reports and Solutions Control Panel Support| wercplsupport                 | Manual    | 🟡&nbsp;No&nbsp;guidance       |
| Program Compatibility Assistant Service  | PcaSvc                                  | Automatic | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| Quality Windows Audio Video Experience   | QWAVE                                   | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| Radio Management Service                 | RmSvc                                   | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| Recommended Troubleshooting Service      | TroubleshootingSvc                      | Manual    | 🟡&nbsp;No&nbsp;guidance       |
| Remote Access Auto Connection Manager    | RasAuto                                 | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| Remote Access Connection Manager         | RasMan                                  | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| Remote Desktop Configuration             | SessionEnv                              | Manual    | ⛔&nbsp;Do&nbsp;not&nbsp;disable     |
| Remote Desktop Services                  | TermService                             | Manual    | ⛔&nbsp;Do&nbsp;not&nbsp;disable     |
| Remote Desktop Services UserMode Port Redirector| UmRdpService                     | Manual    | ⛔&nbsp;Do&nbsp;not&nbsp;disable     |
| Remote Procedure Call (RPC)              | RpcSs                                   | Automatic | ⛔&nbsp;Do&nbsp;not&nbsp;disable     |
| Remote Procedure Call (RPC) Locator      | RpcLocator                              | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| Remote Registry                          | RemoteRegistry                          | Automatic | ⛔&nbsp;Do&nbsp;not&nbsp;disable     |
| Retail Demo Service                      | RetailDemo                              | Automatic | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| Routing and Remote Access                | RemoteAccess                            | Disabled  | ✅&nbsp;Already&nbsp;disabled   |
| RPC Endpoint Mapper                      | RpcEptMapper                            | Automatic | ⛔&nbsp;Do&nbsp;not&nbsp;disable     |
| Secondary Logon                          | seclogon                                | Manual    | ⛔&nbsp;Do&nbsp;not&nbsp;disable     |
| Secure Socket Tunneling Protocol Service | SstpSvc                                 | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| Security Accounts Manager                | SamSs                                   | Automatic | ⛔&nbsp;Do&nbsp;not&nbsp;disable     |
| Security Center                          | wscsvc                                  | Manual    | ⛔&nbsp;Do&nbsp;not&nbsp;disable     |
| Sensor Data Service                      | SensorDataService                       | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| Sensor Monitoring Service                | SensrSvc                                | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| Sensor Service                           | SensorService                           | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| Server                                   | LanmanServer                            | Automatic | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| Shared PC Account Manager                | shpamsvc                                | Automatic | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| Shell Hardware Detection                 | ShellHWDetection                        | Automatic | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| Smart Card                               | SCardSvr                                | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| Smart Card Device Enumeration Service    | ScDeviceEnum                            | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| Smart Card Removal Policy                | SCPolicySvc                             | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| SNMP Trap                                | SNMPTRAP                                | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| Software Protection                      | sppsvc                                  | Automatic | ⛔&nbsp;Do&nbsp;not&nbsp;disable     |
| Spatial Data Service                     | SharedRealitySvc                        | Manual    | ⛔&nbsp;Do&nbsp;not&nbsp;disable     |
| Spot Verifier                            | svsvc                                   | Manual    | ⛔&nbsp;Do&nbsp;not&nbsp;disable     |
| SSDP Discovery                           | SSDPSRV                                 | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| State Repository Service                 | StateRepository                         | Manual    | ⛔&nbsp;Do&nbsp;not&nbsp;disable     |
| Still Image Acquisition Events           | WiaRpc                                  | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| Storage Service                          | StorSvc                                 | Automatic (Delayed Start) | 🟡&nbsp;No&nbsp;guidance|
| Storage Tiers Management                 | TieringEngineService                    | Manual    | 🟡&nbsp;No&nbsp;guidance       |
| Sync Host                                | OneSyncSvc                              | Automatic | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| SysMain                                  | SysMain                                 | Automatic | ⛔&nbsp;Do&nbsp;not&nbsp;disable     |
| System Event Notification Service        | SENS                                    | Automatic | 🟡&nbsp;No&nbsp;guidance       |
| System Events Broker                     | SystemEventsBroker                      | Automatic | ⛔&nbsp;Do&nbsp;not&nbsp;disable     |
| System Guard Runtime Monitor Broker      | SgrmBroker                              | Automatic (Delayed Start) | ⛔&nbsp;Do&nbsp;not&nbsp;disable   |
| Task Scheduler                           | Schedule                                | Automatic | ⛔&nbsp;Do&nbsp;not&nbsp;disable     |
| TCP/IP NetBIOS Helper                    | lmhosts                                 | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| Telephony                                | TapiSrv                                 | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| Themes                                   | Themes                                  | Automatic | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| Time Broker                              | TimeBrokerSvc                           | Manual    | ⛔&nbsp;Do&nbsp;not&nbsp;disable     |
| Touch Keyboard and Handwriting Panel Service| TabletInputService                   | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| Udk User Service                         | UdkUserSvc                              | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| Update Orchestrator Service for Windows Update| UsoSvc                             | Manual    | ⛔&nbsp;Do&nbsp;not&nbsp;disable     |
| UPnP Device Host                         | upnphost                                | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| User Data Access                         | UserDataSvc                             | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| User Data Storage                        | UnistoreSvc                             | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| User Experience Virtualization Service   | UevAgentService                         | Disabled  | ✅&nbsp;Already&nbsp;disabled   |
| User Manager                             | UserManager                             | Automatic | ⛔&nbsp;Do&nbsp;not&nbsp;disable     |
| User Profile Service                     | ProfSvc                                 | Automatic | ⛔&nbsp;Do&nbsp;not&nbsp;disable     |
| Virtual Disk                             | vds                                     | Manual    | 🟡&nbsp;No&nbsp;guidance       |
| Volume Shadow Copy                       | VSS                                     | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| Volumetric Audio Compositor Service      | VacSvc                                  | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| WalletService                            | WalletService                           | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| WarpJITSvc                               | WarpJITSvc                              | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| Web Account Manager                      | TokenBroker                             | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| Web Client                               | WebClient                               | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| Wi-Fi Direct Services Connection Manager | WFDSConMgrSvc                           | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| Windows Audio                            | Audiosrv                                | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| Windows Audio Endpoint Builder           | AudioEndpointBuilder                    | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| Windows Backup                           | SDRSVC                                  | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| Windows Biometric Service                | WbioSrvc                                | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| Windows Camera Frame Server              | FrameServer                             | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| Windows Connect Now - Config Registrar   | Wcncsvc                                 | Automatic | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| Windows Connection Manager               | Wcmsvc                                  | Automatic | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| Windows Defender Advanced Threat Protection Service | WdNisSvc                     | Manual    | ⛔&nbsp;Do&nbsp;not&nbsp;disable     |
| Windows Defender Firewall                | mpssvc                                  | Manual    | ⛔&nbsp;Do&nbsp;not&nbsp;disable     |
| Windows Encryption Provider Host Service | WEPHOSTSVC                              | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| Windows Error Reporting Service          | WerSvc                                  | Manual    | ⛔&nbsp;Do&nbsp;not&nbsp;disable     |
| Windows Event Collector                  | Wecsvc                                  | Manual    | ⛔&nbsp;Do&nbsp;not&nbsp;disable     |
| Windows Event Log                        | EventLog                                | Automatic | ⛔&nbsp;Do&nbsp;not&nbsp;disable     |
| Windows Font Cache Service               | FontCache                               | Automatic | ⛔&nbsp;Do&nbsp;not&nbsp;disable     |
| Windows Image Acquisition (WIA)          | stisvc                                  | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| Windows Insider Service                  | wisvc                                   | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| Windows Installer                        | msiserver                               | Manual    | ⛔&nbsp;Do&nbsp;not&nbsp;disable     |
| Windows License Manager Service          | LicenseManager                          | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| Windows Management Instrumentation       | Winmgmt                                 | Automatic | ⛔&nbsp;Do&nbsp;not&nbsp;disable     |
| Windows Management Service               | WManSvc                                 | Manual    | ⛔&nbsp;Do&nbsp;not&nbsp;disable     |
| Windows Media Player Network Sharing Service | WMPNetworkSvc                       | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| Windows Mobile Hotspot Service           | icssvc                                  | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| Windows Modules Installer                | TrustedInstaller                        | Manual    | ⛔&nbsp;Do&nbsp;not&nbsp;disable     |
| Windows Perception Service               | spectrum                                | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| Windows Perception Simulation Service    | perceptionsimulation                    | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| Windows Push Notifications System Service| WpnService                              | Automatic | ⛔&nbsp;Do&nbsp;not&nbsp;disable     |
| Windows Push Notifications User Service  | WpnUserService                          | Manual    | ⛔&nbsp;Do&nbsp;not&nbsp;disable     |
| Windows PushToInstall Service            | PushToInstall                           | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| Windows Remote Management (WS-Management)| WinRM                                   | Automatic | ⛔&nbsp;Do&nbsp;not&nbsp;disable     |
| Windows Search                           | WSearch                                 | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| Windows Security Service                 | SecurityHealthService                   | Automatic | ⛔&nbsp;Do&nbsp;not&nbsp;disable     |
| Windows Time                             | W32Time                                 | Automatic | ⛔&nbsp;Do&nbsp;not&nbsp;disable     |
| Windows Update                           | wuauserv                                | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| Windows Update Medic Service             | WaaSMedicSvc                            | Manual    | ⛔&nbsp;Do&nbsp;not&nbsp;disable     |
| WinHTTP Web Proxy Auto-Discovery Service | WinHttpAutoProxySvc                     | Manual    | ⛔&nbsp;Do&nbsp;not&nbsp;disable     |
| Wired AutoConfig                         | dot3svc                                 | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| WLAN Autoconfig                          | WLANSVC                                 | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| WMI Performance Adapter                  | wmiApSrv                                | Manual    | ⛔&nbsp;Do&nbsp;not&nbsp;disable     |
| Work Folders                             | workfolderssvc                          | Automatic | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| Workstation                              | LanmanWorkstation                       | Automatic | ⛔&nbsp;Do&nbsp;not&nbsp;disable     |
| WWAN AutoConfig                          | WwanSvc                                 | Manual    | 🟢&nbsp;OK&nbsp;to&nbsp;disable      |
| Xbox Accessory Management Service        | XblAuthManager                          | Manual    | 🔵&nbsp;Should&nbsp;be&nbsp;disabled |
| Xbox Live Auth Manager                   | XblAuthManager                          | Manual    | 🔵&nbsp;Should&nbsp;be&nbsp;disabled |
| Xbox Live Game Save                      | XblGameSave                             | Manual    | 🔵&nbsp;Should&nbsp;be&nbsp;disabled |
| Xbox Live Networking Service             | XboxNetApiSvc                           | Manual    | 🔵&nbsp;Should&nbsp;be&nbsp;disabled |

## More Resources

- [Per-user Services](/windows/application-management/per-user-services-in-windows)
- [Service Host based Services](/windows/application-management/svchost-service-refactoring)
- [Guidance on disabling syestem services on Windows Server](/windows-server/security/windows-services/security-guidelines-for-disabling-system-services-in-windows-server)
