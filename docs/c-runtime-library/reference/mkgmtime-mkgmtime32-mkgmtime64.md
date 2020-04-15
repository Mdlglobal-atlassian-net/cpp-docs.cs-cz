---
title: _mkgmtime, _mkgmtime32, _mkgmtime64
description: Popisuje _mkgmtime, _mkgmtime32 a _mkgmtime64 c runtime knihovny funkce a uvádí příklady, jak je používat.
ms.date: 4/2/2020
api_name:
- _mkgmtime32
- _mkgmtime64
- _mkgmtime
- _o__mkgmtime32
- _o__mkgmtime64
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
- api-ms-win-crt-time-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _mkgmtime64
- mkgmtime32
- _mkgmtime32
- mkgmtime
- mkgmtime64
- _mkgmtime
helpviewer_keywords:
- mkgmtime32 function
- time functions
- mkgmtime function
- _mkgmtime function
- converting times
- mkgmtime64 function
- _mkgmtime64 function
- _mkgmtime32 function
- time, converting
ms.assetid: b4ca2b67-e198-4f43-b3e2-e8ad6bd01867
ms.openlocfilehash: e8b3170fc0413a878777035fd76aac5eefa7b6bf
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338764"
---
# <a name="_mkgmtime-_mkgmtime32-_mkgmtime64"></a>_mkgmtime, _mkgmtime32, _mkgmtime64

Převede čas UTC reprezentované **struct** **tm** na čas UTC reprezentované **time_t** typu.

## <a name="syntax"></a>Syntaxe

```C
time_t _mkgmtime(
   struct tm* timeptr
);
__time32_t _mkgmtime32(
   struct tm* timeptr
);
__time64_t _mkgmtime64(
   struct tm* timeptr
);
```

### <a name="parameters"></a>Parametry

*timeptr*\
Ukazatel na čas UTC jako **struct** **tm** převést.

## <a name="return-value"></a>Návratová hodnota

Množství typu **__time32_t** nebo **__time64_t** představující počet sekund uplynulých od půlnoci 1. Pokud je datum mimo rozsah (viz část Poznámky) nebo vstup nelze interpretovat jako platný čas, vrácená hodnota je -1.

## <a name="remarks"></a>Poznámky

Funkce **_mkgmtime32** a **_mkgmtime64** převádějí čas UTC na **typ __time32_t** nebo **__time64_t** představující čas v čase utc. Chcete-li převést místní čas na čas UTC, použijte místo toho **mktime**, **_mktime32**a **_mktime64.**

**_mkgmtime** je vsazená funkce, která je vyhodnocena jako **_mkgmtime64**a **time_t** je ekvivalentní **__time64_t**. Pokud potřebujete vynutit, aby kompilátor interpretoval **time_t** jako starý 32bitový **time_t**, můžete definovat **_USE_32BIT_TIME_T**. Nedoporučujeme, protože vaše aplikace může selhat po 18 leden 2038, maximální rozsah 32bitový **time_t**. Na 64bitových platformách není vůbec povolen.

Předaná časová struktura se změní následujícím způsobem, stejným způsobem, jako je změněna **_mktime** funkcemi: pole **tm_wday** a **tm_yday** jsou nastavena na nové hodnoty založené na hodnotách **tm_mday** a **tm_year**. Vzhledem k tomu, že čas je považován za čas UTC, **tm_isdst** pole je ignorováno.

Rozsah funkce **_mkgmtime32** je od půlnoci, leden 1, 1970, UTC do 23:59:59 Leden 18, 2038, UTC. Rozsah **_mkgmtime64** je od půlnoci, leden 1, 1970, UTC do 23:59:59, Prosinec 31, 3000, UTC. Datum mimo rozsah má za následek vrácenou hodnotu -1. Rozsah **_mkgmtime** závisí na tom, zda je definován **_USE_32BIT_TIME_T.** Pokud není definován, což je výchozí, rozsah je stejný jako **_mkgmtime64**. V opačném případě je rozsah omezen na 32bitový rozsah **_mkgmtime32**.

**Gmtime** i **localtime** použít společné statické vyrovnávací paměti pro převod. Pokud tuto vyrovnávací paměť zadáte **_mkgmtime**, předchozí obsah bude zničen.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="examples"></a>Příklady

```C
// crt_mkgmtime.c
#include <stdio.h>
#include <time.h>

int main()
{
    struct tm t1, t2;
    time_t now, mytime, gmtime;
    char buff[30];

    time( & now );

    _localtime64_s( &t1, &now );
    _gmtime64_s( &t2, &now );

    mytime = mktime(&t1);
    gmtime = _mkgmtime(&t2);

    printf("Seconds since midnight, January 1, 1970\n");
    printf("My time: %I64d\nGM time (UTC): %I64d\n\n", mytime, gmtime);

    /* Use asctime_s to display these times. */

    _localtime64_s( &t1, &mytime );
    asctime_s( buff, sizeof(buff), &t1 );
    printf( "Local Time: %s\n", buff );

    _gmtime64_s( &t2, &gmtime );
    asctime_s( buff, sizeof(buff), &t2 );
    printf( "Greenwich Mean Time: %s\n", buff );

}
```

```Output
Seconds since midnight, January 1, 1970
My time: 1171588492
GM time (UTC): 1171588492

Local Time: Thu Feb 15 17:14:52 2007

Greenwich Mean Time: Fri Feb 16 01:14:52 2007
```

Následující příklad ukazuje, jak je neúplná struktura vyplněna **_mkgmtime**. Vypočítá hodnoty pro den v týdnu i v roce.

```C
// crt_mkgmtime2.c
#include <stdio.h>
#include <time.h>
#include <memory.h>

int main()
{
    struct tm t1, t2;
    time_t gmtime;
    char buff[30];

    memset(&t1, 0, sizeof(struct tm));
    memset(&t2, 0, sizeof(struct tm));

    t1.tm_mon = 1;
    t1.tm_isdst = 0;
    t1.tm_year = 103;
    t1.tm_mday = 12;

    // The day of the week and year will be incorrect in the output here.
    asctime_s( buff, sizeof(buff), &t1);
    printf("Before calling _mkgmtime, t1 = %s t.tm_yday = %d\n",
            buff, t1.tm_yday );

    gmtime = _mkgmtime(&t1);

    // The correct day of the week and year were determined.
    asctime_s( buff, sizeof(buff), &t1);
    printf("After calling _mkgmtime, t1 = %s t.tm_yday = %d\n",
            buff, t1.tm_yday );

}
```

```Output
Before calling _mkgmtime, t1 = Sun Feb 12 00:00:00 2003
t.tm_yday = 0
After calling _mkgmtime, t1 = Wed Feb 12 00:00:00 2003
t.tm_yday = 42
```

## <a name="see-also"></a>Viz také

[Řízení času](../../c-runtime-library/time-management.md)\
[asctime, _wasctime](asctime-wasctime.md)\
[asctime_s, _wasctime_s](asctime-s-wasctime-s.md)\
[gmtime, _gmtime32, _gmtime64](gmtime-gmtime32-gmtime64.md)\
[gmtime_s, _gmtime32_s, _gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)\
[localtime_s, _localtime32_s, _localtime64_s](localtime-s-localtime32-s-localtime64-s.md)\
[mktime, _mktime32, _mktime64](mktime-mktime32-mktime64.md)\
[time, _time32, _time64](time-time32-time64.md)
