---
title: nearbyint, nearbyintf, nearbyintl
ms.date: 04/05/2018
api_name:
- nearbyint
- nearbyintf
- nearbyintl
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
- nearbyint
- nearbyintf
- nearbyintl
- math/nearbyint
- math/narbyintf
- math/narbyintl
helpviewer_keywords:
- nearbyint function
- nearbyintf function
- nearbyintl function
ms.assetid: dd39cb68-96b0-434b-820f-6ff2ea65584f
ms.openlocfilehash: cd0a7d00c5019dd1e483d555df6db8d9770e61c1
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70951397"
---
# <a name="nearbyint-nearbyintf-nearbyintl"></a>nearbyint, nearbyintf, nearbyintl

Zaokrouhlí zadanou hodnotu s plovoucí desetinnou čárkou na celé číslo a vrátí tuto hodnotu ve formátu s plovoucí desetinnou čárkou.

## <a name="syntax"></a>Syntaxe

```C
double nearbyint( double x );
float nearbyintf( float x );
long double nearbyintl( long double x );
```

```cpp
float nearbyint( float x ); //C++ only
long double nearbyint( long double x ); //C++ only
```

### <a name="parameters"></a>Parametry

*x*<br/>
Hodnota, která má být zaokrouhlena.

## <a name="return-value"></a>Návratová hodnota

V případě úspěchu vrátí *x*, zaokrouhlené na nejbližší celé číslo, pomocí aktuálního formátu zaokrouhlení, jak je uvedeno v [fegetround](fegetround-fesetround2.md). V opačném případě funkce může vracet jednu z následujících hodnot:

|Problém|vrátit|
|-----------|------------|
|*x* = ± nekonečno|± Nekonečno, nezměněno|
|*x* = ±0|± 0, nezměněno|
|*x* = NaN|NaN|

Chyby nejsou hlášeny prostřednictvím [_matherr](matherr.md); Konkrétně tato funkce neoznamuje žádné **FE_INEXACT** výjimky.

## <a name="remarks"></a>Poznámky

Hlavním rozdílem mezi touto funkcí a [isknout](rint-rintf-rintl.md) je, že tato funkce nevyvolává nepřesnou výjimku s plovoucí desetinnou čárkou.

Vzhledem k tomu, že maximální počet hodnot s plovoucí desetinnou čárkou jsou přesná celá čísla, nebude tato funkce nikdy přeplněna sebou; místo toho může výstup přetečení hodnoty vrácenou v závislosti na verzi používané funkce.

C++umožňuje přetížení, takže můžete volat přetížení **nearbyint –** , která přebírají a vracejí parametry **float** nebo **Long** **Double** . V programu v jazyce C **nearbyint –** vždy přebírá dvě hodnoty Double a vrátí hodnotu Double.

## <a name="requirements"></a>Požadavky

|Funkce|Hlavička jazyka C|C++hlaviček|
|--------------|--------------|------------------|
|**nearbyint –** , **nearbyintf –** , **nearbyintl**|\<Math. h >|\<cmath > nebo \<Math. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Abecední seznam odkazů na funkce](crt-alphabetical-function-reference.md)<br/>
[Podpora matematických a plovoucích bodů](../floating-point-support.md)<br/>
