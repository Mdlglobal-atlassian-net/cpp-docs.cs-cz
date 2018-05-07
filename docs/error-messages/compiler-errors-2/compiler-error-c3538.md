---
title: C3538 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3538
dev_langs:
- C++
helpviewer_keywords:
- C3538
ms.assetid: ef3698a5-7356-4c62-b9af-5d3a4baed958
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 35f852e41ff86b9eed39da0aeb367d7049b8db4b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3538"></a>C3538 chyby kompilátoru
v seznamu deklarátor 'auto' musí vždy odvodit do stejného typu  
  
 Všechny proměnné, které jsou deklarované v seznamu deklarace neřešit do stejného typu.  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Ujistěte se, že všechny `auto` deklarace v seznamu odvodit do stejného typu.  
  
## <a name="example"></a>Příklad  
 Následující příkazy yield C3538. Každý příkaz deklaruje více proměnné, ale každý použití `auto` – klíčové slovo není odvodit do stejného typu.  
  
```  
// C3538.cpp  
// Compile with /Zc:auto  
// C3538 expected  
int main()  
{  
// Variable x1 is a pointer to char, but y1 is a double.  
   auto * x1 = "a", y1 = 3.14;    
// Variable c is a char and c1 is char*, but c2, and c3 are pointers to pointers.  
   auto c = 'a', *c1 = &c, * c2 = &c1, * c3 = &c2;   
// Variable x2 is an int, but y2 is a double and z is a char.  
   auto x2(1), y2(0.0), z = 'a';   
// Variable a is a pointer to int, but b is a pointer to double.  
   auto *a = new auto(1), *b = new auto(2.0);   
   return 0;  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Auto – klíčové slovo](../../cpp/auto-keyword.md)