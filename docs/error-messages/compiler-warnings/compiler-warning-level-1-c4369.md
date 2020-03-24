---
title: Upozornění kompilátoru (úroveň 1) C4369
ms.date: 11/04/2016
f1_keywords:
- C4369
helpviewer_keywords:
- C4369
ms.assetid: ade87e84-36be-4e00-be99-2930af848feb
ms.openlocfilehash: b0d99792e3e0ea372c8629319553dd9a59ad4b47
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187060"
---
# <a name="compiler-warning-level-1-c4369"></a>Upozornění kompilátoru (úroveň 1) C4369

' enumerátor ': hodnota čítače výčtu ' value ' nemůže být reprezentována jako typ ' type ', hodnota je ' new_value '

Enumerátor byl vypočítán jako větší než největší hodnota zadaného základního typu.  To způsobilo přetečení a kompilátor zabalí hodnotu enumerátoru k nejnižší možné hodnotě pro daný typ.

## <a name="example"></a>Příklad

Následující ukázka generuje C4369.

```cpp
// C4369.cpp
// compile with: /W1
int main() {
   enum Color: char { red = 0x7e, green, blue };   // C4369
   enum Color2: char { red2 = 0x7d, green2, blue2};   // OK
}
```
