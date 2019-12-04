---
title: Chyba kompilátoru C3699
ms.date: 11/04/2016
f1_keywords:
- C3699
helpviewer_keywords:
- C3699
ms.assetid: 47c29afc-ab8b-4238-adfe-788dd6e00b3b
ms.openlocfilehash: ec902266550e591623894823e6336bd2436bfbd5
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758031"
---
# <a name="compiler-error-c3699"></a>Chyba kompilátoru C3699

' operator ': Toto dereference nelze použít pro typ ' type '

Byl proveden pokus o použití dereference, která není povolena v `type`.

## <a name="example"></a>Příklad

Následující ukázka generuje C3699.

```cpp
// C3699.cpp
// compile with: /clr /c
using namespace System;
int main() {
   String * s;   // C3699
   // try the following line instead
   // String ^ s2;
}
```

## <a name="example"></a>Příklad

Triviální vlastnost nemůže mít odkazový typ. Další informace najdete v tématu [vlastnost](../../extensions/property-cpp-component-extensions.md) . Následující ukázka generuje C3699.

```cpp
// C3699_b.cpp
// compile with: /clr /c
ref struct C {
   property System::String % x;   // C3699
   property System::String ^ y;   // OK
};
```

## <a name="example"></a>Příklad

Ekvivalentem "ukazatele na ukazatel" je popisovačem sledovacího odkazu. Následující ukázka generuje C3699.

```cpp
// C3699_c.cpp
// compile with: /clr /c
using namespace System;
void Test(String ^^ i);   // C3699
void Test2(String ^% i);
```
