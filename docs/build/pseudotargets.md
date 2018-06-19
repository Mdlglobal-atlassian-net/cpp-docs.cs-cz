---
title: Pseudocíle | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- makefiles, pseudotargets
- pseudotargets and NMAKE
- NMAKE program, pseudotargets
- timestamps, makefile pseudotargets
- NMAKE program, targets
ms.assetid: c8c479dc-0129-4186-8366-bc6251f2b494
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 67dbc6ae3ad331ab3297b62d00044c3edf679994
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32368405"
---
# <a name="pseudotargets"></a>Pseudocíle
Pseudotarget je štítek použít místo název souboru na řádku závislostí. Je interpretován jako soubor, který neexistuje a proto je zastaralý. NMAKE předpokládá, že časové razítko pseudotarget je nejnovější všechny jeho závislé objekty. Pokud má žádné závislé objekty, se předpokládá, že aktuální čas. Pokud pseudotarget se používá jako cíl, jsou vždy provádět její příkazy. Pseudotarget, použít jako závislé musí zobrazit i jako cíl v jiné závislostí. Tuto závislost však nemusí mít blok příkazů.  
  
 Názvy pseudotarget podle pravidla syntaxe názvu souboru pro cíle. Ale pokud název nemá rozšíření (to znamená, neobsahuje období), to může být vyšší než 8 znaků limit pro názvy souborů a může být až 256 znaků.  
  
## <a name="see-also"></a>Viz také  
 [Cíle](../build/targets.md)