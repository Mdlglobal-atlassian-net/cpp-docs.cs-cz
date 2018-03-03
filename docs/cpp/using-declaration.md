---
title: "Using – deklarace | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- using declaration
- declaring namespaces, unqualified names in namespaces
- declarations [C++], using-declaration
- namespaces [C++], unqualified names in
- using keyword [C++]
- declarations [C++], namespaces
ms.assetid: 4184e2b1-3adc-408e-b5f3-0b3f8b554723
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c6bf39dfdb4f59bcf54ce1ddd5174f1e3a55e3a0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="using-declaration"></a>using – deklarace
Pomocí deklarace představuje název do deklarativní oblast, ve kterém pomocí deklarace se zobrazí.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
using [typename] nested-name-specifier unqualified-id ;  
using declarator-list ;  
```  
  
### <a name="parameters"></a>Parametry
  
*vnořené specifikátor název*  
    Pořadí oboru názvů, třídy, nebo výčet názvů a oboru rozlišení operátory (:), ukončila příkazem operátor řešení rozsahu. Operátor řešení jednoho rozsahu lze zavést název z globálního oboru názvů. Klíčové slovo `typename` je volitelný a může sloužit k přeložit názvy závislých prvků při zavedená do třídy šablony ze základní třídy.  
  
*nekvalifikované id*  
    Nekvalifikované id výraz, který může být identifikátor, název přetížené operátor, uživatelem definované literálu operátor nebo převod název funkce, destruktor název třídy nebo šablonu název a argument seznamu.  
  
*deklarátor seznamu*  
    Obsahuje čárkami oddělený seznam [`typename`] *vnořené specifikátor název* *nekvalifikované id* deklarátory, volitelně následovaný tři tečky.
    
## <a name="remarks"></a>Poznámky  
A pomocí deklarace zavádí neúplný název jako synonymum pro entitu deklarovaný jinde. To umožňuje z konkrétní názvů bez explicitní kvalifikace v deklaraci oblasti, ve kterém se zobrazí pouze jeden název. To je rozdíl k [using – direktiva](../cpp/namespaces-cpp.md#using_directives), což umožňuje *všechny* názvy v oboru názvů do bez kvalifikace jde používat. `using` – Klíčové slovo slouží také k [zadejte aliasy](../cpp/aliases-and-typedefs-cpp.md).  
  
## <a name="example"></a>Příklad  
 A pomocí deklarace lze použít v definici třídy.  
  
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
Pokud se používá k deklaraci členem, pomocí deklarace musí odkazovat na člena, základní třídy.  
  
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
Členy deklarovat pomocí, pomocí deklarace můžete odkazovat pomocí explicitní kvalifikace. `::` Předponu odkazuje na obor názvů globální.  
  
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
Při použití prohlášení, vytvořené deklaraci synonymum odkazuje pouze na definice, které jsou platné v místě na pomocí deklarace. Přidat do oboru názvů za použití definice deklarace nejsou platná synonyma.  
  
Název definované `using` deklarace je alias pro jeho původní název. Typ, propojení nebo dalšími atributy původního prohlášení neovlivňuje.  
  
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
S ohledem na funkce v oborech názvů, pokud sada místní deklarace a používání deklarace pro jeden název jsou uvedeny v deklarativní oblast, všechny musí odkazovat na stejnou entitu nebo všechny musí odkazovat na funkce.  
  
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
  
 V příkladu nahoře `using B::i` příkaz způsobuje druhý `int i` být deklarován v `g()` funkce. `using B::f` Příkaz není v konfliktu s `f(char)` fungovat, protože názvy funkcí zaváděné `B::f` mají různé typy parametrů.  
  
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
 S ohledem na dědičnosti při použití deklarace představuje název ze základní třídy do odvozené třídy oboru, členské funkce v odvozené třídě přepsat virtuální členské funkce se stejnými typy název a argument v základní třídě.  
  
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
Všechny instance názvu uvedených v pomocí deklarace musí být přístupné. Konkrétně, pokud je odvozená třída používá, pomocí prohlášení o přístup člena základní třídy, název člena musí být přístupné. Pokud název je, že funkce přetížené člen, pak všechny funkce s názvem musí být přístupné.  
  
Další informace o usnadnění přístupu členů najdete v tématu [řízení přístup ke členu](../cpp/member-access-control-cpp.md).  
  
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
 [Obory názvů](../cpp/namespaces-cpp.md)   
 [Klíčová slova](../cpp/keywords-cpp.md)