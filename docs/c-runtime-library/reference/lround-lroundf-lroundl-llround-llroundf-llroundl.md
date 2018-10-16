---
title: lround – lroundf –, lroundl –, llround –, llroundf –, llroundl – | Dokumentace Microsoftu
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- llround
- llroundf
- llroundl
- lroundf
- lround
- lroundl
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
- lround
- lroundl
- llroundl
- llround
- lroundf
- llroundf
dev_langs:
- C++
helpviewer_keywords:
- lround function
- llroundl function
- llround function
- lroundf function
- llroundf function
- lroundl function
ms.assetid: cfb88a35-54c6-469f-85af-f7d695dcfdd8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4ea24e45c26abe418023d4f065117928bb17ae2b
ms.sourcegitcommit: 3f3f1d687e109b63399e14e2c8f4404787bdfae7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2018
ms.locfileid: "49336532"
---
# <a name="lround-lroundf-lroundl-llround-llroundf-llroundl"></a>lround, lroundf, lroundl, llround, llroundf, llroundl

Zaokrouhlí hodnotu s plovoucí desetinnou čárkou na nejbližší celé číslo.

## <a name="syntax"></a>Syntaxe

```C
long lround(
   double x
);
long lround(
   float x
);  // C++ only
long lround(
   long double x
);  // C++ only
long lroundf(
   float x
);
long lroundl(
   long double x
);
long long llround(
   double x
);
long long llround(
   float x
);  // C++ only
long long llround(
   long double x
);  // C++ only
long long llroundf(
   float x
);
long long llroundl(
   long double x
);
```

### <a name="parameters"></a>Parametry

*x*<br/>
Hodnota s plovoucí desetinnou čárkou k zaokrouhlení.

## <a name="return-value"></a>Návratová hodnota

**Lround –** a **llround –** funkce vrátí nejbližší **dlouhé** nebo **dlouhé** **dlouhé** celé číslo *x*. Středové hodnoty jsou zaokrouhleny směrem od nuly bez ohledu na nastavení režimu zaokrouhlení s plovoucí desetinnou čárkou. Není vrácena žádná chyba.

|Vstup|Výjimka SEH|Výjimka Matherr|
|-----------|-------------------|-----------------------|
|ROZMEZÍ **QNAN**, **AJÍT**|žádná|**_DOMÉNA**|

## <a name="remarks"></a>Poznámky

Protože jazyk C++ umožňuje přetížení, můžete volat přetížení **lround –** nebo **llround –** , která používají a vrací **float** a **dlouhé** **double** hodnoty. V programu jazyka C **lround –** a **llround –** vždy převezme a vrátí **double**.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**lround –**, **lroundf –**, **lroundl –**, **llround –**, **llroundf –**, **llroundl –**|\<Math.h >|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_lround.c
// Build with: cl /W4 /Tc crt_lround.c
// This example displays the rounded results of
// the floating-point values 2.499999, -2.499999,
// 2.8, -2.8, 3.5 and -3.5.

#include <math.h>
#include <stdio.h>

int main( void )
{
   double x = 2.499999;
   float y = 2.8f;
   long double z = 3.5L;

   printf("lround(%f) is %d\n", x, lround(x));
   printf("lround(%f) is %d\n", -x, lround(-x));
   printf("lroundf(%f) is %d\n", y, lroundf(y));
   printf("lroundf(%f) is %d\n", -y, lroundf(-y));
   printf("lroundl(%Lf) is %d\n", z, lroundl(z));
   printf("lroundl(%Lf) is %d\n", -z, lroundl(-z));
}
```

```Output
lround(2.499999) is 2
lround(-2.499999) is -2
lroundf(2.800000) is 3
lroundf(-2.800000) is -3
lroundl(3.500000) is 4
lroundl(-3.500000) is -4
```

## <a name="see-also"></a>Viz také:

[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[ceil, ceilf, ceill](ceil-ceilf-ceill.md)<br/>
[floor, floorf, floorl](floor-floorf-floorl.md)<br/>
[fmod, fmodf](fmod-fmodf.md)<br/>
[lrint, lrintf, lrintl, llrint, llrintf, llrintl](lrint-lrintf-lrintl-llrint-llrintf-llrintl.md)<br/>
[round, roundf, roundl](round-roundf-roundl.md)<br/>
[nearbyint – nearbyintf –, nearbyintl](nearbyint-nearbyintf-nearbyintl1.md)<br/>
[rint, rintf, rintl](rint-rintf-rintl.md)<br/>
