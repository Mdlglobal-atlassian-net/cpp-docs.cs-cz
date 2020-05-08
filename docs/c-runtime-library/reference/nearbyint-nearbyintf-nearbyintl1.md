---
title: nearbyint, nearbyintf, nearbyintl
ms.date: 4/2/2020
api_name:
- nearbyint
- nearbyintf
- nearbyintl
- _o_nearbyint
- _o_nearbyintf
- _o_nearbyintl
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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: d9e7adb321d85c728c5185c1663fd7f945fc4a82
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82914568"
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

*znak*<br/>
Hodnota, která se má zaokrouhlit.

## <a name="return-value"></a>Návratová hodnota

V případě úspěchu vrátí *x*, zaokrouhlené na nejbližší celé číslo, pomocí aktuálního formátu zaokrouhlení, jak je uvedeno v [fegetround](fegetround-fesetround2.md). V opačném případě funkce může vracet jednu z následujících hodnot:

|Problém|Vrátit|
|-----------|------------|
|*x* = ± nekonečno|± Nekonečno, nezměněno|
|*x* = ± 0|± 0, nezměněno|
|*x* = NaN|Není číslo|

Chyby nejsou hlášeny prostřednictvím [_matherr](matherr.md); Konkrétně tato funkce neoznamuje žádné výjimky **FE_INEXACT** .

## <a name="remarks"></a>Poznámky

Hlavním rozdílem mezi touto funkcí a [isknout](rint-rintf-rintl.md) je, že tato funkce nevyvolává nepřesnou výjimku s plovoucí desetinnou čárkou.

Vzhledem k tomu, že maximální počet hodnot s plovoucí desetinnou čárkou jsou přesná celá čísla, nebude tato funkce nikdy přeplněna sebou; místo toho může výstup přetečení hodnoty vrácenou v závislosti na verzi používané funkce.

Jazyk C++ umožňuje přetížení, takže můžete volat přetížení **nearbyint –** , která přebírají a vracejí parametry **float** nebo **Long** **Double** . V programu v jazyce C **nearbyint –** vždy přebírá dvě hodnoty Double a vrátí hodnotu Double.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Funkce|Hlavička jazyka C|Hlavička C++|
|--------------|--------------|------------------|
|**nearbyint –**, **nearbyintf –**, **nearbyintl**|\<Math. h>|\<cmath> nebo \<Math. h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Abecední seznam odkazů na funkce](crt-alphabetical-function-reference.md)<br/>
[Podpora matematických a plovoucích bodů](../floating-point-support.md)<br/>
