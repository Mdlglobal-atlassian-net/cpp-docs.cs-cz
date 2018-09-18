---
title: Chyba kompilátoru C3287 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3287
dev_langs:
- C++
helpviewer_keywords:
- C3287
ms.assetid: c1fa73d2-2c82-4136-a7da-0e75e3b420ad
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b7e91878b6c6809fb875380430496db6d6e0b065
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46067451"
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