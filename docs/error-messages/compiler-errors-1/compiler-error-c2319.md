---
title: Chyba kompilátoru C2319
ms.date: 11/04/2016
f1_keywords:
- C2319
helpviewer_keywords:
- C2319
ms.assetid: 25263e6e-f5ba-4d2c-8727-8c2d8ca2e5ce
ms.openlocfilehash: f0ec35cfb74fd08180969344180ff42d485d58c0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62404296"
---
# <a name="compiler-error-c2319"></a>Chyba kompilátoru C2319

bloku try/catch musí následovat složený příkaz. Chybí "{"

A `try` nebo `catch` bloku není nalezen `try` nebo `catch` příkazu. Objekt musí být uzavřen ve složených závorkách.

Následující ukázka generuje C2319:

```
// C2319.cpp
// compile with: /EHsc
#include <eh.h>
class C {};
int main() {
   try {
      throw "ooops!";
   }
   catch( C ) ;    // C2319
   // try the following line instead
   // catch( C ) {}
}
```