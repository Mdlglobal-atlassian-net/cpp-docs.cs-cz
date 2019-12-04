---
title: Chyba kompilátoru C2134
ms.date: 11/04/2016
f1_keywords:
- C2134
ms.assetid: d45cb3e8-0be4-4bd6-8be9-5f8d2384363f
ms.openlocfilehash: a50a94e195c823176e8463f9d0471530b81734c4
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757498"
---
# <a name="compiler-error-c2134"></a>Chyba kompilátoru C2134

' function ': výsledkem volání není konstantní výraz

Funkce deklarovaná jako constexpr může volat jenom jiné funkce deklarované jako constexpr.

Následující ukázka generuje C2134:

```cpp
// C2134.cpp
// compile with: /c
int A() {
    return 42;
};

constexpr int B() {
    return A();  // Error C2134: 'A': call does not result in a constant expression.
}
```

Možné řešení:

```cpp
// C2134b.cpp
constexpr int A() {  // add constexpr to A, since it meets the requirements of constexpr.
    return 42;
};

constexpr int B() {
    return A();  // No error
}
```
