---
title: Kompilátor upozornění (úroveň 1) C4806
ms.date: 11/04/2016
f1_keywords:
- C4806
helpviewer_keywords:
- C4806
ms.assetid: 79eb74cd-b925-4b5b-84e1-8ae6f33e38b3
ms.openlocfilehash: b6fc5708d4e2f9982ceaab57260f13e134e4d247
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50578256"
---
# <a name="compiler-warning-level-1-c4806"></a>Kompilátor upozornění (úroveň 1) C4806

'operation': nebezpečná operace: žádná hodnota typu 'type' povýšen na typ "typ" se nemůže rovnat dané konstantě

Tato zpráva zobrazí upozornění s kódem, jako `b == 3`, kde `b` má typ `bool`. Podpora pravidla Příčina `bool` má být převeden na `int`. Toto je právní, ale nemůže být nikdy **true**. Následující ukázka generuje C4806:

```
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