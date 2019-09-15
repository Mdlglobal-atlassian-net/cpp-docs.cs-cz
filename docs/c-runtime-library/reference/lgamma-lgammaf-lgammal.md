---
title: lgamma, lgammaf, lgammal
ms.date: 04/05/2018
api_name:
- lgamma
- lgammaf
- lgammal
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
- lgamma
- lgammaf
- lgammal
- math/lgamma
- math/lgammaf
- math/lgammal
helpviewer_keywords:
- lgamma function
- lgammal function
- lgammaf function
ms.assetid: 6e326c58-7077-481a-a329-c82ae56ae9e6
ms.openlocfilehash: 9baf8f0fefb50cea6a5301aac9ffd48ff3cd5bde
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70953373"
---
# <a name="lgamma-lgammaf-lgammal"></a>lgamma, lgammaf, lgammal

Určuje přirozený logaritmus absolutní hodnoty funkce gamma zadané hodnoty.

## <a name="syntax"></a>Syntaxe

```C
double lgamma( double x );
float lgammaf( float x );
long double lgammal( long double x );
```

```cpp
float lgamma( float x ); //C++ only
long double lgamma( long double x ); //C++ only
```

### <a name="parameters"></a>Parametry

*x*<br/>
Hodnota, která se má vypočítat

## <a name="return-value"></a>Návratová hodnota

V případě úspěchu vrátí přirozený logaritmus absolutní hodnoty funkce gamma *x*.

|Problém|vrátit|
|-----------|------------|
|*x* = NaN|NaN|
|*x* = ±0|\+ NEKONEČNO|
|*x*= záporné celé číslo|\+ NEKONEČNO|
|± NEKONEČNO|\+ NEKONEČNO|
|Chyba pole|\+ HUGE_VAL, + HUGE_VALF nebo + HUGE_VALL|
|Chyba rozsahu přetečení|± HUGE_VAL, ± HUGE_VALF nebo ± HUGE_VALL|

Chyby jsou hlášeny podle zadání v [_matherr](matherr.md).

## <a name="remarks"></a>Poznámky

Vzhledem C++ k tomu, že umožňuje přetížení, můžete volat přetížení **lgamma –** , která přijímají a vracejí typ **float** a **Long** **Double** . V programu v jazyce C **lgamma –** vždycky přebírá a vrací **Double**.

Pokud x je racionální číslo, vrátí tato funkce logaritmus faktoriál (x-1).

## <a name="requirements"></a>Požadavky

|Funkce|Hlavička jazyka C|C++hlaviček|
|--------------|--------------|------------------|
|**lgamma –** , **lgammaf –** , **lgammal**|\<Math. h >|\<cmath >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Abecední seznam odkazů na funkce](crt-alphabetical-function-reference.md)<br/>
[tgamma, tgammaf, tgammal](tgamma-tgammaf-tgammal.md)<br/>
