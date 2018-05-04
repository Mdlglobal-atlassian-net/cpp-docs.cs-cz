---
title: Globální proměnné | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- c.variables
dev_langs:
- C++
helpviewer_keywords:
- global variables
- variables, global
- global variables, Microsoft run-time library
ms.assetid: 01d1551c-2f0c-4f72-935c-6442caccf84f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a2da3dd07c7088bee4be750b764b4a467bfebeae
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="global-variables"></a>Globální proměnné
Běhové knihovny Microsoft C poskytuje tyto globální proměnné nebo makra. Některé tyto globální proměnné nebo makra jsou zastaralé považuje bezpečnější verze funkční, které doporučujeme že používat místo globální proměnné.  
  
|Proměnná|Popis|  
|--------------|-----------------|  
|[__argc, \__argv, \__wargv](../c-runtime-library/argc-argv-wargv.md)|Obsahuje argumenty příkazového řádku.|  
|[_daylight, _dstbias, _timezone, and _tzname](../c-runtime-library/daylight-dstbias-timezone-and-tzname.md)|Zastaralé Místo toho použijte `_get_daylight`, `_get_dstbias`, `_get_timezone`, a `_get_tzname`.<br /><br /> Upraví pro místní čas; použít v některé funkce data a času.|  
|[errno, _doserrno, _sys_errlist, and _sys_nerr](../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)|Zastaralé Místo toho použijte `_get_errno`, `_set_errno`, `_get_doserrno`, `_set_doserrno`, `perror` a `strerror`.<br /><br /> Ukládá kódy chyb a související informace.|  
|[_environ, _wenviron](../c-runtime-library/environ-wenviron.md)|Zastaralé Místo toho použijte `getenv_s`, `_wgetenv_s`, `_dupenv_s`, `_wdupenv_s`, `_putenv_s`, a `_wputenv_s`.<br /><br /> Ukazatele na pole ukazatele na řetězce prostředí procesu; inicializovat při spuštění.|  
|[_fmode](../c-runtime-library/fmode.md)|Zastaralé Místo toho použijte `_get_fmode` nebo `_set_fmode`.<br /><br /> Nastaví výchozí režim překladu souboru.|  
|[_iob](../c-runtime-library/iob.md)|Pole vstupně-výstupních operací řídicí struktury pro konzolu, soubory a zařízení.|  
|[_pctype, _pwctype, _wctype, _mbctype, _mbcasemap](../c-runtime-library/pctype-pwctype-wctype-mbctype-mbcasemap.md)|Obsahuje informace, které jsou používané funkce klasifikace znaků.|  
|[_pgmptr, _wpgmptr](../c-runtime-library/pgmptr-wpgmptr.md)|Zastaralé Místo toho použijte `_get_pgmptr` nebo `_get_wpgmptr`.<br /><br /> Inicializovaná při spuštění programu úplná nebo relativní cestu k programu, celý název aplikace nebo název programu bez jeho příponu názvu souboru, v závislosti na tom, jak byla vyvolána program.|  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace běhové knihovny jazyka C](../c-runtime-library/c-run-time-library-reference.md)   
 [Globální konstanty](../c-runtime-library/global-constants.md)   
 [__argc, \__argv, \__wargv](../c-runtime-library/argc-argv-wargv.md)   
 [_get_daylight](../c-runtime-library/reference/get-daylight.md)   
 [_get_dstbias –](../c-runtime-library/reference/get-dstbias.md)   
 [_get_timezone](../c-runtime-library/reference/get-timezone.md)   
 [_get_tzname –](../c-runtime-library/reference/get-tzname.md)   
 [perror](../c-runtime-library/reference/perror-wperror.md)   
 [strerror –](../c-runtime-library/reference/strerror-strerror-wcserror-wcserror.md)   
 [_get_doserrno](../c-runtime-library/reference/get-doserrno.md)   
 [_set_doserrno](../c-runtime-library/reference/set-doserrno.md)   
 [_get_errno](../c-runtime-library/reference/get-errno.md)   
 [_set_errno](../c-runtime-library/reference/set-errno.md)   
 [_dupenv_s –, _wdupenv_s –](../c-runtime-library/reference/dupenv-s-wdupenv-s.md)   
 [GETENV –, _wgetenv –](../c-runtime-library/reference/getenv-wgetenv.md)   
 [getenv_s –, _wgetenv_s –](../c-runtime-library/reference/getenv-s-wgetenv-s.md)   
 [_putenv, _wputenv](../c-runtime-library/reference/putenv-wputenv.md)   
 [_putenv_s –, _wputenv_s –](../c-runtime-library/reference/putenv-s-wputenv-s.md)   
 [_get_fmode –](../c-runtime-library/reference/get-fmode.md)   
 [_set_fmode](../c-runtime-library/reference/set-fmode.md)