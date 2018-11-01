---
title: Kompilátor upozornění (úroveň 1) C4813
ms.date: 11/04/2016
f1_keywords:
- C4813
helpviewer_keywords:
- C4813
ms.assetid: c30bf877-ab04-4fe4-897e-8162092426f0
ms.openlocfilehash: c6aaf3cc8e17cd1be1d9c964c03bb18b3bb0ff77
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50605189"
---
# <a name="compiler-warning-level-1-c4813"></a>Kompilátor upozornění (úroveň 1) C4813

'function': funkce friend lokální třídy musí mít byla deklarována

Spřátelené funkce v vnitřní třídu nebyl deklarován ve vnější třídy.

Následující ukázka generuje C4813:

```
// C4813.cpp
// compile with: /W1 /LD
void MyClass()
{
   // void func();
   class InnerClass
   {
      friend void func();   // C4813 uncomment declaration above
   };
}
```