---
title: rand_s
ms.date: 01/02/2018
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
helpviewer_keywords:
- generating pseudorandom numbers
- random numbers, cryptographically secure
- random numbers, generating
- rand_s function
- numbers, pseudorandom
- cryptographically secure random numbers
- pseudorandom numbers
- numbers, generating pseudorandom
ms.openlocfilehash: 2bbefad60d1d54ece0b467fc411ca9b6b7fe498f
ms.sourcegitcommit: effb516760c0f956c6308eeded48851accc96b92
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70927441"
---
# <a name="rand_s"></a>rand_s

Vygeneruje pseudonáhodných číslo. Jedná se o bezpečnější verzi funkce [Rand](rand.md)s vylepšením zabezpečení, jak je popsáno v tématu [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
errno_t rand_s(unsigned int* randomValue);
```

### <a name="parameters"></a>Parametry

*randomValue*<br/>
Ukazatel na celé číslo pro uložení vygenerované hodnoty.

## <a name="return-value"></a>Návratová hodnota

Nula v případě úspěchu, jinak, kód chyby. Pokud je vstupní ukazatel _randomValue_ ukazatel s hodnotou null, funkce vyvolá neplatnou obslužnou rutinu parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, funkce vrátí **EINVAL** a nastaví **errno** na **EINVAL**. Pokud se funkce z jakéhokoli jiného důvodu nezdařila, *_randomValue_ se nastaví na 0.

## <a name="remarks"></a>Poznámky

Funkce **rand_s** zapisuje celé číslo pseudonáhodných v rozsahu 0 až **UINT_MAX** na vstupní ukazatel. Funkce **rand_s** používá operační systém ke generování kryptograficky zabezpečených náhodných čísel. Nepoužívá počáteční hodnotu vygenerovanou funkcí [srand](srand.md) , ani nemá vliv na sekvenci náhodného číslování, kterou používá [Rand](rand.md).

Funkce **rand_s** vyžaduje, aby před příkazem include byla definovaná konstanta **_CRT_RAND_S** , aby byla funkce deklarovaná, jako v následujícím příkladu:

```C
#define _CRT_RAND_S
#include <stdlib.h>
```

**rand_s** závisí na rozhraní [RtlGenRandom](/windows/win32/api/ntsecapi/nf-ntsecapi-rtlgenrandom) API, které je k dispozici pouze v systému Windows XP a novějším.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**rand_s**|\<stdlib.h>|

Další informace najdete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Viz také:

[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[rand](rand.md)<br/>
[srand](srand.md)<br/>
