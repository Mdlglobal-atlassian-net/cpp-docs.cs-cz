---
title: Upozornění kompilátoru (úroveň 1) C4395
ms.date: 11/04/2016
f1_keywords:
- C4395
helpviewer_keywords:
- C4395
ms.assetid: 8051469a-3a39-4677-80f7-1300fbffe8ea
ms.openlocfilehash: 82c7ef9c20b62c0e082a7851bac0ec1e44a8f4c7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80186852"
---
# <a name="compiler-warning-level-1-c4395"></a>Upozornění kompilátoru (úroveň 1) C4395

' function ': členská funkce bude vyvolána pro kopii datového členu initonly ' member '

Členská funkce byla volána pro datový člen [initonlyC++(/CLI)](../../dotnet/initonly-cpp-cli.md) .  C4395 upozorňuje, že datový člen **initonly** nemůže být změněn funkcí.

Následující ukázka generuje C4395:

```cpp
// C4395.cpp
// compile with: /W1 /clr
public value class V {
public:
   V(int data) : m_data(data) {}

   void Mutate() {
      System::Console::WriteLine("Enter Mutate: m_data = {0}", m_data);
      m_data *= 2;
      System::Console::WriteLine("Leave Mutate: m_data = {0}", m_data);
   }

   int m_data;
};

public ref class R {
public:
   static void f() {
      System::Console::WriteLine("v.m_data = {0}", v.m_data);
      v.Mutate();   // C4395
      System::Console::WriteLine("v.m_data = {0}", v.m_data);
   }

private:
   initonly static V v = V(4);
};

int main() {
   R::f();
}
```
