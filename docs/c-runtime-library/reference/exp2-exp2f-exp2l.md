---
title: exp2, exp2f, exp2l
ms.date: 4/2/2020
api_name:
- exp2
- exp2f
- exp2l
- _o_exp2
- _o_exp2f
- _o_exp2l
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
- exp2
- math/exp2
- exp2f
- math/exp2f
- exp2l
- math/exp2l
helpviewer_keywords:
- exp2 function
- exp2f function
- exp2l function
ms.assetid: 526e3e10-201a-4610-a886-533f44ece344
ms.openlocfilehash: a5df1a216b4565f013a4c42b4ef4369b5b7f9b04
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81347586"
---
# <a name="exp2-exp2f-exp2l"></a>exp2, exp2f, exp2l

Vypočítá 2 aktivována na zadanou hodnotu.

## <a name="syntax"></a>Syntaxe

```C
double exp2(
   double x
);

float exp2(
   float x
);  // C++ only

long double exp2(
   long double x
); // C++ only

float exp2f(
   float x
);

long double exp2l(
   long double x
);
```

### <a name="parameters"></a>Parametry

*X*<br/>
Hodnota exponentu.

## <a name="return-value"></a>Návratová hodnota

Pokud je úspěšná, vrátí hodnotu base-2 *x*, tedy 2<sup>x</sup>. V opačném případě vrátí jednu z následujících hodnot:

|Problém|Vrátit|
|-----------|------------|
|*x* = ±0|1|
|*x* = -NEKONEČNO|+0|
|*x* = +INFINITY|+NEKONEČNO|
|*x* = NaN|Není číslo|
|Chyba rozsahu přetečení|+HUGE_VAL, +HUGE_VALF nebo +HUGE_VALL|
|Chyba rozsahu podtečení|Správný výsledek po zaokrouhlení|

Chyby jsou hlášeny podle _matherr [.](matherr.md)

## <a name="remarks"></a>Poznámky

Vzhledem k tomu, že C++ umožňuje přetížení, můžete volat přetížení **exp2,** které take a return **float** a **long double** typy. V programu C **exp2** vždy trvá a vrací **double**.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Hlavička C|Hlavička C++|
|-------------|--------------|------------------|
|**exp**, **expf**, **expl**|\<math.h>|\<cmath>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Abecední seznam odkazů na funkce](crt-alphabetical-function-reference.md)<br/>
[exp, expf, expl](exp-expf.md)<br/>
[log2, log2f, log2l](log2-log2f-log2l.md)<br/>
