---
title: remquo – remquof –, remquol – | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- remquol function
- remquof function
- remquo function
ms.assetid: a1d3cb8b-8027-4cd3-8deb-04eb17f299fc
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2582ab0e2aba8c0798568454c3e1532982f0ffd9
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2018
---
# <a name="remquo-remquof-remquol"></a>remquo, remquof, remquol

Vypočítá zbytek dvě celočíselné hodnoty a ukládá hodnotu celého čísla se přihlaste a přibližný odhad podílu v umístění zadaném v parametr.

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
Čítači.

*denom*<br/>
Jmenovatel.

*současný*<br/>
Ukazatel na celočíselnou hodnotu, která má přihlašovací a přibližný odhad podílu ukládat.

## <a name="return-value"></a>Návratová hodnota

**remquo –** vrátí s plovoucí desetinnou čárkou zbytek *x* / *y*. Pokud hodnota *y* je 0,0, **remquo –** vrátí quiet NaN. Informace o reprezentace quiet NaN pomocí **printf** rodiny, viz [printf _printf_l –, wprintf, _wprintf_l –](printf-printf-l-wprintf-wprintf-l.md).

## <a name="remarks"></a>Poznámky

**Remquo –** funkce vypočítá s plovoucí desetinnou čárkou zbývající *f* z *x* / *y* tak, aby *x*   =  *i* * *y* + *f*, kde *i* je celé číslo , *f* má stejné znaménko jako *x*a absolutní hodnotu *f* je menší než absolutní hodnotu *y*.

C++ umožňuje přetížení, takže můžete volat přetížení **remquo –** , přijmout a vrátit **float** nebo **dlouho** **dvojité** hodnoty. V programu C **remquo –** vždy přebírá dva **dvojité** argumentů a vrátí **dvojité**.

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaná hlavička (C)|Požadovaná hlavička (C++)|
|--------------|---------------------|-|
|**remquo –**, **remquof –**, **remquol –**|\<Math.h >|\<cmath – > nebo \<math.h >|

Informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Viz také

[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[ldiv, lldiv](ldiv-lldiv.md)<br/>
[imaxdiv](imaxdiv.md)<br/>
[fmod, fmodf](fmod-fmodf.md)<br/>
[remainder, remainderf, remainderl](remainder-remainderf-remainderl.md)<br/>
