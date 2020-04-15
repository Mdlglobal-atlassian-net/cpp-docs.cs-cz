---
title: exp, expf, expl
ms.date: 4/2/2020
api_name:
- expf
- expl
- exp
- _o_exp
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
- _expl
- expf
- expl
- exp
helpviewer_keywords:
- exponential calculations
- expf function
- expl function
- calculating exponentials
- exp function
ms.assetid: 7070016d-1143-407e-9e9a-6b059bb88867
ms.openlocfilehash: cbf303b2b92afd83a1c3181dc98a1dbdcd639c1b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81347588"
---
# <a name="exp-expf-expl"></a>exp, expf, expl

Vypočítá exponenciální.

## <a name="syntax"></a>Syntaxe

```C
double exp(
   double x
);
float exp(
   float x
);  // C++ only
long double exp(
   long double x
);  // C++ only
float expf(
   float x
);
long double expl(
   long double x
);
```

### <a name="parameters"></a>Parametry

*X*<br/>
Hodnota s plovoucí desetinnou hodnotou exponenciátní přírodní logaritmu základnu *e* by.

## <a name="return-value"></a>Návratová hodnota

**Exp** funkce vrátí exponenciální hodnotu parametru s plovoucí desetinnou, *x*, pokud je úspěšná. To znamená, že výsledkem je *e*<sup>*x*</sup>, kde *e* je základem přirozeného logaritmu. Při přetečení vrátí funkce INF (nekonečno) a při podtečení **vrátí hodnotu exp** 0.

|Vstup|Výjimka SEH|Výjimka Matherr|
|-----------|-------------------|-----------------------|
|± Tichý NaN, neurčitý|Žádný|_DOMAIN|
|± Nekonečno|Neplatný|_DOMAIN|
|x ≥ 7,097827e+002|NEPŘESNÉ + PŘETEČENÍ|Přetečení|
|X ≤ -7,083964e+002|NEPŘESNÉ + PODTEČENÍ|Podtečení|

Funkce **exp** má implementaci, která používá streaming SIMD extensions 2 (SSE2). Informace a omezení týkající se používání implementace SSE2 naleznete v [_set_SSE2_enable.](set-sse2-enable.md)

## <a name="remarks"></a>Poznámky

C++ umožňuje přetížení, takže můžete volat přetížení **exp,** které trvat **float** nebo **dlouhý dvojitý** argument. V programu C **exp** vždy trvá a vrací **double**.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Funkce|Povinná hlavička C|Povinná hlavička jazyka C++|
|--------------|---------------------|---|
|**exp**, **expf**, **expl**|\<math.h>|\<cmath> \<nebo math.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_exp.c

#include <math.h>
#include <stdio.h>

int main( void )
{
   double x = 2.302585093, y;

   y = exp( x );
   printf( "exp( %f ) = %f\n", x, y );
}
```

```Output
exp( 2.302585 ) = 10.000000
```

## <a name="see-also"></a>Viz také

[Podpora s plovoucí desetinnou tálicí](../../c-runtime-library/floating-point-support.md)<br/>
[log, logf, log10, log10f](log-logf-log10-log10f.md)<br/>
[_CIexp](../../c-runtime-library/ciexp.md)<br/>
