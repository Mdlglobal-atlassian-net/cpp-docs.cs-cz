---
title: fmod, fmodf –, fmodl | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- fmod
- fmodf
- fmodl
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
- fmod
- _fmodl
- fmodf
dev_langs:
- C++
helpviewer_keywords:
- calculating floating-point remainders
- fmodf function
- fmodl function
- fmod function
- floating-point numbers, calculating remainders
ms.assetid: 6962d369-d11f-40b1-a6d7-6f67239f8a23
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9f6cc8cc10c026c5ecd621657c556da883c187f5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32399033"
---
# <a name="fmod-fmodf-fmodl"></a>fmod, fmodf –, fmodl

Vypočítá zbytek s plovoucí desetinnou čárkou.

## <a name="syntax"></a>Syntaxe

```C
double fmod(
   double x,
   double y
);
float fmod(
   float x,
   float y
);  // C++ only
long double fmod(
   long double x,
   long double y
);  // C++ only
float fmodf(
   float x,
   float y
);
long double fmodl(
   long double x,
   long double y
);
```

### <a name="parameters"></a>Parametry

*x*, *y*<br/>
Hodnoty s plovoucí desetinnou čárkou.

## <a name="return-value"></a>Návratová hodnota

**fmod** vrátí s plovoucí desetinnou čárkou zbytek *x* / *y*. Pokud hodnota *y* je 0,0, **fmod** vrátí quiet NaN. Informace o reprezentace quiet NaN pomocí **printf** rodiny, viz [printf](printf-printf-l-wprintf-wprintf-l.md).

## <a name="remarks"></a>Poznámky

**Fmod** funkce vypočítá s plovoucí desetinnou čárkou zbývající *f* z *x* / *y* tak, aby *x*  =  *i* * *y* + *f*, kde *i* celé číslo, *f* má stejné znaménko jako *x*a absolutní hodnotu *f* je menší než absolutní hodnotu *y*.

C++ umožňuje přetížení, takže můžete volat přetížení **fmod** , přijmout a vrátit **float** a **dlouho** **dvojité** hodnoty. V programu C **fmod** vždy přebírá dva **dvojité** argumentů a vrátí **dvojité**.

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**fmod**, **fmodf –**, **fmodl**|\<Math.h >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_fmod.c
// This program displays a floating-point remainder.

#include <math.h>
#include <stdio.h>

int main( void )
{
   double w = -10.0, x = 3.0, z;

   z = fmod( w, x );
   printf( "The remainder of %.2f / %.2f is %f\n", w, x, z );
}
```

```Output
The remainder of -10.00 / 3.00 is -1.000000
```

## <a name="see-also"></a>Viz také

[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[ceil, ceilf, ceill](ceil-ceilf-ceill.md)<br/>
[fabs, fabsf, fabsl](fabs-fabsf-fabsl.md)<br/>
[floor, floorf, floorl](floor-floorf-floorl.md)<br/>
[_CIfmod](../../c-runtime-library/cifmod.md)<br/>
