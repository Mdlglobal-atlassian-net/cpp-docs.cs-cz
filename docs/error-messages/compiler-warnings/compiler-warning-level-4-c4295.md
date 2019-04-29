---
title: Kompilátor upozornění (úroveň 4) C4295
ms.date: 1/09/2018
f1_keywords:
- C4295
helpviewer_keywords:
- C4295
ms.assetid: 20dbff85-9f62-4ca3-8fe9-079d4512006d
ms.openlocfilehash: ed31ea19f9c36a9c6fab7452a4bfc3843a151059
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62400874"
---
# <a name="compiler-warning-level-4-c4295"></a>Kompilátor upozornění (úroveň 4) C4295

> "*pole*': pole je příliš malá, aby zahrnují ukončujícího znaku null

Pole byl inicializován, ale poslední znak v poli není null; přístup k poli jako řetězec může vést k neočekávaným výsledkům.

## <a name="example"></a>Příklad

Následující ukázka generuje C4295. Chcete-li vyřešit tento problém, můžete deklarovat velikost pole pro uchování větší ukončujícího znaku null z inicializátoru řetězec, nebo můžete použít seznam inicializátorů pole aby záměru vymazat, že je to pole `char`, není řetězec zakončený hodnotou null.

```C
// C4295.c
// compile with: /W4

int main() {
   char a[3] = "abc";           // C4295
   char b[3] = {'d', 'e', 'f'}; // No warning
   a[0] = b[2];
}
```
