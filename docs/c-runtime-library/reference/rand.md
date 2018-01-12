---
title: "rand – | Microsoft Docs"
ms.custom: 
ms.date: 1/02/2018
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: rand
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
f1_keywords: rand
dev_langs: C++
helpviewer_keywords:
- generating pseudorandom numbers
- random numbers, generating
- numbers, pseudorandom
- rand function
- pseudorandom numbers
- numbers, generating pseudorandom
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: aada39e6ea3de3cae65642d29fa1b5ce4bad098e
ms.sourcegitcommit: a5d8f5b92cb5e984d5d6c9d67fe8a1241f3fe184
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/05/2018
---
# <a name="rand"></a>rand

Pomocí algoritmu dobře známé a plně reprodukovatelné generuje pseudonáhodná čísla. Více prostřednictvím kódu programu zabezpečené verze této funkce je k dispozici. v tématu [rand_s –](../../c-runtime-library/reference/rand-s.md). Generované čísla `rand` nejsou kryptograficky zabezpečené. Pro bezpečnější kryptograficky náhodné generování čísel, pomocí `rand_s` nebo funkce deklarované v standardní knihovna C++ v [ \<náhodných >](../../standard-library/random.md).

## <a name="syntax"></a>Syntaxe

```C
int rand( void );
```

## <a name="return-value"></a>Návratová hodnota

`rand`Vrátí pseudonáhodná čísla, jak je popsáno výše. Neexistuje žádný návratový chyby.

## <a name="remarks"></a>Poznámky

`rand` Funkce vrátí pseudonáhodných celé číslo v rozsahu od 0 do `RAND_MAX` (32767). Použití [srand –](../../c-runtime-library/reference/srand.md) funkce pro generátor pseudonáhodných čísel před voláním `rand`.

`rand` Funkce generuje dobře známé pořadí a není vhodná pro použití jako Kryptografická funkce. Pro bezpečnější kryptograficky náhodné generování čísel, pomocí `rand_s` nebo funkce deklarované v standardní knihovna C++ v [ \<náhodných >](../../standard-library/random.md). Informace o tom, co je problém se `rand()` a jak `<random>` řeší tyto nedostatky, najdete v části [toto video](http://go.microsoft.com/fwlink/?LinkId=397615).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|`rand`|\<stdlib.h >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.

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

[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)  
[srand](../../c-runtime-library/reference/srand.md)  
[rand_s](../../c-runtime-library/reference/rand-s.md)  