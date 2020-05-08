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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 3a80efab34b45348ca00f09b2fd6e2ea5077fd86
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82909646"
---
# <a name="exp2-exp2f-exp2l"></a>exp2, exp2f, exp2l

Hodnoty COMPUTE 2 byly vyvolány na zadanou hodnotu.

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

*znak*<br/>
Hodnota exponentu

## <a name="return-value"></a>Návratová hodnota

V případě úspěchu vrátí exponent základní-2 třídy *x*, tj. 2<sup>x</sup>. V opačném případě vrátí jednu z následujících hodnot:

|Problém|Vrátit|
|-----------|------------|
|*x* = ± 0|1|
|*x* = – nekonečno|+ 0|
|*x* = + nekonečno|+ Nekonečno|
|*x* = NaN|Není číslo|
|Chyba rozsahu přetečení|+ HUGE_VAL, + HUGE_VALF nebo + HUGE_VALL|
|Chyba podtečení rozsahu|Správný výsledek, po zaokrouhlení|

Chyby jsou hlášeny tak, jak jsou uvedeny v [_matherr](matherr.md).

## <a name="remarks"></a>Poznámky

Vzhledem k tomu, že jazyk C++ umožňuje přetížení, můžete volat přetížení **exp2 –** , která přijímají a vracejí typ **float** a **Long Double** . V programu v jazyce C **exp2 –** vždycky přebírá a vrací **Double**.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Hlavička jazyka C|Hlavička C++|
|-------------|--------------|------------------|
|**exp**, **expf –**, **Expl**|\<Math. h>|\<cmath>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Abecední seznam odkazů na funkce](crt-alphabetical-function-reference.md)<br/>
[exp, expf, expl](exp-expf.md)<br/>
[log2, log2f, log2l](log2-log2f-log2l.md)<br/>
