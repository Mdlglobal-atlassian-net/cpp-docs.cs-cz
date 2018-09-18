---
title: Chyba kompilátoru C2319 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2319
dev_langs:
- C++
helpviewer_keywords:
- C2319
ms.assetid: 25263e6e-f5ba-4d2c-8727-8c2d8ca2e5ce
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f485d26ac2a05cc91a1c918c63e319e893b8cf95
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46103142"
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