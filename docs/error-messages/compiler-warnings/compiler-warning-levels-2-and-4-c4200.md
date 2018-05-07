---
title: Kompilátoru upozornění (úrovně 2 a 4) C4200 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4200
dev_langs:
- C++
helpviewer_keywords:
- C4200
ms.assetid: e44d6073-937f-42b7-acc1-65e802b475c6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6ffc789c3c4da5caf50f0657e17ddabe40a5773c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
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