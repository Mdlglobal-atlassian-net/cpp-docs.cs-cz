---
title: fdim, fdimf, fdiml
ms.date: 04/05/2018
api_name:
- fdim
- fdimf
- fdiml
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
ms.openlocfilehash: 74935f724b678b08e39604d9916c7c5de5925aee
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70941290"
---
# <a name="fdim-fdimf-fdiml"></a>fdim, fdimf, fdiml

Určuje kladný rozdíl mezi první a druhou hodnotou.

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

Vrátí kladný rozdíl mezi *x* a *y*:

|Návratová hodnota|Scénář|
|------------------|--------------|
|x-y|if x > y|
|0|Pokud x < = y|

V opačném případě může vrátit jednu z následujících chyb:

|Problém|vrátit|
|-----------|------------|
|Chyba rozsahu přetečení|\+ HUGE_VAL, + HUGE_VALF nebo + HUGE_VALL|
|Chyba podtečení rozsahu|správná hodnota (po zaokrouhlení)|
|*x* nebo *y* je NaN.|NaN|

Chyby jsou hlášeny podle zadání v [_matherr](matherr.md).

## <a name="remarks"></a>Poznámky

Vzhledem C++ k tomu, že umožňuje přetížení, můžete volat přetížení **fdim –** , která přijímají a vracejí typ **float** a **Long** **Double** . V programu v jazyce C **fdim –** vždycky přebírá a vrací **Double**.

S výjimkou manipulace s NaN je tato funkce ekvivalentní `fmax(x - y, 0)`.

## <a name="requirements"></a>Požadavky

|Funkce|Hlavička jazyka C|C++hlaviček|
|--------------|--------------|------------------|
|**fdim –** , **fdimf –** , **fdiml**|\<Math. h >|\<cmath >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Abecední seznam odkazů na funkce](crt-alphabetical-function-reference.md)<br/>
[fmax, fmaxf, fmaxl](fmax-fmaxf-fmaxl.md)<br/>
[abs, labs, llabs, _abs64](abs-labs-llabs-abs64.md)<br/>
