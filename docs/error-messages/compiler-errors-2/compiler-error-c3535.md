---
title: "C3535 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3535
dev_langs: C++
helpviewer_keywords: C3535
ms.assetid: 24449c98-f681-484d-a00b-32533dca3a88
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 3ab054ceefa51ab944e2d048996e25559b0c86ba
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3535"></a>C3535 chyby kompilátoru
nelze odvodit typ 'type1' z 'type2'.  
  
 Typ proměnné deklarovaná `auto` – klíčové slovo nelze odvodit z typu inicializace výrazu. Například tato chyba nastane, pokud je výsledkem výrazu inicializace `void`, která není typu.  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Ujistěte se, že typ výrazu inicializace není `void`.  
  
2.  Ujistěte se, že deklaraci není ukazatel na základní typ. Další informace najdete v tématu [základní typy](../../cpp/fundamental-types-cpp.md).  
  
3.  Ujistěte se, pokud deklaraci je ukazatel typu, inicializace výrazu je ukazatel typu.  
  
## <a name="example"></a>Příklad  
 Následující příklad vypočítá C3535, protože výsledkem výrazu inicializace `void`.  
  
```  
// C3535a.cpp  
// Compile with /Zc:auto  
void f(){}  
int main()  
{  
   auto x = f();   //C3535  
   return 0;  
}  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad vypočítá C3535, protože příkaz deklaruje proměnnou `x` jako ukazatel na deduced typ, ale typ inicializátoru výraz je double. Kompilátor v důsledku toho nelze odvodit typ proměnné.  
  
```  
// C3535b.cpp  
// Compile with /Zc:auto  
int main()  
{  
   auto* x = 123.0;   // C3535  
   return 0;  
}  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad vypočítá C3535, protože proměnná `p` deklaruje ukazatel typu deduced, ale výraz inicializace není ukazatel typu.  
  
```  
// C3535c.cpp  
// Compile with /Zc:auto  
class A { };  
A x;  
auto *p = x;  // C3535  
```  
  
## <a name="see-also"></a>Viz také  
 [Auto – klíčové slovo](../../cpp/auto-keyword.md)   
 [Základní typy](../../cpp/fundamental-types-cpp.md)