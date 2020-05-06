---
title: Maximální délka řetězce
ms.date: 11/04/2016
helpviewer_keywords:
- lengths, strings
- string length, maximum
- maximum string length
- strings [C++], length
ms.assetid: 99a80e4a-6212-47b7-a6bd-bdf99bd44928
ms.openlocfilehash: 650088249e4c6abd515c29b873a9f09dc1d2a60a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62232875"
---
# <a name="maximum-string-length"></a>Maximální délka řetězce

**Specifické pro Microsoft**

Kompatibilita se standardem ANSI vyžaduje, aby kompilátor v textovém literálu po zřetězení přijal až 509 znaků. Maximální povolená délka textového literálu v jazyce Microsoft C je přibližně 2 048 bajtů. Avšak pokud se textový literál skládá z částí uzavřených v uvozovkách, preprocesor spojí tyto části do jednoho řetězce a pro každý zřetězený řádek přidá k celkovému počtu bajtů dodatečný bajt.

Například si představte, že se řetězec skládá ze 40 řádků s 50 znaky na řádek (2 000 znaků) a jednoho řádku se 7 znaky a každý řádek je ohraničen uvozovkami. To přidá až 2 007 bajtů plus jeden bajt pro ukončující znak null, celkem 2 008 bajtů. Při zřetězení je pro každý z prvních 40 řádků přidán jeden znak navíc. To je celkem 2 048 bajtů. Všimněte si však, že pokud jsou použity řádky pokračování\\() místo dvojitých uvozovek, preprocesor nepřidá znak navíc pro každý řádek.

Zatímco jednotlivé řetězce v uvozovkách nesmějí být delší než 2 048 bajtů, pomocí zřetězení řetězců lze sestavit textový literál o velikosti zhruba 65 535 bajtů.

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[Textové literály jazyka C](../c-language/c-string-literals.md)
