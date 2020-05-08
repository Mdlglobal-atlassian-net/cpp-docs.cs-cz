---
title: _mkgmtime, _mkgmtime32, _mkgmtime64
description: Popisuje funkce knihovny prostředí runtime _mkgmtime, _mkgmtime32 a _mkgmtime64 jazyka C a obsahuje příklady jejich použití.
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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 4b20073a2022c7da59a5e224a04051901b7b8a4f
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82914645"
---
# <a name="_mkgmtime-_mkgmtime32-_mkgmtime64"></a>_mkgmtime, _mkgmtime32, _mkgmtime64

Převede čas UTC reprezentovaný **strukturou** **TM** na čas utc reprezentovaný typem **time_t** .

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
Ukazatel na čas UTC jako **Struktura** **TM** pro převod.

## <a name="return-value"></a>Návratová hodnota

Množství typu **__time32_t** nebo **__time64_t** představující počet sekund uplynulých od půlnoci 1. ledna 1970 v koordinovaném světový čas (UTC). Pokud je datum mimo rozsah (viz oddíl poznámky) nebo vstup nelze interpretovat jako platný čas, vrácená hodnota je-1.

## <a name="remarks"></a>Poznámky

Funkce **_mkgmtime32** a **_mkgmtime64** převádějí čas UTC na typ **__time32_t** nebo **__time64_t** představující čas ve standardu UTC. Chcete-li převést místní čas na čas UTC, použijte místo toho **mktime**, **_mktime32**a **_mktime64** .

**_mkgmtime** je vložená funkce, která se vyhodnocuje jako **_mkgmtime64**a **time_t** je ekvivalentem **__time64_t**. Pokud potřebujete vynutit, aby kompilátor interpretoval **time_t** jako starou **time_t**32, můžete definovat **_USE_32BIT_TIME_T**. Nedoporučujeme ho, protože vaše aplikace může selhat i po 18. lednu 2038, maximálním rozsahu 32 bitové **time_t**. Není povolené na všech 64ových platformách.

Předaná časová struktura je změněna následujícím způsobem, stejně jako se změnila funkcemi **_mktime** : pole **tm_wday** a **tm_yday** jsou nastavena na nové hodnoty na základě hodnot **tm_mday** a **tm_year**. Vzhledem k tomu, že čas se předpokládá jako UTC, pole **tm_isdst** se ignoruje.

Rozsah funkce **_mkgmtime32** je od půlnoci, od 1. ledna 1970, od utc do 23:59:59, 15. ledna 2038, UTC. Rozsah **_mkgmtime64** je od půlnoci 1. ledna 1970, UTC do 23:59:59, 31. prosince 3000, UTC. Datum mimo rozsah má za následek návratovou hodnotu-1. Rozsah **_mkgmtime** závisí na tom, zda je **_USE_32BIT_TIME_T** definována. Pokud není definován, což je výchozí hodnota, je rozsah stejný jako **_mkgmtime64**. V opačném případě je rozsah omezen na 32 rozsah **_mkgmtime32**.

**Gmtime** i **localtime** používají pro převod společnou statickou vyrovnávací paměť. Pokud zadáte tuto vyrovnávací paměť **_mkgmtime**, bude předchozí obsah zničen.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

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

Následující příklad ukazuje, jak je neúplná struktura vyplněna **_mkgmtime**. Vypočítá hodnoty pro den v týdnu i rok.

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

[Správa času](../../c-runtime-library/time-management.md)\
[asctime, _wasctime](asctime-wasctime.md)\
[asctime_s _wasctime_s](asctime-s-wasctime-s.md)\
[gmtime, _gmtime32 _gmtime64](gmtime-gmtime32-gmtime64.md)\
[gmtime_s, _gmtime32_s _gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)\
[localtime_s, _localtime32_s _localtime64_s](localtime-s-localtime32-s-localtime64-s.md)\
[mktime, _mktime32 _mktime64](mktime-mktime32-mktime64.md)\
[time, _time32, _time64](time-time32-time64.md)
