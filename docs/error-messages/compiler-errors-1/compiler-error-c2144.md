---
title: Compiler Error C2144
ms.date: 11/04/2016
f1_keywords:
- C2144
helpviewer_keywords:
- C2144
ms.assetid: 49f3959b-324f-4c06-9588-c0ecef5dc5b3
ms.openlocfilehash: a75330d26b0924e60f7e46d10d617341709d7e23
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59776103"
---
# <a name="compiler-error-c2144"></a>Compiler Error C2144

> Chyba syntaxe: "*typ*"musí předcházet párový příkaz"*token*.

Kompilátor očekává *token* a zjistili jsme *typ* místo.

Tato chyba může být způsobeno chybí pravá složená závorka, pravá závorka nebo středníkem.

C2144 může dojít také při pokusu o vytvoření makra z – klíčové slovo CLR, který obsahuje prázdný znak.

C2144 také může zobrazit, pokud se pokoušíte předávání typů. Zobrazit [předávání typu (C++vyhodnocovací)](../../extensions/type-forwarding-cpp-cli.md) Další informace.

## <a name="examples"></a>Příklady

Následující ukázka generuje C2144 a ukazuje způsob, jak ho opravit:

```cpp
// C2144.cpp
// compile with: /clr /c
#define REF ref
REF struct MyStruct0;   // C2144

// OK
#define REF1 ref struct
REF1 MyStruct1;
```

Následující ukázka generuje C2144 a ukazuje způsob, jak ho opravit:

```cpp
// C2144_2.cpp
// compile with: /clr /c
ref struct X {

   property double MultiDimProp[,,] {   // C2144
   // try the following line instead
   // property double MultiDimProp[int , int, int] {
      double get(int, int, int) { return 1; }
      void set(int i, int j, int k, double l) {}
   }

   property double MultiDimProp2[] {   // C2144
   // try the following line instead
   // property double MultiDimProp2[int] {
      double get(int) { return 1; }
      void set(int i, double l) {}
   }
};
```