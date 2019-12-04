---
title: Chyba kompilátoru C2619
ms.date: 11/04/2016
f1_keywords:
- C2619
helpviewer_keywords:
- C2619
ms.assetid: c826f8ab-d66a-4b79-a0b2-93b0af8c41ac
ms.openlocfilehash: 3ca5ea4612091f1e3eee8fead2b1eaebb264b696
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74754768"
---
# <a name="compiler-error-c2619"></a>Chyba kompilátoru C2619

' identifier ': Statický datový člen není povolen v anonymní struktuře nebo sjednocení.

Člen anonymní struktury nebo sjednocení je deklarován `static`.

Následující ukázka vygeneruje C2619 a ukazuje, jak ji opravit odebráním klíčového slova static.

```cpp
// C2619.cpp
int main() {
   union { static int j; };  // C2619
   union { int j; };  // OK
}
```
