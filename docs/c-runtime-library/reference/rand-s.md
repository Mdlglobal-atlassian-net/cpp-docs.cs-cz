---
title: "rand_s – | Microsoft Docs"
ms.custom: 
ms.date: 1/02/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- rand_s
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
- rand_s
dev_langs:
- C++
helpviewer_keywords:
- generating pseudorandom numbers
- random numbers, cryptographically secure
- random numbers, generating
- rand_s function
- numbers, pseudorandom
- cryptographically secure random numbers
- pseudorandom numbers
- numbers, generating pseudorandom
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2438b2ced054667a658f8f31a37c9a62112debc6
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="rands"></a>rand_s

Generuje pseudonáhodná čísla. Toto je bezpečnější verze funkce [rand –](../../c-runtime-library/reference/rand.md), vylepšení zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md). 

## <a name="syntax"></a>Syntaxe

```C
errno_t rand_s(unsigned int* randomValue);
```

### <a name="parameters"></a>Parametry

*randomValue*  
Ukazatel na celočíselnou hodnotu pro uložení generované hodnoty.

## <a name="return-value"></a>Návratová hodnota

Nula v případě úspěchu, jinak hodnota chybový kód. Pokud je vstupní ukazatel _randomValue_ je ukazatel s hodnotou null, funkce vyvolá obslužnou rutinu neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění chcete-li pokračovat, funkce vrátí hodnotu `EINVAL` a nastaví `errno` k `EINVAL`. Pokud funkce selže z jiného důvodu, *_randomValue_ je nastaven na hodnotu 0.

## <a name="remarks"></a>Poznámky

`rand_s` Funkce zápisů pseudonáhodných celé číslo v rozsahu od 0 do `UINT_MAX` pro vstupní ukazatele. `rand_s` Funkce operačního systému používá ke generování kryptograficky zabezpečené náhodných čísel. Nepoužívá počáteční hodnoty generované [srand –](../../c-runtime-library/reference/srand.md) funkce, ani neovlivní sekvenci náhodné číslo používané `rand`.

`rand_s` Funkce vyžaduje, že konstanta `_CRT_RAND_S` definovat před příkaz zahrnutí pro funkci deklarovat, jako v následujícím příkladu:

```C
#define _CRT_RAND_S
#include <stdlib.h>
```

`rand_s` závisí na [RtlGenRandom](http://msdn.microsoft.com/library/windows/desktop/aa387694) rozhraní API, které je pouze k dispozici v systému Windows XP nebo novější.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|`rand_s`|\<stdlib.h>|

Další informace najdete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_rand_s.c
// This program illustrates how to generate random
// integer or floating point numbers in a specified range.

// Remembering to define _CRT_RAND_S prior
// to inclusion statement.
#define _CRT_RAND_S

#include <stdlib.h>
#include <stdio.h>
#include <limits.h>

int main( void )
{
    int             i;
    unsigned int    number;
    double          max = 100.0;
    errno_t         err;

    // Display 10 random integers in the range [ 1,10 ].
    for( i = 0; i < 10;i++ )
    {
        err = rand_s( &number );
        if (err != 0)
        {
            printf_s("The rand_s function failed!\n");
        }
        printf_s( "  %u\n", (unsigned int) ((double)number /
                       ((double) UINT_MAX + 1 ) * 10.0) + 1);
    }

    printf_s("\n");

    // Display 10 random doubles in [0, max).
    for (i = 0; i < 10;i++ )
    {
        err = rand_s( &number );
        if (err != 0)
        {
            printf_s("The rand_s function failed!\n");
        }
        printf_s( "  %g\n", (double) number / 
                          ((double) UINT_MAX + 1) * max );
    }
}
```

### <a name="sample-output"></a>Vzorový výstup

```Output
10
4
5
2
8
2
5
6
1
1

32.6617
29.4471
11.5413
6.41924
20.711
60.2878
61.0094
20.1222
80.9192
65.0712
```

## <a name="see-also"></a>Viz také

[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)  
[rand](../../c-runtime-library/reference/rand.md)  
[srand](../../c-runtime-library/reference/srand.md)  
