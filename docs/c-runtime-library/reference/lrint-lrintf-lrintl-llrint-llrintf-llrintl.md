---
title: lrint, lrintf, lrintl, llrint, llrintf, llrintl
ms.date: 04/05/2018
api_name:
- lrint
- lrintl
- lrintf
- llrint
- llrintf
- llrintl
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
- lrint
- lrintf
- lrintl
- llrint
- llrintf
- llrintl
- math/lrint
- math/lrintf
- math/lrintl
- math/llrint
- math/llrintf
- math/llrintl
helpviewer_keywords:
- lrint function
- lrintf function
- lrintl function
- llrint function
- llrintf function
- llrintl function
ms.assetid: 28ccd5b3-5e6f-434f-997d-a21d51b8ce7f
ms.openlocfilehash: c7831842eb4d3c1eef9c4c9e83bbddb557cec0e3
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857746"
---
# <a name="lrint-lrintf-lrintl-llrint-llrintf-llrintl"></a>lrint, lrintf, lrintl, llrint, llrintf, llrintl

Zaokrouhlí zadanou hodnotu s plovoucí desetinnou čárkou na nejbližší celočíselnou hodnotu pomocí současného režimu zaokrouhlení a směru.

## <a name="syntax"></a>Syntaxe

```C
long int lrint(
   double x
);

long int lrint(
   float x
); //C++ only

long int lrint(
   long double x
); //C++ only

long int lrintf(
   float x
);

long int lrintl(
   long double x
);

long long int llrint(
   double x
);

long long int llrint(
   float x
); //C++ only

long long int llrint(
   long double x
); //C++ only

long long int llrintf(
   float x
);

long long int llrintl(
   long double x
);
```

### <a name="parameters"></a>Parametry

*x*<br/>
Hodnota, která má být zaokrouhlena.

## <a name="return-value"></a>Návratová hodnota

V případě úspěchu vrátí zaokrouhlenou celočíselnou hodnotu *x*.

|Problém|Výsledek|
|-----------|------------|
|*x* je mimo rozsah návratového typu.<br /><br /> *x* = ± ∞<br /><br /> *x* = NaN|Vyvolává **FE_INVALID** a vrací nulu (0).|

## <a name="remarks"></a>Poznámky

Vzhledem C++ k tomu, že umožňuje přetížení, můžete volat přetížení **lrint** a **llrint** , které přebírají **float** a **Long** **Double** Types. V programu v jazyce C **lrint** a **llrint** vždycky pobírají **dvojitou**hodnotu.

Pokud *x* nepředstavuje ekvivalent plovoucí desetinné čárky integrální hodnoty, tyto funkce vyvolají **FE_INEXACT**.

**Specifické pro společnost Microsoft**: Pokud je výsledek mimo rozsah návratového typu nebo pokud je parametr NaN nebo Infinite, vrácená hodnota je definovaná implementací. Kompilátor Microsoft vrátí hodnotu nula (0).

## <a name="requirements"></a>Požadavky

|Funkce|Hlavička jazyka C|C++hlaviček|
|--------------|--------------|------------------|
|**lrint**, **lrintf**, **lrintl**, **llrint**, **llrintf**, **llrintl**|\<Math. h >|\<cmath >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Abecední seznam odkazů na funkce](crt-alphabetical-function-reference.md)<br/>
