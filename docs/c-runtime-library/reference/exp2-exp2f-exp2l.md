---
title: exp2, exp2f, exp2l
ms.date: 04/05/2018
apiname:
- exp2
- exp2f
- exp2l
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
ms.openlocfilehash: 70a3b7eb610556d4a26de7cf0aad55affcdbdc94
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62338828"
---
# <a name="exp2-exp2f-exp2l"></a>exp2, exp2f, exp2l

Vypočítá 2 umocněné na zadanou hodnotu.

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
Hodnota exponent.

## <a name="return-value"></a>Návratová hodnota

Pokud je úspěšná, vrátí exponent základu 2 *x*, tedy 2<sup>x</sup>. V opačném případě vrátí jednu z následujících hodnot:

|Problém|Vrátí|
|-----------|------------|
|*x* = ±0|1|
|*x* = - NEKONEČNO|+0|
|*x* = + NEKONEČNO|+ NEKONEČNO|
|*x* = NaN|NaN|
|Chyba přetečení rozsahu|+ HUGE_VAL + HUGE_VALF, nebo + HUGE_VALL|
|Chyba podtečení rozsahu|Správný výsledek, po zaokrouhlení|

Jsou hlášeny chyby uvedené v [_matherr](matherr.md).

## <a name="remarks"></a>Poznámky

Protože jazyk C++ umožňuje přetížení, můžete volat přetížení **exp2 –** , která používají a vrací **float** a **long double** typy. V programu jazyka C **exp2 –** vždy převezme a vrátí **double**.

## <a name="requirements"></a>Požadavky

|Rutina|Záhlaví C|Hlaviček jazyka C++|
|-------------|--------------|------------------|
|**Exp**, **expf –**, **expl**|\<math.h>|\<cmath>|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Abecední seznam odkazů na funkce](crt-alphabetical-function-reference.md)<br/>
[exp, expf, expl](exp-expf.md)<br/>
[log2, log2f, log2l](log2-log2f-log2l.md)<br/>
