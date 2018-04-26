---
title: atanh – atanhf –, atanhl – | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- atanhl
- atanhf
- atanh
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
- atanhl
- atanhf
- atanh
dev_langs:
- C++
helpviewer_keywords:
- atanhf function
- atanhl function
- atanh funciton
ms.assetid: 83a43b5b-2580-4461-854f-dc84236d9f32
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5f56568fa4e38d68e45acf976a8802971e63ea66
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2018
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

*x*<br/>
Hodnota s plovoucí desetinnou čárkou.

## <a name="return-value"></a>Návratová hodnota

**Atanh –** funkce vrátí hyberbolic inverzní tangens (oblouk hyperbolický tangens) *x*. Pokud *x* je větší než 1 a menší než -1, **errno** je nastaven na **edom –** a výsledkem je quiet NaN. Pokud *x* se rovná 1 nebo -1, kladné a záporné infinity se vrátí, v uvedeném pořadí, a **errno** je nastaven na **erange –**.

|Vstup|Výjimka SEH|**Matherr –** výjimky|
|-----------|-------------------|-------------------------|
|ROZMEZÍ QNAN, IND|žádná|žádná|
|*X* ≥ 1; *x* ≤ -1|žádná|žádná|

## <a name="remarks"></a>Poznámky

Protože C++ umožňuje, aby přetížení, můžete volat přetížení **atanh –** , přijmout a vrátit **float** nebo **dlouho** **dvojité** hodnoty. V programu C **atanh –** vždy provede a vrátí **dvojité**.

## <a name="requirements"></a>Požadavky

|Funkce|Hlavička C|Hlavička C++|
|--------------|--------------|------------------|
|**atanh –**, **atanhf –**, **atanhl –**|\<Math.h >|\<cmath – > nebo \<math.h >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

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
[COSH, coshf –, coshl –](cosh-coshf-coshl.md)<br/>
[SINH, sinhf –, sinhl –](sinh-sinhf-sinhl.md)<br/>
[TANH, tanhf –, tanhl –](tanh-tanhf-tanhl.md)<br/>
