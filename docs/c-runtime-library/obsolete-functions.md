---
title: Zastaralé funkce
ms.date: 11/04/2016
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
ms.openlocfilehash: 2f42593620c3457694bd57ccdc5a90216b3a28f1
ms.sourcegitcommit: c85c8a1226d8fbbaa29f4691ed719f8e6cc6575c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2019
ms.locfileid: "54893883"
---
# <a name="obsolete-functions"></a>Zastaralé funkce

Některé funkce knihovny jsou zastaralé a novější ekvivalenty. Doporučujeme že vám tyto hodnoty změnit na aktualizované verze. Jiné zastaralé funkce byly odebrány z CRT. Toto téma uvádí zastaralé jako zastaralé funkce a funkce odebrat konkrétní verze sady Visual Studio.

## <a name="deprecated-as-obsolete-in-visual-studio-2015"></a>Zastaralé jako zastaralé ve Visual Studiu 2015

|Zastaralé funkce|Alternativní|
|-----------------------|-----------------|
|`is_wctype`|[iswctype](../c-runtime-library/reference/isctype-iswctype-isctype-l-iswctype-l.md)|
|`_loaddll`|[LoadLibrary](/windows/desktop/api/libloaderapi/nf-libloaderapi-loadlibrarya), [LoadLibraryEx](/windows/desktop/api/libloaderapi/nf-libloaderapi-loadlibraryexa), nebo [LoadPackagedLibrary](/windows/desktop/api/winbase/nf-winbase-loadpackagedlibrary)|
|`_unloaddll`|[FreeLibrary](/windows/desktop/api/libloaderapi/nf-libloaderapi-freelibrary)|
|`_getdllprocaddr`|[GetProcAddress](../build/getprocaddress.md)|
|`_seterrormode`|[SetErrorMode](https://msdn.microsoft.com/library/windows/desktop/ms680621)|
|`_beep`|[Zvukový signál](/windows/desktop/api/utilapiset/nf-utilapiset-beep)|
|`_sleep`|[Přejít do režimu spánku](/windows/desktop/api/synchapi/nf-synchapi-sleep)|
|`_getsystime`|[GetLocalTime](/windows/desktop/api/sysinfoapi/nf-sysinfoapi-getlocaltime)|
|`_setsystime`|[SetLocalTime](/windows/desktop/api/sysinfoapi/nf-sysinfoapi-setlocaltime)|

## <a name="removed-from-the-crt-in-visual-studio-2015"></a>Odebrat z CRT v sadě Visual Studio 2015

|Zastaralé funkce|Alternativní|
|-----------------------|-----------------|
|[_cgets, _cgetws](../c-runtime-library/cgets-cgetws.md)|[_cgets_s, _cgetws_s](../c-runtime-library/reference/cgets-s-cgetws-s.md)|
|[gets, _getws](../c-runtime-library/gets-getws.md)|[gets_s, _getws_s](../c-runtime-library/reference/gets-s-getws-s.md)|
|[_get_output_format](../c-runtime-library/get-output-format.md)|Žádná|
|[_heapadd](../c-runtime-library/heapadd.md)|Žádná|
|[_heapset](../c-runtime-library/heapset.md)|Žádná|
|[inp, inpw](../c-runtime-library/inp-inpw.md)|Žádná|
|[_inp, _inpw, _inpd](../c-runtime-library/inp-inpw-inpd.md)|Žádná|
|[outp, outpw](../c-runtime-library/outp-outpw.md)|Žádná|
|[_outp, _outpw, _outpd](../c-runtime-library/outp-outpw-outpd.md)|Žádná|
|[_set_output_format](../c-runtime-library/set-output-format.md)|Žádná|

## <a name="removed-from-the-crt-in-earlier-versions-of-visual-studio"></a>Odebrat z CRT v dřívějších verzích sady Visual Studio

[_lock](../c-runtime-library/lock.md)

[_unlock](../c-runtime-library/unlock.md)