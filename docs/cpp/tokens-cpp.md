---
title: Tokeny (C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- tokens [C++]
- parsing, C++ tokens
- translation units
- white space, in C++ tokens
ms.assetid: aa812fd0-6d47-4f3f-aee0-db002ee4d8b9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 217061557acb0c8b311a91651eea2f57a8198872
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/02/2018
ms.locfileid: "39467533"
---
# <a name="tokens-c"></a>Tokeny (C++)
Token je nejmenší prvek programu C++, který je smysluplný pro kompilátor. Analyzátor jazyka C++ rozpoznává tyto druhy tokenů: identifikátory, klíčová slova, literály, operátory, interpunkční znaky a jiné oddělovače. Proud těchto tokenů tvoří jednotku překladu.  
  
 Tokeny jsou odděleny obvykle *prázdných*. Prázdný znak může být jeden nebo jich může být více:  
  
-   Prázdné hodnoty  
  
-   Vodorovné nebo svislé tabulátory  
  
-   Nové řádky  
  
-   Zakončení stránky  
  
-   Komentáře  
  
 Analyzátor rozpozná klíčová slova, identifikátory, literály, operátory a interpunkční znaky. Informace o konkrétní typy tokenů, naleznete v tématu [klíčová slova](../cpp/keywords-cpp.md), [identifikátory](../cpp/identifiers-cpp.md), [číselné, logické a literály typu ukazatele](../cpp/numeric-boolean-and-pointer-literals-cpp.md), [řetězcové a znakové literály ](../cpp/string-and-character-literals-cpp.md), [Uživateli definované literály](../cpp/user-defined-literals-cpp.md), [integrované operátory C++, Priorita a asociativita](../cpp/cpp-built-in-operators-precedence-and-associativity.md), a [interpunkční znaky](../cpp/punctuators-cpp.md). Prázdné místo je ignorován, s výjimkou podle potřeby k oddělení tokeny.  
  
 Tokeny předběžného zpracování se používají ve fázích předběžného zpracování k vygenerování tokenu stream předány kompilátoru. Předzpracování token kategorií jsou názvy záhlaví, identifikátory, předzpracování čísla, znakových literálů, řetězcové literály, operátory předběžného zpracování a interpunkční znaky a jednotlivé znaky prázdné znaky, které se neshodují s některou z jiných kategorií. Znakové a řetězcové literály se dá uživateli definované literály. Tokeny předzpracování mohou být odděleny prázdným znakem nebo komentáře.  
  
 Analyzátor oddělí tokeny ze vstupního datového proudu vytvořením nejdelšího možného tokenu použitím vstupních znaků při skenování zleva doprava. Prohlédněte si tento fragment kódu:  
  
```cpp 
a = i+++j;  
```  
  
 Programátor, který kód vytvořil, mohl zamýšlet jeden z těchto dvou příkazů:  
  
```cpp 
a = i + (++j)  
  
a = (i++) + j  
```  
  
 Vzhledem k tomu, že analyzátor vytvoří ze vstupního proudu nejdelší možný token, zvolí druhý výklad, díky čemuž tokeny budou `i++`, `+` a `j`.  
  
## <a name="see-also"></a>Viz také:  
 [Lexikální konvence](../cpp/lexical-conventions.md)