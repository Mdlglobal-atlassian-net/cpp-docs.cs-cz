---
title: "Operátor sekvenčního vyhodnocení | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- operators [C++], sequential-evaluation
- sequential-evaluation operator
- comma operator
ms.assetid: 587514f4-c8e2-44e9-81a8-7a553ce1453a
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: df14f32b8b51d8b74b56a697f3928ff8da485a5a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="sequential-evaluation-operator"></a>Operátor sekvenčního vyhodnocení
Operátor sekvenčního vyhodnocení, označované taky jako "operátor čárka," vyhodnotí jeho dva operandy postupně zleva doprava.  
  
## <a name="syntax"></a>Syntaxe  
 *výraz*:  
 *přiřazení – výraz*  
  
 *výraz***,***přiřazení – výraz*   
  
 Levý operand operátor sekvenčního vyhodnocení budou vyhodnocené jako `void` výraz. Výsledek operace má stejnou hodnotu a typ jako pravý operand. Každý operand můžou být jakéhokoli typu. Operátor sekvenčního vyhodnocení neprovede převody typů mezí jejími operandy, a zisk l hodnota. Po první operand, což znamená, že jsou všechny vedlejší účinky vyplývající z hodnocení levý operand dokončit před zahájením vyhodnocení pravý operand není bodu sekvence. V tématu [body sekvence](../c-language/c-sequence-points.md) Další informace.  
  
 Operátor sekvenčního vyhodnocení se obvykle používá k vyhodnocení, dvě nebo více výrazů v kontextech kde je povolen pouze jeden výraz.  
  
 Čárky lze použít jako oddělovače v některých kontextech. Ale musí být pozor, abyste nezaměnili použití čárky jako oddělovač s jeho použití jako operátor; používá dva se zcela liší.  
  
## <a name="example"></a>Příklad  
 Tento příklad ukazuje operátor sekvenčního vyhodnocení:  
  
```  
for ( i = j = 1; i + j < 20; i += i, j-- );  
```  
  
 V tomto příkladu každý operand **pro** příkaz na třetí výraz vyhodnocen nezávisle. Levý operand `i += i` vyhodnotí první; pak pravý operand `j--`, vyhodnotí.  
  
```  
func_one( x, y + 2, z );  
func_two( (x--, y + 2), z );  
```  
  
 Ve funkci volat na `func_one`, tři argumenty, oddělených čárkami, se předávají: `x`, `y + 2`, a `z`. Ve volání funkce `func_two` donutí závorky kompilátor interpretovat první čárku jako operátor sekvenčního vyhodnocení. Toto volání funkce předává do funkce `func_two` dva argumenty. Prvním argumentem je výsledek operace sekvenčního vyhodnocení `(x--, y + 2)`, který má hodnotu a typ výrazu `y + 2`, druhým argumentem je proměnná `z`.  
  
## <a name="see-also"></a>Viz také  
 [Operátor čárky:,](../cpp/comma-operator.md)