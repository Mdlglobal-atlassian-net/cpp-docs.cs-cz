---
title: Chyba kompilátoru C3379
ms.date: 11/04/2016
f1_keywords:
- C3379
helpviewer_keywords:
- C3379
ms.assetid: a66c2c4e-091c-4426-9cde-7c4cfb2ffce1
ms.openlocfilehash: 2d6b2cb15cfaa0b72b946c0edb3b451737b51772
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50553501"
---
# <a name="compiler-error-c3379"></a>Chyba kompilátoru C3379

'class': vnořená třída nemůže mít specifikátor přístupu sestavení jako součást její deklarace

Při použití spravovaného typu, jako je například třídy nebo struktury, [veřejné](../../cpp/public-cpp.md) a [privátní](../../cpp/private-cpp.md) klíčová slova označuje, zda třída bude vystavená prostřednictvím metadata sestavení. `public` nebo `private` nelze použít pro vnořené třídy, který zdědí přístup k sestavení ohraničující třídy.

Při použití s [/CLR](../../build/reference/clr-common-language-runtime-compilation.md), `ref` a `value` klíčová slova znamenat, že je spravovaná třída (viz [třídy a struktury](../../windows/classes-and-structs-cpp-component-extensions.md)).

Následující ukázka generuje C3379:

```
// C3379a.cpp
// compile with: /clr
using namespace System;

public ref class A {
public:
   static int i = 9;

   public ref class BA {   // C3379
   // try the following line instead
   // ref class BA {
   public:
      static int ii = 8;
   };
};

int main() {

   A^ myA = gcnew A;
   Console::WriteLine(myA->i);

   A::BA^ myBA = gcnew A::BA;
   Console::WriteLine(myBA->ii);
}
```
