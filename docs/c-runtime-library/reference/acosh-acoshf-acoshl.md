---
title: acosh – acoshf –, acoshl | Dokumentace Microsoftu
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- acoshf
- acosh
- acoshl
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
- acosh
- acoshf
- acoshl
- math/acosh
- math/acoshf
- math/acoshl
dev_langs:
- C++
helpviewer_keywords:
- acoshf function
- acosh function
- acoshl function
ms.assetid: 6985c4d7-9e2a-44ce-9a9b-5a43015f15f7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 546006fcf1c559317b4afff424976db8109442e7
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/01/2018
ms.locfileid: "39404749"
---
# <a name="acosh-acoshf-acoshl"></a>acosh, acoshf, acoshl

Vypočítá inverzní hyperbolický kosinus.

## <a name="syntax"></a>Syntaxe

```C
double acosh( double x );
float acoshf( float x );
long double acoshl( long double x );
```

```cpp
float acosh( float x );  // C++ only
long double acosh( long double x );  // C++ only
```

### <a name="parameters"></a>Parametry

*x*  
Hodnota s plovoucí desetinnou čárkou.

## <a name="return-value"></a>Návratová hodnota

**Acosh –** funkce vrátí hyberbolic inverzní kosinus (hyperbolický Arkus kosinus) *x*. Tyto funkce jsou platné po domény *x* ≥ 1. Pokud *x* je menší než 1 `errno` je nastavena na `EDOM` a výsledkem je tichý NaN. Pokud *x* je tichý NaN, nekonečno, nebo nekonečno, je vrácena stejnou hodnotu.

|Vstup|Výjimka SEH|`_matherr` Výjimka|
|-----------|-------------------|--------------------------|
|ROZMEZÍ QNAN, AJÍT INF|žádná|žádná|
|*x* < 1|žádná|žádná|

## <a name="remarks"></a>Poznámky

Při použití jazyka C++, můžete volat přetížení **acosh –** , která používají a vrací **float** nebo **dlouhé** **double** hodnoty. V programu jazyka C **acosh –** vždy převezme a vrátí **double**.

## <a name="requirements"></a>Požadavky

|Funkce|Záhlaví C|Hlaviček jazyka C++|
|--------------|--------------|------------------|
|**acosh –**, **acoshf –**, **acoshl**|\<Math.h >|\<cmath >|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_acosh.c
// Compile by using: cl /W4 crt_acosh.c
// This program displays the hyperbolic cosine of pi / 4
// and the arc hyperbolic cosine of the result.

#include <math.h>
#include <stdio.h>

int main( void )
{
   double pi = 3.1415926535;
   double x, y;

   x = cosh( pi / 4 );
   y = acosh( x );
   printf( "cosh( %f ) = %f\n", pi/4, x );
   printf( "acosh( %f ) = %f\n", x, y );
}
```

```Output
cosh( 0.785398 ) = 1.324609
acosh( 1.324609 ) = 0.785398
```

## <a name="see-also"></a>Viz také:

[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)  
[asinh, asinhf, asinhl](asinh-asinhf-asinhl.md)  
[atanh, atanhf, atanhl](atanh-atanhf-atanhl.md)  
[cosh, coshf, coshl](cosh-coshf-coshl.md)  
[sinh, sinhf, sinhl](sinh-sinhf-sinhl.md)  
[tanh, tanhf, tanhl](tanh-tanhf-tanhl.md)  