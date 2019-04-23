---
title: Chyba kompilátoru C3900
ms.date: 11/04/2016
f1_keywords:
- C3900
helpviewer_keywords:
- C3900
ms.assetid: a94cc561-8fa8-4344-9e01-e81ff462fae5
ms.openlocfilehash: 35df94ccfcd7942f9057cb37ceee349c09b80607
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59776246"
---
# <a name="compiler-error-c3900"></a>Chyba kompilátoru C3900

'member': není povolené v aktuálním rozsahu.

Vlastnost bloky může obsahovat deklarace funkcí a pouze definice vložené funkce. Kromě funkcí se žádní členové jsou povoleny v blocích po vlastnost. Žádné – definice TypeDef, operátory nebo spřátelené funkce jsou povoleny. Další informace najdete v tématu [vlastnost](../../extensions/property-cpp-component-extensions.md).

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