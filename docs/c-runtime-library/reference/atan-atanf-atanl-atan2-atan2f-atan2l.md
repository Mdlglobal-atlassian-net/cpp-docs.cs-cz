---
title: atan, atanf, atanl, atan2, atan2f, atan2l
ms.date: 04/05/2018
api_name:
- atan2f
- atan2l
- atan2
- atanf
- atan
- atanl
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
ms.openlocfilehash: 8c485dea281d2b754628c9663e38ea10a9b6ab57
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70939607"
---
# <a name="atan-atanf-atanl-atan2-atan2f-atan2l"></a>atan, atanf, atanl, atan2, atan2f, atan2l

Vypočítá arkustangens **x** (**Atan**, **atanf –** a **atanl**) nebo arkustangens **y**/**x** (**ARCTG2**, **atan2f –** a **atan2l**).

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
Libovolná čísla.

## <a name="return-value"></a>Návratová hodnota

**Atan** Vrátí arkustangens *x* v rozsahu-π/2 na π/2 radiány. funkce **ARCTG2** vrací arkustangens *y*/*x* v rozsahu od-π do π radiánů. Pokud je *x* 0, funkce **Atan** vrátí hodnotu 0. Pokud jsou oba parametry funkce **ARCTG2** 0, vrátí funkce hodnotu 0. Všechny výsledky jsou v radiánech.

funkce **ARCTG2** používá znaménka obou parametrů k určení kvadrantu návratové hodnoty.

|Vstup|Výjimka SEH|Výjimka matherr|
|-----------|-------------------|-----------------------|
|± **QNAN**, **IND**|žádná|**_DOMAIN**|

## <a name="remarks"></a>Poznámky

Funkce **Atan** vypočítá arkustangens (funkci inverzní tangens) *x*. funkce **ARCTG2** vypočítá arkustangens *y*/*x* (Pokud *x* Equals 0, funkce **ARCTG2** vrátí π/2, pokud *y* je kladné,-π/2, pokud *y* je záporné nebo 0, pokud je *y* 0.)

**Atan** má implementaci, která používá streaming SIMD Extensions 2 (SSE2). Informace a omezení týkající se použití implementace SSE2 naleznete v tématu [_set_SSE2_enable](set-sse2-enable.md).

Vzhledem C++ k tomu, že umožňuje přetížení, můžete volat přetížení funkce **Atan** a **ARCTG2** , které přebírají argumenty **typu float** nebo **Long** **Double** . V programu v jazyce C mají funkce **Atan** a **ARCTG2** vždycky argumenty **Double** a vracet hodnotu **Double**.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaná hlavička (C)|Požadovaná hlavička (C++)|
|-------------|---------------------|-|
|**Atan**, **ARCTG2**, **atanf –** , **atan2f –** , **atanl**, **atan2l**|\<Math. h >|\<cmath > nebo \<Math. h >|

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

## <a name="see-also"></a>Viz také:

[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[acos, acosf, acosl](acos-acosf-acosl.md)<br/>
[asin, asinf, asinl](asin-asinf-asinl.md)<br/>
[cos, cosf, cosl](cos-cosf-cosl.md)<br/>
[_matherr](matherr.md)<br/>
[sin, sinf, sinl](sin-sinf-sinl.md)<br/>
[tan, tanf, tanl](tan-tanf-tanl.md)<br/>
[_CIatan](../../c-runtime-library/ciatan.md)<br/>
[_CIatan2](../../c-runtime-library/ciatan2.md)<br/>
