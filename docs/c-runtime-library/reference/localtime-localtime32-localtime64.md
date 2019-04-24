---
title: localtime, _localtime32, _localtime64
ms.date: 11/04/2016
apiname:
- _localtime64
- _localtime32
- localtime
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
- localtime64
- _localtime64
- localtime32
- localtime
- _localtime32
helpviewer_keywords:
- localtime32 function
- _localtime32 function
- _localtime64 function
- localtime64 function
- localtime function
- time, converting values
ms.assetid: 4260ec3d-43ee-4538-b998-402a282bb9b8
ms.openlocfilehash: d34a45ff20cb74d61a8eb189282bfdce4d8954ae
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62157510"
---
# <a name="localtime-localtime32-localtime64"></a>localtime, _localtime32, _localtime64

Převede časovou hodnotu a pro místní časové pásmo opraví. Bezpečnější verze těchto funkcí jsou k dispozici. Zobrazit [localtime_s – _localtime32_s –, _localtime64_s –](localtime-s-localtime32-s-localtime64-s.md).

## <a name="syntax"></a>Syntaxe

```C
struct tm *localtime( const time_t *sourceTime );
struct tm *_localtime32( const __time32_t *sourceTime );
struct tm *_localtime64( const __time64_t *sourceTime );
```

### <a name="parameters"></a>Parametry

*sourceTime*<br/>
Ukazatel na uložený čas.

## <a name="return-value"></a>Návratová hodnota

Vrací ukazatel na strukturu výsledek nebo **NULL** datum předán do funkce je:

- Před půlnocí, 1. ledna 1970.

- Po 03:14:07, 19. ledna 2038 UTC (pomocí **_time32 –** a **time32_t**).

- Po 23:59:59, 31 prosince 3000 UTC (pomocí **_time64** a **__time64_t –**).

**_localtime64**, který používá **__time64_t –** struktury, umožňuje data vyjadřují až do 23:59:59, 31 prosince 3000 koordinovaného univerzálního času (UTC), zatímco **_localtime32** představuje data do 23:59:59 18. ledna 2038 UTC.

**localtime** je vložená funkce, která je vyhodnocena na **_localtime64**, a **time_t** je ekvivalentní **__time64_t –**. Pokud je nutné donutit kompilátor k interpretaci **time_t** jako staré 32bitové **time_t**, můžete definovat **_USE_32BIT_TIME_T**. To způsobí, že to **localtime** vyhodnotilo **_localtime32**. Toto nastavení nedoporučujeme, protože může vaše aplikace selhat po 18. ledna 2038, a to není povoleno na 64bitových platformách.

Pole typu Struktura [tm](../../c-runtime-library/standard-types.md) ukládat následující hodnoty, z nichž každý je **int**:

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

Pokud **TZ** nastavení proměnné prostředí, knihovny run-time jazyka C předpokládá pravidla vhodné Spojených států pro implementaci výpočtu letního času – času (DST).

## <a name="remarks"></a>Poznámky

**Localtime** funkce převede uložené jako čas [time_t](../../c-runtime-library/standard-types.md) hodnotu a výsledek je uložen na strukturu typu [tm](../../c-runtime-library/standard-types.md). **Dlouhé** hodnotu *sourceTime* představuje sekundách uplynulých od půlnoci (00: 00:00), 1. ledna 1970, UTC. Tato hodnota se obvykle získá z [čas](time-time32-time64.md) funkce.

32bitové a 64bitové verze systému [gmtime](gmtime-gmtime32-gmtime64.md), [mktime](mktime-mktime32-mktime64.md), [mkgmtime –](mkgmtime-mkgmtime32-mkgmtime64.md), a **localtime** vše pomocí jediné **tm** struktury na vlákno pro převod. Každé volání některé z těchto rutin ničí výsledek předchozího volání.

**localtime** pro místní časové pásmo opraví, pokud uživatel nejprve nastaví proměnnou prostředí globální **TZ**. Když **TZ** nastavena tři další proměnné prostředí (**_timezone**, **_daylight**, a **_tzname**) se automaticky nastaví také. Pokud **TZ** proměnná není nastavená, **localtime** pokusí použít informace o časovém pásmu, zadaný v aplikaci datum/čas v Ovládacích panelech. Pokud nelze získat tyto informace, se standardně používá PST8PDT, což znamená tichomořské časové pásmo. Zobrazit [_tzset –](tzset.md) popis těchto proměnných. **TZ** je rozšíření společnosti Microsoft a není součástí standardní definice ANSI **localtime**.

> [!NOTE]
> Cílové prostředí snažte se zjistit, zda je v platnosti letní čas.

Tyto funkce ověřují své parametry. Pokud *sourceTime* je ukazatel s hodnotou null, nebo pokud *sourceTime* hodnota je negativní, tyto funkce vyvolají obslužnou rutinu neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md) . Pokud provádění může pokračovat, vrátí funkce **NULL** a nastavte **errno** k **EINVAL**.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaná hlavička C|Požadované hlaviček jazyka C++|
|-------------|---------------------|-|
|**localtime**, **_localtime32**, **_localtime64**|\<time.h>|\<CTime – > nebo \<time.h >|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_localtime.cpp
// compile with: /W3
// This program uses _time64 to get the current time
// and then uses localtime64() to convert this time to a structure
// representing the local time. The program converts the result
// from a 24-hour clock to a 12-hour clock and determines the
// proper extension (AM or PM).

#include <stdio.h>
#include <string.h>
#include <time.h>

int main( void )
{
    struct tm *newtime;
    char am_pm[] = "AM";
    __time64_t long_time;

    _time64( &long_time );             // Get time as 64-bit integer.
                                       // Convert to local time.
    newtime = _localtime64( &long_time ); // C4996
    // Note: _localtime64 deprecated; consider _localetime64_s

    if( newtime->tm_hour > 12 )        // Set up extension.
        strcpy_s( am_pm, sizeof(am_pm), "PM" );
    if( newtime->tm_hour > 12 )        // Convert from 24-hour
        newtime->tm_hour -= 12;        //   to 12-hour clock.
    if( newtime->tm_hour == 0 )        // Set hour to 12 if midnight.
        newtime->tm_hour = 12;

    char buff[30];
    asctime_s( buff, sizeof(buff), newtime );
    printf( "%.19s %s\n", buff, am_pm );
}
```

```Output
Tue Feb 12 10:05:58 AM
```

## <a name="see-also"></a>Viz také:

[Správa času](../../c-runtime-library/time-management.md)<br/>
[asctime, _wasctime](asctime-wasctime.md)<br/>
[ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime, _gmtime32, _gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime_s, _localtime32_s, _localtime64_s](localtime-s-localtime32-s-localtime64-s.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
[_tzset](tzset.md)<br/>
