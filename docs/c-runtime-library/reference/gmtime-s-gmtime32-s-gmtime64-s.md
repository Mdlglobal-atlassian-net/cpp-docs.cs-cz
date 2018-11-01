---
title: gmtime_s, _gmtime32_s, _gmtime64_s
ms.date: 11/04/2016
apiname:
- _gmtime32_s
- gmtime_s
- _gmtime64_s
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
- _gmtime_s
- gmtime64_s
- gmtime32_s
- _gmtime64_s
- gmtime_s
- _gmtime32_s
helpviewer_keywords:
- gmtime_s function
- gmtime32_s function
- time functions
- gmtime64_s function
- _gmtime64_s function
- time structure conversion
- _gmtime_s function
- _gmtime32_s function
ms.assetid: 261c7df0-2b0c-44ba-ba61-cb83efaec60f
ms.openlocfilehash: 1d9bfc7858dbc718e0f6c07358c5ebcec546063e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50650005"
---
# <a name="gmtimes-gmtime32s-gmtime64s"></a>gmtime_s, _gmtime32_s, _gmtime64_s

Převede hodnotu času **tm** struktury. Jde o verzích [_gmtime32, _gmtime64](gmtime-gmtime32-gmtime64.md) s rozšířeními zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
errno_t gmtime_s(
   struct tm* tmDest,
   const __time_t* sourceTime
);
errno_t _gmtime32_s(
   struct tm* tmDest,
   const __time32_t* sourceTime
);
errno_t _gmtime64_s(
   struct tm* tmDest,
   const __time64_t* sourceTime
);
```

### <a name="parameters"></a>Parametry

*tmDest*<br/>
Ukazatel [tm](../../c-runtime-library/standard-types.md) struktury. Pole vrácené struktury obsahují vyhodnocenou hodnotu z *časovače* argument ve standardu UTC, nikoli v místním čase.

*sourceTime*<br/>
Ukazatel na uložený čas. Čas je vyjádřen v sekundách uplynulých od půlnoci (00: 00:00), 1. ledna 1970, koordinovaného univerzálního času (UTC).

## <a name="return-value"></a>Návratová hodnota

Nula v případě úspěchu. Vrácená hodnota je kód chyby, pokud dojde k selhání. Kódy chyb jsou definovány v Errno.h; seznam těchto chyb, naleznete v tématu [errno](../../c-runtime-library/errno-constants.md).

### <a name="error-conditions"></a>Chybové podmínky

|*tmDest*|*sourceTime*|Vrátí|Hodnota v *tmDest*|
|-----------|------------|------------|--------------------|
|**HODNOTU NULL**|Všechny|**EINVAL**|Nedojde ke změně.|
|Není **NULL** (odkazuje na platný paměti)|**HODNOTU NULL**|**EINVAL**|Všechna pole nastavena na hodnotu -1.|
|Není **NULL**|< 0|**EINVAL**|Všechna pole nastavena na hodnotu -1.|

V případě první dvě chybové stavy, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud smí provádění pokračovat, tyto funkce nastaví **errno** k **EINVAL** a vrátit **EINVAL**.

## <a name="remarks"></a>Poznámky

**_Gmtime32_s –** rozdělí funkci *sourceTime* hodnoty a uloží jej v strukturu typu **tm**, definované v souboru Time.h. Předaná adresa struktury *tmDest*. Hodnota *sourceTime* se obvykle získá z volání [čas](time-time32-time64.md) funkce.

> [!NOTE]
> Cílové prostředí snažte se zjistit, zda je v platnosti letní čas. Knihovny run-time jazyka C předpokládá pravidla Spojených států pro implementaci výpočtu letního času.

Každé pole struktury je typu **int**, jak je znázorněno v následující tabulce.

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
|**tm_isdst**|Vždy 0 pro **gmtime_s –**.|

**_gmtime64_s –**, který používá **__time64_t –** struktury, umožňuje data vyjadřují až do 23:59:59, 31 prosince 3000 UTC, zatímco **gmtime32_s –** pouze představuje data do 23:59:59 18. ledna 2038 UTC. Půlnoc 1. ledna 1970 je dolní mez rozsahu kalendářních dat pro obě tyto funkce.

**gmtime_s –** je vložená funkce, která je vyhodnocena na **_gmtime64_s –** a **time_t** je ekvivalentní **__time64_t –**. Pokud je nutné donutit kompilátor k interpretaci **time_t** jako staré 32bitové **time_t**, můžete definovat **_USE_32BIT_TIME_T**. To způsobí, že to **gmtime_s –** bude vloží do **_gmtime32_s –**. Toto nastavení nedoporučujeme, protože může vaše aplikace selhat po 18. ledna 2038, a to není povoleno na 64bitových platformách.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaná hlavička C|Požadované hlaviček jazyka C++|
|-------------|---------------------|-|
|**gmtime_s**|, **_gmtime32_s –**, **_gmtime64_s –**|\<Time.h >|\<CTime – > nebo \<time.h >|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_gmtime64_s.c
// This program uses _gmtime64_s to convert a 64-bit
// integer representation of coordinated universal time
// to a structure named newtime, then uses asctime_s to
// convert this structure to an output string.

#include <time.h>
#include <stdio.h>

int main( void )
{
   struct tm newtime;
   __int64 ltime;
   char buf[26];
   errno_t err;

   _time64( &ltime );

   // Obtain coordinated universal time:
   err = _gmtime64_s( &newtime, &ltime );
   if (err)
   {
      printf("Invalid Argument to _gmtime64_s.");
   }

   // Convert to an ASCII representation
   err = asctime_s(buf, 26, &newtime);
   if (err)
   {
      printf("Invalid Argument to asctime_s.");
   }

   printf( "Coordinated universal time is %s\n",
           buf );
}
```

```Output
Coordinated universal time is Fri Apr 25 20:12:33 2003
```

## <a name="see-also"></a>Viz také:

[Správa času](../../c-runtime-library/time-management.md)<br/>
[asctime_s, _wasctime_s](asctime-s-wasctime-s.md)<br/>
[ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime, _gmtime32, _gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime_s, _localtime32_s, _localtime64_s](localtime-s-localtime32-s-localtime64-s.md)<br/>
[_mkgmtime, _mkgmtime32, _mkgmtime64](mkgmtime-mkgmtime32-mkgmtime64.md)<br/>
[mktime, _mktime32, _mktime64](mktime-mktime32-mktime64.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
