---
title: Chyba kompilátoru C2178 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 05/08/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2178
dev_langs:
- C++
helpviewer_keywords:
- C2178
ms.assetid: 79a14158-17f3-4221-bd06-9d675c49cef4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: af9efdb3258e6793a17a26b552df8ba4e63c9107
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46102332"
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
