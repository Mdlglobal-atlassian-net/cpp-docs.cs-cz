---
title: ERF –, erff –, erfl –, erfc, erfcf –, erfcl | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- erfl function
- erff function
- erf function
ms.assetid: 144d90d3-e437-41c2-a659-cd57596023b5
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1703b4e352fee798a7b38dd16edf6158cd7f53ea
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2018
---
# <a name="erf-erff-erfl-erfc-erfcf-erfcl"></a>erf, erff, erfl, erfc, erfcf, erfcl

Vypočítá chybovou funkci nebo funkce doplňkovou chybovou hodnotu.

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

**ERF –** funkce vrátit gaussech Chyba funkce *x*. **ERFC –** funkce vrátí doplňkové gaussech Chyba funkce *x*.

## <a name="remarks"></a>Poznámky

**ERF –** funkce Vypočítat gaussech Chyba funkce *x*, který je definován jako:

![Chyba funkce x](media/crt_erf_formula.PNG "CRT_erf_formula")

Doplňkové funkce gaussech chyba je definován jako 1 - erf(x). **ERF –** funkce vrátí hodnotu v rozsahu-1.0 1.0. Neexistuje žádný návratový chyby. **Erfc** funkce vrátí hodnotu v rozsahu 0 až 2. Pokud *x* je příliš velký pro **ERFC –**, **errno** proměnná je nastavená na **erange –**.

Protože C++ umožňuje, aby přetížení, můžete volat přetížení **ERF –** a **ERFC –** , přijmout a vrátit **float** a **dlouho** **dvojité** typy. V programu C **ERF –** a **ERFC –** vždy přijmout a vrátit **dvojité**.

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**ERF –**, **erff –**, **erfl –**, **ERFC –**, **erfcf –**, **erfcl**|\<Math.h >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
