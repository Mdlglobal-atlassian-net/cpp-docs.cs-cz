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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 92e3a744ef8069d45733c06b7a2681905c3eab55
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338592"
---
# <a name="nearbyint-nearbyintf-nearbyintl"></a>nearbyint, nearbyintf, nearbyintl

Zaokrouhlí zadanou hodnotu s plovoucí desetinnou desetinnou hodnotou na celé číslo a vrátí tuto hodnotu ve formátu s plovoucí desetinnou táhou.

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

*X*<br/>
Hodnota, která se má zaokrouhlit.

## <a name="return-value"></a>Návratová hodnota

Pokud je úspěšná, vrátí *x*, zaokrouhlená na nejbližší celé číslo, pomocí aktuálního formátu zaokrouhlení, jak je uvedeno [fegetround](fegetround-fesetround2.md). V opačném případě může funkce vrátit jednu z následujících hodnot:

|Problém|Vrátit|
|-----------|------------|
|*x* = ±NEKONEČNO|±INFINITY, nezměněno|
|*x* = ±0|±0, nezměněno|
|*x* = NaN|Není číslo|

Chyby nejsou hlášeny prostřednictvím [_matherr](matherr.md); konkrétně tato funkce nehlásí žádné **FE_INEXACT** výjimky.

## <a name="remarks"></a>Poznámky

Hlavní rozdíl mezi touto funkcí a [oplachem](rint-rintf-rintl.md) je, že tato funkce nevyvolá nepřesnou výjimku s plovoucí desetinnou desetinnou desetinnou desetinnou desetinnou.

Vzhledem k tomu, že maximální hodnoty s plovoucí desetinnou desetinnou desetinnou hodnotou jsou přesná celá čísla, tato funkce nikdy přetečení sama o sobě; místo toho výstup může přetečení vrácené hodnoty, v závislosti na verzi funkce, kterou používáte.

C++ umožňuje přetížení, takže můžete volat přetížení **nearint,** které trvat a vrátit **float** nebo **dlouhé** **dvojité** parametry. V programu C **nearint** vždy trvá dvě dvojité hodnoty a vrátí dvojitou hodnotu.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Funkce|Hlavička C|Hlavička C++|
|--------------|--------------|------------------|
|**nearbyint**, **nearbyintf**, **nearbyintl**|\<math.h>|\<cmath> \<nebo math.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Abecední seznam odkazů na funkce](crt-alphabetical-function-reference.md)<br/>
[Podpora matematiky a plovoucí desetinné hodnoty](../floating-point-support.md)<br/>
