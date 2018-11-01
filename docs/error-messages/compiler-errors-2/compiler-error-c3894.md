---
title: Chyba kompilátoru C3894
ms.date: 11/04/2016
f1_keywords:
- C3894
helpviewer_keywords:
- C3894
ms.assetid: 6d5ac903-1dea-431d-8e3a-cebca4342983
ms.openlocfilehash: 4d935e140d89cb5c3714450597677a7a02a245e8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50496041"
---
# <a name="compiler-error-c3894"></a>Chyba kompilátoru C3894

'příkaz var': použití l-value statického datového členu initonly je povolený jenom v konstruktoru class třídy 'class'

Statické [initonly](../../dotnet/initonly-cpp-cli.md) datové členy jde použít jenom jako l hodnoty na jejich bod prohlášení nebo ve statickém konstruktoru.

Datové členy initonly (nestatické) instance jde použít jenom jako l hodnoty na jejich bod deklarace nebo v instančních konstruktorech (nestatické).

Následující ukázka generuje C3894:

```
// C3894.cpp
// compile with: /clr
ref struct Y1 {
   initonly static int data_var = 0;

public:
   // class constructor
   static Y1() {
      data_var = 99;   // OK
      System::Console::WriteLine("in static constructor");
   }

   // not the class constructor
   Y1(int i) {
      data_var = i;   // C3894
   }

   static void Test() {}

};

int main() {
   Y1::data_var = 88;   // C3894
   int i = Y1::data_var;
   Y1 ^ MyY1 = gcnew Y1(99);
   Y1::Test();
}
```