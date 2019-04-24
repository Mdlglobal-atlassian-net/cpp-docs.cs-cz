---
title: _mkgmtime, _mkgmtime32, _mkgmtime64
ms.date: 11/04/2016
apiname:
- _mkgmtime32
- _mkgmtime64
- _mkgmtime
apilocation:
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
apitype: DLLExport
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
ms.openlocfilehash: 65d96d79a45e05e4b371315c0612ed086f6ea2a0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62156496"
---
# <a name="mkgmtime-mkgmtime32-mkgmtime64"></a>_mkgmtime, _mkgmtime32, _mkgmtime64

Převede čas UTC reprezentovaný **struktura** **tm** na čas UTC reprezentovaný **time_t** typu.

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

*timeptr*<br/>
Ukazatel na čas UTC jako **struktura** **tm** pro převod.

## <a name="return-value"></a>Návratová hodnota

Množství typu **__time32_t** nebo **__time64_t –** představující dobu v sekundách uplynulých od půlnoci 1. ledna 1970, koordinovaný univerzální čas (UTC). Pokud datum je mimo rozsah (viz část poznámky) nebo vstup se nedá interpretovat jako platný čas, návratovou hodnotou -1.

## <a name="remarks"></a>Poznámky

**_Mkgmtime32 –** a **_mkgmtime64 –** převádějí na čas UTC **__time32_t** nebo **__time64_t –** typ představující čas v ČAS UTC. K převodu místní čas na čas UTC, použijte **mktime**, **_mktime32**, a **_mktime64** místo.

**_mkgmtime –** je vložená funkce, který se vyhodnotí **_mkgmtime64 –**, a **time_t** je ekvivalentní **__time64_t –**. Pokud je nutné donutit kompilátor k interpretaci **time_t** jako staré 32bitové **time_t**, můžete definovat **_USE_32BIT_TIME_T**. To se nedoporučuje, protože aplikace může selhat po 18. ledna 2038 (maximální rozsah 32bitové **time_t**), a to není povoleno vůbec na 64bitových platformách.

Času předané v se změní takto, stejným způsobem, jak se mění s **_mktime** funkce: **tm_wday** a **tm_yday** se nastaví na nové hodnoty podle hodnoty **tm_mday** a **tm_year**. Při zadávání **tm** struktury čas, nastavte **tm_isdst** pole:

- Nula (0) k označení, že je v platnosti (běžný čas).

- Hodnota, která je větší než 0, která znamená, že je v platnosti letní čas.

- Hodnotu menší než nula, která mají kód knihovny run-time C compute, zda (běžný čas) nebo letního času je v platnosti.

Knihovny run-time C používá proměnnou prostředí TZ k určení správné letní čas. Pokud není nastavena TZ, operační systém je dotazován zobrazíte správné místní letního času chování. **tm_isdst** je povinné pole. Pokud není nastavený, jeho hodnota není definována a návratovou hodnotu z **mktime** nepředvídatelné.

Rozsah **_mkgmtime32 –** funkce je mezi půlnocí 1. ledna 1970, UTC do 23:59:59 18. ledna 2038 UTC. Rozsah **_mkgmtime64 –** je od půlnoci 1. ledna 1970, UTC do 23:59:59, 31 prosince 3000 UTC. Návratová hodnota-1 za následek datem mimo rozsah. Rozsah **_mkgmtime –** závisí na tom, zda **_USE_32BIT_TIME_T** je definována. Pokud není definován (výchozí) rozsahu je **_mkgmtime64 –**; v opačném případě rozsah je omezen na rozsah 32bitové **_mkgmtime32 –**.

Všimněte si, že **gmtime** a **localtime** pomocí jedné staticky přidělenou vyrovnávací paměti pro převod. Pokud zadáte tuto vyrovnávací paměť pro **mkgmtime –**, předchozí obsah je zničen.

## <a name="example"></a>Příklad

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

### <a name="sample-output"></a>Vzorový výstup

```Output
Seconds since midnight, January 1, 1970
My time: 1171588492
GM time (UTC): 1171588492

Local Time: Thu Feb 15 17:14:52 2007

Greenwich Mean Time: Fri Feb 16 01:14:52 2007
```

Následující příklad ukazuje, jak neúplné struktura je vyplněná vypočítané hodnoty dne v týdnu a den v roce.

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

### <a name="output"></a>Výstup

```Output
Before calling _mkgmtime, t1 = Sun Feb 12 00:00:00 2003
t.tm_yday = 0
After calling _mkgmtime, t1 = Wed Feb 12 00:00:00 2003
t.tm_yday = 42
```

## <a name="see-also"></a>Viz také:

[Správa času](../../c-runtime-library/time-management.md)<br/>
[asctime, _wasctime](asctime-wasctime.md)<br/>
[asctime_s, _wasctime_s](asctime-s-wasctime-s.md)<br/>
[gmtime, _gmtime32, _gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[gmtime_s, _gmtime32_s, _gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)<br/>
[localtime_s, _localtime32_s, _localtime64_s](localtime-s-localtime32-s-localtime64-s.md)<br/>
[mktime, _mktime32, _mktime64](mktime-mktime32-mktime64.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
