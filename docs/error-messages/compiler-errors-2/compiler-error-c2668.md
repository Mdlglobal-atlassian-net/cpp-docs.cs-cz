---
title: Chyba kompilátoru C2668
ms.date: 03/28/2017
f1_keywords:
- C2668
helpviewer_keywords:
- C2668
ms.assetid: 041e9627-1c76-420e-a653-cfc83f933bd3
ms.openlocfilehash: f59cb33bed15847ed1a7a2dbe99ea030babf3337
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80177154"
---
# <a name="compiler-error-c2668"></a>Chyba kompilátoru C2668

' function ': nejednoznačné volání přetížené funkce

Zadané přetížené volání funkce nebylo možné přeložit. Je možné, že budete chtít explicitně přetypovat jeden nebo více skutečných parametrů.

Tuto chybu můžete získat také prostřednictvím použití šablony. Pokud ve stejné třídě máte regulární členskou funkci a členskou funkci šablon se stejnou signaturou, je nutné, aby se šablona nacházela jako první. Toto je omezení aktuální implementace vizuálu C++.

## <a name="example"></a>Příklad

Následující ukázka generuje C2668:

```cpp
// C2668.cpp
struct A {};
struct B : A {};
struct X {};
struct D : B, X {};

void func( X, X ){}
void func( A, B ){}
D d;
int main() {
   func( d, d );   // C2668 D has an A, B, and X
   func( (X)d, (X)d );   // OK, uses func( X, X )
}
```

## <a name="example"></a>Příklad

Další způsob, jak tuto chybu vyřešit, je [deklarace using](../../cpp/using-declaration.md):

```cpp
// C2668b.cpp
// compile with: /EHsc /c
// C2668 expected
#include <iostream>
class TypeA {
public:
   TypeA(int value) {}
};

class TypeB {
   TypeB(int intValue);
   TypeB(double dbValue);
};

class TestCase {
public:
   void AssertEqual(long expected, long actual, std::string
                    conditionExpression = "");
};

class AppTestCase : public TestCase {
public:
   // Uncomment the following line to resolve.
   // using TestCase::AssertEqual;
   void AssertEqual(const TypeA expected, const TypeA actual,
                    std::string conditionExpression = "");
   void AssertEqual(const TypeB expected, const TypeB actual,
                    std::string conditionExpression = "");
};

class MyTestCase : public AppTestCase {
   void TestSomething() {
      int actual = 0;
      AssertEqual(0, actual, "Value");
   }
};
```

## <a name="example"></a>Příklad

Tato chyba se může vygenerovat taky v důsledku práce s vyhovujícími kompilátory, které se provedly pro Visual Studio .NET 2003: dvojznačný převod na přetypování konstanty 0.

Převod na přetypování pomocí konstanty 0 je nejednoznačný, protože int vyžaduje převod jak na Long, tak na void *. Chcete-li tuto chybu vyřešit, přetypování 0 na přesný typ parametru funkce, který je používán pro tak, aby se nemusely provádět žádné převody (Tento kód bude platný v jazyce Visual Studio .NET 2003 a Visual Studio .NET verze vizuálu C++).

```cpp
// C2668c.cpp
#include "stdio.h"
void f(long) {
   printf_s("in f(long)\n");
}
void f(void*) {
   printf_s("in f(void*)\n");
}
int main() {
   f((int)0);   // C2668

   // OK
   f((long)0);
   f((void*)0);
}
```

## <a name="example"></a>Příklad

K této chybě může dojít, protože CRT teď má plovoucí a dvojitou formu všech matematických funkcí.

```cpp
// C2668d.cpp
#include <math.h>
int main() {
   int i = 0;
   float f;
   f = cos(i);   // C2668
   f = cos((float)i);   // OK
}
```

## <a name="example"></a>Příklad

K této chybě může dojít, protože v CRT došlo k odebrání POW (int, int) z Math. h.

```cpp
// C2668e.cpp
#include <math.h>
int main() {
   pow(9,9);   // C2668
   pow((double)9,9);   // OK
}
```

## <a name="example"></a>Příklad

Tento kód je úspěšný v aplikaci Visual Studio 2015, ale v nástroji Visual Studio 2017 a novějším s C2668em selže. V sadě Visual Studio 2015 kompilátor chybně zpracoval inicializaci kopírováním seznamu, stejně jako při normální inicializaci kopírování; považuje se za převádění pouze konstruktorů pro řešení přetížení.

```cpp
struct A {
    explicit A(int) {}
};

struct B {
    B(int) {}
};

void f(const A&) {}
void f(const B&) {}

int main()
{
    f({ 1 }); // error C2668: 'f': ambiguous call to overloaded function
}
```
