---
title: "Operátory jazyka C | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- ternary operators
- operators [C]
- symbols, operators
- binary operators
- associativity of operators
- binary data, binary expressions
ms.assetid: 13bc4c8e-2dc9-4b23-9f3a-25064e8777ed
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: fee64f3d5c5e26783745961f4aa5dc076dd472c1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="c-operators"></a>Operátory jazyka C
Operátory jazyka C, jsou podmnožinou [předdefinované operátory jazyka C++](../cpp/cpp-built-in-operators-precedence-and-associativity.md).  
  
 Existují tři typy operátorů. Jednočlenný výraz sestává buď z jednočlenného operátoru uvedeného před operandem, nebo z klíčového slova `sizeof` následovaného výrazem. Výrazem může být název proměnné nebo výraz přetypování. Je-li výraz výrazem přetypování, musí být uzavřen závorkami. Binární výraz se skládá ze dvou operandů spojených binárním operátorem. Ternární výraz je složen ze tří operandů spojených operátorem podmíněného výrazu.  
  
 Jazyk C obsahuje následující jednočlenné operátory:  
  
|Symbol|Název|  
|------------|----------|  
|**- ~ !**|Operátor negace a doplňku|  
|**\* &**|Operátory dereference a adresa|  
|`sizeof`|Operátor velikosti|  
|**+**|Jednočlenný operátor plus|  
|**++ --**|Jednočlenné operátory inkrementace a dekrementace|  
  
 Binární operátory jsou asociativní zleva doprava. Jazyk C poskytuje následující binární operátory:  
  
|Symbol|Název|  
|------------|----------|  
|**\* / %**|Operátory násobení|  
|**+ -**|Operátory sčítání|  
|**<\< >>**|Operátory posunutí|  
|**\<   >   \<=   >=   ==   !=**|Relační operátory|  
|**&   &#124; ^**|Bitové operátory|  
|**&&   &#124;&#124;**|Logické operátory|  
|**,**|Operátor sekvenčního vyhodnocení|  
  
 Základní operátor (**: >**), podporované v předchozích verzích nástroje kompilátor jazyka C 16bitové Microsoft, je popsaný v [souhrn syntaxe jazyka C](../c-language/c-language-syntax-summary.md).  
  
 Operátor podmíněného výrazu má nižší prioritu než binární výrazy a liší se od nich asociativitou zprava.  
  
 Výrazy s operátory obsahují také výrazy přiřazení, které používají jednočlenné nebo binární operátory přiřazení. Unární operátory přiřazení jsou přírůstku (`++`) a snížení (**--**) operátory; binárního souboru operátory přiřazení jsou operátor jednoduchého přiřazení ( **=** ) operátory a operátory složené přiřazení. Všechny složené operátory jsou kombinací jiného binárního operátoru s operátorem jednoduchého přiřazení.  
  
## <a name="see-also"></a>Viz také  
 [Výrazy a přiřazení](../c-language/expressions-and-assignments.md)