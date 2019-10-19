---
title: erf, erff, erfl, erfc, erfcf, erfcl
ms.date: 01/31/2019
api_name:
- erff
- erfl
- erf
- erfc
- erfcf
- erfcl
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
ms.openlocfilehash: df724ed056c02d79b5b51f97ae4aaf8ae267fde5
ms.sourcegitcommit: 8178d22701047d24f69f10d01ba37490e3d67241
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "70937622"
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

*znak*<br/>
Hodnota s plovoucí desetinnou čárkou.

## <a name="return-value"></a>Návratová hodnota

Funkce **ERF** vrátí funkci Gauss Error *x*. Funkce **ERFC –** vrátí doplňkovou funkci Gauss Error *x*.

## <a name="remarks"></a>Poznámky

Funkce **ERF** vypočítá funkci Gauss Error *x*, která je definována jako:

![Funkce Error x](media/crt_erf_formula.PNG "Funkce Error x")

Doplňková chybová funkce Gauss je definována jako 1 – ERF (x). Funkce **ERF** vrací hodnotu v rozsahu-1,0 až 1,0. Nevrátila se žádná chybová zpráva. Funkce **ERFC –** vrací hodnotu v rozsahu 0 až 2. Pokud je *x* pro **ERFC –** moc velké, proměnná **errno** je nastavená na **ERANGE**.

Vzhledem C++ k tomu, že umožňuje přetížení, můžete volat přetížení funkce **ERF** a **ERFC –** , které přebírají a vracejí typ **float** a **Long** **Double** . V programu v jazyce C, funkce **ERF** a **ERFC –** vždy převezme a vrátí hodnotu **Double**.

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**ERF**, **erff –** , **erfl**, **ERFC –** , **erfcf –** , **erfcl**|\<math. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
