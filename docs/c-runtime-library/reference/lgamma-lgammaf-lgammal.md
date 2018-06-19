---
title: lgamma – lgammaf –, lgammal | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
apiname:
- lgamma
- lgammaf
- lgammal
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
- lgamma
- lgammaf
- lgammal
- math/lgamma
- math/lgammaf
- math/lgammal
dev_langs:
- C++
helpviewer_keywords:
- lgamma function
- lgammal function
- lgammaf function
ms.assetid: 6e326c58-7077-481a-a329-c82ae56ae9e6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4fb668e1c24d3f24331e0892002530192afdaeb6
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32400249"
---
# <a name="lgamma-lgammaf-lgammal"></a>lgamma, lgammaf, lgammal

Určuje přirozený logaritmus absolutní hodnotu funkce gamma zadané hodnoty.

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

*x*<br/>
Hodnota k výpočtu.

## <a name="return-value"></a>Návratová hodnota

V případě úspěchu vrátí přirozený logaritmus absolutní hodnotu gama funkce *x*.

|Problém|Vrátí|
|-----------|------------|
|*x* = NaN.|NaN|
|*x* = ±0|+ INFINITY|
|*x*= záporné celé číslo|+ INFINITY|
|±INFINITY|+ INFINITY|
|Chyba pólu|+ Huge_val – + HUGE_VALF, nebo + HUGE_VALL|
|Rozsah chybu přetečení|±HUGE_VAL, ±HUGE_VALF nebo ±HUGE_VALL|

Vznikly chyby uvedené v [_matherr –](matherr.md).

## <a name="remarks"></a>Poznámky

Protože C++ umožňuje, aby přetížení, můžete volat přetížení **lgamma –** , přijmout a vrátit **float** a **dlouho** **dvojité** typy. V programu C **lgamma –** vždy provede a vrátí **dvojité**.

Pokud x je racionální číslo, vrátí tato funkce logaritmus faktoriál (x - 1).

## <a name="requirements"></a>Požadavky

|Funkce|Hlavička C|Hlavička C++|
|--------------|--------------|------------------|
|**lgamma –**, **lgammaf –**, **lgammal**|\<Math.h >|\<cmath – >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Abecední seznam odkazů na funkce](crt-alphabetical-function-reference.md)<br/>
[tgamma, tgammaf, tgammal](tgamma-tgammaf-tgammal.md)<br/>
