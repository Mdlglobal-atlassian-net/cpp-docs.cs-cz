---
title: "difftime – _difftime32 –, _difftime64 – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _difftime32
- difftime
- _difftime64
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
- _difftime64
- difftime
- difftime64
- _difftime32
- difftime32
dev_langs: C++
helpviewer_keywords:
- _difftime32 function
- difftime function
- time, finding the difference
- difftime64 function
- _difftime64 function
- difftime32 function
ms.assetid: 4cc0ac2b-fc7b-42c0-8283-8c9d10c566d0
caps.latest.revision: "21"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 544f3abbcdfa67a450e7c722d1ff5994f13c5e87
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="difftime-difftime32-difftime64"></a>difftime, _difftime32, _difftime64
Najde rozdíl mezi dvěma časy.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
double difftime(   
   time_t timer1,  
   time_t timer0   
);  
double _difftime32(   
   __time32_t timer1,  
   __time32_t timer0   
);  
double _difftime64(   
   __time64_t timer1,  
   __time64_t timer0   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `timer1`  
 Čas dokončení.  
  
 `timer0`  
 Počáteční čas.  
  
## <a name="return-value"></a>Návratová hodnota  
 `difftime`Vrátí uplynulý čas v sekundách, z `timer0` k `timer1`. Hodnota vrácená je číslo s plovoucí desetinnou čárkou a dvojitou přesností. Návratová hodnota může být 0, která znamená chybu.  
  
## <a name="remarks"></a>Poznámky  
 `difftime` Funkce vypočítá rozdíl mezi dvěma hodnotami zadaný čas `timer0` a `timer1`.  
  
 Zadaná hodnota času se musí vejít v rozsahu `time_t`. `time_t`je hodnota 64-bit. Proto konec rozsahu byla rozšířena z 23:59:59 18 leden 2038 UTC do 23:59:59, 31. prosince 3000. Nižší rozsah `time_t` je stále půlnoc, 1. ledna 1970.  
  
 `difftime`je vložená funkce, která vyhodnotí buď `_difftime32` nebo `_difftime64` podle toho, jestli `_USE_32BIT_TIME_T` je definována. _difftime32 – a _difftime64 – lze přímo můžete vynutit používání určité velikosti typu time.  
  
 Tyto funkce ověřit jejich parametrů. Pokud z parametrů je nula nebo záporná, obslužná rutina neplatný parametr je vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění pokračovat, tyto funkce vrátí 0 a nastavte `errno` k `EINVAL`.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`difftime`|\<Time.h >|  
|`_difftime32`|\<Time.h >|  
|`_difftime64`|\<Time.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="example"></a>Příklad  
  
```cpp  
// crt_difftime.c  
// This program calculates the amount of time  
// needed to do a floating-point multiply 100 million times.  
//  
  
#include <stdio.h>  
#include <stdlib.h>  
#include <time.h>  
#include <float.h>  
  
double RangedRand( float range_min, float range_max)  
{  
   // Generate random numbers in the half-closed interval  
   // [range_min, range_max). In other words,  
   // range_min <= random number < range_max  
   return ((double)rand() / (RAND_MAX + 1) * (range_max - range_min)  
            + range_min);  
}  
  
int main( void )  
{  
   time_t   start, finish;  
   long     loop;  
   double   result, elapsed_time;  
   double   arNums[3];  
  
   // Seed the random-number generator with the current time so that  
   // the numbers will be different every time we run.  
   srand( (unsigned)time( NULL ) );  
  
   arNums[0] = RangedRand(1, FLT_MAX);  
   arNums[1] = RangedRand(1, FLT_MAX);  
   arNums[2] = RangedRand(1, FLT_MAX);  
   printf( "Using floating point numbers %.5e %.5e %.5e\n", arNums[0], arNums[1], arNums[2] );  
  
   printf( "Multiplying 2 numbers 100 million times...\n" );  
  
   time( &start );  
   for( loop = 0; loop < 100000000; loop++ )  
      result = arNums[loop%3] * arNums[(loop+1)%3];   
   time( &finish );  
  
   elapsed_time = difftime( finish, start );  
   printf( "\nProgram takes %6.0f seconds.\n", elapsed_time );  
}  
  
```  
  
```Output  
Using random floating point numbers 1.04749e+038 2.01482e+038 1.72737e+038Multiplying 2 floating point numbers 100 million times...Program takes      3 seconds.Multiplying 2 floating point numbers 500 million times...  
  
Program takes      5 seconds.  
```  
  
## <a name="see-also"></a>Viz také  
 [Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)   
 [Správa času](../../c-runtime-library/time-management.md)   
 [čas, _time32 –, _time64 –](../../c-runtime-library/reference/time-time32-time64.md)