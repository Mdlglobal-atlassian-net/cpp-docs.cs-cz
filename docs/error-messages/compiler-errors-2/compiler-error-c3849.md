---
title: Chyba kompilátoru C3849
ms.date: 11/04/2016
f1_keywords:
- C3849
helpviewer_keywords:
- C3849
ms.assetid: 5347140e-1a81-4841-98c0-b63d98264b64
ms.openlocfilehash: ec6725472d31b0b2ade0cd73da4440036239fde3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50598559"
---
# <a name="compiler-error-c3849"></a>Chyba kompilátoru C3849

volání Function-style na výrazu typu 'type' ztratí kvalifikátory const nebo volatile pro všechna čísla dostupná přetížení operátorů

Proměnná s zadaného typu const-volatile pouze lze volat členské funkce definované s kvalifikací const-volatile stejnou nebo větší.

Chcete-li vyřešit tuto chybu, zadejte odpovídající členskou funkci. Nelze provést převod pro deklarovaný jako const nebo volatile kvalifikovaný objektu, když že převod nezpůsobí ztrátu kvalifikace. Můžete získat kvalifikátory, ale můžete dovolit kvalifikátory převodu na.

Následující ukázky generovat C3849:

```
// C3849.cpp
void glbFunc3(int i, char c)
{
   i;
}
typedef void (* pFunc3)(int, char);

void glbFunc2(int i)
{
   i;
}

typedef void (* pFunc2)(int);

void glbFunc1()
{
}
typedef void (* pFunc1)();

struct S4
{
   operator ()(int i)
   {
      i;
   }

   operator pFunc1() const
   {
      return &glbFunc1;
   }

   operator pFunc2() volatile
   {
      return &glbFunc2;
   }

   operator pFunc3()
   {
      return &glbFunc3;
   }

   // operator pFunc1() const volatile
   // {
   //    return &glbFunc1;
   // }
};

int main()
{
   // Cannot call any of the 4 overloads of "operator ()(.....)" and
   // "operator pFunc()" because none is declared as "const volatile"
   const volatile S4 s4;  // can only call cv member functions of S4
   s4();   // C3849 to resolve, uncomment member function
}
```