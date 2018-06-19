---
title: protokol, logf –, logl, log10, log10f –, log10l | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- log10f
- logf
- log10
- log
- log10l
- logl
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
- logf
- logl
- _log10l
- log
- _logl
- log10f
- log10l
- log10
dev_langs:
- C++
helpviewer_keywords:
- calculating logarithms
- log10f function
- log10 function
- log function
- log10l function
- logl function
- logf function
- logarithms
ms.assetid: 7adc77c2-04f7-4245-a980-21215563cfae
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 12f475cde27d4660f4b4936f3f7717a665b70e86
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32402839"
---
# <a name="log-logf-logl-log10-log10f-log10l"></a>protokol, logf –, logl, log10, log10f –, log10l

Vypočítá logaritmů.

## <a name="syntax"></a>Syntaxe

```C
double log( double x );
float logf( float x );
long double logl( double x );
double log10( double x );
float log10f ( float x );
long double log10l( double x );
```

```cpp
float log( float x );  // C++ only
long double log( long double x );  // C++ only
float log10( float x );  // C++ only
long double log10( long double x );  // C++ only
```

### <a name="parameters"></a>Parametry

*x*<br/>
Hodnota, jejíž logaritmus má být nalezen.

## <a name="return-value"></a>Návratová hodnota

**Protokolu** funkce vrátí přirozený logaritmus (základní *e*) z *x* v případě úspěchu. **Log10** funkce Vrátí logaritmus o základu 10. Pokud *x* je záporná, vrátí tyto funkce neomezené (IND), ve výchozím nastavení. Pokud *x* je 0, že budou vracet infinity (INF).

|Vstup|Výjimka SEH|Matherr – výjimka|
|-----------|-------------------|-----------------------|
|ROZMEZÍ QNAN, IND|žádná|_DOMAIN –|
|± 0|ZERODIVIDE|–|
|*x* < 0|NEPLATNÝ|_DOMAIN –|

**protokol** a **log10** mít implementace, která používá Streaming SIMD Extensions 2 (SSE2). V tématu [_set_sse2_enable –](set-sse2-enable.md) informace a omezení používání SSE2 implementace.

## <a name="remarks"></a>Poznámky

C++ umožňuje přetížení, takže můžete volat přetížení **protokolu** a **log10** , přijmout a vrátit **float** nebo **long double** hodnoty. V programu C **protokolu** a **log10** vždy přijmout a vrátit **dvojité**.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**protokol**, **logf –**, **logl**, **log10**, **log10f –**, **log10l**|\<Math.h >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_log.c
/* This program uses log and log10
* to calculate the natural logarithm and
* the base-10 logarithm of 9,000.
*/

#include <math.h>
#include <stdio.h>

int main( void )
{
   double x = 9000.0;
   double y;

   y = log( x );
   printf( "log( %.2f ) = %f\n", x, y );
   y = log10( x );
   printf( "log10( %.2f ) = %f\n", x, y );
}
```

```Output
log( 9000.00 ) = 9.104980
log10( 9000.00 ) = 3.954243
```

Chcete-li vygenerovat logaritmů u jiných základů, použijte matematický vztah: protokolu základní b == přirozené protokolu (a) / přirozené protokolu (b).

```cpp
// logbase.cpp
#include <math.h>
#include <stdio.h>

double logbase(double a, double base)
{
   return log(a) / log(base);
}

int main()
{
   double x = 65536;
   double result;

   result = logbase(x, 2);
   printf("Log base 2 of %lf is %lf\n", x, result);
}
```

```Output
Log base 2 of 65536.000000 is 16.000000
```

## <a name="see-also"></a>Viz také

[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md) <br/>
[exp, expf, expl](exp-expf.md) <br/>
[_matherr](matherr.md) <br/>
[pow, powf, powl](pow-powf-powl.md) <br/>
[_CIlog](../../c-runtime-library/cilog.md) <br/>
[_CIlog10](../../c-runtime-library/cilog10.md)<br/>
