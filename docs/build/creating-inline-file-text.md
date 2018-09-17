---
title: Vytvoření textu vloženého souboru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- inline files, creating text
- NMAKE program, inline files
- text, inline file
ms.assetid: b8a332ed-8244-4ff8-89e6-029d7f659725
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ce0a345c6c2f48d3d5c2e6fb9d9cfc2a5c03e4ed
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45720912"
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

## <a name="see-also"></a>Viz také

[Soubory vložené do souboru pravidel](../build/inline-files-in-a-makefile.md)