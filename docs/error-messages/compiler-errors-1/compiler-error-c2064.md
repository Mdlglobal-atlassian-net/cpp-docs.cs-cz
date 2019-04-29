---
title: Chyba kompilátoru C2064
ms.date: 11/04/2016
f1_keywords:
- C2064
helpviewer_keywords:
- C2064
ms.assetid: 6cda05da-f437-4f50-9813-ae69538713a3
ms.openlocfilehash: 8af20c5172cddd0194ed018c13960bbed7859674
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62386028"
---
# <a name="compiler-error-c2064"></a>Chyba kompilátoru C2064

Termín se nevyhodnocuje na funkci s argumenty N

Je provedeno volání funkce prostřednictvím výrazu. Výraz se nevyhodnocuje na ukazatel na funkci, která přijímá zadaný počet argumentů.

V tomto příkladu kód pokusí volat jiné funkce jako funkce. Následující ukázka generuje C2064:

```
// C2064.cpp
int i, j;
char* p;
void func() {
   j = i();    // C2064, i is not a function
   p();        // C2064, p doesn't point to a function
}
```

Ukazatele na nestatické členské funkce je nutné volat z kontextu instance objektu. Následující ukázka generuje C2064 a ukazuje, jak ho opravit:

```
// C2064b.cpp
struct C {
   void func1(){}
   void func2(){}
};

typedef void (C::*pFunc)();

int main() {
   C c;
   pFunc funcArray[2] = {&C::func1, &C::func2};
   (funcArray[0])();    // C2064
   (c.*funcArray[0])(); // OK - function called in instance context
}
```

V rámci třídy musíte uvést ukazatelů na členské funkce také volání kontextu objektu. Následující ukázka generuje C2064 a ukazuje, jak ho opravit:

```
// C2064d.cpp
// Compile by using: cl /c /W4 C2064d.cpp
struct C {
   typedef void (C::*pFunc)();
   pFunc funcArray[2];
   void func1(){}
   void func2(){}
   C() {
      funcArray[0] = &C::func1;
      funcArray[1] = &C::func2;
   }
   void func3() {
      (funcArray[0])();   // C2064
      (this->*funcArray[0])(); // OK - called in this instance context
   }
};
```