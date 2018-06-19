---
title: Atan atanf –, atanl –, atan2, atan2f –, atan2l – | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- atan2f
- atan2l
- atan2
- atanf
- atan
- atanl
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
- atan
- atan2l
- atan2
- atanl
- atanf
- atan2f
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5e1f8b60c25c57e3e2eb6a9a964fd80664e3aa4c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32393895"
---
# <a name="atan-atanf-atanl-atan2-atan2f-atan2l"></a>atan, atanf, atanl, atan2, atan2f, atan2l

Vypočítá Arkus tangens **x** (**atan**, **atanf –**, a **atanl –**) nebo Arkus tangens **y** / **x** (**atan2**, **atan2f –**, a **atan2l –**).

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

**Atan** vrátí Arkus tangens *x* v rozsahu - pí/2 do pí/2 radiánech. **ATAN2** vrátí Arkus tangens *y*/*x* v rozsahu - pí do pí radiánech. Pokud *x* 0, **atan** vrátí hodnotu 0. Pokud oba parametry **atan2** mají hodnotu 0, funkce vrátí hodnotu 0. Všechny výsledky jsou v radiánech.

**ATAN2** známky oba parametry používá k určení kvadrantu návratovou hodnotu.

|Vstup|Výjimka SEH|Matherr – výjimka|
|-----------|-------------------|-----------------------|
|ROZMEZÍ **QNAN**, **IND**|žádná|**_DOMAIN –**|

## <a name="remarks"></a>Poznámky

**Atan** funkce vypočítá Arkus tangens (inverzní funkce tangens) *x*. **ATAN2** vypočítá Arkus tangens *y*/*x* (Pokud *x* rovná 0, **atan2** vrátí pí/2, pokud *y* kladné, pokud - pí/2 *y* je záporný nebo 0, pokud *y* je 0.)

**Atan** má implementace, která používá Streaming SIMD Extensions 2 (SSE2). Informace a omezení o pomocí implementace SSE2 najdete v tématu [_set_sse2_enable –](set-sse2-enable.md).

Protože C++ umožňuje, aby přetížení, můžete volat přetížení **atan** a **atan2** trvají **float** nebo **dlouho** **double**  argumenty. V programu C **atan** a **atan2** vždy provést **dvojité** argumenty a vraťte se **dvojité**.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaná hlavička (C)|Požadovaná hlavička (C++)|
|-------------|---------------------|-|
|**Atan**, **atan2**, **atanf –**, **atan2f –**, **atanl –**, **atan2l –**|\<Math.h >|\<cmath – > nebo \<math.h >|

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

[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[acos, acosf, acosl](acos-acosf-acosl.md)<br/>
[asin, asinf, asinl](asin-asinf-asinl.md)<br/>
[Cos, cosf –, cosl –](cos-cosf-cosl.md)<br/>
[_matherr](matherr.md)<br/>
[sin, sinf, sinl](sin-sinf-sinl.md)<br/>
[tan, tanf, tanl](tan-tanf-tanl.md)<br/>
[_CIatan](../../c-runtime-library/ciatan.md)<br/>
[_CIatan2](../../c-runtime-library/ciatan2.md)<br/>
