---
title: fdim, fdimf, fdiml
ms.date: 04/05/2018
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
helpviewer_keywords:
- fdim function
- fdimf function
- fdiml function
ms.assetid: 2d4ac639-51e9-462d-84ab-fb03b06971a0
ms.openlocfilehash: d8cea831e333ebcd9677d830641c60e460ba5ed4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50515086"
---
# <a name="fdim-fdimf-fdiml"></a>fdim, fdimf, fdiml

Určuje pozitivní rozdíl mezi hodnotami prvního a druhého.

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

Vrátí pozitivní rozdíl mezi *x* a *y*:

|Návratová hodnota|Scénář|
|------------------|--------------|
|x-y|if x > y|
|0|Pokud x < = y|

V opačném případě může vracet instanci jednoho z následujících chyb:

|Problém|Vrátí|
|-----------|------------|
|Chyba přetečení rozsahu|+ HUGE_VAL + HUGE_VALF, nebo + HUGE_VALL|
|Chyba podtečení rozsahu|správnou hodnotu (po zaokrouhlení)|
|*x* nebo *y* NaN|NaN|

Jsou hlášeny chyby uvedené v [_matherr](matherr.md).

## <a name="remarks"></a>Poznámky

Protože jazyk C++ umožňuje přetížení, můžete volat přetížení **fdim –** , která používají a vrací **float** a **dlouhé** **double** typy. V programu jazyka C **fdim –** vždy převezme a vrátí **double**.

S výjimkou zpracování NaN, tato funkce je ekvivalentní `fmax(x - y, 0)`.

## <a name="requirements"></a>Požadavky

|Funkce|Záhlaví C|Hlaviček jazyka C++|
|--------------|--------------|------------------|
|**fdim –**, **fdimf –**, **fdiml**|\<Math.h >|\<cmath >|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Abecední seznam odkazů na funkce](crt-alphabetical-function-reference.md)<br/>
[fmax, fmaxf, fmaxl](fmax-fmaxf-fmaxl.md)<br/>
[abs, labs, llabs, _abs64](abs-labs-llabs-abs64.md)<br/>
