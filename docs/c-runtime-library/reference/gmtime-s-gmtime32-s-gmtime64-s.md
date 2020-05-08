---
title: gmtime_s, _gmtime32_s, _gmtime64_s
ms.date: 4/2/2020
api_name:
- _gmtime32_s
- gmtime_s
- _gmtime64_s
- _o__gmtime32_s
- _o__gmtime64_s
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
ms.openlocfilehash: 152b0569d452fc48af7583b23c6a2449cb24d0d6
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82916220"
---
# <a name="gmtime_s-_gmtime32_s-_gmtime64_s"></a>gmtime_s, _gmtime32_s, _gmtime64_s

Převede hodnotu času na strukturu **TM** . Jedná se o verze [_gmtime32, _gmtime64](gmtime-gmtime32-gmtime64.md) s vylepšeními zabezpečení, jak je popsáno v [části funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

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
Ukazatel na strukturu [TM](../../c-runtime-library/standard-types.md) . Pole vrácené struktury uchovávají vyhodnocenou hodnotu argumentu *časovače* v čase UTC, nikoli v místním čase.

*sourceTime*<br/>
Ukazatel na uložený čas. Čas je vyjádřený jako sekund uplynulý od půlnoci (00:00:00), od 1. ledna 1970 a koordinovaného univerzálního času (UTC).

## <a name="return-value"></a>Návratová hodnota

Nula v případě úspěchu. Návratová hodnota je kód chyby, pokud dojde k selhání. Kódy chyb jsou definovány v errno. h; Seznam těchto chyb naleznete v tématu [errno](../../c-runtime-library/errno-constants.md).

### <a name="error-conditions"></a>Chybové stavy

|*tmDest*|*sourceTime*|Vrátit|Hodnota v *tmDest*|
|-----------|------------|------------|--------------------|
|**PLATNOST**|jakýmikoli|**EINVAL**|Nezměněno.|
|Není **null** (ukazuje na platnou paměť)|**PLATNOST**|**EINVAL**|Všechna pole jsou nastavena na hodnotu-1.|
|Není **null**|< 0|**EINVAL**|Všechna pole jsou nastavena na hodnotu-1.|

V případě první dvě chybové podmínky je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, tyto funkce nastaví **errno** na **EINVAL** a vrátí **EINVAL**.

## <a name="remarks"></a>Poznámky

Funkce **_gmtime32_s** rozdělí hodnotu *sourceTime* a uloží ji ve struktuře typu **TM**, definovaná v time. h. Adresa struktury se předává v *tmDest*. Hodnota *sourceTime* je obvykle získána voláním funkce [Time](time-time32-time64.md) .

> [!NOTE]
> Cílové prostředí by mělo zkusit zjistit, jestli je v platnosti letní čas. Knihovna run-time jazyka C předpokládá pravidla USA pro implementaci výpočtu letního času.

Každé pole struktury je typu **int**, jak je znázorněno v následující tabulce.

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
|**tm_isdst**|Vždy 0 pro **gmtime_s**.|

**_gmtime64_s**, která používá strukturu **__time64_t** , umožňuje, aby se data vyjádřila až 23:59:59, 31. prosince 3000, UTC; zatímco **gmtime32_s** reprezentují jenom data 23:59:59 do 18. ledna 2038, UTC. Půlnoc, 1. ledna 1970 je dolní mez rozsahu kalendářních dat obou těchto funkcí.

**gmtime_s** je vložená funkce, která se vyhodnocuje jako **_gmtime64_s** a **time_t** je ekvivalentem **__time64_t**. Pokud potřebujete vynutit, aby kompilátor interpretoval **time_t** jako starou **time_t**32, můžete definovat **_USE_32BIT_TIME_T**. Tím dojde k tomu, že **gmtime_s** být vloženy do **_gmtime32_s**. To se nedoporučuje, protože vaše aplikace může selhat i po 18. lednu 2038 a není povolená na 64 platformách.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Povinné záhlaví jazyka C|Požadovaná hlavička C++|
|-------------|---------------------|-|
|**gmtime_s**, **_gmtime32_s** **_gmtime64_s**|\<Time. h>|\<CTime –> nebo \<Time. h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Viz také

[Časová správa](../../c-runtime-library/time-management.md)<br/>
[asctime_s, _wasctime_s](asctime-s-wasctime-s.md)<br/>
[ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime, _gmtime32, _gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime_s, _localtime32_s, _localtime64_s](localtime-s-localtime32-s-localtime64-s.md)<br/>
[_mkgmtime, _mkgmtime32, _mkgmtime64](mkgmtime-mkgmtime32-mkgmtime64.md)<br/>
[mktime, _mktime32, _mktime64](mktime-mktime32-mktime64.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
