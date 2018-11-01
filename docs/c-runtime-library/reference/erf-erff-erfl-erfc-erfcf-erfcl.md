---
title: erf, erff, erfl, erfc, erfcf, erfcl
ms.date: 04/05/2018
apiname:
- erff
- erfl
- erf
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
- erfl
- erf
- erff
helpviewer_keywords:
- erfl function
- erff function
- erf function
ms.assetid: 144d90d3-e437-41c2-a659-cd57596023b5
ms.openlocfilehash: 5723286add75a57844f177b9df5d86eb15080229
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50450043"
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

*x*<br/>
Hodnota s plovoucí desetinnou čárkou.

## <a name="return-value"></a>Návratová hodnota

**Erf** funkce vrátí Gauss chybovou funkci *x*. **Erfc** vrátí funkce Gauss doplňkovou chybovou funkci *x*.

## <a name="remarks"></a>Poznámky

**Erf** funkce vypočítá chybovou funkci Gauss z *x*, který je definován jako:

![Chyba funkce x](media/crt_erf_formula.PNG "CRT_erf_formula")

Doplňková chybová funkce Gauss je definována jako 1 – erf(x). **Erf** vrátí funkce hodnotu v rozsahu-1.0 1.0. Není vrácena žádná chyba. **Erfc** vrátí funkce hodnotu v rozsahu 0 až 2. Pokud *x* je příliš velká pro **erfc**, **errno** proměnná je nastavená na **ERANGE**.

Protože jazyk C++ umožňuje přetížení, můžete volat přetížení **erf** a **erfc** , která používají a vrací **float** a **dlouhé** **double** typy. V programu jazyka C **erf** a **erfc** vždy převezme a vrátí **double**.

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**ERF –**, **erff –**, **erfl –**, **erfc**, **erfcf –**, **erfcl**|\<Math.h >|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
