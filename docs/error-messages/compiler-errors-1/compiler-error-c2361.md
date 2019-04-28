---
title: Chyba kompilátoru C2361
ms.date: 11/04/2016
f1_keywords:
- C2361
helpviewer_keywords:
- C2361
ms.assetid: efbdaeb9-891c-4f7d-97da-89088a8413f3
ms.openlocfilehash: ca03a42cbf746a1ef32d9c79c23de637f05b56fc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62364360"
---
# <a name="compiler-error-c2361"></a>Chyba kompilátoru C2361

Inicializace 'identifier' je podle popisku "default" přeskočila.

Inicializace `identifier` mohly být přeskočeny, v `switch` příkazu. Nelze přejít po deklaraci s inicializátorem, není-li prohlášení je uzavřen v bloku. (Pokud je deklarovaná v rámci bloku, proměnná je v rámci oboru až do konce `switch` příkazu.)

Následující ukázka generuje C2361:

```
// C2361.cpp
void func( void ) {
   int x;
   switch (x) {
   case 0 :
      int i = 1;
      { int j = 1; }
   default :   // C2361 error
      int k = 1;
   }
}
```

Možná řešení:

```
// C2361b.cpp
// compile with: /c
void func( void ) {
   int x = 0;
   switch (x) {
   case 0 :
      { int j = 1; int i = 1;}
   default :
      int k = 1;
   }
}
```