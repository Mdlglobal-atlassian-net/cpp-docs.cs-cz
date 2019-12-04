---
title: Chyba kompilátoru C2178
ms.date: 05/08/2017
f1_keywords:
- C2178
helpviewer_keywords:
- C2178
ms.assetid: 79a14158-17f3-4221-bd06-9d675c49cef4
ms.openlocfilehash: 85cac4919c048c30a3ed1ff5573a3c14b77da0bd
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74737189"
---
# <a name="compiler-error-c2178"></a>Chyba kompilátoru C2178

'*Identifier*' nemůže být deklarován specifikátorem '*specifikátor*'

V deklaraci byl použit specifikátor `mutable`, ale specifikátor není v tomto kontextu povolený.

Specifikátor `mutable` lze použít pouze pro názvy datových členů třídy a nelze jej použít pro názvy deklarované `const` nebo `static`a nelze jej použít pro členy odkazu.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak může C2178 nastat, a jak ho opravit.

```cpp
// C2178.cpp
// compile with: cl /c /W4 C2178.cpp

class S {
    mutable const int i; // C2178
    // To fix, declare either const or mutable, not both.
};

mutable int x = 4; // C2178
// To fix, remove mutable keyword
```
