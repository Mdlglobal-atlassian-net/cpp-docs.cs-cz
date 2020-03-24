---
title: Závažná chyba kompilátoru prostředků RW1025
ms.date: 11/04/2016
f1_keywords:
- RW1025
helpviewer_keywords:
- RW1025
ms.assetid: 561a02af-e7e0-442a-8ad3-a00b2ca1b62e
ms.openlocfilehash: 9b6697dff0a445cc342f30d08bd79822b02df7b8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80172721"
---
# <a name="resource-compiler-fatal-error-rw1025"></a>Závažná chyba kompilátoru prostředků RW1025

Nedostatek paměti haldy

Vyhledejte rezidentní software v paměti, který může zabírat příliš mnoho místa. Zjistěte, kolik paměti máte, pomocí programu CHKDSK.

Pokud vytváříte rozsáhlý soubor prostředků, rozdělte skript prostředků do dvou souborů. Po vytvoření dvou souborů. res použijte příkazový řádek MS-DOS k jejich vzájemnému připojení:

```
copy first.res /b + second.res /b full.res
```
