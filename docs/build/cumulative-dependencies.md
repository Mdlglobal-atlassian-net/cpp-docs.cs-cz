---
title: "Kumulativní závislosti | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- dependencies, cumulative
- cumulative dependencies in NMAKE
- dependencies
ms.assetid: fa6dd777-80b8-437d-87a7-aec0ed818a49
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: f2fd356ae37eda8820e3a6e0e31a8cecde8d3929
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="cumulative-dependencies"></a>Kumulativní závislosti
Závislosti jsou kumulativní v bloku popis, pokud se opakuje cíl.  
  
 Například tato sada pravidel,  
  
```Output  
bounce.exe : jump.obj  
bounce.exe : up.obj  
   echo Building bounce.exe...  
```  
  
 vyhodnotí jako tento:  
  
```Output  
bounce.exe : jump.obj up.obj  
   echo Building bounce.exe...  
```  
  
 Více cílů ve více řádků závislostí v jednom popis bloku se vyhodnocují jako kdyby každý byly zadány v samostatných popis bloku, ale cíle, které nejsou na posledním řádku závislostí nepoužívejte příkazy bloku. NMAKE se pokouší použít pravidlo odvození týkající se těchto cílů.  
  
 Například tato sada pravidel,  
  
```Output  
leap.exe bounce.exe : jump.obj  
bounce.exe climb.exe : up.obj  
   echo Building bounce.exe...  
```  
  
 vyhodnotí jako tento:  
  
```Output  
  
leap.exe : jump.obj  
# invokes an inference rule  
bounce.exe : jump.obj up.obj  
   echo Building bounce.exe...  
climb.exe : up.obj  
   echo Building bounce.exe...  
```  
  
## <a name="see-also"></a>Viz také  
 [Cíle](../build/targets.md)