---
title: asinh – asinhf –, asinhl | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- asinh
- asinhf
- asinhl
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
- asinhf
- asinhl
- asinh
dev_langs:
- C++
helpviewer_keywords:
- asinh function
- asinhl function
- asinhf function
ms.assetid: 4488babe-1a7e-44ca-8b7b-c2db0a70084f
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 50cd387f2c943d407dd11fe2e191457314f5cba9
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2018
---
# <a name="asinh-asinhf-asinhl"></a>asinh, asinhf, asinhl

Vypočítá inverzní hyperbolický sinus.

## <a name="syntax"></a>Syntaxe

```C
double asinh( double x );
float asinhf( float x );
long double asinhl( long double x );
```

```cpp
float asinh( float x );  // C++ only
long double asinh( long double x );  // C++ only
```

### <a name="parameters"></a>Parametry

*x*<br/>
Hodnota s plovoucí desetinnou čárkou.

## <a name="return-value"></a>Návratová hodnota

**Asinh –** funkce vrátí hyberbolic inverzní sinus (oblouk hyperbolický sinus) *x*. Tato funkce je platný doménou, s plovoucí desetinnou čárkou. Pokud *x* quiet NaN, neomezené, nebo infinity, je vrácena stejnou hodnotu.

|Vstup|Výjimka SEH|**_matherr –** výjimky|
|-----------|-------------------|--------------------------|
|INF QNAN, IND PŘESNOSTÍ|žádná|žádná|

## <a name="remarks"></a>Poznámky

Pokud používáte C++, můžete volat přetížení **asinh –** , přijmout a vrátit **float** nebo **dlouho** **dvojité** hodnoty. V programu C **asinh –** vždy provede a vrátí **dvojité**.

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaná hlavička C|Požadovaná hlavička v C++|
|--------------|--------------|------------------|
|**asinh –**, **asinhf –**, **asinhl**|\<Math.h >|\<cmath – > nebo \<math.h <|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_asinh.c
// Compile by using: cl /W4 crt_asinh.c
// This program displays the hyperbolic sine of pi / 4
// and the arc hyperbolic sine of the result.

#include <math.h>
#include <stdio.h>

int main( void )
{
   double pi = 3.1415926535;
   double x, y;

   x = sinh( pi / 4 );
   y = asinh( x );
   printf( "sinh( %f ) = %f\n", pi/4, x );
   printf( "asinh( %f ) = %f\n", x, y );
}
```

```Output
sinh( 0.785398 ) = 0.868671
asinh( 0.868671 ) = 0.785398
```

## <a name="see-also"></a>Viz také

[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[acosh, acoshf, acoshl](acosh-acoshf-acoshl.md)<br/>
[atanh, atanhf, atanhl](atanh-atanhf-atanhl.md)<br/>
[COSH, coshf –, coshl –](cosh-coshf-coshl.md)<br/>
[SINH, sinhf –, sinhl –](sinh-sinhf-sinhl.md)<br/>
[TANH, tanhf –, tanhl –](tanh-tanhf-tanhl.md)<br/>
