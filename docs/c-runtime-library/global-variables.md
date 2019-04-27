---
title: Globální proměnné
ms.date: 11/04/2016
f1_keywords:
- c.variables
helpviewer_keywords:
- global variables
- variables, global
- global variables, Microsoft run-time library
ms.assetid: 01d1551c-2f0c-4f72-935c-6442caccf84f
ms.openlocfilehash: dfa78bd2c7aae7cc6059443066cbef58512755ce
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62343950"
---
# <a name="global-variables"></a>Globální proměnné

Knihovny run-time C společnosti Microsoft poskytuje tyto globální proměnné nebo makra. Některé z těchto globálních proměnných nebo makra jsou zastaralé a místo toho použití-bezpečnější verze funkční, které doporučujeme že používat místo globální proměnné.

|Proměnná|Popis|
|--------------|-----------------|
|[__argc, \__argv, \__wargv](../c-runtime-library/argc-argv-wargv.md)|Obsahuje argumenty příkazového řádku.|
|[_daylight, _dstbias, _timezone, and _tzname](../c-runtime-library/daylight-dstbias-timezone-and-tzname.md)|Zastaralé Místo toho použijte `_get_daylight`, `_get_dstbias`, `_get_timezone`, a `_get_tzname`.<br /><br /> Upraví pro místní čas; používá se v některých funkcích datum a čas.|
|[errno, _doserrno, _sys_errlist, and _sys_nerr](../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)|Zastaralé Místo toho použijte `_get_errno`, `_set_errno`, `_get_doserrno`, `_set_doserrno`, `perror` a `strerror`.<br /><br /> Ukládají se kódy chyb a související informace.|
|[_environ, _wenviron](../c-runtime-library/environ-wenviron.md)|Zastaralé Místo toho použijte `getenv_s`, `_wgetenv_s`, `_dupenv_s`, `_wdupenv_s`, `_putenv_s`, a `_wputenv_s`.<br /><br /> Ukazatele na pole ukazatelů do procesu prostředí řetězce; inicializován při spuštění.|
|[_fmode](../c-runtime-library/fmode.md)|Zastaralé Místo toho použijte `_get_fmode` nebo `_set_fmode`.<br /><br /> Nastaví výchozí režim překladu souboru.|
|[_iob](../c-runtime-library/iob.md)|Pole struktury řízení vstupně-výstupních operací pro konzolu, soubory a zařízení.|
|[_pctype, _pwctype, _wctype, _mbctype, _mbcasemap](../c-runtime-library/pctype-pwctype-wctype-mbctype-mbcasemap.md)|Obsahuje informace o používané funkce klasifikaci znaků.|
|[_pgmptr, _wpgmptr](../c-runtime-library/pgmptr-wpgmptr.md)|Zastaralé Místo toho použijte `_get_pgmptr` nebo `_get_wpgmptr`.<br /><br /> Inicializovány při spuštění programu úplnou nebo relativní cestu k programu, celý název aplikace nebo název programu bez jeho příponu názvu souboru, v závislosti na tom, jak byl vyvolán program.|

## <a name="see-also"></a>Viz také:

[Referenční dokumentace knihovny CRT](../c-runtime-library/c-run-time-library-reference.md)<br/>
[Globální konstanty](../c-runtime-library/global-constants.md)<br/>
[__argc, \__argv, \__wargv](../c-runtime-library/argc-argv-wargv.md)<br/>
[_get_daylight](../c-runtime-library/reference/get-daylight.md)<br/>
[_get_dstbias](../c-runtime-library/reference/get-dstbias.md)<br/>
[_get_timezone](../c-runtime-library/reference/get-timezone.md)<br/>
[_get_tzname](../c-runtime-library/reference/get-tzname.md)<br/>
[perror](../c-runtime-library/reference/perror-wperror.md)<br/>
[strerror](../c-runtime-library/reference/strerror-strerror-wcserror-wcserror.md)<br/>
[_get_doserrno](../c-runtime-library/reference/get-doserrno.md)<br/>
[_set_doserrno](../c-runtime-library/reference/set-doserrno.md)<br/>
[_get_errno](../c-runtime-library/reference/get-errno.md)<br/>
[_set_errno](../c-runtime-library/reference/set-errno.md)<br/>
[_dupenv_s, _wdupenv_s](../c-runtime-library/reference/dupenv-s-wdupenv-s.md)<br/>
[getenv, _wgetenv](../c-runtime-library/reference/getenv-wgetenv.md)<br/>
[getenv_s, _wgetenv_s](../c-runtime-library/reference/getenv-s-wgetenv-s.md)<br/>
[_putenv, _wputenv](../c-runtime-library/reference/putenv-wputenv.md)<br/>
[_putenv_s, _wputenv_s](../c-runtime-library/reference/putenv-s-wputenv-s.md)<br/>
[_get_fmode](../c-runtime-library/reference/get-fmode.md)<br/>
[_set_fmode](../c-runtime-library/reference/set-fmode.md)
