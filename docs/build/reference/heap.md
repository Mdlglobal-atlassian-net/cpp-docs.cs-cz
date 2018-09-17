---
title: -HALDY | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /heap
dev_langs:
- C++
helpviewer_keywords:
- heap allocation, setting heap size
- HEAP editbin option
- -HEAP editbin option
- /HEAP editbin option
ms.assetid: 6ce759b5-75b7-44ff-a5fd-3a83a0ba9a48
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 22698760ba23dc60b64002f0f728bb7a036f6731
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45699813"
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

## <a name="see-also"></a>Viz také

[EDITBIN – možnosti](../../build/reference/editbin-options.md)