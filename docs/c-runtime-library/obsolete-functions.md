---
title: Zastaralé funkce | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp
- devlang-cpp
ms.topic: conceptual
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
dev_langs:
- C++
helpviewer_keywords:
- obsolete functions
- _beep function
- _sleep function
- _seterrormode function
ms.assetid: 8e14c2d4-1481-4240-8586-47eb43db02b0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7ae341a6e3c997870f81381cbe68f13b2384ee7e
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43686069"
---
# <a name="obsolete-functions"></a>Zastaralé funkce
Některé funkce knihovny jsou zastaralé a novější ekvivalenty. Doporučujeme že vám tyto hodnoty změnit na aktualizované verze. Jiné zastaralé funkce byly odebrány z CRT. Toto téma uvádí zastaralé jako zastaralé funkce a funkce odebrat konkrétní verze sady Visual Studio.  
  
## <a name="deprecated-as-obsolete-in-visual-studio-2015"></a>Zastaralé jako zastaralé ve Visual Studiu 2015  
  
|Zastaralé funkce|Alternativní|  
|-----------------------|-----------------|  
|`is_wctype`|[iswctype](../c-runtime-library/reference/isctype-iswctype-isctype-l-iswctype-l.md)|  
|`_loaddll`|[LoadLibrary](https://msdn.microsoft.com/library/windows/desktop/ms684175\(v=vs.85\).aspx), [LoadLibraryEx](/windows/desktop/api/libloaderapi/nf-libloaderapi-loadlibraryexa), nebo [LoadPackagedLibrary](/windows/desktop/api/winbase/nf-winbase-loadpackagedlibrary)|  
|`_unloaddll`|[FreeLibrary](https://msdn.microsoft.com/library/windows/desktop/ms683152\(v=vs.85\).aspx)|  
|`_getdllprocaddr`|[GetProcAddress](../build/getprocaddress.md)|  
|`_seterrormode`|[SetErrorMode](https://msdn.microsoft.com/en-us/library/windows/desktop/ms680621\(v=vs.85\).aspx)|  
|`_beep`|[Zvukový signál](https://msdn.microsoft.com/library/windows/desktop/ms679277\(v=vs.85\).aspx)|  
|`_sleep`|[Přejít do režimu spánku](/windows/desktop/api/synchapi/nf-synchapi-sleep)|  
|`_getsystime`|[GetLocalTime](https://msdn.microsoft.com/library/windows/desktop/ms724338\(v=vs.85\).aspx)|  
|`_setsystime`|[SetLocalTime](https://msdn.microsoft.com/library/windows/desktop/ms724936\(v=vs.85\).aspx)|  
  
## <a name="removed-from-the-crt-in-visual-studio-2015"></a>Odebrat z CRT v sadě Visual Studio 2015  
  
|Zastaralé funkce|Alternativní|  
|-----------------------|-----------------|  
|[_cgets, _cgetws](../c-runtime-library/cgets-cgetws.md)|[_cgets_s, _cgetws_s](../c-runtime-library/reference/cgets-s-cgetws-s.md)|  
|[gets, _getws](../c-runtime-library/gets-getws.md)|[gets_s, _getws_s](../c-runtime-library/reference/gets-s-getws-s.md)|  
|[_get_output_format](../c-runtime-library/get-output-format.md)|Žádné|  
|[_heapadd](../c-runtime-library/heapadd.md)|Žádné|  
|[_heapset](../c-runtime-library/heapset.md)|Žádné|  
|[inp, inpw](../c-runtime-library/inp-inpw.md)|Žádné|  
|[_inp, _inpw, _inpd](../c-runtime-library/inp-inpw-inpd.md)|Žádné|  
|[outp, outpw](../c-runtime-library/outp-outpw.md)|Žádné|  
|[_outp, _outpw, _outpd](../c-runtime-library/outp-outpw-outpd.md)|Žádné|  
|[_set_output_format](../c-runtime-library/set-output-format.md)|Žádné|  
  
## <a name="removed-from-the-crt-in-earlier-versions-of-visual-studio"></a>Odebrat z CRT v dřívějších verzích sady Visual Studio  
 [_lock](../c-runtime-library/lock.md)  
  
 [_unlock](../c-runtime-library/unlock.md)