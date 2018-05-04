---
title: Exp, expf –, expl | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- exponential calculations
- expf function
- expl function
- calculating exponentials
- exp function
ms.assetid: 7070016d-1143-407e-9e9a-6b059bb88867
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e9569eee475a80fc5c08c2ec1d099cf627c7b5fb
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
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
S plovoucí desetinnou čárkou hodnotu exponentiate základ přirozeného logaritmu *e* podle.

## <a name="return-value"></a>Návratová hodnota

**Exp** funkce vrátí hodnotu exponenciálního parametru s plovoucí desetinnou čárkou *x*, pokud bylo úspěšné. Výsledkem je *e*<sup>*x*</sup>, kde *e* je základ přirozeného logaritmu. Na přetečení, vrátí funkce INF (infinity) a na podtečení **exp** vrátí hodnotu 0.

|Vstup|Výjimka SEH|Matherr – výjimka|
|-----------|-------------------|-----------------------|
|Rozmezí quiet NaN neurčitém|Žádné|_DOMAIN –|
|Rozmezí infinity|NEPLATNÝ|_DOMAIN –|
|x ≥ 7.097827e + 002|NEPŘESNÝ + PŘETEČENÍ|PŘETEČENÍ|
|X ≤-7.083964e + 002|PODTEČENÍ NEPŘESNÝ +|PODTEČENÍ|

**Exp** funkce má implementace, která používá Streaming SIMD Extensions 2 (SSE2). V tématu [_set_sse2_enable –](set-sse2-enable.md) informace a omezení používání SSE2 implementace.

## <a name="remarks"></a>Poznámky

C++ umožňuje přetížení, takže můžete volat přetížení **exp** trvají **float** nebo **long double** argument. V programu C **exp** vždy provede a vrátí **dvojité**.

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaná hlavička C|Požadovaná hlavička v C++|
|--------------|---------------------|---|
|**Exp**, **expf –**, **expl**|\<Math.h >|\<cmath – > nebo \<math.h >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

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

[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[log, logf, log10, log10f](log-logf-log10-log10f.md)<br/>
[_CIexp](../../c-runtime-library/ciexp.md)<br/>
