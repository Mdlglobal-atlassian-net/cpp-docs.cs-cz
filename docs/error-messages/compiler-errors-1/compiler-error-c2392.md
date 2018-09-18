---
title: Chyba kompilátoru C2392 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2392
dev_langs:
- C++
helpviewer_keywords:
- C2392
ms.assetid: 98ced473-6383-46ed-b79c-21857d65dcb2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c45c5b271235e4ada0945a79087186a213c75343
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46064266"
---
# <a name="compiler-error-c2392"></a>Chyba kompilátoru C2392

'– metoda1': kovariant se vrací typy nejsou podporované v spravovanou nebo WinRTtypes, jinak "method2' by být přepsána.

Kovariantní návratové typy nejsou povolené u členských funkcí Windows Runtime nebo při kompilaci s [/CLR (kompilace Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md) možnost.

## <a name="example"></a>Příklad

Následující ukázka generuje C2392 a ukazuje, jak ho opravit.

```
// C2392.cpp
// compile with: /clr
public ref struct B {
public:
   int i;
};

public ref struct D: public B{};

public ref struct B1 {
public:
   virtual B^ mf() {
      B^ pB = gcnew B;
      pB->i = 11;
      return pB;
   }
};

public ref struct D1: public B1 {
public:
   virtual D^ mf() override {  // C2392
   // try the following line instead
   // virtual B^ mf() override {
   // return type D^ is covariant with B^, not allowed with CLR types
      D^ pD = gcnew D;
      pD->i = 12;
      return pD;
   }
};

int main() {
   B1^ pB1 = gcnew D1;
   B^ pB = pB1->mf();
   D^ pD = dynamic_cast<D^>(pB);
}
```