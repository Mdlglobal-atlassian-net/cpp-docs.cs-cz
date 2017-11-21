---
title: hodiny | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: clock
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
f1_keywords: clock
dev_langs: C++
helpviewer_keywords:
- processor time used, calculating
- time, calculating processor
- clock function
- processor time used
- calculating processor time used
ms.assetid: 3e1853dd-498f-49ba-b06a-f2315f20904e
caps.latest.revision: "15"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 32b0f1bdd4e7db4f870aa23919ab426335d3f446
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="clock"></a>clock
Vypočítá wall čas používá proces volání.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
clock_t clock( void );  
```  
  
## <a name="return-value"></a>Návratová hodnota  
Uplynulý čas od inicializace CRT na začátku procesu, měřená v `CLOCKS_PER_SEC` jednotek za sekundu. Pokud není k dispozici uplynulý čas, nebo byla překročena maximální kladné dobu, kterou lze zaznamenat jako `clock_t` typu, funkce vrátí hodnotu `(clock_t)(-1)`.   
  
## <a name="remarks"></a>Poznámky  
`clock` Funkce řekne, jak dlouho wall hodiny od inicializace CRT během procesu spuštění uplynul. Všimněte si, že tato funkce není v souladu s výhradně C ISO, který určuje net čas procesoru jako návratovou hodnotu. Chcete-li získat časy procesoru, použijte Win32 [GetProcessTimes](https://msdn.microsoft.com/library/windows/desktop/ms683223) funkce. Pokud chcete zjistit uplynulý čas v sekundách, dělení hodnoty vrácené `clock` funkce pomocí makro `CLOCKS_PER_SEC`.  
  
Dispozici dostatek času nevrací `clock` může být vyšší než maximální hodnota kladné `clock_t`. Při procesu byla spuštěna déle hodnoty vrácené `clock` je vždy `(clock_t)(-1)`podle specifikace standard ISO C99 (7.23.2.1) a standard ISO C11 (7.27.2.1). Microsoft implementuje `clock_t` jako `long`, znaménkem 32-bit a `CLOCKS_PER_SEC` makro je definován jako 1000. To dává maximální `clock` funkce návratovou hodnotu 2147483.647 vteřin, nebo o 24,8 dnů. Nespoléhejte na hodnoty vrácené `clock` v procesy, které mají spuštěna déle, než toto množství času. Můžete použít 64-bit `time` funkce nebo Windows [QueryPerformanceCounter](https://msdn.microsoft.com/library/windows/desktop/ms644904) funkce záznamů proces uplynulý čas mnoha let.  

## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`clock`|\<Time.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="example"></a>Příklad  
  
```  
// crt_clock.c  
// This sample uses clock() to 'sleep' for three 
// seconds, then determines how long it takes  
// to execute an empty loop 600000000 times.  
  
#include <stdio.h>  
#include <stdlib.h>  
#include <time.h>  
  
// Pauses for a specified number of milliseconds.  
void do_sleep( clock_t wait )  
{  
   clock_t goal;  
   goal = wait + clock();  
   while( goal > clock() )  
      ;  
}  
  
const long num_loops = 600000000L;

int main( void )  
{  
   long    i = num_loops;  
   clock_t start, finish;  
   double  duration;  
  
   // Delay for a specified time.  
   printf( "Delay for three seconds\n" );  
   do_sleep( (clock_t)3 * CLOCKS_PER_SEC );  
   printf( "Done!\n" );  
  
   // Measure the duration of an event.  
   start = clock();  
   while( i-- )   
      ;  
   finish = clock();  
   duration = (double)(finish - start) / CLOCKS_PER_SEC;  
   printf( "Time to do %ld empty loops is ", num_loops );  
   printf( "%2.3f seconds\n", duration );  
}  
```  
  
```Output  
Delay for three seconds  
Done!  
Time to do 600000000 empty loops is 1.354 seconds  
```  
  
## <a name="see-also"></a>Viz také  
 [Správa času](../../c-runtime-library/time-management.md)   
 [difftime – _difftime32 –, _difftime64 –](../../c-runtime-library/reference/difftime-difftime32-difftime64.md)   
 [čas, _time32 –, _time64 –](../../c-runtime-library/reference/time-time32-time64.md)