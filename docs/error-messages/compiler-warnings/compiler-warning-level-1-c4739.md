---
title: Upozornění kompilátoru (úroveň 1) C4739
ms.date: 11/04/2016
f1_keywords:
- C4739
helpviewer_keywords:
- C4739
ms.assetid: 600873b3-7c85-4cd4-944e-cd8e01bfcbb0
ms.openlocfilehash: 9c68a9e0a2873de7e919fafbef68835f0970c03b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80185695"
---
# <a name="compiler-warning-level-1-c4739"></a>Upozornění kompilátoru (úroveň 1) C4739

odkaz na proměnnou var překračuje její prostor úložiště.

Proměnné byla přiřazena hodnota, ale hodnota je větší než velikost proměnné. Paměť bude zapsána za rámec místa v paměti proměnné a může dojít ke ztrátě dat.

Chcete-li toto upozornění vyřešit, přiřaďte hodnotu pouze proměnné, jejíž velikost může být přizpůsobena hodnotě.

Následující ukázka generuje C4739:

```cpp
// C4739.cpp
// compile with: /RTCs /Zi /W1 /c
char *pc;
int main() {
   char c;
   *(int *)&c = 1;   // C4739

   // OK
   *(char *)&c = 1;
}
```
