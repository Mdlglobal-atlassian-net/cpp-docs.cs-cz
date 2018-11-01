---
title: Kompilátor upozornění (úroveň 1) C4369
ms.date: 11/04/2016
f1_keywords:
- C4369
helpviewer_keywords:
- C4369
ms.assetid: ade87e84-36be-4e00-be99-2930af848feb
ms.openlocfilehash: b374b67fa3319be35490358d7664bcb45bc640db
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50623949"
---
# <a name="compiler-warning-level-1-c4369"></a>Kompilátor upozornění (úroveň 1) C4369

'čítače výčtu': hodnota výčtu 'value' nemůže být reprezentovaná jako 'type', hodnota je "nová_hodnota"

Enumerátor vypočítal být větší než největší hodnota zadaného základního typu.  To způsobilo přetečení a kompilátor zabalená hodnota enumerátoru na nejnižší možná hodnota pro typ.

## <a name="example"></a>Příklad

Následující ukázka generuje C4369.

```
// C4369.cpp
// compile with: /W1
int main() {
   enum Color: char { red = 0x7e, green, blue };   // C4369
   enum Color2: char { red2 = 0x7d, green2, blue2};   // OK
}
```