---
title: "_ftime_s – _ftime32_s –, _ftime64_s – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _ftime_s
- _ftime64_s
- _ftime32_s
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
- _ftime_s
- _ftime64_s
- ftime_s
- _ftime32_s
- ftime32_s
- ftime64_s
dev_langs: C++
helpviewer_keywords:
- ftime32_s function
- ftime_s function
- _ftime64_s function
- current time
- ftime64_s function
- time, getting current
- _ftime_s function
- _ftime32_s function
ms.assetid: d03080d9-a520-45be-aa65-504bdb197e8b
caps.latest.revision: "24"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: eb90c8f9ed18355821e3a067b0f2b9b92562b08c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="ftimes-ftime32s-ftime64s"></a>_ftime_s, _ftime32_s, _ftime64_s
Získá aktuální čas. Toto jsou verze [_ftime – _ftime32 –, _ftime64 –](../../c-runtime-library/reference/ftime-ftime32-ftime64.md) vylepšení zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
errno_t _ftime_s(   
   struct _timeb *timeptr   
);  
errno_t _ftime32_s(   
   struct __timeb32 *timeptr   
);  
errno_t _ftime64_s(   
   struct __timeb64 *timeptr   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `timeptr`  
 Ukazatel na `_timeb`, `__timeb32`, nebo `__timeb64` struktury.  
  
## <a name="return-value"></a>Návratová hodnota  
 Nula v případě úspěchu, kód chyby při selhání. Pokud `timeptr` je `NULL`, je vrácenou hodnotou `EINVAL`.  
  
## <a name="remarks"></a>Poznámky  
 `_ftime_s` Funkce získá aktuálním místním časem a uloží je ve struktuře, na kterou odkazuje `timeptr`. `_timeb`, `__timeb32`, A `__timeb64` struktury jsou definovány v SYS\Timeb.h. Obsahují čtyři pole, které jsou uvedeny v následující tabulce.  
  
 `dstflag`  
 Nenulové hodnoty, pokud letní čas je aktuálně platí pro místní časovou zónu. (Viz [_tzset –](../../c-runtime-library/reference/tzset.md) Další informace o tom, jak je určen letní čas.)  
  
 `millitm`  
 Část sekundy v milisekundách.  
  
 `time`  
 Čas v sekundách od půlnoc (00: 00:00), 1. ledna 1970, koordinovaný světový čas (UTC).  
  
 `timezone`  
 Rozdíl v minutách, westward, přesun mezi místním ČASEM a. Hodnota `timezone` nastavena z hodnoty globální proměnné `_timezone` (viz `_tzset`).  
  
 `_ftime64_s`, které používá `__timeb64` struktury, umožňuje vytvoření souboru data, která se vyjádřit až do 23:59:59, 31. prosince 3000, UTC; zatímco `_ftime32_s` pouze představuje datům až 23:59:59 18 leden 2038 UTC. Půlnoc, 1. ledna 1970, je dolní mez rozsahu kalendářních dat pro všechny tyto funkce.  
  
 `_ftime_s`je ekvivalentní `_ftime64_s` a `_timeb` obsahuje 64-bit čas. Toto je hodnota true, pokud `_USE_32BIT_TIME_T` je definována v takovém případě staré chování je v platnosti; `_ftime_s` používá čas 32bitová verze a `_timeb` obsahuje 32-bit čas.  
  
 `_ftime_s`ověří jeho parametry. Pokud předány ukazatele null jako `timeptr`, funkce vyvolá obslužnou rutinu neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění pokračovat, nastaví funkci `errno` k `EINVAL`.  
  
## <a name="requirements"></a>Požadavky  
  
|Funkce|Požadovaný hlavičkový soubor|  
|--------------|---------------------|  
|`_ftime_s`|\<SYS/Types.h > a \<sys/timeb.h >|  
|`_ftime32_s`|\<SYS/Types.h > a \<sys/timeb.h >|  
|`_ftime64_s`|\<SYS/Types.h > a \<sys/timeb.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="libraries"></a>Knihovny  
 Všechny verze [běhové knihovny jazyka C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="example"></a>Příklad  
  
```  
// crt_ftime64_s.c  
// This program uses _ftime64_s to obtain the current  
// time and then stores this time in timebuffer.  
  
#include <stdio.h>  
#include <sys/timeb.h>  
#include <time.h>  
  
int main( void )  
{  
   struct _timeb timebuffer;  
   char timeline[26];  
   errno_t err;  
   time_t time1;  
   unsigned short millitm1;  
   short timezone1;  
   short dstflag1;  
  
   _ftime64_s( &timebuffer );  
  
    time1 = timebuffer.time;  
    millitm1 = timebuffer.millitm;  
    timezone1 = timebuffer.timezone;  
    dstflag1 = timebuffer.dstflag;  
  
   printf( "Seconds since midnight, January 1, 1970 (UTC): %I64d\n",   
   time1);  
   printf( "Milliseconds: %d\n", millitm1);  
   printf( "Minutes between UTC and local time: %d\n", timezone1);  
   printf( "Daylight savings time flag (1 means Daylight time is in "  
           "effect): %d\n", dstflag1);   
  
   err = ctime_s( timeline, 26, & ( timebuffer.time ) );  
   if (err)  
   {  
       printf("Invalid argument to ctime_s. ");  
   }  
   printf( "The time is %.19s.%hu %s", timeline, timebuffer.millitm,  
           &timeline[20] );  
}  
```  
  
```Output  
Seconds since midnight, January 1, 1970 (UTC): 1051553334  
Milliseconds: 230  
Minutes between UTC and local time: 480  
Daylight savings time flag (1 means Daylight time is in effect): 1  
The time is Mon Apr 28 11:08:54.230 2003  
```  
  
## <a name="see-also"></a>Viz také  
 [Správa času](../../c-runtime-library/time-management.md)   
 [asctime –, _wasctime –](../../c-runtime-library/reference/asctime-wasctime.md)   
 [CTime –, _ctime32 –, _ctime64 –, _wctime –, _wctime32 –, _wctime64 –](../../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)   
 [gmtime – _gmtime32 –, _gmtime64 –](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)   
 [místní čas, _localtime32 –, _localtime64 –](../../c-runtime-library/reference/localtime-localtime32-localtime64.md)   
 [time, _time32, _time64](../../c-runtime-library/reference/time-time32-time64.md)