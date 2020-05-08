---
title: localtime, _localtime32, _localtime64
ms.date: 4/2/2020
api_name:
- _localtime64
- _localtime32
- localtime
- _o__localtime32
- _o__localtime64
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
ms.openlocfilehash: 764a3768610d97df2eb3af4ed0425065aba4b4fa
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82916415"
---
# <a name="localtime-_localtime32-_localtime64"></a>localtime, _localtime32, _localtime64

Převede hodnotu času a oprav pro místní časové pásmo. K dispozici jsou bezpečnější verze těchto funkcí; viz [localtime_s, _localtime32_s _localtime64_s](localtime-s-localtime32-s-localtime64-s.md).

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

Vrátí ukazatel na výsledek struktury nebo **hodnotu null** , pokud je datum předané funkci:

- Před půlnocí 1. ledna 1970.

- Až 03:14:07, 19. ledna 2038, UTC (pomocí **_time32** a **time32_t**).

- Po 23:59:59, 31. prosince 3000, UTC (pomocí **_time64** a **__time64_t**).

**_localtime64**, která používá strukturu **__time64_t** , umožňuje, aby data byla vyjádřena až 23:59:59, 31. prosince 3000, KOORDINOVANÝ světový čas (UTC), zatímco **_localtime32** představují kalendářní data prostřednictvím 23:59:59 15. ledna, 2038, UTC.

**localtime** je vložená funkce, která je vyhodnocena jako **_localtime64**a **time_t** je ekvivalentní **__time64_t**. Pokud potřebujete vynutit, aby kompilátor interpretoval **time_t** jako starou **time_t**32, můžete definovat **_USE_32BIT_TIME_T**. To způsobí, že se **localtime** vyhodnotí jako **_localtime32**. To se nedoporučuje, protože vaše aplikace může selhat i po 18. lednu 2038 a není povolená na 64 platformách.

Pole struktury typu [TM](../../c-runtime-library/standard-types.md) ukládají následující hodnoty, z nichž každá je **int**:

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

Pokud je nastavena proměnná prostředí **TZ** , knihovna run-time jazyka C předpokládá pravidla, která jsou vhodná pro USA pro implementaci výpočtu času letního času (DST).

## <a name="remarks"></a>Poznámky

Funkce **localtime** převede čas uložený jako hodnotu [time_t](../../c-runtime-library/standard-types.md) a výsledek uloží ve struktuře typu [TM](../../c-runtime-library/standard-types.md). Hodnota **Long** *sourceTime* představuje sekundy, které uplynuly od půlnoci (00:00:00), 1. ledna 1970, UTC. Tato hodnota je obvykle získána z funkce [Time](time-time32-time64.md) .

32 a 64 verze [gmtime](gmtime-gmtime32-gmtime64.md), [mktime](mktime-mktime32-mktime64.md), [mkgmtime](mkgmtime-mkgmtime32-mkgmtime64.md)a **localtime** používají pro převod jednu strukturu **TM** na vlákno. Každé volání jedné z těchto rutin zničí výsledek předchozího volání.

**localtime** správné pro místní časové pásmo, pokud uživatel napřed nastaví globální proměnnou prostředí na **TZ**. Je-li nastavena hodnotu **TZ** , jsou automaticky nastaveny i tři další proměnné prostředí (**_timezone**, **_daylight**a **_tzname**). Pokud není nastavena proměnná **TZ** , **localtime** se pokusí použít informace o časovém pásmu zadané v aplikaci datum/čas v Ovládacích panelech. Pokud tyto informace nelze získat, PST8PDT, který označuje časové pásmo tichomořského, se ve výchozím nastavení používá. Popis těchto proměnných naleznete v tématu [_tzset](tzset.md) . **TZ** je rozšíření společnosti Microsoft, které není součástí standardní definice standardu ANSI pro **localtime**.

> [!NOTE]
> Cílové prostředí by mělo zkusit zjistit, jestli je aktivní letní čas.

Tyto funkce ověřují své parametry. Pokud je *sourceTime* ukazatel s hodnotou null, nebo pokud je hodnota *sourceTime* záporná, tyto funkce vyvolají obslužnou rutinu neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, funkce vrátí **hodnotu null** a nastaví **errno** na **EINVAL**.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Povinné záhlaví jazyka C|Požadovaná hlavička C++|
|-------------|---------------------|-|
|**localtime**, **_localtime32** **_localtime64**|\<Time. h>|\<CTime –> nebo \<Time. h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Viz také

[Časová správa](../../c-runtime-library/time-management.md)<br/>
[asctime, _wasctime](asctime-wasctime.md)<br/>
[ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime, _gmtime32, _gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime_s, _localtime32_s, _localtime64_s](localtime-s-localtime32-s-localtime64-s.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
[_tzset](tzset.md)<br/>
