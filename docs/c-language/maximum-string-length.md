---
title: Maximální délka řetězce | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- lengths, strings
- string length, maximum
- maximum string length
- strings [C++], length
ms.assetid: 99a80e4a-6212-47b7-a6bd-bdf99bd44928
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f95f4cb279c7e13d9500fbf5ce90a8ed82d55307
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32386100"
---
# <a name="maximum-string-length"></a>Maximální délka řetězce
**Konkrétní Microsoft**  
  
 Kompatibilita se standardem ANSI vyžaduje, aby kompilátor v textovém literálu po zřetězení přijal až 509 znaků. Maximální povolená délka textového literálu v jazyce Microsoft C je přibližně 2 048 bajtů. Avšak pokud se textový literál skládá z částí uzavřených v uvozovkách, preprocesor spojí tyto části do jednoho řetězce a pro každý zřetězený řádek přidá k celkovému počtu bajtů dodatečný bajt.  
  
 Například si představte, že se řetězec skládá ze 40 řádků s 50 znaky na řádek (2 000 znaků) a jednoho řádku se 7 znaky a každý řádek je ohraničen uvozovkami. To přidá až 2 007 bajtů plus jeden bajt pro ukončující znak null, celkem 2 008 bajtů. Při zřetězení je pro každý z prvních 40 řádků přidán jeden znak navíc. To je celkem 2 048 bajtů. Všimněte si, ale, že pokud řádek pokračování (\\) se používají místo dvojitých uvozovek preprocesor nepřidá znakem navíc pro každý řádek.  
  
 Zatímco jednotlivé řetězce v uvozovkách nesmějí být delší než 2 048 bajtů, pomocí zřetězení řetězců lze sestavit textový literál o velikosti zhruba 65 535 bajtů.  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Textové literály jazyka C](../c-language/c-string-literals.md)