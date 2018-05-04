---
title: ilogb – ilogbf –, ilogbl2 | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
apiname:
- ilogb
- ilogbf
- ilogbl
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
- ilogb
- ilogbf
- ilogbl
- math/ilogb
- math/ilogbf
- math/ilogbl
helpviewer_keywords:
- ilogb function
- ilogbf function
- ilogbl function
ms.assetid: 9ef19d57-1caa-41d5-8233-2faad3562fcb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1436874e1ab35cc72dc40390adf5597529d3bf57
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ilogb-ilogbf-ilogbl"></a>ilogb, ilogbf, ilogbl

Načte celé číslo, které představuje neposunutého exponent základní-2 se zadanou hodnotou.

## <a name="syntax"></a>Syntaxe

```C
int ilogb(
   double x
);

int ilogb(
   float x
); //C++ only

int ilogb(
   long double x
); //C++ only

int ilogbf(
   float x
);

int ilogbl(
   long double x
);

```

### <a name="parameters"></a>Parametry

*x*<br/>
Zadaná hodnota.

## <a name="return-value"></a>Návratová hodnota

V případě úspěchu vrátí exponent základu 2 *x* jako přihlášeni **int** hodnotu.

Jinak vrátí jednu z následujících hodnot, které jsou definované v \<math.h >:

|Vstup|Výsledek|
|-----------|------------|
|±0|FP_ILOGB0|
|±INF, ±nan neomezené|FP_ILOGBNAN|

Vznikly chyby uvedené v [_matherr –](matherr.md).

## <a name="remarks"></a>Poznámky

Protože C++ umožňuje, aby přetížení, můžete volat přetížení **ilogb –** , přijmout a vrátit **float** a **dlouho** **dvojité** typy. V programu C **ilogb –** vždy provede a vrátí **dvojité**.

Volání této funkce je podobná volání ekvivalent **logb –** funkce a potom přetypování návratovou hodnotu pro **int**.

## <a name="requirements"></a>Požadavky

|Rutina|Hlavička C|Hlavička C++|
|-------------|--------------|------------------|
|**ilogb –**, **ilogbf –**, **ilogbl**|\<Math.h >|\<cmath – >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Abecední seznam odkazů na funkce](crt-alphabetical-function-reference.md)<br/>
[frexp](frexp.md)<br/>
[logb, logbf, logbl, _logb, _logbf](logb-logbf-logbl-logb-logbf.md)<br/>
