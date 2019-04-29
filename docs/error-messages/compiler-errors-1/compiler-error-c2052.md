---
title: Chyba kompilátoru C2052
ms.date: 11/04/2016
f1_keywords:
- C2052
helpviewer_keywords:
- C2052
ms.assetid: 922ca43b-b64b-4ef7-9611-c7313be3fd79
ms.openlocfilehash: 2f7d77dbfcf8eb13b1c4b1a5f50750f954fd9281
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62408807"
---
# <a name="compiler-error-c2052"></a>Chyba kompilátoru C2052

'type': Neplatný typ pro výraz case

Výrazy Case musí být konstanty typu integer.

Následující ukázka generuje C2052:

```
// C2052.cpp
int main() {
   int index = 0;
   switch (index) {
      case 1:
         return 24;
      case 1.0:   // C2052
      // try the following line instead
      // case 2:
         return 23;
   }
}
```