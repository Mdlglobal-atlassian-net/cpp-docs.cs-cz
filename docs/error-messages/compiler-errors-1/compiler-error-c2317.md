---
title: Chyba kompilátoru C2317 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2317
dev_langs:
- C++
helpviewer_keywords:
- C2317
ms.assetid: e44d129b-8d3e-4ce9-9d79-6791ee77f25e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: adf536fa1fd8976e3e3251514b3b7486eb57456c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46085365"
---
# <a name="compiler-error-c2317"></a>Chyba kompilátoru C2317

blok "akci" začínající na řádku 'number' nemá žádné obslužné rutiny catch

A `try` bloku musí mít aspoň jednu obslužnou rutinu catch.

Následující ukázka generuje C2317:

```
// C2317.cpp
// compile with: /EHsc
#include <eh.h>
int main() {
   try {
      throw "throw an exception";
   }
   // C2317, no catch handler
}
```

Možná řešení:

```
// C2317b.cpp
// compile with: /EHsc
#include <eh.h>
int main() {
   try {
      throw "throw an exception";
   }
   catch(char*) {}
}
```