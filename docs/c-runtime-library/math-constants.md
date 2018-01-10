---
title: "Matematické konstanty | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: c.constants
dev_langs: C++
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
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d68559e9248d7123d299f3bf5ee43a9fd05669dd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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
 Následující symboly jsou definovány pro hodnoty jejich označených výrazů:  
  
|Symbol|Výraz|Hodnota|  
|------------|----------------|-----------|  
|M_E –|e|2.71828182845904523536|  
|M_LOG2E –|log2(e)|1.44269504088896340736|  
|M_LOG10E –|LOG10(e)|0.434294481903251827651|  
|M_LN2 –|ln(2)|0.693147180559945309417|  
|M_LN10 –|: ln(10)|2.30258509299404568402|  
|M_PI –|platformy|3.14159265358979323846|  
|M_PI_2 –|pí/2|1.57079632679489661923|  
|M_PI_4 –|pí/4|0.785398163397448309616|  
|M_1_PI –|1/pi|0.318309886183790671538|  
|M_2_PI –|2/pi|0.636619772367581343076|  
|M_2_SQRTPI –|2/Sqrt(pi)|1.12837916709551257390|  
|M_SQRT2 –|Sqrt(2)|1.41421356237309504880|  
|M_SQRT1_2 –|1/Sqrt(2)|0.707106781186547524401|  
  
 Matematické konstanty nejsou definovány v standardní C/C++. Používat, je nutné nejprve definovat `_USE_MATH_DEFINES` a potom vložte cmath – nebo math.h.  
  
 Soubor ATLComTime.h zahrnuje math.h při sestavení projektu v režimu vydání. Pokud použijete jeden nebo více matematické konstanty v projektu, který také obsahuje ATLComTime.h, je nutné definovat `_USE_MATH_DEFINES` předtím, než zahrnete ATLComTime.h.  
  
## <a name="see-also"></a>Viz také  
 [Globální konstanty](../c-runtime-library/global-constants.md)