---
title: Chyba kompilátoru C2885
ms.date: 11/04/2016
f1_keywords:
- C2885
helpviewer_keywords:
- C2885
ms.assetid: 7743e5f3-a034-44b4-9ee8-5a6254c27f8c
ms.openlocfilehash: e60f3fff2ef61f4d6374072c05a2ad3e64a57031
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760925"
---
# <a name="compiler-error-c2885"></a>Chyba kompilátoru C2885

' class:: identifier ': nejedná se o platnou deklaraci using-Declaration v oboru, který není třídou.

Nesprávně jste použili deklaraci [using](../../cpp/using-declaration.md) .

## <a name="example"></a>Příklad

Tato chyba se může vygenerovat v důsledku práce s shodami s kompilátorem, která byla provedena pro sadu Visual Studio 2005: již není platná pro použití deklarace `using` vnořeného typu; musíte explicitně kvalifikovat každý odkaz, který uděláte na vnořený typ, vložit typ do oboru názvů nebo vytvořit typedef.

Následující ukázka generuje C2885.

```cpp
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

Použijete-li klíčové slovo `using` s členem třídy, C++ vyžaduje, abyste definovali tohoto člena uvnitř jiné třídy (odvozené třídy).

Následující ukázka generuje C2885.

```cpp
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
