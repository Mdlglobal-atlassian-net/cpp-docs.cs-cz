---
title: Chyba kompilátoru C2589
ms.date: 11/04/2016
f1_keywords:
- C2589
helpviewer_keywords:
- C2589
ms.assetid: 1d7942c7-8a81-4bb4-b272-76a0019e8513
ms.openlocfilehash: 76cc35e57c1577ed23c043740f37c602600da542
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74748499"
---
# <a name="compiler-error-c2589"></a>Chyba kompilátoru C2589

identifikátor: neplatný token na pravé straně operátoru::

Pokud se název třídy, struktury nebo sjednocení nachází nalevo od operátoru rozlišení oboru (dvojité dvojtečky), token na pravé straně musí být členem třídy, struktury nebo sjednocení. V opačném případě se každý globální identifikátor může napravo zobrazit.

Operátor rozlišení oboru nemůže být přetížen.

Následující ukázka generuje C2589:

```cpp
// C2589.cpp
void Test(){}
class A {};
void operator :: ();   // C2589

int main() {
   ::Test();
}
```
