---
title: "Pseudocíle | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- makefiles, pseudotargets
- pseudotargets and NMAKE
- NMAKE program, pseudotargets
- timestamps, makefile pseudotargets
- NMAKE program, targets
ms.assetid: c8c479dc-0129-4186-8366-bc6251f2b494
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: b018cd586e48f344b93b31571ba60ae9982ad4fe
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="pseudotargets"></a>Pseudocíle
Pseudotarget je štítek použít místo název souboru na řádku závislostí. Je interpretován jako soubor, který neexistuje a proto je zastaralý. NMAKE předpokládá, že časové razítko pseudotarget je nejnovější všechny jeho závislé objekty. Pokud má žádné závislé objekty, se předpokládá, že aktuální čas. Pokud pseudotarget se používá jako cíl, jsou vždy provádět její příkazy. Pseudotarget, použít jako závislé musí zobrazit i jako cíl v jiné závislostí. Tuto závislost však nemusí mít blok příkazů.  
  
 Názvy pseudotarget podle pravidla syntaxe názvu souboru pro cíle. Ale pokud název nemá rozšíření (to znamená, neobsahuje období), to může být vyšší než 8 znaků limit pro názvy souborů a může být až 256 znaků.  
  
## <a name="see-also"></a>Viz také  
 [Cíle](../build/targets.md)