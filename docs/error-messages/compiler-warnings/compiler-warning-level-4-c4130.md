---
title: Kompilátoru (úroveň 4) upozornění C4130 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4130
dev_langs:
- C++
helpviewer_keywords:
- C4130
ms.assetid: 45e4c7b2-6b51-41c7-ba5e-941aa5c7d3dc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 226b715689e506cb34ea6e7684f9ddcf041e638b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33292172"
---
# <a name="compiler-warning-level-4-c4130"></a>C4130 kompilátoru upozornění (úroveň 4)
'operátor': logický provoz na adrese řetězcová konstanta  
  
 Pomocí operátoru s adresou řetězcový literál vytvoří neočekávaný kód.  
  
 Následující ukázka generuje C4130:  
  
```  
// C4130.cpp  
// compile with: /W4  
int main()  
{  
   char *pc;  
   pc = "Hello";  
   if (pc == "Hello") // C4130  
   {  
   }  
}  
```  
  
 **Pokud** příkaz porovná s hodnotou uloženou v ukazatele `pc` řetězce "Hello" na adresu, která je přidělena samostatně pokaždé, když dojde k řetězec v kódu. **Pokud** příkaz není porovnat řetězec, na kterou odkazuje `pc` řetězcem "Hello".  
  
 Pro porovnání řetězců, použijte `strcmp` funkce.