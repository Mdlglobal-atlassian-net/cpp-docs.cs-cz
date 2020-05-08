---
title: FMOD –, fmodf –, fmodl
ms.date: 4/2/2020
api_name:
- fmod
- fmodf
- fmodl
- _o_fmod
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
- fmod
- _fmodl
- fmodf
helpviewer_keywords:
- calculating floating-point remainders
- fmodf function
- fmodl function
- fmod function
- floating-point numbers, calculating remainders
ms.assetid: 6962d369-d11f-40b1-a6d7-6f67239f8a23
ms.openlocfilehash: a6fcb7feeae72ff15d7b1ed0d55c5abbb408135a
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82914959"
---
# <a name="fmod-fmodf-fmodl"></a>FMOD –, fmodf –, fmodl

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

**FMOD –** vrátí zbytek s plovoucí desetinnou čárkou pro *x* / *y*. Pokud hodnota *y* je 0,0, vrátí **FMOD –** tichou hodnotu NaN. Informace o reprezentace tichého NaN **printf** Family naleznete v tématu [printf](printf-printf-l-wprintf-wprintf-l.md).

## <a name="remarks"></a>Poznámky

Funkce **FMOD –** vypočítá zbytek s plovoucí desetinnou čárkou *f* z *x* / *y* tak, že *x* = *i* \* *y* + *f*, kde *i* je celé číslo, *f* má stejné znaménko jako *x*a absolutní hodnota *f* je menší než absolutní hodnota *y*.

Jazyk C++ umožňuje přetížení, takže můžete volat přetížení **FMOD –** , která přijímají a vracejí hodnoty **float** a **Long** **Double** . V programu v jazyce C **FMOD –** vždy přebírá dva **dvojité** argumenty a vrací hodnotu **Double**.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**FMOD –**, **fmodf –**, **fmodl**|\<Math. h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

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
