---
title: 'Postupy: Používání operátoru safe_cast v jazyce C++/CLI'
ms.date: 11/04/2016
helpviewer_keywords:
- safe_cast keyword [C++], upcasting
ms.assetid: 0fbc87d8-ecdf-4cd5-81f4-0d8cc18e2aff
ms.openlocfilehash: 30aee0407e41533d34a860f3cedceb0be5b7b881
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50656999"
---
# <a name="how-to-use-safecast-in-ccli"></a>Postupy: Používání operátoru safe_cast v jazyce C++/CLI

Tento článek popisuje, jak pomocí operátoru safe_cast v jazyce C + +/ CLI aplikací. Informace o operátoru safe_cast v jazyce C + +/ CX, viz [safe_cast](../windows/safe-cast-cpp-component-extensions.md).

## <a name="upcasting"></a>Upcasting

Povýšení je přetypování z odvozeného typu do jedné z jejích základních tříd. Toto přetypování je bezpečné a nevyžaduje zápisu explicitní přetypování. Následující příklad ukazuje, jak provést povýšení, `safe_cast` a bez něj.

```cpp
// safe_upcast.cpp
// compile with: /clr
using namespace System;
interface class A {
   void Test();
};

ref struct B : public A {
   virtual void Test() {
      Console::WriteLine("in B::Test");
   }

   void Test2() {
      Console::WriteLine("in B::Test2");
   }
};

ref struct C : public B {
   virtual void Test() override {
      Console::WriteLine("in C::Test");
   };
};

int main() {
   C ^ c = gcnew C;

   // implicit upcast
   B ^ b = c;
   b->Test();
   b->Test2();

   // upcast with safe_cast
   b = nullptr;
   b = safe_cast<B^>(c);
   b->Test();
   b->Test2();
}
```

```Output
in C::Test
in B::Test2
in C::Test
in B::Test2
```

## <a name="downcasting"></a>Přetypování na nižší

Přetypování dolů je přetypování ze základní třídy na třídu, která je odvozena ze základní třídy.  Přetypování dolů je bezpečné, pouze v případě, že objekt, který je určena v době běhu ve skutečnosti řeší objektu odvozené třídy.  Na rozdíl od `static_cast`, `safe_cast` provede kontrolu dynamické a vyvolá <xref:System.InvalidCastException> Pokud převod selže.

```cpp
// safe_downcast.cpp
// compile with: /clr
using namespace System;

interface class A { void Test(); };

ref struct B : public A {
   virtual void Test() {
      Console::WriteLine("in B::Test()");
   }

   void Test2() {
      Console::WriteLine("in B::Test2()");
   }
};

ref struct C : public B {
   virtual void Test() override {
      Console::WriteLine("in C::Test()");
   }
};

interface class I {};

value struct V : public I {};

int main() {
   A^ a = gcnew C();
   a->Test();
   B^ b = safe_cast<B^>(a);
   b->Test();
   b->Test2();

   V v;
   I^ i = v;   // i boxes V
   V^ refv = safe_cast<V^>(i);

   Object^ o = gcnew B;
   A^ a2= safe_cast<A^>(o);
}
```

```Output
in C::Test()
in C::Test()
in B::Test2()
```

## <a name="safecast-with-user-defined-conversions"></a>safe_cast s uživatelem definované převody

Další příklad ukazuje, jak můžete `safe_cast` k vyvolání uživatelem definovaných převodů.

```cpp
// safe_cast_udc.cpp
// compile with: /clr
using namespace System;
value struct V;

ref struct R {
   int x;
   R() {
      x = 1;
   }

   R(int argx) {
      x = argx;
   }

   static operator R::V^(R^ r);
};

value struct V {
   int x;
   static operator R^(V& v) {
      Console::WriteLine("in operator R^(V& v)");
      R^ r = gcnew R();
      r->x = v.x;
      return r;
   }

   V(int argx) {
      x = argx;
   }
};

   R::operator V^(R^ r) {
      Console::WriteLine("in operator V^(R^ r)");
      return gcnew V(r->x);
   }

int main() {
   bool fReturnVal = false;
   V v(2);
   R^ r = safe_cast<R^>(v);   // should invoke UDC
   V^ v2 = safe_cast<V^>(r);   // should invoke UDC
}
```

```Output
in operator R^(V& v
in operator V^(R^ r)
```

## <a name="safecast-and-boxing-operations"></a>operace safe_cast a zabalení

### <a name="boxing"></a>Zabalení

Zabalení je definován jako vložený kompilátoru, uživatelem definovaný převod.  Proto můžete použít `safe_cast` do pole hodnota haldu CLR.

Následující příklad ukazuje zabalení se hodnota jednoduchého a uživatelem definované typy.  A `safe_cast` proměnné typu hodnoty, který je nativní zásobníku, takže je možné přiřadit k proměnné na haldě uvolňování pole.

```cpp
// safe_cast_boxing.cpp
// compile with: /clr
using namespace System;

interface struct I {};

value struct V : public I {
   int m_x;

   V(int i) : m_x(i) {}
};

int main() {
   // box a value type
   V v(100);
   I^ i = safe_cast<I^>(v);

   int x = 100;
   V^ refv = safe_cast<V^>(v);
   int^ refi = safe_cast<int^>(x);
}
```

Další příklad ukazuje, že zabalení má přednost před uživatelem definovaný převod v `safe_cast` operace.

```cpp
// safe_cast_boxing_2.cpp
// compile with: /clr
static bool fRetval = true;

interface struct I {};
value struct V : public I {
   int x;

   V(int argx) {
      x = argx;
   }

   static operator I^(V v) {
      fRetval = false;
      I^ pi = v;
      return pi;
   }
};

ref struct R {
   R() {}
   R(V^ pv) {}
};

int main() {
   V v(10);
   I^ pv = safe_cast<I^>(v);   // boxing will occur, not UDC "operator I^"
}
```

### <a name="unboxing"></a>Rozbalení

Rozbalení je definován jako vložený kompilátoru, uživatelem definovaný převod.  Proto můžete použít `safe_cast` k rozbalení hodnotu na haldě modulu CLR.

Rozbalení je uživatelem definovaný převod, ale na rozdíl od zabalení, rozbalení musí být explicitní – to znamená, ho musíte provést `static_cast`, C-style přetypování, nebo `safe_cast`; rozbalení nemůže být proveden implicitně.

```cpp
// safe_cast_unboxing.cpp
// compile with: /clr
int main() {
   System::Object ^ o = 42;
   int x = safe_cast<int>(o);
}
```

Následující ukázka ukazuje rozbalení s typy hodnot a primitivní typy.

```cpp
// safe_cast_unboxing_2.cpp
// compile with: /clr
using namespace System;

interface struct I {};

value struct VI : public I {};

void test1() {
   Object^ o = 5;
   int x = safe_cast<Int32>(o);
}

value struct V {
   int x;
   String^ s;
};

void test2() {
   V localv;
   Object^ o = localv;
   V unboxv = safe_cast<V>(o);
}

void test3() {
   V localv;
   V^ o2 = localv;
   V unboxv2 = safe_cast<V>(o2);
}

void test4() {
   I^ refi = VI();
   VI vi  = safe_cast<VI>(refi);
}

int main() {
   test1();
   test2();
   test3();
   test4();
}
```

## <a name="safecast-and-generic-types"></a>safe_cast a obecných typů

Další příklad ukazuje, jak můžete `safe_cast` provést přetypování dolů pomocí obecného typu.

```cpp
// safe_cast_generic_types.cpp
// compile with: /clr
interface struct I {};

generic<class T> where T:I
ref struct Base {
   T t;
   void test1() {}
};

generic<class T> where T:I
ref struct Derived:public Base <T> {};

ref struct R:public I {};

typedef Base<R^> GBase_R;
typedef Derived<R^> GDerived_R;

int main() {
   GBase_R^ br = gcnew GDerived_R();
   GDerived_R^ dr = safe_cast<GDerived_R^>(br);
}
```

## <a name="see-also"></a>Viz také

[safe_cast](../windows/safe-cast-cpp-component-extensions.md)