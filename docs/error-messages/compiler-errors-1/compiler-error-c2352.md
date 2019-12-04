---
title: Chyba kompilátoru C2352
ms.date: 11/04/2016
f1_keywords:
- C2352
helpviewer_keywords:
- C2352
ms.assetid: 0efad8cb-659f-4b3e-8f6f-9f8ec44d345c
ms.openlocfilehash: 33fdaff31fc9e3fcde1a7101c7858704773ae74c
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759981"
---
# <a name="compiler-error-c2352"></a>Chyba kompilátoru C2352

' class:: function ': neplatné volání jiné než statické členské funkce

Členská funkce `static` s názvem nestatickou členskou funkcí. Nebo je nestatická členská funkce volána z vnějšku třídy jako statické funkce.

Následující ukázka generuje C2352 a ukazuje, jak ji opravit:

```cpp
// C2352.cpp
// compile with: /c
class CMyClass {
public:
   static void func1();
   void func2();
   static void func3() {
      func2();   // C2352 calls nonstatic func2
      func1();   // OK calls static func1
   }
};
```

Následující ukázka generuje C2352 a ukazuje, jak ji opravit:

```cpp
// C2352b.cpp
class MyClass {
public:
   void MyFunc() {}
   static void MyFunc2() {}
};

int main() {
   MyClass::MyFunc();   // C2352
   MyClass::MyFunc2();   // OK
}
```
