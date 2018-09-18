---
title: Chyba kompilátoru C2668 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 03/28/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2668
dev_langs:
- C++
helpviewer_keywords:
- C2668
ms.assetid: 041e9627-1c76-420e-a653-cfc83f933bd3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c3b318c663bb036629086d0bca9a67641e3c4c4e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46093750"
---
# <a name="compiler-error-c2668"></a>Chyba kompilátoru C2668

'function': nejednoznačné volání přetížené funkce

Volání zadané funkce přetížení se nepodařilo přeložit. Můžete explicitně přetypovat jeden nebo více skutečných parametrů.

Tuto chybu můžete získat také pomocí šablony. Pokud ve stejné třídě, máte regulární členské funkce a bez vizuálního vzhledu členská funkce se stejným podpisem, musí být první je bez vizuálního vzhledu. Jedná se omezení aktuální implementace jazyka Visual C++.

Na částečné řazení šablon funkcí najdete v článku znalostní báze Knowledge Base Q240869 Další informace.

Pokud vytváříte projekt knihovny ATL, který obsahuje objekt modelu COM podporuje `ISupportErrorInfo`, najdete v článku znalostní báze Q243298.

## <a name="example"></a>Příklad

Následující ukázka generuje C2668:

```
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

Dalším způsobem, jak vyřešit tuto chybu je [using – deklarace](../../cpp/using-declaration.md):

```
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

Tato chyba může být také generovány jako důsledek kompilátoru prací, které bylo provedeno pro Visual Studio .NET 2003: nejednoznačný převod na přetypování konstant 0.

Převod na přetypování pomocí konstantní 0 je nejednoznačný, protože int vyžaduje převod jak dlouho a na typ void *. Chcete-li vyřešit tuto chybu, přetypování 0 pro přesného typu parametru funkce, který používá se pro tak, aby žádný převod muset provést (Tento kód bude platit ve Visual Studio .NET 2003 a Visual Studio .NET verzí jazyka Visual C++).

```
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

Této chybě může dojít, protože CRT má teď plovoucí desetinnou čárkou a double formy všechny matematické funkce.

```
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

Této chybě může dojít, protože pow (int, int) byla odstraněna z math.h v CRT.

```
// C2668e.cpp
#include <math.h>
int main() {
   pow(9,9);   // C2668
   pow((double)9,9);   // OK
}
```

## <a name="example"></a>Příklad

Tento kód v sadě Visual Studio 2015 úspěšné, ale v sadě Visual Studio 2017 a novější s C2668 se nezdaří. V sadě Visual Studio 2015 kompilátor nesprávně zpracovávají Inicializace kopírování seznamu v stejným způsobem jako regulární Inicializace kopírování; za to, převod pouze konstruktory pro řešení přetížení.

```
C++
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