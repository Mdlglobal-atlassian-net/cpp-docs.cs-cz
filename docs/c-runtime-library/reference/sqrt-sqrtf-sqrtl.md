---
title: Sqrt, sqrtf –, sqrtl – | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- sqrtf function
- sqrt function
- sqrtl function
- _sqrtl function
- calculating square roots
- square roots, calculating
ms.assetid: 2ba9467b-f172-41dc-8f10-b86f68fa813c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a6eefbbf3269ad809cdf30dd3ea034f7ca6c8ad8
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32407298"
---
# <a name="sqrt-sqrtf-sqrtl"></a>Sqrt, sqrtf –, sqrtl –

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

Protože C++ umožňuje, aby přetížení, můžete volat přetížení **sqrt** trvají **float** nebo **dlouho** **dvojité** typy. V programu C **sqrt** vždy provede a vrátí **dvojité**.

## <a name="return-value"></a>Návratová hodnota

**Sqrt** funkce vrátí druhou odmocninu výsledku *x*. Ve výchozím nastavení pokud *x* záporné, **sqrt** vrátí neomezené NaN.

|Vstup|Výjimka SEH|**_matherr –** výjimky|
|-----------|-------------------|--------------------------|
|ROZMEZÍ QNAN, IND|žádná|_DOMAIN –|
|- ∞|žádná|_DOMAIN –|
|x<0|žádná|_DOMAIN –|

## <a name="requirements"></a>Požadavky

|Funkce|Hlavička C|Hlavička C++|
|--------------|--------------|------------------|
|**Sqrt**, **sqrtf –**, **sqrtl –**|\<Math.h >|\<cmath – >|

Informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Viz také

[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[exp, expf, expl](exp-expf.md)<br/>
[log, logf, log10, log10f](log-logf-log10-log10f.md)<br/>
[pow, powf, powl](pow-powf-powl.md)<br/>
[_CIsqrt](../../c-runtime-library/cisqrt.md)<br/>
