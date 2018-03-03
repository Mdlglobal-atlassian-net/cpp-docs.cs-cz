---
title: "C2659 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2659
dev_langs:
- C++
helpviewer_keywords:
- C2659
ms.assetid: b0883600-4d27-4ca7-a931-8ca6bd48654d
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5c69af55d7a5fd61508505bd96091ffcbed41c5a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2659"></a>C2659 chyby kompilátoru
Operátor: funkce jako levý operand  
  
 Funkce byla na levé straně zadaného operátoru. Nejčastější příčinou této chyby je, že kompilátor analyzoval identifikátor na levé straně operátoru jako funkci, ale vývojář chtěl, aby to byla proměnná. Další informace najdete v tématu Wikipedia článku [nejvíce vexing analýzy](http://en.wikipedia.org/wiki/Most_vexing_parse). Tento příklad ukazuje deklaraci funkce a definici proměnné, které lze snadno zaměnit:  
  
```  
// C2659a.cpp  
// Compile using: cl /W4 /EHsc C2659a.cpp  
#include <string>  
using namespace std;  
  
int main()   
{  
   string string1(); // string1 is a function returning string  
   string string2{}; // string2 is a string initialized to empty   
  
   string1 = "String 1"; // C2659  
   string2 = "String 2";  
}  
```  
  
 Chcete-li tento problém vyřešit, změňte deklaraci identifikátoru tak, aby nebyl analyzován jako deklarace funkce.  
  
 Chyba C2659 se může zobrazit také v případě, že funkce má typ, který nelze použít ve výrazu na levé straně zadaného operátoru. Tento příklad vygeneruje chybu C2659, když kód funkci přiřadí ukazatel na funkci:  
  
```  
// C2659b.cpp  
// Compile using: cl /W4 /EHsc C2659b.cpp  
int func0(void) { return 42; }  
int (*func1)(void);  
  
int main()  
{  
   func1 = func0;  
   func0 = func1; // C2659  
}  
```