---
title: remquo, remquof, remquol
ms.date: 04/05/2018
apiname:
- remquof
- remquo
- remquol
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
- remquof
- remquol
- remquo
helpviewer_keywords:
- remquol function
- remquof function
- remquo function
ms.assetid: a1d3cb8b-8027-4cd3-8deb-04eb17f299fc
ms.openlocfilehash: 4c7e93806600ff674baf186a66662aafdeceeaca
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50605101"
---
# <a name="remquo-remquof-remquol"></a>remquo, remquof, remquol

Vypočítá zbytek dvou celočíselných hodnot a uloží hodnotu celého čísla se znaménkem a přibližnou velikosti podílu v umístění zadaném v parametr.

## <a name="syntax"></a>Syntaxe

```C
double remquo( double numer, double denom, int* quo );
float remquof( float numer, float denom, int* quo );
long double remquol( long double numer, long double denom, int* quo );
```

```cpp
float remquo( float numer, float denom, int* quo ); /* C++ only */
long double remquo( long double numer, long double denom, int* quo ); /* C++ only */
```

### <a name="parameters"></a>Parametry

*počet*<br/>
Čítač.

*denom*<br/>
Jmenovatel.

*současný*<br/>
Ukazatel na celé číslo k uložení hodnoty se znaménkem a přibližnou velikostí podílu.

## <a name="return-value"></a>Návratová hodnota

**remquo –** Vrátí zbytek s plovoucí desetinnou čárkou z *x* / *y*. Pokud hodnota *y* je 0,0, **remquo –** vrátí tichý NaN. Informace o reprezentaci tichého NaN **printf** řady, viz [printf _printf_l –, wprintf _wprintf_l –](printf-printf-l-wprintf-wprintf-l.md).

## <a name="remarks"></a>Poznámky

**Remquo –** funkce vypočítá zbytek s plovoucí desetinnou čárkou *f* z *x* / *y* tak, aby *x*   =  *můžu* \* *y* + *f*, kde *můžu* je celé číslo , *f* má stejné znaménko jako *x*a absolutní hodnota *f* je menší než absolutní hodnota *y*.

Jazyk C++ umožňuje přetížení, takže můžete volat přetížení **remquo –** , která používají a vrací **float** nebo **dlouhé** **double** hodnoty. V programu jazyka C **remquo –** vždy má dva **double** argumenty a vrátí **double**.

## <a name="requirements"></a>Požadavky

|Funkce|Požadované záhlaví (C)|Požadované záhlaví (C++)|
|--------------|---------------------|-|
|**remquo –**, **remquof –**, **remquol –**|\<Math.h >|\<cmath > nebo \<math.h >|

Informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_remquo.c
// This program displays a floating-point remainder.

#include <math.h>
#include <stdio.h>

int main( void )
{
   double w = -10.0, x = 3.0, z;
   int quo = 0;

   z = remquo(w, x, &quo);
   printf("The remainder of %.2f / %.2f is %f\n", w, x, z);
   printf("Approximate signed quotient is %d\n", quo);
}
```

```Output
The remainder of -10.00 / 3.00 is -1.000000
Approximate signed quotient is -3
```

## <a name="see-also"></a>Viz také:

[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[ldiv, lldiv](ldiv-lldiv.md)<br/>
[imaxdiv](imaxdiv.md)<br/>
[fmod, fmodf](fmod-fmodf.md)<br/>
[remainder, remainderf, remainderl](remainder-remainderf-remainderl.md)<br/>
