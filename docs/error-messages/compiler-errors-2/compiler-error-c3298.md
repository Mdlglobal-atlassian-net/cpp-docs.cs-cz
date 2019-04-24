---
title: Compiler Error C3298
ms.date: 11/04/2016
f1_keywords:
- C3298
helpviewer_keywords:
- C3298
ms.assetid: 458c2680-95bb-4d5e-895f-ce4115844193
ms.openlocfilehash: fe6913d402c6ce4df3551c159eb56a12590799cb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62222528"
---
# <a name="compiler-error-c3298"></a>Compiler Error C3298

"constraint_1": 'constraint_2' nelze použít jako omezení, protože má omezení ref "constraint_2" a 'constraint_1' má omezení hodnoty

Nelze zadat vzájemně se vylučující charakteristiky pro omezení. Například parametr obecného typu nemůže být omezen na typ hodnoty a typ odkazu.

Další informace najdete v tématu [omezení parametrů obecných typů (C++vyhodnocovací)](../../extensions/constraints-on-generic-type-parameters-cpp-cli.md).

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