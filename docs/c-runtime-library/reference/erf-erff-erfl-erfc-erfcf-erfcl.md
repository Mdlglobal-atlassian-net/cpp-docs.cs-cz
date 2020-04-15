---
title: erf, erff, erfl, erfc, erfcf, erfcl
ms.date: 4/2/2020
api_name:
- erff
- erfl
- erf
- erfc
- erfcf
- erfcl
- _o_erf
- _o_erfc
- _o_erfcf
- _o_erfcl
- _o_erff
- _o_erfl
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
- erfl
- erf
- erff
- erfc
- erfcf
- erfcl
helpviewer_keywords:
- erfl function
- erff function
- erf function
- erfcl function
- erfcf function
- erfc function
ms.assetid: 144d90d3-e437-41c2-a659-cd57596023b5
ms.openlocfilehash: ad7ad279d3686e4f33a6f5f901c60348c131b89a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81347914"
---
# <a name="erf-erff-erfl-erfc-erfcf-erfcl"></a>erf, erff, erfl, erfc, erfcf, erfcl

Vypočítá chybovou funkci nebo doplňkovou chybovou funkci hodnoty.

## <a name="syntax"></a>Syntaxe

```C
double erf(
   double x
);
float erf(
   float x
); // C++ only
long double erf(
   long double x
); // C++ only
float erff(
   float x
);
long double erfl(
   long double x
);
double erfc(
   double x
);
float erfc(
   float x
); // C++ only
long double erfc(
   long double x
); // C++ only
float erfcf(
   float x
);
long double erfcl(
   long double x
);
```

### <a name="parameters"></a>Parametry

*X*<br/>
Hodnota s plovoucí desetinnou tácem.

## <a name="return-value"></a>Návratová hodnota

Funkce **erf** vrátí chybovou funkci Gauss *x*. Funkce **erfc** vrátí doplňkovou funkci Gaussovy chyby *x*.

## <a name="remarks"></a>Poznámky

Funkce **erf** vypočítají gaussovu chybovou funkci *x*, která je definována jako:

![Chybová funkce x](media/crt_erf_formula.PNG "Chybová funkce x")

Doplňková funkce Gaussovy chyby je definována jako 1 - erf(x). Funkce **erf** vrátí hodnotu v rozsahu -1,0 až 1,0. Neexistuje žádná chyba vrátit. Funkce **erfc** vrátí hodnotu v rozsahu 0 až 2. Pokud *x* je příliš velký pro **erfc**, je proměnná **errno** nastavena na **ERANGE**.

Protože C++ umožňuje přetížení, můžete volat přetížení **erf** a **erfc,** které take a return **float** a **long** **double** typy. V programu C **erf** a **erfc** vždy vzít a vrátit **double**.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**erf**, **erff**, **erfl**, **erfc**, **erfcf**, **erfcl**|\<math.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Podpora s plovoucí desetinnou tálicí](../../c-runtime-library/floating-point-support.md)<br/>
