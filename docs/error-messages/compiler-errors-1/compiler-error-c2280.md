---
title: "C2280 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 04/25/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C2280
helpviewer_keywords: C2280
dev_langs: C++
ms.assetid: e6c5b1fb-2b9b-4554-8ff9-775eeb37161b
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: af19f0a0c347ab0f898a3a3d72b8cca5cb07dad8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2280"></a>C2280 chyby kompilátoru  
  
'*deklarace*': Při pokusu o odkazu na funkci odstraněné  
  
Kompilátor zjistil pokus o odkaz `deleted` funkce. Tato chyba může být způsobeno volání funkce člen, který byl výslovně označen jako `= deleted` ve zdrojovém kódu. Tuto chybu mohl způsobit také voláním do implicitní speciální členské funkce struktura nebo třídu, která automaticky definována a je označen jako `deleted` kompilátorem. Další informace o kompilátor automaticky vygeneruje-li `default` nebo `deleted` speciální členské funkce, najdete v části [speciální členské funkce](../../cpp/special-member-functions.md).  
  
## <a name="example-explicitly-deleted-functions"></a>Příklad: Explicitně odstranit funkce  

Volání explicitně `deleted` funkce způsobí, že k této chybě. Explicitně `deleted` – členská funkce znamená, že třídě nebo struktuře záměrně slouží ke znemožnění jeho použití, takže na tento problém vyřešit, měli byste změnit svůj kód tomu zamezit.  
  
```cpp  
// C2280_explicit.cpp
// compile with: cl /c /W4 C2280_explicit.cpp
struct A {
    A();
    A(int) = delete;
};

struct B {
    A a1;
    A a2 = A(3); // C2280, calls deleted A::A(int)
    // To fix, remove the call to A(int)
};

void f() {
    B b;    // calls implicit B::B(void)
}
```  
  
## <a name="example-uninitialized-data-members"></a>Příklad: Neinicializovaný datové členy  
  
Člena Neinicializovaný odkaz na typ dat nebo `const` – datový člen způsobí, že kompilátor implicitně deklarovat `deleted` výchozí konstruktor. Chcete-li tento problém vyřešit, inicializujte datového člena, když je deklarován.  
  
```cpp  
// C2280_uninit.cpp
// compile with: cl /c C2280_uninit.cpp
struct A {
    const int i; // uninitialized const-qualified data
    // members or reference type data members cause
    // the implicit default constructor to be deleted.
    // To fix, initialize the value in the declaration:
    // const int i = 42;
} a;    // C2280
```  
  
## <a name="example-reference-and-const-data-members"></a>Příklad: Referenční dokumentace a const datové členy  
  
A `const` nebo odkaz na typ datový člen způsobí, že kompilátor deklarovat `deleted` operátor přiřazení pro kopírování. Jakmile inicializován, tyto členy nelze přiřadit, tak jednoduché kopírování nebo přesunutí nemůže pracovat. Chcete-li tento problém vyřešit, doporučujeme že změnit logika odebrat přiřazení operace, které způsobí chybu.  
  
```cpp  
// C2280_ref.cpp
// compile with: cl /c C2280_ref.cpp
extern int k;
struct A {
    A();
    int& ri = k; // a const or reference data member causes 
    // implicit copy assignment operator to be deleted.
};

void f() {
    A a1, a2;
    // To fix, consider removing this assignment.
    a2 = a1;    // C2280
}
```  
  
## <a name="example-movable-deletes-implicit-copy"></a>Příklad: Movable odstraní implicitní kopie  
  
Pokud třída deklaruje konstruktor move nebo operátor přiřazení přesunutí, ale explicitně nedeklaruje kopírovacího konstruktoru, kompilátor implicitně deklaruje kopírovacího konstruktoru a definuje jej jako `deleted`. Podobně, pokud třída deklaruje konstruktor move nebo operátor přiřazení přesunutí, ale explicitně nedeklaruje operátor přiřazení kopírování, kompilátor implicitně deklaruje operátor přiřazení kopírování a definuje jej jako `deleted`. Chcete-li tento problém vyřešit, je potřeba explicitně deklarovat tito členové.  
 
Až se zobrazí chyba C2280 ve spojení s `unique_ptr`, je skoro určitě vzhledem k tomu, že se pokoušíte vyvolat kopírovací konstruktor, který je `deleted` funkce. Návrh `unique_ptr` nelze zkopírovat. Převést vlastnictví místo toho použijte konstruktor move.  

```cpp  
// C2280_move.cpp
// compile with: cl /c C2280_move.cpp
class base  
{  
public:  
    base();  
    ~base(); 
    base(base&&); 
    // Move constructor causes copy constructor to be
    // implicitly declared as deleted. To fix this 
    // issue, you can explicitly declare a copy constructor:
    // base(base&);
    // If you want the compiler default version, do this:
    // base(base&) = default;
};  

void copy(base *p)  
{  
    base b{*p};  // C2280
}  
```  

## <a name="example-variant-and-volatile-members"></a>Příklad: Členy typu Variant a volatile  
  
Nonkonformní a vygenerovaný výchozí konstruktory a destruktory pro anonymní sjednocení byly verze kompilátoru před Visual Studio 2015 Update 2. Tyto jsou nyní implicitně deklarován jako `deleted`. Tyto verze také povoleny nonkonformní implicitní definice `default` kopírování a přesouvání konstruktory a `default` kopírování a přesouvání operátory přiřazení v tříd a struktur, které mají `volatile` proměnné členů. Kompilátor teď zvažuje do mají netriviální konstruktory a operátory přiřazení a nepodporuje generování `default` implementace. Když tyto třídy je členem spojení nebo anonymní – typ union uvnitř třídu, přesunutí a kopie konstruktorů a kopírování a přesunutí operátory přiřazení pro třídy nebo sjednocení jsou implicitně definované jako `deleted`. Chcete-li tento problém vyřešit, je potřeba explicitně deklarovat vyžaduje speciální členské funkce.  
  
```cpp  
// C2280_variant.cpp
// compile with: cl /c C2280_variant.cpp
struct A {  
    A() = default;
    A(const A&);
};  

struct B {  
    union {  
        A a;  
        int i;  
    };
    // To fix this issue, declare the required 
    // special member functions:
    // B(); 
    // B(const B& b);
};  

int main() {
    B b1;  
    B b2(b1);  // C2280  
}
```  
  
## <a name="example-indirect-base-members-deleted"></a>Příklad: Nepřímé základní členy odstranit  
  
Verze kompilátoru před Visual Studio 2015 Update 2 byly nonkonformní a povoleny odvozené třídy za účelem volání speciální členské funkce nepřímo odvozené `private virtual` základní třídy. Kompilátor Chyba kompilátoru C2280 vystaví teď, když takové Přišla žádost.  
  
V tomto příkladu třída `top` nepřímo odvozuje od privátní virtuální `base`. V kódu vyhovující, díky členů `base` nepřístupný pro `top`; na objektu typu `top` nemůže být výchozí sestavený nebo zničeno. Odstranění tohoto problému v kódu, který spoléhali na staré chování kompilátoru, změňte třídu zprostředkující používat `protected virtual` odvození nebo změňte `top` třídu se má použít přímé odvození:  

```cpp  
// C2280_indirect.cpp
// compile with: cl /c C2280_indirect.cpp
class base  
{  
protected:  
    base();  
    ~base();  
};  

class middle : private virtual base {}; 
// Possible fix: Replace line above with:
// class middle : protected virtual base {};
class top : public virtual middle {};    // C4594, C4624
// Another possible fix: use direct derivation:
// class top : public virtual middle, private virtual base {};   

void destroy(top *p)  
{  
    delete p;  // C2280  
}  
```  
  