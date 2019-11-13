---
title: Upozornění kompilátoru (úroveň 1) C4806
ms.date: 11/04/2016
f1_keywords:
- C4806
helpviewer_keywords:
- C4806
ms.assetid: 79eb74cd-b925-4b5b-84e1-8ae6f33e38b3
ms.openlocfilehash: dae6ed7d7a38daf0ce525ae62409823212db711b
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052367"
---
# <a name="compiler-warning-level-1-c4806"></a>Upozornění kompilátoru (úroveň 1) C4806

' operation ': nebezpečná operace: žádná hodnota typu typu zvýšená na typ ' type ' se může rovnat dané konstantě.

Tato zpráva se upozorní na kód, například `b == 3`, kde `b` je typu `bool`. Pravidla propagace způsobují, `bool` budou povýšeny na `int`. To je právní, ale nemůže mít nikdy **hodnotu true**. Následující ukázka generuje C4806:

```cpp
// C4806.cpp
// compile with: /W1
int main()
{
   bool b = true;
   // try..
   // int b = true;

   if (b == 3)   // C4806
   {
      b = false;
   }
}
```