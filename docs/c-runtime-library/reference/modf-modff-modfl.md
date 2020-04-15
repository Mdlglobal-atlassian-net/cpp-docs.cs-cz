---
title: modf, modff, modfl
ms.date: 4/2/2020
api_name:
- modff
- modf
- modfl
- _o_modf
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
- modff
- _modfl
- modf
- modfl
- math/modf
- math/modff
- math/modfl
helpviewer_keywords:
- modf function
- modff function
- modfl function
ms.assetid: b1c7abf5-d476-43ca-a03c-02072a86e32d
ms.openlocfilehash: b509da5f18ea1f606b8a3b47ab66a78e4f595558
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338688"
---
# <a name="modf-modff-modfl"></a>modf, modff, modfl

Rozdělí hodnotu s plovoucí desetinnou desetinnou hodnotou na zlomkové a celé části.

## <a name="syntax"></a>Syntaxe

```C
double modf( double x, double * intptr );
float modff( float x, float * intptr );
long double modfl( long double x, long double * intptr );
```

```cpp
float modf( float x, float * intptr );  // C++ only
long double modf( long double x, long double * intptr );  // C++ only
```

### <a name="parameters"></a>Parametry

*X*<br/>
Hodnota s plovoucí desetinnou táceckou.

*Intptr*<br/>
Ukazatel na uloženou část celého čísla.

## <a name="return-value"></a>Návratová hodnota

Tato funkce vrátí podepsanou zlomkovou část *x*. Neexistuje žádná chyba vrátit.

## <a name="remarks"></a>Poznámky

**Modf** funkce rozdělit hodnotu s plovoucí desetinnou hodnotou *x* na frakční a celočíselné části, z nichž každá má stejné znaménko jako *x*. Podepsaná zlomková část *x* je vrácena. Celá část je uložena jako hodnota s plovoucí desetinnou hodnotou *v intptr*.

**modf** má implementaci, která používá streaming SIMD extensions 2 (SSE2). Informace a omezení týkající se používání implementace SSE2 naleznete v [_set_SSE2_enable.](set-sse2-enable.md)

C++ umožňuje přetížení, takže můžete volat přetížení **modf,** které trvat a vrátit **float** nebo **dlouhé** **dvojité** parametry. V programu C **modf** vždy trvá dvě dvojité hodnoty a vrátí dvojitou hodnotu.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**modf**, **modff**, **modfl**|C: \<math.h><br /><br /> C++: \<, cmath \<> nebo math.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_modf.c

#include <math.h>
#include <stdio.h>

int main( void )
{
   double x, y, n;

   x = -14.87654321;      /* Divide x into its fractional */
   y = modf( x, &n );     /* and integer parts            */

   printf( "For %f, the fraction is %f and the integer is %.f\n",
           x, y, n );
}
```

```Output
For -14.876543, the fraction is -0.876543 and the integer is -14
```

## <a name="see-also"></a>Viz také

[Podpora s plovoucí desetinnou tálicí](../../c-runtime-library/floating-point-support.md)<br/>
[frexp](frexp.md)<br/>
[ldexp](ldexp.md)<br/>
