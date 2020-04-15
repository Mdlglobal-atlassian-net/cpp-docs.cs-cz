---
title: rand
ms.date: 4/2/2020
api_name:
- rand
- _o_rand
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
- api-ms-win-crt-utility-l1-1-0.dll
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- rand
helpviewer_keywords:
- generating pseudorandom numbers
- random numbers, generating
- numbers, pseudorandom
- rand function
- pseudorandom numbers
- numbers, generating pseudorandom
ms.openlocfilehash: 944c512d0102b459afc2924ef7515311e46cd43c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338165"
---
# <a name="rand"></a>rand

Generuje pseudonáhodné číslo pomocí známého a plně reprodukovatelného algoritmu. Je k dispozici programově bezpečnější verze této funkce. viz [rand_s](rand-s.md). Čísla generovaná **randem** nejsou kryptograficky zabezpečená. Pro více kryptograficky zabezpečené generování náhodných čísel použijte [rand_s](rand-s.md) nebo funkce deklarované ve standardní knihovně Jazyka C++ v [ \<náhodném>](../../standard-library/random.md).

## <a name="syntax"></a>Syntaxe

```C
int rand( void );
```

## <a name="return-value"></a>Návratová hodnota

**rand** vrátí pseudonáhodné číslo, jak je popsáno výše. Neexistuje žádná chyba vrátit.

## <a name="remarks"></a>Poznámky

Funkce **rand** vrátí pseudonáhodné celé číslo v rozsahu 0 až **RAND_MAX** (32767). Použijte funkci [srand](srand.md) k osivu pseudogenerátoru náhodných čísel před voláním **rand**.

Funkce **rand** generuje známou sekvenci a není vhodná pro použití jako kryptografická funkce. Pro více kryptograficky zabezpečené generování náhodných čísel použijte [rand_s](rand-s.md) nebo funkce deklarované ve standardní knihovně Jazyka C++ v [ \<náhodném>](../../standard-library/random.md). Informace o tom, co je špatného **na rand** a jak \<náhodné> řeší tyto nedostatky, viz toto video s názvem [rand považován za škodlivý](https://channel9.msdn.com/Events/GoingNative/2013/rand-Considered-Harmful).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**Rand**|\<stdlib.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_rand.c
// This program seeds the random-number generator
// with the time, then exercises the rand function.
//

#include <stdlib.h>
#include <stdio.h>
#include <time.h>

void SimpleRandDemo( int n )
{
   // Print n random numbers.
   int i;
   for( i = 0; i < n; i++ )
      printf( "  %6d\n", rand() );
}

void RangedRandDemo( int range_min, int range_max, int n )
{
   // Generate random numbers in the half-closed interval
   // [range_min, range_max). In other words,
   // range_min <= random number < range_max
   int i;
   for ( i = 0; i < n; i++ )
   {
      int u = (double)rand() / (RAND_MAX + 1) * (range_max - range_min)
            + range_min;
      printf( "  %6d\n", u);
   }
}

int main( void )
{
   // Seed the random-number generator with the current time so that
   // the numbers will be different every time we run.
   srand( (unsigned)time( NULL ) );

   SimpleRandDemo( 10 );
   printf("\n");
   RangedRandDemo( -100, 100, 10 );
}
```

```Output
22036
18330
11651
27464
18093
3284
11785
14686
11447
11285

   74
   48
   27
   65
   96
   64
   -5
  -42
  -55
   66
```

## <a name="see-also"></a>Viz také

[Podpora s plovoucí desetinnou tálicí](../../c-runtime-library/floating-point-support.md)<br/>
[srand](srand.md)<br/>
[rand_s](rand-s.md)<br/>
