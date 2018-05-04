---
title: Logické operátory jazyka C | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- logical operators, expression sequence points
- logical operators, C
- logical AND operator
- '|| operator'
- operators [C], logical
- short-circuit evaluation
- '&& operator'
- logical OR operator
ms.assetid: c0a4e766-ad56-4300-bf76-b28dc0e19b43
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3f92adbeab4175178be8f41a09c4455d8a581131
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="c-logical-operators"></a>Logické operátory jazyka C
Logické operátory provést logické- a (**&&**) a logické OR ( `||` ) operace.  
  
 **Syntaxe**  
  
 *logický a výraz*:  
 *Inkluzivní nebo výraz*  
  
 *logický a výraz***&&***(včetně) nebo výraz*   
  
 *logický výraz OR*:  
 *logické a – výraz*  
  
 *logický výraz OR***&#124;&#124;***logické a – výraz*   
  
 Logické operátory neprovádět obvyklé aritmetické převody. Místo toho vyhodnocují každý operand z hlediska jeho ekvivalenční na hodnotu 0. Výsledek logické operace je 0 nebo 1. Výsledný typ není `int`.  
  
 Logické operátory jazyka C jsou následující:  
  
|Operátor|Popis|  
|--------------|-----------------|  
|**&&**|Logické- a operátor vytvoří hodnotu 1, pokud oba operandy mít nenulové hodnoty. Pokud buď operand rovná 0, výsledkem je 0. Pokud první operand logickou- a operace se rovná 0, druhý operand, nebude hodnocen.|  
|`&#124;&#124;`|Operátor logického nebo provádí operaci (včetně) nebo na jeho operandy. Výsledkem je 0, pokud oba operandy hodnoty 0. Pokud má buď operand nenulovou hodnotu, výsledkem je 1. Pokud první operand operace logické nebo má nenulovou hodnotu, nebude hodnocen Druhý operand.|  
  
 Operandy logického- a a logické nebo výrazy jsou vyhodnocovány zleva doprava. Pokud hodnota První operand stačí určit výsledek operace, druhý operand, nebude hodnocen. To se označuje jako "krátká smyčka – vyhodnocení." Po první operand není bodu sekvence. V tématu [body sekvence](../c-language/c-sequence-points.md) Další informace.  
  
## <a name="examples"></a>Příklady  
 Následující příklady ilustrují logické operátory:  
  
```  
int w, x, y, z;  
  
if ( x < y && y < z )  
    printf( "x is less than z\n" );  
```  
  
 V tomto příkladu `printf` tisknout zprávu, pokud je volána funkce `x` je menší než `y` a `y` je menší než `z`. Pokud `x` je větší než `y`, druhý operand (`y < z`), nebude hodnocen a nic je vytisknout. Všimněte si, že to může způsobit problémy v případech, kdy Druhý operand obsahuje vedlejší účinky, které jsou právě spoléhali na z jiného důvodu.  
  
```  
printf( "%d" , (x == w || x == y || x == z) );  
```  
  
 V tomto příkladu Pokud `x` se rovná buď `w`, `y`, nebo `z`, aby druhý argument `printf` funkce vyhodnotí jako true, a hodnota 1 je vytisknout. Jinak je vyhodnocena jako false a hodnota 0 je vytisknout. Jakmile jedna z podmínek vyhodnotí jako true, přestane vyhodnocení.  
  
## <a name="see-also"></a>Viz také  
 [Logický operátor AND: & &](../cpp/logical-and-operator-amp-amp.md)   
 [Logický operátor OR:&#124;&#124;](../cpp/logical-or-operator-pipe-pipe.md)