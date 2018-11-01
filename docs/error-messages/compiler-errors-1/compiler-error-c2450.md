---
title: Chyba kompilátoru C2450
ms.date: 11/04/2016
f1_keywords:
- C2450
helpviewer_keywords:
- C2450
ms.assetid: 929f1c06-8774-468b-be2a-f428757875a2
ms.openlocfilehash: 3cbab274f8f7cd04d5fb86db69572e0b7fc1c04e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50621800"
---
# <a name="compiler-error-c2450"></a>Chyba kompilátoru C2450

výraz přepínače typu 'type' je neplatný.

`switch` Výraz vyhodnocen jako neplatného typu. Musí být celočíselného typu nebo typ třídy s jednoznačný převod na typ integer. Pokud je vyhodnocen jako typ definovaný uživatelem, je třeba zadat operátoru převodu.

Následující ukázka generuje C2450:

```
// C2450.cpp
class X {
public:
   int i;
} x;

class Y {
public:
   int i;
   operator int() { return i; }   // conversion operator
} y;

int main() {
   int j = 1;
   switch ( x ) {   // C2450, x is not type int
   // try the following line instead
   // switch ( y ) {
      default:  ;
   }
}
```