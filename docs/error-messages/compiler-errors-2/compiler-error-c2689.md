---
title: Chyba kompilátoru C2689
ms.date: 11/04/2016
f1_keywords:
- C2689
helpviewer_keywords:
- C2689
ms.assetid: b5216fba-524d-4194-9168-26e9dc5210ce
ms.openlocfilehash: fb9a45f775da582daa0fbe421f29b6e469a91197
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50484549"
---
# <a name="compiler-error-c2689"></a>Chyba kompilátoru C2689

'function': funkce friend nemůže být definovaná v rámci lokální třídy

Můžete deklarovat, ale nejsou definovány spřátelené funkce v lokální třídy.

Následující ukázka generuje C2689:

```
// C2689.cpp
// compile with: /c
void g() {
   void f2();
   class X {
      friend void f2(){}   // C2689
      friend void f2();   // OK
   };
}
```