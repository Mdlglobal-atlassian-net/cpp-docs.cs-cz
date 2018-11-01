---
title: fmax, fmaxf, fmaxl
ms.date: 04/05/2018
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
helpviewer_keywords:
- fmax function
- fmaxf function
- fmaxl function
ms.assetid: a773ccf7-495e-4a9a-8c6d-dfb53e341e35
ms.openlocfilehash: 0fbe23a4b7d6e0c59523d62f844dd89e66642933
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50465153"
---
# <a name="fmax-fmaxf-fmaxl"></a>fmax, fmaxf, fmaxl

Určení větší ze dvou číselných hodnot, které se zadané.

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

Pokud je úspěšná, vrátí větší z následujících *x* nebo *y*. Vrácená hodnota je přesné a nezávisí na jakoukoli formu zaokrouhlení.

V opačném případě může vracet instanci jednoho z následujících hodnot:

|Problém|Vrátí|
|-----------|------------|
|*x* = NaN|*y*|
|*y* = NaN|*x*|
|*x* a *y* = NaN|NaN|

Tato funkce nebude používat chyby uvedené v [_matherr](matherr.md).

## <a name="remarks"></a>Poznámky

Protože jazyk C++ umožňuje přetížení, můžete volat přetížení fmax, které používají a vrací plovoucí desetinnou čárkou a typy long double. Fmax – v programu jazyka C, vždy převezme a vrátí double.

## <a name="requirements"></a>Požadavky

|Funkce|Záhlaví C|Hlaviček jazyka C++|
|--------------|--------------|------------------|
|**Fmax –**, **fmaxf –**, **fmaxl**|\<Math.h >|\<cmath > nebo \<math.h >|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Abecední seznam odkazů na funkce](crt-alphabetical-function-reference.md)<br/>
[fmin, fminf, fminl](fmin-fminf-fminl.md)<br/>
