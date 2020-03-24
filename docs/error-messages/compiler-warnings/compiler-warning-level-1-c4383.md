---
title: Upozornění kompilátoru (úroveň 1) C4383
ms.date: 11/04/2016
f1_keywords:
- C4383
helpviewer_keywords:
- C4383
ms.assetid: 96c0e52d-874e-4b57-a154-0e49b6a00fae
ms.openlocfilehash: 1c4a7ca806430c73c8e8396e596782253cc06f09
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80162735"
---
# <a name="compiler-warning-level-1-c4383"></a>Upozornění kompilátoru (úroveň 1) C4383

' instance_dereference_operator ': význam zrušení odkazu na popisovač se může změnit, pokud existuje uživatelem definovaný operátor ' operator '; napsat operátor jako statickou funkci, aby byl pro operand explicitní

Při přidání uživatelem definovaného přepsání operátoru dereference do spravovaného typu můžete přepsat schopnost operátora zrušení reference typu, aby vrátil objekt popisovače. Zvažte zápis statického uživatelem definovaného operátoru zpětného odkazování.

Další informace naleznete v tématu [popisovač na objekt operátor (^)](../../extensions/handle-to-object-operator-hat-cpp-component-extensions.md) a [referenční operátor sledování](../../extensions/tracking-reference-operator-cpp-component-extensions.md).

Operátor instance není k dispozici pro jiné jazykové kompilátory prostřednictvím odkazovaných metadat. Další informace najdete v tématu [operátory definované uživatelem (C++/CLI)](../../dotnet/user-defined-operators-cpp-cli.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C4383.

```cpp
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
