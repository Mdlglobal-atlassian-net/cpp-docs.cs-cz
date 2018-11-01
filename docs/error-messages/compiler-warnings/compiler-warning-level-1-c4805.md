---
title: Kompilátor upozornění (úroveň 1) C4805
ms.date: 11/04/2016
f1_keywords:
- C4805
helpviewer_keywords:
- C4805
ms.assetid: 99c7b7e2-272e-4ab5-8580-17c42e62e2ef
ms.openlocfilehash: 3bbce2529b208b764fa28bad1d67e1bbb38ec127
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50662745"
---
# <a name="compiler-warning-level-1-c4805"></a>Kompilátor upozornění (úroveň 1) C4805

'operation': potenciálně nebezpečné směšování typu "typ" a zadejte "typ" v operaci

Toto upozornění je generováno pro operace porovnání mezi [bool](../../cpp/bool-cpp.md) a [int](../../c-language/integer-types.md). Následující ukázka generuje C4805:

```
// C4805.cpp
// compile with: /W1
int main() {
   int i = 1;
   bool b = true;

   if (i == b) {   // C4805, comparing bool and int variables
   }
}
```