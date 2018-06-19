---
title: nearbyint – nearbyintf –, nearbyintl | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- nearbyint function
- nearbyintf function
- nearbyintl function
ms.assetid: dd39cb68-96b0-434b-820f-6ff2ea65584f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2362a68bf73a370f2fdf8eaa5ecb18b0a08bfaad
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32403232"
---
# <a name="nearbyint-nearbyintf-nearbyintl"></a>nearbyint, nearbyintf, nearbyintl

Zaokrouhlí číslo s plovoucí desetinnou čárkou zadanou hodnotu na celé číslo a vrátí tuto hodnotu ve formátu s plovoucí desetinnou čárkou.

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
Hodnota, která má být zaokrouhleno.

## <a name="return-value"></a>Návratová hodnota

V případě úspěchu vrátí *x*, zaokrouhleno na nejbližší celé číslo ve formátu aktuální zaokrouhlení vykazované [fegetround](fegetround-fesetround2.md). Funkce, jinak může vrátit jednu z následujících hodnot:

|Problém|Vrátí|
|-----------|------------|
|*x* = ±INFINITY|±INFINITY, ponechat beze změny|
|*x* = ±0|±0, ponechat beze změny|
|*x* = NaN.|NaN|

Nejsou chyby nahlášené prostřednictvím [_matherr –](matherr.md); konkrétně tato funkce nehlásí žádné **FE_INEXACT** výjimky.

## <a name="remarks"></a>Poznámky

Hlavní rozdíl mezi tato funkce a [tisknout](rint-rintf-rintl.md) je, že tato funkce nevyvolá nepřesný plovoucí výjimka bodu.

Protože jsou maximální hodnoty s plovoucí desetinnou čárkou přesný celá čísla, tato funkce se nikdy přetečení samostatně; Místo toho může výstupu přetečení návratovou hodnotu, podle toho, kterou verzi funkce používáte.

C++ umožňuje přetížení, takže můžete volat přetížení **nearbyint –** , přijmout a vrátit **float** nebo **dlouho** **dvojité** parametry. V programu C **nearbyint –** vždy má dvě hodnoty double a vrátí hodnotu double.

## <a name="requirements"></a>Požadavky

|Funkce|Hlavička C|Hlavička C++|
|--------------|--------------|------------------|
|**nearbyint –**, **nearbyintf –**, **nearbyintl**|\<Math.h >|\<cmath – > nebo \<math.h >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Abecední seznam odkazů na funkce](crt-alphabetical-function-reference.md)<br/>
[Matematické a podpora plovoucí desetinné čárky](../floating-point-support.md)<br/>
