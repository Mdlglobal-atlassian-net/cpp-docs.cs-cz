---
title: Standardní typy
ms.date: 11/04/2016
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
ms.openlocfilehash: c93cf4bf138fc6bc648d33c180edbed0dbe5014e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69500641"
---
# <a name="standard-types"></a>Standardní typy

Knihovna run-time společnosti Microsoft definuje následující standardní typy a definice typedef.

### <a name="fixed-width-integral-types-stdinth"></a>Integrální typy s pevnou šířkou (stdin. h)

|Name|Ekvivalentní vestavěný typ|
|----------|-------------------------------|
|int8\_t, uint8\_t|signed char, unsigned char|
|int16\_t, uint16\_t|krátký, unsigned short|
|Int32\_t, UInt32\_t|int, unsigned int|
|Int64\_t, UInt64\_t|Long Long, bez znaménka Long Long|
|int_least8_t, uint_least8_t|signed char, unsigned char|
|int_least16_t, uint_least16_t|krátký, unsigned short|
|int_least32_t, uint_least32_t|int, unsigned int|
|int_least64_t, uint_least64_t|Long Long, bez znaménka Long Long|
|int_fast8_t, uint_fast8_t|signed char, unsigned char|
|int_fast16_t, uint_fast16_t|int, unsigned int|
|int_fast32_t, uint_fast32_t|int, unsigned int|
|int_fast64_t, uint_fast64_t|Long Long, bez znaménka Long Long|
|intmax_t, uintmax_t|Long Long, bez znaménka Long Long|

|type|Popis|Deklarováno v|
|----------|-----------------|-----------------|
|`clock_t`dlouhou|Ukládá hodnoty času; používá se [hodinami](../c-runtime-library/reference/clock.md).|TIME.H|
|`_complex`strukturované|Ukládá reálné a imaginární části komplexních čísel; používá se v [_cabs](../c-runtime-library/reference/cabs.md).|MATH.H|
|`_CRT_ALLOC_HOOK`|Definice typu uživatelem definované funkce připojení (hook). Používá se v [_CrtSetAllocHook](../c-runtime-library/reference/crtsetallochook.md).|CRTDBG.H|
|`_CRT_DUMP_CLIENT`,<br /><br /> `_CRT_DUMP_CLIENT_M`|Typ definovaný pro funkci zpětného volání, která bude volána v [_CrtMemDumpAllObjectsSince](../c-runtime-library/reference/crtmemdumpallobjectssince.md).|CRTDBG.H|
|`_CrtMemState`strukturované|Obsahuje informace o aktuálním stavu haldy ladicího nástroje modulu runtime jazyka C.|CRTDBG.H|
|`_CRT_REPORT_HOOK`,<br /><br /> `_CRT_REPORT_HOOKW`,<br /><br /> `_CRT_REPORT_HOOKW_M`|Typ definovaný pro funkci zpětného volání, která bude volána v [_CrtDbgReport](../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md).<br /><br /> Parametry této funkce jsou: typ sestavy, výstupní zpráva a návratová hodnota funkce zpětného volání.|CRTDBG.H|
|`dev_t`, `_dev_t` short nebo unsigned integer|Představuje popisovače zařízení.|SYS\TYPES.H|
|`_diskfree_t`strukturované|Obsahuje informace o diskové jednotce. Používá se v [_getdiskfree](../c-runtime-library/reference/getdiskfree.md) **.**|DOS.H a DIRECT.H|
|`div_t``ldiv_t` a struktury`lldiv_t`|Hodnoty, které vrací [div](../c-runtime-library/reference/div.md), [ldiv](../c-runtime-library/reference/ldiv-lldiv.md)a [lldiv](../c-runtime-library/reference/ldiv-lldiv.md), jsou uloženy v uvedeném pořadí.|STDLIB.H|
|`errno_t`čísla|Používá se pro návratový typ funkce nebo parametr, který se zabývá kódy `errno`chyb.|STDDEF.H,<br /><br /> CRTDEFS.H|
|`_exception`strukturované|Ukládá informace o chybě pro [_matherr](../c-runtime-library/reference/matherr.md).|MATH.H|
|`_EXCEPTION_POINTERS`|Obsahuje záznam o výjimce. Další informace najdete v tématu [EXCEPTION_POINTERS](/windows/win32/api/winnt/ns-winnt-exception_pointers) .|FPIEEE.H|
|`FILE`strukturované|Ukládá informace o aktuálním stavu datového proudu, používá se u všech vstupně-výstupních operací datového proudu.|STDIO.H|
|`_finddata_t`, `_wfinddata_t` `_finddata32_t` ,`_finddatai64_t`,,, ,`__wfinddata64i32_t` ,,,, ,`__finddata64i32_t`struktury `__wfinddata64_t` `__finddata64_t` `_wfinddatai64_t` `_wfinddata32_t` `__finddata32i64_t` `__wfinddata32i64_t`|Uloží informace o atributu souboru vrácené funkcí [_findfirst, _wfindfirst a souvisejícími funkcemi](../c-runtime-library/reference/findfirst-functions.md) a [_findnext, _wfindnext a souvisejícími funkcemi](../c-runtime-library/reference/findnext-functions.md). Informace o členech struktury naleznete v tématu [funkce vyhledávání názvů souborů](../c-runtime-library/filename-search-functions.md) .|IO.H, WCHAR.H|
|`_FPIEEE_RECORD`strukturované|Obsahuje informace týkající se výjimky s plovoucí desetinnou čárkou standardu IEEE; předána uživatelsky definované obslužné rutině depeše od [_fpieee_flt](../c-runtime-library/reference/fpieee-flt.md).|FPIEEE.H|
|`fpos_t`(dlouhé celé číslo `__int64`, nebo struktura, v závislosti na cílové platformě)|Používá se v [fgetpos](../c-runtime-library/reference/fgetpos.md) a [fsetpos](../c-runtime-library/reference/fsetpos.md) k zaznamenávání informací pro jedinečné určení každé pozice v souboru.|STDIO.H|
|`_fsize_t`(dlouhé celé číslo bez znaménka)|Slouží k reprezentaci velikosti souboru.|IO.H,<br /><br /> WCHAR.H|
|`_HEAPINFO`strukturované|Obsahuje informace o další položce haldy pro [_heapwalk](../c-runtime-library/reference/heapwalk.md).|MALLOC.H|
|`_HFILE`(void \*)|Popisovač souboru operačního systému|CRTDBG.H|
|`imaxdiv_t`|Typ hodnoty vrácený funkcí [imaxdiv](../c-runtime-library/reference/imaxdiv.md) , která obsahuje podíl i zbytek.|inttypes.h|
|`ino_t`, `_ino_t` (krátký unsigned)|Pro vracení informací o stavu|WCHAR.H|
|`intmax_t`|Typ signed integer schopný reprezentovat jakoukoli hodnotu typu signed integer|stdint.h|
|`intptr_t`(dlouhé celé číslo `__int64`nebo, v závislosti na cílové platformě)|Ukládá ukazatel (nebo popisovač) na platformách Win32 a Win64.|STDDEF.H a další vkládané soubory|
|`jmp_buf`skupin|Používá se v [setjmp](../c-runtime-library/reference/setjmp.md) a [longjmp](../c-runtime-library/reference/longjmp.md) k ukládání a obnovování prostředí programu.|SETJMP.H|
|`lconv`strukturované|Obsahuje pravidla formátování číselných hodnot v různých zemích nebo oblastech. Používá se v [localeconv](../c-runtime-library/reference/localeconv.md).|LOCALE.H|
|`_LDOUBLE`,<br /><br /> `_LONGDOUBLE`,<br /><br /> `_LDBL12`(Long Double nebo pole znaků bez znaménka)|Představuje hodnotu long double.|STDLIB.H|
|`_locale_t`strukturované|Ukládá aktuální hodnoty národního prostředí. Používá se ve všech knihovnách modulu runtime jazyka C pro specifická národní prostředí.|CRTDEF.H|
|`mbstate_t`|Sleduje stav převodu vícebajtových znaků.|WCHAR.H|
|`off_t`, `_off_t` dlouhé celé číslo|Představuje hodnotu posunu souboru.|WCHAR.H, SYS\TYPES.H|
|`_onexit_t`,<br /><br /> `_onexit_m_t`ukazatele|Vráceno funkcí [_onexit, _onexit_m](../c-runtime-library/reference/onexit-onexit-m.md).|STDLIB.H|
|`_PNH`ukazatel na funkci|Typ argumentu, který bude [_set_new_handler](../c-runtime-library/reference/set-new-handler.md).|NEW.H|
|`ptrdiff_t`(dlouhé celé číslo `__int64`nebo, v závislosti na cílové platformě)|Výsledek odečtení dvou ukazatelů|CRTDEFS.H|
|`_purecall_handler`,<br /><br /> `_purecall_handler_m`|Definice typu funkce zpětného volání, která je volána při volání čistě virtuální funkce. Používá [se v _get_purecall_handler, _set_purecall_handler](../c-runtime-library/reference/get-purecall-handler-set-purecall-handler.md). `_purecall_handler` Funkce by měla mít návratový typ void.|STDLIB.H|
|`_RTC_error_fn`typ – definice|Definice typu funkce, která bude ošetřovat kontroly chyb modulu runtime. Používá se v [_RTC_SetErrorFunc](../c-runtime-library/reference/rtc-seterrorfunc.md).|RTCAPI.H|
|`_RTC_error_fnW`typ – definice|Definice typu funkce, která bude ošetřovat kontroly chyb modulu runtime. Používá se v [_RTC_SetErrorFuncW](../c-runtime-library/reference/rtc-seterrorfuncw.md).|RTCAPI.H|
|`_RTC_ErrorNumber`Enumeration|Definuje chybové stavy pro [_RTC_GetErrDesc](../c-runtime-library/reference/rtc-geterrdesc.md) a [_RTC_SetErrorType](../c-runtime-library/reference/rtc-seterrortype.md).|RTCAPI.H|
|`_se_translator_function`|Definice typu funkce zpětného volání, která převádí výjimku. První parametr je kód výjimky a druhý parametr je záznam o výjimce. Používá se v [_set_se_translator](../c-runtime-library/reference/set-se-translator.md).|EH.H|
|`sig_atomic_t`čísla|Typ objektu, který lze upravit jako atomickou entitu, a to i v případě asynchronních přerušení; používá se u [signálu](../c-runtime-library/reference/signal.md).|SIGNAL.H|
|`size_t`(bez znaménka __int64 nebo unsigned integer v závislosti na cílové platformě)|`sizeof` Výsledek operátoru|CRTDEFS.H a další vkládané soubory|
|`_stat`strukturované|Obsahuje informace o stavu souboru vrácené funkcí [_stat](../c-runtime-library/reference/stat-functions.md) a [_fstat](../c-runtime-library/reference/fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md).|SYS\STAT.H|
|`__stat64`strukturované|Obsahuje informace o stavu souborů vracené [_fstat64](../c-runtime-library/reference/fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md) a [_stat64](../c-runtime-library/reference/stat-functions.md)a [_wstat64](../c-runtime-library/reference/stat-functions.md).|SYS\STAT.H|
|`_stati64`strukturované|Obsahuje informace o stavu souborů vracené [_fstati64](../c-runtime-library/reference/fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md), [_stati64](../c-runtime-library/reference/stat-functions.md)a [_wstati64](../c-runtime-library/reference/stat-functions.md).|SYS\STAT.H|
|`terminate_function`typ – definice|Typ definovaný pro funkci zpětného volání, která je volána při volání funkce [Terminate](../c-runtime-library/reference/terminate-crt.md) . Používá se v [set_terminate](../c-runtime-library/reference/set-terminate-crt.md).|EH.H|
|`time_t`(__int64 nebo Long Integer)|Představuje časové hodnoty v [mktime](../c-runtime-library/reference/mktime-mktime32-mktime64.md), [Time](../c-runtime-library/reference/time-time32-time64.md), [CTime –, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md), [ctime_s, _ctime32_s,](../c-runtime-library/reference/ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)_ctime64_s, _wctime_s, _wctime32_s, _wctime64_s, CTime –, _ctime32, _ctime64, _wctime [, _ wctime32, _wctime64](../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md) a [gmtime, _gmtime32, _gmtime64](../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md). Počet sekund od 1. ledna 1970, 0:00 UTC. Pokud je definován _USE_32BIT_TIME_T, `time_t` je dlouhé celé číslo. Pokud definována není, je 64-bit integer.|TIME.H,<br /><br /> SYS\STAT.H,<br /><br /> SYS\TIMEB.H|
|`__time32_t`(dlouhé celé číslo)|Představuje hodnoty času v [mktime, _mktime32, _mktime64](../c-runtime-library/reference/mktime-mktime32-mktime64.md), [CTime –, _ctime32, _ctime64, _wctime, _wctime32](../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md), _wctime64, ctime_s, _ctime32_s, _ctime64_s, [_wctime_s, _wctime32_s, _wctime64_s](../c-runtime-library/reference/ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md), [gmtime, _gmtime32, _gmtime64 ](../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)a [localtime, _localtime32, _localtime64](../c-runtime-library/reference/localtime-localtime32-localtime64.md).|CRTDEFS.H, SYS\STAT.H,<br /><br /> SYS\TIMEB.H|
|`__time64_t` (`__int64`)|Představuje hodnoty času v [mktime, _mktime32, _mktime64](../c-runtime-library/reference/mktime-mktime32-mktime64.md), [_ctime64, _wctime64](../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md), [ctime_s, _ctime32_s, _ctime64_s, _wctime_s, _wctime32_s, _wctime64_s](../c-runtime-library/reference/ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md), [_gmtime64](../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md), [_localtime64](../c-runtime-library/reference/localtime-localtime32-localtime64.md) a [_time64](../c-runtime-library/reference/time-time32-time64.md).|TIME.H,<br /><br /> SYS\STAT.H,<br /><br /> SYS\TIMEB.H|
|`_timeb`strukturované|Používá se v [_ftime](../c-runtime-library/reference/ftime-ftime32-ftime64.md) a [_ftime_s, _ftime32_s, _ftime64_s](../c-runtime-library/reference/ftime-s-ftime32-s-ftime64-s.md) k uložení aktuálního systémového času.|SYS\TIMEB.H|
|`__timeb32`strukturované|Používá se v [_ftime, _ftime32, _ftime64](../c-runtime-library/reference/ftime-ftime32-ftime64.md) a [_ftime_s, _ftime32_s, _ftime64_s](../c-runtime-library/reference/ftime-s-ftime32-s-ftime64-s.md) k uložení aktuálního systémového času.|SYS\TIMEB.H|
|`__timeb64`strukturované|Používá se v [_ftime64](../c-runtime-library/reference/ftime-ftime32-ftime64.md) a [_ftime_s, _ftime32_s, _ftime64_s](../c-runtime-library/reference/ftime-s-ftime32-s-ftime64-s.md) k uložení aktuálního systémového času.|SYS\TIMEB.H|
|`tm`strukturované|Používá se v [asctime, _wasctime](../c-runtime-library/reference/asctime-wasctime.md), [asctime_s, _wasctime_s](../c-runtime-library/reference/asctime-s-wasctime-s.md), [gmtime, _gmtime32, _gmtime64](../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md), [gmtime_s, _gmtime32_s, _gmtime64_s](../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md), [localtime, _localtime32, _localtime64](../c-runtime-library/reference/localtime-localtime32-localtime64.md), [localtime_s, _localtime32_s, _ localtime64_s](../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md), [mktime, _mktime32, _mktime64](../c-runtime-library/reference/mktime-mktime32-mktime64.md) a [strftime, wcsftime, _strftime_l, _wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) , aby ukládaly a načetly informace o čase.|TIME.H|
|`uintmax_t`|Typ unsigned integer schopný reprezentovat jakoukoli hodnotu typu unsigned integer|stdint.h|
|`uintptr_t`(dlouhé celé číslo `__int64`nebo, v závislosti na cílové platformě)|Unsigned integer nebo nepodepsaná __int64 verze systému `intptr_t`.|STDDEF.H a další vkládané soubory|
|`unexpected_function`|Typ definovaný pro funkci zpětného volání, která je volána, když [](../c-runtime-library/reference/unexpected-crt.md) je volána neočekávaná. Používá se v [set_unexpected](../c-runtime-library/reference/set-unexpected-crt.md).|EH.H|
|`_utimbuf`strukturované|Ukládá přístup k souborům a časy úprav používané [_utime, _wutime](../c-runtime-library/reference/utime-utime32-utime64-wutime-wutime32-wutime64.md) a [_futime, _futime32, _futime64](../c-runtime-library/reference/futime-futime32-futime64.md) pro změnu dat úprav souborů.|SYS\UTIME.H|
|`_utimbuf32`strukturované|Ukládá přístup k souborům a časy úprav používané [_utime, _utime32, _utime64, _wutime, _wutime32, _wutime64](../c-runtime-library/reference/utime-utime32-utime64-wutime-wutime32-wutime64.md) a [_futime, _futime32, _futime64](../c-runtime-library/reference/futime-futime32-futime64.md) a mění data úprav souborů.|SYS\UTIME.H|
|`__utimbuf64`strukturované|Používá se v [_utime64, _wutime64](../c-runtime-library/reference/utime-utime32-utime64-wutime-wutime32-wutime64.md) a [_futime64](../c-runtime-library/reference/futime-futime32-futime64.md) k uložení aktuálního času.|SYS\UTIME.H|
|`va_list`strukturované|Slouží k uchovávání informací požadovaných makry [va_arg](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md) a [va_end](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md) . Volaná funkce deklaruje proměnnou typu `va_list` , která může být předána jako argument jiné funkci.|STDARG.H,<br /><br /> CRTDEFS.H|
|`wchar_t`velký znak|Užitečné při vytváření přenositelných programů pro mezinárodní trhy.|STDDEF.H, STDLIB.H,<br /><br /> CRTDEFS.H,<br /><br /> SYS\STAT.H|
|`wctrans_t`čísla|Představuje mapování znaků specifických pro národní prostředí.|WCTYPE.H|
|`wctype_t`čísla|Může představovat všechny znaky znakové sady libovolného jazyka.|WCHAR.H,<br /><br /> CRTDEFS.H|
|`wint_t`čísla|Typ datového objektu, který může pojmout všechny široké znaky nebo hodnotu širokého konce souboru.|WCHAR.H,<br /><br /> CRTDEFS.H|

## <a name="see-also"></a>Viz také:

[Referenční dokumentace knihovny CRT](../c-runtime-library/c-run-time-library-reference.md)
