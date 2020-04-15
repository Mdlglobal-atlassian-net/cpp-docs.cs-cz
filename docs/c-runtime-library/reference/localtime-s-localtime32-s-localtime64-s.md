---
title: localtime_s, _localtime32_s, _localtime64_s
ms.date: 4/2/2020
api_name:
- _localtime64_s
- _localtime32_s
- localtime_s
- _o__localtime32_s
- _o__localtime64_s
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
ms.openlocfilehash: 3c5d194da85eb5d008dfc9cf19f222ebb575747d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81342126"
---
# <a name="localtime_s-_localtime32_s-_localtime64_s"></a>localtime_s, _localtime32_s, _localtime64_s

Převede **hodnotu time_t** času na strukturu **tm** a opraví místní časové pásmo. Jedná se o verze [místního času, _localtime32 _localtime64](localtime-localtime32-localtime64.md) s vylepšeními zabezpečení, jak je popsáno v [části Funkce zabezpečení v crt](../../c-runtime-library/security-features-in-the-crt.md).

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
Ukazatel na strukturu času, která má být vyplněna.

*sourceTime*<br/>
Ukazatel na uložený čas.

## <a name="return-value"></a>Návratová hodnota

Nula v případě úspěchu. Vrácená hodnota je kód chyby, pokud došlo k chybě. Kódy chyb jsou definovány v souboru Errno.h. Seznam těchto chyb naleznete v [tématu errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

### <a name="error-conditions"></a>Chybové stavy

|*tmDest*|*sourceTime*|Návratová hodnota|Hodnota v *tmDest*|Vyvolá neplatnou obslužnou rutinu parametru.|
|-----------|------------|------------------|--------------------|---------------------------------------|
|**Null**|jakékoli|**EINVAL**|Nezměněno|Ano|
|Není **null** (odkazuje na platnou paměť)|**Null**|**EINVAL**|Všechna pole nastavená na -1|Ano|
|Není **null** (odkazuje na platnou paměť)|menší než 0 nebo větší než **_MAX__TIME64_T**|**EINVAL**|Všechna pole nastavená na -1|Ne|

V případě prvních dvou chybových stavů je vyvolána neplatná obslužná rutina parametru, jak je popsáno v [parametru Validation](../../c-runtime-library/parameter-validation.md). Pokud je spuštění povoleno pokračovat, tyto funkce nastavit **errno** na **EINVAL** a vrátit **EINVAL**.

## <a name="remarks"></a>Poznámky

Funkce **localtime_s** převede čas uložený jako [time_t](../../c-runtime-library/standard-types.md) hodnotu a uloží výsledek do struktury typu [tm](../../c-runtime-library/standard-types.md). **Time_t** *hodnota sourceTime* představuje sekundy uplynulé od půlnoci (00:00:00), 1. Tato hodnota se obvykle získává z [funkce time.](time-time32-time64.md)

**localtime_s** opraví pro místní časové pásmo, pokud uživatel nejprve nastaví globální proměnnou prostředí **TZ**. Když je **nastavena TZ,** tři další proměnné prostředí (**_timezone**, **_daylight**a **_tzname**) jsou automaticky nastaveny také. Pokud není proměnná **TZ** nastavena, **localtime_s** pokusí použít informace o časovém pásmu zadané v ovládacím panelu Datum a čas. Pokud tyto informace nelze získat, PST8PDT, což znamená tichomořské časové pásmo, se používá ve výchozím nastavení. Popis těchto proměnných naleznete [_tzset.](tzset.md) **TZ** je rozšíření společnosti Microsoft a není součástí standardní definice ANSI **místního času**.

> [!NOTE]
> Cílové prostředí by se měl pokusit zjistit, zda letní čas je v platnosti.

**_localtime64_s**, který používá **__time64_t** strukturu, umožňuje data, která mají být vyjádřena až do 23:59:59, Leden 18, 3001, koordinovaný světový čas (UTC), zatímco **_localtime32_s** představuje data až 23:59:59 Leden 18, 2038, UTC.

**localtime_s** je vsazená funkce , která je vyhodnocena jako **_localtime64_s**a **time_t** je ekvivalentní **__time64_t**. Pokud potřebujete vynutit, aby kompilátor interpretoval **time_t** jako starý 32bitový **time_t**, můžete definovat **_USE_32BIT_TIME_T**. To **způsobí, že localtime_s** vyhodnotit na **_localtime32_s**. To se nedoporučuje, protože vaše aplikace může selhat po 18 leden 2038 a není povoleno na 64bitové platformy.

Pole typu [tm](../../c-runtime-library/standard-types.md) struktury ukládají následující hodnoty, z nichž každá je **int**.

|Pole|Popis|
|-|-|
|**tm_sec**|Sekundpo minutě (0 - 59).|
|**tm_min**|Minuty po hodině (0 - 59).|
|**tm_hour**|Hodiny od půlnoci (0 - 23).|
|**tm_mday**|Den v měsíci (1 - 31).|
|**tm_mon**|Měsíc (0 - 11; leden = 0).|
|**tm_year**|Rok (aktuální rok minus 1900).|
|**tm_wday**|Den v týdnu (0 - 6; Neděle = 0).|
|**tm_yday**|Den v roce (0 - 365; 1. ledna = 0).|
|**tm_isdst**|Kladná hodnota, pokud je v platnosti letní čas; 0, pokud letní čas není v platnosti; záporná hodnota, pokud není znám stav letního času.|

Pokud je nastavena proměnná prostředí **TZ,** c run-time knihovna předpokládá pravidla odpovídající Spojeným státům pro implementaci výpočtu letního času (DST).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Povinná hlavička C|Povinná hlavička jazyka C++|
|-------------|---------------------|-|
|**localtime_s**, **_localtime32_s**, **_localtime64_s**|\<time.h>|\<ctime> \<nebo time.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Viz také

[Časová správa](../../c-runtime-library/time-management.md)<br/>
[asctime_s, _wasctime_s](asctime-s-wasctime-s.md)<br/>
[ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime_s, _gmtime32_s, _gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)<br/>
[localtime, _localtime32, _localtime64](localtime-localtime32-localtime64.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
[_tzset](tzset.md)<br/>
