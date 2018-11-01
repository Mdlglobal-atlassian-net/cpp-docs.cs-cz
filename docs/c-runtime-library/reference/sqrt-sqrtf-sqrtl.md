---
title: Sqrt sqrtf –, sqrtl –
ms.date: 04/05/2018
apiname:
- sqrtl
- sqrtf
- sqrt
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
- sqrt
- sqrtf
- _sqrtl
helpviewer_keywords:
- sqrtf function
- sqrt function
- sqrtl function
- _sqrtl function
- calculating square roots
- square roots, calculating
ms.assetid: 2ba9467b-f172-41dc-8f10-b86f68fa813c
ms.openlocfilehash: c44f8813812b2aeffc2680a0a666d968bb2b4da6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50560573"
---
# <a name="sqrt-sqrtf-sqrtl"></a>Sqrt sqrtf –, sqrtl –

Vypočítá druhou odmocninu.

## <a name="syntax"></a>Syntaxe

```C
double sqrt(
   double x
);
float sqrt(
   float x
);  // C++ only
long double sqrt(
   long double x
);  // C++ only
float sqrtf(
   float x
);
long double sqrtl(
   long double x
);
```

### <a name="parameters"></a>Parametry

*x*<br/>
Nezáporná hodnota s plovoucí desetinnou čárkou

## <a name="remarks"></a>Poznámky

Protože jazyk C++ umožňuje přetížení, můžete volat přetížení **sqrt** trvají **float** nebo **dlouhé** **double** typy. V programu jazyka C **sqrt** vždy převezme a vrátí **double**.

## <a name="return-value"></a>Návratová hodnota

**Sqrt** funkce vrátí druhou odmocninu z *x*. Ve výchozím nastavení pokud *x* je záporný, **sqrt** vrátí nekonečno hodnotu NaN.

|Vstup|Výjimka SEH|**_matherr** výjimky|
|-----------|-------------------|--------------------------|
|ROZMEZÍ QNAN, AJÍT|žádná|_DOMÉNA|
|- ∞|žádná|_DOMÉNA|
|x<0|žádná|_DOMÉNA|

## <a name="requirements"></a>Požadavky

|Funkce|Záhlaví C|Hlaviček jazyka C++|
|--------------|--------------|------------------|
|**Sqrt**, **sqrtf –**, **sqrtl –**|\<Math.h >|\<cmath >|

Informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_sqrt.c
// This program calculates a square root.

#include <math.h>
#include <stdio.h>
#include <stdlib.h>

int main( void )
{
   double question = 45.35, answer;
   answer = sqrt( question );
   if( question < 0 )
      printf( "Error: sqrt returns %f\n", answer );
   else
      printf( "The square root of %.2f is %.2f\n", question, answer );
}
```

```Output
The square root of 45.35 is 6.73
```

## <a name="see-also"></a>Viz také:

[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[exp, expf, expl](exp-expf.md)<br/>
[log, logf, log10, log10f](log-logf-log10-log10f.md)<br/>
[pow, powf, powl](pow-powf-powl.md)<br/>
[_CIsqrt](../../c-runtime-library/cisqrt.md)<br/>
