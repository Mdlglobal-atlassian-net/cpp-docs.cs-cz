---
title: Chyba kompilátoru C2178
ms.date: 05/08/2017
f1_keywords:
- C2178
helpviewer_keywords:
- C2178
ms.assetid: 79a14158-17f3-4221-bd06-9d675c49cef4
ms.openlocfilehash: cd153bb5b331872bfe35b046d41612998bd0eff7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50622557"
---
# <a name="compiler-error-c2178"></a>Chyba kompilátoru C2178

"*identifikátor*"se nedá deklarovat pomocí"*specifikátor*" specifikátor

A `mutable` byl použit specifikátor v deklaraci, ale specifikátor není povolený v tomto kontextu.

`mutable` Specifikátor lze použít pouze u názvů datové členy třídy a nejde použít pro názvy deklarované `const` nebo `static`a nedá se použít k odkazování členů.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak může dojít k C2178 a jak ho opravit.

```
// C2178.cpp
// compile with: cl /c /W4 C2178.cpp

class S {
    mutable const int i; // C2178
    // To fix, declare either const or mutable, not both.
};

mutable int x = 4; // C2178
// To fix, remove mutable keyword
```
