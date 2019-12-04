---
title: Chyba kompilátoru C3238
ms.date: 11/04/2016
f1_keywords:
- C3238
helpviewer_keywords:
- C3238
ms.assetid: 19942497-b3c5-4df0-9144-142ced92468b
ms.openlocfilehash: 6f60a9abbc5702c1a0d14d0f894c9b1684378c3f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759357"
---
# <a name="compiler-error-c3238"></a>Chyba kompilátoru C3238

Typ: typ s tímto názvem už je předaný sestavení Assembly.

Typ byl definován v klientské aplikaci, která je také definována prostřednictvím syntaxe předávání typu v odkazovaném sestavení. V oboru aplikace nelze definovat oba typy.

Další informace najdete v tématu [přesměrování typu (C++/CLI)](../../extensions/type-forwarding-cpp-cli.md) .

## <a name="example"></a>Příklad

Následující příklad vytvoří sestavení, které obsahuje typ, který byl předán z jiného sestavení.

```cpp
// C3238.cpp
// compile with: /clr /LD
public ref class R {};
```

## <a name="example"></a>Příklad

Následující příklad vytvoří sestavení, které slouží k zahrnutí definice typu, ale neobsahuje pouze syntaxi předávání typu.

```cpp
// C3238_b.cpp
// compile with: /clr /LD
#using "C3238.dll"
[ assembly:TypeForwardedTo(R::typeid) ];
```

## <a name="example"></a>Příklad

Následující ukázka generuje C3238.

```cpp
// C3238_c.cpp
// compile with: /clr /c
// C3238 expected
// Delete the following line to resolve.
#using "C3238_b.dll"
public ref class R {};
```
