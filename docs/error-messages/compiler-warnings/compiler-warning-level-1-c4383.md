---
title: Kompilátor upozornění (úroveň 1) C4383
ms.date: 11/04/2016
f1_keywords:
- C4383
helpviewer_keywords:
- C4383
ms.assetid: 96c0e52d-874e-4b57-a154-0e49b6a00fae
ms.openlocfilehash: 61bc3951a7d57a5a4eefb69b5a0c4399df99160a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50548794"
---
# <a name="compiler-warning-level-1-c4383"></a>Kompilátor upozornění (úroveň 1) C4383

'instance_dereference_operator': význam zrušení odkazu na popisovač může změnit, pokud existuje uživatelem definovaný 'operator' – operátor Zapište operátor jako statickou funkci k explicitnímu operand

Když chcete přidat uživatelské instance přepsání metody operátor zrušení odkazu v spravovaného typu, potenciálně přepsat možnost operátor zrušení odkazu typ vrátit popisovač objektu. Vezměte v úvahu zápis statická, uživatelem definovaný operátor zrušení odkazu.

Další informace najdete v tématu [operátor popisovače objektu (^)](../../windows/handle-to-object-operator-hat-cpp-component-extensions.md) a [Tracking Reference Operator](../../windows/tracking-reference-operator-cpp-component-extensions.md).

Operátor instance není k dispozici pro jiné kompilátory jazyka prostřednictvím odkazovaných metadat. Další informace najdete v tématu [uživatelem definované operátory (C + +/ CLI)](../../dotnet/user-defined-operators-cpp-cli.md).

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