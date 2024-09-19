---
title: What's new in Windows 11 IoT Enterprise, version 24H2?
titleSuffix: Windows IoT Enterprise
description: Learn about new and updated features that are of interest to device makers and IT Pros working with Windows 11 IoT Enterprise, version 24H2.
author: TerryWarwick
ms.author: twarwick
ms.date: 07/25/2024
ms.topic: article
ms.service: windows-iot
ms.subservice: iot
keywords: Windows IoT Enterprise, Windows 11, Windows 11 IoT, Windows 11 IoT Enterprise
---

# What's new in Windows 11 IoT Enterprise, version 24H2

Windows 11 IoT Enterprise, version 24H2 is a feature update for Windows 11 IoT Enterprise. Windows 11 IoT Enterprise, version 24H2 includes all updates to Windows 11 IoT Enterprise, version 23H2 plus some new and updated features. This article lists the new and updated features valuable for IoT scenarios.

Windows 11 IoT Enterprise follows the [Modern Lifecycle Policy](/lifecycle/policies/modern).

| Release Version | Build | Start Date | End&nbsp;of&nbsp;Servicing |
|---------|---------|--------------|----------------------------|
| Windows&nbsp;11&nbsp;IoT&nbsp;Enterprise,&nbsp;version&nbsp;24H2 | 26100 | 2024&#8209;10&#8209;01 | 2027&#8209;10&#8209;12 |

For more information, see [Windows 11 IoT Enterprise support lifecycle](/lifecycle/products/windows-11-iot-enterprise).

## Availability

Windows 11 IoT Enterprise, version 24H2 is available through Windows Update, Windows Server Update Services (including Configuration Manager), the OEM Software Order Center, as well as [volume licensing](https://www.microsoft.com/licensing/terms/productoffering/WindowsDesktopOperatingSystem/all).

To learn more about the status of the update rollout, known issues, and new information, see [Windows release health](/windows/release-health/).

## What's new

### Accessibility

| Feature | Description |
| ------- | ----------- |
| **Bluetooth &#174; Low Energy Audio support for assistive devices** </br> [24H2] | Windows has taken a significant step forward in accessibility by supporting the use of hearing aids equipped with the latest Bluetooth &#174; Low Energy Audio technology. For more information, see [Improving accessibility with Bluetooth &#174; LE Audio](https://blogs.windows.com/windows-insider/2023/10/18/announcing-windows-11-insider-preview-build-25977-canary-channel/). |

### Applications

| Feature | Description |
| ------- | ----------- |
| **File Explorer** </br> [24H2] | The following changes were made to File Explorer context menu: </br> &nbsp;&nbsp;• Support for creating 7-zip and TAR archives </br> &nbsp;&nbsp;• **Compress to** > **Additional options** allows you to compress individual files with gzip, BZip2, xz, or Zstandard </br> &nbsp;&nbsp;• Labels were added to the context menu icons for actions like copy, paste, delete, and rename. |
| **Registry Editor** </br> [24H2] | The Registry Editor supports limiting a search to the currently selected key and its descendants |
| **Remote Desktop Connection improvements** </br> [24H2] | Remote Desktop Connection has the following improvements: </br> &nbsp;&nbsp;• The Remote Desktop Connection setup window (mstsc.exe) follows the text scaling settings under **Settings** > **Accessibility** > **Text size**. </br>&nbsp;&nbsp;• Zoom options of 350, 400, 450, and 500% </br> &nbsp;&nbsp;• Improvements to the connection bar design |
| **Task Manager** </br> [24H2] | The Task Manager settings page has [Mica material](/windows/apps/design/style/mica) and a redesigned icon. |

### Developer

| Feature | Description |
| ------- | ----------- |
| **Power Grid Forecast** </br> [24H2] | The [Power Grid Forecast API](/uwp/api/windows.devices.power.powergridforecast) was introduced. App developers can minimize environmental impact by shifting background workloads to times when renewable energy is available to the local grid. Forecast data isn't available globally and quality of data may vary by region. |
| **Energy saver notification callback** </br> [24H2] | Added an energy saver notification callback setting GUID to represent the new energy saver experience. Apps can subscribe to the energy saver status by passing the appropriate GUID to the PowerSettingRegisterNotification API and can implement different behaviors to optimize energy or performance depending on the current energy saver status. For more information, see [Power Setting GUIDs](/windows/win32/power/power-setting-guids) |
| **Effective Power Mode** </br> [24H2] | Extended the [Effective Power Mode API](/windows/win32/api/powersetting/ne-powersetting-effective_power_mode) to interpret the new energy saver levels when determining the returned effective power mode. |

### Networking

| Feature | Description |
| ------- | ----------- |
| **Wi-Fi 7 consumer access points** </br> [24H2] | Support for Wi-Fi 7 consumer access points offers unprecedented speed, reliability, and efficiency for wireless devices.  For more information, see the Win-Fi 7 announcements from [Wi-Fi Alliance](https://www.wi-fi.org/discover-wi-fi/wi-fi-certified-7) and the [Windows Insider](https://blogs.windows.com/windows-insider/2024/02/22/announcing-windows-11-insider-preview-build-26063-canary-channel/). |
| **Windows location improvements** </br> [24H2] | New controls were added to help manage which apps have access to the list of Wi-Fi networks around you, which could be used to determine your location.  You can view and modify which apps can access the list of Wi-Fi networks from **Settings** > **Privacy & security** > **Location**. A new prompt appears the first time an app attempts to access your location or Wi-Fi information. Developers can use the [Changes to API behavior for Wi-Fi access and location](/windows/win32/nativewifi/wi-fi-access-location-changes) article to learn about API surfaces impacted by this change. |

### Management

| Feature | Description |
| ------- | ----------- |
| **Sudo for Windows** </br> [24H2] | Sudo for Windows is a new way for users to run elevated commands (as an administrator) directly from an unelevated console session. For more information, see [Sudo for Windows](/windows/sudo/). |

### Security

| Feature | Description |
| ------- | ----------- |
| **App Control for Business** </br> [24H2]<!--8223790--> | Customers can now use App Control for Business (formerly called Windows Defender Application Control) and its next-generation capabilities to protect their digital property from malicious code. With App Control for Business, IT teams can configure what runs in a business environment through Microsoft Intune or other MDMs in the admin console, including setting up Intune as a managed installer. For more information, see [Application Control for Windows](/windows/security/application-security/application-control/app-control-for-business/appcontrol).|
| **Local Security Authority (LSA) protection** </br> [24H2] |  [LSA protection](/windows-server/security/credentials-protection-and-management/configuring-additional-lsa-protection) helps protect against theft of secrets and credentials used for logon by preventing unauthorized code from running in the LSA process and by preventing dumping of process memory. An audit occurs for incompatibilities with LSA protection for a period of time, starting with this upgrade. If incompatibilities aren't detected, LSA protection is automatically enabled. You can check and change the enablement state of LSA protection in the Windows Security application under the **Device Security** > **Core Isolation** page. In the event log, LSA protection records whether programs are blocked from loading into LSA. If you would like to check if something was blocked, review the [logging](/windows-server/security/credentials-protection-and-management/configuring-additional-lsa-protection#identify-plug-ins-and-drivers-that-lsassexe-fails-to-load). |
| **SHA-3 support** </br> [24H2] | We are adding support for the SHA-3 family of hash functions and SHA-3 derived functions (SHAKE, cSHAKE, KMAC). The SHA-3 family of algorithms are the latest standardized hash functions by the National Institute of Standards and Technology (NIST). Support for these functions is enabled through the Windows [CNG](/windows/win32/seccng/cng-portal) library. </br></br>**Supported SHA-3 hash functions**: </br> SHA3-256, SHA3-384, SHA3-512 (SHA3-224 isn't supported).</br></br>**Supported SHA-3 HMAC algorithms** </br> HMAC-SHA3-256, HMAC-SHA3-384, HMAC-SHA3-512 </br></br>**Supported SHA-3 derived algorithms** </br> extendable-output functions (XOF) (SHAKE128, SHAKE256), customizable XOFs (cSHAKE128, cSHAKE256), and KMAC (KMAC128, KMAC256, KMACXOF128, KMACXOF256). |
| **SMB** </br> Firewall rule changes </br> [24H2] | The Windows Firewall [default behavior has changed](/windows-server/storage/file-server/smb-secure-traffic#updated-firewall-rules-preview). Creating an SMB share automatically configures the new **File and Printer Sharing (Restrictive)** group, which no longer contains inbound NetBIOS ports 137-139 as its default. This change enforces a higher degree  of network security as well as bringing SMB firewall rules closer to the Windows Server **File Server** role behavior, which only opens the minimum ports needed to connect and manage sharing. For more information about this change, see [https://aka.ms/SMBfirewall](https://techcommunity.microsoft.com/t5/storage-at-microsoft/smb-firewall-rule-changes-in-windows-insider/ba-p/3974496). |
| **SMB** </br> NTLM blocking exception list </br> [24H2] | The SMB client now supports [blocking NTLM](/windows-server/storage/file-server/smb-ntlm-blocking) for remote outbound connections. With this new option, administrators can intentionally block Windows from offering NTLM via SMB and specify exceptions for NTLM usage. An attacker who tricks a user or application into sending NTLM challenge responses to a malicious server will no longer receive any NTLM data and cannot brute force, crack, or pass hashes. This adds a new level of protection for enterprises without a requirement to entirely disable NTLM usage in the OS. For more information about this change, see [https://aka.ms/SmbNtlmBlock](https://techcommunity.microsoft.com/t5/storage-at-microsoft/smb-ntlm-blocking-now-supported-in-windows-insider/ba-p/3916206). |
| **SMB** </br> Alternative client and server ports </br> [24H2] | The SMB client now supports connecting to an SMB server over TCP, QUIC, or RDMA using [alternative network ports](/windows-server/storage/file-server/smb-ports) to the hardcoded defaults. Windows Server doesn't support configuring alternative SMB server TCP ports, but some third parties do. This is part of a campaign to improve the security of Windows and Windows Server for the modern landscape. For more information about this change, see [https://aka.ms/SMBAlternativePorts](https://techcommunity.microsoft.com/t5/storage-at-microsoft/smb-alternative-ports-now-supported-in-windows-insider/ba-p/3974509). |
| **SMB** </br> Dialect management </br> [24H2] | The SMB server now supports controlling which [SMB 2 and 3 dialects](/windows-server/storage/file-server/manage-smb-dialects) it negotiates. For more information about this change, see [https://aka.ms/SmbDialectManage](https://techcommunity.microsoft.com/t5/storage-at-microsoft/smb-dialect-management-now-supported-in-windows-insider/ba-p/3916368). |
| **SMB** </br> Signing requirement changes </br> [24H2] | In Windows 11, version 24H2, [SMB signing](/windows-server/storage/file-server/smb-signing) is now required by default for all connections. For more information about SMB signing being required by default, see [https://aka.ms/SMBSigningOBD](https://techcommunity.microsoft.com/t5/storage-at-microsoft/smb-signing-required-by-default-in-windows-insider/ba-p/3831704). |
| **SMB** </br> Client encryption </br> [24H2] | SMB now supports [requiring encryption](/windows-server/storage/file-server/smb-security) on all outbound SMB client connections. With this new option, administrators can mandate that all destination servers use SMB 3 and encryption, and if missing those capabilities, the client won't connect. For more information about this change, see [https://aka.ms/SmbClientEncrypt](https://techcommunity.microsoft.com/t5/storage-at-microsoft/smb-client-encryption-mandate-now-supported-in-windows-insider/ba-p/3964037). |
| **SMB** </br> Signing and encryption auditing </br> [24H2] | Administrators can now [enable auditing](/windows-server/storage/file-server/smb-signing-overview#smb-signing-and-encryption-auditing) of the SMB server and client for support of SMB signing and encryption. To configure SMB client or server signing or encryption auditing using Group Policy. For more information about SMB network security, see [Secure SMB Traffic in Windows Server](/windows-server/storage/file-server/smb-secure-traffic). |
| **SMB over QUIC** </br> Client access control </br> [24H2] | [SMB over QUIC](/windows-server/storage/file-server/smb-over-quic) now supports additional [access control options](/windows-server/storage/file-server/configure-smb-over-quic-client-access-control) for clients. This change improves the existing SMB over QUIC feature, which introduced an alternative to the TCP network transport, providing secure, reliable connectivity to edge file servers over untrusted networks like the Internet. For more information about this change, see [https://aka.ms/SmbOverQUICCAC](/windows-server/storage/file-server/configure-smb-over-quic-client-access-control). |
| **SMB over QUIC** </br> Client disable </br> [24H2] | Administrators can now [disable the SMB over QUIC](/windows-server/storage/file-server/configure-smb-over-quic-client-access-control#disable-smb-over-quic) for client with Group Policy and PowerShell. To disable SMB over QUIC using PowerShell, use `Set-SmbClientConfiguration -EnableSMBQUIC $false`. To disable SMB over QUIC using Group Policy, use the **Computer Configuration** > **Administrative Templates** > **Network** > **Lanman Workstation** > **Enable SMB over QUIC** policy. |
| **SMB over QUIC** </br> Client connection auditing </br> [24H2] | Successful [SMB over QUIC client connection events](/windows-server/storage/file-server/smb-over-quic#smb-over-quic-client-auditing) are now written to the event log to include the QUIC transport. You can view these events using Event Viewer under the following path: </br> **Applications and Services Logs** > **Microsoft** > **Windows** > **SMBClient** > **Connectivity**; Event ID = 30832. |
| **Windows&nbsp;LAPS** </br> Automatic account management </br> [24H2] | [Windows Local Administrator Password Solution (LAPS)](/windows-server/identity/laps/laps-overview) has a new automatic account management feature. Admins can configure Windows LAPS to:</br>&nbsp;&nbsp;• Automatically create the managed local account</br>&nbsp;&nbsp;• Configure name of account</br>&nbsp;&nbsp;• Enable or disable the account</br>&nbsp;&nbsp;• Randomize the name of the account |
| **Windows&nbsp;LAPS** </br> Policy improvements </br> [24H2]| &nbsp;&nbsp;• Added passphrase settings for the [PasswordComplexity](/windows/client-management/mdm/laps-csp#policiespasswordcomplexity) policy </br> &nbsp;&nbsp;• Use [PassphraseLength](/windows/client-management/mdm/laps-csp#policiespassphraselength) to control the number of words in a new passphrase </br> &nbsp;&nbsp;• Added an improved readability setting for the [PasswordComplexity](/windows/client-management/mdm/laps-csp#policiespasswordcomplexity) policy, which generates passwords without using characters that are easily confused with another character. For example, the <kbd>0</kbd> (zero) and the letter <kbd>O</kbd> aren't used in the password since the characters can be confused. </br>&nbsp;&nbsp;• Added the `Reset the password, logoff the managed account, and terminate any remaining processes` setting to the [PostAuthenticationActions](/windows/client-management/mdm/laps-csp#policiespostauthenticationactions) policy. The event logging messages that are emitted during post-authentication-action execution were also expanded, to give insights into exactly what was done during the operation. |
| **Windows&nbsp;LAPS** </br> Image rollback detection </br> [24H2] | Image rollback detection was introduced for LAPS. LAPS can detect when a device was rolled back to a previous image. When a device is rolled back, the password in Active Directory might not match the password on the device that was rolled back. This new feature adds an Active Directory attribute, `msLAPS-CurrentPasswordVersion`, to the [Windows LAPS schema](/windows-server/identity/laps/laps-technical-reference#mslaps-currentpasswordversion). This attribute contains a random GUID that Windows LAPS writes every time a new password is persisted in Active Directory, followed by saving a local copy. During every processing cycle, the GUID stored in `msLAPS-CurrentPasswordVersion` is queried and compared to the locally persisted copy. If the GUIDs are different, the password is immediately rotated. To enable this feature, you need to run the latest version of the [Update-LapsADSchema PowerShell cmdlet](/powershell/module/laps/update-lapsadschema). |
| **Windows protected print mode** </br> [24H2] | Windows protected print mode (WPP) enables a modern print stack which is designed to work exclusively with [Mopria certified printers](https://mopria.org/certified-products). For more information, see [What is Windows protected print mode (WPP)](https://techcommunity.microsoft.com/t5/security-compliance-and-identity/a-new-modern-and-secure-print-experience-from-windows/ba-p/4002645) and [Windows Insider WPP announcement](https://blogs.windows.com/windows-insider/2023/12/13/announcing-windows-11-insider-preview-build-26016-canary-channel/). |

### Servicing

| Feature | Description |
| ------- | ----------- |
| **Checkpoint cumulative updates** </br> [24H2] | Windows quality updates are provided as cumulative updates throughout the life cycle of a Windows release.  Checkpoint cumulative updates introduce periodic baselines that reduce the size of future cumulative updates making the distribution of monthly quality updates more efficient.  For more information, see [https://aka.ms/CheckpointCumulativeUpdates](https://techcommunity.microsoft.com/t5/windows-it-pro-blog/introducing-windows-11-checkpoint-cumulative-updates/ba-p/4182552). |

## Features Removed

The following [deprecated features](/windows/deprecated-features.md) are removed in Windows 11, version 24H2:

| Feature | Description |
|---------|-------------|
| **WordPad** </br> [24H2]| WordPad is removed from all editions of Windows starting in Windows 11, version 24H2 and Windows Server 2025. <!--8254696, 8494641--> |
| **Alljoyn** </br> [24H2] | Microsoft's implementation of AllJoyn, which included the [Windows.Devices.AllJoyn API namespace](/uwp/api/windows.devices.alljoyn), a [Win32 API](/windows/win32/api/_alljoyn/), a [management configuration service provider (CSP)](/windows/client-management/mdm/alljoynmanagement-csp), and an [Alljoyn Router Service](/windows-server/security/windows-services/security-guidelines-for-disabling-system-services-in-windows-server#alljoyn-router-service) is retired.<!--8396030--> |

## Related articles

- Windows Experience Blog: How to get the Windows 11 2024 Update
- Windows IT Pro Blog: What’s new for IT pros in Windows 11, version 24H2
- [What's new in Windows 11, version 24H2](/windows/whats-new/whats-new-windows-11-version-24h2)
- [Windows Consumer: What's new in recent Windows updates](https://support.microsoft.com/windows/what-s-new-in-recent-windows-updates-2df971e0-341a-68b1-3bf8-bc3e3ff8c3a5)
- [Windows 11 requirements](/windows/whats-new/windows-11-requirements)
- [Plan for Windows 11](/windows/whats-new/windows-11-plan)
- [Prepare for Windows 11](/windows/whats-new/windows-11-prepare)
- [Windows release health](https://aka.ms/windowsreleasehealth)
- [Windows 11 release information](/windows/release-health/windows11-release-information)
