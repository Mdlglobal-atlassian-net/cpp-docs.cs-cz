---
title: Příkazy iterace (C++) | Dokumentace Microsoftu
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
ms.openlocfilehash: 988d46b3f4b2e20ff14227fda70a6f39ac95756c
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/01/2018
ms.locfileid: "39402894"
---
# <a name="iteration-statements-c"></a>Příkazy iterace (C++)
Příkazy iterace způsobit, že příkazy (nebo složené příkazy) má být proveden nulakrát nebo vícekrát, v souladu s kritérií ukončení smyčky. Pokud tyto příkazy jsou složené příkazy, jsou provedeny v pořadí, kromě případů, kdy buď [přerušení](../cpp/break-statement-cpp.md) příkaz nebo [pokračovat](../cpp/continue-statement-cpp.md) příkaz dochází.  
  
 Jazyk C++ poskytuje čtyři příkazy iterace – [při](../cpp/while-statement-cpp.md), [proveďte](../cpp/do-while-statement-cpp.md), [pro](../cpp/for-statement-cpp.md), a [rozsahový pro](../cpp/range-based-for-statement-cpp.md). Každá z těchto iterace, dokud jeho ukončení výraz vyhodnocen jako nula (NEPRAVDA), nebo ukončení smyčky je nucen se **přerušení** příkazu. Následující tabulka shrnuje tyto příkazy a jejich akcí. každý je podrobně popsány v následující části.  
  
### <a name="iteration-statements"></a>Příkazy iterace  
  
|Příkaz|Vyhodnotit za|Inicializace|Přírůstek|  
|---------------|------------------|--------------------|---------------|  
|**while**|Horní části smyčky|Ne|Ne|  
|**do**|Dolní smyčky|Ne|Ne|  
|**for**|Horní části smyčky|Ano|Ano|  
|**na základě rozsahu pro**|Horní části smyčky|Ano|Ano|  
  
 Část příkazu iterace příkazu nemůže být deklarace. Může však být složeného příkazu, který obsahuje deklaraci.  
  
## <a name="see-also"></a>Viz také:  
 [Přehled příkazů jazyka C++](../cpp/overview-of-cpp-statements.md)