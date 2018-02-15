---
title: "_mkgmtime – _mkgmtime32 –, _mkgmtime64 – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _mkgmtime32
- _mkgmtime64
- _mkgmtime
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
- _mkgmtime64
- mkgmtime32
- _mkgmtime32
- mkgmtime
- mkgmtime64
- _mkgmtime
dev_langs:
- C++
helpviewer_keywords:
- mkgmtime32 function
- time functions
- mkgmtime function
- _mkgmtime function
- converting times
- mkgmtime64 function
- _mkgmtime64 function
- _mkgmtime32 function
- time, converting
ms.assetid: b4ca2b67-e198-4f43-b3e2-e8ad6bd01867
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7eec9b123c47b13c73836fd41a2c490951e4fecd
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="mkgmtime-mkgmtime32-mkgmtime64"></a>_mkgmtime, _mkgmtime32, _mkgmtime64
Převede čas UTC reprezentována `tm struct` čas UTC reprezentována `time_t` typu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      time_t _mkgmtime(  
   struct tm* timeptr  
);  
__time32_t _mkgmtime32(  
   struct tm* timeptr  
);  
__time64_t _mkgmtime64(  
   struct tm* timeptr  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `timeptr`  
 Ukazatel na čas UTC jako `struct tm` převést.  
  
## <a name="return-value"></a>Návratová hodnota  
 Množství typu `__time32_t` nebo `__time64_t` představující počet sekund uběhlých od půlnoci, 1. ledna 1970, koordinovaný světový čas (UTC). Pokud datum je mimo rozsah (naleznete v části poznámky) nebo vstup není možné interpretovat jako platný čas, je vrácenou hodnotu -1.  
  
## <a name="remarks"></a>Poznámky  
 `_mkgmtime32` a `_mkgmtime64` funkce převést na čas UTC `__time32_t` nebo `__time64_t` typu reprezentující čas v UTC. Chcete-li převést místního času na čas UTC, použijte `mktime`, `_mktime32`, a `_mktime64` místo.  
  
 `_mkgmtime` Vložená funkce, jehož výsledkem je `_mkgmtime64`, a `time_t` je ekvivalentní `__time64_t`. Pokud potřebujete vynutit kompilátoru interpretovat `time_t` jako starý 32bitovou verzi `time_t`, můžete definovat `_USE_32BIT_TIME_T`. Není doporučeno, protože vaše aplikace může selhat po 18 leden 2038 (maximální rozsah 32bitové `time_t`), a není povolena na všech na 64bitových platformách.  
  
 Čas struktura předaná se změní následujícím způsobem stejným způsobem, jako jsou změněna s `_mktime` funkce: `tm_wday` a `tm_yday` pole jsou nastaveny na nové hodnoty, které jsou založené na hodnotách `tm_mday` a `tm_year`. Při zadávání `tm` struktury čas, nastavte `tm_isdst` pole na:  
  
-   Nula (0) k označení, že (běžný čas) je v platnosti.  
  
-   Hodnota, která je větší než 0 k označení, že letní čas je v platnosti.  
  
-   Hodnotu menší než nula tak, aby měl kód běhové knihovny jazyka C výpočetní, zda (běžný čas) nebo letní čas je v platnosti.  
  
 Běhové knihovny jazyka C používá proměnnou prostředí TZ k určení správný letní čas. Pokud není nastavena TZ, operační systém je dotazován získat správné regionální letního času chování. `tm_isdst` je povinné pole. Pokud není nastavená, jeho hodnota může být definovaný a návratovou hodnotou z `mktime` předpovědět.  
  
 Rozsah `_mkgmtime32` funkce je od půlnoci 1. ledna 1970 UTC do 23:59:59 18 leden 2038 UTC. Rozsah `_mkgmtime64` je od půlnoci 1. ledna 1970 UTC do 23:59:59, 31. prosince 3000, UTC. Datum out-of-range výsledkem návratovou hodnotu-1. Rozsah `_mkgmtime` závisí na tom, zda `_USE_32BIT_TIME_T` je definována. Pokud není definována (výchozí) rozsah je u `_mkgmtime64`, jinak hodnota rozsahu je omezený na 32-bit rozsahu `_mkgmtime32`.  
  
 Všimněte si, že `gmtime` a `localtime` ke konverzi použijte jeden staticky přidělené vyrovnávací paměti. Pokud zadáte tento vyrovnávací paměť pro `mkgmtime`, jsou zničen předchozí obsah.  
  
## <a name="example"></a>Příklad  
  
```  
// crt_mkgmtime.c  
#include <stdio.h>  
#include <time.h>  
  
int main()  
{  
    struct tm t1, t2;  
    time_t now, mytime, gmtime;  
    char buff[30];  
  
    time( & now );  
  
    _localtime64_s( &t1, &now );  
    _gmtime64_s( &t2, &now );  
  
    mytime = mktime(&t1);  
    gmtime = _mkgmtime(&t2);  
  
    printf("Seconds since midnight, January 1, 1970\n");  
    printf("My time: %I64d\nGM time (UTC): %I64d\n\n", mytime, gmtime);  
  
    /* Use asctime_s to display these times. */  
  
    _localtime64_s( &t1, &mytime );  
    asctime_s( buff, sizeof(buff), &t1 );  
    printf( "Local Time: %s\n", buff );  
  
    _gmtime64_s( &t2, &gmtime );  
    asctime_s( buff, sizeof(buff), &t2 );  
    printf( "Greenwich Mean Time: %s\n", buff );  
  
}  
```  
  
## <a name="sample-output"></a>Vzorový výstup  
  
```  
Seconds since midnight, January 1, 1970  
My time: 1171588492  
GM time (UTC): 1171588492  
  
Local Time: Thu Feb 15 17:14:52 2007  
  
Greenwich Mean Time: Fri Feb 16 01:14:52 2007  
```  
  
 Následující příklad ukazuje, jak je neúplná struktura doplnit počítaný hodnotami den v týdnu a den v roce.  
  
```  
// crt_mkgmtime2.c  
#include <stdio.h>  
#include <time.h>  
#include <memory.h>  
  
int main()  
{  
    struct tm t1, t2;  
    time_t gmtime;  
    char buff[30];  
  
    memset(&t1, 0, sizeof(struct tm));  
    memset(&t2, 0, sizeof(struct tm));  
  
    t1.tm_mon = 1;  
    t1.tm_isdst = 0;  
    t1.tm_year = 103;  
    t1.tm_mday = 12;  
  
    // The day of the week and year will be incorrect in the output here.  
    asctime_s( buff, sizeof(buff), &t1);  
    printf("Before calling _mkgmtime, t1 = %s t.tm_yday = %d\n",  
            buff, t1.tm_yday );  
  
    gmtime = _mkgmtime(&t1);  
  
    // The correct day of the week and year were determined.  
    asctime_s( buff, sizeof(buff), &t1);  
    printf("After calling _mkgmtime, t1 = %s t.tm_yday = %d\n",  
            buff, t1.tm_yday );  
  
}  
```  
  
## <a name="output"></a>Výstup  
  
```  
Before calling _mkgmtime, t1 = Sun Feb 12 00:00:00 2003  
 t.tm_yday = 0  
After calling _mkgmtime, t1 = Wed Feb 12 00:00:00 2003  
 t.tm_yday = 42  
```  
  
## <a name="see-also"></a>Viz také  
 [Správa času](../../c-runtime-library/time-management.md)   
 [asctime, _wasctime](../../c-runtime-library/reference/asctime-wasctime.md)   
 [asctime_s, _wasctime_s](../../c-runtime-library/reference/asctime-s-wasctime-s.md)   
 [gmtime, _gmtime32, _gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)   
 [gmtime_s, _gmtime32_s, _gmtime64_s](../../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)   
 [localtime_s, _localtime32_s, _localtime64_s](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md)   
 [mktime, _mktime32, _mktime64](../../c-runtime-library/reference/mktime-mktime32-mktime64.md)   
 [time, _time32, _time64](../../c-runtime-library/reference/time-time32-time64.md)