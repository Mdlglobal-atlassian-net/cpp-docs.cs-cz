---
title: Maximální délka řetězce
ms.date: 11/04/2016
helpviewer_keywords:
- lengths, strings
- string length, maximum
- maximum string length
- strings [C++], length
ms.assetid: 99a80e4a-6212-47b7-a6bd-bdf99bd44928
ms.openlocfilehash: f2e5461c433a0d195682c1a0f4312a71a8ff5032
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50483981"
---
# <a name="maximum-string-length"></a>Maximální délka řetězce

**Specifické pro Microsoft**

Kompatibilita se standardem ANSI vyžaduje, aby kompilátor v textovém literálu po zřetězení přijal až 509 znaků. Maximální povolená délka textového literálu v jazyce Microsoft C je přibližně 2 048 bajtů. Avšak pokud se textový literál skládá z částí uzavřených v uvozovkách, preprocesor spojí tyto části do jednoho řetězce a pro každý zřetězený řádek přidá k celkovému počtu bajtů dodatečný bajt.

Například si představte, že se řetězec skládá ze 40 řádků s 50 znaky na řádek (2 000 znaků) a jednoho řádku se 7 znaky a každý řádek je ohraničen uvozovkami. To přidá až 2 007 bajtů plus jeden bajt pro ukončující znak null, celkem 2 008 bajtů. Při zřetězení je pro každý z prvních 40 řádků přidán jeden znak navíc. To je celkem 2 048 bajtů. Všimněte si, ale, že pokud řádek pokračování (\\) se používají místo uvozovek, nepřidá preprocesor pro každý řádek znak navíc.

Zatímco jednotlivé řetězce v uvozovkách nesmějí být delší než 2 048 bajtů, pomocí zřetězení řetězců lze sestavit textový literál o velikosti zhruba 65 535 bajtů.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také

[Textové literály jazyka C](../c-language/c-string-literals.md)