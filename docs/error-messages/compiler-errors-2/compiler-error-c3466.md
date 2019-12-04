---
title: Chyba kompilátoru C3466
ms.date: 11/04/2016
f1_keywords:
- C3466
helpviewer_keywords:
- C3466
ms.assetid: 69a877d9-a749-474b-bfc3-8d3fd53ba8fd
ms.openlocfilehash: c51dffb1fd8c0a7ef962566635976acca8a3776f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74742636"
---
# <a name="compiler-error-c3466"></a>Chyba kompilátoru C3466

' type ': specializace obecné třídy nemůže být předána

Nelze použít přesměrování typu u specializace obecné třídy.

Další informace naleznete v tématu [předávání typů (C++/CLI)](../../extensions/type-forwarding-cpp-cli.md).

## <a name="example"></a>Příklad

Následující příklad vytvoří komponentu.

```cpp
// C3466.cpp
// compile with: /clr /LD
generic<typename T>
public ref class GR {};

public ref class GR2 {};
```

## <a name="example"></a>Příklad

Následující ukázka generuje C3466.

```cpp
// C3466_b.cpp
// compile with: /clr /c
#using "C3466.dll"
[assembly:TypeForwardedTo(GR<int>::typeid)];   // C3466
[assembly:TypeForwardedTo(GR2::typeid)];   // OK
```
