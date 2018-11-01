---
title: Chyba kompilátoru C2046
ms.date: 11/04/2016
f1_keywords:
- C2046
helpviewer_keywords:
- C2046
ms.assetid: f0c8f9dd-dbd7-4c4a-8838-fde54208ec71
ms.openlocfilehash: b502c70c62d87d6807f586e289aaa5c67be9f048
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50649550"
---
# <a name="compiler-error-c2046"></a>Chyba kompilátoru C2046

Neplatný případ

Klíčové slovo `case` může vyskytovat jenom ve `switch` příkazu.

Následující ukázka generuje C2046:

```
// C2046.cpp
int main() {
   case 0:   // C2046
}
```

Možná řešení:

```
// C2046b.cpp
int main() {
   int i = 0;

   switch(i) {
      case 0:
      break;

      default:
      break;
   }
}
```