---
title: Compiler Error C3298
ms.date: 11/04/2016
f1_keywords:
- C3298
helpviewer_keywords:
- C3298
ms.assetid: 458c2680-95bb-4d5e-895f-ce4115844193
ms.openlocfilehash: fe6913d402c6ce4df3551c159eb56a12590799cb
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2019
ms.locfileid: "58773894"
---
# <a name="compiler-error-c3298"></a>Compiler Error C3298

"constraint_1": 'constraint_2' nelze použít jako omezení, protože má omezení ref "constraint_2" a 'constraint_1' má omezení hodnoty

Nelze zadat vzájemně se vylučující charakteristiky pro omezení. Například parametr obecného typu nemůže být omezen na typ hodnoty a typ odkazu.

Další informace najdete v tématu [omezení parametrů obecných typů (C + +/ CLI)](../../extensions/constraints-on-generic-type-parameters-cpp-cli.md).

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