---
title: Chyba kompilátoru C2589
ms.date: 11/04/2016
f1_keywords:
- C2589
helpviewer_keywords:
- C2589
ms.assetid: 1d7942c7-8a81-4bb4-b272-76a0019e8513
ms.openlocfilehash: 18d8f7130c34f5e1e33bc7aa9b9463f50c243045
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50587310"
---
# <a name="compiler-error-c2589"></a>Chyba kompilátoru C2589

'identifier': neplatný token na pravé straně '::'

Pokud třída, struktura nebo sjednocení název se zobrazí na levé straně operátoru rozlišení oboru (double dvojtečky), musí být token na pravé straně třídy, struktury nebo člen sjednocení. Žádné globálního identifikátoru, jinak může objevit na pravé straně.

Operátor rozlišení oboru nelze přetížit.

Následující ukázka generuje C2589:

```
// C2589.cpp
void Test(){}
class A {};
void operator :: ();   // C2589

int main() {
   ::Test();
}
```