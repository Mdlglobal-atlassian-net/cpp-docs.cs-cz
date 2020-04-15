---
title: rint, rintf, rintl
ms.date: 4/2/2020
api_name:
- rintf
- rintl
- rint
- _o_rint
- _o_rintf
- _o_rintl
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
- rintf
- rintl
- rint
helpviewer_keywords:
- rintf function
- rint function
- rintl function
ms.assetid: 312ae3e6-278c-459a-9393-11b8f87d9184
ms.openlocfilehash: 6489b7ebed5246738fb660dffd07a0b8f8ed9743
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81332764"
---
# <a name="rint-rintf-rintl"></a>rint, rintf, rintl

Zaokrouhlí hodnotu s plovoucí desetinnou desetinnou hodnotou na nejbližší celé číslo ve formátu s plovoucí desetinnou desetinnou desetinnou desetinnou táslužbou.

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

*X*<br/>
Hodnota s plovoucí desetinnou tácem k zaokrouhlení.

## <a name="return-value"></a>Návratová hodnota

Funkce **rint** vrátí hodnotu s plovoucí desetinnou hodnotou, která představuje nejbližší celé číslo na *x*. Hodnoty do poloviny jsou zaokrouhleny podle aktuálního nastavení režimu zaokrouhlení s plovoucí desetinnou čárkou, stejně jako funkce **nearint.** Na rozdíl od **funkcí nearint** funkce **rint** funkce může vyvolat **výjimku FE_INEXACT** plovoucí desetinnou desetinnou, pokud výsledek se liší v hodnotě od argumentu. Neexistuje žádná chyba vrátit.

|Vstup|Výjimka SEH|**_matherr** Výjimka|
|-----------|-------------------|--------------------------|
|± ∞, QNAN, IND|Žádná|Žádná|
|Denormální jevy|EXCEPTION_FLT_UNDERFLOW|Žádná|

## <a name="remarks"></a>Poznámky

Vzhledem k tomu, že C++ umožňuje přetížení, můžete volat přetížení **rint,** které trvat a vrátit **float** a **dlouhé** **dvojité** hodnoty. V programu C **rint** vždy trvá a vrací **double**.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Funkce|Hlavička C|Hlavička C++|
|--------------|--------------|------------------|
|**rint**, **rintf**, **rintl**|\<math.h>|\<cmath>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

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

[Podpora s plovoucí desetinnou tálicí](../../c-runtime-library/floating-point-support.md)<br/>
[ceil, ceilf, ceill](ceil-ceilf-ceill.md)<br/>
[floor, floorf, floorl](floor-floorf-floorl.md)<br/>
[fmod, fmodf](fmod-fmodf.md)<br/>
[lrint, lrintf, lrintl, llrint, llrintf, llrintl](lrint-lrintf-lrintl-llrint-llrintf-llrintl.md)<br/>
[lround, lroundf, lroundl, llround, llroundf, llroundl](lround-lroundf-lroundl-llround-llroundf-llroundl.md)<br/>
[nearbyint, nearbyintf, nearbyintl](nearbyint-nearbyintf-nearbyintl1.md)<br/>
[rint](rint-rintf-rintl.md)<br/>
