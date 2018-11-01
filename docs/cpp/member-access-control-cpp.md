---
title: řízení přístupu ke členu (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- access control [C++]
- member access [C++]
- member-access control [C++]
ms.assetid: 2d596bca-56ad-4277-94e1-ce3db45fa14a
ms.openlocfilehash: ee4e9d89878aab4be2e4daf45525f9e951d214f2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50611416"
---
# <a name="member-access-control-c"></a>řízení přístupu ke členu (C++)

Řízení přístupu vám umožňují oddělit [veřejné](../cpp/public-cpp.md) rozhraní třídy z [privátní](../cpp/private-cpp.md) podrobnosti implementace a [chráněné](../cpp/protected-cpp.md) členy, které jsou určeny pouze pro použití podle odvozené třídy. Specifikátor přístupu se vztahuje na všechny členy deklarované za ním až do dalšího specifikátoru přístupu.

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

Přístup k výchozím **privátní** ve třídě, a **veřejné** v struktura nebo sjednocení. Specifikátory přístupu ve třídě může být libovolný počet pokusů o použít v libovolném pořadí. Přidělení úložiště pro objekty typů třídy je závislé na implementaci, ale je zaručeno, že členům budou přiřazeny postupné vyšší adresy paměti mezi specifikátory přístupu.

## <a name="member-access-control"></a>Ovládací prvek přístupu členů

|Typ přístupu|Význam|
|--------------------|-------------|
|[private](../cpp/private-cpp.md)|Členy třídy deklarované jako **privátní** mohou být používány pouze členskými funkcemi a přáteli třídy (třídy nebo funkce).|
|[protected](../cpp/protected-cpp.md)|Členy třídy deklarované jako **chráněné** lze použít členskými funkcemi a přáteli třídy (třídy nebo funkce). Navíc je možné je použít třídami odvozenými z třídy.|
|[public](../cpp/public-cpp.md)|Členy třídy deklarované jako **veřejné** lze použít v jakékoli funkci.|

Řízení přístupu pomůže zabránit používání objektů způsoby, které nebyly k použití určeny. Tato ochrana je ztracena při provedení explicitních převodů typu (přetypování).

> [!NOTE]
>  Řízení přístupu se vztahuje rovněž na všechny názvy: členské funkce, data členů, vnořené třídy a enumerátory.

## <a name="access-control-in-derived-classes"></a>Řízení přístupu v odvozených třídách

Ovládací prvek dva faktory, které členy základní třídy jsou k dispozici v odvozené třídě; stejných faktorů řízení přístupu k zděděné členy v odvozené třídě:

- Určuje, zda odvozená třída deklaruje pomocí základní třídy **veřejné** specifikátor přístupu.

- Přístup ke členu Novinky v základní třídě.

Následující tabulka ukazuje interakci mezi tyto faktory a jak určit přístup ke členům základní třídy.

### <a name="member-access-in-base-class"></a>Přístup ke členům v základní třídě.

|private|protected|Public|
|-------------|---------------|------------|
|Vždy nedostupné bez ohledu na to odvozením přístup|V odvozené třídě, pokud používáte privátní odvození privátní|V odvozené třídě, pokud používáte privátní odvození privátní|
||Pokud používáte chráněné odvození chráněné v odvozené třídě|Pokud používáte chráněné odvození chráněné v odvozené třídě|
||Pokud používáte veřejné odvození chráněné v odvozené třídě|Veřejné v odvozené třídě, pokud používáte veřejné odvození|

Následující příklad ukazuje toto:

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

V `DerivedClass1`, členské funkce `PublicFunc` je členem veřejné a `ProtectedFunc` je chráněný člen, protože `BaseClass` se o veřejnou základní třídu. `PrivateFunc` soukromý `BaseClass`, a je nepřístupný pro jakékoli odvozené třídy.

V `DerivedClass2`, funkce `PublicFunc` a `ProtectedFunc` jsou považovány za soukromé členy, protože `BaseClass` je soukromé základní třídy. Opět `PrivateFunc` soukromý `BaseClass`, a je nepřístupný pro jakékoli odvozené třídy.

Je možné deklarovat odvozené třídy bez specifikátoru základní třídy přístup. V takovém případě odvozování považována za soukromou, pokud používá deklaraci odvozené třídy **třídy** – klíčové slovo. Odvození se považuje za veřejné, pokud odvozené třídy prohlášení, použije **struktura** – klíčové slovo. Například následující kód:

```cpp
class Derived : Base
...
```

je ekvivalentní:

```cpp
class Derived : private Base
...
```

Podobně následující kód:

```cpp
struct Derived : Base
...
```

je ekvivalentní:

```cpp
struct Derived : public Base
...
```

Všimněte si, že nejsou dostupné na funkce členy deklarované jako soukromý přístup nebo pokud těchto funkcí nebo tříd jsou deklarovány pomocí odvozené třídy **friend** deklarace v základní třídě.

A **sjednocení** typ nemůže mít základní třídu.

> [!NOTE]
>  Při zadávání soukromé základní třídy, je vhodné explicitně použít **privátní** – klíčové slovo to uživatelé odvozené třídy pochopit přístup ke členu.

## <a name="access-control-and-static-members"></a>Řízení přístupu a statické členy

Pokud zadáte základní třídu jako **privátní**, ovlivní to pouze nestatické členy. Veřejné statické členy jsou v odvozených třídách stále přístupné. Avšak přístup ke členům základní třídy pomocí ukazatelů, odkazů nebo objektů může vyžadovat převod, kdy se znovu uplatní časové řízení přístupu. Vezměte v úvahu v následujícím příkladu:

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

V předchozím kódu řízení přístupu zakazuje převod z ukazatele na typ `Derived2` na ukazatele na typ `Base`. **To** ukazatel je implicitně typu `Derived2 *`. Chcete-li vybrat `CountOf` funkci **to** musí být převeden na typ `Base *`. Takový převod není povolen, protože typ `Base` je privátní nepřímá základní třída typu `Derived2`. Převod na typ soukromé základní třídy je přijatelný pouze pro ukazatele na přímé odvozené třídy. Proto lze ukazatele typu `Derived1 *` převést na typ `Base *`.

Explicitní volání funkce `CountOf` bez použití ukazatele, odkazu nebo objektu neprovede žádný převod. Proto je toto volání povoleno.

Členové a přátelé odvozené třídy `T` mohou převést ukazatel na typ `T` na ukazatel na přímou soukromou základní třídu typu `T`.

## <a name="access-to-virtual-functions"></a>Přístup k virtuálním funkcím

Řízení přístupu uplatňované pro [virtuální](../cpp/virtual-cpp.md) funkce je určeno typem použitým k volání funkce. Přepisovací deklarace funkce neovlivňují řízení přístupu pro daný typ. Příklad:

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
>  Virtuální funkci `GetState` lze zavolat pomocí ukazatele na základní třídu `VFuncBase`. To neznamená, že volaná funkce je verzí této funkce obsaženou v základní třídě.

## <a name="access-control-with-multiple-inheritance"></a>Řízení přístupu pomocí vícenásobná dědičnost

Ve svazech vícenásobné dědičnosti zahrnujících virtuální základní třídy lze konkrétního názvu dosáhnout více cestami. Protože v případě těchto různých cest mohou platit různá řízení přístupu, volí kompilátor volí, která poskytuje nejvíce přístupu. Prohlédněte si následující obrázek.

![Přístup podél cest grafu dědičnosti](../cpp/media/vc38v91.gif "vc38V91") přístup podél cest grafu dědičnosti

Na obrázku je název deklarovaný ve třídě `VBase` vždy dosažen prostřednictvím třídy `RightPath`. Pravá cesta je přístupnější, protože třída `RightPath` deklaruje třídu `VBase` jako veřejnou základní, zatímco třída `LeftPath` deklaruje třídu `VBase` jako soukromou.

## <a name="see-also"></a>Viz také

[Referenční dokumentace jazyka C++](../cpp/cpp-language-reference.md)
