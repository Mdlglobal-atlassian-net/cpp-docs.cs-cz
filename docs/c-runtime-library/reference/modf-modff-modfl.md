---
title: modf – modff –, modfl
ms.date: 04/05/2018
apiname:
- modff
- modf
- modfl
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
ms.openlocfilehash: 59d6e2b9b02ad182c5630d6dc9a989c035e8fa92
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50478062"
---
# <a name="modf-modff-modfl"></a>modf – modff –, modfl

Rozdělí hodnotu s plovoucí desetinnou čárkou na frakce a celá čísla.

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

*IntPtr*<br/>
Ukazatel na uložený celočíselnou část.

## <a name="return-value"></a>Návratová hodnota

Tato funkce vrací podepsaná desetinná část čísla *x*. Není vrácena žádná chyba.

## <a name="remarks"></a>Poznámky

**Modf –** funkce Rozdělit hodnotu s plovoucí desetinnou čárkou *x* na frakce a celá čísla, z nichž každá má stejné znaménko jako *x*. Podepsaná desetinná část čísla *x* je vrácena. Část celého čísla se ukládá jako hodnota s plovoucí desetinnou čárkou na *intptr*.

**modf –** má implementace, která používá Streaming SIMD Extensions 2 (SSE2). Zobrazit [_set_sse2_enable –](set-sse2-enable.md) informace a omezení používání implementace SSE2.

Jazyk C++ umožňuje přetížení, takže můžete volat přetížení **modf –** , která používají a vrací **float** nebo **dlouhé** **double** parametry. V programu jazyka C **modf –** vždy převezme dvě double hodnoty a vrátí hodnotu double.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**modf –**, **modff –**, **modfl**|C: \<math.h ><br /><br /> Jazyk C++:, \<cmath > nebo \<math.h >|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

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
