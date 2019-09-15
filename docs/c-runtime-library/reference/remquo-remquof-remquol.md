---
title: remquo, remquof, remquol
ms.date: 04/05/2018
api_name:
- remquof
- remquo
- remquol
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
- remquof
- remquol
- remquo
helpviewer_keywords:
- remquol function
- remquof function
- remquo function
ms.assetid: a1d3cb8b-8027-4cd3-8deb-04eb17f299fc
ms.openlocfilehash: c96357dda007e9bf12ddaf6091af47794bfc0630
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70949364"
---
# <a name="remquo-remquof-remquol"></a>remquo, remquof, remquol

Vypočítá zbytek dvou celočíselných hodnot a uloží celočíselnou hodnotu se znaménkem a přibližnou velikostí podílu v umístění, které je zadáno v parametru.

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

*numer*<br/>
Čitatel.

*denom*<br/>
Jmenovatel.

*quo*<br/>
Ukazatel na celé číslo, aby se uložila hodnota, která má znaménko a přibližnou velikost podílu.

## <a name="return-value"></a>Návratová hodnota

**remquo –** vrátí zbytek s plovoucí desetinnou čárkou pro *x* / *y*. Pokud hodnota *y* je 0,0, vrátí **remquo –** tichou hodnotu NaN. Informace o reprezentace tichého NaN **printf** Family naleznete v tématu [printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md).

## <a name="remarks"></a>Poznámky

Funkce **remquo –** vypočítá zbytek s plovoucí desetinnou čárkou *f* z *x* / *y* tak, aby *x* = *i* \* *y* + *f*, kde *i* je celé číslo, *f* má stejné znaménko jako *x*a absolutní hodnota *f* je menší než absolutní hodnota *y*.

C++umožňuje přetížení, takže můžete volat přetížení **remquo –** , která přijímají a vracejí hodnoty **float** nebo **Long** **Double** . V programu v jazyce C **remquo –** vždy přebírá dva **dvojité** argumenty a vrací hodnotu **Double**.

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaná hlavička (C)|Požadovaná hlavička (C++)|
|--------------|---------------------|-|
|**remquo**, **remquof**, **remquol**|\<Math. h >|\<cmath > nebo \<Math. h >|

Informace o kompatibilitě najdete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

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
