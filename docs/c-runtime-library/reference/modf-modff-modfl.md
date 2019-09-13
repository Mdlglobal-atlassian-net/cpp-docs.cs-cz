---
title: modf, modff, modfl
ms.date: 04/05/2018
api_name:
- modff
- modf
- modfl
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
- api-ms-win-crt-math-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- modff
- _modfl
- modf
- modfl
- math/modf
- math/modff
- math/modfl
helpviewer_keywords:
- modf function
- modff function
- modfl function
ms.assetid: b1c7abf5-d476-43ca-a03c-02072a86e32d
ms.openlocfilehash: 32caadb787031dca0b0726c546a11c5cd6722b82
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70951542"
---
# <a name="modf-modff-modfl"></a>modf, modff, modfl

Rozdělí hodnotu s plovoucí desetinnou čárkou na zlomky a celočíselné části.

## <a name="syntax"></a>Syntaxe

```C
double modf( double x, double * intptr );
float modff( float x, float * intptr );
long double modfl( long double x, long double * intptr );
```

```cpp
float modf( float x, float * intptr );  // C++ only
long double modf( long double x, long double * intptr );  // C++ only
```

### <a name="parameters"></a>Parametry

*x*<br/>
Hodnota s plovoucí desetinnou čárkou.

*intptr*<br/>
Ukazatel na uloženou část celého čísla.

## <a name="return-value"></a>Návratová hodnota

Tato funkce vrací zlomkovou část čísla *x*se znaménkem. Nevrátila se žádná chybová zpráva.

## <a name="remarks"></a>Poznámky

Funkce **modf –** rozdělují hodnotu s plovoucí desetinnou čárkou *x* na zlomky a celočíselné části, z nichž každá má stejné znaménko jako *x*. Vrátí se podepsaná Zlomková část čísla *x* . Celočíselná část je uložena jako hodnota s plovoucí desetinnou čárkou na *IntPtr*.

**modf –** má implementaci, která používá streaming SIMD Extensions 2 (SSE2). Informace a omezení použití implementace SSE2 najdete v tématu [_set_SSE2_enable](set-sse2-enable.md) .

C++umožňuje přetížení, takže můžete volat přetížení **modf –** , která přebírají a vracejí parametry **float** nebo **Long** **Double** . V programu v jazyce C **modf –** vždy přebírá dvě hodnoty Double a vrátí hodnotu Double.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**modf –** , **modff –** , **modfl**|C: \<Math. h ><br /><br /> C++:, \<cmath > nebo \<Math. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_modf.c

#include <math.h>
#include <stdio.h>

int main( void )
{
   double x, y, n;

   x = -14.87654321;      /* Divide x into its fractional */
   y = modf( x, &n );     /* and integer parts            */

   printf( "For %f, the fraction is %f and the integer is %.f\n",
           x, y, n );
}
```

```Output
For -14.876543, the fraction is -0.876543 and the integer is -14
```

## <a name="see-also"></a>Viz také:

[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[frexp](frexp.md)<br/>
[ldexp](ldexp.md)<br/>
