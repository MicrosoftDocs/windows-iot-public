---
title: Removable Package: Microsoft-Media-Foundation
author: twarwick
ms.author: twarwick
ms.date: 12/7/2022
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: Removable Package Details for Microsoft-Media-Foundation
keywords: IoT Enterprise, removable packages, storage
---

# Removable Package: Microsoft-Media-Foundation
## Microsoft-Media-Foundation
[Microsoft Media Foundation](/windows/win32/medfound/microsoft-media-foundation-sdk) enables the development of applications and components for using digital media. [Supported Media Formats in Media Foundation](/windows/win32/medfound/supported-media-formats-in-media-foundation).

Approximate on-disk footprint: 63,747 KB

## Removing Package

### Online Servicing (audit mode)
Use the [DISM command-line tool](/windows-hardware/manufacture/desktop/what-is-dism) with the ```/Online``` command-line parammeter to remove a single package via online servicing (audit mode).

```powershell
Dism.exe /Online /LogPath:%WINDIR%\Temp\Microsoft-Media-Foundation.log /NoRestart /Disable-Feature /FeatureName:Microsoft-Media-Foundation /PackageName:@Package
````
### Offline Servicing
Use the [DISM command-line tool](/windows-hardware/manufacture/desktop/what-is-dism) with the ```/Image:<image path>``` command-line parameter to remove a single package via offline servicing.

```powershell
Dism.exe /Image:c:\offline /LogPath:%WINDIR%\Temp\Microsoft-Media-Foundation.log /NoRestart /Disable-Feature /FeatureName:Microsoft-Media-Foundation /PackageName:@Package
````

## Related Packages
These packages collectively provide the functionality represented by the the [Media Feature Pack](https://learn.microsoft.com/en-us/windows/win32/wmdm/windows-media-device-manager-architecture).  There are dependencies between each of these packages.  Although it is possible, it is not recommended to remove a subset of these packages.
- [Microsoft-Media-Foundation](/windows/iot/iot-enterprise/Optimize-Your-Device/Removable-Packages-Details/Microsoft-Media-Foundation)
- [Microsoft-Windows-Media-Format](/windows/iot/iot-enterprise/Optimize-Your-Device/Removable-Packages-Details/Microsoft-Windows-Media-Format)
- [Microsoft-Windows-Media-Streaming](/windows/iot/iot-enterprise/Optimize-Your-Device/Removable-Packages-Details/Microsoft-Windows-Media-Streaming) 
- [Microsoft-Windows-MediaPlayback-OC](/windows/iot/iot-enterprise/Optimize-Your-Device/Removable-Packages-Details/Microsoft-Windows-MediaPlayback-OC)    
- [Microsoft-Windows-Portable-Devices](/windows/iot/iot-enterprise/Optimize-Your-Device/Removable-Packages-Details/Microsoft-Windows-Portable-Devices)   
- [Microsoft-Windows-WebcamExperience](/windows/iot/iot-enterprise/Optimize-Your-Device/Removable-Packages-Details/Microsoft-Windows-WebcamExperience.md) 
- [Microsoft-Windows-WinSATMediaFiles](/windows/iot/iot-enterprise/Optimize-Your-Device/Removable-Packages-Details/Microsoft-Windows-WinSATMediaFiles.md) 

## File List
| File Name                 | Installed Location |
|---------------------------|--------------------|
| active.grl	            | %programdata%\microsoft\mf\active.grl
| colorcnv.dll	            | %windir%\system32\colorcnv.dll
| coremmres.dll	            | %windir%\system32\coremmres.dll
| evr.dll	                | %windir%\system32\evr.dll
| l3codeca.acm	            | %windir%\system32\l3codeca.acm
| l3codecp.acm	            | %windir%\system32\l3codecp.acm
| mf.dll	                | %windir%\system32\mf.dll
| mfaacenc.dll	            | %windir%\system32\mfaacenc.dll
| mfasfsrcsnk.dll	        | %windir%\system32\mfasfsrcsnk.dll
| mfaudiocnv.dll	        | %windir%\system32\mfaudiocnv.dll
| mfcaptureengine.dll	    | %windir%\system32\mfcaptureengine.dll
| mfcore.dll	            | %windir%\system32\mfcore.dll
| mfds.dll	                | %windir%\system32\mfds.dll
| mfdvdec.dll	            | %windir%\system32\mfdvdec.dll
| mferror.dll	            | %windir%\system32\mferror.dll
| mfh263enc.dll	            | %windir%\system32\mfh263enc.dll
| mfh264enc.dll	            | %windir%\system32\mfh264enc.dll
| mfmediaengine.dll	        | %windir%\system32\mfmediaengine.dll
| mfmjpegdec.dll	        | %windir%\system32\mfmjpegdec.dll
| mfmkvsrcsnk.dll	        | %windir%\system32\mfmkvsrcsnk.dll
| mfmp4srcsnk.dll	        | %windir%\system32\mfmp4srcsnk.dll
| mfmpeg2srcsnk.dll        	| %windir%\system32\mfmpeg2srcsnk.dll
| mfnetcore.dll	            | %windir%\system32\mfnetcore.dll
| mfnetsrc.dll	            | %windir%\system32\mfnetsrc.dll
| mfperfhelper.dll        	| %windir%\system32\mfperfhelper.dll
| mfplat.dll	            | %windir%\system32\mfplat.dll
| mfplat.dll.mun        	| %windir%\systemresources\mfplat.dll.mun
| mfplay.dll	            | %windir%\system32\mfplay.dll
| mfpmp.exe	                | %windir%\system32\mfpmp.exe
| mfps.dll	                | %windir%\system32\mfps.dll
| mfreadwrite.dll	        | %windir%\system32\mfreadwrite.dll
| mfsrcsnk.dll	            | %windir%\system32\mfsrcsnk.dll
| mfsvr.dll	                | %windir%\system32\mfsvr.dll
| mftranscode.dll        	| %windir%\system32\mftranscode.dll
| mfvdsp.dll	            | %windir%\system32\mfvdsp.dll
| mfvfw.dll	                | %windir%\system32\mfvfw.dll
| mfwmaaec.dll	            | %windir%\system32\mfwmaaec.dll
| mp3dmod.dll	            | %windir%\system32\mp3dmod.dll
| mp43decd.dll	            | %windir%\system32\mp43decd.dll
| mp4sdecd.dll	            | %windir%\system32\mp4sdecd.dll
| mpg4decd.dll	            | %windir%\system32\mpg4decd.dll
| msac3enc.dll	            | %windir%\system32\msac3enc.dll
| msalacdecoder.dll	        | %windir%\system32\msalacdecoder.dll
| msalacencoder.dll	        | %windir%\system32\msalacencoder.dll
| msamrnbdecoder.dll	    | %windir%\system32\msamrnbdecoder.dll
| msamrnbencoder.dll	    | %windir%\system32\msamrnbencoder.dll
| msamrnbsink.dll	        | %windir%\system32\msamrnbsink.dll
| msamrnbsource.dll	        | %windir%\system32\msamrnbsource.dll
| msauddecmft.dll	        | %windir%\system32\msauddecmft.dll
| msflacdecoder.dll	        | %windir%\system32\msflacdecoder.dll
| msflacencoder.dll	        | %windir%\system32\msflacencoder.dll
| msheif.dll	            | %windir%\system32\msheif.dll
| msmpeg2adec.dll	        | %windir%\system32\msmpeg2adec.dll
| msmpeg2enc.dll	        | %windir%\system32\msmpeg2enc.dll
| msmpeg2vdec.dll	        | %windir%\system32\msmpeg2vdec.dll
| msopusdecoder.dll	        | %windir%\system32\msopusdecoder.dll
| msphotography.dll	        | %windir%\system32\msphotography.dll
| msrawimage.dll	        | %windir%\system32\msrawimage.dll
| msvideodsp.dll	        | %windir%\system32\msvideodsp.dll
| msvp9dec_redirect.dll	    | %windir%\system32\msvp9dec.dll
| msvproc.dll	            | %windir%\system32\msvproc.dll
| msvpxenc_redirect.dll	    | %windir%\system32\msvpxenc.dll
| mswebp.dll	            | %windir%\system32\mswebp.dll
| resampledmo.dll	        | %windir%\system32\resampledmo.dll
| rrinstaller.exe	        | %windir%\system32\rrinstaller.exe
| vidreszr.dll	            | %windir%\system32\vidreszr.dll
| windows.media.audio.dll	| %windir%\system32\windows.media.audio.dll
| windows.media.dll	        | %windir%\system32\windows.media.dll
| windows.media.editing.dll	| %windir%\system32\windows.media.editing.dll
| windows.media.renewal.dll	| %windir%\system32\windows.media.renewal.dll
| wmadmod.dll	            | %windir%\system32\wmadmod.dll
| wmadmoe.dll	            | %windir%\system32\wmadmoe.dll
| wmcodecdspps.dll	        | %windir%\system32\wmcodecdspps.dll
| wmspdmoe.dll	            | %windir%\system32\wmspdmoe.dll
| wmvdecod.dll	            | %windir%\system32\wmvdecod.dll
| wmvdspa.dll	            | %windir%\system32\wmvdspa.dll
| wmvencod.dll	            | %windir%\system32\wmvencod.dll
| wmvsdecd.dll	            | %windir%\system32\wmvsdecd.dll
| wmvsencd.dll	            | %windir%\system32\wmvsencd.dll
| wmvxencd.dll	            | %windir%\system32\wmvxencd.dll
