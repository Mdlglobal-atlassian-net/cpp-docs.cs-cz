---
title: Chyba kompilátoru C2619
ms.date: 11/04/2016
f1_keywords:
- C2619
helpviewer_keywords:
- C2619
ms.assetid: c826f8ab-d66a-4b79-a0b2-93b0af8c41ac
ms.openlocfilehash: f82b315a3e7ae4bb1f6d281e1d80ddc2c7fb0dea
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50662910"
---
# <a name="compiler-error-c2619"></a>Chyba kompilátoru C2619

'identifier': Statický datový člen není povolený v anonymní struktury nebo sjednocení

Člen anonymní struktury nebo sjednocení je deklarovaný `static`.

Následující ukázka generuje C2619 a ukazuje, jak ho opravit tak, že odeberete static – klíčové slovo.

```
// C2619.cpp
int main() {
   union { static int j; };  // C2619
   union { int j; };  // OK
}
```