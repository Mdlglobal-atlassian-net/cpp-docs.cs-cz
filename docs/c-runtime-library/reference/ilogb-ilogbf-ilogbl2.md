---
title: ilogb – ilogbf –, ilogbl2
ms.date: 04/05/2018
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
ms.openlocfilehash: 63e04246d29fde50c745a5f353829bd337a814ad
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50551980"
---
# <a name="ilogb-ilogbf-ilogbl"></a>ilogb, ilogbf, ilogbl

Načte celé číslo, které představuje nevyváženého exponentu base-2 zadané hodnoty.

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

Pokud je úspěšná, vrátí exponent základu 2 *x* jako podepsané **int** hodnotu.

V opačném případě vrátí jednu z následujících hodnot, podle \<math.h >:

|Vstup|Výsledek|
|-----------|------------|
|±0|FP_ILOGB0|
|±INF ±nan nekonečno|FP_ILOGBNAN|

Jsou hlášeny chyby uvedené v [_matherr](matherr.md).

## <a name="remarks"></a>Poznámky

Protože jazyk C++ umožňuje přetížení, můžete volat přetížení **ilogb –** , která používají a vrací **float** a **dlouhé** **double** typy. V programu jazyka C **ilogb –** vždy převezme a vrátí **double**.

Volání této funkce je podobný voláním ekvivalentní **logb –** funkce a pak přetypování návratová hodnota rovna **int**.

## <a name="requirements"></a>Požadavky

|Rutina|Záhlaví C|Hlaviček jazyka C++|
|-------------|--------------|------------------|
|**ilogb –**, **ilogbf –**, **ilogbl**|\<Math.h >|\<cmath >|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Abecední seznam odkazů na funkce](crt-alphabetical-function-reference.md)<br/>
[frexp](frexp.md)<br/>
[logb, logbf, logbl, _logb, _logbf](logb-logbf-logbl-logb-logbf.md)<br/>
