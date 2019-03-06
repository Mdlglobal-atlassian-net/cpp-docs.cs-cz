---
title: Příkazy v souboru pravidel
ms.date: 11/04/2016
helpviewer_keywords:
- commands, makefiles
ms.assetid: 8085517e-42f4-493b-b8f8-44311fc08c64
ms.openlocfilehash: 1fbaddef535ee1066c0723b5709ce2d55e67682e
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57419658"
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

[Modifikátory příkazů](../build/command-modifiers.md)

[Syntaxe částí názvu souboru](../build/filename-parts-syntax.md)

[Vložené soubory v souboru pravidel](../build/inline-files-in-a-makefile.md)

## <a name="see-also"></a>Viz také:

[NMAKE – referenční zdroje](../build/nmake-reference.md)
