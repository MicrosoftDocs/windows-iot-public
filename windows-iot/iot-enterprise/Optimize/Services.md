---
title: Guidance on disabling system services on Windows IoT Enterprise
author: TerryWarwick
ms.author: twarwick
ms.date: 3/28/2021
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: Security guidelines for disabling services in Windows IoT Enterprise
keywords: IoT Enterprise, Security, services
---
# Guidance on disabling system services on Windows IoT Enterprise

**Applies to:**

- Windows 10 IoT Enterprise
- Windows 11 IoT Enterprise

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


For all system services listed in this document, Microsoft provides guidance the two tables that follow offer an explanation of columns and Microsoft recommendations for enabling and disabling system services in Windows IoT Enterprise.

**Explanation of Microsoft recommendations**

- **No guidance:** The impact of disabling these services has not been fully evaluated. Therefore, the default configuration of these services should not be changed. 
- **Do not disable:** Disabling this service will impact essential functionality or prevent specific roles or features from functioning correctly. Therefore it should not be disabled.
- **OK to disable:** This service provides functionality that is useful to some but not all enterprises, and security-focused enterprises that don't use it can safely disable it.
- **Already disabled:** This service is disabled by default; no need to enforce with policy.
- **Should be disabled:** This service should never be enabled on a well-managed enterprise system.

The following table offer Microsoft guidance on disabling system services on Windows IoT Enterprise:

| Name | Service Name | Startup Type | Recommendation |
|--|--|--|--|
| ActiveX Installer                       | AxInstSV                 | Manual    | OK to Disable    |
| Agent Activation runtime                | AarSvc                   | Manual    | Do not disable   |
| AllJoyn Router Service                  | AJRouter                 | Manual    | OK to disable    |
| App Readiness                           | AppReadiness             | Manual    | Do not disable   |
| Application Identity                    | AppIDSvc                 | Manual    | Do not disable   |
| Application Information                 | Appinfo                  | Manual    | Do not disable   |
| Application Layer Gateway Service       | ALG                      | Manual    | OK to disable    |
| Application Management                  | AppMgmt                  | Manual    | OK to disable    |
| AppX Deployment Service (AppXSVC)       | AppXSvc                  | Manual    | OK to disable    |
| AssignedAccessManager Service           | AssignedAccessManagerSvc | Manual    | Do not disable   |
| Auto Time Zone Updater                  | tzautoupdate             | Disabled  | Already disabled |
| AVCTP Service                           | BthAvctpSvc              | Manual    | OK to disable    |
| Background Intelligent Transfer Service | BITS                     | Manual    | OK to disable    |
| Background Tasks Infrastructure Service | BrokerInfrastructure     | Automatic | Do not disable   |
| Base Filtering Engine                   | BFE                      | Automatic | Do not disable   |
| BitLocker Drive Encryption Service      | BDESVC                   | Manual    | Do not disable   |
| Block Level Backup Engine Service       | wbengine                 | Manual    | No Guidance      |
| Bluetooth Audio Gateway Service         | BTAGService              | Manual    | OK to disable    |
| Bluetooth Support Service               | bthserv                  | Manual    | OK to disable    |
| Bluetooth User Support Service          | BluetoothUserService     | Manual    | OK to disable    |
| BranchCache                             | PeerDistSvc              | Manual    | OK to disable    |
| Capability Access Manager Service       | camsvc                   | Manual    | OK to disable    |
| Capture Service                         | CaptureService           | Manual    | OK to disable    |
| Cellular Time                           | autotimesvc              | Manual    | OK to disable    |
| Certificate Propagation                 | CertPropSvc              | Manual    | Do not disable   |
| Client License Service (ClipSVC)        | ClipSVC                  | Manual    | OK to disable    |
| Clipboard User Service                  | cbdhsvc                  | Manual    | OK to disable    |
| CNG Key Isolation                       | KeyIso                   | Manual    | Do not disable   |
| COM+ Event System                       | EventSystem              | Automatic | Do not disable   |
| COM+ System Application                 | COMSysApp                | Manual    | Do not disable   |
| Connected Devices Platform Service      | CDPSvc                   | Automatic | OK to disable    |
| Connected Devices Platform User Service | CDPUserSvc               | Automatic | OK to disable    |
| Connected User Experiences and Telemetry | DiagTrack                | Automatic | OK to disable    |
| ConsentUX                                | ConsentUxUserSvc         | Manual    | OK to disable    |
| Contact Data                             | PimIndexMaintenanceSvc   | Manual    | OK to disable    |
| CoreMessaging                            | CoreMessagingRegistrar   | Automatic | Do not disable   |
| Credential Manager                       | VaultSvc                 | Manual    | Do not disable   |
| Credential Enrollment Manager            |CredentialEnrollmentManagerUserSvc | Manual    | Do not disable   |
| Cryptographic Services                   | CryptSvc                 | Automatic | Do not disable   |
| Data Sharing Service                     | DsSvc                    | Manual    | Do not disable   |
| Data Usage                               | DusmSvc                  | Automatic | Do not disable   |
| DCOM Server Process Launcher             | DcomLaunch               | Automatic | Do not disable   |
| Delivery Optimization                    | DoSvc                    | Automatic | Do not disable   |
| Device Association Service               | DeviceAssociationService | Manual    | OK to disable    |
| Device Install Service                   | DeviceInstall            | Manual    | Do not disable   |
| Device Management Enrollment Service     | DmEnrollmentSvc          | Manual    | No guidance |
| Device Management Wireless Application Protocol (WAP) Push message Routing Service| dmwappushservic | Manual    | No guidance |
| Device Setup Manager                     | DsmSvc                   | Manual    | Do not disable   |
| DevicePicker                             | DevicePickerUserSvc      | Manual    | OK to disable    |
| DevicesFlow                              | DevicesFlowUserSvc       | Manual    | OK to disable    |
| DevQuery Background Discovery Broker     | DevQueryBroker           | Manual    | Do not disable   |
| DHCP Client                              | Dhcp                     | Automatic | Do not disable   |
| Diagnostic Execution Service             | diagsvc                  | Manual    | Do not disable   |
| Diagnostic Policy Service                | DPS                      | Automatic | Do not disable   |
| Diagnostic Service Host                  | WdiServiceHost           | Manual    | Do not disable   |
| Diagnostic System Host                   | WdiSystemHost            | Manual    | Do not disable   |
| Dialog Blocking Service                  | DialogBlockingService    | Disabled  | Already disabled |
| Display Enhancement Service              | DisplayEnhancementService | Manual    | Do not disable   |
| Display Policy Service                   | DispBrokerDesktopSvc     | Automatic | Do not disable   |
| Distributed Link Tracking Client         | TrkWks                   | Automatic | OK to disable    |
| Distributed Transaction Coordinator      | MSDTC                    | Automatic | OK to disable    |
| DNS Client                               | Dnscache                 | Automatic | Do not disable   |
| Downloaded Maps Manager                  | MapsBroker               | Automatic | OK to disable    |
| Embedded Mode                            | embeddedmode             | Manual    | Do not disable   |
| Encrypting File System (EFS)             | EFS                      | Manual    | Do not disable   |
| Enterprise App Management Service        | EntAppSvc                | Manual    | OK to disable    |
| Extensible Authentication Protocol       | EapHost                  | Manual    | OK to disable    |
| Fax                                      | Fax                      | Manual    | OK to disable    |
| File History Service                     | fhsvc                    | Manual    | Do not disable   |
| Function Discovery Provider Host         | fdPHost                  | Manual    | OK to disable    |
| Function Discovery Resource Publication  | FDResPub                 | Manual    | OK to disable    |
| GameDVR and Broadcast User Service       | BcastDVRUserService      | Manual    | OK to disable    |
| Geolocation Service                      | lfsvc                    | Manual    | OK to disable    |
| GraphicsPerfSvc                          | GraphicsPerfSvc          | Manual    | Do not disable   |
| Group Policy Client                      | gpsvc                    | Automatic | Do not disable   |
| Human Interface Device Service           | hidserv                  | Manual    | Do not disable   |
| HV Host Service                          | HvHost                   | Manual    | OK to disable    |
| Hyper-V Data Exchange Service            | vmickvpexchange          | Manual    | OK to disable    |
| Hyper-V Guest Service Interface          | vmicguestinterface       | Manual    | OK to disable    |
| Hyper-V Guest Shutdown Service           | vmicshutdown             | Manual    | OK to disable    |
| Hyper-V Heartbeat Service                | vmicheartbeat            | Manual    | OK to disable    |
| Hyper-V PowerShell Direct Service        | vmicvmsession            | Manual    | OK to disable    |
| Hyper-V Remote Desktop Virtualization Service | vmicrdv             | Manual    | OK to disable    |
| Hyper-V Time Synchronization Service     | vmictimesync             | Manual    | OK to disable    |
| Hyper-V Volume Shadow Copy Requestor     | vmicvss                  | Manual    | OK to disable    |
| IKE and AuthIP IPsec Keying Modules      | IKEEXT                   | Manual    | Do not disable   |
| Internet Connection Sharing (ICS)        | SharedAccess             | Manual    | OK to disable    |
| IP Helper                                | iphlpsvc                 | Automatic | OK to disable    |
| IP Translation Configuration Service     | IpxlatCfgSvc             | Manual    | OK to disable    |
| IPsec Policy Agent                       | PolicyAgent              | Manual    | Do not disable   |
| KtmRm for Distributed Transaction Coordinator| KtmRm                | Manual    | Do not disable   |
| Language Experience Service              | LxpSvc                   | Manual    | Do not disable   |
| Link-Layer Topology Discovery Mapper     | lltdsvc                  | Manual    | OK to disable    |
| Local Profile Assistance Service         | wlpasvc                  | Automatic | OK to disable    |
| Local Session Manager                    | LSM                      | Automatic | Do not disable   |
| Messaging Service                        | MessagingService         | Manual    | OK to disable    |
| Microsoft (R) Diagnostics Hub Standard Collector| diagnosticshub.standardcollector.service | Manual    | Do not disable   |
| Microsoft Account Sign-in Assistant      | wlidsvc                  | Manual    | OK to disable    |
| Microsoft App-V Client                   | AppVClient               | Disabled  | Already disabled |
| Microsoft Defender Antivirus Network Inspection Service | WdNisSvc  | Manual    | Do not disable   |
| Microsoft Defender Antivirus Service     | WinDefend                | Automatic | Do not disable   |
| Microsoft Edge Elevation Service         | MicrosoftEdgeElevationService | Automatic | No guidance |
| Microsoft Edge Update Service            | edgeupdate               | Automatic (Delayed Start) | Do not disable   |
| Microsoft Edge Update Service (edgeupdatem)| edgeupdatem            | Manual    | Do not disable   |
| Microsoft iSCSI Initiator Service        | MSiSCSI                  | Manual    | OK to disable    |
| Microsoft Keyboard Filter                | MsKeyboardFilter         | Manual    | No guidance |
| Microsoft Passport                       | NgcSvc                   | Manual    | OK to disable    |
| Microsoft Passport Container             | NgcCtnrSvc               | Manual    | OK to disable    |
| Microsoft Software Shadow Copy Provider  | swprv                    | Manual    | OK to disable    |
| Microsoft Storage Spaces SMP             | smphost                  | Manual    | OK to disable    |
| Microsoft Store Install Service          | InstallService           | Manual    | OK to disable    |
| Microsoft Windows SMS Router Service     | SmsRouter                | Manual    | OK to disable    |
| Natural Authentication                   | NaturalAuthentication    | Manual    | OK to disable    |
| Net.Tcp Port Sharing Service             | NetTcpPortSharing        | Disabled  | Already disabled |
| Netlogon                                 | Netlogon                 | Manual    | OK to disable    |
| Network Connected Devices Auto-Setup     | NcdAutoSetup             | Manual    | OK to disable    |
| Network Connection Broker                | NcbService               | Manual    | OK to disable    |
| Network Connections                      | Netman                   | Manual    | Do not disable   |
| Network Connectivity Assistant           | NcaSvc                   | Manual    | OK to disable    |
| Network List Service                     | netprofm                 | Manual    | No guidance |
| Network Location Awareness               | NlaSvc                   | Automatic | OK to disable    |
| Network Setup Service                    | NetSetupSvc              | Manual    | Do not disable   |
| Network Store Interface Service          | nsi                      | Automatic | No guidance |
| Offline Files                            | CscService               | Manual    | OK to disable    |
| OpenSSH Authentication Agent             | ssh-agent                | Disabled  | Already disabled |
| Optimize drives                          | defragsvc                | Manual    | OK to disable    |
| Parental Controls                        | WpcMonSvc                | Manual    | OK to disable    |
| Payments and NFC/SE Manager              | SEMgrSvc                 | Manual    | OK to disable    |
| Peer Name Resolution Protocol            | PNRPsvc                  | Manual    | OK to disable    |
| Peer Networking Grouping                 | p2psvc                   | Manual    | OK to disable    |
| Peer Networking Identity Manager         | p2pimsvc                 | Manual    | OK to disable    |
| Performance Counter DLL Host             | PerfHost                 | Manual    | Do not disable   |
| Performance Logs & Alerts                | pla                      | Manual    | Do not disable   |
| Phone Service                            | PhoneSvc                 | Manual    | OK to disable    |
| Plug and Play                            | PlugPlay                 | Manual    | No guidance |
| PNRP Machine Name Publication Service    | PNRPAutoReg              | Manual    | OK to disable    |
| Portable Device Enumerator Service       | WPDBusEnum               | Manual    | OK to disable    |
| Power                                    | Power                    | Automatic | Do not disable   |
| Print Spooler                            | Spooler                  | Automatic | OK to disable    |
| Printer Extensions and Notifications     | PrintNotify              | Manual    | OK to disable    |
| Problem Reports and Solutions Control Panel Support| wercplsupport  | Manual    | No guidance |
| Program Compatibility Assistant Service  | PcaSvc                   | Automatic | OK to disable    |
| Quality Windows Audio Video Experience   | QWAVE                    | Manual    | OK to disable    |
| Radio Management Service                 | RmSvc                    | Manual    | OK to disable    |
| Recommended Troubleshooting Service      | TroubleshootingSvc       | Manual    | No guidance |
| Remote Access Auto Connection Manager    | RasAuto                  | Manual    | OK to disable    |
| Remote Access Connection Manager         | RasMan                   | Manual    | OK to disable    |
| Remote Desktop Configuration             | SessionEnv               | Manual    | Do not disable   |
| Remote Desktop Services                  | TermService              | Manual    | Do not disable   |
| Remote Desktop Services UserMode Port Redirector| UmRdpService      | Manual    | Do not disable   |
| Remote Procedure Call (RPC)              | RpcSs                    | Automatic | Do not disable   |
| Remote Procedure Call (RPC) Locator      | RpcLocator               | Manual    | OK to disable    |
| Remote Registry                          | RemoteRegistry           | Automatic | Do not disable   |
| Retail Demo Service                      | RetailDemo               | Automatic | OK to disable    |
| Routing and Remote Access                | RemoteAccess             | Disabled  | Already disabled |
| RPC Endpoint Mapper                      | RpcEptMapper             | Automatic | Do not disable   |
| Secondary Logon                          | seclogon                 | Manual    | Do not disable   |
| Secure Socket Tunneling Protocol Service | SstpSvc                  | Manual    | Ok to disable |
| Security Accounts Manager                | SamSs                    | Automatic | Do not disable   |
| Security Center                          | wscsvc                   | Manual    | Do not disable   |
| Sensor Data Service                      | SensorDataService        | Manual    | OK to disable    |
| Sensor Monitoring Service                | SensrSvc                 | Manual    | OK to disable    |
| Sensor Service                           | SensorService            | Manual    | OK to disable    |
| Server                                   | LanmanServer             | Automatic | Ok to disable |
| Shared PC Account Manager                | shpamsvc                 | Automatic | Ok to disable |
| Shell Hardware Detection                 | ShellHWDetection         | Automatic | OK to disable    |
| Smart Card                               | SCardSvr                 | Manual    | OK to disable    |
| Smart Card Device Enumeration Service    | ScDeviceEnum             | Manual    | OK to disable    |
| Smart Card Removal Policy                | SCPolicySvc              | Manual    | Ok to disable |
| SNMP Trap                                | SNMPTRAP                 | Manual    | OK to disable    |
| Software Protection                      | sppsvc                   | Automatic | Do not disable   |
| Spatial Data Service                     | SharedRealitySvc         | Manual    | Do not disable   |
| Spot Verifier                            | svsvc                    | Manual    | Do not disable   |
| SSDP Discovery                           | SSDPSRV                  | Manual    | OK to disable    |
| State Repository Service                 | StateRepository          | Manual    | Do not disable   |
| Still Image Acquisition Events           | WiaRpc                   | Manual    | OK to disable    |
| Storage Service                          | StorSvc                  | Automatic (Delayed Start) | No guidance |
| Storage Tiers Management                 | TieringEngineService     | Manual    | No guidance |
| Sync Host                                | OneSyncSvc               | Automatic | OK to disable    |
| SysMain                                  | SysMain                  | Automatic | Do not disable   |
| System Event Notification Service        | SENS                     | Automatic | No guidance |
| System Events Broker                     | SystemEventsBroker       | Automatic | Do not disable   |
| System Guard Runtime Monitor Broker      | SgrmBroker               | Automatic (Delayed Start) | Do not disable   |
| Task Scheduler                           | Schedule                 | Automatic | Do not disable   |
| TCP/IP NetBIOS Helper                    | lmhosts                  | Manual    | OK to disable    |
| Telephony                                | TapiSrv                  | Manual    | OK to disable    |
| Themes                                   | Themes                   | Automatic | OK to disable    |
| Time Broker                              | TimeBrokerSvc            | Manual    | Do not disable   |
| Touch Keyboard and Handwriting Panel Service| TabletInputService    | Manual    | OK to disable    |
| Udk User Service                         | UdkUserSvc               | Manual    | OK to disable    |
| Update Orchestrator Service for Windows Update| UsoSvc              | Manual    | Do not disable   |
| UPnP Device Host                         | upnphost                 | Manual    | OK to disable    |
| User Data Access                         | UserDataSvc              | Manual    | OK to disable    |
| User Data Storage                        | UnistoreSvc              | Manual    | OK to disable    |
| User Experience Virtualization Service   | UevAgentService          | Disabled  | Already disabled |
| User Manager                             | UserManager              | Automatic | Do not disable   |
| User Profile Service                     | ProfSvc                  | Automatic | Do not disable   |
| Virtual Disk                             | vds                      | Manual    | No guidance |
| Volume Shadow Copy                       | VSS                      | Manual    | OK to disable    |
| Volumetric Audio Compositor Service      | VacSvc                   | Manual    | OK to disable    |
| WalletService                            | WalletService            | Manual    | OK to disable    |
| WarpJITSvc                               | WarpJITSvc               | Manual    | OK to disable    |
| Web Account Manager                      | TokenBroker              | Manual    | OK to disable    |
| Web Client                               | WebClient                | Manual    | OK to disable    |
| Wi-Fi Direct Services Connection Manager | WFDSConMgrSvc            | Manual    | OK to disable    |
| Windows Audio                            | Audiosrv                 | Manual    | OK to disable    |
| Windows Audio Endpoint Builder           | AudioEndpointBuilder     | Manual    | OK to disable    |
| Windows Backup                           | SDRSVC                   | Manual    | OK to disable    |
| Windows Biometric Service                | WbioSrvc                 | Manual    | OK to disable    |
| Windows Camera Frame Server              | FrameServer              | Manual    | OK to disable    |
| Windows Connect Now - Config Registrar   | Wcncsvc                  | Automatic | OK to disable    |
| Windows Connection Manager               | Wcmsvc                   | Automatic | OK to disable    |
| Windows Defender Advanced Threat Protection Service | WdNisSvc      | Manual    | Do not disable   |
| Windows Defender Firewall                | mpssvc                   | Manual    | Do not disable   |
| Windows Encryption Provider Host Service | WEPHOSTSVC               | Manual    | OK to disable    |
| Windows Error Reporting Service          | WerSvc                   | Manual    | Do not disable   |
| Windows Event Collector                  | Wecsvc                   | Manual    | Do not disable   |
| Windows Event Log                        | EventLog                 | Automatic | Do not disable   |
| Windows Font Cache Service               | FontCache                | Automatic | Do not disable   |
| Windows Image Acquisition (WIA)          | stisvc                   | Manual    | OK to disable    |
| Windows Insider Service                  | wisvc                    | Manual    | OK to disable    |
| Windows Installer                        | msiserver                | Manual    | Do not disable   |
| Windows License Manager Service          | LicenseManager           | Manual    | Ok to disable |
| Windows Management Instrumentation       | Winmgmt                  | Automatic | Do not disable   |
| Windows Management Service               | WManSvc                  | Manual    | Do not disable   |
| Windows Media Player Network Sharing Service| WMPNetworkSvc         | Manual    | OK to disable    |
| Windows Mobile Hotspot Service           | icssvc                   | Manual    | OK to disable    |
| Windows Modules Installer                | TrustedInstaller         | Manual    | Do not disable   |
| Windows Perception Service               | spectrum                 | Manual    | Ok to disable |
| Windows Perception Simulation Service    | perceptionsimulation     | Manual    | Ok to disable |
| Windows Push Notifications System Service| WpnService               | Automatic | Do not disable   |
| Windows Push Notifications User Service  | WpnUserService           | Manual    | Do not disable   |
| Windows PushToInstall Service            | PushToInstall            | Manual    | Ok to disable |
| Windows Remote Management (WS-Management)| WinRM                    | Automatic | Do not disable   |
| Windows Search                           | WSearch                  | Manual    | Ok to disable |
| Windows Security Service                 | SecurityHealthService    | Automatic | Do not disable   |
| Windows Time                             | W32Time                  | Automatic | Do not disable   |
| Windows Update                           | wuauserv                 | Manual    | OK to disable    |
| Windows Update Medic Service             | WaaSMedicSvc             | Manual    | Do not disable   |
| WinHTTP Web Proxy Auto-Discovery Service | WinHttpAutoProxySvc      | Manual    | Do not disable   |
| Wired AutoConfig                         | dot3svc                  | Manual    | OK to disable    |
| WLAN Autoconfig                          | WLANSVC                  | Manual    | OK to disable    |
| WMI Performance Adapter                  | wmiApSrv                 | Manual    | Do not disable   |
| Work Folders                             | workfolderssvc           | Automatic | Ok to disable |
| Workstation                              | LanmanWorkstation        | Automatic | Do not disable   |
| WWAN AutoConfig                          | WwanSvc                  | Manual    | OK to disable    |
| Xbox Accessory Management Service        | XblAuthManager           | Manual    | Should be disabled |
| Xbox Live Auth Manager                   | XblAuthManager           | Manual    | Should be disabled |
| Xbox Live Game Save                      | XblGameSave              | Manual    | Should be disabled |
| Xbox Live Networking Service             | XboxNetApiSvc            | Manual    | Should be disabled |

## More Resources
- [Per-user Services](/windows/application-management/per-user-services-in-windows)
- [Service Host based Services](/windows/application-management/svchost-service-refactoring)
- [Guidance on disabling syestem services on Windows Server](/windows-server/security/windows-services/security-guidelines-for-disabling-system-services-in-windows-server)
