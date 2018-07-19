---
title: Upozornění (úroveň 4) C4690 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 07/03/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4690
dev_langs:
- C++
helpviewer_keywords:
- C4690
ms.assetid: 080a0ea1-458b-477b-a37a-4a34c94709ff
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 04fb68bdab762f0f541849fad1568caff836b623
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/05/2018
ms.locfileid: "37853319"
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
