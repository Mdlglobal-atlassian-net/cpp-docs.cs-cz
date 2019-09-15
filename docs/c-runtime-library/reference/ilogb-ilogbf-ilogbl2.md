---
title: ilogb, ilogbf, ilogbl2
ms.date: 04/05/2018
api_name:
- ilogb
- ilogbf
- ilogbl
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
ms.openlocfilehash: fdafba039537358c9b6a1de21dc176ceea38b4fa
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70954768"
---
# <a name="ilogb-ilogbf-ilogbl"></a>ilogb, ilogbf, ilogbl

Načte celé číslo, které představuje neposunutý exponent Base-2 zadané hodnoty.

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
Zadaná hodnota

## <a name="return-value"></a>Návratová hodnota

V případě úspěchu vrátí exponent Base-2 hodnoty *x* jako hodnotu se znaménkem **int** .

V opačném případě vrátí jednu z následujících hodnot, která \<je definována v Math. h >:

|Vstup|Výsledek|
|-----------|------------|
|±0|FP_ILOGB0|
|± INF, ± NaN, neomezeno|FP_ILOGBNAN|

Chyby jsou hlášeny podle zadání v [_matherr](matherr.md).

## <a name="remarks"></a>Poznámky

Vzhledem C++ k tomu, že umožňuje přetížení, můžete volat přetížení **ilogb –** , která přijímají a vracejí typ **float** a **Long** **Double** . V programu v jazyce C **ilogb –** vždycky přebírá a vrací **Double**.

Volání této funkce je podobné jako volání ekvivalentní funkce **logb –** a pak přetypování návratové hodnoty na **int**.

## <a name="requirements"></a>Požadavky

|Rutina|Hlavička jazyka C|C++hlaviček|
|-------------|--------------|------------------|
|**ilogb**, **ilogbf**, **ilogbl**|\<Math. h >|\<cmath >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Abecední seznam odkazů na funkce](crt-alphabetical-function-reference.md)<br/>
[frexp](frexp.md)<br/>
[logb, logbf, logbl, _logb, _logbf](logb-logbf-logbl-logb-logbf.md)<br/>
