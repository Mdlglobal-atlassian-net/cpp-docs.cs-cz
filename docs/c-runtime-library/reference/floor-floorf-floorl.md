---
title: floor, floorf, floorl
ms.date: 04/05/2018
api_name:
- floorf
- floorl
- floor
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
- floor
- floorl
- _floorl
- floorf
helpviewer_keywords:
- floor function
- floorf function
- calculating floors of values
- floorl function
ms.assetid: e9955f70-d659-414f-8050-132e13c8ff36
ms.openlocfilehash: c646437b4a1d79ef79e53d79fcbc342e5360f3cd
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957160"
---
# <a name="floor-floorf-floorl"></a>floor, floorf, floorl

Vypočítá podlahovou hodnotu hodnoty.

## <a name="syntax"></a>Syntaxe

```C
double floor(
   double x
);
float floor(
   float x
); // C++ only
long double floor(
   long double x
); // C++ only
float floorf(
   float x
);
long double floorl(
   long double x
);
```

### <a name="parameters"></a>Parametry

*x*<br/>
Hodnota s plovoucí desetinnou čárkou.

## <a name="return-value"></a>Návratová hodnota

Funkce **Floor** vrací hodnotu s plovoucí desetinnou čárkou, která představuje největší celé číslo, které je menší nebo rovno *x*. Nevrátila se žádná chybová zpráva.

|Vstup|Výjimka SEH|Výjimka matherr|
|-----------|-------------------|-----------------------|
|QNAN, ZASÁHNOUT|žádná|_DOMAIN|

**podlahová plocha** má implementaci, která používá streaming SIMD Extensions 2 (SSE2). Informace a omezení týkající se použití implementace SSE2 naleznete v tématu [_set_SSE2_enable](set-sse2-enable.md).

## <a name="remarks"></a>Poznámky

C++umožňuje přetížení, takže můžete volat přetížení **podlah** , která přijímají a vracejí hodnoty **float** a **Long** **Double** . V programu v jazyce C má **podlaha** vždycky a vrací hodnotu **Double**.

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**podlahová**, **floorf –á**, **podlahová**|\<Math. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_floor.c
// This example displays the largest integers
// less than or equal to the floating-point values 2.8
// and -2.8. It then shows the smallest integers greater
// than or equal to 2.8 and -2.8.

#include <math.h>
#include <stdio.h>

int main( void )
{
   double y;

   y = floor( 2.8 );
   printf( "The floor of 2.8 is %f\n", y );
   y = floor( -2.8 );
   printf( "The floor of -2.8 is %f\n", y );

   y = ceil( 2.8 );
   printf( "The ceil of 2.8 is %f\n", y );
   y = ceil( -2.8 );
   printf( "The ceil of -2.8 is %f\n", y );
}
```

```Output
The floor of 2.8 is 2.000000
The floor of -2.8 is -3.000000
The ceil of 2.8 is 3.000000
The ceil of -2.8 is -2.000000
```

## <a name="see-also"></a>Viz také:

[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[ceil, ceilf, ceill](ceil-ceilf-ceill.md)<br/>
[round, roundf, roundl](round-roundf-roundl.md)<br/>
[fmod, fmodf](fmod-fmodf.md)<br/>
