---
title: dynamic_cast – operátor
ms.date: 11/19/2018
f1_keywords:
- dynamic_cast_cpp
helpviewer_keywords:
- dynamic_cast keyword [C++]
ms.assetid: f380ada8-6a18-4547-93c9-63407f19856b
ms.openlocfilehash: 3b359885eb72f9272fb1efe14afe9a6cbe6ddb30
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62399038"
---
# <a name="dynamiccast-operator"></a>dynamic_cast – operátor

Převede operand `expression` na objekt typu `type-id`.

## <a name="syntax"></a>Syntaxe

```
dynamic_cast < type-id > ( expression )
```

## <a name="remarks"></a>Poznámky

`type-id` Musí být ukazatel nebo odkaz na typ dříve definicí třídy nebo "ukazatel na typ void". Typ `expression` musí být ukazatel, pokud `type-id` je ukazatel nebo l hodnotou, pokud `type-id` je odkaz.

Zobrazit [static_cast](../cpp/static-cast-operator.md) vysvětlení rozdílu mezi statickými a dynamickými převody a kdy je vhodné je použít.

Existují dvě rozbíjející změny v chování nástroje **dynamic_cast** ve spravovaném kódu:

- **přetypování dynamic_cast** na ukazatel na základní typ zabalené výčtu za běhu selže, vrátí 0, a ne ukazatel na převedený.

- **přetypování dynamic_cast** už nevyvolá výjimku při `type-id` je vnitřní ukazatel na typ hodnoty, s přetypování selhání za běhu.  Přetypování nyní vrátí hodnotu 0 ukazatele namísto vyvolání.

Pokud `type-id` je ukazatel na jednoznačný přístupné přímou nebo nepřímou základní třídou `expression`, ukazatel na jedinečné podřízený typ `type-id` je výsledek. Příklad:

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

Tento typ převodu se nazývá "povýšení", protože ji přesune ukazatel myši nahoru hierarchie tříd, z odvozené třídy, která je odvozena z třídy. Povýšení je implicitní převod.

Pokud `type-id` je typ void *, určit skutečný typ se provede kontrola za běhu `expression`. Výsledkem je ukazatelem na kompletní objekt, na které odkazuje `expression`. Příklad:

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

Pokud `type-id` není void *, kontrolu za běhu se provede, pokud objekt, na který podle `expression` lze převést na typ, na které odkazuje `type-id`.

Pokud typ `expression` je základní třídu typu `type-id`, a zjistěte, jestli se provede kontrola za běhu `expression` skutečně ukazuje na kompletní objekt typu `type-id`. Pokud je to pravda, výsledkem je ukazatel na kompletní objekt typu `type-id`. Příklad:

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

Tento typ převodu se nazývá z něj odvozenou "downcast", protože přesunete ukazatel o hierarchii tříd, z dané třídy do třídy.

V případě vícenásobné dědičnosti se vydávají možnosti nejednoznačnost. Vezměte v úvahu hierarchii tříd znázorněnou na následujícím obrázku.

Pro typy CLR **dynamic_cast** výsledkem no-op. Pokud převod lze provést implicitně nebo MSIL `isinst` instrukce, která provede kontrolu dynamické a vrátí **nullptr** Pokud převod nezdaří.

Následující ukázkový používá **dynamic_cast** k určení, zda třída je instance určitého typu:

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

![Hierarchie, která zobrazuje vícenásobná dědičnost třídy](../cpp/media/vc39011.gif "hierarchie, která zobrazuje vícenásobná dědičnost třídy") <br/>
Hierarchie tříd, který zobrazuje vícenásobná dědičnost

Ukazatel na objekt typu `D` lze jej bezpečně přetypovat tak `B` nebo `C`. Ale pokud `D` přetypovat tak, aby odkazovala na `A` objektu, která instance `A` , by stálo? To způsobí chybu nejednoznačný přetypování. Chcete-li tento problém vyřešit, můžete provádět dvěma jednoznačný přetypování. Příklad:

```cpp
// dynamic_cast_4.cpp
// compile with: /c /GR
class A {virtual void f();};
class B {virtual void f();};
class D : public B {virtual void f();};

void f() {
   D* pd = new D;
   B* pb = dynamic_cast<B*>(pd);   // first cast to B
   A* pa2 = dynamic_cast<A*>(pb);   // ok: unambiguous
}
```

Použijete-li virtuální základní třídy je možné vytvářet další nejednoznačnosti. Vezměte v úvahu hierarchii tříd znázorněnou na následujícím obrázku.

![Třída hierarchie, která ukazuje virtuální základní třídy](../cpp/media/vc39012.gif "třídy hierarchie, která ukazuje virtuální třídy base") <br/>
Hierarchie tříd, který ukazuje virtuální třídy base

V této hierarchii `A` je virtuální základní třídy. Dána instance třídy `E` a ukazatel `A` podobjekt, **dynamic_cast** na ukazatel na `B` se nezdaří z důvodu nejednoznačnosti. Nejprve musíte přetypovat zpět na úplnou `E` a pak nahlíželi zpět nahoru hierarchii jednoznačně, k dosažení správné `B` objektu.

Vezměte v úvahu hierarchii tříd znázorněnou na následujícím obrázku.

![Hierarchie, která zobrazuje duplicitní základní třídy třídy](../cpp/media/vc39013.gif "třídy hierarchie, která ukazuje duplicitní základní třídy") <br/>
Hierarchie tříd, který zobrazuje duplicitní základní třídy

Zadaný objekt typu `E` a ukazatel `D` podobjekt přejít z `D` podobjekt k nejvíce vlevo `A` podobjekt, můžete provést tři převody. Můžete provádět **dynamic_cast** převod `D` ukazatel na `E` ukazatele a pak převod (buď **dynamic_cast** nebo implicitní převod) z `E`k `B`a nakonec implicitní převod z `B` k `A`. Příklad:

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

**Dynamic_cast** operátor je také možné provádět "mezi přetypování". Pomocí stejné hierarchie třídy, je možné přetypovat ukazatel, například z `B` podobjekt k `D` podobjekt, jako je kompletní objekt typu `E`.

Vzhledem k tomu různé přetypování, je skutečně možné provést převod z ukazatele na `D` na ukazatel na nejvíce vlevo `A` podobjekt v pouhých dvou kroků. Můžete provádět různé přetypování z `D` k `B`, pak implicitní převod z `B` k `A`. Příklad:

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

Hodnota ukazatele s hodnotou null je převedena na hodnotu ukazatele s hodnotou null typu cílového podle **dynamic_cast**.

Při použití `dynamic_cast < type-id > ( expression )`, pokud `expression` nelze bezpečně převést na typ `type-id`, kontrola běhu způsobí, že přetypování selhání. Příklad:

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

Hodnota neúspěšného přetypování na typ ukazatele je ukazatel s hodnotou null. Neúspěšného přetypování na odkaz typu vyvolá [bad_cast – výjimka](../cpp/bad-cast-exception.md).   Pokud `expression` přejděte nebo odkazovat na platný objekt `__non_rtti_object` je vyvolána výjimka.

Zobrazit [typeid](../cpp/typeid-operator.md) vysvětlení `__non_rtti_object` výjimky.

## <a name="example"></a>Příklad

Následující příklad vytvoří ukazatel základní třídy (struktura A) na objekt (struktura jazyka C).  To, a navíc skutečnost, že jsou virtuální funkce, umožňuje modul runtime polymorfismu.

Ukázka volá také bez virtuální funkce v hierarchii.

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