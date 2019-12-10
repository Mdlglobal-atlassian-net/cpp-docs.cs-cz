---
title: Upozornění kompilátoru (úroveň 4) C4673
ms.date: 11/04/2016
f1_keywords:
- C4673
helpviewer_keywords:
- C4673
ms.assetid: 95626ec6-f05b-43c7-8b9a-a60a6f98dd30
ms.openlocfilehash: cd53aeb7f767b06c017c64caa55c916aa1e2b9c9
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74990575"
---
# <a name="compiler-warning-level-4-c4673"></a>Upozornění kompilátoru (úroveň 4) C4673

throw ' identifikátor ' následující typy se nebudou brát v úvahu na webu catch.

V bloku **catch** nelze zpracovat objekt throw. Každý typ, který nelze zpracovat, je uveden ve výstupu chyby hned za řádkem obsahujícím toto upozornění. Každý neošetřený typ má své vlastní upozornění. Další informace najdete v upozornění pro každý konkrétní typ.

Následující ukázka generuje C4673:

```cpp
// C4673.cpp
// compile with: /EHsc /W4
class Base {
private:
   char * m_chr;
public:
   Base() {
      m_chr = 0;
   }

   ~Base() {
      if(m_chr)
         delete m_chr;
   }
};

class Derv : private Base {
public:
   Derv() {}
   ~Derv() {}
};

int main() {
   try {
      Derv D1;
      // delete previous line, uncomment the next line to resolve
      // Base D1;
      throw D1;   // C4673
   }

   catch(...) {}
}
```
