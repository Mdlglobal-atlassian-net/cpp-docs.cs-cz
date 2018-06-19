---
title: floorf – Floor, floorl – | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- floorf
- floorl
- floor
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
- floor
- floorl
- _floorl
- floorf
dev_langs:
- C++
helpviewer_keywords:
- floor function
- floorf function
- calculating floors of values
- floorl function
ms.assetid: e9955f70-d659-414f-8050-132e13c8ff36
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 83795c9388b3889f99c9283cbffd33755d63fcd8
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32399420"
---
# <a name="floor-floorf-floorl"></a>floor, floorf, floorl

Vypočítá podlaží hodnoty.

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

**Podlaží** funkce vrátí hodnotu s plovoucí desetinnou čárkou, která představuje největší číslo typu integer, která je menší než nebo rovno *x*. Neexistuje žádný návratový chyby.

|Vstup|Výjimka SEH|Matherr – výjimka|
|-----------|-------------------|-----------------------|
|ROZMEZÍ QNAN, IND|žádná|_DOMAIN –|

**Floor** má implementace, která používá Streaming SIMD Extensions 2 (SSE2). Informace a omezení o pomocí implementace SSE2 najdete v tématu [_set_sse2_enable –](set-sse2-enable.md).

## <a name="remarks"></a>Poznámky

C++ umožňuje přetížení, takže můžete volat přetížení **podlaží** , přijmout a vrátit **float** a **dlouho** **dvojité** hodnoty. V programu C **podlaží** vždy provede a vrátí **dvojité**.

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**Floor**, **floorf –**, **floorl –**|\<Math.h >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Viz také

[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[ceil, ceilf, ceill](ceil-ceilf-ceill.md)<br/>
[round, roundf, roundl](round-roundf-roundl.md)<br/>
[fmod, fmodf](fmod-fmodf.md)<br/>
