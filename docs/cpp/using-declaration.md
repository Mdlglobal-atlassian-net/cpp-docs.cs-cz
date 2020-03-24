---
title: using – deklarace
ms.date: 11/04/2016
helpviewer_keywords:
- using declaration
- declarations [C++], using-declaration
- namespaces [C++], unqualified names in
- using keyword [C++]
ms.assetid: 4184e2b1-3adc-408e-b5f3-0b3f8b554723
ms.openlocfilehash: d762ea36e83d2384b7bb50c2914f6a634c134d15
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187840"
---
# <a name="using-declaration"></a>using – deklarace

Deklarace **using** zavádí název do deklarativní oblasti, ve které se zobrazí deklarace using.

## <a name="syntax"></a>Syntaxe

```
using [typename] nested-name-specifier unqualified-id ;
using declarator-list ;
```

### <a name="parameters"></a>Parametry

*vnořené specifikátory názvu* Sekvence oboru názvů, třídy nebo výčtových názvů a operátorů rozlišení oboru (::), ukončené operátorem rozlišení oboru. K zavedení názvu z globálního oboru názvů se dá použít operátor rozlišení s jedním oborem. Hodnota **TypeName** pro klíčové slovo je volitelná a může být použita k překladu závislých názvů při zavlečení do šablony třídy ze základní třídy.

*nekvalifikované ID* Nekvalifikovaný výraz ID, který může být identifikátorem, název přetíženého operátoru, uživatelem definovaný operátor literálu nebo název funkce pro převod, název destruktoru třídy nebo název šablony a seznam argumentů.

*deklarátor – seznam* Seznam oddělený čárkami [**TypeName**] *Nested-Name-specifikátor* *nekvalifikovaného* názvu (deklarátory) následovaný volitelně třemi tečkami.

## <a name="remarks"></a>Poznámky

Deklarace using zavádí Nekvalifikovaný název jako synonymum pro entitu deklarovanou jinde. Umožňuje použití jednoho názvu z konkrétního oboru názvů bez explicitní kvalifikace v oblasti deklarace, ve které se zobrazí. To je na rozdíl od [direktivy using](../cpp/namespaces-cpp.md#using_directives), která umožňuje použití *všech* názvů v oboru názvů bez kvalifikace. Klíčové slovo **using** je také použito pro [aliasy typu](../cpp/aliases-and-typedefs-cpp.md).

## <a name="example"></a>Příklad

Deklarace using se dá použít v definici třídy.

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

Při použití k deklaraci člena musí deklarace using odkazovat na člena základní třídy.

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

Členy deklarované pomocí deklarace using lze odkazovat pomocí explicitní kvalifikace. Předpona `::` odkazuje na globální obor názvů.

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

Pokud je vytvořena deklarace using, synonymum vytvořené deklarací odkazuje pouze na definice, které jsou platné v místě deklarace using. Definice přidané do oboru názvů po deklaraci using nejsou platnými synonymy.

Název definovaný deklarací **using** je alias pro jeho původní název. Neovlivňuje typ, propojení ani jiné atributy původní deklarace.

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

V souvislosti s funkcemi v oborech názvů, pokud je v deklarativní oblasti uvedena sada místních deklarací a použití deklarace pro jeden název, musí všechny odkazovat na stejnou entitu nebo musí všechny odkazovat na funkce.

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

V příkladu výše příkaz `using B::i` způsobí, že ve funkci `g()` je deklarován druhý `int i`. Příkaz `using B::f` není v konfliktu s funkcí `f(char)`, protože názvy funkcí zavedené `B::f` mají jiné typy parametrů.

## <a name="example"></a>Příklad

Deklarace místní funkce nemůže mít stejný název a typ jako funkce zavedená pomocí deklarace. Příklad:

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

S ohledem na dědění, když deklarace using zavádí název ze základní třídy do oboru odvozené třídy, členské funkce v odvozené třídě přepíší virtuální členské funkce se stejným názvem a typy argumentů v základní třídě.

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

Všechny instance názvu uvedené v deklaraci using musí být přístupné. Zejména pokud odvozená třída používá deklaraci using pro přístup ke členu základní třídy, musí být název člena přístupný. Pokud je název typu přetížené členské funkce, pak všechny funkce s názvem musí být přístupné.

Další informace o dostupnosti členů naleznete v tématu [Member-Access Control](../cpp/member-access-control-cpp.md).

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

## <a name="see-also"></a>Viz také

[Obory názvů](../cpp/namespaces-cpp.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)
