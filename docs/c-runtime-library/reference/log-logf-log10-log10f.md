---
title: log, logf –, logl, log10 –, log10f –, log10l
ms.date: 4/2/2020
api_name:
- log10f
- logf
- log10
- log
- log10l
- logl
- _o_log
- _o_log10
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- logf
- logl
- _log10l
- log
- _logl
- log10f
- log10l
- log10
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
ms.openlocfilehash: 0acfbefb1fb01215e543538b9fdb8d554b10f8c1
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82911481"
---
# <a name="log-logf-logl-log10-log10f-log10l"></a>log, logf –, logl, log10 –, log10f –, log10l

Vypočítá logaritmy.

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

*znak*<br/>
Hodnota, jejíž logaritmus má být nalezen.

## <a name="return-value"></a>Návratová hodnota

Funkce **protokolu** Vrátí přirozený logaritmus (základ *e*) *x* v případě úspěchu. Funkce **log10 –** vrací logaritmus o základu 10. Pokud je *x* záporné, vrátí tyto funkce ve výchozím nastavení neurčitelné (). Pokud je *x* 0, vrátí nekonečno (INF).

|Vstup|Výjimka SEH|Výjimka matherr|
|-----------|-------------------|-----------------------|
|QNAN, ZASÁHNOUT|žádné|_DOMAIN|
|± 0|ZERODIVIDE|_SING|
|*x* < 0|NENÍ|_DOMAIN|

**protokol** a **log10 –** mají implementaci, která používá streaming SIMD Extensions 2 (SSE2). Informace a omezení použití implementace SSE2 najdete v tématu [_set_SSE2_enable](set-sse2-enable.md) .

## <a name="remarks"></a>Poznámky

Jazyk C++ umožňuje přetížení, takže můžete volat přetížení **log** a **log10 –** , která přijímají a vracejí hodnoty **float** nebo **Long Double** . V programu v jazyce C, **protokol** a **log10 –** vždycky přebírají a vracejí **dvojitou**hodnotu.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**log**, **logf –**, **logl**, **log10 –**, **log10f –**, **log10l**|\<Math. h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

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

Chcete-li generovat logaritmy pro jiné základy, použijte matematický vztah: log Base b of a = = přirozený protokol (a)/přirozený protokol (b).

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
