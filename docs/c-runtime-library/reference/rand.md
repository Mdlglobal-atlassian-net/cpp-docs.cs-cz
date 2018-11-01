---
title: rand
ms.date: 1/02/2018
apiname:
- rand
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
- api-ms-win-crt-utility-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- rand
helpviewer_keywords:
- generating pseudorandom numbers
- random numbers, generating
- numbers, pseudorandom
- rand function
- pseudorandom numbers
- numbers, generating pseudorandom
ms.openlocfilehash: 67e128fc4adea345807a2d59078a00e3c4bd1f07
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50440726"
---
# <a name="rand"></a>rand

Pseudonáhodná čísla vygeneruje pomocí algoritmu dobře známé a plně reprodukovatelné. Více programově bezpečné verze této funkce je k dispozici. Zobrazit [rand_s –](rand-s.md). Generované čísel **rand** nejsou kryptograficky zabezpečené. Pro další kryptograficky zabezpečené generování náhodných čísel, pomocí [rand_s –](rand-s.md) nebo funkce deklarované ve standardní knihovně jazyka C++ v [ \<náhodné >](../../standard-library/random.md).

## <a name="syntax"></a>Syntaxe

```C
int rand( void );
```

## <a name="return-value"></a>Návratová hodnota

**rand** vrátí pseudonáhodná čísla, jak je popsáno výše. Není vrácena žádná chyba.

## <a name="remarks"></a>Poznámky

**Rand** funkce vrací pseudonáhodných celé číslo v rozsahu 0 až **RAND_MAX** (32767). Použití [srand –](srand.md) funkce pro generátor pseudonáhodných čísel před voláním **rand**.

**Rand** funkce generuje posloupnost dobře známé a není vhodná pro použití jako kryptografické funkce. Pro další kryptograficky zabezpečené generování náhodných čísel, pomocí [rand_s –](rand-s.md) nebo funkce deklarované ve standardní knihovně jazyka C++ v [ \<náhodné >](../../standard-library/random.md). Informace o čem je problém s **rand** a jak \<náhodné > řeší tyto nedostatky, najdete v tomto videu s názvem [rand považovat za škodlivých](https://channel9.msdn.com/Events/GoingNative/2013/rand-Considered-Harmful).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**rand**|\<stdlib.h>|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Viz také:

[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[srand](srand.md)<br/>
[rand_s](rand-s.md)<br/>
