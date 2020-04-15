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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: d7e27e8b818a16cb0c18f58e2f40c0090dd13ecf
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81362509"
---
# <a name="tgamma-tgammaf-tgammal"></a>tgamma, tgammaf, tgammal

Určuje funkci gama zadané hodnoty.

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

*X*<br/>
Hodnota najít gama.

## <a name="return-value"></a>Návratová hodnota

Pokud je úspěšná, vrátí gama *x*.

Pokud je velikost *x* pro datový typ příliš velká nebo příliš malá, může dojít k chybě rozsahu. Pokud *x* <= 0, může dojít k chybě domény nebo rozsahu.

|Problém|Vrátit|
|-----------|------------|
|x = ±0|±NEKONEČNO|
|x = záporné celé číslo|Není číslo|
|x = -NEKONEČNO|Není číslo|
|x = +INFINITY|+NEKONEČNO|
|x = NaN|Není číslo|
|chyba domény|Není číslo|
|pole chyba|±HUGE_VAL, ±HUGE_VALF nebo ±HUGE_VALL|
|chyba rozsahu přetečení|±HUGE_VAL, ±HUGE_VALF nebo ±HUGE_VALL|
|chyba rozsahu podtoje|správnou hodnotu po zaokrouhlení.|

Chyby jsou hlášeny podle _matherr [.](matherr.md)

## <a name="remarks"></a>Poznámky

Vzhledem k tomu, že C++ umožňuje přetížení, můžete volat přetížení **tgamma,** které táhnou a vrátí **float** a **dlouhé** **dvojité** typy. V programu C **tgamma** vždy trvá a vrací **double**.

Pokud x je přirozené číslo, tato funkce vrátí faktoriál (x-1).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Funkce|Hlavička C|Hlavička C++|
|--------------|--------------|------------------|
|**tgamma**, **tgammaf**, **tgammální**|\<math.h>|\<cmath>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Abecední seznam odkazů na funkce](crt-alphabetical-function-reference.md)<br/>
[lgamma, lgammaf, lgammal](lgamma-lgammaf-lgammal.md)<br/>
