---
title: Chyba kompilátoru C3904
ms.date: 11/04/2016
f1_keywords:
- C3904
helpviewer_keywords:
- C3904
ms.assetid: 08297605-e4f2-4c6c-b637-011f1fd40631
ms.openlocfilehash: 8c7f4a2861825a35d676328b5e283a5e4087d85b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50519779"
---
# <a name="compiler-error-c3904"></a>Chyba kompilátoru C3904

'property_accessor': musíte zadat počet parametrů:

Zkontrolujte počet parametrů ve vaší `get` a `set` metody proti vlastnost dimenze.

- Počet parametrů pro `get` metoda musí být roven počtu dimenzí vlastnosti nebo nulu pro neindexované vlastnosti.

- Počet parametrů `set` metoda musí být větší než počet rozměrů vlastnost.

Další informace najdete v tématu [vlastnost](../../windows/property-cpp-component-extensions.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C3904.

```
// C3904.cpp
// compile with: /clr /c
ref class X {
   property int P {
      // set
      void set();   // C3904
      // try the following line instead
      // void set(int);

      // get
      int get(int, int);   // C3904
      // try the following line instead
      // int get();
   };
};
```

## <a name="example"></a>Příklad

Následující ukázka generuje C3904.

```
// C3904b.cpp
// compile with: /clr /c
ref struct X {
   property int Q[double, double, float, float, void*, int] {
      // set
      void set(double, void*);   // C3904
      // try the following line instead
      // void set(double, double, float, float, void*, int, int);

      // get
      int get();   // C3904
      // try the following line instead
      // int get(double, double, float, float, void*, int);
   }
};
```