---
title: localtime_s, _localtime32_s, _localtime64_s
ms.date: 07/09/2019
apiname:
- _localtime64_s
- _localtime32_s
- localtime_s
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
ms.openlocfilehash: 454ab492fbe8a31b9ceeca518fa5e590271dbf06
ms.sourcegitcommit: 07b34ca1c1fecced9fadc95de15dc5fee4f31e5a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/09/2019
ms.locfileid: "67693416"
---
# <a name="localtimes-localtime32s-localtime64s"></a>localtime_s, _localtime32_s, _localtime64_s

Převede **time_t** čas hodnota, která má **tm** struktury a opravuje pro místní časové pásmo. Jde o verzích [localtime, _localtime32, _localtime64](localtime-localtime32-localtime64.md) s rozšířeními zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

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
Ukazatel na strukturu čas být vyplněna.

*sourceTime*<br/>
Ukazatel na uložený čas.

## <a name="return-value"></a>Návratová hodnota

Nula v případě úspěchu. Vrácená hodnota je kód chyby, pokud dojde k selhání. Kódy chyb jsou definovány v Errno.h. Seznam těchto chyb, naleznete v tématu [errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

### <a name="error-conditions"></a>Chybové podmínky

|*tmDest*|*sourceTime*|Návratová hodnota|Hodnota v *tmDest*|Vyvolá obslužnou rutinu neplatného parametru|
|-----------|------------|------------------|--------------------|---------------------------------------|
|**NULL**|Všechny|**EINVAL**|Nezměněno|Ano|
|Není **NULL** (odkazuje na platný paměti)|**NULL**|**EINVAL**|Všechna pole nastavena na hodnotu -1|Ano|
|Není **NULL** (odkazuje na platný paměti)|menší než 0 nebo větší než **_MAX__TIME64_T**|**EINVAL**|Všechna pole nastavena na hodnotu -1|Ne|

V případě první dvě chybové stavy, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud smí provádění pokračovat, tyto funkce nastaví **errno** k **EINVAL** a vrátit **EINVAL**.

## <a name="remarks"></a>Poznámky

**Localtime_s –** funkce převede uložené jako čas [time_t](../../c-runtime-library/standard-types.md) hodnotu a výsledek je uložen na strukturu typu [tm](../../c-runtime-library/standard-types.md). **Time_t** hodnotu *sourceTime* představuje sekundách uplynulých od půlnoci (00: 00:00), 1. ledna 1970, UTC. Tato hodnota se obvykle získá z [čas](time-time32-time64.md) funkce.

**localtime_s –** pro místní časové pásmo opraví, pokud uživatel nejprve nastaví proměnnou prostředí globální **TZ**. Když **TZ** nastavena tři další proměnné prostředí ( **_timezone**, **_daylight**, a **_tzname**) se automaticky nastaví také. Pokud **TZ** proměnná není nastavená, **localtime_s –** pokusí použít informace o časovém pásmu, zadaný v aplikaci datum/čas v Ovládacích panelech. Pokud nelze získat tyto informace, se standardně používá PST8PDT, což znamená tichomořské časové pásmo. Zobrazit [_tzset –](tzset.md) popis těchto proměnných. **TZ** je rozšíření společnosti Microsoft a není součástí standardní definice ANSI **localtime**.

> [!NOTE]
> Cílové prostředí snažte se zjistit, zda je v platnosti letní čas.

**_localtime64_s –** , který používá **__time64_t –** struktury, umožňuje data vyjadřují až do 23:59:59, 18. ledna 3001, koordinovaného univerzálního času (UTC), zatímco **_localtime32_s –** představuje data do 23:59:59 18. ledna 2038 UTC.

**localtime_s –** je vložená funkce, která je vyhodnocena na **_localtime64_s –** , a **time_t** je ekvivalentní **__time64_t –** . Pokud je nutné donutit kompilátor k interpretaci **time_t** jako staré 32bitové **time_t**, můžete definovat **_USE_32BIT_TIME_T**. To způsobí, že to **localtime_s –** vyhodnotilo **_localtime32_s –** . Toto nastavení nedoporučujeme, protože může vaše aplikace selhat po 18. ledna 2038, a to není povoleno na 64bitových platformách.

Pole typu Struktura [tm](../../c-runtime-library/standard-types.md) ukládat následující hodnoty, z nichž každý je **int**.

|Pole|Popis|
|-|-|
|**tm_sec**|Sekundy po minutě (0 – 59).|
|**tm_min**|Minuty po hodině (0 – 59).|
|**tm_hour**|Hodiny od půlnoci (0 - 23).|
|**tm_mday**|Den v měsíci (1-31).|
|**tm_mon**|Měsíc (0 – 11; Leden = 0).|
|**tm_year**|Rok (aktuální rok minus 1900).|
|**tm_wday**|Den v týdnu (0 – 6; Neděle = 0).|
|**tm_yday**|Den roku (0 - 365; 1. ledna = 0).|
|**tm_isdst**|Kladnou hodnotu, pokud je v platnosti; letního času 0, pokud není platná; letního času Záporná hodnota, pokud stav letní čas není znám.|

Pokud **TZ** nastavení proměnné prostředí, knihovny run-time jazyka C předpokládá pravidla vhodné Spojených států pro implementaci výpočtu letního času (DST).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaná hlavička C|Požadované hlaviček jazyka C++|
|-------------|---------------------|-|
|**localtime_s**, **_localtime32_s**, **_localtime64_s**|\<time.h>|\<CTime – > nebo \<time.h >|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

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
