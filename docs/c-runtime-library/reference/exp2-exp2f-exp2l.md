---
title: exp2, exp2f, exp2l
ms.date: 04/05/2018
api_name:
- exp2
- exp2f
- exp2l
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
ms.openlocfilehash: 89e0448501cbd423278607bb22959c6cd1ed9464
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70941567"
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

*x*<br/>
Hodnota exponentu

## <a name="return-value"></a>Návratová hodnota

V případě úspěchu vrátí exponent základní-2 třídy *x*, tj. 2<sup>x</sup>. V opačném případě vrátí jednu z následujících hodnot:

|Problém|vrátit|
|-----------|------------|
|*x* = ±0|1|
|*x* = – nekonečno|+0|
|*x* = + nekonečno|\+ NEKONEČNO|
|*x* = NaN|NaN|
|Chyba rozsahu přetečení|\+ HUGE_VAL, + HUGE_VALF nebo + HUGE_VALL|
|Chyba podtečení rozsahu|Správný výsledek, po zaokrouhlení|

Chyby jsou hlášeny podle zadání v [_matherr](matherr.md).

## <a name="remarks"></a>Poznámky

Vzhledem C++ k tomu, že umožňuje přetížení, můžete volat přetížení **exp2 –** , která přijímají a vracejí typ **float** a **Long Double** . V programu v jazyce C **exp2 –** vždycky přebírá a vrací **Double**.

## <a name="requirements"></a>Požadavky

|Rutina|Hlavička jazyka C|C++hlaviček|
|-------------|--------------|------------------|
|**exp**, **expf –** , **Expl**|\<Math. h >|\<cmath >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Abecední seznam odkazů na funkce](crt-alphabetical-function-reference.md)<br/>
[exp, expf, expl](exp-expf.md)<br/>
[log2, log2f, log2l](log2-log2f-log2l.md)<br/>
