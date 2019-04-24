---
title: fma, fmaf, fmal
ms.date: 04/05/2018
apiname:
- fma
- fmaf
- fmal
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
- fma
- fmaf
- fmal
- math/fma
- math/fmaf
- math/fmal
helpviewer_keywords:
- fma function
- fmaf function
- fmal function
ms.assetid: 584a6037-da1e-4e86-9f0c-97aae86de0c0
ms.openlocfilehash: f96592e245e443bae2f3334da51cae5572753708
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62333492"
---
# <a name="fma-fmaf-fmal"></a>fma, fmaf, fmal

Vynásobí dvě hodnoty společně, přidá třetí hodnotu a potom zaokrouhlí výsledek, aniž by ztratily všechny přesnost kvůli zprostředkující zaokrouhlení.

## <a name="syntax"></a>Syntaxe

```C
double fma(
   double x,
   double y,
   double z
);

float fma(
   float  x,
   float  y,
   float z
); //C++ only

long double fma(
   long double  x,
   long double  y,
   long double z
); //C++ only

float fmaf(
   float  x,
   float  y,
   float z
);

long double fmal(
   long double  x,
   long double  y,
   long double z
);
```

### <a name="parameters"></a>Parametry

*x*<br/>
První hodnota pro násobení.

*y*<br/>
Druhá hodnota pro násobení.

*z*<br/>
Hodnota k přidání.

## <a name="return-value"></a>Návratová hodnota

Vrátí `(x * y) + z`. Návratová hodnota se zaokrouhlí formátu aktuální zaokrouhlení.

V opačném případě může vracet instanci jednoho z následujících hodnot:

|Problém|Vrátí|
|-----------|------------|
|*x* = NEKONEČNO, *y* = 0 nebo<br /><br /> *x* = 0, *y* = NEKONEČNO|NaN|
|*x* nebo *y* = přesné rozmezí NEKONEČNO, *z* = NEKONEČNO s opačným znaménkem|NaN|
|*x* nebo *y* = NaN|NaN|
|Ne (*x* = 0, *y*= nekonečno) a *z* = NaN<br /><br /> Ne (*x*= nekonečno, *y*= 0) a *z* = NaN|NaN|
|Chyba přetečení rozsahu|±HUGE_VAL, ±HUGE_VALF nebo ±HUGE_VALL|
|Chyba podtečení rozsahu|správnou hodnotu, po zaokrouhlení.|

Jsou hlášeny chyby uvedené v [_matherr](matherr.md).

## <a name="remarks"></a>Poznámky

Protože jazyk C++ umožňuje přetížení, můžete volat přetížení **fma** , která používají a vrací **float** a **dlouhé** **double** typy. V programu jazyka C **fma** vždy převezme a vrátí **double**.

Tato funkce vypočítá hodnotu jako by byly provedeny s nekonečnou přesností a zaokrouhlí pak konečný výsledek.

## <a name="requirements"></a>Požadavky

|Funkce|Záhlaví C|Hlaviček jazyka C++|
|--------------|--------------|------------------|
|**fma**, **fmaf**, **fmal**|\<math.h>|\<cmath>|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Abecední seznam odkazů na funkce](crt-alphabetical-function-reference.md)<br/>
[remainder, remainderf, remainderl](remainder-remainderf-remainderl.md)<br/>
[remquo, remquof, remquol](remquo-remquof-remquol.md)<br/>
