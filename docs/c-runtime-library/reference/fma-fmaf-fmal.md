---
title: fma, fmaf, fmal
ms.date: 4/2/2020
api_name:
- fma
- fmaf
- fmal
- _o_fma
- _o_fmaf
- _o_fmal
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
ms.openlocfilehash: 993ca4d57202b3789929161a964b3e41d48fd98f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81346573"
---
# <a name="fma-fmaf-fmal"></a>fma, fmaf, fmal

Vynásobí dvě hodnoty dohromady, přidá třetí hodnotu a pak zaokrouhlí výsledek, aniž by došlo ke ztrátě přesnosti z důvodu zaokrouhlení zprostředkovatele.

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

*X*<br/>
První hodnota násobit.

*Y*<br/>
Druhá hodnota násobit.

*Z*<br/>
Hodnota přidat.

## <a name="return-value"></a>Návratová hodnota

Vrací objekt `(x * y) + z`. Vrácená hodnota se pak zaokrouhlí pomocí aktuálního formátu zaokrouhlení.

V opačném případě může vrátit jednu z následujících hodnot:

|Problém|Vrátit|
|-----------|------------|
|*x* = INFINITY, *y* = 0 nebo<br /><br /> *x* = 0, *y* = NEKONEČNO|Není číslo|
|*x* nebo *y* = přesné ± INFINITY, *z* = INFINITY s opačným znaménkem|Není číslo|
|*x* nebo *y* = NaN|Není číslo|
|ne (*x* = 0, *y*= neurčitý) a *z* = NaN<br /><br /> ne (*x*= neurčitý, *y*= 0) a *z* = NaN|Není číslo|
|Chyba rozsahu přetečení|±HUGE_VAL, ±HUGE_VALF nebo ±HUGE_VALL|
|Chyba rozsahu podtečení|správnou hodnotu po zaokrouhlení.|

Chyby jsou hlášeny podle _matherr [.](matherr.md)

## <a name="remarks"></a>Poznámky

Vzhledem k tomu, že C++ umožňuje přetížení, můžete volat přetížení **fma,** které take a return **float** a **dlouhé** **dvojité** typy. V programu C **fma** vždy trvá a vrací **double**.

Tato funkce vypočítá hodnotu, jako by byla přijata na nekonečnou přesnost a pak zaokrouhlí konečný výsledek.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Funkce|Hlavička C|Hlavička C++|
|--------------|--------------|------------------|
|**fma**, **fmaf**, **fmal**|\<math.h>|\<cmath>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Abecední seznam odkazů na funkce](crt-alphabetical-function-reference.md)<br/>
[remainder, remainderf, remainderl](remainder-remainderf-remainderl.md)<br/>
[remquo, remquof, remquol](remquo-remquof-remquol.md)<br/>
