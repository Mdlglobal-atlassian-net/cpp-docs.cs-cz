---
title: Kompilátor upozornění (úroveň 1) C4142
ms.date: 11/04/2016
f1_keywords:
- C4142
helpviewer_keywords:
- C4142
ms.assetid: 1fdfc3dc-60a2-4f00-b133-20e400f9b7a6
ms.openlocfilehash: 762f52c9f051a660cce68d424e02fc45422376e2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62302277"
---
# <a name="compiler-warning-level-1-c4142"></a>Kompilátor upozornění (úroveň 1) C4142

neškodné předefinování typu

Předefinovalo se typ způsobem, který nemá žádný vliv na generovaný kód.

Chcete-li vyřešit tak, že zkontrolujete následující možné příčiny:

- Členské funkce odvozené třídy má jiný typ vrácené z odpovídající členskou funkci základní třídy.

- Typ definovaný pomocí `typedef` příkaz je znovu definovat pomocí jiné syntaxe.

Následující ukázka generuje C4142:

```
// C4142.c
// compile with: /W1
float X2;
X2 = 2.0 + 1.0;   // C4142

int main() {
   float X2;
   X2 = 2.0 + 1.0;   // OK
}
```