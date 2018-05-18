---
title: localtime_s – _localtime32_s –, _localtime64_s – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- _localtime64_s function
- localtime32_s function
- _localtime32_s function
- localtime64_s function
- time, converting values
- localtime_s function
ms.assetid: 842d1dc7-d6f8-41d3-b340-108d4b90df54
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 513bfe5baa16c9cae5052da084c65f580aad7f2e
ms.sourcegitcommit: 19a108b4b30e93a9ad5394844c798490cb3e2945
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/17/2018
---
# <a name="localtimes-localtime32s-localtime64s"></a>localtime_s, _localtime32_s, _localtime64_s

Převede **time_t** čas hodnotu **tm** struktury a opravuje pro místní časovou zónu. Toto jsou verze [místní čas, _localtime32 –, _localtime64 –](localtime-localtime32-localtime64.md) vylepšení zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

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
Ukazatel na strukturu čas k vyplnění.

*sourceTime*<br/>
Ukazatel na uložené čas.

## <a name="return-value"></a>Návratová hodnota

Nula v případě úspěchu. Vrácená hodnota je kód chyby, pokud dojde k selhání. Kódy chyb jsou definovány v Errno.h. Seznam těchto chybách naleznete v tématu [errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

### <a name="error-conditions"></a>Chybové stavy

|*tmDest*|*sourceTime*|Návratová hodnota|Hodnota v *tmDest*|Vyvolá obslužnou rutinu neplatný parametr|
|-----------|------------|------------------|--------------------|---------------------------------------|
|**HODNOTU NULL**|všechny|**EINVAL –**|nedojde ke změně|Ano|
|Není **NULL** (odkazuje na platný paměti)|**HODNOTU NULL**|**EINVAL –**|Všechna pole nastavena na hodnotu -1|Ano|
|Není **NULL** (odkazuje na platný paměti)|menší než 0 nebo větší než **_MAX__TIME64_T**|**EINVAL –**|Všechna pole nastavena na hodnotu -1|Ne|

V případě první dvě chybové stavy, je vyvolána obslužná rutina neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění pokračovat, nastavte tyto funkce **errno** k **einval –** a vrátit **einval –**.

## <a name="remarks"></a>Poznámky

**_Localtime32_s –** funkce převede čas uložené jako [time_t](../../c-runtime-library/standard-types.md) hodnotu a výsledek je uložen ve struktuře typu [tm](../../c-runtime-library/standard-types.md). **Dlouho** hodnotu *sourceTime* představuje počet sekund uběhlých od půlnoci (00: 00:00), 1. ledna 1970, UTC. Tato hodnota se obvykle získávají z [čas](time-time32-time64.md) funkce.

**_localtime32_s –** vyřeší pro místní časovou zónu, pokud uživatel nejprve nastaví proměnnou prostředí globální **TZ**. Když **TZ** nastavena, tři další systémové proměnné (**_timezone**, **_daylight**, a **_tzname**) se nastaví automaticky také. Pokud **TZ** proměnná není nastavena, **localtime32_s –** pokusí použít informace o časovém pásmu, který je zadán v aplikaci datum a čas v Ovládacích panelech. Pokud tyto informace nelze získat, PST8PDT, která označuje, že tichomořském časovém pásmu, se používá ve výchozím nastavení. V tématu [_tzset –](tzset.md) popis těchto proměnných. **TZ** je rozšíření Microsoft a není součástí standardní definice ANSI **místní čas**.

> [!NOTE]
> Cílové prostředí by měl pokusit určit, zda je v platnosti letní čas.

**_localtime64_s –**, které používá **__time64_t –** struktury, umožňuje data, která se vyjádřit až do 23:59:59, leden 18 3001, koordinovaný světový čas (UTC), zatímco **_localtime32_s –** představuje data do 23:59:59 18 leden 2038 UTC.

**localtime_s –** vložená funkce, jehož výsledkem je **_localtime64_s –**, a **time_t** je ekvivalentní **__time64_t –**. Pokud potřebujete vynutit kompilátoru interpretovat **time_t** jako starý 32bitovou verzi **time_t**, můžete definovat **_USE_32BIT_TIME_T**. Provedete to způsobí, že **localtime_s –** k vyhodnocení **_localtime32_s –**. Není doporučeno, protože vaše aplikace může selhat po 18. ledna 2038, a není povoleno na 64bitových platformách.

Pole typu Struktura [tm](../../c-runtime-library/standard-types.md) ukládat následující hodnoty, z nichž každý je **int**.

|Pole|Popis|
|-|-|
|**tm_sec**|Sekund za minutu (0 - 59).|
|**tm_min**|Počet minut po hodině (0 - 59).|
|**tm_hour**|Hodiny od půlnoci (0 - 23).|
|**tm_mday**|Den v měsíci (1-31).|
|**tm_mon**|Měsíc (0 - 11; Ledna = 0).|
|**tm_year**|Rok (aktuálního roku minus 1900).|
|**tm_wday**|Den v týdnu (0 - 6; Neděle = 0).|
|**tm_yday**|Den v roce (0 - 365; 1. ledna = 0).|
|**tm_isdst**|Kladnou hodnotu, pokud letní čas je v platnosti; 0, pokud letní čas není platný; Pokud má neznámý stav letní čas zápornou hodnotu.|

Pokud **TZ** proměnná prostředí je nastavena, běhové knihovny jazyka C předpokládá pravidla vhodné pro Spojené státy pro implementaci výpočtu letní čas (letní čas).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaná hlavička C|Požadovaná hlavička v C++|
|-------------|---------------------|-|
|**localtime_s –**, **_localtime32_s –**, **_localtime64_s –**|\<Time.h >|\<CTime – > nebo \<time.h >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

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

[Správa času](../../c-runtime-library/time-management.md)<br/>
[asctime_s, _wasctime_s](asctime-s-wasctime-s.md)<br/>
[ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime_s, _gmtime32_s, _gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)<br/>
[localtime, _localtime32, _localtime64](localtime-localtime32-localtime64.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
[_tzset](tzset.md)<br/>
