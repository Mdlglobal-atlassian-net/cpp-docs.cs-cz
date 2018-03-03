---
title: "Kompilátoru upozornění (úrovně 2 a 4) C4200 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4200
dev_langs:
- C++
helpviewer_keywords:
- C4200
ms.assetid: e44d6073-937f-42b7-acc1-65e802b475c6
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f160476deb2ab3e4ad0ff00100305c934dfb14c3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-levels-2-and-4-c4200"></a>Upozornění kompilátoru (úrovně 2 a 4) C4200
nestandardní rozšíření používané: nulovou velikostí pole v struktura/sjednocení  
  
 Označuje, že struktura nebo union obsahuje pole, které má nulové velikost.  
  
 Deklarace pole nulovou velikostí je rozšíření Microsoft. To způsobí, že Level 2 upozornění při kompilaci souboru C++ a úroveň 4 upozornění při kompilaci souboru C. Kompilace C++ také poskytuje toto upozornění: "Nelze vygenerovat operátor konstruktor Copy nebo kopírování přiřazení při UDT obsahuje pole nulovou velikostí." Tento příklad vytvoří upozornění C4200:  
  
```cpp  
// C4200.cpp  
// compile by using: cl /W4 c4200.cpp  
struct A {  
    int a[0];  // C4200  
};  
int main() {  
}  
```  
  
 Toto nestandardní rozšíření se často používá ke kódu rozhraní s externí datové struktury, které mají proměnlivou délkou. Pokud se tento scénář se vztahuje na kód, můžete zakázat upozornění:  
  
## <a name="example"></a>Příklad  
  
```cpp  
// C4200b.cpp  
// compile by using: cl /W4 c4200a.cpp  
#pragma warning(disable : 4200)  
struct A {  
    int a[0];  
};  
int main() {  
}  
```