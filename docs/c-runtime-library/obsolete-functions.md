---
title: "Zastaralé funkce | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
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
dev_langs: C++
helpviewer_keywords:
- obsolete functions
- _beep function
- _sleep function
- _seterrormode function
ms.assetid: 8e14c2d4-1481-4240-8586-47eb43db02b0
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 8a8811703234f2c4e23dab6ad2b99b1aae316c04
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="obsolete-functions"></a>Zastaralé funkce
Některé funkce knihovny jsou zastaralé a novější ekvivalenty. Doporučujeme, že aby aktualizované verze změníte. Další zastaralé funkce byly odebrány z CRT. Toto téma obsahuje zastaralý jako zastaralé funkce a funkce v konkrétní verzi sady Visual Studio odebrána.  
  
## <a name="deprecated-as-obsolete-in-visual-studio-2015"></a>Zastaralé jako zastaralé v sadě Visual Studio 2015  
  
|Zastaralé funkce|Alternativní|  
|-----------------------|-----------------|  
|`is_wctype`|[iswctype –](../c-runtime-library/reference/isctype-iswctype-isctype-l-iswctype-l.md)|  
|`_loaddll`|[LoadLibrary](http://go.microsoft.com/fwlink/p/?LinkID=259187), [funkce LoadLibraryEx](http://go.microsoft.com/fwlink/p/?LinkID=236091), nebo [LoadPackagedLibrary](https://msdn.microsoft.com/library/windows/desktop/hh447159\(v=vs.85\).aspx)|  
|`_unloaddll`|[FreeLibrary](http://go.microsoft.com/fwlink/p/?LinkID=259188)|  
|`_getdllprocaddr`|[GetProcAddress](../build/getprocaddress.md)|  
|`_seterrormode`|[SetErrorMode](http://go.microsoft.com/fwlink/p/?LinkID=255242)|  
|`_beep`|[Zvukový signál](https://msdn.microsoft.com/library/windows/desktop/ms679277\(v=vs.85\).aspx)|  
|`_sleep`|[Přejít do režimu spánku](https://msdn.microsoft.com/library/windows/desktop/ms686298\(v=vs.85\).aspx)|  
|`_getsystime`|[GetLocalTime](https://msdn.microsoft.com/library/windows/desktop/ms724338\(v=vs.85\).aspx)|  
|`_setsystime`|[SetLocalTime](https://msdn.microsoft.com/library/windows/desktop/ms724936\(v=vs.85\).aspx)|  
  
## <a name="removed-from-the-crt-in-visual-studio-2015"></a>Odebrat z CRT ve Visual Studiu 2015  
  
|Zastaralé funkce|Alternativní|  
|-----------------------|-----------------|  
|[_cgets –, _cgetws –](../c-runtime-library/cgets-cgetws.md)|[_cgets_s –, _cgetws_s –](../c-runtime-library/reference/cgets-s-cgetws-s.md)|  
|[Získá _getws –](../c-runtime-library/gets-getws.md)|[gets_s –, _getws_s –](../c-runtime-library/reference/gets-s-getws-s.md)|  
|[_get_output_format –](../c-runtime-library/get-output-format.md)|Žádné|  
|[_heapadd –](../c-runtime-library/heapadd.md)|Žádné|  
|[_heapset –](../c-runtime-library/heapset.md)|Žádné|  
|[INP –, inpw –](../c-runtime-library/inp-inpw.md)|Žádné|  
|[_inp – _inpw –, _inpd –](../c-runtime-library/inp-inpw-inpd.md)|Žádné|  
|[outp –, outpw –](../c-runtime-library/outp-outpw.md)|Žádné|  
|[_outp – _outpw –, _outpd –](../c-runtime-library/outp-outpw-outpd.md)|Žádné|  
|[_set_output_format –](../c-runtime-library/set-output-format.md)|Žádné|  
  
## <a name="removed-from-the-crt-in-earlier-versions-of-visual-studio"></a>Odebrat z CRT v dřívějších verzích sady Visual Studio  
 [_Lock](../c-runtime-library/lock.md)  
  
 [_Unlock –](../c-runtime-library/unlock.md)