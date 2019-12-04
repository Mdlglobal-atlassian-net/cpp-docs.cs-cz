---
title: Chyba kompilátoru C2801
ms.date: 11/04/2016
f1_keywords:
- C2801
helpviewer_keywords:
- C2801
ms.assetid: 35dfc7ea-9e37-4e30-baa1-944dc61302f5
ms.openlocfilehash: 0d2ea3677d883fa4843c37a41d733872b23cbba0
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760670"
---
# <a name="compiler-error-c2801"></a>Chyba kompilátoru C2801

operátor operator musí být nestatický člen.

Následující operátory mohou být přetíženy pouze jako nestatické členy:

- `=` přiřazení

- Přístup ke členu třídy `->`

- `[]` pro dolní index

- `()` volání funkce

Možné příčiny C2801:

- Přetížený operátor není členem třídy, struktury nebo sjednocení.

- Přetížený operátor je deklarován `static`.

- Následující ukázka generuje C2801:

```cpp
// C2801.cpp
// compile with: /c
operator[]();   // C2801 not a member
class A {
   static operator->();   // C2801 static
   operator()();   // OK
};
```
