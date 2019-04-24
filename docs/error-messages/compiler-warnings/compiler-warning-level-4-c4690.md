---
title: Kompilátor upozornění (úroveň 4) C4690
ms.date: 07/03/2018
f1_keywords:
- C4690
helpviewer_keywords:
- C4690
ms.assetid: 080a0ea1-458b-477b-a37a-4a34c94709ff
ms.openlocfilehash: c7facdde54b44ba2ce07db0447b251d7014f76c8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62324581"
---
# <a name="compiler-warning-level-4-c4690"></a>Kompilátor upozornění (úroveň 4) C4690

> \[ emitidl (pop)]: Další POP než push

## <a name="remarks"></a>Poznámky

[Emitidl](../../windows/emitidl.md) atribut byl odebrán ještě jednou, které bylo vloženo.

## <a name="example"></a>Příklad

Následující ukázka generuje C4690. Chcete-li tento problém vyřešit, ujistěte se, že atribut vyjmut přesně tak, jak ho tolikrát, kolikrát je vloženo.

```cpp
// C4690.cpp
// compile with: /c /W4
[emitidl(pop)];   // C4690
class x {};
```
