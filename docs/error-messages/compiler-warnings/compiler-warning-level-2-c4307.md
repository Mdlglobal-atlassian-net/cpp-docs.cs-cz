---
title: Kompilátor upozornění (úroveň 2) C4307
ms.date: 11/04/2016
f1_keywords:
- C4307
helpviewer_keywords:
- C4307
ms.assetid: 7cca11e9-be61-49e4-8b15-88b84f0cbf07
ms.openlocfilehash: e9ad30f60260893130beed921aab811c894868cc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50528151"
---
# <a name="compiler-warning-level-2-c4307"></a>Kompilátor upozornění (úroveň 2) C4307

'operator': přetečení celočíselné konstanty

Operátor, který se používá ve výrazu, jehož výsledkem došlo k přetečení místa pro něj přidělené celočíselná konstanta. Budete muset použít větší typ pro konstantu. A **znaménkem** obsahuje hodnotu menší než `unsigned int` protože **znaménkem** jeden bit používá k reprezentaci znaménko.

Následující ukázka generuje C4307:

```
// C4307.cpp
// compile with: /W2
int i = 2000000000 + 2000000000;   // C4307
int j = (unsigned)2000000000 + 2000000000;   // OK

int main()
{
}
```