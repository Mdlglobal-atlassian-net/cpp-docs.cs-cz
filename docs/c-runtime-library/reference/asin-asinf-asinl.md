---
title: asin, asinf, asinl
ms.date: 04/05/2018
api_name:
- asinf
- asinl
- asin
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
- asin
- asinl
- asinf
helpviewer_keywords:
- asin function
- asinl function
- asinf function
- trigonometric functions
- arcsine function
ms.assetid: ca05f9ea-b711-49f6-9f32-2f4019abfd69
ms.openlocfilehash: 1e70c9b2187b97d3dea589c1757081da8bf2bd10
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70943651"
---
# <a name="asin-asinf-asinl"></a>asin, asinf, asinl

Vypočítá Arkus sinus.

## <a name="syntax"></a>Syntaxe

```C
double asin( double x );
float asinf ( float x );
long double asinl( long double x );
```

```cpp
float asin( float x );  // C++ only
long double asin( long double x );  // C++ only
```

### <a name="parameters"></a>Parametry

*x*<br/>
Hodnota, jejíž arkussinus se má vypočítat

## <a name="return-value"></a>Návratová hodnota

Funkce **asin** vrátí Arkus (inverzní funkci sinus) hodnoty *x* v rozsahu-π/2 do π/2 radiánů.

Ve výchozím nastavení, pokud *x* je menší než-1 nebo větší než 1, **asin** vrátí nekonečnou hodnotu.

|Vstup|Výjimka SEH|Výjimka matherr|
|-----------|-------------------|-----------------------|
|± ∞|**NENÍ**|**_DOMAIN**|
|± **QNAN**, **IND**|žádná|**_DOMAIN**|
|&#124;x&#124;>1|**NENÍ**|**_DOMAIN**|

## <a name="remarks"></a>Poznámky

Vzhledem C++ k tomu, že umožňuje přetížení, můžete volat přetížení **asin** s hodnotami **float** a **Long** **Double** . V programu v jazyce C **asin** vždycky přebírá a vrací **Double**.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaná hlavička (C)|Požadovaná hlavička (C++)|
|-------------|---------------------|-|
|**asin**, **asinf –** , **asinl**|\<Math. h >|\<cmath > nebo \<Math. h >|

## <a name="example"></a>Příklad

Další informace najdete v tématu [ACOS, acosf –, acosl](acos-acosf-acosl.md).

## <a name="see-also"></a>Viz také:

[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[acos, acosf, acosl](acos-acosf-acosl.md)<br/>
[atan, atanf, atanl, atan2, atan2f, atan2l](atan-atanf-atanl-atan2-atan2f-atan2l.md)<br/>
[cos, cosf, cosl](cos-cosf-cosl.md)<br/>
[_matherr](matherr.md)<br/>
[sin, sinf, sinl](sin-sinf-sinl.md)<br/>
[tan, tanf, tanl](tan-tanf-tanl.md)<br/>
