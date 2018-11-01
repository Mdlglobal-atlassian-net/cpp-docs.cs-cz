---
title: Chyba kompilátoru C3298
ms.date: 11/04/2016
f1_keywords:
- C3298
helpviewer_keywords:
- C3298
ms.assetid: 458c2680-95bb-4d5e-895f-ce4115844193
ms.openlocfilehash: 8a2d8f6ab72a5e72a646cb1fca64635bc72dd2ee
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50492832"
---
# <a name="compiler-error-c3298"></a>Chyba kompilátoru C3298

"constraint_1": 'constraint_2' nelze použít jako omezení, protože má omezení ref "constraint_2" a 'constraint_1' má omezení hodnoty

Nelze zadat vzájemně se vylučující charakteristiky pro omezení. Například parametr obecného typu nemůže být omezen na typ hodnoty a typ odkazu.

Další informace najdete v tématu [omezení parametrů obecných typů (C + +/ CLI)](../../windows/constraints-on-generic-type-parameters-cpp-cli.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C3298.

```
// C3298.cpp
// compile with: /clr /c
generic<class T, class U>
where T : ref class
where U : T, value class   // C3298
public ref struct R {};
```