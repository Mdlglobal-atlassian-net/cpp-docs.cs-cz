---
title: tisknout, rintf, rintl | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- rintf
- rintl
- rint
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
- rintf
- rintl
- rint
dev_langs:
- C++
helpviewer_keywords:
- rintf function
- rint function
- rintl function
ms.assetid: 312ae3e6-278c-459a-9393-11b8f87d9184
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 784a540982c41ba7aa144559d3846746b59481f7
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32407285"
---
# <a name="rint-rintf-rintl"></a>rint, rintf, rintl

Zaokrouhlí na nejbližší celé číslo s plovoucí desetinnou čárkou formát hodnotu s plovoucí desetinnou čárkou.

## <a name="syntax"></a>Syntaxe

```C
double rint( double x );
float rintf( float x );
long double rintl( long double x );
```

```cpp
float rint( float x );  // C++ only
long double rint( long double x );  // C++ only
```

### <a name="parameters"></a>Parametry

*x*<br/>
Hodnota s plovoucí desetinnou čárkou má být zaokrouhleno.

## <a name="return-value"></a>Návratová hodnota

**Tisknout** funkce vrátí hodnotu s plovoucí desetinnou čárkou, která představuje na nejbližší celé číslo na *x*. Uprostřed hodnoty jsou zaokrouhleny podle aktuálního nastavení režimu zaokrouhlení s plovoucí desetinnou čárkou, stejně jako **nearbyint –** funkce. Na rozdíl od **nearbyint –** funkce, **tisknout** může vyvolat funkce **FE_INEXACT** výjimek plovoucí desetinné čárky, pokud výsledek se liší v hodnotě v argumentu. Neexistuje žádný návratový chyby.

|Vstup|Výjimka SEH|**_matherr –** výjimky|
|-----------|-------------------|--------------------------|
|ROZMEZÍ ∞, QNAN, IND|žádná|žádná|
|Denormals|EXCEPTION_FLT_UNDERFLOW|žádná|

## <a name="remarks"></a>Poznámky

Protože C++ umožňuje, aby přetížení, můžete volat přetížení **tisknout** , přijmout a vrátit **float** a **dlouho** **dvojité** hodnoty. V programu C **tisknout** vždy provede a vrátí **dvojité**.

## <a name="requirements"></a>Požadavky

|Funkce|Hlavička C|Hlavička C++|
|--------------|--------------|------------------|
|**Tisknout**, **rintf**, **rintl**|\<Math.h >|\<cmath – >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_rint.c
// Build with: cl /W3 /Tc crt_rint.c
// This example displays the rounded results of
// the floating-point values 2.499999, -2.499999,
// 2.8, -2.8, 2.5 and -2.5.

#include <math.h>
#include <stdio.h>

int main( void )
{
   double x = 2.499999;
   float y = 2.8f;
   long double z = 2.5;

   printf("rint(%f) is %.0f\n", x, rint (x));
   printf("rint(%f) is %.0f\n", -x, rint (-x));
   printf("rintf(%f) is %.0f\n", y, rintf(y));
   printf("rintf(%f) is %.0f\n", -y, rintf(-y));
   printf("rintl(%Lf) is %.0Lf\n", z, rintl(z));
   printf("rintl(%Lf) is %.0Lf\n", -z, rintl(-z));
}
```

```Output
rint(2.499999) is 2
rint(-2.499999) is -2
rintf(2.800000) is 3
rintf(-2.800000) is -3
rintl(2.500000) is 3
rintl(-2.500000) is -3
```

## <a name="see-also"></a>Viz také

[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[ceil, ceilf, ceill](ceil-ceilf-ceill.md)<br/>
[floor, floorf, floorl](floor-floorf-floorl.md)<br/>
[fmod, fmodf](fmod-fmodf.md)<br/>
[lrint, lrintf, lrintl, llrint, llrintf, llrintl](lrint-lrintf-lrintl-llrint-llrintf-llrintl.md)<br/>
[lround, lroundf, lroundl, llround, llroundf, llroundl](lround-lroundf-lroundl-llround-llroundf-llroundl.md)<br/>
[nearbyint – nearbyintf –, nearbyintl](nearbyint-nearbyintf-nearbyintl1.md)<br/>
[Tisknout](rint-rintf-rintl.md)<br/>