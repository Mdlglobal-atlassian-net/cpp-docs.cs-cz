---
title: Upozornění kompilátoru (úroveň 1) C4806
ms.date: 11/04/2016
f1_keywords:
- C4806
helpviewer_keywords:
- C4806
ms.assetid: 79eb74cd-b925-4b5b-84e1-8ae6f33e38b3
ms.openlocfilehash: 5895e9bf489e240b1eff6f1499b711047ea74b9b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175048"
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
