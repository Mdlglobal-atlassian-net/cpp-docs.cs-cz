---
title: Příkazy v souboru pravidel | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- commands, makefiles
ms.assetid: 8085517e-42f4-493b-b8f8-44311fc08c64
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 99e1eb5b4800ff1046ca60d4d4874d386809e2e0
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="commands-in-a-makefile"></a>Příkazy v souboru pravidel
Popis bloku nebo odvození pravidlo určuje blok příkazů ke spouštění, pokud závislost je zastaralý. NMAKE každý příkaz zobrazí před spuštěním, pokud /S, **. TICHOU**, **! Cmdswitches –**, nebo se používá @. NMAKE hledá odpovídající odvozené pravidlo, pokud blok popis nenásleduje blok příkazů.  
  
 Příkazy bloku obsahuje jeden nebo více příkazů, každou na samostatném řádku. Mezi závislosti nebo pravidla a příkazy bloku se může zobrazit žádné prázdný řádek. Může se však zobrazí řádek, který obsahuje pouze mezery ani karty; Tento řádek se interpretuje jako prázdný příkaz a nedojde k žádné chybě. Prázdné řádky nejsou povolené mezi příkazy na příkazových řádcích.  
  
 Příkazový řádek začíná mezery nebo karty. Zpětné lomítko (\) následuje znak nového řádku interpretována jako prostor v příkazu; použití zpětné lomítko na konci řádku pokračujte na další řádek příkaz. NMAKE interpretuje zpětné lomítko oznámena Pokud jiný znak, včetně místa nebo na kartě dodržuje zpětné lomítko.  
  
 Příkaz sebou středníkem (;) lze zobrazit na řádek nebo odvozená pravidla závislostí, jestli odpovídá blok příkazů:  
  
```  
project.obj : project.c project.h ; cl /c project.c  
```  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o?  
 [Modifikátory příkazů](../build/command-modifiers.md)  
  
 [Syntaxe částí názvu souboru](../build/filename-parts-syntax.md)  
  
 [Vložené soubory v souboru pravidel](../build/inline-files-in-a-makefile.md)  
  
## <a name="see-also"></a>Viz také  
 [NMAKE – referenční zdroje](../build/nmake-reference.md)