---
title: "&lt;omezení&gt; | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- limits/std::<limits>
- <limits>
dev_langs: C++
helpviewer_keywords: limits header
ms.assetid: e07d6379-5b00-4a3d-a789-40d41538b59e
caps.latest.revision: "18"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: eace3f5dd5d0693f5cb42b32e4d2c8c52a5eddfe
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ltlimitsgt"></a>&lt;omezení&gt;
Definuje třídu šablony `numeric_limits` a dva výčty týkající se reprezentace plovoucí desetinné čárky a zaokrouhlení.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
#include <limits>  
  
```  
  
## <a name="remarks"></a>Poznámky  
 Explicitní specializací `numeric_limits` třída popisují mnoho vlastností základních typů, včetně znaku, celé číslo a typy s plovoucí desetinnou čárkou a `bool` , které jsou implementace definované než Pevná pravidly C++ jazyk. Vlastnosti popsané v \<omezení > zahrnují přesnost, minimální a maximální velikost reprezentace zaokrouhlení a signalizace typ chyby.  
  
### <a name="enumerations"></a>Výčty  
  
|||  
|-|-|  
|[float_denorm_style –](../standard-library/limits-enums.md#float_denorm_style)|Výčet popisuje různé metody, které můžete vybrat implementace pro představující hodnotu s plovoucí desetinnou čárkou nenormalizované – jeden příliš malá, aby představují jako normalizovanou hodnotu:|  
|[float_round_style –](../standard-library/limits-enums.md#float_round_style)|Výčet popisuje různé metody, které můžete vybrat implementace pro zaokrouhlení hodnotu s plovoucí desetinnou čárkou na celočíselnou hodnotu.|  
  
### <a name="classes"></a>Třídy  
  
|||  
|-|-|  
|[numeric_limits – třída](../standard-library/numeric-limits-class.md)|Šablony třídy popisuje aritmetické vlastnosti vestavěné číselné typy.|  
  
## <a name="see-also"></a>Viz také  
 [Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)   
 [Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)



