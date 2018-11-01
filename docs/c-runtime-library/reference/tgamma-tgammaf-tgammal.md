---
title: tgamma, tgammaf, tgammal
ms.date: 04/05/2018
apiname:
- tgamma
- tgammaf
- tgammal
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
ms.openlocfilehash: 6cfe455b0e9e83cd5283d36fed33ca168bc97d0a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50570661"
---
# <a name="tgamma-tgammaf-tgammal"></a>tgamma, tgammaf, tgammal

Určuje funkce gamma zadanou hodnotu.

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
Hodnota k vyhledání gama z.

## <a name="return-value"></a>Návratová hodnota

Pokud je úspěšná, vrátí funkce gamma z *x*.

Rozsah chybě může dojít, pokud velikost *x* je příliš velký či příliš malý datového typu. Chyba domény nebo rozsah chybě může dojít, pokud *x* < = 0.

|Problém|Vrátí|
|-----------|------------|
|x = ±0|±INFINITY|
|x = záporné celé číslo|NaN|
|x = - NEKONEČNO|NaN|
|x =, + NEKONEČNO|+ NEKONEČNO|
|x = NaN|NaN|
|chyby domény|NaN|
|Chyba pole|±HUGE_VAL, ±HUGE_VALF nebo ±HUGE_VALL|
|Chyba přetečení rozsahu|±HUGE_VAL, ±HUGE_VALF nebo ±HUGE_VALL|
|Chyba podtečení rozsahu|správnou hodnotu, po zaokrouhlení.|

Jsou hlášeny chyby uvedené v [_matherr](matherr.md).

## <a name="remarks"></a>Poznámky

Protože jazyk C++ umožňuje přetížení, můžete volat přetížení **tgamma –** , která používají a vrací **float** a **dlouhé** **double** typy. V programu jazyka C **tgamma –** vždy převezme a vrátí **double**.

Pokud x je přirozené číslo, tato funkce Vrátí faktoriál čísla (x-1).

## <a name="requirements"></a>Požadavky

|Funkce|Záhlaví C|Hlaviček jazyka C++|
|--------------|--------------|------------------|
|**tgamma –**, **tgammaf –**, **tgammal**|\<Math.h >|\<cmath >|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Abecední seznam odkazů na funkce](crt-alphabetical-function-reference.md)<br/>
[lgamma, lgammaf, lgammal](lgamma-lgammaf-lgammal.md)<br/>
