---
title: Odčítání (-) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- operators [C], subtraction
- subtraction operator, syntax
ms.assetid: 9cacba7d-20b3-4372-8a63-ba5d8ee64177
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 295c6bc33b42ed34fd476dbc72bec9dd398efa14
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="subtraction--"></a>Odčítání (-)
Operátor odčítání (**-**) odečítá Druhý operand od prvního. Oba operandy mohou být typy s plovoucí desetinnou čárkou nebo celočíselné typy, případně může být jeden operand ukazatel a druhý celé číslo.  
  
 Při odečtení dvou ukazatelů je rozdíl převeden na celočíselnou hodnotu se znaménkem vydělením rozdílu velikostí hodnoty typu, na který ukazatel odkazuje. Velikost celočíselné hodnoty je definován typ **ptrdiff_t –** v standardní zahrnout souboru STDDEF. H. Výsledek představuje počet míst paměti tohoto typu mezi dvěma adresami. Výsledek je pouze zaručena smysl pro dva elementy stejného pole, jak je popsáno v [aritmetika ukazatele](../c-language/pointer-arithmetic.md).  
  
 Když celočíselnou hodnotu je odečten od hodnota ukazatele, operátor odčítání převede na celé číslo (*i*) vynásobením velikost hodnoty, které řeší ukazatele. Po převodu celočíselná hodnota představuje *i* paměti pozice, kdy každý pozice má délku určeného je ukazatel typu. Když převedený celočíselná hodnota je odečten od hodnota ukazatele, výsledkem je, adresa paměti *i* pozic před původní adresu. Nový ukazatel odkazuje na hodnotu typu odkazovaného původní hodnotou ukazatele.  
  
## <a name="see-also"></a>Viz také  
 [Sčítací operátory jazyka C](../c-language/c-additive-operators.md)