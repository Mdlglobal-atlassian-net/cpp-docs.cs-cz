---
title: gmtime_s – _gmtime32_s –, _gmtime64_s – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b15896ff9ec96ed8dd9867c14d252edaad2c67a2
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32405273"
---
# <a name="gmtimes-gmtime32s-gmtime64s"></a>gmtime_s, _gmtime32_s, _gmtime64_s

Převede hodnotu na čas **tm** struktura. Toto jsou verze [_gmtime32 –, _gmtime64 –](gmtime-gmtime32-gmtime64.md) vylepšení zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

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
Ukazatel na [tm](../../c-runtime-library/standard-types.md) struktura. Pole vrácené struktury uložení vyhodnotí hodnotu *časovače* argument ve standardu UTC, spíše než v místním čase.

*sourceTime*<br/>
Ukazatel na uložené čas. Čas je reprezentována jako sekund uběhlých od půlnoci (00: 00:00), 1. ledna 1970, koordinovaný světový čas (UTC).

## <a name="return-value"></a>Návratová hodnota

Nula v případě úspěchu. Vrácená hodnota je kód chyby, pokud dojde k selhání. Kódy chyb jsou definovány v Errno.h; seznam těchto chybách naleznete v tématu [errno](../../c-runtime-library/errno-constants.md).

### <a name="error-conditions"></a>Chybové stavy

|*tmDest*|*sourceTime*|Vrátí|Hodnota v *tmDest*|
|-----------|------------|------------|--------------------|
|**HODNOTU NULL**|všechny|**EINVAL –**|Nedojde ke změně.|
|Není **NULL** (odkazuje na platný paměti)|**HODNOTU NULL**|**EINVAL –**|Všechna pole je nastaven na hodnotu -1.|
|není **hodnotu NULL.**|< 0|**EINVAL –**|Všechna pole je nastaven na hodnotu -1.|

V případě první dvě chybové stavy, je vyvolána obslužná rutina neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění pokračovat, nastavte tyto funkce **errno** k **einval –** a vrátit **einval –**.

## <a name="remarks"></a>Poznámky

**_Gmtime32_s –** funkce, které jsou rozděleny *sourceTime* hodnotu a ukládá je do struktury typu **tm**, definované v Time.h. Předaná adresa struktury *tmDest*. Hodnota *sourceTime* se obvykle získávají z volání [čas](time-time32-time64.md) funkce.

> [!NOTE]
> Cílové prostředí by měl pokusit určit, zda je v platnosti letní čas. Běhové knihovny jazyka C předpokládá Spojených států pravidla pro implementaci výpočtu letní čas.

Každé pole struktura je typu **int**, jak je znázorněno v následující tabulce.

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
|**tm_isdst**|Vždy 0 pro **gmtime_s –**.|

**_gmtime64_s –**, které používá **__time64_t –** struktury, umožňuje data, která se vyjádřit až do 23:59:59, 31. prosince 3000, UTC; zatímco **gmtime32_s –** pouze představují data prostřednictvím 23:59:59 18 leden 2038 UTC. Půlnoc, 1. ledna 1970, je dolní mez rozsahu kalendářních dat pro obě tyto funkce.

**gmtime_s –** vložená funkce, jehož výsledkem je **_gmtime64_s –** a **time_t** je ekvivalentní **__time64_t –**. Pokud potřebujete vynutit kompilátoru interpretovat **time_t** jako starý 32bitovou verzi **time_t**, můžete definovat **_USE_32BIT_TIME_T**. Provedete to způsobí, že **gmtime_s –** jako v leží na **_gmtime32_s –**. Není doporučeno, protože vaše aplikace může selhat po 18. ledna 2038, a není povoleno na 64bitových platformách.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaná hlavička C|Požadovaná hlavička v C++|
|-------------|---------------------|-|
|**gmtime_s**|, **_gmtime32_s –**, **_gmtime64_s –**|\<Time.h >|\<CTime – > nebo \<time.h >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

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

[Správa času](../../c-runtime-library/time-management.md)<br/>
[asctime_s, _wasctime_s](asctime-s-wasctime-s.md)<br/>
[ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime, _gmtime32, _gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime_s, _localtime32_s, _localtime64_s](localtime-s-localtime32-s-localtime64-s.md)<br/>
[_mkgmtime, _mkgmtime32, _mkgmtime64](mkgmtime-mkgmtime32-mkgmtime64.md)<br/>
[mktime, _mktime32, _mktime64](mktime-mktime32-mktime64.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
