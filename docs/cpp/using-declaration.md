---
title: using – deklarace
ms.date: 11/04/2016
helpviewer_keywords:
- using declaration
- declaring namespaces, unqualified names in namespaces
- declarations [C++], using-declaration
- namespaces [C++], unqualified names in
- using keyword [C++]
- declarations [C++], namespaces
ms.assetid: 4184e2b1-3adc-408e-b5f3-0b3f8b554723
ms.openlocfilehash: 46d8b1e13b55988efd40643482ffd6123034ccb5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50559840"
---
# <a name="using-declaration"></a>using – deklarace

Názvu pomocí deklarace zavádí do deklarativní oblast, ve které using – deklarace se zobrazí.

## <a name="syntax"></a>Syntaxe

```
using [typename] nested-name-specifier unqualified-id ;
using declarator-list ;
```

### <a name="parameters"></a>Parametry

*vnořené specifikátorem názvu* posloupnost obor názvů, třídy, nebo názvy výčtů a operátory rozlišení oboru (::) byla ukončena operátorem rozlišení oboru. Operátor rozlišení oboru jednoho slouží k zavedení názvu v globálním oboru názvů. Klíčové slovo **typename** je volitelná a můžou sloužit k řešení názvy závislých prvků při zavedení do šablony třídy ze základní třídy.

*nekvalifikované id* nekvalifikované id výraz, který může být identifikátor, název přetíženého operátoru, uživatelem definované literální operátor nebo převod názvu funkce, název destruktor třídy nebo seznamu název a argument šablony.

*seznam deklarátorů* čárkou oddělený seznam [**typename**] *vnořené specifikátorem názvu* *nekvalifikované id* deklarátory, a volitelně podle tlačítko se třemi tečkami.

## <a name="remarks"></a>Poznámky

A pomocí deklarace zavádí neúplný název jako synonymum pro entitu někde jinde deklarovaný. To umožňuje název jedné z konkrétní obor názvů bez explicitní kvalifikace v deklaraci oblasti, ve kterém se zobrazí. To je v kontrastu s [direktiva using](../cpp/namespaces-cpp.md#using_directives), což umožňuje *všechny* názvů z oboru názvů bez kvalifikace lze používat. **Pomocí** – klíčové slovo se také používá pro [zadejte aliasy](../cpp/aliases-and-typedefs-cpp.md).

## <a name="example"></a>Příklad

A pomocí prohlášení lze použít v definici třídy.

```cpp
// using_declaration1.cpp
#include <stdio.h>
class B {
public:
   void f(char) {
      printf_s("In B::f()\n");
   }

   void g(char) {
      printf_s("In B::g()\n");
   }
};

class D : B {
public:
   using B::f;    // B::f(char) is now visible as D::f(char)
   using B::g;    // B::g(char) is now visible as D::g(char)
   void f(int) {
      printf_s("In D::f()\n");
      f('c');     // Invokes B::f(char) instead of recursing
   }

   void g(int) {
      printf_s("In D::g()\n");
      g('c');     // Invokes B::g(char) instead of recursing
   }
};

int main() {
   D myD;
   myD.f(1);
   myD.g('a');
}
```

```Output
In D::f()
In B::f()
In B::g()
```

## <a name="example"></a>Příklad

Pokud se použije k deklarování člena a s použitím deklarace musí odkazovat na člena základní třídy.

```cpp
// using_declaration2.cpp
#include <stdio.h>

class B {
public:
   void f(char) {
      printf_s("In B::f()\n");
   }

   void g(char) {
      printf_s("In B::g()\n");
   }
};

class C {
public:
   int g();
};

class D2 : public B {
public:
   using B::f;   // ok: B is a base of D2
   // using C::g;   // error: C isn't a base of D2
};

int main() {
   D2 MyD2;
   MyD2.f('a');
}
```

```Output
In B::f()
```

## <a name="example"></a>Příklad

Členy deklarované pomocí using deklarace můžete odkazovat pomocí explicitní kvalifikace. `::` Předponu odkazuje na globální obor názvů.

```cpp
// using_declaration3.cpp
#include <stdio.h>

void f() {
   printf_s("In f\n");
}

namespace A {
   void g() {
      printf_s("In A::g\n");
   }
}

namespace X {
   using ::f;   // global f is also visible as X::f
   using A::g;   // A's g is now visible as X::g
}

void h() {
   printf_s("In h\n");
   X::f();   // calls ::f
   X::g();   // calls A::g
}

int main() {
   h();
}
```

```Output
In h
In f
In A::g
```

## <a name="example"></a>Příklad

Při použití prohlášení, synonymum vytvořené deklarace odkazuje pouze na definice, které jsou platné místě na pomocí deklarace. Definice přidaní do oboru názvů using prohlášení nejsou platná synonyma.

Název určené **pomocí** deklarace je alias pro jeho původní název. To nemá vliv na typ propojení a další atributy původní deklarace.

```cpp
// post_declaration_namespace_additions.cpp
// compile with: /c
namespace A {
   void f(int) {}
}

using A::f;   // f is a synonym for A::f(int) only

namespace A {
   void f(char) {}
}

void f() {
   f('a');   // refers to A::f(int), even though A::f(char) exists
}

void b() {
   using A::f;   // refers to A::f(int) AND A::f(char)
   f('a');   // calls A::f(char);
}
```

## <a name="example"></a>Příklad

S ohledem na funkce v oborech názvů, pokud sadu místní deklarace a používání deklarace pro jeden název jsou uvedeny v deklarativním regionu, všechny musí odkazovat na stejnou entitu, nebo všechny musí odkazovat na funkce.

```cpp
// functions_in_namespaces1.cpp
// C2874 expected
namespace B {
    int i;
    void f(int);
    void f(double);
}

void g() {
    int i;
    using B::i;   // error: i declared twice
    void f(char);
    using B::f;   // ok: each f is a function
}
```

V příkladu výše `using B::i` příkaz způsobí, že druhý `int i` být deklarován v `g()` funkce. `using B::f` Příkaz není v konfliktu s `f(char)` fungovat, protože funkce názvy zavedené `B::f` mají různé typy parametrů.

## <a name="example"></a>Příklad

Deklarace lokální funkce nemůže mít stejný název a typ jako funkce zavedená pomocí deklarace. Příklad:

```cpp
// functions_in_namespaces2.cpp
// C2668 expected
namespace B {
    void f(int);
    void f(double);
}

namespace C {
    void f(int);
    void f(double);
    void f(char);
}

void h() {
    using B::f;          // introduces B::f(int) and B::f(double)
    using C::f;          // C::f(int), C::f(double), and C::f(char)
    f('h');              // calls C::f(char)
    f(1);                // C2668 ambiguous: B::f(int) or C::f(int)?
    void f(int);         // C2883 conflicts with B::f(int) and C::f(int)
}
```

## <a name="example"></a>Příklad

S ohledem na dědičnost když pomocí deklarace zavádí název ze základní třídy do oboru / / coleserveritem, členské funkce v odvozené třídě přepsat virtuální členská funkce se stejnými typy název a argument v základní třídě.

```cpp
// using_declaration_inheritance1.cpp
#include <stdio.h>
struct B {
   virtual void f(int) {
      printf_s("In B::f(int)\n");
   }

   virtual void f(char) {
      printf_s("In B::f(char)\n");
   }

   void g(int) {
      printf_s("In B::g\n");
   }

   void h(int);
};

struct D : B {
   using B::f;
   void f(int) {   // ok: D::f(int) overrides B::f(int)
      printf_s("In D::f(int)\n");
   }

   using B::g;
   void g(char) {   // ok: there is no B::g(char)
      printf_s("In D::g(char)\n");
   }

   using B::h;
   void h(int) {}   // Note: D::h(int) hides non-virtual B::h(int)
};

void f(D* pd) {
   pd->f(1);     // calls D::f(int)
   pd->f('a');   // calls B::f(char)
   pd->g(1);     // calls B::g(int)
   pd->g('a');   // calls D::g(char)
}

int main() {
   D * myd = new D();
   f(myd);
}
```

```Output
In D::f(int)
In B::f(char)
In B::g
In D::g(char)
```

## <a name="example"></a>Příklad

Všechny výskyty názvu uvedených v pomocí prohlášení musí být přístupná. Zejména pokud odvozená třída používá, a s použitím deklarace pro přístup ke členu základní třídy, název člena musí být přístupná. Pokud je název, který funkce přetíženého členu, všechny funkce s názvem musí být přístupná.

Další informace o usnadnění přístupu členů, naleznete v tématu [řízení přístupu členů](../cpp/member-access-control-cpp.md).

```cpp
// using_declaration_inheritance2.cpp
// C2876 expected
class A {
private:
   void f(char);
public:
   void f(int);
protected:
   void g();
};

class B : public A {
   using A::f;   // C2876: A::f(char) is inaccessible
public:
   using A::g;   // B::g is a public synonym for A::g
};
```

## <a name="see-also"></a>Viz také:

[Obory názvů](../cpp/namespaces-cpp.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)