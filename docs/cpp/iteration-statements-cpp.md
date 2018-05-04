---
title: Příkazy iterace (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- iteration statements
- loop structures, iteration statements
ms.assetid: bf6d75f7-ead2-426a-9c47-33847f59b8c7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1973223d6aab44d4c5d8652111d3e6b8251676fb
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="iteration-statements-c"></a>Příkazy iterace (C++)
Příkazy iterace způsobit příkazy (nebo složené příkazy) být provedeny v počtu nula či více dobu, může některá kritéria ukončení smyčky. Když jsou tyto příkazy složené příkazy, jsou spouštěny v pořadí, s výjimkou případů, kdy buď [zalomení](../cpp/break-statement-cpp.md) příkaz nebo [pokračovat](../cpp/continue-statement-cpp.md) příkaz je zjistil.  
  
 Poskytuje čtyři příkazy iterace C++ – [při](../cpp/while-statement-cpp.md), [provést](../cpp/do-while-statement-cpp.md), [pro](../cpp/for-statement-cpp.md), a [na základě rozsahu pro](../cpp/range-based-for-statement-cpp.md). Každá z těchto opakuje, dokud jeho ukončení výraz vyhodnocen jako nula (NEPRAVDA), nebo dokud ukončení smyčky je nucen se **zalomení** příkaz. Následující tabulka shrnuje tyto příkazy a jejich akce; každý je podrobněji v následujících částech.  
  
### <a name="iteration-statements"></a>Příkazy iterace  
  
|Příkaz|Vyhodnocovány v|Inicializace|Přírůstek|  
|---------------|------------------|--------------------|---------------|  
|`while`|Začátek smyčky|Ne|Ne|  
|**do**|Dolní části smyčky|Ne|Ne|  
|**for**|Začátek smyčky|Ano|Ano|  
|**na základě rozsahu pro**|Začátek smyčky|Ano|Ano|  
  
 Příkaz část příkazu iterace nemůže být deklaraci. Však může být složené příkazu, který obsahuje deklaraci.  
  
## <a name="see-also"></a>Viz také  
 [Přehled příkazů jazyka C++](../cpp/overview-of-cpp-statements.md)