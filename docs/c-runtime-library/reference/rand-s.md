---
title: rand_s
ms.date: 4/2/2020
api_name:
- rand_s
- _o_rand_s
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- rand_s
helpviewer_keywords:
- generating pseudorandom numbers
- random numbers, cryptographically secure
- random numbers, generating
- rand_s function
- numbers, pseudorandom
- cryptographically secure random numbers
- pseudorandom numbers
- numbers, generating pseudorandom
ms.openlocfilehash: b11a40dd9dc58964df77330767a55aa95a179319
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338193"
---
# <a name="rand_s"></a>rand_s

Generuje pseudonáhodné číslo. Jedná se o bezpečnější verzi funkce [rand](rand.md)s vylepšeními zabezpečení popsanými v části [Funkce zabezpečení v crt](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
errno_t rand_s(unsigned int* randomValue);
```

### <a name="parameters"></a>Parametry

*randomValue*<br/>
Ukazatel na celé číslo pro uložení generované hodnoty.

## <a name="return-value"></a>Návratová hodnota

Nula v případě úspěchu, jinak kód chyby. Pokud je vstupní ukazatel _randomValue_ ukazatelem null, funkce vyvolá neplatnou obslužnou rutinu parametru, jak je popsáno v [části Ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je spuštění povoleno pokračovat, funkce vrátí **EINVAL** a nastaví **errno** na **EINVAL**. Pokud funkce selže z jiného důvodu, *_randomValue_ je nastavena na 0.

## <a name="remarks"></a>Poznámky

Funkce **rand_s** zapíše pseudonáhodné celé číslo v rozsahu 0, aby **UINT_MAX** vstupníukazatel. Funkce **rand_s** používá operační systém ke generování kryptograficky zabezpečených náhodných čísel. Nepoužívá osivo generované [srand](srand.md) funkcí, ani nemá vliv na náhodné číselné pořadí používané [rand](rand.md).

Funkce **rand_s** vyžaduje, aby byla před příkazem inclusion definována konstantní **_CRT_RAND_S** pro funkci, která má být deklarována, jako v následujícím příkladu:

```C
By default, this function's global state is scoped to the application. To change this, see [Global state in the CRT](../global-state.md).

#define _CRT_RAND_S
#include <stdlib.h>
```

**rand_s** závisí na [rozhraní RTLGenRandom](/windows/win32/api/ntsecapi/nf-ntsecapi-rtlgenrandom) API, které je k dispozici pouze v systému Windows XP a novějším.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**rand_s**|\<stdlib.h>|

Další informace naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

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

[Podpora s plovoucí desetinnou tálicí](../../c-runtime-library/floating-point-support.md)<br/>
[Rand](rand.md)<br/>
[srand](srand.md)<br/>
