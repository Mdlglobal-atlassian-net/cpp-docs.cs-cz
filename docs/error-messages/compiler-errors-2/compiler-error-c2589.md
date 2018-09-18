---
title: Chyba kompilátoru C2589 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2589
dev_langs:
- C++
helpviewer_keywords:
- C2589
ms.assetid: 1d7942c7-8a81-4bb4-b272-76a0019e8513
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2db5dde898a3e5918eed62b2b32231b5d7ed014f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46046053"
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