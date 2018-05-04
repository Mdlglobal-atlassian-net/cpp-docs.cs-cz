---
title: fdim – fdimf –, fdiml | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
apiname:
- fdim
- fdimf
- fdiml
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
- fdim
- fdimf
- fdiml
- math/fdim
- math/fdimf
- math/fdiml
dev_langs:
- C++
helpviewer_keywords:
- fdim function
- fdimf function
- fdiml function
ms.assetid: 2d4ac639-51e9-462d-84ab-fb03b06971a0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cdcad02c94717715fdda1b3a9d2e820fc16d0bf4
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="fdim-fdimf-fdiml"></a>fdim, fdimf, fdiml

Určuje kladné rozdíl mezi hodnotami prvním a druhém.

## <a name="syntax"></a>Syntaxe

```C
double fdim(
   double x,
   double y
);

float fdim(
   float x,
   float y
); //C++ only

long double fdim(
   long double x,
   long double y
); //C++ only

float fdimf(
   float x,
   float y
);

long double fdiml(
   long double x,
   long double y
);

```

### <a name="parameters"></a>Parametry

*x*<br/>
První hodnota.

*y*<br/>
Druhá hodnota.

## <a name="return-value"></a>Návratová hodnota

Vrátí kladné rozdíl mezi *x* a *y*:

|Návratová hodnota|Scénář|
|------------------|--------------|
|x-y|if x > y|
|0|Pokud x < = y|

Jinak může vrátit jednu z těchto chyb:

|Problém|Vrátí|
|-----------|------------|
|Rozsah chybu přetečení|+ Huge_val – + HUGE_VALF, nebo + HUGE_VALL|
|Podtečení rozsah chyby|správnou hodnotu (po zaokrouhlení)|
|*x* nebo *y* je NaN.|NaN|

Vznikly chyby uvedené v [_matherr –](matherr.md).

## <a name="remarks"></a>Poznámky

Protože C++ umožňuje, aby přetížení, můžete volat přetížení **fdim –** , přijmout a vrátit **float** a **dlouho** **dvojité** typy. V programu C **fdim –** vždy provede a vrátí **dvojité**.

S výjimkou NaN zpracování, tato funkce je ekvivalentní volání `fmax(x - y, 0)`.

## <a name="requirements"></a>Požadavky

|Funkce|Hlavička C|Hlavička C++|
|--------------|--------------|------------------|
|**fdim –**, **fdimf –**, **fdiml**|\<Math.h >|\<cmath – >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Abecední seznam odkazů na funkce](crt-alphabetical-function-reference.md)<br/>
[fmax, fmaxf, fmaxl](fmax-fmaxf-fmaxl.md)<br/>
[abs, labs, llabs, _abs64](abs-labs-llabs-abs64.md)<br/>
