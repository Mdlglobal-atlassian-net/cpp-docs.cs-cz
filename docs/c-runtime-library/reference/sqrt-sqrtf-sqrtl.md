---
title: sqrt, sqrtf, sqrtl
ms.date: 04/05/2018
api_name:
- sqrtl
- sqrtf
- sqrt
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
- ntoskrnl.exe
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: 9805141a630afc123c19416595b2a96bc801eee3
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70958099"
---
# <a name="sqrt-sqrtf-sqrtl"></a>sqrt, sqrtf, sqrtl

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

Vzhledem C++ k tomu, že umožňuje přetížení, můžete volat přetížení **odmocniny** , které přebírají typ **float** nebo **Long** **Double** . V programu v jazyce C **odmocnina** vždy přebírá a vrací hodnotu **Double**.

## <a name="return-value"></a>Návratová hodnota

Funkce **Sqrt** Vrátí druhou odmocninu *x*. Ve výchozím nastavení, pokud je *x* záporné, **odmocnina** vrátí nekonečnou hodnotu NaN.

|Vstup|Výjimka SEH|**_matherr** Jímka|
|-----------|-------------------|--------------------------|
|QNAN, ZASÁHNOUT|žádná|_DOMAIN|
|- ∞|žádná|_DOMAIN|
|x < 0|žádná|_DOMAIN|

## <a name="requirements"></a>Požadavky

|Funkce|Hlavička jazyka C|C++hlaviček|
|--------------|--------------|------------------|
|**sqrt**, **sqrtf**, **sqrtl**|\<Math. h >|\<cmath >|

Informace o kompatibilitě najdete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

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
