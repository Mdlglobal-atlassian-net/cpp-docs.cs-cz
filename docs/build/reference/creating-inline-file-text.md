---
title: Vytvořit vložený text souboru
ms.date: 11/04/2016
helpviewer_keywords:
- inline files, creating text
- NMAKE program, inline files
- text, inline file
ms.assetid: b8a332ed-8244-4ff8-89e6-029d7f659725
ms.openlocfilehash: a45aa526ca99af93cda86a2a8e0580d4d036ca6d
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57823014"
---
# <a name="creating-inline-file-text"></a>Vytvořit vložený text souboru

Vložené soubory jsou dočasné nebo trvalé.

## <a name="syntax"></a>Syntaxe

```
inlinetext
.
.
.
<<[KEEP | NOKEEP]
```

## <a name="remarks"></a>Poznámky

Zadejte *inlinetext* na prvním řádku po příkazu. Konec pomocí hranatých závorkách (<<) na začátku samostatný řádek. Tento soubor obsahuje všechny *inlinetext* před oddělovací závorky. *Inlinetext* může mít tento počet rozšíření maker a nahrazení, ale ne direktivy nebo komentáře souboru pravidel. Mezery, tabulátory a znaky nového řádku jsou zpracovány doslova.

Dočasný soubor existuje po dobu trvání relace a můžete znovu použít další příkazy. Zadejte **zachovat** za uzavírací hranaté závorce úhel zachovat soubor po relaci NMAKE; soubor bez názvu se zachovají na disku s vygenerovaný název souboru. Zadejte **NOKEEP** nebo nic pro dočasný soubor. **ZACHOVAT** a **NOKEEP** nejsou velká a malá písmena.

## <a name="see-also"></a>Viz také:

[Soubory vložené do souboru pravidel](inline-files-in-a-makefile.md)
