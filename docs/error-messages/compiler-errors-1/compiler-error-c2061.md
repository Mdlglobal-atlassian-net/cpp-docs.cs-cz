---
title: Chyba kompilátoru C2061
ms.date: 11/04/2016
f1_keywords:
- C2061
helpviewer_keywords:
- C2061
ms.assetid: b0e61c0c-a205-4820-b9aa-301d6c6fe6eb
ms.openlocfilehash: 85357d94c7bc2d709e852daa60caf269949ad1b8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62408690"
---
# <a name="compiler-error-c2061"></a>Chyba kompilátoru C2061

Chyba syntaxe: identifikátor 'identifier'

Kompilátor najít identifikátor, ve kterém se neočekávala. Ujistěte se, že `identifier` je deklarována před jejich použitím.

Inicializátor mohou být uzavřeny v závorkách. K tomuto problému vyhnout, uzavřete deklarátoru v závorkách nebo ji `typedef`.

Tato chyba může být způsobeno i když kompilátor zjistí výraz jako argument šablony třídy; použít [typename](../../cpp/typename.md) pro oznámení kompilátoru je typem.

Následující ukázka generuje C2061:

```
// C2061.cpp
// compile with: /c
template < A a >   // C2061
// try the following line instead
// template < typename b >
class c{};
```

C2061 může dojít, pokud předáte název instance do [typeid](../../extensions/typeid-cpp-component-extensions.md):

```
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