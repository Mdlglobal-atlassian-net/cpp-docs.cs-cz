---
title: Upozornění (úroveň 4) C4673 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4673
dev_langs:
- C++
helpviewer_keywords:
- C4673
ms.assetid: 95626ec6-f05b-43c7-8b9a-a60a6f98dd30
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1ab61a71a747b1fd917db579a57700107d12da87
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46085813"
---
# <a name="compiler-warning-level-4-c4673"></a>Kompilátor upozornění (úroveň 4) C4673

'identifier' vyvolání těchto typů nebude brát v lokalitě catch

Objekt throw nemůže být zpracovány v **catch** bloku. Každý typ, který nelze zpracovat je uvedená ve výstupu chyba hned za řádek obsahující toto upozornění. Každý Nezpracovaný typ má své vlastní upozornění. Přečtěte si upozornění pro každý typ konkrétní informace.

Následující ukázka generuje C4673:

```
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