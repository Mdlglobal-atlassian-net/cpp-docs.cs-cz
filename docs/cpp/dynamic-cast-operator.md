---
title: "dynamic_cast – operátor | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- dynamic_cast_cpp
dev_langs:
- C++
helpviewer_keywords:
- dynamic_cast keyword [C++]
ms.assetid: f380ada8-6a18-4547-93c9-63407f19856b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 29add795c7adeca67fc85c7cf3b1b90d17f804fd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="dynamiccast-operator"></a>dynamic_cast – operátor
Převede operand `expression` na objekt typu `type-id`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
dynamic_cast < type-id > ( expression )  
```  
  
## <a name="remarks"></a>Poznámky  
 `type-id` Musí být ukazatel nebo odkaz na typ dříve definované třídy nebo "ukazatel na void". Typ `expression` musí být ukazatel, pokud `type-id` ukazatel nebo hodnotu l `type-id` je odkaz.  
  
 V tématu [static_cast](../cpp/static-cast-operator.md) vysvětlení rozdílu mezi statickým a dynamickým přetypování převody a kdy je vhodné používat.  
  
 Existují dvě nejnovější změny v chování nástroje `dynamic_cast` ve spravovaném kódu:  
  
-   `dynamic_cast`na ukazatel na základní typ zabalené výčtu se nezdaří za běhu, vrácení 0, a ne převedený ukazatele.  
  
-   `dynamic_cast`už vyvolá výjimku při `type-id` je vnitřní ukazatel na typ hodnoty, s přetypování selhání za běhu.  Přetypování nyní vrátí hodnotu 0 ukazatel místo vyvolání.  
  
 Pokud `type-id` ukazatel jednoznačným přístupné přímý nebo nepřímý základní třídy z `expression`, ukazatel na jedinečný určitých podřízených objektů typu `type-id` je výsledek. Příklad:  
  
```  
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
  
 Tento typ převodu nazývá "povýšení", protože ukazatel až hierarchie tříd, přesune z odvozené třídy za účelem, který je odvozen od třídy. Povýšení je implicitní převod.  
  
 Pokud `type-id` je void * spuštění ověření k určení skutečný typ `expression`. Výsledkem je ukazatel na kompletní objekt, na kterou odkazuje `expression`. Příklad:  
  
```  
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
  
 Pokud `type-id` není void * spuštění ověření zobrazíte, pokud objekt na kterou odkazuje `expression` lze převést na typ, na kterou odkazuje `type-id`.  
  
 Pokud typ `expression` je základní třídou typu `type-id`, a zjistěte, zda se provede kontrola běhu `expression` ve skutečnosti odkazuje na objekt dokončení typu `type-id`. Pokud je to pravda, výsledkem je ukazatel na kompletní objekt typu `type-id`. Příklad:  
  
```  
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
  
 Tento typ převodu se nazývá z něj odvozenou "přetypování dolů" protože přesune ukazatel dolů hierarchie tříd, z dané třídy na třídu.  
  
 V případě vícenásobná dědičnost se vydávají možnosti nejednoznačnosti. Vezměte v úvahu hierarchie tříd vidět na následujícím obrázku.  
  
 Pro typy CLR `dynamic_cast` výsledkem no-op, pokud převod mohou být provedeny implicitně nebo MSIL `isinst` instrukce, která provede kontrolu dynamické a vrátí `nullptr` Pokud převod selže.  
  
 Následující ukázkové používá `dynamic_cast` k určení, pokud třída je instance určitého typu:  
  
```  
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
  
 ![Hierarchie, který ukazuje vícenásobná dědičnost třídy](../cpp/media/vc39011.gif "vc39011")  
Hierarchie tříd zobrazující vícenásobná dědičnost  
  
 Ukazatel na objekt typu `D` můžete bezpečně přetypovat na `B` nebo `C`. Ale pokud `D` vložena tak, aby odkazoval `A` objektu, která instance `A` by? To by způsobilo chybu nejednoznačný přetypování. Pokud chcete tento problém vyřešit, můžete provádět dva jednoznačným přetypování. Příklad:  
  
```  
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
  
 Pokud používáte základní virtuální třídy další nejednoznačnosti zavedení. Vezměte v úvahu hierarchie tříd vidět na následujícím obrázku.  
  
 ![Třídy hierarchie, která ukazuje základní virtuální třídy](../cpp/media/vc39012.gif "vc39012")  
Hierarchie tříd zobrazující základní virtuální třídy  
  
 V této hierarchii `A` je virtuální základní třídy. Zadané instance třídy `E` a odkazy `A` určitých podřízených objektů, `dynamic_cast` na ukazatel na `B` se nezdaří z důvodu nejednoznačnosti. Nejdřív musíte vysílat zpět na kompletní `E` objektu a pak fungují zálohování hierarchie, jednoznačným způsobem spojit správný `B` objektu.  
  
 Vezměte v úvahu hierarchie tříd vidět na následujícím obrázku.  
  
 ![Třídy hierarchie, která zobrazuje duplicitní základní třídy](../cpp/media/vc39013.gif "vc39013")  
Hierarchie tříd zobrazující duplicitní základní třídy  
  
 Zadaný objekt typu `E` a odkazy `D` určitých podřízených objektů, přejděte z `D` určitých podřízených objektů k nejvíce vlevo `A` určitých podřízených objektů, můžete provést tři převody. Můžete provádět `dynamic_cast` převod `D` ukazatel na `E` ukazatele, pak převodu z (buď `dynamic_cast` nebo implicitní převod) z `E` k `B`a nakonec implicitní převod z `B` k `A`. Příklad:  
  
```  
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
  
 `dynamic_cast` Operátor lze také provést "křížové přetypování." Pomocí stejné hierarchie tříd, je možné přetypovat ukazatel, například z `B` určitých podřízených objektů k `D` určitých podřízených objektů, dokud kompletní objekt je typu `E`.  
  
 Vzhledem k tomu křížové přetypování, je ve skutečnosti možné provést převod z ukazatel na `D` na ukazatel na nejvíce vlevo `A` určitých podřízených objektů v právě dva kroky. Můžete provádět na křížek přetypování z `D` k `B`, pak implicitní převod z `B` k `A`. Příklad:  
  
```  
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
  
 Hodnota ukazatele null je převést na hodnotu ukazatele null typu cílové podle `dynamic_cast`.  
  
 Při použití `dynamic_cast < type-id > ( expression )`, pokud `expression` nelze bezpečně převést na typ `type-id`, kontrola běhu způsobí selhání přetypování. Příklad:  
  
```  
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
  
 Selhání přetypování na typ ukazatele hodnotu ukazatele null. Selhání přetypování tak, aby odkazovaly vrátí typu [bad_cast – výjimka](../cpp/bad-cast-exception.md).   Pokud `expression` přejděte na příkaz nebo odkazovat na platný objekt, `__non_rtti_object` je vyvolána výjimka.  
  
 V tématu [typeid](../cpp/typeid-operator.md) vysvětlení `__non_rtti_object` výjimka.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří ukazatele základní třídy (struktura A), k objektu (struktura C).  To plus skutečnost, že jsou virtuální funkce, umožňuje polymorfismus modulu runtime.  
  
 Ukázka volá také bez virtuální funkce v hierarchii.  
  
```  
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
  
## <a name="see-also"></a>Viz také  
 [Operátory přetypování](../cpp/casting-operators.md)   
 [Klíčová slova](../cpp/keywords-cpp.md)