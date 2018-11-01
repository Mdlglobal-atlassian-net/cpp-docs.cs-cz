---
title: Chyba kompilátoru C3287
ms.date: 11/04/2016
f1_keywords:
- C3287
helpviewer_keywords:
- C3287
ms.assetid: c1fa73d2-2c82-4136-a7da-0e75e3b420ad
ms.openlocfilehash: ab0b93aa1a74ea79515e24ef2b1e289cf0227dac
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50538676"
---
# <a name="compiler-error-c3287"></a>Chyba kompilátoru C3287

Typ 'type' (návratový typ GetEnumerator) musí mít vhodnou členskou funkci public MoveNext a veřejnou vlastnost Current

Uživatelem definované kolekci tříd musí obsahovat definice pro `MoveNext` a `Current`.

V tématu [jak: Iterate Over a User-Defined kolekce s pro jednotlivé](../../dotnet/how-to-iterate-over-a-user-defined-collection-with-for-each.md) Další informace.

## <a name="example"></a>Příklad

Následující ukázka generuje C3287.

```
// C3287.cpp
// compile with: /clr
using namespace System;

ref struct R {
   bool MoveNext() {
      return true;
   }
   property Object^ Current {
      Object^ get() {
         Object ^ o = gcnew Object;
         return o;
      }
   }
};

ref struct R2 {
   R ^GetEnumerator() {
      R^ r = gcnew R;
      return r;
   }
};

ref struct T {};

ref struct T2 {
   T ^GetEnumerator() {
      T^ t = gcnew T;
      return t;
   }
};

int main() {
   for each (int i in gcnew T2) {}   // C3287
   for each (int i in gcnew R2) {}   // OK
}
```