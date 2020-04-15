---
title: gmtime, _gmtime32, _gmtime64
ms.date: 4/2/2020
api_name:
- _gmtime32
- gmtime
- _gmtime64
- _o__gmtime32
- _o__gmtime64
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
- gmtime
- _gmtime32
- _gmtime64
helpviewer_keywords:
- gmtime32 function
- _gmtime64 function
- gmtime function
- time functions
- _gmtime32 function
- gmtime64 function
- time structure conversion
ms.assetid: 315501f3-477e-475d-a414-ef100ee0db27
ms.openlocfilehash: afa46e583437ebace8edd3a54a6d85e61e02854c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81344091"
---
# <a name="gmtime-_gmtime32-_gmtime64"></a>gmtime, _gmtime32, _gmtime64

Převede **hodnotu time_t** času na strukturu **tm.** K dispozici jsou bezpečnější verze těchto funkcí. viz [gmtime_s, _gmtime32_s, _gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md).

## <a name="syntax"></a>Syntaxe

```C
struct tm *gmtime( const time_t *sourceTime );
struct tm *_gmtime32( const __time32_t *sourceTime );
struct tm *_gmtime64( const __time64_t *sourceTime );
```

### <a name="parameters"></a>Parametry

*sourceTime*<br/>
Ukazatel na uložený čas. Čas je reprezentován jako sekundy, které uplynuly od půlnoci (00:00:00), 1.

## <a name="return-value"></a>Návratová hodnota

Ukazatel na strukturu typu [tm](../../c-runtime-library/standard-types.md). Pole vrácené struktury obsahovat vyhodnocenou hodnotu *sourceTime* argument v UTC spíše než v místním čase. Každé pole struktury je typu **int**, takto:

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
|**tm_isdst**|Vždy 0 pro **gmtime**.|

32bitové i 64bitové verze **gmtime**, [mktime](mktime-mktime32-mktime64.md), [mkgmtime](mkgmtime-mkgmtime32-mkgmtime64.md)a [localtime](localtime-localtime32-localtime64.md) používají pro převod jednu společnou strukturu **tm** na vlákno. Každé volání jedné z těchto funkcí zničí výsledek předchozího volání. Pokud *sourceTime* představuje datum před půlnocí 1. **gmtime** **NULL** Neexistuje žádná chyba vrátit.

**_gmtime64**, který používá **__time64_t** strukturu, umožňuje data, která mají být vyjádřena až do 23:59:59, Prosinec 31, 3000, UTC, zatímco **_gmtime32** představují pouze data do 23:59:59 Leden 18, 2038, UTC. Midnight, January 1, 1970, je dolní mez časového období pro obě funkce.

**gmtime** je vřadná funkce, která je vyhodnocena jako **_gmtime64**a **time_t** je ekvivalentní **__time64_t,** pokud **není definována _USE_32BIT_TIME_T.** Pokud je nutné vynutit, aby kompilátor interpretoval **time_t** jako starý 32bitový **time_t**, můžete definovat **_USE_32BIT_TIME_T**, ale to způsobí , že **gmtime** bude vložen do **_gmtime32** a **time_t** bude definován jako **__time32_t**. Doporučujeme, abyste to nedělali, protože to není povoleno na 64bitových platformách a v každém případě může vaše aplikace selhat po 18.

Tyto funkce ověřují jejich parametry. Pokud *sourceTime* je ukazatel null, nebo pokud *sourceTime* hodnota je záporná, tyto funkce vyvolat obslužnou rutinu neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je spuštění povoleno pokračovat, funkce vrátí **NULL** a nastavit **errno** **eINVAL**.

## <a name="remarks"></a>Poznámky

Funkce **_gmtime32** rozdělí hodnotu *sourceTime* a uloží ji do staticky přidělené struktury typu **tm**definované v čase. H. Hodnota *sourceTime* je obvykle získána z volání [časové](time-time32-time64.md) funkce.

> [!NOTE]
> Ve většině případů cílové prostředí se pokusí určit, zda letní čas je v platnosti. C run-time knihovna předpokládá, že pravidla Spojených států pro implementaci výpočtu letního času (DST) jsou používány.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Povinná hlavička C|Povinná hlavička jazyka C++|
|-------------|---------------------|-|
|**gmtime**, **_gmtime32**, **_gmtime64**|\<time.h>|\<ctime> \<nebo time.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

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

[Časová správa](../../c-runtime-library/time-management.md)<br/>
[asctime, _wasctime](asctime-wasctime.md)<br/>
[ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime_s, _gmtime32_s, _gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)<br/>
[localtime, _localtime32, _localtime64](localtime-localtime32-localtime64.md)<br/>
[_mkgmtime, _mkgmtime32, _mkgmtime64](mkgmtime-mkgmtime32-mkgmtime64.md)<br/>
[mktime, _mktime32, _mktime64](mktime-mktime32-mktime64.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
