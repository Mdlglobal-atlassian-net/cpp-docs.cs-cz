---
title: Chyba kompilátoru C2733
ms.date: 11/04/2016
f1_keywords:
- C2733
helpviewer_keywords:
- C2733
ms.assetid: 67f83561-c633-407c-a2ee-f9fd16e165bf
ms.openlocfilehash: 26819f1928223b5fa96d275290105f32787057f5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50518843"
---
# <a name="compiler-error-c2733"></a>Chyba kompilátoru C2733

druhé propojení C-linkage přetížení funkce 'function' není povoleno

Více než jeden přetížené funkce je deklarována s C-linkage. Pokud používáte C-linkage, může být pouze jednu formu zadanou funkci externí. Protože přetížené funkce mají stejné nedekorovaný název, nelze použít s programy C.

Následující ukázka generuje C2733:

```
// C2733.cpp
extern "C" {
   void F1(int);
}

extern "C" {
   void F1();   // C2733
   // try the following line instead
   // void F2();
}
```