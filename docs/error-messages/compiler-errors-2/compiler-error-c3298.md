---
title: Chyba kompilátoru C3298
ms.date: 11/04/2016
f1_keywords:
- C3298
helpviewer_keywords:
- C3298
ms.assetid: 458c2680-95bb-4d5e-895f-ce4115844193
ms.openlocfilehash: d5e9586b026e0092491c80c23f55080354c9e465
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760072"
---
# <a name="compiler-error-c3298"></a>Chyba kompilátoru C3298

' constraint_1 ': nelze použít ' constraint_2 ' jako omezení, protože ' constraint_2 ' má omezení ref a ' constraint_1 ' má omezení hodnoty

U omezení nelze zadat vzájemně se vylučující charakteristiky. Například parametr obecného typu nemůže být omezen na typ hodnoty i typ odkazu.

Další informace najdete v tématu [omezení parametrů obecného typuC++(/CLI)](../../extensions/constraints-on-generic-type-parameters-cpp-cli.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C3298.

```cpp
// C3298.cpp
// compile with: /clr /c
generic<class T, class U>
where T : ref class
where U : T, value class   // C3298
public ref struct R {};
```
