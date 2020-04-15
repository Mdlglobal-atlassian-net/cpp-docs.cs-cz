---
title: řízení přístupu ke členu (C++)
ms.date: 11/19/2018
helpviewer_keywords:
- access control [C++]
- member access [C++]
- member-access control [C++]
ms.assetid: 2d596bca-56ad-4277-94e1-ce3db45fa14a
ms.openlocfilehash: e8f62e82ebb7fcc18be5ac7d203df0fb46c9b635
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369863"
---
# <a name="member-access-control-c"></a>řízení přístupu ke členu (C++)

Ovládací prvky přístupu umožňují oddělit [veřejné](../cpp/public-cpp.md) rozhraní třídy od podrobností [soukromé](../cpp/private-cpp.md) implementace a [chráněných](../cpp/protected-cpp.md) členů, které jsou určeny pouze pro použití odvozenými třídami. Specifikátor přístupu se vztahuje na všechny členy deklarované po něm, dokud nebude zjištěn další specifikátor přístupu.

```cpp
class Point
{
public:
    Point( int, int ) // Declare public constructor.;
    Point();// Declare public default constructor.
    int &x( int ); // Declare public accessor.
    int &y( int ); // Declare public accessor.

private:                 // Declare private state variables.
    int _x;
    int _y;

protected:      // Declare protected function for derived classes only.
    Point ToWindowCoords();
};
```

Výchozí přístup je **soukromý** ve třídě a **veřejný** ve struktuře nebo sjednocení. Specifikátory přístupu ve třídě lze použít libovolný počet opakování v libovolném pořadí. Přidělení úložiště pro objekty typů třídy je závislé na implementaci, ale je zaručeno, že členům budou přiřazeny postupné vyšší adresy paměti mezi specifikátory přístupu.

## <a name="member-access-control"></a>Ovládací prvek přístupu členů

|Typ přístupu|Význam|
|--------------------|-------------|
|[private](../cpp/private-cpp.md)|Členy třídy deklarované jako **soukromé** mohou používat pouze členské funkce a přátelé (třídy nebo funkce) třídy.|
|[protected](../cpp/protected-cpp.md)|Členy třídy deklarované jako **chráněné** mohou být použity členské funkce a přátelé (třídy nebo funkce) třídy. Navíc je možné je použít třídami odvozenými z třídy.|
|[public](../cpp/public-cpp.md)|Členy třídy deklarované jako **veřejné** mohou být použity libovolnou funkcí.|

Řízení přístupu pomůže zabránit používání objektů způsoby, které nebyly k použití určeny. Tato ochrana je ztracena při provedení explicitních převodů typu (přetypování).

> [!NOTE]
> Řízení přístupu se vztahuje rovněž na všechny názvy: členské funkce, data členů, vnořené třídy a enumerátory.

## <a name="access-control-in-derived-classes"></a>Řízení přístupu v odvozených třídách

Dva faktory řídí, které členy základní třídy jsou přístupné v odvozené třídě; tyto stejné faktory řídí přístup k zděděné členy v odvozené třídě:

- Určuje, zda odvozená třída deklaruje základní třídu pomocí specifikátoru **veřejného** přístupu.

- Jaký přístup k členu je v základní třídě.

V následující tabulce je uvedena interakce mezi těmito faktory a způsob určení přístupu členů základní třídy.

### <a name="member-access-in-base-class"></a>Přístup členů v základní třídě

|private|protected|Public|
|-------------|---------------|------------|
|Vždy nepřístupné bez ohledu na přístup k odvození|Soukromé v odvozené třídě, pokud používáte soukromé odvození|Soukromé v odvozené třídě, pokud používáte soukromé odvození|
||Chráněno v odvozené třídě, pokud používáte chráněnou odvození|Chráněno v odvozené třídě, pokud používáte chráněnou odvození|
||Chráněno v odvozené třídě, pokud používáte public derivation|Veřejné v odvozené třídě, pokud používáte public derivation|

Ilustruje to následující příklad:

```cpp
// access_specifiers_for_base_classes.cpp
class BaseClass
{
public:
    int PublicFunc(); // Declare a public member.
protected:
    int ProtectedFunc(); // Declare a protected member.
private:
    int PrivateFunc(); // Declare a private member.
};

// Declare two classes derived from BaseClass.
class DerivedClass1 : public BaseClass
{
    void foo()
    {
        PublicFunc();
        ProtectedFunc();
        PrivateFunc(); // function is inaccessible
    }
};

class DerivedClass2 : private BaseClass
{
    void foo()
    {
        PublicFunc();
        ProtectedFunc();
        PrivateFunc(); // function is inaccessible
    }
};

int main()
{
    DerivedClass1 derived_class1;
    DerivedClass2 derived_class2;
    derived_class1.PublicFunc();
    derived_class2.PublicFunc(); // function is inaccessible
}
```

V `DerivedClass1`aplikaci `PublicFunc` je členská `ProtectedFunc` funkce veřejným členem `BaseClass` a je chráněným členem, protože je třídou veřejné základní. `PrivateFunc`je privátní pro `BaseClass`, a je nepřístupný pro všechny odvozené třídy.

V `DerivedClass2`aplikaci `PublicFunc` `ProtectedFunc` funkce a jsou `BaseClass` považovány za soukromé členy, protože je soukromé základní třídy. Opět `PrivateFunc` je privátní a `BaseClass`je nepřístupný pro všechny odvozené třídy.

Odvozenou třídu můžete deklarovat bez specifikátoru přístupu základní třídy. V takovém případě je odvození považováno za soukromé, pokud deklarace odvozené třídy používá klíčové slovo **třídy.** Odvození je považováno za veřejné, pokud deklarace odvozené třídy používá klíčové slovo **strukturní.** Například následující kód:

```cpp
class Derived : Base
...
```

odpovídá:

```cpp
class Derived : private Base
...
```

Podobně následující kód:

```cpp
struct Derived : Base
...
```

odpovídá:

```cpp
struct Derived : public Base
...
```

Všimněte si, že členové deklarované jako soukromé přístup nejsou přístupné funkce nebo odvozené třídy, pokud tyto funkce nebo třídy jsou deklarovány pomocí **deklarace friend** v základní třídě.

Typ **sjednocení** nemůže mít základní třídu.

> [!NOTE]
> Při zadávání soukromé základní třídy je vhodné explicitně použít klíčové slovo **private,** aby uživatelé odvozené třídy pochopili přístup člena.

## <a name="access-control-and-static-members"></a>Řízení přístupu a statické členy

Zadáte-li základní třídu jako **soukromou**, ovlivní pouze nestatické členy. Veřejné statické členy jsou v odvozených třídách stále přístupné. Avšak přístup ke členům základní třídy pomocí ukazatelů, odkazů nebo objektů může vyžadovat převod, kdy se znovu uplatní časové řízení přístupu. Uvažujte následující příklad:

```cpp
// access_control.cpp
class Base
{
public:
    int Print();             // Nonstatic member.
    static int CountOf();    // Static member.
};

// Derived1 declares Base as a private base class.
class Derived1 : private Base
{
};
// Derived2 declares Derived1 as a public base class.
class Derived2 : public Derived1
{
    int ShowCount();    // Nonstatic member.
};
// Define ShowCount function for Derived2.
int Derived2::ShowCount()
{
   // Call static member function CountOf explicitly.
    int cCount = Base::CountOf();     // OK.

   // Call static member function CountOf using pointer.
    cCount = this->CountOf();  // C2247. Conversion of
                               //  Derived2 * to Base * not
                               //  permitted.
    return cCount;
}
```

V předchozím kódu řízení přístupu zakazuje převod z ukazatele na typ `Derived2` na ukazatele na typ `Base`. Tento **this** ukazatel je implicitně `Derived2 *`typu . Chcete-li `CountOf` vybrat **funkci,** musí být `Base *`převedena na typ . Takový převod není povolen, protože typ `Base` je privátní nepřímá základní třída typu `Derived2`. Převod na typ soukromé základní třídy je přijatelný pouze pro ukazatele na přímé odvozené třídy. Proto lze ukazatele typu `Derived1 *` převést na typ `Base *`.

Explicitní volání funkce `CountOf` bez použití ukazatele, odkazu nebo objektu neprovede žádný převod. Proto je toto volání povoleno.

Členové a přátelé odvozené třídy `T` mohou převést ukazatel na typ `T` na ukazatel na přímou soukromou základní třídu typu `T`.

## <a name="access-to-virtual-functions"></a>Přístup k virtuálním funkcím

Řízení přístupu použité na [virtuální](../cpp/virtual-cpp.md) funkce je určeno typem použitým k volání funkce. Přepisovací deklarace funkce neovlivňují řízení přístupu pro daný typ. Příklad:

```cpp
// access_to_virtual_functions.cpp
class VFuncBase
{
public:
    virtual int GetState() { return _state; }
protected:
    int _state;
};

class VFuncDerived : public VFuncBase
{
private:
    int GetState() { return _state; }
};

int main()
{
   VFuncDerived vfd;             // Object of derived type.
   VFuncBase *pvfb = &vfd;       // Pointer to base type.
   VFuncDerived *pvfd = &vfd;    // Pointer to derived type.
   int State;

   State = pvfb->GetState();     // GetState is public.
   State = pvfd->GetState();     // C2248 error expected; GetState is private;
}
```

V předchozím příkladu volání virtuální funkce `GetState` pomocí ukazatele na typ `VFuncBase` volá funkci `VFuncDerived::GetState` a funkce `GetState` je považována za veřejnou. Volání funkce `GetState` pomocí ukazatele na typ `VFuncDerived` je však narušením řízení přístupu, protože funkce `GetState` je ve třídě `VFuncDerived` deklarována jako soukromá.

> [!CAUTION]
> Virtuální funkci `GetState` lze zavolat pomocí ukazatele na základní třídu `VFuncBase`. To neznamená, že volaná funkce je verzí této funkce obsaženou v základní třídě.

## <a name="access-control-with-multiple-inheritance"></a>Řízení přístupu s více násobnou dědičností

Ve svazech vícenásobné dědičnosti zahrnujících virtuální základní třídy lze konkrétního názvu dosáhnout více cestami. Protože v případě těchto různých cest mohou platit různá řízení přístupu, volí kompilátor volí, která poskytuje nejvíce přístupu. Prohlédněte si následující obrázek.

![Přístup podél cest grafu dědičnosti](../cpp/media/vc38v91.gif "Přístup podél cest grafu dědičnosti") <br/>
Přístup podél cest grafu dědičnosti

Na obrázku je název deklarovaný ve třídě `VBase` vždy dosažen prostřednictvím třídy `RightPath`. Pravá cesta je přístupnější, protože třída `RightPath` deklaruje třídu `VBase` jako veřejnou základní, zatímco třída `LeftPath` deklaruje třídu `VBase` jako soukromou.

## <a name="see-also"></a>Viz také

[Referenční příručka jazyka C++](../cpp/cpp-language-reference.md)
