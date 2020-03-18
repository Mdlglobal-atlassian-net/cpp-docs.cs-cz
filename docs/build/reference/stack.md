---
title: /STACK
ms.date: 11/04/2016
f1_keywords:
- /stack_editbin
helpviewer_keywords:
- -STACK editbin option
- STACK editbin option
- stack, setting size
- /STACK editbin option
ms.assetid: a39bcff0-c945-4355-80cc-8e4f24a5f142
ms.openlocfilehash: 63fcddec8ff8afd81084bb5a2786f394db594b07
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79438885"
---
# <a name="stack"></a>/STACK

```
/STACK:reserve[,commit]
```

## <a name="remarks"></a>Poznámky

Tato možnost nastaví velikost zásobníku v bajtech a převezme argumenty v desítkovém nebo jazykovém zápisu jazyka C. Možnost/STACK se vztahuje pouze na spustitelný soubor.

Argument *Reserve* Určuje celkové přidělení zásobníku ve virtuální paměti. NÁSTROJE EDITBIN zaokrouhlí zadanou hodnotu na nejbližší 4 bajty.

Volitelný `commit` argument podléhá interpretaci operačním systémem. V systémech Windows NT, Windows 95 a Windows 98 `commit` určuje velikost fyzické paměti, která se má přidělit v daném čase. Potvrzená virtuální paměť rezervuje místo ve stránkovacím souboru. Vyšší hodnota `commit` šetří čas, když aplikace potřebuje více místa na zásobníku, ale zvyšuje požadavky na paměť a případně i čas spuštění.

## <a name="see-also"></a>Viz také

[EDITBIN – možnosti](editbin-options.md)
