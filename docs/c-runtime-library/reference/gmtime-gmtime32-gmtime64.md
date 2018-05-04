---
title: gmtime – _gmtime32 –, _gmtime64 – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _gmtime32
- gmtime
- _gmtime64
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
- gmtime
- _gmtime32
- _gmtime64
dev_langs:
- C++
helpviewer_keywords:
- gmtime32 function
- _gmtime64 function
- gmtime function
- time functions
- _gmtime32 function
- gmtime64 function
- time structure conversion
ms.assetid: 315501f3-477e-475d-a414-ef100ee0db27
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 28ce8b8e2367e1d4dd26672206557867c07827e5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="gmtime-gmtime32-gmtime64"></a>gmtime, _gmtime32, _gmtime64

Převede **time_t** čas hodnotu **tm** struktura. Bezpečnější verze tyto funkce jsou k dispozici. v tématu [gmtime_s – _gmtime32_s –, _gmtime64_s –](gmtime-s-gmtime32-s-gmtime64-s.md).

## <a name="syntax"></a>Syntaxe

```C
struct tm *gmtime( const time_t *sourceTime );
struct tm *_gmtime32( const __time32_t *sourceTime );
struct tm *_gmtime64( const __time64_t *sourceTime );
```

### <a name="parameters"></a>Parametry

*sourceTime*<br/>
Ukazatel na uložené čas. Čas je reprezentována jako sekund uběhlých od půlnoci (00: 00:00), 1. ledna 1970, koordinovaný světový čas (UTC).

## <a name="return-value"></a>Návratová hodnota

Ukazatel na strukturu typu [tm](../../c-runtime-library/standard-types.md). Pole vrácené struktury uložení vyhodnotí hodnotu *sourceTime* argument ve standardu UTC, spíše než v místním čase. Každé pole struktura je typu **int**, a to takto:

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
|**tm_isdst**|Vždy 0 pro **gmtime –**.|

32bitové a 64bitové verze systému **gmtime –**, [mktime –](mktime-mktime32-mktime64.md), [mkgmtime –](mkgmtime-mkgmtime32-mkgmtime64.md), a [místní čas](localtime-localtime32-localtime64.md) všichni používají jeden běžné **tm**  struktura na vlákno pro převod. Každé volání jednu z těchto funkcí zničí výsledek všech předchozích volání. Pokud *sourceTime* představuje datum před půlnoc, 1. ledna 1970 **gmtime –** vrátí **NULL**. Neexistuje žádný návratový chyby.

**_gmtime64 –**, které používá **__time64_t –** struktury, umožňuje data, která se vyjádřit až do 23:59:59, 31. prosince 3000, UTC, zatímco **_gmtime32 –** pouze představují datům až 23:59:59 18. ledna 2038, UTC. Půlnoc, 1. ledna 1970, je dolní mez rozsahu kalendářních dat pro obě funkce.

**gmtime –** je vložená funkce, která vyhodnotí jako **_gmtime64 –**, a **time_t** je ekvivalentní **__time64_t –** Pokud **_USE_32BIT_TIME_ T** je definována. Pokud musíte vynutit kompilátoru interpretovat **time_t** jako starý 32bitovou verzi **time_t**, můžete definovat **_USE_32BIT_TIME_T**, ale to Ano příčiny **gmtime –** jako v leží na **_gmtime32 –** a **time_t** být definován jako **__time32_t**. Doporučujeme vám, že neprovedete, protože není povolená na 64bitových platformách a v každém případě mohou vaše aplikace po 18 leden 2038 selhat.

Tyto funkce ověřit jejich parametrů. Pokud *sourceTime* je ukazatel s hodnotou null, nebo pokud *sourceTime* je hodnota záporná, tyto funkce vyvolat obslužnou rutinu neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md) . Pokud je povoleno spuštění chcete-li pokračovat, vrátí funkce **NULL** a nastavte **errno** k **einval –**.

## <a name="remarks"></a>Poznámky

**_Gmtime32 –** funkce, které jsou rozděleny *sourceTime* hodnotu a ukládá je do staticky přidělené struktury typu **tm**definovaná v čase. H. Hodnota *sourceTime* je obvykle získané z volání [čas](time-time32-time64.md) funkce.

> [!NOTE]
> Ve většině případů se pokusí zjistit, zda je v platnosti letní čas cílovém prostředí. Běhové knihovny jazyka C předpokládá, že se používá pravidla Spojených států k výpočtu letní čas (DST).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaná hlavička C|Požadovaná hlavička v C++|
|-------------|---------------------|-|
|**gmtime –**, **_gmtime32 –**, **_gmtime64 –**|\<Time.h >|\<CTime – > nebo \<time.h >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_gmtime.c
// compile with: /W3
// This program uses _gmtime64 to convert a long-
// integer representation of coordinated universal time
// to a structure named newtime, then uses asctime to
// convert this structure to an output string.

#include <time.h>
#include <stdio.h>

int main( void )
{
   struct tm *newtime;
   __int64 ltime;
   char buff[80];

   _time64( &ltime );

   // Obtain coordinated universal time:
   newtime = _gmtime64( &ltime ); // C4996
   // Note: _gmtime64 is deprecated; consider using _gmtime64_s
   asctime_s( buff, sizeof(buff), newtime );
   printf( "Coordinated universal time is %s\n", buff );
}
```

```Output
Coordinated universal time is Tue Feb 12 23:11:31 2002
```

## <a name="see-also"></a>Viz také

[Správa času](../../c-runtime-library/time-management.md)<br/>
[asctime, _wasctime](asctime-wasctime.md)<br/>
[ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime_s, _gmtime32_s, _gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)<br/>
[localtime, _localtime32, _localtime64](localtime-localtime32-localtime64.md)<br/>
[_mkgmtime, _mkgmtime32, _mkgmtime64](mkgmtime-mkgmtime32-mkgmtime64.md)<br/>
[mktime, _mktime32, _mktime64](mktime-mktime32-mktime64.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
