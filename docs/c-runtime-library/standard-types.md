---
title: "Standardní typy | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- __time64_t
- _diskfree_t
- _CRT_DUMP_CLIENT
- _fsize_t
- __timeb64
- File
- __utimeb64
- jmp_buf
- __finddata64_t
- _wfinddata_t
- _finddata_t
- utimbuf64
- wint_t
- wctrans_t
- wctype_t
- _HFILE
- _secerr_handler_func
- clock_t
- fpos_t
- _dev_t
- time64_t
- wfinddata64_t
- stat64
- ldiv_t
- _EXCEPTION_POINTERS
- terminate_function
- size_t
- timeb64
- tm
- _HEAPINFO
- unexpected_function
- _CrtMemState
- _se_translator_function
- sig_atomic_t
- _CRT_REPORT_HOOK
- _complex
- _w_finddatai64_t
- _timeb
- _onexit_t
- _RTC_ErrorNumber
- lconv
- _PNH
- _off_t
- ptrdiff_t
- time_t
- _FPIEEE_RECORD
- _exception
- __w_finddata64_t
- __stat64
- _utimbuf
- __utimbuf64
- div_t
- _CRT_ALLOC_HOOK
- int8_t
- uint8_t
- int16_t
- uint16_t
- int32_t
- uint32_t
- int64_t
- int_least8_t
- uint_least8_t
- int_least16_t
- uint_least16_t
- int_least32_t
- uint_least32_t
- int_least64_t
- uint_least64_t
- int_fast8_t
- uint_fast8_t
- int_fast16_t
- uint_fast16_t
- int_fast32_t
- uint_fast32_t
- int_fast64_t
- uint_fast64_t
- intmax_t
- uintmax_t
dev_langs: C++
helpviewer_keywords:
- __timeb64 type
- tm type
- clock_t type
- intptr_t type
- diskfree_t type
- wctype_t type
- CRT_DUMP_CLIENT type
- sig_atomic_t type
- _PNH type
- time_t type
- wfinddata_t type
- timeb64
- CRT, standard types
- wint_t type
- _RTC_ErrorNumber type
- _diskfree_t type
- _dev_t type
- _wfinddata_t type
- HFILE type
- __utimbuf64 type
- div_t type
- _onexit_t type
- _secerr_handler_func type
- FPIEEE_RECORD type
- HEAPINFO type
- PNH type
- _CRT_ALLOC_HOOK type
- _se_translater_function type
- va_list type
- wctrans_t type
- secerr_handler_func type
- _locale_t type
- timeb type
- lconv type
- utimbuf type
- dev_t type
- unexpected_function typedef
- _complex type
- _off_t type
- off_t type
- RTC_ErrorNumber type
- _FPIEEE_RECORD type
- exception type
- _CRT_REPORT_HOOK type
- _HEAPINFO type
- ldiv_t type
- terminate_function type
- uintptr_t type
- _CRT_DUMP_CLIENT type
- _utimbuf type
- wfinddatai64_t type
- fpos_t type
- wchar_t type
- CRT_ALLOC_HOOK type
- _HFILE type
- __time64_t type
- _timeb type
- CrtMemState type
- __finddata64_t type
- _exception type
- stat type
- onexit_t type
- FILE constant
- _stat type
- finddata_t type
- __wfinddata64_t type
- ptrdiff_t type
- complex types
- _wfinddatai64_t type
- _EXCEPTION_POINTERS type
- jmp_buf type
- se_translater_function type
- size_t type
- EXCEPTION_POINTERS type
- __stat64 type
- _fsize_t type
- CRT_REPORT_HOOK type
- _finddata_t type
ms.assetid: 23312dd2-4a6a-4d70-9b48-2a5d0d8c9f28
caps.latest.revision: "27"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: b80a4b8c947064886d6afa18e9c24d62195a049a
ms.sourcegitcommit: c9108f0c45b7a634d4e6e5c2d2ec192d50ffdbab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/18/2017
---
# <a name="standard-types"></a>Standardní typy
Běhové knihovny Microsoft definuje následující standardní typy a definice TypeDef.  
  
### <a name="fixed-width-integral-types-stdinth"></a>Celočíselné typy pevnou šířkou (stdint.h)  
  
|Název|Ekvivalentní předdefinovaný typ|  
|----------|-------------------------------|  
|int8\_t, uint8\_t|podepsaný char, unsigned char|  
|Int16\_t, uint16\_t|krátký, prostě bez znaménka|  
|Int32\_t, uint32\_t|int, int bez znaménka|  
|Int64\_t, uint64\_t|Long long long long bez znaménka|  
|int_least8_t uint_least8_t|podepsaný char, unsigned char|  
|int_least16_t uint_least16_t|krátký, prostě bez znaménka|  
|int_least32_t uint_least32_t|int, int bez znaménka|  
|int_least64_t uint_least64_t|Long long long long bez znaménka|  
|int_fast8_t uint_fast8_t|podepsaný char, unsigned char|  
|int_fast16_t uint_fast16_t|int, int bez znaménka|  
|int_fast32_t uint_fast32_t|int, int bez znaménka|  
|int_fast64_t uint_fast64_t|Long long long long bez znaménka|  
|intmax_t uintmax_t|Long long long long bez znaménka|  
  
|Typ|Popis|Deklarováno v|  
|----------|-----------------|-----------------|  
|`clock_t`(Pokud)|Úložiště čas hodnoty; používá [hodiny](../c-runtime-library/reference/clock.md).|TIME.H|  
|`_complex`Struktura|Ukládá skutečné a pomyslná částí komplexní čísla; používá [_cabs –](../c-runtime-library/reference/cabs.md).|MATH.H|  
|`_CRT_ALLOC_HOOK`|Definice typu uživatelem definované funkce připojení (hook). Použít v [_crtsetallochook –](../c-runtime-library/reference/crtsetallochook.md).|CRTDBG.H|  
|`_CRT_DUMP_CLIENT`,<br /><br /> `_CRT_DUMP_CLIENT_M`|Zadejte typ pro funkci zpětné volání, která bude zavolána v [_crtmemdumpallobjectssince –](../c-runtime-library/reference/crtmemdumpallobjectssince.md).|CRTDBG.H|  
|`_CrtMemState`Struktura|Obsahuje informace o aktuálním stavu haldy ladicího nástroje modulu runtime jazyka C.|CRTDBG.H|  
|`_CRT_REPORT_HOOK`,<br /><br /> `_CRT_REPORT_HOOKW`,<br /><br /> `_CRT_REPORT_HOOKW_M`|Zadejte typ pro funkci zpětné volání, která bude zavolána v [_crtdbgreport –](../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md).<br /><br /> Parametry této funkce jsou: typ sestavy, výstupní zpráva a návratová hodnota funkce zpětného volání.|CRTDBG.H|  
|`dev_t`, `_dev_t` krátký nebo bez znaménka celé číslo|Představuje popisovače zařízení.|SYS\TYPES.H|  
|`_diskfree_t`Struktura|Obsahuje informace o diskové jednotce. Používá [_getdiskfree –](../c-runtime-library/reference/getdiskfree.md)**.**|DOS.H a DIRECT.H|  
|`div_t`, `ldiv_t` a `lldiv_t` struktury|Ukládání hodnot vrácených [div](../c-runtime-library/reference/div.md), [ldiv –](../c-runtime-library/reference/ldiv-lldiv.md), a [lldiv –](../c-runtime-library/reference/ldiv-lldiv.md), v uvedeném pořadí.|STDLIB.H|  
|`errno_t`celé číslo|Použít pro funkce návratový typ nebo parametr, který se zabývá kódy chyb z `errno`.|STDDEF.H,<br /><br /> CRTDEFS.H|  
|`_exception`Struktura|Ukládá informace o chybách [_matherr –](../c-runtime-library/reference/matherr.md).|MATH.H|  
|`_EXCEPTION_POINTERS`|Obsahuje záznam o výjimce. V tématu [exception_pointers –](http://msdn.microsoft.com/library/windows/desktop/ms679331) Další informace.|FPIEEE.H|  
|`FILE`Struktura|Ukládá informace o aktuálním stavu datového proudu, používá se u všech vstupně-výstupních operací datového proudu.|STDIO.H|  
|`_finddata_t`, `_wfinddata_t`, `_finddata32_t`, `_wfinddata32_t`, `_finddatai64_t`, `_wfinddatai64_t`, `__finddata64_t`, `__wfinddata64_t`, `__finddata32i64_t`, `__wfinddata32i64_t`, `__finddata64i32_t`, `__wfinddata64i32_t` struktury|Uložit informace o atributu souboru vrácené [_findfirst –, _wfindfirst – a související funkce](../c-runtime-library/reference/findfirst-functions.md) a [_findnext –, _wfindnext – a související funkce](../c-runtime-library/reference/findnext-functions.md). V tématu [funkce hledání Filename](../c-runtime-library/filename-search-functions.md) informace o členové struktury.|IO.H, WCHAR.H|  
|`_FPIEEE_RECORD`Struktura|Obsahuje informace týkající se výjimek plovoucí desetinné čárky IEEE; Předaný depeše uživatelem definované obslužné rutiny podle [_fpieee_flt –](../c-runtime-library/reference/fpieee-flt.md).|FPIEEE.H|  
|`fpos_t`(dlouhých celých čísel, `__int64`, nebo struktura, v závislosti na cílové platformy)|Používá [fgetpos –](../c-runtime-library/reference/fgetpos.md) a [fsetpos –](../c-runtime-library/reference/fsetpos.md) k zaznamenání informací pro jednoznačné určení každých pozice v souboru.|STDIO.H|  
|`_fsize_t`(bez znaménka dlouhých celých čísel)|Slouží k reprezentaci velikosti souboru.|IO.H,<br /><br /> WCHAR.H|  
|`_HEAPINFO`Struktura|Obsahuje informace o další záznam haldy pro [_heapwalk –](../c-runtime-library/reference/heapwalk.md).|MALLOC.H|  
|`_HFILE`(void *)|Popisovač souboru operačního systému|CRTDBG.H|  
|`imaxdiv_t`|Typ hodnoty, který je vrácen [imaxdiv –](../c-runtime-library/reference/imaxdiv.md) funkce, obsahující podílu a zbytek.|inttypes.h|  
|`ino_t`, `_ino_t` (prostě bez znaménka)|Pro vracení informací o stavu|WCHAR.H|  
|`intmax_t`|Typ signed integer schopný reprezentovat jakoukoli hodnotu typu signed integer|stdint.h|  
|`intptr_t`(dlouhé celé číslo nebo `__int64`, v závislosti na cílové platformy)|Ukládá ukazatel (nebo popisovač) na platformách Win32 a Win64.|STDDEF.H a další vkládané soubory|  
|`jmp_buf`pole|Používá [setjmp](../c-runtime-library/reference/setjmp.md) a [longjmp](../c-runtime-library/reference/longjmp.md) k uložení a obnovení prostředí programu.|SETJMP.H|  
|`lconv`Struktura|Obsahuje pravidla formátování číselných hodnot v různých zemích nebo oblastech. Používá [localeconv –](../c-runtime-library/reference/localeconv.md).|LOCALE.H|  
|`_LDOUBLE`,<br /><br /> `_LONGDOUBLE`,<br /><br /> `_LDBL12`(dlouho double nebo unsigned char pole)|Představuje hodnotu long double.|STDLIB.H|  
|`_locale_t`Struktura|Ukládá aktuální hodnoty národního prostředí. Používá se ve všech knihovnách modulu runtime jazyka C pro specifická národní prostředí.|CRTDEF.H|  
|`mbstate_t`|Sleduje stav převodu vícebajtových znaků.|WCHAR.H|  
|`off_t`, `_off_t` dlouhých celých čísel|Představuje hodnotu posunu souboru.|WCHAR.H, SYS\TYPES.H|  
|`_onexit_t`,<br /><br /> `_onexit_m_t`ukazatele|Vrácený [_onexit –, _onexit_m –](../c-runtime-library/reference/onexit-onexit-m.md).|STDLIB.H|  
|`_PNH`ukazatel na funkci|Typ argumentu [_set_new_handler –](../c-runtime-library/reference/set-new-handler.md).|NEW.H|  
|`ptrdiff_t`(dlouhé celé číslo nebo `__int64`, v závislosti na cílové platformy)|Výsledek odečtení dvou ukazatelů|CRTDEFS.H|  
|`_purecall_handler`,<br /><br /> `_purecall_handler_m`|Definice typu funkce zpětného volání, která je volána při volání čistě virtuální funkce. Používá [_get_purecall_handler, _set_purecall_handler –](../c-runtime-library/reference/get-purecall-handler-set-purecall-handler.md). A `_purecall_handler` funkce by měla mít typ vrácené hodnoty void.|STDLIB.H|  
|`_RTC_error_fn`definování typu|Definice typu funkce, která bude ošetřovat kontroly chyb modulu runtime. Použít v [_rtc_seterrorfunc –](../c-runtime-library/reference/rtc-seterrorfunc.md).|RTCAPI.H|  
|`_RTC_error_fnW`definování typu|Definice typu funkce, která bude ošetřovat kontroly chyb modulu runtime. Použít v [_rtc_seterrorfuncw –](../c-runtime-library/reference/rtc-seterrorfuncw.md).|RTCAPI.H|  
|`_RTC_ErrorNumber`– výčet|Definuje chybové stavy pro [_rtc_geterrdesc –](../c-runtime-library/reference/rtc-geterrdesc.md) a [_rtc_seterrortype –](../c-runtime-library/reference/rtc-seterrortype.md).|RTCAPI.H|  
|`_se_translator_function`|Definice typu funkce zpětného volání, která převádí výjimku. První parametr je kód výjimky a druhý parametr je záznam o výjimce. Používá [_set_se_translator –](../c-runtime-library/reference/set-se-translator.md).|EH.H|  
|`sig_atomic_t`celé číslo|Typ objektu, který lze upravit jako atomic entita, i v přítomnost asynchronní přerušení; použít s [signál](../c-runtime-library/reference/signal.md).|SIGNAL.H|  
|`size_t`(bez znaménka __int64 nebo celé číslo bez znaménka, v závislosti na cílové platformy)|Výsledek `sizeof` operátor.|CRTDEFS.H a další vkládané soubory|  
|`_stat`Struktura|Obsahuje informace o stavu souboru vrácené [_stat –](../c-runtime-library/reference/stat-functions.md) a [_fstat –](../c-runtime-library/reference/fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md).|SYS\STAT.H|  
|`__stat64`Struktura|Obsahuje informace o stavu souboru vrácené [_fstat64 –](../c-runtime-library/reference/fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md) a [_stat64 –](../c-runtime-library/reference/stat-functions.md), a [_wstat64 –](../c-runtime-library/reference/stat-functions.md).|SYS\STAT.H|  
|`_stati64`Struktura|Obsahuje informace o stavu souboru vrácené [_fstati64 –](../c-runtime-library/reference/fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md), [_stati64 –](../c-runtime-library/reference/stat-functions.md), a [_wstati64 –](../c-runtime-library/reference/stat-functions.md).|SYS\STAT.H|  
|`terminate_function`definování typu|Zadejte typ pro funkci zpětné volání, která je volána, když [ukončit](../c-runtime-library/reference/terminate-crt.md) je volána. Používá [set_terminate –](../c-runtime-library/reference/set-terminate-crt.md).|EH.H|  
|`time_t`(__int64 nebo dlouhých celých čísel)|Představuje čas hodnoty v [mktime –](../c-runtime-library/reference/mktime-mktime32-mktime64.md), [čas](../c-runtime-library/reference/time-time32-time64.md), [ctime _ctime32 –, _ctime64 –, _wctime –, _wctime32 –, _wctime64 –](../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md), [ctime_s –, _ctime32_s –, _ctime64_s –, _ wctime_s –, _wctime32_s –, _wctime64_s –](../c-runtime-library/reference/ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md), [ctime _ctime32 –, _ctime64 –, _wctime –, _wctime32 –, _wctime64 –](../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md) a [gmtime – _gmtime32 –, _gmtime64 –](../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md). Počet sekund od 1. ledna 1970, 0:00 UTC. Pokud je definována _USE_32BIT_TIME_T, `time_t` je dlouhé celé číslo. Pokud definována není, je 64-bit integer.|TIME.H,<br /><br /> SYS\STAT.H,<br /><br /> SYS\TIMEB.H|  
|`__time32_t`(dlouhých celých čísel)|Představuje čas hodnoty v [mktime – _mktime32 –, _mktime64 –](../c-runtime-library/reference/mktime-mktime32-mktime64.md), [ctime _ctime32 –, _ctime64 –, _wctime –, _wctime32 –, _wctime64 –](../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md), [ctime_s –, _ctime32_s –, _ctime64_s –, _wctime_s –, _wctime32_s –, _ wctime64_s –](../c-runtime-library/reference/ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md), [gmtime – _gmtime32 –, _gmtime64 –](../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md) a [místní čas, _localtime32 –, _localtime64 –](../c-runtime-library/reference/localtime-localtime32-localtime64.md).|CRTDEFS.H, SYS\STAT.H,<br /><br /> SYS\TIMEB.H|  
|`__time64_t` (`__int64`)|Představuje čas hodnoty v [mktime – _mktime32 –, _mktime64 –](../c-runtime-library/reference/mktime-mktime32-mktime64.md), [_ctime64 –, _wctime64 –](../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md), [ctime_s –, _ctime32_s –, _ctime64_s –, _wctime_s –, _wctime32_s –, _wctime64_s –](../c-runtime-library/reference/ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md), [_gmtime64 –](../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md), [_localtime64 –](../c-runtime-library/reference/localtime-localtime32-localtime64.md) a [_time64 –](../c-runtime-library/reference/time-time32-time64.md).|TIME.H,<br /><br /> SYS\STAT.H,<br /><br /> SYS\TIMEB.H|  
|`_timeb`Struktura|Používá [_ftime –](../c-runtime-library/reference/ftime-ftime32-ftime64.md) a [_ftime_s – _ftime32_s –, _ftime64_s –](../c-runtime-library/reference/ftime-s-ftime32-s-ftime64-s.md) k uložení aktuální systémový čas.|SYS\TIMEB.H|  
|`__timeb32`Struktura|Používá [_ftime – _ftime32 –, _ftime64 –](../c-runtime-library/reference/ftime-ftime32-ftime64.md) a [_ftime_s – _ftime32_s –, _ftime64_s –](../c-runtime-library/reference/ftime-s-ftime32-s-ftime64-s.md) k uložení aktuální systémový čas.|SYS\TIMEB.H|  
|`__timeb64`Struktura|Používá [_ftime64 –](../c-runtime-library/reference/ftime-ftime32-ftime64.md) a [_ftime_s – _ftime32_s –, _ftime64_s –](../c-runtime-library/reference/ftime-s-ftime32-s-ftime64-s.md) k uložení aktuální systémový čas.|SYS\TIMEB.H|  
|`tm`Struktura|Používá [asctime –, _wasctime –](../c-runtime-library/reference/asctime-wasctime.md), [asctime_s –, _wasctime_s –](../c-runtime-library/reference/asctime-s-wasctime-s.md), [gmtime – _gmtime32 –, _gmtime64 –](../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md), [gmtime_s – _gmtime32_s –, _gmtime64_s –](../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md), [místní čas, _localtime32 –, _localtime64 –](../c-runtime-library/reference/localtime-localtime32-localtime64.md), [localtime_s – _localtime32_s –, _localtime64_s –](../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md), [mktime – _mktime32 –, _mktime64 –](../c-runtime-library/reference/mktime-mktime32-mktime64.md) a [strftime wcsftime –, _strftime_l –, _wcsftime_l –](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) k ukládání a načítání informací o době.|TIME.H|  
|`uintmax_t`|Typ unsigned integer schopný reprezentovat jakoukoli hodnotu typu unsigned integer|stdint.h|  
|`uintptr_t`(dlouhé celé číslo nebo `__int64`, v závislosti na cílové platformy)|Celé číslo bez znaménka nebo bez znaménka __int64 verzi `intptr_t`.|STDDEF.H a další vkládané soubory|  
|`unexpected_function`|Zadejte typ pro funkci zpětné volání, která je volána, když [neočekávané](../c-runtime-library/reference/unexpected-crt.md) je volána. Používá [set_unexpected –](../c-runtime-library/reference/set-unexpected-crt.md).|EH.H|  
|`_utimbuf`Struktura|Úložiště souborů časů přístup a změny používané [_utime –, _wutime –](../c-runtime-library/reference/utime-utime32-utime64-wutime-wutime32-wutime64.md) a [_futime – _futime32 –, _futime64 –](../c-runtime-library/reference/futime-futime32-futime64.md) změnit data modifikace souboru.|SYS\UTIME.H|  
|`_utimbuf32`Struktura|Úložiště souborů časů přístup a změny používané [_utime –, _utime32 –, _utime64 –, _wutime –, _wutime32 –, _wutime64 –](../c-runtime-library/reference/utime-utime32-utime64-wutime-wutime32-wutime64.md) a [_futime – _futime32 –, _futime64 –](../c-runtime-library/reference/futime-futime32-futime64.md) změnit data modifikace souboru.|SYS\UTIME.H|  
|`__utimbuf64`Struktura|Používá [_utime64 –, _wutime64 –](../c-runtime-library/reference/utime-utime32-utime64-wutime-wutime32-wutime64.md) a [_futime64 –](../c-runtime-library/reference/futime-futime32-futime64.md) k uložení aktuální čas.|SYS\UTIME.H|  
|`va_list`Struktura|Používané pro udržení informace potřebné pro [va_arg –](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md) a [va_end –](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md) makra. Volaná funkce deklaruje proměnné typu `va_list` , můžete předat jako argument jinou funkci.|STDARG.H,<br /><br /> CRTDEFS.H|  
|`wchar_t`široké znaky|Užitečné při vytváření přenositelných programů pro mezinárodní trhy.|STDDEF.H, STDLIB.H,<br /><br /> CRTDEFS.H,<br /><br /> SYS\STAT.H|  
|`wctrans_t`celé číslo|Představuje mapování znaků specifických pro národní prostředí.|WCTYPE.H|  
|`wctype_t`celé číslo|Může představovat všechny znaky znakové sady libovolného jazyka.|WCHAR.H,<br /><br /> CRTDEFS.H|  
|`wint_t`celé číslo|Typ datového objektu, který může pojmout všechny široké znaky nebo hodnotu širokého konce souboru.|WCHAR.H,<br /><br /> CRTDEFS.H|  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace běhové knihovny jazyka C](../c-runtime-library/c-run-time-library-reference.md)