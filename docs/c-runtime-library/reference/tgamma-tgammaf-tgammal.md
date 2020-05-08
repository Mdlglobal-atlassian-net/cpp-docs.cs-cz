---
title: tgamma, tgammaf, tgammal
ms.date: 4/2/2020
api_name:
- tgamma
- tgammaf
- tgammal
- _o_tgamma
- _o_tgammaf
- _o_tgammal
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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 6f3eb1bd791e645407b09a99a8c8e96025ca47e3
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82912234"
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

*znak*<br/>
Hodnota, pro kterou má být nalezena hodnota gamma.

## <a name="return-value"></a>Návratová hodnota

V případě úspěchu vrátí hodnotu gamma *x*.

Pokud je velikost *x* pro datový typ příliš velká nebo příliš malá, může dojít k chybě rozsahu. Pokud *x* <= 0, může dojít k chybě domény nebo rozsahu.

|Problém|Vrátit|
|-----------|------------|
|x = ± 0|± Nekonečno|
|x = záporné celé číslo|Není číslo|
|x = – nekonečno|Není číslo|
|x = + nekonečno|+ Nekonečno|
|x = NaN|Není číslo|
|Chyba domény|Není číslo|
|Chyba pole|± HUGE_VAL, ± HUGE_VALF nebo ± HUGE_VALL|
|Chyba rozsahu přetečení|± HUGE_VAL, ± HUGE_VALF nebo ± HUGE_VALL|
|Chyba podtečení rozsahu|správná hodnota, po zaokrouhlení.|

Chyby jsou hlášeny tak, jak jsou uvedeny v [_matherr](matherr.md).

## <a name="remarks"></a>Poznámky

Vzhledem k tomu, že jazyk C++ umožňuje přetížení, můžete volat přetížení **tgamma –** , která přijímají a vracejí typ **float** a **Long** **Double** . V programu v jazyce C **tgamma –** vždycky přebírá a vrací **Double**.

Pokud je x přirozené číslo, vrátí tato funkce faktoriál (x-1).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Funkce|Hlavička jazyka C|Hlavička C++|
|--------------|--------------|------------------|
|**tgamma –**, **tgammaf –**, **tgammal**|\<Math. h>|\<cmath>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Abecední seznam odkazů na funkce](crt-alphabetical-function-reference.md)<br/>
[lgamma, lgammaf, lgammal](lgamma-lgammaf-lgammal.md)<br/>
