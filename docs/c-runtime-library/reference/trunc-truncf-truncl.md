---
title: trunc, truncf, truncl
ms.date: 04/05/2018
api_name:
- trunc
- truncf
- truncl
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
- trunc
- truncf
- truncl
- math/trunc
- math/truncf
- math/truncl
helpviewer_keywords:
- trunc function
- truncf function
- truncl function
ms.assetid: de2038ac-ac0b-483e-870c-e8992dcd4fd0
ms.openlocfilehash: b0c615c91e562fa45f791d8cc20f39a830013aeb
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70945995"
---
# <a name="trunc-truncf-truncl"></a>trunc, truncf, truncl

Určuje nejbližší celé číslo, které je menší nebo rovno zadané hodnotě s plovoucí desetinnou čárkou.

## <a name="syntax"></a>Syntaxe

```C
double trunc( double x );
float trunc( float x ); //C++ only
long double truncl( long double x );
```

```cpp
long double trunc( long double x ); //C++ only
float trunc( float x ); //C++ only
```

### <a name="parameters"></a>Parametry

*x*<br/>
Hodnota, která se má zkrátit

## <a name="return-value"></a>Návratová hodnota

V případě úspěchu vrátí celočíselnou hodnotu *x*, zaokrouhlenou směrem k nule.

V opačném případě může vrátit jednu z následujících možností:

|Problém|vrátit|
|-----------|------------|
|*x* = ± nekonečno|x|
|*x* =  ±0|x|
|*x* = NaN|NaN|

Chyby jsou hlášeny podle zadání v [_matherr](matherr.md).

## <a name="remarks"></a>Poznámky

Vzhledem C++ k tomu, že umožňuje přetížení, můžete volat přetížení **TRUNC –** , která přijímají a vracejí typ **float** a **Long** **Double** . V programu v jazyce C **TRUNC –** vždycky přebírá a vrací **Double**.

Vzhledem k tomu, že největší hodnoty s plovoucí desetinnou čárkou jsou přesná celá čísla, nebude tato funkce sama přeplněna. Funkce přetečení však může způsobit přetečení funkce vrácením hodnoty na celočíselný typ.

Můžete také zaokrouhlit dolů implicitním převodem z plovoucí desetinné čárky na integrální; Nicméně v tomto případě je omezen na hodnoty, které mohou být uloženy v cílovém typu.

## <a name="requirements"></a>Požadavky

|Funkce|Hlavička jazyka C|C++hlaviček|
|--------------|--------------|------------------|
|**TRUNC –** , **truncf –** , **truncl**|\<Math. h >|\<cmath >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Abecední seznam odkazů na funkce](crt-alphabetical-function-reference.md)<br/>
[floor, floorf, floorl](floor-floorf-floorl.md)<br/>
[ceil, ceilf, ceill](ceil-ceilf-ceill.md)<br/>
[round, roundf, roundl](round-roundf-roundl.md)<br/>
