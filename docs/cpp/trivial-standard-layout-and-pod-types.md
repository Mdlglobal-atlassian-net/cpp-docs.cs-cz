---
title: Triviální typy, standardní rozložení, POD a literál
ms.date: 04/05/2018
ms.assetid: 2b23a7be-9bad-49fc-8298-31a9a7c556b0
ms.openlocfilehash: 6fe237386e63fcdd96621edabf2b0b66ce72e4f8
ms.sourcegitcommit: 435133128b18cdd02d33d929b16c33e7ec40e9eb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2020
ms.locfileid: "81664138"
---
# <a name="trivial-standard-layout-pod-and-literal-types"></a>Triviální typy, standardní rozložení, POD a literál

*Rozložení* termínodkazuje, jak jsou členové objektu třídy, struktury nebo typu sjednocení uspořádány v paměti. V některých případech je rozložení dobře definováno specifikací jazyka. Ale když třída nebo struktura obsahuje určité funkce jazyka C++, jako jsou virtuální základní třídy, virtuální funkce, členy s různým řízením přístupu, pak kompilátor může zvolit rozložení. Toto rozložení se může lišit v závislosti na tom, jaké optimalizace jsou prováděny a v mnoha případech objekt nemusí ani zabírat souvislou oblast paměti. Například pokud třída má virtuální funkce, všechny instance této třídy může sdílet jednu tabulku virtuálnífunkce. Takové typy jsou velmi užitečné, ale mají také omezení. Vzhledem k tomu, že rozložení není definováno, nelze je předat programům napsaným v jiných jazycích, například v jazyce C, a protože mohou být nesouvislé, nelze je spolehlivě zkopírovat pomocí rychlých funkcí nižší úrovně, například `memcopy`aplikace , ani serializovat v síti.

Chcete-li povolit kompilátory, stejně jako c++ programy a metaprogramy důvod o vhodnosti daného typu pro operace, které závisí na rozložení konkrétní paměti, C++ 14 představil tři kategorie jednoduchých tříd a struktur: *triviální*, *standardní rozložení*a *POD* nebo plain old data. Standardní knihovna má šablony `is_trivial<T>` `is_standard_layout<T>` funkcí `is_pod<T>` a určuje, zda daný typ patří do dané kategorie.

## <a name="trivial-types"></a>Triviální typy

Pokud třída nebo struktura v jazyce C++ má kompilátor poskytované nebo explicitně výchozí speciální členské funkce, pak je triviální typ. Zabírá souvislou paměťovou oblast. Může mít členy s různými specifikátory přístupu. V jazyce C++ kompilátor je zdarma zvolit, jak objednat členy v této situaci. Proto můžete memcopy tyto objekty, ale nelze spolehlivě spotřebovat z programu C. Triviální typ T lze zkopírovat do pole char nebo nepodepsané char a bezpečně zkopírovat zpět do proměnné T. Všimněte si, že z důvodu požadavků na zarovnání může být odsazení bajtů mezi členy typu.

Triviální typy mají triviální výchozí konstruktor, trivial copy konstruktor, triviální operátor přiřazení kopírování a triviální destruktor. V každém případě *triviální* znamená, že konstruktor/operátor/destruktor není poskytován uživatelem a patří do třídy, která

- žádné virtuální funkce nebo virtuální základní třídy,

- žádné základní třídy s odpovídajícím netriviálním konstruktorem/operátorem/destruktorem

- žádné datové členy typu třídy s odpovídajícím netriviálním konstruktorem/operátorem/destruktorem

Následující příklady ukazují triviální typy. V Trivial2 přítomnost konstruktoru `Trivial2(int a, int b)` vyžaduje, abyste poskytli výchozí konstruktor. Pro typ kvalifikovat jako triviální, je nutné explicitně výchozí tento konstruktor.

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

Pokud třída nebo struktura neobsahuje určité funkce jazyka C++, jako jsou virtuální funkce, které nejsou nalezeny v jazyce C, a všichni členové mají stejný přístupový prvek, je to typ standardního rozložení. Je memcopy-able a rozložení je dostatečně definován, že může být spotřebována programy C. Typy standardního rozložení mohou mít uživatelem definované speciální členské funkce. Kromě toho standardní typy rozložení mají tyto vlastnosti:

- žádné virtuální funkce nebo virtuální základní třídy

- všechny nestatické datové členy mají stejné řízení přístupu

- všechny nestatické členy typu třídy jsou standardním rozložením

- všechny základní třídy jsou standardní

- nemá žádné základní třídy stejného typu jako první nestatický datový člen.

- splňuje jednu z těchto podmínek:

  - žádný nestatický datový člen v nejvíce odvozené třídě a ne více než jedna základní třída s nestatickými datovými členy, nebo

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

Poslední dva požadavky mohou být lépe ilustrovány s kódem. V dalším příkladu, i když Base `Derived` je standardní rozložení, není standardní rozložení, `Base` protože oba (nejvíce odvozené třídy) a mají nestatické datové členy:

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

V tomto `Derived` příkladu je `Base` standardní rozložení, protože nemá žádné nestatické datové členy:

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

Odvozené by také standardní `Base` rozložení, pokud `Derived` měl datové členy a měl pouze členské funkce.

## <a name="pod-types"></a>Typy POD

Pokud je třída nebo struktura triviální a standardní rozložení, je typ POD (Plain Old Data). Rozložení paměti typů POD je proto souvislé a každý člen má vyšší adresu než člen, který byl deklarován před ním, takže bajt pro bajt kopie a binární V/O lze provést na tyto typy.  Skalární typy, jako je int jsou také TYPY POD. Typy POD, které jsou třídy může mít pouze POD typy jako nestatické datové členy.

## <a name="example"></a>Příklad

Následující příklad ukazuje rozdíly mezi typy trivial, standard-layout a POD:

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

## <a name="literal-types"></a><a name="literal_types"></a>Doslovné typy

Doslovný typ je ten, jehož rozložení lze určit v době kompilace. Následují literál typy:

- void
- skalární typy
- odkazy
- Pole void, skalární typy nebo odkazy
- Třída, která má triviální destruktor a jeden nebo více konstruktorů constexpr, které nejsou přesunout nebo kopírovat konstruktory. Kromě toho všechny jeho nestatické datové členy a základní třídy musí být literálové typy a není volatilní.

## <a name="see-also"></a>Viz také

[Základní pojmy](../cpp/basic-concepts-cpp.md)
