---
title: "Bitové operátory jazyka C | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- '| operator, bitwise operators'
- bitwise operators, Visual C
- bitwise operators
- operators [C], bitwise
- ^ operator, bitwise operators
- AND operator
- ampersand operator (&)
- ^ operator
- '& operator, bitwise operators'
ms.assetid: e22127b1-9a2d-4876-b01d-c8f72cec3317
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a55cbad7606eb5ce204e3363b1d292c787b59740
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="c-bitwise-operators"></a>Bitové operátory jazyka C
Bitové operátory provést bitový- a (**&**), bitový exkluzivní OR (**^**) a bitové – včetně OR (**&#124;**) operace.  
  
 **Syntaxe**  
  
 *A výraz*:  
 *rovnost – výraz*  
  
 *Výraz a***&***rovnosti – výraz*   
  
 *výraz exkluzivní OR*:  
 *AND – výraz*  
  
 *výraz exkluzivní OR***^***a výraz*   
  
 *včetně výraz OR*:  
 *výraz exkluzivní OR*  
  
 *včetně výraz OR* &#124; *výraz exkluzivní OR*  
  
 Operandy bitové operátory musí mít integrální typy, ale jejich typy mohou být různé. Obvyklé aritmetické převody; provést tyto operátory Typ výsledku je typ operandy po převodu.  
  
 Bitové operátory jazyka C jsou následující:  
  
|Operátor|Popis|  
|--------------|-----------------|  
|**&**|Bitové hodnotě- a porovná každý bit jeho první operand odpovídající bit její druhý operand operátoru. Pokud jsou obě bits 1, 1 je nastavena odpovídající bit výsledek. Odpovídající bit výsledek, jinak hodnota nastavena na hodnotu 0.|  
|**^**|Bitový exkluzivní OR operátor porovná každý bit jeho první operand odpovídající bit její druhý operand. Pokud je jeden bit 0 a dalších bit je 1, 1 je nastavena odpovídající výsledek bit. Odpovídající bit výsledek, jinak hodnota nastavena na hodnotu 0.|  
|**&#124;**|Bitový – včetně-operátoru OR porovná každý bit jeho první operand odpovídající bit její druhý operand. Pokud je buď bit 1, odpovídající výsledek bit nastavená na 1. Odpovídající bit výsledek, jinak hodnota nastavena na hodnotu 0.|  
  
## <a name="examples"></a>Příklady  
 Tyto deklarace se používají pro následující tři příklady:  
  
```  
short i = 0xAB00;  
short j = 0xABCD;  
short n;  
  
n = i & j;  
```  
  
 Výsledek přiřazené `n` v této první příklad je stejný jako `i` (0xAB00 šestnáctkové).  
  
```  
n = i | j;  
  
n = i ^ j;  
```  
  
 Bitový inkluzivní nebo v druhém příkladu výsledkem hodnota 0xABCD (hexadecimální), zatímco bitový exkluzivní OR v třetím příkladu vytvoří 0xCD (hexadecimální).  
  
 **Konkrétní Microsoft**  
  
 Výsledky bitové operace na podepsaná celá čísla je definován implementace podle standardní ANSI C. Pro kompilátor Microsoft C bitové operace na podepsaná celá čísla fungovat stejně jako bitové operace na celá čísla bez znaménka. Například `-16 & 99` může být vyjádřený v binární soubor jako  
  
```  
  11111111 11110000  
& 00000000 01100011  
  _________________  
  00000000 01100000  
```  
  
 Výsledek bitové operace AND je 96 decimal.  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Bitový operátor AND: &](../cpp/bitwise-and-operator-amp.md)   
 [Bitový exkluzivní operátor OR: ^](../cpp/bitwise-exclusive-or-operator-hat.md)   
 [Bitový inkluzivní operátor OR: &#124;](../cpp/bitwise-inclusive-or-operator-pipe.md)