---
title: Chyba kompilátoru C3379 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3379
dev_langs:
- C++
helpviewer_keywords:
- C3379
ms.assetid: a66c2c4e-091c-4426-9cde-7c4cfb2ffce1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f90a4ccc17e63c21d4b6fb26e607450849f27b48
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46109324"
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
