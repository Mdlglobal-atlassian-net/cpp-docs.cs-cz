---
title: rand
ms.date: 01/02/2018
api_name:
- rand
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
ms.openlocfilehash: 6042ab917083cf4131c16012b84afbbe43a7d834
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70949544"
---
# <a name="rand"></a>rand

Vygeneruje pseudonáhodných číslo pomocí dobře známého a plně reprodukovatelného algoritmu. K dispozici je programově zabezpečená verze této funkce; viz [rand_s](rand-s.md). Čísla generovaná pomocí funkce **Rand** nejsou kryptograficky zabezpečena. Pro kryptograficky zabezpečené generování náhodných čísel použijte [rand_s](rand-s.md) nebo funkce deklarované ve standardní knihovně v C++ [ \<části náhodný >](../../standard-library/random.md).

## <a name="syntax"></a>Syntaxe

```C
int rand( void );
```

## <a name="return-value"></a>Návratová hodnota

**Rand** Vrátí pseudonáhodných číslo, jak je popsáno výše. Nevrátila se žádná chybová zpráva.

## <a name="remarks"></a>Poznámky

Funkce **Rand** vrátí celé číslo pseudonáhodných v rozsahu 0 až **RAND_MAX** (32767). Před voláním funkce **Rand**použijte funkci [srand](srand.md) k osazení generátoru pseudonáhodných.

Funkce **NÁHČÍSLO** vygeneruje dobře známou sekvenci a není vhodná pro použití jako kryptografická funkce. Pro kryptograficky zabezpečené generování náhodných čísel použijte [rand_s](rand-s.md) nebo funkce deklarované ve standardní knihovně v C++ [ \<části náhodný >](../../standard-library/random.md). Informace o tom, co je pro **funkci NÁHČÍSLO** chybné \<, a o tom, jak náhodná > řeší tyto nedostatky, najdete v tomto videu s názvem [Rand považovaný za škodlivý](https://channel9.msdn.com/Events/GoingNative/2013/rand-Considered-Harmful).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**rand**|\<stdlib.h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

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
