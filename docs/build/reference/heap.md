---
title: /HEAP
ms.date: 11/04/2016
f1_keywords:
- /heap
helpviewer_keywords:
- heap allocation, setting heap size
- HEAP editbin option
- -HEAP editbin option
- /HEAP editbin option
ms.assetid: 6ce759b5-75b7-44ff-a5fd-3a83a0ba9a48
ms.openlocfilehash: fcf557b467ba5bd04352ba2f2702659a1eb2948d
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57810351"
---
# <a name="heap"></a>/HEAP

Nastaví velikost haldy v bajtech. Tato možnost platí pouze pro spustitelné soubory.

```

/HEAP:
reserve[,commit]
```

## <a name="remarks"></a>Poznámky

`reserve` Argument určuje celkový počet počáteční haldy ve virtuální paměti. Ve výchozím nastavení je velikost haldy 1 MB. [Editbin – referenční dokumentace](editbin-reference.md) zaokrouhluje nahoru na nejbližší násobek 4 bajty zadanou hodnotu.

Volitelný `commit` argument podléhá interpretaci operačního systému. V operačním systému Windows určuje počáteční velikost fyzické paměti k přidělení a množství další paměti k přidělení musí být rozbaleném haldy. Potvrzená virtuální paměť rezervuje místo ve stránkovacím souboru. Vyšší `commit` hodnota umožňuje systému přidělení paměti, méně často, když aplikace potřebuje více místa v haldě, ale zvyšuje požadavky na paměť a případně doba spuštění aplikace. `commit` Hodnota musí být menší než nebo rovna hodnotě `reserve` hodnotu.

Zadejte `reserve` a `commit` hodnoty v desítkové nebo šestnáctkové nebo osmičkové soustavě zápisu jazyka. Například může být zadána hodnota 1 MB jako 1048576 v desítkové soustavě, nebo jako 0x100000 v šestnáctkové soustavě nebo jako 04000000 v osmičkové.

## <a name="see-also"></a>Viz také:

[EDITBIN – možnosti](editbin-options.md)
