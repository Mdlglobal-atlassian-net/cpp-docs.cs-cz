---
title: Chyba kompilátoru C2392
ms.date: 11/04/2016
f1_keywords:
- C2392
helpviewer_keywords:
- C2392
ms.assetid: 98ced473-6383-46ed-b79c-21857d65dcb2
ms.openlocfilehash: 5977d9bf41d55ef6db8409e0187153fdbf91149e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62393594"
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