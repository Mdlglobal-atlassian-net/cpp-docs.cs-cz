---
title: Chyba kompilátoru C2885 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2885
dev_langs:
- C++
helpviewer_keywords:
- C2885
ms.assetid: 7743e5f3-a034-44b4-9ee8-5a6254c27f8c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cf47d830980b9fb93481f575e3e3a806ce8bbf68
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46035692"
---
# <a name="compiler-error-c2885"></a>Chyba kompilátoru C2885

'class::identifier': není platná deklarace using na netřídním oborem

Použili jste [pomocí](../../cpp/using-declaration.md) deklarace nesprávně.

## <a name="example"></a>Příklad

Tuto chybu mohou být generovány jako důsledek kompilátoru prací, které bylo provedeno pro Visual C++ 2005: již není platný, aby `using` deklarace pro vnořený typ; musí explicitně kvalifikovat každý odkaz provedete vnořeného typu put v názvu typu místo nebo vytváření definice typu.

Následující ukázka generuje C2885.

```
// C2885.cpp
namespace MyNamespace {
   class X1 {};
}

struct MyStruct {
   struct X1 {
      int i;
   };
};

int main () {
   using MyStruct::X1;   // C2885

   // OK
   using MyNamespace::X1;
   X1 myX1;

   MyStruct::X1 X12;

   typedef MyStruct::X1 abc;
   abc X13;
   X13.i = 9;
}
```

## <a name="example"></a>Příklad

Pokud používáte `using` – klíčové slovo se členem třídy C++, musíte definovat člena v jiné třídy (třídy odvozené).

Následující ukázka generuje C2885.

```
// C2885_b.cpp
// compile with: /c
class A {
public:
   int i;
};

void z() {
   using A::i;   // C2885 not in a class
}

class B : public A {
public:
   using A::i;
};
```