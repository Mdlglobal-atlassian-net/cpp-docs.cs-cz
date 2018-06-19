---
title: Fmin, fminf –, fminl | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
apiname:
- fmin
- fminf
- fminl
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
- fmin
- fminf
- fminl
- math/fmin
- math/fminf
- math/fminl
helpviewer_keywords:
- fmin function
- fminf function
- fminl function
ms.assetid: 1916dfb5-99c1-4b0d-aefb-513525c3f2ac
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: abf16c4cc21d1dc396f0b81aadc8d495c6bdd4b9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32398942"
---
# <a name="fmin-fminf-fminl"></a>fmin, fminf, fminl

Určuje menší ze dvou zadaných hodnot.

## <a name="syntax"></a>Syntaxe

```C
double fmin(
   double x,
   double y
);

float fmin(
   float x,
   float y
); //C++ only

long double fmin(
   long double x,
   long double y
); //C++ only

float fminf(
   float x,
   float y
);

long double fminl(
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

V případě úspěchu vrátí menší z *x* nebo *y*.

|Vstup|Výsledek|
|-----------|------------|
|*x* je NaN.|*y*|
|*y* je NaN.|*x*|
|*x* a *y* jsou NaN.|NaN|

Funkce nezpůsobí [_matherr –](matherr.md) má být volána, způsobit, že všechny výjimky, s plovoucí desetinnou čárkou nebo změňte hodnotu **errno**.

## <a name="remarks"></a>Poznámky

Protože C++ umožňuje, aby přetížení, můžete volat přetížení **fmin** , přijmout a vrátit **float** a **dlouho** **dvojité** typy. V programu C **fmin** vždy provede a vrátí **dvojité**.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**Fmin**, **fminf –**, **fminl**|C: \<math.h ><br />C++: \<math.h > nebo \<cmath – >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Abecední seznam odkazů na funkce](crt-alphabetical-function-reference.md)<br/>
[fmax, fmaxf, fmaxl](fmax-fmaxf-fmaxl.md)<br/>
