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
ms.openlocfilehash: 24470c00afce54bab0a15dd08e03cef6dfee63fc
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57415250"
---
# <a name="heap"></a>/HEAP

Nastaví velikost haldy v bajtech. Tato možnost platí pouze pro spustitelné soubory.

```

/HEAP:
reserve[,commit]
```

## <a name="remarks"></a>Poznámky

`reserve` Argument určuje celkový počet počáteční haldy ve virtuální paměti. Ve výchozím nastavení je velikost haldy 1 MB. [Editbin – referenční dokumentace](../../build/reference/editbin-reference.md) zaokrouhluje nahoru na nejbližší násobek 4 bajty zadanou hodnotu.

Volitelný `commit` argument podléhá interpretaci operačního systému. V operačním systému Windows určuje počáteční velikost fyzické paměti k přidělení a množství další paměti k přidělení musí být rozbaleném haldy. Potvrzená virtuální paměť rezervuje místo ve stránkovacím souboru. Vyšší `commit` hodnota umožňuje systému přidělení paměti, méně často, když aplikace potřebuje více místa v haldě, ale zvyšuje požadavky na paměť a případně doba spuštění aplikace. `commit` Hodnota musí být menší než nebo rovna hodnotě `reserve` hodnotu.

Zadejte `reserve` a `commit` hodnoty v desítkové nebo šestnáctkové nebo osmičkové soustavě zápisu jazyka. Například může být zadána hodnota 1 MB jako 1048576 v desítkové soustavě, nebo jako 0x100000 v šestnáctkové soustavě nebo jako 04000000 v osmičkové.

## <a name="see-also"></a>Viz také:

[EDITBIN – možnosti](../../build/reference/editbin-options.md)
