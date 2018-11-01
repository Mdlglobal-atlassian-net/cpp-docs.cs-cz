---
title: Kompilátor upozornění (úroveň 3) C4538
ms.date: 11/04/2016
f1_keywords:
- C4538
helpviewer_keywords:
- C4538
ms.assetid: 747e3d51-b6d0-41c1-a726-7af3253b59d7
ms.openlocfilehash: 81634ed45ad7d09a35f8399774920f6445628dee
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50569361"
---
# <a name="compiler-warning-level-3-c4538"></a>Kompilátor upozornění (úroveň 3) C4538

'type': kvalifikátory const/volatile pro tento typ nejsou podporované

Klíčové slovo kvalifikátor nesprávně použila na pole. Další informace najdete v tématu [pole](../../windows/arrays-cpp-component-extensions.md).

Následující ukázka generuje C4538:

```
// C4538.cpp
// compile with: /clr /W3 /LD
const array<int> ^f1();   // C4538
array<const int> ^f2();   // OK
```