---
title: acos, acosf, acosl
ms.date: 04/05/2018
apiname:
- acosf
- acos
- acosl
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
- api-ms-win-crt-math-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- acos
- acosl
- acosf
- math/acosf
- math/acosl
helpviewer_keywords:
- acos function
- acosl function
- acosf function
- trigonometric functions
- arccosine function
ms.assetid: 00b89c48-8faf-4824-aa95-fa4349a4975d
ms.openlocfilehash: 22149e9ff552015238d34a15166d04115438534b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62335669"
---
# <a name="acos-acosf-acosl"></a>acos, acosf, acosl

Vypočítá arkuskosinus.

## <a name="syntax"></a>Syntaxe

```C
double acos( double x );
float acosf( float x );
long double acosl( long double x );
```

```cpp
float acos( float x );   // C++ only
long double acos( long double x );   // C++ only
```

### <a name="parameters"></a>Parametry

*x*<br/>
Hodnota mezi -1 a 1, pro které chcete vypočítat Arkus kosinus (inverzní kosinus).

## <a name="return-value"></a>Návratová hodnota

**Acos** funkce vrátí hodnotu Arkus kosinus *x* v rozsahu 0 až pí radiánů.

Ve výchozím nastavení pokud *x* je menší než -1 nebo větší než 1, **acos** vrátí nekonečno.

|Vstup|Výjimka SEH|Výjimka Matherr|
|-----------|-------------------|-----------------------|
|± ∞|NEPLATNÝ|_DOMAIN|
|ROZMEZÍ QNAN, AJÍT|žádná|_DOMAIN|
|&#124;x&#124;>1|NEPLATNÝ|_DOMAIN|

## <a name="remarks"></a>Poznámky

Protože jazyk C++ umožňuje přetížení, můžete volat přetížení **acos** , která používají a vrací **float** a **dlouhé** **double** typy. V programu jazyka C **acos** vždy převezme a vrátí **double**.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Volitelná záhlaví|
|-------------|---------------------|----------------------|
|**acos**, **acosf**, **acosl**|\<math.h>|\<errno.h>|

## <a name="example"></a>Příklad

Tento program vyzve k zadání hodnoty v rozsahu -1 do 1. Vytvoření vstupní hodnoty mimo tento rozsah `_DOMAIN` chybové zprávy. Pokud je zadána platná hodnota, program vytiskne Arkus sinus a kosinus tuto hodnotu.

```C
// crt_asincos.c
// arguments: 0

#include <math.h>
#include <stdio.h>
#include <stdlib.h>
#include <errno.h>

int main( int ac, char* av[] )
{
    double  x,
            y;
    errno_t err;

    // argument checking
    if (ac != 2)
    {
        fprintf_s( stderr, "Usage: %s <number between -1 and 1>\n",
                   av[0]);
        return 1;
    }

    // Convert argument into a double value
    if ((err = sscanf_s( av[1], "%lf", &x )) != 1)
    {
        fprintf_s( stderr, "Error converting argument into ",
                   "double value.\n");
        return 1;
    }

    // Arcsine of X
    y = asin( x );
    printf_s( "Arcsine of %f = %f\n", x, y );

    // Arccosine of X
    y = acos( x );
    printf_s( "Arccosine of %f = %f\n", x, y );
}
```

```Output
Arcsine of 0.000000 = 0.000000
Arccosine of 0.000000 = 1.570796
```

## <a name="see-also"></a>Viz také:

[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[asin, asinf, asinl](asin-asinf-asinl.md)<br/>
[atan, atanf, atanl, atan2, atan2f, atan2l](atan-atanf-atanl-atan2-atan2f-atan2l.md)<br/>
[cos, cosf, cosl](cos-cosf-cosl.md)<br/>
[_matherr](matherr.md)<br/>
[sin, sinf, sinl](sin-sinf-sinl.md)<br/>
[tan, tanf, tanl](tan-tanf-tanl.md)