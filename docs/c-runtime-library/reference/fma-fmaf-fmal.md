---
title: fma, fmaf, fmal
ms.date: 04/05/2018
api_name:
- fma
- fmaf
- fmal
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
ms.openlocfilehash: 4ddc4061e5a24ee3b5176aedc569d134d85e0002
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957109"
---
# <a name="fma-fmaf-fmal"></a>fma, fmaf, fmal

Vynásobí dvě hodnoty dohromady, přidá třetí hodnotu a pak výsledek zaokrouhlí, aniž by došlo ke ztrátě přesnosti kvůli zaokrouhlení.

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
První hodnota, která se má vynásobit.

*y*<br/>
Druhá hodnota, která se má vynásobit.

*z*<br/>
Hodnota, která má být přidána.

## <a name="return-value"></a>Návratová hodnota

Vrátí `(x * y) + z`. Návratová hodnota se pak zaokrouhluje pomocí aktuálního formátu zaokrouhlení.

V opačném případě může vracet jednu z následujících hodnot:

|Problém|vrátit|
|-----------|------------|
|*x* = nekonečno, *y* = 0 nebo<br /><br /> *x* = 0, *y* = nekonečno|NaN|
|*x* nebo *y* = přesné ± nekonečno, *z* = nekonečno s opačným znaménkem|NaN|
|*x* nebo *y* = NaN|NaN|
|NOT (*x* = 0, *y*= nekonečno) a *z* = NaN<br /><br /> Ne (*x*= nekonečno, *y*= 0) a *z* = NaN|NaN|
|Chyba rozsahu přetečení|± HUGE_VAL, ± HUGE_VALF nebo ± HUGE_VALL|
|Chyba podtečení rozsahu|správná hodnota, po zaokrouhlení.|

Chyby jsou hlášeny podle zadání v [_matherr](matherr.md).

## <a name="remarks"></a>Poznámky

Vzhledem C++ k tomu, že umožňuje přetížení, můžete volat přetížení **FMA** , která přijímají a vracejí typ **float** a **Long** **Double** . V programu v jazyce C **FMA** vždycky přebírá a vrací **Double**.

Tato funkce vypočítá hodnotu, jako by byla převedena na nekonečnou přesnost, a pak zaokrouhlí konečný výsledek.

## <a name="requirements"></a>Požadavky

|Funkce|Hlavička jazyka C|C++hlaviček|
|--------------|--------------|------------------|
|**FMA**, **fmaf –** , **fmal**|\<Math. h >|\<cmath >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Abecední seznam odkazů na funkce](crt-alphabetical-function-reference.md)<br/>
[remainder, remainderf, remainderl](remainder-remainderf-remainderl.md)<br/>
[remquo, remquof, remquol](remquo-remquof-remquol.md)<br/>
