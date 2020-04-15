---
title: lgamma, lgammaf, lgammal
ms.date: 4/2/2020
api_name:
- lgamma
- lgammaf
- lgammal
- _o_lgamma
- _o_lgammaf
- _o_lgammal
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
- lgamma
- lgammaf
- lgammal
- math/lgamma
- math/lgammaf
- math/lgammal
helpviewer_keywords:
- lgamma function
- lgammal function
- lgammaf function
ms.assetid: 6e326c58-7077-481a-a329-c82ae56ae9e6
ms.openlocfilehash: e2bdfbeac7b995be0b589156437a3ded39114adf
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81342165"
---
# <a name="lgamma-lgammaf-lgammal"></a>lgamma, lgammaf, lgammal

Určuje přirozený logaritmus absolutní hodnoty funkce gama zadané hodnoty.

## <a name="syntax"></a>Syntaxe

```C
double lgamma( double x );
float lgammaf( float x );
long double lgammal( long double x );
```

```cpp
float lgamma( float x ); //C++ only
long double lgamma( long double x ); //C++ only
```

### <a name="parameters"></a>Parametry

*X*<br/>
Hodnota pro výpočet.

## <a name="return-value"></a>Návratová hodnota

V případě úspěchu vraťte přirozený logaritmus absolutní hodnoty funkce gama *x*.

|Problém|Vrátit|
|-----------|------------|
|*x* = NaN|Není číslo|
|*x* = ±0|+NEKONEČNO|
|*x*= záporné celé číslo|+NEKONEČNO|
|±NEKONEČNO|+NEKONEČNO|
|pole chyba|+HUGE_VAL, +HUGE_VALF nebo +HUGE_VALL|
|chyba rozsahu přetečení|±HUGE_VAL, ±HUGE_VALF nebo ±HUGE_VALL|

Chyby jsou hlášeny podle _matherr [.](matherr.md)

## <a name="remarks"></a>Poznámky

Protože C++ umožňuje přetížení, můžete volat přetížení **lgamma,** které take a return **float** a **long** **double** typy. V programu C **lgamma** vždy trvá a vrací **double**.

Pokud x je racionální číslo, tato funkce vrátí logaritmus faktoriálu (x - 1).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Funkce|Hlavička C|Hlavička C++|
|--------------|--------------|------------------|
|**lgamma**, **lgammaf**, **lgammální**|\<math.h>|\<cmath>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Abecední seznam odkazů na funkce](crt-alphabetical-function-reference.md)<br/>
[tgamma, tgammaf, tgammal](tgamma-tgammaf-tgammal.md)<br/>
