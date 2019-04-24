---
title: Chyba kompilátoru C3421
ms.date: 11/04/2016
f1_keywords:
- C3421
helpviewer_keywords:
- C3421
ms.assetid: b52050c6-17a4-424a-8894-337b0cec7010
ms.openlocfilehash: 399224a3d091a26066a03df0c77511997ae2403c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62182417"
---
# <a name="compiler-error-c3421"></a>Chyba kompilátoru C3421

'type': nelze volat finalizační metodu pro tuto třídu, protože je buď nedostupná nebo není k dispozici

Finalizační metoda je implicitně soukromé, takže ho nejde volat z mimo jeho nadřazeného typu.

Další informace najdete v tématu [destruktory a finalizační metody v tom, jak: Definice a používání tříd a struktur (C++vyhodnocovací)](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers).

## <a name="example"></a>Příklad

Následující ukázka generuje C3421.

```
// C3421.cpp
// compile with: /clr
ref class A {};

ref class B {
   !B() {}

public:
   ~B() {}
};

int main() {
   A a;
   a.!A();   // C3421

   B b;
   b.!B();   // C3421
}
```