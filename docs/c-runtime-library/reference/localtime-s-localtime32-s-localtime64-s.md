---
title: localtime_s, _localtime32_s, _localtime64_s
ms.date: 07/09/2019
api_name:
- _localtime64_s
- _localtime32_s
- localtime_s
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _localtime32_s
- localtime32_s
- localtime_s
- localtime64_s
- _localtime64_s
helpviewer_keywords:
- _localtime64_s function
- localtime32_s function
- _localtime32_s function
- localtime64_s function
- time, converting values
- localtime_s function
ms.assetid: 842d1dc7-d6f8-41d3-b340-108d4b90df54
ms.openlocfilehash: c00a5d23441612d0e70bfafd571bcb25250edb09
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70953329"
---
# <a name="localtime_s-_localtime32_s-_localtime64_s"></a>localtime_s, _localtime32_s, _localtime64_s

Převede hodnotu **time_t** času na strukturu **TM** a opraví se pro místní časové pásmo. Jedná se o verze [localtime, _localtime32 a _localtime64](localtime-localtime32-localtime64.md) s vylepšeními zabezpečení, jak [je popsáno v části funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
errno_t localtime_s(
   struct tm* const tmDest,
   time_t const* const sourceTime
);
errno_t _localtime32_s(
   struct tm* tmDest,
   __time32_t const* sourceTime
);
errno_t _localtime64_s(
   struct tm* tmDest,
   __time64_t const* sourceTime
);
```

### <a name="parameters"></a>Parametry

*tmDest*<br/>
Ukazatel na časovou strukturu, která má být vyplněna.

*sourceTime*<br/>
Ukazatel na uložený čas.

## <a name="return-value"></a>Návratová hodnota

Nula v případě úspěchu. Návratová hodnota je kód chyby, pokud dojde k selhání. Kódy chyb jsou definovány v errno. h. Seznam těchto chyb naleznete v tématu [errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

### <a name="error-conditions"></a>Chybové stavy

|*tmDest*|*sourceTime*|Návratová hodnota|Hodnota v *tmDest*|Vyvolá neplatnou obslužnou rutinu parametru.|
|-----------|------------|------------------|--------------------|---------------------------------------|
|**NULL**|Jakýmikoli|**EINVAL**|Neupraveno|Ano|
|Není **null** (ukazuje na platnou paměť)|**NULL**|**EINVAL**|Všechna pole nastavená na-1|Ano|
|Není **null** (ukazuje na platnou paměť)|menší než 0 nebo větší než **_MAX__TIME64_T**|**EINVAL**|Všechna pole nastavená na-1|Ne|

V případě první dvě chybové podmínky je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, tyto funkce nastaví **errno** na **EINVAL** a vrátí **EINVAL**.

## <a name="remarks"></a>Poznámky

Funkce **localtime_s** převede čas uložený jako hodnotu [time_t](../../c-runtime-library/standard-types.md) a výsledek uloží ve struktuře typu [TM](../../c-runtime-library/standard-types.md). Hodnota **time_t** *sourceTime* představuje sekundy, které uplynuly od půlnoci (00:00:00), 1. ledna 1970, UTC. Tato hodnota je obvykle získána z funkce [Time](time-time32-time64.md) .

**localtime_s** správné pro místní časové pásmo, pokud uživatel napřed nastaví globální proměnnou prostředí na **TZ**. Je-li nastavena hodnotu **TZ** , jsou automaticky nastaveny i tři další proměnné prostředí ( **_timezone**, **_daylight**a **_tzname**). Pokud není nastavena proměnná **TZ** , **localtime_s** se pokusí použít informace o časovém pásmu zadané v aplikaci datum/čas v Ovládacích panelech. Pokud tyto informace nelze získat, PST8PDT, který označuje časové pásmo tichomořského, se ve výchozím nastavení používá. Popis těchto proměnných naleznete v tématu [_tzset](tzset.md) . **TZ** je rozšíření společnosti Microsoft, které není součástí standardní definice standardu ANSI pro **localtime**.

> [!NOTE]
> Cílové prostředí by mělo zkusit zjistit, jestli je aktivní letní čas.

**_localtime64_s**, která používá strukturu **__time64_t** , umožňuje data vyjádřit až 23:59:59, 18. ledna 3001, KOORDINOVANÝ světový čas (UTC), zatímco **_localtime32_s** představuje datum až 23:59:59 do 18. ledna. 2038, UTC.

**localtime_s** je vložená funkce, která se vyhodnotí na **_localtime64_s**a **time_t** je ekvivalentem **__time64_t**. Pokud potřebujete vynutit, aby kompilátor interpretoval **time_t** jako starou 32 **time_t**, můžete definovat **_USE_32BIT_TIME_T**. To způsobí, že se **localtime_s** vyhodnotí jako **_localtime32_s**. To se nedoporučuje, protože vaše aplikace může selhat i po 18. lednu 2038 a není povolená na 64 platformách.

Pole struktury typu [TM](../../c-runtime-library/standard-types.md) ukládají následující hodnoty, z nichž každá je **int**.

|Pole|Popis|
|-|-|
|**tm_sec**|Sekundy po minutě (0-59).|
|**tm_min**|Minut po hodině (0-59).|
|**tm_hour**|Hodiny od půlnoci (0-23).|
|**tm_mday**|Den v měsíci (1-31).|
|**tm_mon**|Měsíc (0-11; Leden = 0).|
|**tm_year**|Year (aktuální rok minus 1900).|
|**tm_wday**|Den v týdnu (0-6; Neděle = 0).|
|**tm_yday**|Den v roce (0-365; 1. ledna = 0).|
|**tm_isdst**|Kladná hodnota v případě, že platí letní čas; 0, pokud letní čas neplatí; záporná hodnota, pokud stav letního času není znám.|

Pokud je nastavena proměnná prostředí **TZ** , knihovna run-time jazyka C předpokládá pravidla, která jsou vhodná pro USA pro implementaci výpočtu letního času (DST).

## <a name="requirements"></a>Požadavky

|Rutina|Povinné záhlaví jazyka C|Požadovaná C++ hlavička|
|-------------|---------------------|-|
|**localtime_s**, **_localtime32_s**, **_localtime64_s**|\<time.h>|\<CTime – > nebo \<Time. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_localtime_s.c
// This program uses _time64 to get the current time
// and then uses _localtime64_s() to convert this time to a structure
// representing the local time. The program converts the result
// from a 24-hour clock to a 12-hour clock and determines the
// proper extension (AM or PM).

#include <stdio.h>
#include <string.h>
#include <time.h>

int main( void )
{
    struct tm newtime;
    char am_pm[] = "AM";
    __time64_t long_time;
    char timebuf[26];
    errno_t err;

    // Get time as 64-bit integer.
    _time64( &long_time );
    // Convert to local time.
    err = _localtime64_s( &newtime, &long_time );
    if (err)
    {
        printf("Invalid argument to _localtime64_s.");
        exit(1);
    }
    if( newtime.tm_hour > 12 )        // Set up extension.
        strcpy_s( am_pm, sizeof(am_pm), "PM" );
    if( newtime.tm_hour > 12 )        // Convert from 24-hour
        newtime.tm_hour -= 12;        // to 12-hour clock.
    if( newtime.tm_hour == 0 )        // Set hour to 12 if midnight.
        newtime.tm_hour = 12;

    // Convert to an ASCII representation.
    err = asctime_s(timebuf, 26, &newtime);
    if (err)
    {
        printf("Invalid argument to asctime_s.");
        exit(1);
    }
    printf( "%.19s %s\n", timebuf, am_pm );
}
```

```Output
Fri Apr 25 01:19:27 PM
```

## <a name="see-also"></a>Viz také:

[Správa času](../../c-runtime-library/time-management.md)<br/>
[asctime_s, _wasctime_s](asctime-s-wasctime-s.md)<br/>
[ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime_s, _gmtime32_s, _gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)<br/>
[localtime, _localtime32, _localtime64](localtime-localtime32-localtime64.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
[_tzset](tzset.md)<br/>
