---
title: /STACK
ms.date: 11/04/2016
f1_keywords:
- /stack
helpviewer_keywords:
- -STACK editbin option
- STACK editbin option
- stack, setting size
- /STACK editbin option
ms.assetid: a39bcff0-c945-4355-80cc-8e4f24a5f142
ms.openlocfilehash: 6f30877800d4597054601f7459df88c78193fd3c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62318495"
---
# <a name="stack"></a>/STACK

```
/STACK:reserve[,commit]
```

## <a name="remarks"></a>Poznámky

Tato možnost nastaví velikost zásobníku v bajtech a přebírá argumenty v zápisu jazyka C nebo decimal. Možnost/Stack se vztahuje pouze na spustitelný soubor.

*Rezervovat* argument určuje celkové přidělení zásobníku ve virtuální paměti. Editbin – zaokrouhlí nahoru zadanou hodnotu do nejbližší 4 bajty.

Volitelný `commit` argument podléhá interpretaci operačního systému. V systému Windows NT, Windows 95 a Windows 98 `commit` určuje množství fyzické paměti do okamžiku přidělit. Potvrzená virtuální paměť rezervuje místo ve stránkovacím souboru. Vyšší `commit` hodnotu šetří čas, kdy aplikace potřebuje více místa v zásobníku, ale zvyšuje požadavky na paměť a případně čas spuštění.

## <a name="see-also"></a>Viz také:

[EDITBIN – možnosti](editbin-options.md)
