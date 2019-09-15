---
title: exp, expf, expl
ms.date: 04/05/2018
api_name:
- expf
- expl
- exp
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
ms.openlocfilehash: 380f3e861b3ae1ba2f57aa781c32829771612b9f
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70941628"
---
# <a name="exp-expf-expl"></a>exp, expf, expl

Vypočítá exponenciální hodnotu.

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
Hodnota s plovoucí desetinnou čárkou, která má exponentiate přirozený logaritmus, je základem *e* .

## <a name="return-value"></a>Návratová hodnota

Funkce **exp** vrátí exponenciální hodnotu parametru s plovoucí desetinnou čárkou, *x*, pokud bylo úspěšné. To znamená, že výsledkem je *e*<sup>*x*</sup>, kde *e* je základem přirozeného logaritmu. Při přetečení vrátí funkce hodnotu INF (nekonečno) a v podtečení, **exp** vrátí hodnotu 0.

|Vstup|Výjimka SEH|Výjimka matherr|
|-----------|-------------------|-----------------------|
|Tiché NaN, neurčité|Žádné|_DOMAIN|
|± Nekonečno|NENÍ|_DOMAIN|
|× ≥ 7.097827 e + 002|NEPŘESNÉ A PŘETEČENÍ|PLNĚ|
|× ≤-7.083964 e + 002|NEPŘESNÉ A PODTEČENÍ|PODTEČENÍ|

Funkce **exp** má implementaci, která používá streaming SIMD Extensions 2 (SSE2). Informace a omezení použití implementace SSE2 najdete v tématu [_set_SSE2_enable](set-sse2-enable.md) .

## <a name="remarks"></a>Poznámky

C++umožňuje přetížení, takže můžete volat přetížení **exp** , která přebírají argument **typu float** nebo **Long Double** . V programu v jazyce C, **exp** vždycky přebírá a vrací **Double**.

## <a name="requirements"></a>Požadavky

|Funkce|Povinné záhlaví jazyka C|Požadovaná C++ hlavička|
|--------------|---------------------|---|
|**exp**, **expf –** , **Expl**|\<Math. h >|\<cmath > nebo \<Math. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

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
