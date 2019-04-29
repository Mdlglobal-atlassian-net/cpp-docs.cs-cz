---
title: Kompilátor upozornění (úroveň 1) C4805
ms.date: 11/04/2016
f1_keywords:
- C4805
helpviewer_keywords:
- C4805
ms.assetid: 99c7b7e2-272e-4ab5-8580-17c42e62e2ef
ms.openlocfilehash: 3bbce2529b208b764fa28bad1d67e1bbb38ec127
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62406350"
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