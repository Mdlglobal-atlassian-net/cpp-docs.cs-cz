---
title: Zastaralé funkce
description: Obsahuje seznam zastaralých funkcí, které jsou zastaralé a odebrané z knihovny Microsoft C Runtime Library (CRT).
ms.date: 4/2/2020
api_name:
- _beep
- _sleep
- _loaddll
- _getdllprocaddr
- _seterrormode
- is_wctype
- _getsystime
- _setsystime
- _unloaddll
- _o__beep
- _o__getdllprocaddr
- _o__getsystime
- _o__loaddll
- _o__seterrormode
- _o__setsystime
- _o__sleep
- _o__unloaddll
- _o_is_wctype
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-process-l1-1-0.dll
- api-ms-win-crt-runtime-l1-1-0.dll
- api-ms-win-crt-string-l1-1-0.dll
- api-ms-win-crt-time-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- is_wctype
- _loaddll
- _unloaddll
- _getdllprocaddr
- _seterrormode
- _beep
- _sleep
- _getsystime
- corecrt_wctype/is_wctype
- process/_loaddll
- process/_unloaddll
- process/_getdllprocaddr
- stdlib/_seterrormode
- stdlib/_beep
- stdlib/_sleep
- time/_getsystime
- time/_setsystime
helpviewer_keywords:
- obsolete functions
- _beep function
- _sleep function
- _seterrormode function
ms.assetid: 8e14c2d4-1481-4240-8586-47eb43db02b0
ms.openlocfilehash: b8a094294abba46ae78e9d3529ccf3a7b0a31f39
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919894"
---
# <a name="obsolete-functions"></a>Zastaralé funkce

Některé funkce knihovny jsou zastaralé a mají novější ekvivalenty. Tyto funkce doporučujeme změnit na aktualizované verze. Jiné zastaralé funkce byly odebrány z CRT. Tento článek obsahuje seznam funkcí, které jsou zastaralé jako zastaralé, a funkce odebrané v konkrétní verzi sady Visual Studio.

## <a name="deprecated-as-obsolete-in-visual-studio-2015"></a>Zastaralé jako zastaralé v aplikaci Visual Studio 2015

|Zastaralá funkce|Jiné|
|-----------------------|-----------------|
|`is_wctype`|[iswctype](../c-runtime-library/reference/isctype-iswctype-isctype-l-iswctype-l.md)|
|`_loaddll`|[LoadLibrary](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryw), [LoadLibraryEx](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexw)nebo [LoadPackagedLibrary](/windows/win32/api/winbase/nf-winbase-loadpackagedlibrary)|
|`_unloaddll`|[FreeLibrary](/windows/win32/api/libloaderapi/nf-libloaderapi-freelibrary)|
|`_getdllprocaddr`|[GetProcAddress](../build/getprocaddress.md)|
|`_seterrormode`|[SetErrorMode](/windows/win32/api/errhandlingapi/nf-errhandlingapi-seterrormode)|
|`_beep`|[Signálu](/windows/win32/api/utilapiset/nf-utilapiset-beep)|
|`_sleep`|[Režim spánku](/windows/win32/api/synchapi/nf-synchapi-sleep)|
|`_getsystime`|[GetLocalTime](/windows/win32/api/sysinfoapi/nf-sysinfoapi-getlocaltime)|
|`_setsystime`|[SetLocalTime](/windows/win32/api/sysinfoapi/nf-sysinfoapi-setlocaltime)|

## <a name="removed-from-the-crt-in-visual-studio-2015"></a>Odebráno z CRT v aplikaci Visual Studio 2015

|Zastaralá funkce|Jiné|
|-----------------------|-----------------|
|[_cgets, _cgetws](../c-runtime-library/cgets-cgetws.md)|[_cgets_s, _cgetws_s](../c-runtime-library/reference/cgets-s-cgetws-s.md)|
|[gets, _getws](../c-runtime-library/gets-getws.md)|[gets_s, _getws_s](../c-runtime-library/reference/gets-s-getws-s.md)|
|[_get_output_format](../c-runtime-library/get-output-format.md)|Žádné|
|[_heapadd](../c-runtime-library/heapadd.md)|Žádné|
|[_heapset](../c-runtime-library/heapset.md)|Žádné|
|[INP, inpw, _inp, _inpw, _inpd](../c-runtime-library/inp-inpw-inpd.md)|Žádné|
|[outp, outpw, _outp, _outpw, _outpd](../c-runtime-library/outp-outpw-outpd.md)|Žádné|
|[_set_output_format](../c-runtime-library/set-output-format.md)|Žádné|

## <a name="removed-from-the-crt-in-earlier-versions-of-visual-studio"></a>Odebráno z CRT v dřívějších verzích sady Visual Studio

[_lock](../c-runtime-library/lock.md)

[_unlock](../c-runtime-library/unlock.md)
