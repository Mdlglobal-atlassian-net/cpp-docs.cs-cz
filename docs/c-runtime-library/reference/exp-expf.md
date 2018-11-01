---
title: Exp, expf –, expl
ms.date: 04/05/2018
apiname:
- expf
- expl
- exp
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
ms.openlocfilehash: b9fb38adcc442e60864ec632cd92793f16e47502
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50596752"
---
# <a name="exp-expf-expl"></a>Exp, expf –, expl

Vypočítá exponent.

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

*x*<br/>
Plovoucí desetinné čárky hodnota, která se exponentiate základ přirozeného logaritmu *e* podle.

## <a name="return-value"></a>Návratová hodnota

**Exp** exponenciální hodnota s plovoucí desetinnou čárkou parametru, vrátí funkce *x*, pokud je úspěšná. To znamená, výsledek je *e*<sup>*x*</sup>, kde *e* je základ přirozeného logaritmu. Při přetečení, funkce vrátí INF (nekonečno) a na podtečení **exp** vrátí hodnotu 0.

|Vstup|Výjimka SEH|Výjimka Matherr|
|-----------|-------------------|-----------------------|
|Rozmezí tichý NaN neurčitý|Žádné|_DOMÉNA|
|Nekonečno přesností|NEPLATNÝ|_DOMÉNA|
|x ≥ 7.097827e + 002|NEPŘESNÉ + PŘETEČENÍ|PŘETEČENÍ|
|X ≤-7.083964e + 002|NEPŘESNÉ + PODTEČENÍ|PODTEČENÍ|

**Exp** funkce má implementace, která používá Streaming SIMD Extensions 2 (SSE2). Zobrazit [_set_sse2_enable –](set-sse2-enable.md) informace a omezení používání implementace SSE2.

## <a name="remarks"></a>Poznámky

Jazyk C++ umožňuje přetížení, takže můžete volat přetížení **exp** trvají **float** nebo **long double** argument. V programu jazyka C **exp** vždy převezme a vrátí **double**.

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaná hlavička C|Požadované hlaviček jazyka C++|
|--------------|---------------------|---|
|**Exp**, **expf –**, **expl**|\<Math.h >|\<cmath > nebo \<math.h >|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Viz také:

[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[log, logf, log10, log10f](log-logf-log10-log10f.md)<br/>
[_CIexp](../../c-runtime-library/ciexp.md)<br/>
