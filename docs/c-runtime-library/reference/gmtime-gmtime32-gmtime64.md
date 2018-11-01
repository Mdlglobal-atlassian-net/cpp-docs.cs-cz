---
title: gmtime, _gmtime32, _gmtime64
ms.date: 11/04/2016
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
helpviewer_keywords:
- gmtime32 function
- _gmtime64 function
- gmtime function
- time functions
- _gmtime32 function
- gmtime64 function
- time structure conversion
ms.assetid: 315501f3-477e-475d-a414-ef100ee0db27
ms.openlocfilehash: 4f32da5920a0cb892619195207d6501a4b1fd874
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50479999"
---
# <a name="gmtime-gmtime32-gmtime64"></a>gmtime, _gmtime32, _gmtime64

Převede **time_t** čas hodnota, která má **tm** struktury. Bezpečnější verze těchto funkcí jsou k dispozici. Zobrazit [gmtime_s – _gmtime32_s –, _gmtime64_s –](gmtime-s-gmtime32-s-gmtime64-s.md).

## <a name="syntax"></a>Syntaxe

```C
struct tm *gmtime( const time_t *sourceTime );
struct tm *_gmtime32( const __time32_t *sourceTime );
struct tm *_gmtime64( const __time64_t *sourceTime );
```

### <a name="parameters"></a>Parametry

*sourceTime*<br/>
Ukazatel na uložený čas. Čas je vyjádřen v sekundách uplynulých od půlnoci (00: 00:00), 1. ledna 1970, koordinovaného univerzálního času (UTC).

## <a name="return-value"></a>Návratová hodnota

Ukazatel na strukturu typu [tm](../../c-runtime-library/standard-types.md). Pole vrácené struktury obsahují vyhodnocenou hodnotu z *sourceTime* argument ve standardu UTC, nikoli v místním čase. Každé pole struktury je typu **int**, následujícím způsobem:

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
|**tm_isdst**|Vždy 0 pro **gmtime**.|

32bitové a 64bitové verze systému **gmtime**, [mktime](mktime-mktime32-mktime64.md), [mkgmtime –](mkgmtime-mkgmtime32-mkgmtime64.md), a [localtime](localtime-localtime32-localtime64.md) používají jednu společnou **tm**  struktury na vlákno pro převod. Každé volání některé z těchto funkcí ničí výsledek jakéhokoli předchozího volání. Pokud *sourceTime* představuje datum před půlnocí, 1. ledna 1970, **gmtime** vrátí **NULL**. Není vrácena žádná chyba.

**_gmtime64**, který používá **__time64_t –** struktury, umožňuje vyjádřit až do 23:59:59, 31 prosince 3000 UTC, zatímco **_gmtime32** pouze představuje data do 23:59:59 18. ledna 2038 UTC. Půlnoc 1. ledna 1970 je dolní mez rozsahu kalendářních dat pro obě funkce.

**gmtime** je vložená funkce, který se vyhodnotí **_gmtime64**, a **time_t** je ekvivalentní **__time64_t –** Pokud **_USE_32BIT_TIME_ T** je definována. Pokud je nutné donutit kompilátor k interpretaci **time_t** jako staré 32bitové **time_t**, můžete definovat **_USE_32BIT_TIME_T**, způsobí tak ale **gmtime** bude vloží do **_gmtime32** a **time_t** je definovat jako **__time32_t**. Doporučujeme vám, že vám to nedělali, protože to není povoleno na 64bitových platformách a v každém případě může vaše aplikace selhat po 18. ledna 2038.

Tyto funkce ověřují své parametry. Pokud *sourceTime* je ukazatel s hodnotou null, nebo pokud *sourceTime* hodnota je negativní, tyto funkce vyvolají obslužnou rutinu neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md) . Pokud provádění může pokračovat, vrátí funkce **NULL** a nastavte **errno** k **EINVAL**.

## <a name="remarks"></a>Poznámky

**_Gmtime32** rozdělí funkci *sourceTime* hodnoty a uloží ji do staticky přidělené struktury typu **tm**definovaná v čase. H. Hodnota *sourceTime* se obvykle získá z volání [čas](time-time32-time64.md) funkce.

> [!NOTE]
> Ve většině případů cílové prostředí zkusí zjistit, jestli je v platnosti letní čas. Knihovny run-time jazyka C předpokládá, že jsou použita pravidla Spojených států pro implementaci výpočtu letního času (DST).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaná hlavička C|Požadované hlaviček jazyka C++|
|-------------|---------------------|-|
|**gmtime**, **_gmtime32**, **_gmtime64**|\<Time.h >|\<CTime – > nebo \<time.h >|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Viz také:

[Správa času](../../c-runtime-library/time-management.md)<br/>
[asctime, _wasctime](asctime-wasctime.md)<br/>
[ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime_s, _gmtime32_s, _gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)<br/>
[localtime, _localtime32, _localtime64](localtime-localtime32-localtime64.md)<br/>
[_mkgmtime, _mkgmtime32, _mkgmtime64](mkgmtime-mkgmtime32-mkgmtime64.md)<br/>
[mktime, _mktime32, _mktime64](mktime-mktime32-mktime64.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
