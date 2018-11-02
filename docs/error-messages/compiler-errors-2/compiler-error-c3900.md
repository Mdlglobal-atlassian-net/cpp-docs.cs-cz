---
title: Chyba kompilátoru C3900
ms.date: 11/04/2016
f1_keywords:
- C3900
helpviewer_keywords:
- C3900
ms.assetid: a94cc561-8fa8-4344-9e01-e81ff462fae5
ms.openlocfilehash: d031b55407d108b4f8be362156911bfae688326a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50512356"
---
# <a name="compiler-error-c3900"></a>Chyba kompilátoru C3900

'member': není povolené v aktuálním rozsahu.

Vlastnost bloky může obsahovat deklarace funkcí a pouze definice vložené funkce. Kromě funkcí se žádní členové jsou povoleny v blocích po vlastnost. Žádné – definice TypeDef, operátory nebo spřátelené funkce jsou povoleny. Další informace najdete v tématu [vlastnost](../../windows/property-cpp-component-extensions.md).

Definice událostí může obsahovat pouze přístupové metody a funkce.

Následující ukázka generuje C3900:

```
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

```
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