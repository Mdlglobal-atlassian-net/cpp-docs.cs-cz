---
title: atan, atanf, atanl, atan2, atan2f, atan2l
ms.date: 4/2/2020
api_name:
- atan2f
- atan2l
- atan2
- atanf
- atan
- atanl
- _o_atan
- _o_atan2
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
- atan
- atan2l
- atan2
- atanl
- atanf
- atan2f
helpviewer_keywords:
- atan function
- atanf function
- atanl function
- atan2 function
- atan2l function
- arctangent function
- trigonometric functions
- atan2f function
ms.assetid: 7a87a18e-c94d-4727-9cb1-1bb5c2725ae4
ms.openlocfilehash: 3b8411f9839022477dff3100792e271e2f0b572b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81334119"
---
# <a name="atan-atanf-atanl-atan2-atan2f-atan2l"></a>atan, atanf, atanl, atan2, atan2f, atan2l

Vypočítá arctangent **x** (**atan**, **atanf**, a **atanl**) nebo arctangent **y**/**x** (**atan2**, **atan2f**, a **atan2l**).

## <a name="syntax"></a>Syntaxe

```C
double atan( double x );
float atanf( float x );
long double atanl( long double x );

double atan2( double y, double x );
float atan2f( float y, float x );
long double atan2l( long double y, long double x );
```

```cpp
float atan( float x );  // C++ only
long double atan( long double x );  // C++ only

float atan2( float y, float x );  // C++ only
long double atan2( long double y, long double x );  // C++ only
```

### <a name="parameters"></a>Parametry

*x*, *y*<br/>
Všechna čísla.

## <a name="return-value"></a>Návratová hodnota

**atan** vrátí arctangent *x* v rozsahu -π/2 až π/2 radiánů. **atan2** vrátí arctangent *y*/*x* v rozsahu -π to π radiány. Pokud *x* je 0, **atan** vrátí 0. Pokud oba parametry **atan2** jsou 0, funkce vrátí 0. Všechny výsledky jsou v radiánech.

**atan2** používá znaménky obou parametrů k určení kvadrantu vrácené hodnoty.

|Vstup|Výjimka SEH|Výjimka Matherr|
|-----------|-------------------|-----------------------|
|± **QNAN**, **IND**|Žádná|**_DOMAIN**|

## <a name="remarks"></a>Poznámky

Funkce **atan** vypočítá arctangen (inverzní tečovou funkci) *x*. **atan2** vypočítá arctangent *y*/*x* (pokud *x* rovná 0, **atan2** vrátí π/2, pokud *y* je kladná, -π/2, pokud *y* je záporná, nebo 0, pokud *y* je 0.)

**atan** má implementaci, která používá streaming SIMD rozšíření 2 (SSE2). Informace a omezení týkající se použití implementace SSE2 naleznete [v tématu _set_SSE2_enable](set-sse2-enable.md).

Protože C++ umožňuje přetížení, můžete volat přetížení **atan** a **atan2,** které trvat **float** nebo **dlouhé** **dvojité** argumenty. V programu C **atan** a **atan2** vždy vzít **dvojité** argumenty a vrátit **double**.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Povinná hlavička (C)|Povinné záhlaví (C++)|
|-------------|---------------------|-|
|**atan**, **atan2**, **atanf**, **atan2f**, **atanl**, **atan2l**|\<math.h>|\<cmath> \<nebo math.h>|

## <a name="example"></a>Příklad

```C
// crt_atan.c
// arguments: 5 0.5
#include <math.h>
#include <stdio.h>
#include <errno.h>

int main( int ac, char* av[] )
{
   double x, y, theta;
   if( ac != 3 ){
      fprintf( stderr, "Usage: %s <x> <y>\n", av[0] );
      return 1;
   }
   x = atof( av[1] );
   theta = atan( x );
   printf( "Arctangent of %f: %f\n", x, theta );
   y = atof( av[2] );
   theta = atan2( y, x );
   printf( "Arctangent of %f / %f: %f\n", y, x, theta );
   return 0;
}
```

```Output
Arctangent of 5.000000: 1.373401
Arctangent of 0.500000 / 5.000000: 0.099669
```

## <a name="see-also"></a>Viz také

[Podpora s plovoucí desetinnou tálicí](../../c-runtime-library/floating-point-support.md)<br/>
[acos, acosf, acosl](acos-acosf-acosl.md)<br/>
[asin, asinf, asinl](asin-asinf-asinl.md)<br/>
[cos, cosf, cosl](cos-cosf-cosl.md)<br/>
[_matherr](matherr.md)<br/>
[sin, sinf, sinl](sin-sinf-sinl.md)<br/>
[tan, tanf, tanl](tan-tanf-tanl.md)<br/>
[_CIatan](../../c-runtime-library/ciatan.md)<br/>
[_CIatan2](../../c-runtime-library/ciatan2.md)<br/>
