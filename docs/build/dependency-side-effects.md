---
title: "Vedlejší efekty závislostí | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- dependencies, side effects
- NMAKE program, dependents
ms.assetid: d4e8db25-fdc0-4d73-81ec-1538f2e1b3e8
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 9d19426a34620cfdd14b426b94757715ca2d1cbd
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="dependency-side-effects"></a>Vedlejší efekty závislostí
Pokud cíl je definován s dvojtečkou (:) dvou řádcích závislostí v různých umístěních, a pokud příkazy se zobrazí po pouze jeden řádek, interpretuje NMAKE závislosti, jako kdyby přiléhající nebo kombinovaná. Ho nevyvolá pravidlo odvození pro závislostí, který nemá žádné příkazy, ale místo toho předpokládá, že závislosti patří do jedné popis bloku a provede příkazy zadané s další závislosti. Například tato sada pravidel:  
  
```Output  
bounce.exe : jump.obj  
   echo Building bounce.exe...  
  
bounce.exe : up.obj  
```  
  
 vyhodnotí jako tento:  
  
```Output  
bounce.exe : jump.obj up.obj  
   echo Building bounce.exe...  
```  
  
 Tento efekt nedojde, pokud dvě dvojtečky (`::`) se používá. Například tato sada pravidel:  
  
```Output  
bounce.exe :: jump.obj  
   echo Building bounce.exe...  
  
bounce.exe :: up.obj  
```  
  
 vyhodnotí jako tento:  
  
```Output  
bounce.exe : jump.obj  
   echo Building bounce.exe...  
  
bounce.exe : up.obj  
# invokes an inference rule  
```  
  
## <a name="see-also"></a>Viz také  
 [Cíle](../build/targets.md)