---
title: Chyba kompilátoru C2360
ms.date: 11/04/2016
f1_keywords:
- C2360
helpviewer_keywords:
- C2360
ms.assetid: 51bfd2ee-8108-4777-aa93-148b9cebfa83
ms.openlocfilehash: 226fcd8a27c9abdb789b8191a5cf4e59cc4a66cc
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759903"
---
# <a name="compiler-error-c2360"></a>Chyba kompilátoru C2360

Inicializace identifikátoru se přeskočila jmenovkou Case.

Inicializace `identifier` může být vynechána v příkazu `switch`. Nejde přeskočit deklaraci s inicializátorem, pokud deklarace není uzavřená v bloku. (Pokud není deklarována v rámci bloku, proměnná je v rozsahu až do konce příkazu `switch`.)

Následující ukázka generuje C2360:

```cpp
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

Možné řešení:

```cpp
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
