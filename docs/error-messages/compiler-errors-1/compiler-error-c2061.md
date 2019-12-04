---
title: Chyba kompilátoru C2061
ms.date: 11/04/2016
f1_keywords:
- C2061
helpviewer_keywords:
- C2061
ms.assetid: b0e61c0c-a205-4820-b9aa-301d6c6fe6eb
ms.openlocfilehash: dc64852523b6b56bc506260576e3c79164628340
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74735928"
---
# <a name="compiler-error-c2061"></a>Chyba kompilátoru C2061

Chyba syntaxe: identifikátor identifikátoru

Kompilátor našel identifikátor, u kterého se neočekával. Ujistěte se, že je před použitím deklarováno `identifier`.

Inicializátor může být uzavřený v závorkách. Chcete-li se tomuto problému vyhnout, vložte deklarátor do závorek nebo ho Udělejte `typedef`.

Tato chyba může být také způsobena tím, že kompilátor detekuje výraz jako argument šablony třídy; použijte [TypeName](../../cpp/typename.md) k oznámení, že kompilátor je typu.

Následující ukázka generuje C2061:

```cpp
// C2061.cpp
// compile with: /c
template < A a >   // C2061
// try the following line instead
// template < typename b >
class c{};
```

K C2061 může dojít, Pokud předáte název instance na [typeid](../../extensions/typeid-cpp-component-extensions.md):

```cpp
// C2061b.cpp
// compile with: /clr
ref struct G {
   int i;
};

int main() {
   G ^ pG = gcnew G;
   System::Type ^ pType = typeid<pG>;   // C2061
   System::Type ^ pType2 = typeid<G>;   // OK
}
```
