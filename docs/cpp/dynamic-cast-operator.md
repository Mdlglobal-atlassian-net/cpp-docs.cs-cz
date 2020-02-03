---
title: dynamic_cast – operátor
description: Přehled operátoru C++ jazyka dynamic_cast.
ms.date: 02/03/2020
f1_keywords:
- dynamic_cast_cpp
helpviewer_keywords:
- dynamic_cast keyword [C++]
ms.assetid: f380ada8-6a18-4547-93c9-63407f19856b
ms.openlocfilehash: 0073aaa886bba33a0ec6c07fb89d6eee032765c8
ms.sourcegitcommit: ba4180a2d79d7e391f2f705797505d4aedbc2a5e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/03/2020
ms.locfileid: "76972223"
---
# <a name="dynamic_cast-operator"></a>dynamic_cast – operátor

Převede operand `expression` na objekt typu `type-id`.

## <a name="syntax"></a>Syntaxe

```
dynamic_cast < type-id > ( expression )
```

## <a name="remarks"></a>Poznámky

`type-id` musí být ukazatel nebo odkaz na dříve definovaný typ třídy nebo "ukazatel na void". Typ `expression` musí být ukazatel, pokud `type-id` je ukazatel nebo l-hodnota, pokud je `type-id` odkazem.

V tématu [static_cast](../cpp/static-cast-operator.md) naleznete vysvětlení rozdílu mezi převody statického a dynamického přetypování a v případě, kdy je vhodné je použít.

Existují dva zásadní změny v chování **dynamic_cast** ve spravovaném kódu:

- **dynamic_cast** k ukazateli na nadřízený typ zabaleného výčtu selže za běhu a vrátí hodnotu 0 namísto převedeného ukazatele.

- **dynamic_cast** přestane vyvolat výjimku, pokud `type-id` je vnitřním ukazatelem na typ hodnoty, přičemž přetypování selže za běhu.  Přetypování nyní vrátí hodnotu ukazatele 0 namísto vyvolání.

Pokud je `type-id` ukazatel na nejednoznačnou dostupnou přímou nebo nepřímou základní třídu `expression`, je výsledkem ukazatel na jedinečný podobjekt typu `type-id`. Příklad:

```cpp
// dynamic_cast_1.cpp
// compile with: /c
class B { };
class C : public B { };
class D : public C { };

void f(D* pd) {
   C* pc = dynamic_cast<C*>(pd);   // ok: C is a direct base class
                                   // pc points to C subobject of pd
   B* pb = dynamic_cast<B*>(pd);   // ok: B is an indirect base class
                                   // pb points to B subobject of pd
}
```

Tento typ převodu se nazývá "přetypování", protože přesouvá ukazatel nahoru na třídu, od odvozené třídy až po třídu, ze které je odvozena. Přetypování je implicitní převod.

Je-li `type-id` je typu void *, je provedena kontroly za běhu, aby bylo možné určit skutečný typ `expression`. Výsledkem je ukazatel na úplný objekt, na který ukazuje `expression`. Příklad:

```cpp
// dynamic_cast_2.cpp
// compile with: /c /GR
class A {virtual void f();};
class B {virtual void f();};

void f() {
   A* pa = new A;
   B* pb = new B;
   void* pv = dynamic_cast<void*>(pa);
   // pv now points to an object of type A

   pv = dynamic_cast<void*>(pb);
   // pv now points to an object of type B
}
```

Pokud `type-id` není typu void *, je provedena kontrolní rutina, aby bylo možné zjistit, zda objekt, na který je odkazováno pomocí `expression`, lze převést na typ, na který ukazuje `type-id`.

Pokud je typ `expression` základní třídou typu `type-id`, je provedena kontrolní rutina pro zjištění, zda `expression` skutečně odkazuje na úplný objekt typu `type-id`. Pokud je to pravda, výsledek je ukazatel na úplný objekt typu `type-id`. Příklad:

```cpp
// dynamic_cast_3.cpp
// compile with: /c /GR
class B {virtual void f();};
class D : public B {virtual void f();};

void f() {
   B* pb = new D;   // unclear but ok
   B* pb2 = new B;

   D* pd = dynamic_cast<D*>(pb);   // ok: pb actually points to a D
   D* pd2 = dynamic_cast<D*>(pb2);   // pb2 points to a B not a D
}
```

Tento typ převodu se nazývá "downcast", protože přesouvá ukazatel dolů na hierarchii tříd z dané třídy na třídu odvozenou od ní.

V případě vícenásobné dědičnosti jsou zavedeny možnosti nejednoznačnosti. Vezměte v úvahu hierarchii tříd znázorněnou na následujícím obrázku.

U typů CLR **dynamic_cast** výsledkem buď no-op, pokud je možné převod provést implicitně, nebo MSIL `isinst` instrukci, která provede dynamickou kontrolu a vrátí **nullptr** , pokud převod selhává.

Následující příklad používá **dynamic_cast** k určení, zda je třída instancí konkrétního typu:

```cpp
// dynamic_cast_clr.cpp
// compile with: /clr
using namespace System;

void PrintObjectType( Object^o ) {
   if( dynamic_cast<String^>(o) )
      Console::WriteLine("Object is a String");
   else if( dynamic_cast<int^>(o) )
      Console::WriteLine("Object is an int");
}

int main() {
   Object^o1 = "hello";
   Object^o2 = 10;

   PrintObjectType(o1);
   PrintObjectType(o2);
}
```

![Hierarchie tříd, která zobrazuje vícenásobnou dědičnost](../cpp/media/vc39011.gif "Hierarchie tříd, která zobrazuje vícenásobnou dědičnost") <br/>
Hierarchie tříd, která zobrazuje vícenásobnou dědičnost

Ukazatel na objekt typu `D` lze bezpečně přetypovat na `B` nebo `C`. Pokud je však `D` přetypování tak, aby odkazovalo na objekt `A`, která instance `A` by měla výsledek? Výsledkem je nejednoznačná Chyba při přetypování. Chcete-li se tomuto problému vyhnout, můžete provést dvě nejednoznačná přetypování. Příklad:

```cpp
// dynamic_cast_4.cpp
// compile with: /c /GR
class A {virtual void f();};
class B : public A {virtual void f();};
class C : public A {virtual void f();};
class D : public B, public C {virtual void f();};

void f() {
   D* pd = new D;
   A* pa = dynamic_cast<A*>(pd);   // C4540, ambiguous cast fails at runtime
   B* pb = dynamic_cast<B*>(pd);   // first cast to B
   A* pa2 = dynamic_cast<A*>(pb);   // ok: unambiguous
}
```

Pokud používáte virtuální základní třídy, můžete zavádět další nejednoznačnosti. Vezměte v úvahu hierarchii tříd znázorněnou na následujícím obrázku.

![Hierarchie tříd, která zobrazuje virtuální základní třídy](../cpp/media/vc39012.gif "Hierarchie tříd, která zobrazuje virtuální základní třídy") <br/>
Hierarchie tříd, která zobrazuje virtuální základní třídy

V této hierarchii je `A` virtuální základní třídou. Vzhledem k instanci třídy `E` a ukazatele na podobjektu `A`, **dynamic_cast** na ukazatel na `B` se nezdaří z důvodu nejednoznačnosti. Je nutné nejprve přetypování zpátky na dokončený objekt `E` a pak můžete pracovat způsobem, který je v hierarchii jednoznačným způsobem, aby se dosáhlo správného objektu `B`.

Vezměte v úvahu hierarchii tříd znázorněnou na následujícím obrázku.

![Hierarchie tříd, která zobrazuje duplicitní základní třídy](../cpp/media/vc39013.gif "Hierarchie tříd, která zobrazuje duplicitní základní třídy") <br/>
Hierarchie tříd, která zobrazuje duplicitní základní třídy

Vzhledem k objektu typu `E` a ukazatel na podobjektu `D`, aby bylo možné přejít z podobjektu `D` na levou stranu `A`, lze vytvořit tři převody. Můžete provést **dynamic_cast** převod z ukazatele `D` na ukazatel `E`, pak převod (buď **dynamic_cast** nebo implicitní převod) z `E` na `B`, a nakonec implicitní převod z `B` na `A`. Příklad:

```cpp
// dynamic_cast_5.cpp
// compile with: /c /GR
class A {virtual void f();};
class B : public A {virtual void f();};
class C : public A { };
class D {virtual void f();};
class E : public B, public C, public D {virtual void f();};

void f(D* pd) {
   E* pe = dynamic_cast<E*>(pd);
   B* pb = pe;   // upcast, implicit conversion
   A* pa = pb;   // upcast, implicit conversion
}
```

Operátor **dynamic_cast** lze také použít k provedení "vzájemného přetypování". Pomocí stejné hierarchie třídy je možné přetypovat ukazatel, například z podobjektu `B` na `D` podobjekt, pokud je kompletní objekt typu `E`.

S ohledem na křížové přetypování je ve skutečnosti možné provést převod z ukazatele na `D` ukazatel na levou krajní `A` podobjekt v pouze dvou krocích. Můžete provést přetypování z `D` na `B`a pak implicitní převod z `B` na `A`. Příklad:

```cpp
// dynamic_cast_6.cpp
// compile with: /c /GR
class A {virtual void f();};
class B : public A {virtual void f();};
class C : public A { };
class D {virtual void f();};
class E : public B, public C, public D {virtual void f();};

void f(D* pd) {
   B* pb = dynamic_cast<B*>(pd);   // cross cast
   A* pa = pb;   // upcast, implicit conversion
}
```

Hodnota nulového ukazatele je převedena na hodnotu nulového ukazatele cílového typu **dynamic_cast**.

Pokud použijete `dynamic_cast < type-id > ( expression )`, pokud `expression` nelze bezpečně převést na typ `type-id`, bude při spuštění přetypování příčinou selhání. Příklad:

```cpp
// dynamic_cast_7.cpp
// compile with: /c /GR
class A {virtual void f();};
class B {virtual void f();};

void f() {
   A* pa = new A;
   B* pb = dynamic_cast<B*>(pa);   // fails at runtime, not safe;
   // B not derived from A
}
```

Hodnota neúspěšného přetypování na typ ukazatele je ukazatel s hodnotou null. Neúspěšné přetypování na odkazový typ vyvolá [výjimku bad_cast](../cpp/bad-cast-exception.md).   Pokud `expression` nesměruje na platný objekt nebo na něj odkazuje, je vyvolána výjimka `__non_rtti_object`.

Vysvětlení výjimky `__non_rtti_object` naleznete v tématu [typeid](../cpp/typeid-operator.md) .

## <a name="example"></a>Příklad

Následující příklad vytvoří ukazatel základní třídy (struktura A) na objekt (struct C).  A navíc k tomu, že existují virtuální funkce, umožňují polymorfismus za běhu.

Ukázka také volá nevirtuální funkci v hierarchii.

```cpp
// dynamic_cast_8.cpp
// compile with: /GR /EHsc
#include <stdio.h>
#include <iostream>

struct A {
    virtual void test() {
        printf_s("in A\n");
   }
};

struct B : A {
    virtual void test() {
        printf_s("in B\n");
    }

    void test2() {
        printf_s("test2 in B\n");
    }
};

struct C : B {
    virtual void test() {
        printf_s("in C\n");
    }

    void test2() {
        printf_s("test2 in C\n");
    }
};

void Globaltest(A& a) {
    try {
        C &c = dynamic_cast<C&>(a);
        printf_s("in GlobalTest\n");
    }
    catch(std::bad_cast) {
        printf_s("Can't cast to C\n");
    }
}

int main() {
    A *pa = new C;
    A *pa2 = new B;

    pa->test();

    B * pb = dynamic_cast<B *>(pa);
    if (pb)
        pb->test2();

    C * pc = dynamic_cast<C *>(pa2);
    if (pc)
        pc->test2();

    C ConStack;
    Globaltest(ConStack);

   // will fail because B knows nothing about C
    B BonStack;
    Globaltest(BonStack);
}
```

```Output
in C
test2 in B
in GlobalTest
Can't cast to C
```

## <a name="see-also"></a>Viz také:

[Operátory přetypování](../cpp/casting-operators.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)