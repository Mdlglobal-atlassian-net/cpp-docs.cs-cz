---
title: tgamma, tgammaf, tgammal
ms.date: 04/05/2018
api_name:
- tgamma
- tgammaf
- tgammal
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
- tgamma
- tgammaf
- tgammal
- math/tgamma
- math/tgammaf
- math/tgammal
helpviewer_keywords:
- tgamma function
- tgammaf function
- tgammal function
ms.assetid: f1bd2681-8af2-48a9-919d-5358fd068acd
ms.openlocfilehash: 02926fa49bbabeb9cf532f53cfa6e30a77805e70
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70946214"
---
# <a name="tgamma-tgammaf-tgammal"></a>tgamma, tgammaf, tgammal

Určuje funkci gamma zadané hodnoty.

## <a name="syntax"></a>Syntaxe

```C
double tgamma(
   double x
);

float tgamma(
   float x
); //C++ only

long double tgamma(
   long double x
); //C++ only

float tgammaf(
   float x
);

long double tgammal(
   long double x
);
```

### <a name="parameters"></a>Parametry

*x*<br/>
Hodnota, pro kterou má být nalezena hodnota gamma.

## <a name="return-value"></a>Návratová hodnota

V případě úspěchu vrátí hodnotu gamma *x*.

Pokud je velikost *x* pro datový typ příliš velká nebo příliš malá, může dojít k chybě rozsahu. Pokud *x* < = 0, může dojít k chybě domény nebo rozsahu.

|Problém|vrátit|
|-----------|------------|
|x = ± 0|± NEKONEČNO|
|x = záporné celé číslo|NaN|
|x = – nekonečno|NaN|
|x = + nekonečno|\+ NEKONEČNO|
|x = NaN|NaN|
|Chyba domény|NaN|
|Chyba pole|± HUGE_VAL, ± HUGE_VALF nebo ± HUGE_VALL|
|Chyba rozsahu přetečení|± HUGE_VAL, ± HUGE_VALF nebo ± HUGE_VALL|
|Chyba podtečení rozsahu|správná hodnota, po zaokrouhlení.|

Chyby jsou hlášeny podle zadání v [_matherr](matherr.md).

## <a name="remarks"></a>Poznámky

Vzhledem C++ k tomu, že umožňuje přetížení, můžete volat přetížení **tgamma –** , která přijímají a vracejí typ **float** a **Long** **Double** . V programu v jazyce C **tgamma –** vždycky přebírá a vrací **Double**.

Pokud je x přirozené číslo, vrátí tato funkce faktoriál (x-1).

## <a name="requirements"></a>Požadavky

|Funkce|Hlavička jazyka C|C++hlaviček|
|--------------|--------------|------------------|
|**tgamma –** , **tgammaf –** , **tgammal**|\<Math. h >|\<cmath >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Abecední seznam odkazů na funkce](crt-alphabetical-function-reference.md)<br/>
[lgamma, lgammaf, lgammal](lgamma-lgammaf-lgammal.md)<br/>
