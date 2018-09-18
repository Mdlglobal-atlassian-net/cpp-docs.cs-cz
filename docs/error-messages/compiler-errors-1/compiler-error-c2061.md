---
title: Chyba kompilátoru C2061 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2061
dev_langs:
- C++
helpviewer_keywords:
- C2061
ms.assetid: b0e61c0c-a205-4820-b9aa-301d6c6fe6eb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 896fdb21c57e0f558b87ec23e2be309cf49f8095
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46057961"
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

C2061 může dojít, pokud předáte název instance do [typeid](../../windows/typeid-cpp-component-extensions.md):

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