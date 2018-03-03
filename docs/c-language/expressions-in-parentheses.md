---
title: "Výrazy v závorkách | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- parentheses
- expression evaluation, evaluation order
- expressions [C++], evaluating
- parentheses, expressions
ms.assetid: b8636147-6982-408c-9e64-29e40678ee43
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c09209a323a06f883a54e7ecaec17c55a3bc6205
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="expressions-in-parentheses"></a>Výrazy v závorkách
Libovolný operand je možné uzavřít do uvozovek, aniž by se změnil typ nebo hodnota uzavřeného výrazu. Například ve výrazu:  
  
```  
( 10 + 5 ) / 5  
```  
  
 závorky `10 + 5` znamenají, že hodnota `10 + 5` je první vyhodnocen a začne levý operand rozdělení (**/**) operátor. Výsledek `( 10 + 5 ) / 5` je 3. Bez závorek by byl výraz `10 + 5 / 5` vyhodnocen jako 11.  
  
 Přestože závorky mají vliv na způsob, jakým jsou seskupeny operandy ve výrazu, nemohou zaručit konkrétní pořadí vyhodnocení ve všech případech. Například ani závorky, ani seskupení zleva doprava v následujícím výrazu nezaručují, jaké hodnoty nabyde proměnná `i` v podřízených výrazech:  
  
```  
( i++ +1 ) * ( 2 + i )  
```  
  
 Kompilátoru je umožněno vyhodnocení obou stran násobení v libovolném pořadí. Je-li počáteční hodnota proměnné `i` nula, může být celý výraz vyhodnocen jako jeden z těchto dvou příkazů:  
  
```  
( 0 + 1 + 1 ) * ( 2 + 1 )   
( 0 + 1 + 1 ) * ( 2 + 0 )  
```  
  
 Výjimky vyplývající z vedlejší účinky, jsou popsané v [vedlejší účinky](../c-language/side-effects.md).  
  
## <a name="see-also"></a>Viz také  
 [Primární výrazy jazyka C](../c-language/c-primary-expressions.md)