---
title: nearbyint, nearbyintf, nearbyintl
ms.date: 04/05/2018
apiname:
- nearbyint
- nearbyintf
- nerabyintl
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
ms.openlocfilehash: 4a36bddb28db9fb4c5809432dfaef9ca3ece4328
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50668309"
---
# <a name="nearbyint-nearbyintf-nearbyintl"></a>nearbyint, nearbyintf, nearbyintl

Zaokrouhlí zadanou hodnotu s plovoucí desetinnou čárkou na celá čísla a vrátí tuto hodnotu ve formátu s plovoucí desetinnou čárkou.

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
Hodnota má být zaokrouhleno.

## <a name="return-value"></a>Návratová hodnota

Pokud je úspěšná, vrátí *x*, zaokrouhlený na nejbližší celé číslo pomocí aktuální formát zaokrouhlení podle [fegetround](fegetround-fesetround2.md). V opačném případě funkce může vrátit jednu z následujících hodnot:

|Problém|Vrátí|
|-----------|------------|
|*x* = ±INFINITY|±INFINITY ponechat beze změny|
|*x* = ±0|±0 ponechat beze změny|
|*x* = NaN|NaN|

Nejsou hlášeny chyby prostřednictvím [_matherr](matherr.md); konkrétně, tato funkce nehlásí žádné **FE_INEXACT** výjimky.

## <a name="remarks"></a>Poznámky

Hlavní rozdíl mezi touto funkcí a [rint](rint-rintf-rintl.md) je, že tato funkce nevyvolá nepřesné výjimky s plovoucí desetinnou čárkou bodu.

Protože maximálních hodnot s plovoucí desetinnou čárkou jsou přesné celých čísel, tato funkce se nikdy přetečení samostatně; Místo toho výstup může přetéci vrácené hodnoty, podle toho, kterou verzi funkce použijete.

Jazyk C++ umožňuje přetížení, takže můžete volat přetížení **nearbyint –** , která používají a vrací **float** nebo **dlouhé** **double** parametry. V programu jazyka C **nearbyint –** vždy převezme dvě double hodnoty a vrátí hodnotu double.

## <a name="requirements"></a>Požadavky

|Funkce|Záhlaví C|Hlaviček jazyka C++|
|--------------|--------------|------------------|
|**nearbyint –**, **nearbyintf –**, **nearbyintl**|\<Math.h >|\<cmath > nebo \<math.h >|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Abecední seznam odkazů na funkce](crt-alphabetical-function-reference.md)<br/>
[Matematické a podpora plovoucí desetinné čárky](../floating-point-support.md)<br/>
