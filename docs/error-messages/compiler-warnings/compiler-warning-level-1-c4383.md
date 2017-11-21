---
title: "Kompilátoru (úroveň 1) upozornění C4383 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4383
dev_langs: C++
helpviewer_keywords: C4383
ms.assetid: 96c0e52d-874e-4b57-a154-0e49b6a00fae
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 2dacaa9b621a4578aafced38fa38d1b82a687d07
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4383"></a>C4383 kompilátoru upozornění (úroveň 1)
'instance_dereference_operator': význam vyhodnocení popisovač lze změnit, pokud existuje operátor uživatelem definované 'operátor'; zápis operátor jako statické funkce jako explicitní o operand  
  
 Když přidáte uživatelské instance přepsání operátoru dereference v spravovaného typu, je potenciálně přepsat schopnost operátor dereference typ vrátit je popisovač objektu. Vezměte v úvahu zápis statického, uživatelem definované operátoru zrušení.  
  
 Další informace najdete v tématu [operátor popisovače objektu (^)](../../windows/handle-to-object-operator-hat-cpp-component-extensions.md) a [sledování Reference – operátor](../../windows/tracking-reference-operator-cpp-component-extensions.md).  
  
 Operátor instance není k dispozici pro ostatní kompilátory jazyka prostřednictvím odkazovaného metadat. Další informace najdete v tématu [uživatelem definované operátory (C + +/ CLI)](../../dotnet/user-defined-operators-cpp-cli.md).  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C4383.  
  
```  
// C4383.cpp  
// compile with: /clr /W1  
  
ref struct S {  
   int operator*() { return 0; }   // C4383  
};  
  
ref struct T {  
   static int operator*(T%) { return 0; }  
};   
  
int main() {  
   S s;  
   S^ pS = %s;  
  
   T t;  
   T^ pT = %t;  
   T% rT = *pT;  
}  
```