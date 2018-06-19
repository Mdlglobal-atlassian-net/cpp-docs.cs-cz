---
title: lrint, lrintf, lrintl, llrint, llrintf, llrintl | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
apiname:
- lrint
- lrintl
- lrintf
- llrint
- llrintf
- llrintl
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
dev_langs:
- C++
helpviewer_keywords:
- lrint function
- lrintf function
- lrintl function
- llrint function
- llrintf function
- llrintl function
ms.assetid: 28ccd5b3-5e6f-434f-997d-a21d51b8ce7f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5ace427267a45c87213f62276e1d7799f27db1cd
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32401256"
---
# <a name="lrint-lrintf-lrintl-llrint-llrintf-llrintl"></a>lrint, lrintf, lrintl, llrint, llrintf, llrintl

Zaokrouhlí na nejbližší hodnotu integrální zadaná hodnota s plovoucí desetinnou čárkou s použitím aktuální režim zaokrouhlení a směr.

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
Hodnota, která má být zaokrouhleno.

## <a name="return-value"></a>Návratová hodnota

V případě úspěchu vrátí zaokrouhlené integrální hodnotu *x*.

|Problém|Vrátí|
|-----------|------------|
|*x* je mimo rozsah návratový typ<br /><br /> *x* = ±∞<br /><br /> *x* = NaN.|Vyvolá **FE_INVALID** a vrátí nula (0).|

## <a name="remarks"></a>Poznámky

Protože C++ umožňuje, aby přetížení, můžete volat přetížení **lrint** a **llrint** trvají **float** a **dlouho**  **dvojité** typy. V programu C **lrint** a **llrint** vždy provést **dvojité**.

Pokud *x* nepředstavuje s plovoucí desetinnou čárkou ekvivalentní celočíselné hodnoty, tyto funkce vyvolat **FE_INEXACT**.

**Microsoft konkrétní**: Pokud výsledkem je mimo rozsah návratový typ, nebo pokud je parametr NaN nebo infinity, vrácená hodnota je implementace definované. Kompilátor Microsoft vrátí nula (0) hodnotu.

## <a name="requirements"></a>Požadavky

|Funkce|Hlavička C|Hlavička C++|
|--------------|--------------|------------------|
|**lrint**, **lrintf**, **lrintl**, **llrint**, **llrintf**, **llrintl**|\<Math.h >|\<cmath – >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Abecední seznam odkazů na funkce](crt-alphabetical-function-reference.md)<br/>
