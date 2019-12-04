---
title: Chyba kompilátoru C2361
ms.date: 11/04/2016
f1_keywords:
- C2361
helpviewer_keywords:
- C2361
ms.assetid: efbdaeb9-891c-4f7d-97da-89088a8413f3
ms.openlocfilehash: 747b85b57bee9e53f13a978254798a1dc268ef85
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759890"
---
# <a name="compiler-error-c2361"></a>Chyba kompilátoru C2361

Inicializace identifikátoru se přeskočila jmenovkou default.

Inicializace `identifier` může být vynechána v příkazu `switch`. Nejde přeskočit deklaraci s inicializátorem, pokud deklarace není uzavřená v bloku. (Pokud není deklarována v rámci bloku, proměnná je v rozsahu až do konce příkazu `switch`.)

Následující ukázka generuje C2361:

```cpp
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

Možné řešení:

```cpp
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
