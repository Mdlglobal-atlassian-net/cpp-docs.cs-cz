---
title: C2668 Chyba kompilátoru | Microsoft Docs
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
ms.openlocfilehash: ea6cb5f53d3d4d0971398dbba10e24b579ce6c62
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2668"></a>C2668 chyby kompilátoru
'function': nejednoznačné volání přetížené funkce  
  
 Zadaná přetížené funkce volání nebylo možné přeložit. Můžete explicitně převést jednu nebo více parametrů skutečný.  
  
 Tuto chybu můžete získat také pomocí šablony. Pokud ve stejné třídě, máte regulární členské funkce a funkce šablonované člen se stejným podpisem, musí být první šablonované jeden. Jedná se o omezení aktuální implementace Visual C++.  
  
 Částečné řazení šablon funkcí v najdete v článku znalostní báze Knowledge Base Q240869 Další informace.  
  
 Pokud vytváříte projektu knihovny ATL obsahující objekt COM podporující `ISupportErrorInfo`, najdete v článku znalostní báze Knowledge Base Q243298.  
  
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
 Je také možné tuto chybu vyřešit s [pomocí deklarace](../../cpp/using-declaration.md):  
  
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
 Tato chyba může být také vygenerovaného jako výsledek kompilátoru shoda práci, kterou bylo provedeno pro Visual Studio .NET 2003: nejednoznačné konverzi na přetypování konstantní 0.  
  
 Převod na přetypování pomocí konstantní 0 je nejednoznačné, protože int vyžaduje převod i na dlouho a pro void *. Pokud chcete tuto chybu vyřešit, přetypování 0 přesný typ parametru funkce, které používá se pro tak, aby žádné převody muset provést (Tento kód bude v verze Visual C++ pro Visual Studio .NET 2003 a sady Visual Studio .NET).  
  
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
 Této chybě může dojít, protože teď má CRT float a double formy všechny matematické funkce.  
  
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
 Této chybě může dojít, protože z math.h v CRT odebral pow (int, int).  
  
```  
// C2668e.cpp  
#include <math.h>  
int main() {  
   pow(9,9);   // C2668  
   pow((double)9,9);   // OK  
}  
```

## <a name="example"></a>Příklad  
Tento kód v sadě Visual Studio 2015 se podaří, ale selže ve Visual Studio 2017 a později se C2668. V sadě Visual Studio 2015 kompilátor chybnou informací považovat kopírování. seznam inicializace stejným způsobem jako regulární kopie inicializace; považuje za pouze převod konstruktory pro rozlišení přetížení. 

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