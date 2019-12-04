---
title: Chyba kompilátoru C3900
ms.date: 11/04/2016
f1_keywords:
- C3900
helpviewer_keywords:
- C3900
ms.assetid: a94cc561-8fa8-4344-9e01-e81ff462fae5
ms.openlocfilehash: f1289fb9a4d60f2c75b54fd573c83064f1517282
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74749097"
---
# <a name="compiler-error-c3900"></a>Chyba kompilátoru C3900

member: není povolené v aktuálním oboru.

Bloky vlastností mohou obsahovat pouze deklarace funkcí a vložené definice funkcí. V blocích vlastností nejsou povoleny žádné jiné členy než funkce. Nejsou povoleny žádné definice typedef, operátory nebo funkce Friend. Další informace najdete v tématu [vlastnost](../../extensions/property-cpp-component-extensions.md).

Definice událostí můžou obsahovat jenom metody a funkce přístupu.

Následující ukázka generuje C3900:

```cpp
// C3900.cpp
// compile with: /clr
ref class X {
   property int P {
      void set(int);   // OK
      int i;   // C3900 variable declaration
   };
};
```

Následující ukázka generuje C3900:

```cpp
// C3900b.cpp
// compile with: /clr
using namespace System;
delegate void H();
ref class X {
   event H^ E {
      int m;   // C3900

      // OK
      void Test() {}

      void add( H^ h ) {}
      void remove( H^ h ) {}
      void raise( ) {}
   }
};
```
