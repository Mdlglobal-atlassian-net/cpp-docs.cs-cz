---
title: clock
ms.date: 11/04/2016
api_name:
- clock
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- clock
helpviewer_keywords:
- processor time used, calculating
- time, calculating processor
- clock function
- processor time used
- calculating processor time used
ms.assetid: 3e1853dd-498f-49ba-b06a-f2315f20904e
ms.openlocfilehash: 836d0c6448adb4c99a251a0e97aa642e30362dcb
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70939119"
---
# <a name="clock"></a>clock

Vypočítá čas v hodinách, který používá volající proces.

## <a name="syntax"></a>Syntaxe

```C
clock_t clock( void );
```

## <a name="return-value"></a>Návratová hodnota

Uplynulý čas od inicializace CRT na začátku procesu, měřená v jednotkách **CLOCKS_PER_SEC** za sekundu. Pokud uplynulý čas není k dispozici nebo překročil maximální kladný čas, který může být zaznamenán jako **clock_t** typ, funkce vrátí hodnotu `(clock_t)(-1)`.

## <a name="remarks"></a>Poznámky

Funkce **Clock** obsahuje informace o tom, kolik hodinových hodin bylo dokončeno od inicializace CRT během spuštění procesu. Všimněte si, že tato funkce nevyhovuje výhradně normě ISO C, která určuje, že jako návratová hodnota se použije čistý čas procesoru. K získání časů procesoru použijte funkci Win32 [GetProcessTimes](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getprocesstimes) . Chcete-li určit uplynulý čas v sekundách, vydělte hodnotu vrácenou funkcí **Clock** makra **CLOCKS_PER_SEC**.

Hodnota vrácená **hodinami** může přesáhnout maximální hodnotu **clock_t**, která je dost času. Po delší době procesu je hodnota vrácená **hodinou** vždy `(clock_t)(-1)`, jak je uvedeno ve standardu ISO C99 standard (7.23.2.1) a ISO C11 Standard (7.27.2.1). Společnost Microsoft implementuje **clock_t** jako **dlouhé**celé číslo se 32 znaménkem a makro **CLOCKS_PER_SEC** je definováno jako 1000. Tato hodnota poskytuje maximální hodnotu funkce **hodin** 2147483,647 sekund nebo asi 24,8 dní. Nespoléhá se na hodnotu vrácenou v procesech, které jsou spuštěny **po dobu** delší než tento časový rozsah. K zaznamenání uplynulých časů během mnoha let můžete [použít funkci 64 nebo funkci](time-time32-time64.md) [QueryPerformanceCounter](/windows/win32/api/profileapi/nf-profileapi-queryperformancecounter) pro Windows.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**clock**|\<time.h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
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

## <a name="see-also"></a>Viz také:

[Správa času](../../c-runtime-library/time-management.md)<br/>
[difftime, _difftime32, _difftime64](difftime-difftime32-difftime64.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
