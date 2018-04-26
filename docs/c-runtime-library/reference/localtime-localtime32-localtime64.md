---
title: místní čas, _localtime32 –, _localtime64 – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- localtime32 function
- _localtime32 function
- _localtime64 function
- localtime64 function
- localtime function
- time, converting values
ms.assetid: 4260ec3d-43ee-4538-b998-402a282bb9b8
caps.latest.revision: 28
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 32b462dfbe794d1817fa727736452e961a2b1dfd
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2018
---
# <a name="localtime-localtime32-localtime64"></a>localtime, _localtime32, _localtime64

Převede hodnotu času a opravuje pro místní časovou zónu. Bezpečnější verze tyto funkce jsou k dispozici. v tématu [localtime_s – _localtime32_s –, _localtime64_s –](localtime-s-localtime32-s-localtime64-s.md).

## <a name="syntax"></a>Syntaxe

```C
struct tm *localtime( const time_t *sourceTime );
struct tm *_localtime32( const __time32_t *sourceTime );
struct tm *_localtime64( const __time64_t *sourceTime );
```

### <a name="parameters"></a>Parametry

*sourceTime*<br/>
Ukazatel na uložené čas.

## <a name="return-value"></a>Návratová hodnota

Vrátí ukazatel na strukturu výsledek nebo **NULL** Pokud funkci byl předán datum:

- Před půlnoc, 1. ledna 1970.

- Po 03:14:07, 19. ledna 2038, UTC (pomocí **_time32 –** a **time32_t**).

- Po 23:59:59, 31. prosince 3000, UTC (pomocí **_time64 –** a **__time64_t –**).

**_localtime64 –**, které používá **__time64_t –** struktury, umožňuje data, která se vyjádřit až do 23:59:59, 31. prosince 3000, koordinovaný světový čas (UTC), zatímco **_localtime32 –** představuje data do 23:59:59 18 leden 2038 UTC.

**místní čas** vložená funkce, jehož výsledkem je **_localtime64 –**, a **time_t** je ekvivalentní **__time64_t –**. Pokud potřebujete vynutit kompilátoru interpretovat **time_t** jako starý 32bitovou verzi **time_t**, můžete definovat **_USE_32BIT_TIME_T**. Provedete to způsobí, že **místní čas** k vyhodnocení **_localtime32 –**. Není doporučeno, protože vaše aplikace může selhat po 18. ledna 2038, a není povoleno na 64bitových platformách.

Pole typu Struktura [tm](../../c-runtime-library/standard-types.md) ukládat následující hodnoty, z nichž každý je **int**:

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

Pokud **TZ** proměnná prostředí je nastavena, běhové knihovny jazyka C předpokládá pravidla vhodné pro Spojené státy pro implementaci výpočtu letního času ukládání – letního času.

## <a name="remarks"></a>Poznámky

**Místní čas** funkce převede čas uložené jako [time_t](../../c-runtime-library/standard-types.md) hodnotu a výsledek je uložen ve struktuře typu [tm](../../c-runtime-library/standard-types.md). **Dlouho** hodnotu *sourceTime* představuje počet sekund uběhlých od půlnoci (00: 00:00), 1. ledna 1970, UTC. Tato hodnota se obvykle získávají z [čas](time-time32-time64.md) funkce.

32bitové a 64bitové verze systému [gmtime –](gmtime-gmtime32-gmtime64.md), [mktime –](mktime-mktime32-mktime64.md), [mkgmtime –](mkgmtime-mkgmtime32-mkgmtime64.md), a **místní čas** všichni používají jeden **tm** struktura na vlákno pro převod. Každé volání na jednu z těchto rutin zničí výsledek předchozí volání.

**místní čas** vyřeší pro místní časovou zónu, pokud uživatel nejprve nastaví proměnnou prostředí globální **TZ**. Když **TZ** nastavena, tři další systémové proměnné (**_timezone**, **_daylight**, a **_tzname**) se nastaví automaticky také. Pokud **TZ** proměnná není nastavena, **místní čas** pokusí použít informace o časovém pásmu, který je zadán v aplikaci datum a čas v Ovládacích panelech. Pokud tyto informace nelze získat, PST8PDT, která označuje, že tichomořském časovém pásmu, se používá ve výchozím nastavení. V tématu [_tzset –](tzset.md) popis těchto proměnných. **TZ** je rozšíření Microsoft a není součástí standardní definice ANSI **místní čas**.

> [!NOTE]
> Cílové prostředí by měl pokusit určit, zda je v platnosti letní čas.

Tyto funkce ověřit jejich parametrů. Pokud *sourceTime* je ukazatel s hodnotou null, nebo pokud *sourceTime* je hodnota záporná, tyto funkce vyvolat obslužnou rutinu neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md) . Pokud je povoleno spuštění chcete-li pokračovat, vrátí funkce **NULL** a nastavte **errno** k **einval –**.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaná hlavička C|Požadovaná hlavička v C++|
|-------------|---------------------|-|
|**místní čas**, **_localtime32 –**, **_localtime64 –**|\<Time.h >|\<CTime – > nebo \<time.h >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

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

[Správa času](../../c-runtime-library/time-management.md)<br/>
[asctime, _wasctime](asctime-wasctime.md)<br/>
[ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime, _gmtime32, _gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime_s, _localtime32_s, _localtime64_s](localtime-s-localtime32-s-localtime64-s.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
[_tzset](tzset.md)<br/>
