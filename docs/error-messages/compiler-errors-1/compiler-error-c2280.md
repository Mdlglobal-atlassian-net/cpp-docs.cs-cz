---
title: Chyba kompilátoru C2280
ms.date: 04/25/2017
f1_keywords:
- C2280
helpviewer_keywords:
- C2280
ms.assetid: e6c5b1fb-2b9b-4554-8ff9-775eeb37161b
ms.openlocfilehash: e1ec032878fefdc1992605df5ee1aa13c673d4cf
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62388901"
---
# <a name="compiler-error-c2280"></a>Chyba kompilátoru C2280

"*deklarace*': Pokus o odkazování na odstraněnou funkci

Kompilátor zjistil pokus o odkaz `deleted` funkce. Tuto chybu může způsobovat volání na členskou funkci, která byla explicitně označena jako `= deleted` ve zdrojovém kódu. Tato chyba může taky způsobovat volání implicitní zvláštní členskou funkci ze struktury nebo třídy, která je automaticky deklarovat a označena jako `deleted` kompilátorem. Další informace o Když kompilátor automaticky generuje `default` nebo `deleted` zvláštní členské funkce, najdete v článku [speciálních členských funkcí](../../cpp/special-member-functions.md).

## <a name="example-explicitly-deleted-functions"></a>Příklad: Explicitně odstraněné funkce

Volání explicitně `deleted` funkce způsobí, že k této chybě. Explicitně `deleted` členská funkce znamená, že dané třídy nebo struktury je záměrně cílem znemožnění jeho použití, takže chcete opravit tento problém, měli byste změnit váš kód jak jí předcházet.

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

## <a name="example-uninitialized-data-members"></a>Příklad: Použít neinicializované datové členy

Datový člen typu neinicializované odkaz nebo `const` datový člen způsobí, že kompilátor implicitně deklarovat `deleted` výchozí konstruktor. Chcete-li vyřešit tento problém, inicializujte datový člen při deklaraci.

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

## <a name="example-reference-and-const-data-members"></a>Příklad: Referenční dokumentace a konstantní datové členy

A `const` nebo odkaz na typ datový člen způsobí, že kompilátor pro deklaraci `deleted` kopírovacího operátoru přiřazení. Po inicializaci tyto členy nelze přiřadit, tak jednoduché kopírování nebo přesunutí nemůže pracovat. Chcete-li vyřešit tento problém, doporučujeme že změnit svoji logiku odebrat přiřazení operací, které způsobí chybu.

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

## <a name="example-movable-deletes-implicit-copy"></a>Příklad: Pohyblivé odstraní implicitní kopie

Pokud třída deklaruje přenosový konstruktor nebo operátor přiřazení přesunu, ale nedeklaruje explicitně kopírovací konstruktor, kompilátor implicitně deklaruje kopírovací konstruktor a definuje jako `deleted`. Podobně, pokud třída deklaruje přenosový konstruktor nebo operátor přiřazení přesunu, ale nedeklaruje explicitně operátor přiřazení kopie, kompilátor implicitně deklaruje operátor přiřazení kopie a definuje jako `deleted`. Chcete-li vyřešit tento problém, musíte explicitně deklarovat těchto členů.

Když se zobrazí chyba C2280 v souvislosti s `unique_ptr`, je téměř jistě vzhledem k tomu, že se pokoušíte vyvolání konstruktoru kopie, což je `deleted` funkce. Návrh `unique_ptr` nelze zkopírovat. Pokud chcete převést vlastnictví místo toho použijte konstruktor přesunutí.

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

## <a name="example-variant-and-volatile-members"></a>Příklad: Členy typu variant a volatile

Verze kompilátoru před Visual Studio 2015 Update 2 byly nonkonformní a generovaný výchozí konstruktory a destruktory pro anonymní sjednocení. Ty se teď implicitně deklarovaný jako `deleted`. Tato verze také povoleny nonkonformní implicitní definice `default` kopírování a přesun konstruktorů a `default` kopírování a přesouvání operátory přiřazení v tříd a struktur, které mají `volatile` členské proměnné. Kompilátor nyní bere v úvahu tyto netriviálními konstruktory a operátory přiřazení a negeneruje `default` implementace. Pokud takové třídy je člen sjednocení nebo anonymní sjednocení uvnitř třídy, kopírování a přesun konstruktory a operátory přiřazení přesunutí a kopírování sjednocení nebo třídy jsou implicitně definovaný jako `deleted`. Chcete-li vyřešit tento problém, musíte explicitně deklarovat vyžaduje zvláštní členské funkce.

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

## <a name="example-indirect-base-members-deleted"></a>Příklad: Odstranit nepřímých základních členů.

Verze kompilátoru před Visual Studio 2015 Update 2 byly nonkonformní a povolený odvozené třídy za účelem volání zvláštní členské funkce nepřímo odvozeny `private virtual` základních tříd. Kompilátor vyvolá chybu kompilátoru C2280 nyní, po provedení těchto volání.

V tomto příkladu třída `top` nepřímo odvozuje od privátní virtuální `base`. Vyhovující kódu, díky tomu členy `base` do nedostupný `top`; objekt typu `top` nemůže být výchozí vytvořen nebo zničení. Chcete-li vyřešit tento problém v kódu, který spoléhal na staré chování kompilátoru, změňte zprostředkující třída použití `protected virtual` odvození nebo změna `top` třídu použít odvození s přímým přístupem:

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
