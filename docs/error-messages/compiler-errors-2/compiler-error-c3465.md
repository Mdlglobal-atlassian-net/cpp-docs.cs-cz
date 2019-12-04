---
title: Chyba kompilátoru C3465
ms.date: 11/04/2016
f1_keywords:
- C3465
helpviewer_keywords:
- C3465
ms.assetid: aeb815e5-b3fc-4525-afe2-d738e9321df1
ms.openlocfilehash: 1d82d367c5b77f54548403b7b142aa740919b6c2
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756562"
---
# <a name="compiler-error-c3465"></a>Chyba kompilátoru C3465

Pokud chcete použít typ Type, musíte odkazovat na sestavení Assembly.

Přesměrování typu bude fungovat pro klientskou aplikaci, dokud nezkompilujete klienta. Při rekompilaci budete potřebovat odkaz pro každé sestavení, které obsahuje definici typu používaného v klientské aplikaci.

Další informace naleznete v tématu [předávání typů (C++/CLI)](../../extensions/type-forwarding-cpp-cli.md).

## <a name="example"></a>Příklad

Následující příklad vytvoří sestavení, které obsahuje nové umístění typu.

```cpp
// C3465.cpp
// compile with: /clr /LD
public ref class R {
public:
   ref class N {};
};
```

## <a name="example"></a>Příklad

Následující příklad sestaví sestavení, které slouží k zahrnutí definice typu, ale nyní obsahuje syntaxi předávání pro daný typ.

```cpp
// C3465_b.cpp
// compile with: /clr /LD
#using "C3465.dll"
[ assembly:TypeForwardedTo(R::typeid) ];
```

## <a name="example"></a>Příklad

Následující ukázka generuje C3465.

```cpp
// C3465_c.cpp
// compile with: /clr
// C3465 expected
#using "C3465_b.dll"
// Uncomment the following line to resolve.
// #using "C3465.dll"

int main() {
   R^ r = gcnew R();
}
```
