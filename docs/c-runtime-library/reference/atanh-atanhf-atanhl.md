---
title: atanh, atanhf, atanhl
ms.date: 4/2/2020
api_name:
- atanhl
- atanhf
- atanh
- _o_atanh
- _o_atanhf
- _o_atanhl
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- atanhl
- atanhf
- atanh
helpviewer_keywords:
- atanhf function
- atanhl function
- atanh funciton
ms.assetid: 83a43b5b-2580-4461-854f-dc84236d9f32
ms.openlocfilehash: ce40cf25fde12c6413e88519906b807f2ee65faa
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82920054"
---
# <a name="atanh-atanhf-atanhl"></a>atanh, atanhf, atanhl

Vypočítá inverzní hyperbolický tangens.

## <a name="syntax"></a>Syntaxe

```C
double atanh( double x );
float atanhf( float x );
long double atanhl( long double x );
```

```cpp
float atanh( float x );  // C++ only
long double atanh( long double x );  // C++ only
```

### <a name="parameters"></a>Parametry

*znak*<br/>
Hodnota s plovoucí desetinnou čárkou.

## <a name="return-value"></a>Návratová hodnota

Funkce **atanh –** vrátí inverzní arkustangens tangens (oblouk hyperbolický tangens) *x*. Pokud je *x* větší než 1 nebo menší než-1, **errno** je nastaveno na **EDOM** a výsledek je tiché NaN. Pokud je *x* rovno 1 nebo-1, vrátí se kladné nebo záporné nekonečno, v uvedeném pořadí a **errno** je nastavena na **ERANGE**.

|Vstup|Výjimka SEH|**Matherr** Jímka|
|-----------|-------------------|-------------------------|
|QNAN, ZASÁHNOUT|žádné|žádné|
|*X* ≥ 1; *×* ≤-1|žádné|žádné|

## <a name="remarks"></a>Poznámky

Vzhledem k tomu, že jazyk C++ umožňuje přetížení, můžete volat přetížení **atanh –** , která přijímají a vracejí hodnoty **float** nebo **Long** **Double** . V programu v jazyce C **atanh –** vždycky přebírá a vrací **Double**.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Funkce|Hlavička jazyka C|Hlavička C++|
|--------------|--------------|------------------|
|**atanh –**, **atanhf –**, **atanhl**|\<Math. h>|\<cmath> nebo \<Math. h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_atanh.c
// This program displays the hyperbolic tangent of pi / 4
// and the arc hyperbolic tangent of the result.
//

#include <math.h>
#include <stdio.h>

int main( void )
{
   double pi = 3.1415926535;
   double x, y;

   x = tanh( pi / 4 );
   y = atanh( x );
   printf( "tanh( %f ) = %f\n", pi/4, x );
   printf( "atanh( %f ) = %f\n", x, y );
}
```

```Output
tanh( 0.785398 ) = 0.655794
atanh( 0.655794 ) = 0.785398
```

## <a name="see-also"></a>Viz také

[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[acosh, acoshf, acoshl](acosh-acoshf-acoshl.md)<br/>
[asinh, asinhf, asinhl](asinh-asinhf-asinhl.md)<br/>
[cosh, coshf, coshl](cosh-coshf-coshl.md)<br/>
[sinh, sinhf, sinhl](sinh-sinhf-sinhl.md)<br/>
[tanh, tanhf, tanhl](tanh-tanhf-tanhl.md)<br/>
