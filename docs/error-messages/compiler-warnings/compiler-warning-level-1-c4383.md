---
title: Kompilátor upozornění (úroveň 1) C4383
ms.date: 11/04/2016
f1_keywords:
- C4383
helpviewer_keywords:
- C4383
ms.assetid: 96c0e52d-874e-4b57-a154-0e49b6a00fae
ms.openlocfilehash: 2510dda59047632e2a4823f734feeffd0c0a5b02
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62390435"
---
# <a name="compiler-warning-level-1-c4383"></a>Kompilátor upozornění (úroveň 1) C4383

'instance_dereference_operator': význam zrušení odkazu na popisovač může změnit, pokud existuje uživatelem definovaný 'operator' – operátor Zapište operátor jako statickou funkci k explicitnímu operand

Když chcete přidat uživatelské instance přepsání metody operátor zrušení odkazu v spravovaného typu, potenciálně přepsat možnost operátor zrušení odkazu typ vrátit popisovač objektu. Vezměte v úvahu zápis statická, uživatelem definovaný operátor zrušení odkazu.

Další informace najdete v tématu [operátor popisovače objektu (^)](../../extensions/handle-to-object-operator-hat-cpp-component-extensions.md) a [Tracking Reference Operator](../../extensions/tracking-reference-operator-cpp-component-extensions.md).

Operátor instance není k dispozici pro jiné kompilátory jazyka prostřednictvím odkazovaných metadat. Další informace najdete v tématu [uživatelem definované operátory (C++vyhodnocovací)](../../dotnet/user-defined-operators-cpp-cli.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C4383.

```
// C4383.cpp
// compile with: /clr /W1

ref struct S {
   int operator*() { return 0; }   // C4383
};

ref struct T {
   static int operator*(T%) { return 0; }
};

int main() {
   S s;
   S^ pS = %s;

   T t;
   T^ pT = %t;
   T% rT = *pT;
}
```