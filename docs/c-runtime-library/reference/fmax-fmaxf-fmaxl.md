---
title: Fmax, fmaxf –, fmaxl | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
apiname:
- fmax
- fmaxf
- fmaxl
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
- fmax
- fmaxf
- fmaxl
- math/fmax
- math/fmaxf
- math/fmaxl
dev_langs:
- C++
helpviewer_keywords:
- fmax function
- fmaxf function
- fmaxl function
ms.assetid: a773ccf7-495e-4a9a-8c6d-dfb53e341e35
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d6e210fac83c19efaecb909d54734d0422956f37
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="fmax-fmaxf-fmaxl"></a>fmax, fmaxf, fmaxl

Určení větší ze dvou zadaný číselných hodnot.

## <a name="syntax"></a>Syntaxe

```C
double fmax(
   double x,
   double y
);

float fmax(
   float x,
   float y
); //C++ only

long double fmax(
   long double x,
   long double y
); //C++ only

float fmaxf(
   float x,
   float y
);

long double fmaxl(
   long double x,
   long double y
);

```

### <a name="parameters"></a>Parametry

*x*<br/>
První hodnota pro porovnání.

*y*<br/>
Druhá hodnota pro porovnání.

## <a name="return-value"></a>Návratová hodnota

V případě úspěchu vrátí větší z *x* nebo *y*. Hodnota vrácená je přesný a není závislá na jakoukoli formu zaokrouhlení.

Jinak může vrátit jednu z následujících hodnot:

|Problém|Vrátí|
|-----------|------------|
|*x* = NaN.|*y*|
|*y* = NaN.|*x*|
|*x* a *y* = NaN.|NaN|

Tato funkce nepoužívá chyby uvedené v [_matherr –](matherr.md).

## <a name="remarks"></a>Poznámky

Protože C++ umožňuje, aby přetížení, můžete volat přetížení fmax, která přijmout a vrátit float a typy long double. V programu C fmax vždy provede a vrátí hodnotu typu double.

## <a name="requirements"></a>Požadavky

|Funkce|Hlavička C|Hlavička C++|
|--------------|--------------|------------------|
|**Fmax**, **fmaxf –**, **fmaxl**|\<Math.h >|\<cmath – > nebo \<math.h >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Abecední seznam odkazů na funkce](crt-alphabetical-function-reference.md)<br/>
[fmin, fminf, fminl](fmin-fminf-fminl.md)<br/>
