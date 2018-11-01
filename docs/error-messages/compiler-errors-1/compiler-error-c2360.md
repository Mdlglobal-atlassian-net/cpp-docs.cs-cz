---
title: Chyba kompilátoru C2360
ms.date: 11/04/2016
f1_keywords:
- C2360
helpviewer_keywords:
- C2360
ms.assetid: 51bfd2ee-8108-4777-aa93-148b9cebfa83
ms.openlocfilehash: 6e956ccb021dc3bce4d107e4aa6e0bbe4356283b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50498173"
---
# <a name="compiler-error-c2360"></a>Chyba kompilátoru C2360

Inicializace 'identifier' je podle popisku 'case' přeskočila.

Inicializace `identifier` mohly být přeskočeny, v `switch` příkazu. Nelze přejít po deklaraci s inicializátorem, není-li prohlášení je uzavřen v bloku. (Pokud je deklarovaná v rámci bloku, proměnná je v rámci oboru až do konce `switch` příkazu.)

Následující ukázka generuje C2360:

```
// C2360.cpp
int main() {
   int x = 0;
   switch ( x ) {
   case 0 :
      int i = 1;
      { int j = 1; }
   case 1 :   // C2360
      int k = 1;
   }
}
```

Možná řešení:

```
// C2360b.cpp
int main() {
   int x = 0;
   switch ( x ) {
   case 0 :
      { int j = 1; int i = 1;}
   case 1 :
      int k = 1;
   }
}
```