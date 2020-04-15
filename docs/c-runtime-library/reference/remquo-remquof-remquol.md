---
title: remquo, remquof, remquol
ms.date: 4/2/2020
api_name:
- remquof
- remquo
- remquol
- _o_remquo
- _o_remquof
- _o_remquol
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: e6a6f211e83118379e0697464d21f5968ea68cee
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81332842"
---
# <a name="remquo-remquof-remquol"></a>remquo, remquof, remquol

Vypočítá zbývající dvě celé hodnoty a uloží celou hodnotu se znaménkem a přibližnou velikostí podílu v umístění určeném v parametru.

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

*číslo*<br/>
Čitatel.

*denom*<br/>
Jmenovatel.

*Quo*<br/>
Ukazatel na celé číslo pro uložení hodnoty, která má znaménko a přibližnou velikost kvocientu.

## <a name="return-value"></a>Návratová hodnota

**vrátí** zbytek s plovoucí desetinnou cívka *x* / *y*. Pokud je hodnota *y* 0,0, **vrátí funkce remquo** tichou NaN. Informace o reprezentaci tiché honosné NaN rodinou **printf** naleznete v [tématu printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md).

## <a name="remarks"></a>Poznámky

Funkce **remquo** vypočítá zbytek s plovoucí desetinnou cínek *f* *x* / *y* tak, že *x* = *i* \* *y* + *f*, kde *i* je celé číslo, *f* má stejné znaménko jako *x*a absolutní hodnota *f* je menší než absolutní hodnota *y*.

C++ umožňuje přetížení, takže můžete volat přetížení **remquo,** které take a return **float** nebo **dlouhé** **dvojité** hodnoty. V programu C **remquo** vždy trvá dva **dvojité** argumenty a vrátí **double**.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Funkce|Povinná hlavička (C)|Povinné záhlaví (C++)|
|--------------|---------------------|-|
|**remquo**, **remquof**, **remquol**|\<math.h>|\<cmath> \<nebo math.h>|

Informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

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

[Podpora s plovoucí desetinnou tálicí](../../c-runtime-library/floating-point-support.md)<br/>
[ldiv, lldiv](ldiv-lldiv.md)<br/>
[imaxdiv](imaxdiv.md)<br/>
[fmod, fmodf](fmod-fmodf.md)<br/>
[remainder, remainderf, remainderl](remainder-remainderf-remainderl.md)<br/>
