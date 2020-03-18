---
title: Matematické konstanty
ms.date: 11/04/2016
f1_keywords:
- c.constants.math
helpviewer_keywords:
- M_PI constant
- M_PI_2 constant
- math constants
- M_2_PI constant
- M_1_PI constant
- M_E constant
- USE_MATH_DEFINES constant
- M_LOG2E constant
- M_LOG10E constant
- M_LN10 constant
- M_SQRT1_2 constant
- _USE_MATH_DEFINES constant
- M_PI_4 constant
- constants, math
- M_2_SQRTPI constant
- M_SQRT2 constant
- M_LN2 constant
ms.assetid: db533c3f-6ae8-4520-9d35-c8fabbef3529
ms.openlocfilehash: 156e4df4bcd4be457f2d14e7e5f5531d93d642be
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79438262"
---
# <a name="math-constants"></a>Matematické konstanty

## <a name="syntax"></a>Syntaxe

```
#define _USE_MATH_DEFINES // for C++
#include <cmath>

#define _USE_MATH_DEFINES // for C
#include <math.h>
```

## <a name="remarks"></a>Poznámky

Následující symboly jsou definovány pro hodnoty jejich uvedených výrazů:

|Písmeno|Výraz|Hodnota|
|------------|----------------|-----------|
|M_E|e|2.71828182845904523536|
|M_LOG2E|log2 – (e)|1.44269504088896340736|
|M_LOG10E|log10 – (e)|0.434294481903251827651|
|M_LN2|ln(2)|0.693147180559945309417|
|M_LN10|ln(10)|2.30258509299404568402|
|M_PI|π|3.14159265358979323846|
|M_PI_2|2|1.57079632679489661923|
|M_PI_4|PI/4|0.785398163397448309616|
|M_1_PI|1/PI|0.318309886183790671538|
|M_2_PI|2/PI|0.636619772367581343076|
|M_2_SQRTPI|2/sqrt(pi)|1.12837916709551257390|
|M_SQRT2|SQRT (2)|1.41421356237309504880|
|M_SQRT1_2|1/odmocnina (2)|0.707106781186547524401|

Matematické konstanty nejsou definovány Standard C/C++. Chcete-li je použít, je nutné nejprve definovat `_USE_MATH_DEFINES` a pak zahrnout cmath nebo Math. h.

Soubor ATLComTime. h zahrnuje Math. h, pokud je projekt sestaven v režimu vydání. Použijete-li jednu nebo více matematických konstant v projektu, které také obsahují ATLComTime. h, je nutné definovat `_USE_MATH_DEFINES` před zahrnutím ATLComTime. h.

## <a name="see-also"></a>Viz také

[Globální konstanty](../c-runtime-library/global-constants.md)
