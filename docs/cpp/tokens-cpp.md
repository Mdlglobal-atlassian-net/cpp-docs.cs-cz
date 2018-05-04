---
title: Tokeny (C++) | Microsoft Docs
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
ms.openlocfilehash: ba2e1a6cc36e4e5f2f785c1e5dff03c6fb5e392d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="tokens-c"></a>Tokeny (C++)
Token je nejmenší prvek programu C++, který je smysluplný pro kompilátor. Analyzátor jazyka C++ rozpoznává tyto druhy tokenů: identifikátory, klíčová slova, literály, operátory, interpunkční znaky a jiné oddělovače. Proud těchto tokenů tvoří jednotku překladu.  
  
 Tokeny jsou obvykle oddělených *mezer*. Prázdný znak může být jeden nebo jich může být více:  
  
-   Prázdné hodnoty  
  
-   Vodorovné nebo svislé tabulátory  
  
-   Nové řádky  
  
-   Zakončení stránky  
  
-   Komentáře  
  
 Analyzátor rozpozná klíčová slova, identifikátory, literály, operátory a interpunkční znaky. Informace o konkrétní typy tokenů, najdete v části [klíčová slova](../cpp/keywords-cpp.md), [identifikátory](../cpp/identifiers-cpp.md), [číselný, logické a literály typu ukazatele](../cpp/numeric-boolean-and-pointer-literals-cpp.md), [řetězcové a znakové literály ](../cpp/string-and-character-literals-cpp.md), [Uživateli definované literály](../cpp/user-defined-literals-cpp.md), [operátory předdefinované C++, prioritu a Asociativnost](../cpp/cpp-built-in-operators-precedence-and-associativity.md), a [interpunkční znaky jazyka](../cpp/punctuators-cpp.md). Prázdné znaky je ignorován, s výjimkou podle potřeby k oddělení tokeny.  
  
 Předběžného zpracování tokeny se používají ve fázích předběžného zpracování ke generování tokenů datový proud předaný kompilátoru. Předběžného zpracování tokenu kategorie jsou názvy záhlaví, identifikátory, předběžného zpracování čísla, znakové literály, textové literály, operátory předběžného zpracování a interpunkční znaky jazyka a jeden prázdný znak znaky, které neodpovídá jedné z jiných kategorií. Řetězec a znakové literály může být uživateli definované literály. Předběžné zpracování tokeny je možné oddělit mezer nebo komentáře.  
  
 Analyzátor oddělí tokeny ze vstupního datového proudu vytvořením nejdelšího možného tokenu použitím vstupních znaků při skenování zleva doprava. Prohlédněte si tento fragment kódu:  
  
```  
a = i+++j;  
```  
  
 Programátor, který kód vytvořil, mohl zamýšlet jeden z těchto dvou příkazů:  
  
```  
a = i + (++j)  
  
a = (i++) + j  
```  
  
 Vzhledem k tomu, že analyzátor vytvoří ze vstupního proudu nejdelší možný token, zvolí druhý výklad, díky čemuž tokeny budou `i++`, `+` a `j`.  
  
## <a name="see-also"></a>Viz také  
 [Lexikální konvence](../cpp/lexical-conventions.md)