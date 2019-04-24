---
title: Příkazy v souboru pravidel
ms.date: 11/04/2016
helpviewer_keywords:
- commands, makefiles
ms.assetid: 8085517e-42f4-493b-b8f8-44311fc08c64
ms.openlocfilehash: fcb8737070931cf95d7bfb3971a84e22c7ad70a4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62294392"
---
# <a name="commands-in-a-makefile"></a>Příkazy v souboru pravidel

Popis bloku nebo odvození pravidlo určuje blok příkazů ke spuštění, pokud závislost je zastaralý. NMAKE zobrazí každý příkaz před spuštěním, není-li /S, **. TICHÉ**, **! CMDSWITCHES**, nebo \@ se používá. NMAKE hledá odpovídající pravidlo pro odvození, pokud blok popis nenásleduje blok příkazů.

Blok příkazů obsahuje jeden nebo více příkazů, každou na samostatném řádku. Žádné prázdný řádek mohou objevit mezi závislost nebo pravidlo a blok příkazů. Můžete se však zobrazí řádek, který obsahuje pouze mezery nebo tabulátory; Tento řádek je interpretován jako prázdný příkaz, a nedojde k žádné chybě. Prázdné řádky jsou povolené mezi příkazové řádky.

Příkazový řádek, který začíná mezery nebo tabulátory. Zpětné lomítko (\) následované znakem je interpretován jako mezera v příkazu; Pokračujte na další řádek příkazu použijte zpětné lomítko na konci řádku. NMAKE interpretuje zpětné lomítko doslova Pokud jakýkoli jiný znak, včetně mezera nebo tabulátor, následuje za zpětným lomítkem.

Příkaz předchází středníkem (;) se může objevit v řádku nebo odvozená pravidla závislostí, zda blok příkazů následující:

```
project.obj : project.c project.h ; cl /c project.c
```

## <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací?

[Modifikátory příkazů](command-modifiers.md)

[Syntaxe částí názvu souboru](filename-parts-syntax.md)

[Vložené soubory v souboru pravidel](inline-files-in-a-makefile.md)

## <a name="see-also"></a>Viz také:

[NMAKE – referenční zdroje](nmake-reference.md)
