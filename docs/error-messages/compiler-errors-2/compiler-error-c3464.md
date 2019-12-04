---
title: Chyba kompilátoru C3464
ms.date: 11/04/2016
f1_keywords:
- C3464
helpviewer_keywords:
- C3464
ms.assetid: 0ede05dc-4486-4921-8e8c-78ab5a2e09c5
ms.openlocfilehash: bcbacf6ad3f3eda1b1f7448f60278bddfc30f4e6
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756575"
---
# <a name="compiler-error-c3464"></a>Chyba kompilátoru C3464

typ vnořeného typu nemůže být předán.

Předávání typů nefunguje u vnořených typů.

Další informace naleznete v tématu [předávání typů (C++/CLI)](../../extensions/type-forwarding-cpp-cli.md).

## <a name="example"></a>Příklad

Následující příklad vytvoří komponentu.

```cpp
// C3464.cpp
// compile with: /LD /clr
public ref class R {
public:
   ref class N {};
};
```

## <a name="example"></a>Příklad

Následující ukázka generuje C3464.

```cpp
// C3464_b.cpp
// compile with: /clr /c
#using "C3464.dll"
[assembly:TypeForwardedTo(R::N::typeid)];   // C3464
[assembly:TypeForwardedTo(R::typeid)];   // OK
```
