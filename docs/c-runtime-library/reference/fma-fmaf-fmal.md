---
title: FMA – fmaf –, fmal | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: ''
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- fma function
- fmaf function
- fmal function
ms.assetid: 584a6037-da1e-4e86-9f0c-97aae86de0c0
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e4530a816617e564bf1d98766cf0861dd5fa7d08
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2018
---
# <a name="fma-fmaf-fmal"></a>fma, fmaf, fmal

Vynásobí dvě hodnoty společně, přidá třetí hodnota a pak zaokrouhlí výsledek, aniž by došlo ke ztrátě všech přesnost kvůli zprostředkující zaokrouhlení.

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
První hodnota k násobení.

*y*<br/>
Druhá hodnota mají vynásobit.

*z*<br/>
Hodnota k přidání.

## <a name="return-value"></a>Návratová hodnota

Vrátí `(x * y) + z`. Návratová hodnota je zaokrouhlí formátu aktuální zaokrouhlení.

Jinak může vrátit jednu z následujících hodnot:

|Problém|Vrátí|
|-----------|------------|
|*x* = INFINITY, *y* = 0 nebo<br /><br /> *x* = 0, *y* = INFINITY|NaN|
|*x* nebo *y* = přesný rozmezí INFINITY, *z* = INFINITY s opačným znaménkem|NaN|
|*x* nebo *y* = NaN.|NaN|
|Ne (*x* = 0, *y*= neomezené) a *z* = NaN.<br /><br /> Ne (*x*= neomezené, *y*= 0) a *z* = NaN.|NaN|
|Rozsah chybu přetečení|±HUGE_VAL, ±HUGE_VALF nebo ±HUGE_VALL|
|Podtečení rozsah chyby|správnou hodnotu po zaokrouhlení.|

Vznikly chyby uvedené v [_matherr –](matherr.md).

## <a name="remarks"></a>Poznámky

Protože C++ umožňuje, aby přetížení, můžete volat přetížení **FMA –** , přijmout a vrátit **float** a **dlouho** **dvojité** typy. V programu C **FMA –** vždy provede a vrátí **dvojité**.

Tato funkce vypočítá hodnotu, jako kdyby byly provedeny na neomezenou přesnost a pak zaokrouhlí konečný výsledek.

## <a name="requirements"></a>Požadavky

|Funkce|Hlavička C|Hlavička C++|
|--------------|--------------|------------------|
|**FMA –**, **fmaf –**, **fmal**|\<Math.h >|\<cmath – >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Abecední seznam odkazů na funkce](crt-alphabetical-function-reference.md)<br/>
[remainder, remainderf, remainderl](remainder-remainderf-remainderl.md)<br/>
[remquo, remquof, remquol](remquo-remquof-remquol.md)<br/>
