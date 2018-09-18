---
title: Chyba kompilátoru C3298 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3298
dev_langs:
- C++
helpviewer_keywords:
- C3298
ms.assetid: 458c2680-95bb-4d5e-895f-ce4115844193
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 06296fed3f33b56cb53cf3bc4531205638f0a204
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46053677"
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