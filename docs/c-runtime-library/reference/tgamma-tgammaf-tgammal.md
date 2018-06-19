---
title: tgamma – tgammaf –, tgammal | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- tgamma function
- tgammaf function
- tgammal function
ms.assetid: f1bd2681-8af2-48a9-919d-5358fd068acd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7861b297646f4a704134e0d874fad8c924a7ebc8
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32409872"
---
# <a name="tgamma-tgammaf-tgammal"></a>tgamma, tgammaf, tgammal

Určuje funkce gamma zadané hodnoty.

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

V případě úspěchu vrátí gama z *x*.

Rozsah chybě může dojít, pokud odhad *x* je příliš velký či příliš malý pro datový typ. Chyba domény nebo rozsah chybě může dojít, pokud *x* < = 0.

|Problém|Vrátí|
|-----------|------------|
|x = ±0|±INFINITY|
|x = záporné celé číslo|NaN|
|x = - INFINITY|NaN|
|x = + INFINITY|+ INFINITY|
|x = NaN.|NaN|
|chyby domény|NaN|
|Chyba pólu|±HUGE_VAL, ±HUGE_VALF nebo ±HUGE_VALL|
|Rozsah chybu přetečení|±HUGE_VAL, ±HUGE_VALF nebo ±HUGE_VALL|
|Podtečení rozsah chyby|správnou hodnotu, po zaokrouhlení.|

Vznikly chyby uvedené v [_matherr –](matherr.md).

## <a name="remarks"></a>Poznámky

Protože C++ umožňuje, aby přetížení, můžete volat přetížení **tgamma –** , přijmout a vrátit **float** a **dlouho** **dvojité** typy. V programu C **tgamma –** vždy provede a vrátí **dvojité**.

Pokud x je číslo přirozený, vrátí tato funkce faktoriál (x-1).

## <a name="requirements"></a>Požadavky

|Funkce|Hlavička C|Hlavička C++|
|--------------|--------------|------------------|
|**tgamma –**, **tgammaf –**, **tgammal**|\<Math.h >|\<cmath – >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Abecední seznam odkazů na funkce](crt-alphabetical-function-reference.md)<br/>
[lgamma, lgammaf, lgammal](lgamma-lgammaf-lgammal.md)<br/>
