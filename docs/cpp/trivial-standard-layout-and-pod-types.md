---
title: Typy triviální, Standard-layout, POD a Literal
ms.date: 04/05/2018
ms.assetid: 2b23a7be-9bad-49fc-8298-31a9a7c556b0
ms.openlocfilehash: 2745302b3ebd7927e9d839e4661e884a2bd91042
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79418389"
---
# <a name="trivial-standard-layout-pod-and-literal-types"></a>Typy triviální, Standard-layout, POD a Literal

Termín *rozložení* odkazuje na to, jak jsou členy objektu typu třída, struktura nebo sjednocení uspořádány do paměti. V některých případech je rozložení správně definováno specifikací jazyka. Pokud však třída nebo struktura obsahuje určité C++ jazykové funkce, jako jsou virtuální základní třídy, virtuální funkce, členové s jiným řízením přístupu, pak je kompilátor zdarma zvolit rozložení. Toto rozložení se může lišit v závislosti na tom, jaké optimalizace se probíhají, a v mnoha případech objekt nemusí dokonce zabírat souvislou oblast paměti. Například pokud třída má virtuální funkce, všechny instance této třídy mohou sdílet jednu tabulku virtuálních funkcí. Tyto typy jsou velmi užitečné, ale mají také omezení. Vzhledem k tomu, že rozložení není definováno, nelze je předat do programů napsaných v jiných jazycích, jako je například C, a protože by mohly být nesouvislé, nelze je spolehlivě kopírovat pomocí rychlých funkcí nízké úrovně, například `memcopy`nebo serializovaných přes síť.

Chcete-li povolit kompilátory i C++ programy a metaprograms z důvodu vhodnosti jakéhokoli daného typu pro operace, které závisí na konkrétním rozložení paměti, c++ 14 zavedl tři kategorie jednoduchých tříd a struktur: *triviální*, *standardní-rozložení*a *pod* nebo prostá stará data. Standardní knihovna má šablony funkcí `is_trivial<T>`, `is_standard_layout<T>` a `is_pod<T>`, které určují, zda daný typ patří do dané kategorie.

## <a name="trivial-types"></a>Triviální typy

V případě, že třída nebo C++ struktura v v má poskytnuté kompilátorem nebo explicitně výchozí členské funkce, pak je triviální typ. Zabírá souvislou oblast paměti. Může mít členy s různými specifikátory přístupu. V C++nástroji je kompilátor bezplatný pro výběr způsobu řazení členů v této situaci. Proto můžete tyto objekty memcopy, ale nemůžete je spolehlivě spotřebovávat z programu v jazyce C. Triviální typ T může být zkopírován do pole char nebo unsigned char a bezpečně zkopírován zpět do proměnné T. Všimněte si, že z důvodu požadavků na zarovnání mohou být mezi členy typu oddálení bajty.

Triviální typy mají triviální výchozí konstruktor, triviální kopírovací konstruktor, operátor přiřazení triviální kopie a triviální destruktor. V každém případě *triviální* znamená, že konstruktor/operator/destruktor není poskytnut uživatelem a patří do třídy, která má

- žádné virtuální funkce ani virtuální základní třídy

- žádné základní třídy s odpovídajícím netriviálním konstruktorem/operátorem/destruktorem

- žádné datové členy typu třídy s odpovídajícím netriviálním konstruktorem/operátorem/destruktorem

Následující příklady znázorňují triviální typy. V Trivial2 přítomnost konstruktoru `Trivial2(int a, int b)` vyžaduje, abyste zadali výchozí konstruktor. Pro typ, který má být kvalifikován jako triviální, je nutné explicitně výchozí konstruktor.

```cpp
struct Trivial
{
      int i;
private:
   int j;
   };

struct Trivial2
{
   int i;
   Trivial2(int a, int b) : i(a), j(b) {}
   Trivial2() = default;
   private:
   int j;   // Different access control
};
```

## <a name="standard-layout-types"></a>Standardní typy rozložení

Pokud třída nebo struktura neobsahuje určité C++ jazykové funkce, jako jsou virtuální funkce, které se nenašly v jazyce C, a všichni členové mají stejný ovládací prvek přístupu, jedná se o typ standardního rozložení. Je memcopy a rozložení je dostatečně definované tak, aby je bylo možné spotřebovat pomocí programů v jazyce C. Standardní typy rozložení mohou mít uživatelsky definované speciální členské funkce. Kromě toho standardní typy rozložení mají tyto vlastnosti:

- žádné virtuální funkce ani virtuální základní třídy

- všechny nestatické datové členy mají stejný řízení přístupu.

- všechny nestatické členy typu třídy jsou standardní – rozložení.

- jakékoli základní třídy jsou standardní – rozložení.

- nemá žádné základní třídy stejného typu jako první nestatický datový člen.

- splňuje jednu z těchto podmínek:

  - v nejvíce odvozené třídě není žádný nestatický datový člen a ne více než jedna základní třída s nestatickými datovými členy.

  - nemá žádné základní třídy s nestatickými datovými členy.

Následující kód ukazuje jeden příklad typu standardního rozložení:

```cpp
struct SL
{
   // All members have same access:
   int i;
   int j;
   SL(int a, int b) : i(a), j(b) {} // User-defined constructor OK
};
```

Poslední dva požadavky mohou být lépe znázorněny kódem. V následujícím příkladu, i když je základem standardní rozložení, `Derived` není standardní rozložení, protože IT (nejvíce odvozené třídy) a `Base` mají nestatické datové členy:

```cpp
struct Base
{
   int i;
   int j;
};

// std::is_standard_layout<<Derived> == false!
struct Derived : public Base
{
   int x;
   int y;
};
```

V tomto příkladu `Derived` je standardní rozložení, protože `Base` nemá žádné nestatické datové členy:

```cpp
struct Base
{
   void Foo() {}
};

// std::is_standard_layout<<Derived> == true
struct Derived : public Base
{
   int x;
   int y;
};
```

Odvozený by také představoval standardní rozložení, pokud `Base` mít datové členy a `Derived` obsahovaly jenom členské funkce.

## <a name="pod-types"></a>Typy POD

Když je třída nebo struktura triviální a standardní – je to typ POD (prostý stará data). Rozložení paměti typu POD je tedy souvislé a každý člen má vyšší adresu než člen, který byl deklarován před ním, aby bylo možné na těchto typech použít bajt pro kopie bajtů a binární I výstupní vstupně-výstupní operace.  Skalární typy, jako je int, jsou také POD typy. Typy POD třídy, které jsou třídy, mohou mít pouze POD typy jako nestatické datové členy.

## <a name="example"></a>Příklad

Následující příklad ukazuje rozdíly mezi typy triviální, Standard-layout a POD:

```cpp
#include <type_traits>
#include <iostream>

using namespace std;

struct B
{
protected:
   virtual void Foo() {}
};

// Neither trivial nor standard-layout
struct A : B
{
      int a;
   int b;
   void Foo() override {} // Virtual function
};

// Trivial but not standard-layout
struct C
   {
      int a;
private:
   int b;   // Different access control
};

// Standard-layout but not trivial
struct D
{
   int a;
   int b;
   D() {} //User-defined constructor
};

struct POD
{
   int a;
   int b;
};

int main()
{
   cout << boolalpha;
   cout << "A is trivial is " << is_trivial<A>() << endl; // false
   cout << "A is standard-layout is " << is_standard_layout<A>() << endl;  // false

   cout << "C is trivial is " << is_trivial<C>() << endl; // true
   cout << "C is standard-layout is " << is_standard_layout<C>() << endl;  // false

   cout << "D is trivial is " << is_trivial<D>() << endl;  // false
   cout << "D is standard-layout is " << is_standard_layout<D>() << endl; // true

   cout << "POD is trivial is " << is_trivial<POD>() << endl; // true
   cout << "POD is standard-layout is " << is_standard_layout<POD>() << endl; // true

   return 0;
}
```

## <a name="literal_types"></a>Typy literálů

Typ literálu je jeden, jehož rozložení lze určit v době kompilace. Typy literálů jsou následující:

- void
- skalární typy
- odkazy
- Pole void, skalárních typů nebo odkazů
- Třída, která má triviální destruktor, a jeden nebo více konstruktorů constexpr, které nepřesunou ani nekopírují konstruktory. Kromě toho všechny jeho nestatické datové členy a základní třídy musí být literální typy a nikoli volatile.

## <a name="see-also"></a>Viz také

[Základní koncepty](../cpp/basic-concepts-cpp.md)