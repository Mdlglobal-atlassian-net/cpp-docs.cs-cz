---
title: Chyba kompilátoru C2473
ms.date: 11/04/2016
f1_keywords:
- C2473
helpviewer_keywords:
- C2473
ms.assetid: 6bb7dbf5-b198-490f-860e-fd64d0c2a284
ms.openlocfilehash: 2f7ce0e18070c2b5ee6ebb2284d5564b3d750d77
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74743715"
---
# <a name="compiler-error-c2473"></a>Chyba kompilátoru C2473

' identifier ': vypadá jako definice funkce, ale neexistuje seznam parametrů.

Kompilátor zjistil, co vypadal jako funkce, bez seznamu parametrů.

## <a name="example"></a>Příklad

Následující ukázka generuje C2473.

```cpp
// C2473.cpp
// compile with: /clr /c
class A {
   int i {}   // C2473
};

class B {
   int i() {}   // OK
};
```
