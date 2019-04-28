---
title: rand_s
ms.date: 1/02/2018
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
ms.openlocfilehash: d196a6f5d7483deb9a7e1b8d7fa929532b6197db
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62358122"
---
# <a name="rands"></a>rand_s

Generuje pseudonáhodná čísla. Toto je bezpečnější verze funkce [rand](rand.md), s rozšířeními zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
errno_t rand_s(unsigned int* randomValue);
```

### <a name="parameters"></a>Parametry

*randomValue*<br/>
Ukazatel na celé číslo k uložení vygenerovanou hodnotu.

## <a name="return-value"></a>Návratová hodnota

Nula v případě úspěchu, jinak kód chyby. Pokud vstupní ukazatel _randomValue_ je ukazatel s hodnotou null, funkce vyvolá obslužnou rutinu neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, funkce vrátí **EINVAL** a nastaví **errno** k **EINVAL**. Pokud funkce selže z jiného důvodu, *_randomValue_ je nastavena na hodnotu 0.

## <a name="remarks"></a>Poznámky

**Rand_s –** funkce zapíše pseudonáhodných celé číslo v rozsahu 0 až **UINT_MAX** na vstupní ukazatel. **Rand_s –** funkce operačního systému používá k vygenerování kryptograficky zabezpečená náhodná čísla. Nepoužívá generovaných počáteční hodnotu [srand –](srand.md) funkce, ani to ovlivní náhodné číslo pořadí používané [rand](rand.md).

**Rand_s –** vyžaduje funkce této konstanty **_CRT_RAND_S** nadefinovat před příkaz zahrnutí má funkce deklarovaná jako v následujícím příkladu:

```C
#define _CRT_RAND_S
#include <stdlib.h>
```

**rand_s –** závisí [RtlGenRandom](/windows/desktop/api/ntsecapi/nf-ntsecapi-rtlgenrandom) rozhraní API, které je dostupný jenom ve Windows XP a vyšší.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**rand_s**|\<stdlib.h>|

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

## <a name="see-also"></a>Viz také:

[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[rand](rand.md)<br/>
[srand](srand.md)<br/>
