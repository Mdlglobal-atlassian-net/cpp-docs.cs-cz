---
title: Triviální, typy literálu, standardního rozložení a POD | Dokumentace Microsoftu
ms.custom: ''
ms.date: 04/05/2018
ms.topic: language-reference
ms.assetid: 2b23a7be-9bad-49fc-8298-31a9a7c556b0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 824beed4c49556f564ff933575d1bbd0d844e2d7
ms.sourcegitcommit: 7f3df9ff0310a4716b8136ca20deba699ca86c6c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2018
ms.locfileid: "42465779"
---
# <a name="trivial-standard-layout-pod-and-literal-types"></a>Triviální, standardního rozložení, POD a typy literálu

Termín *rozložení* odkazuje na tom, jak členům v objektu typu třídy, struktury nebo sjednocení jsou uspořádáni v paměti. V některých případech je dobře definovaných ve specifikaci jazyka rozložení. Ale když třída nebo struktura obsahuje určitých funkcí jazyka C++, jako jsou virtuální základní třídy, virtuální funkce, členy s různá řízení přístupu, pak kompilátoru je umožněno vybrat rozložení. Toto rozložení se mohou lišit v závislosti na tom, jaké optimalizace provádění a v mnoha případech nemusí objekt i zabírat souvislých oblasti paměti. Například pokud třída má virtuální funkce, všechny instance této třídy může sdílet tabulku jedné virtuální funkce. Tyto typy jsou samozřejmě velmi užitečné, ale mají omezení. Vzhledem k tomu, že není definováno rozložení nejde jim předat programy napsané v jiných jazycích, jako je C, a protože ty můžou být nesouvislé, nelze zkopírovat spolehlivě pomocí funkce rychle nízké úrovně, jako `memcopy` nebo serializovali přes síť.

 Umožňuje kompilátory stejně jako programy v jazyce C++ a metaprograms argumentovat o vhodnosti daného typu pro operace, které jsou závislé na rozložení konkrétní paměťové zavedené C ++ 14 tři kategorie jednoduché třídy a struktury: *triviální*, *standardního rozložení*, a *POD* nebo obyčejná stará Data. Standardní knihovna obsahuje šablony funkcí `is_trivial<T>`, `is_standard_layout<T>` a `is_pod<T>` určující, zda daného typu patří k dané kategorie.

## <a name="trivial-types"></a>Triviální typy

 Když třídy nebo struktury v jazyce C++ má zadaná kompilátoru nebo explicitně nastavena jako výchozí speciálních členských funkcí, pak se o typ jednoduchého dotazu. Zabírá oblasti souvislé paměti. Může mít členy s jinou přístup ke specifikátorům. V jazyce C++ kompilátoru je umožněno vybrat způsob řazení členů v této situaci. Proto můžete memcopy tyto objekty ale nebudete moci spotřebovat spolehlivě je z jazyka C programu. Triviální typu T můžete zkopírovat do pole char nebo unsigned char a bezpečně zkopírovat zpět do proměnné T. Všimněte si, že z důvodu požadavků na přiřazení, může být bajtů odsazení mezi členy typu.

 Triviální typy mít triviální výchozí konstruktor, triviální kopírovací konstuktor, triviální kopírovacího operátoru přiřazení a triviální destruktor. V obou případech *triviální* znamená, že konstruktor nebo operátor/destruktor není uživatelem zadaný a že patří do třídy, která má

- žádné virtuální funkce nebo virtuální základní třídy

- žádné základní třídy s netriviálními odpovídající konstruktor nebo operátor/destruktorem

- žádné datové členy typu třídy s netriviálními odpovídající konstruktor nebo operátor/destruktorem

Následující příklady ukazují triviální typy. V Trivial2 přítomnost `Trivial2(int a, int b)` konstruktor vyžaduje, že zadáte výchozí konstruktor. Pro typ, který má kvalifikovat jako triviální musí explicitně výchozí tento konstruktor.

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

## <a name="standard-layout-types"></a>Typy standardního rozložení

 Když třídy nebo struktury neobsahuje určitých funkcí jazyka C++, jako je například virtuální funkce, což není k dispozici v jazyce C a všichni členové mají stejné řízení přístupu, je typ standardního rozložení. Je možné memcopy a rozložení je dostatečně definován, že mohou být spotřebovány aplikacemi C. Typy standardního rozložení mohou mít uživatelem definované speciálních členských funkcí. Typy standardního rozložení kromě toho mají tyto charakteristiky:

- žádné virtuální funkce nebo virtuální základní třídy

- všechny nestatické datové členy mají stejné řízení přístupu

- všechny nestatické členy typu třídy jsou standardního rozložení

- všechny základní třídy jsou standardního rozložení

- nemá žádné základní třídy stejného typu jako první nestatický datový člen.

- splňuje jedno z těchto podmínek:

  - žádné nestatický datový člen třídy nejvíce odvozenému a více než jedné základní třídy s nestatických datových členů, nebo

  - nemá žádné základní třídy s nestatických datových členů

Následující kód ukazuje příklad typu standardního rozložení:

```cpp
struct SL
{
   // All members have same access:
   int i;
   int j;
   SL(int a, int b) : i(a), j(b) {} // User-defined constructor OK
};
```

 Poslední dva požadavky lze případně lépe ukázat s kódem. V následujícím příkladu, i když Base je standardního rozložení, `Derived` není standardní rozložení, protože obě it (nejvíce odvozená třída) a `Base` mají nestatické datové členy:

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

 V tomto příkladu `Derived` je standardního rozložení protože `Base` nemá žádné nestatické datové členy:

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

 Odvozené by také standardního rozložení Pokud `Base` měl datové členy a `Derived` měli jenom členské funkce.

## <a name="pod-types"></a>Typy POD

 Třídy nebo struktury je jednoduché a standardního rozložení, je typ POD (Plain Old Data). Je rozložení paměti stejné typy POD se proto souvislých a každý člen má adresu vyšší než člena, který byl deklarován dříve, než se, aby bytech zkopíruje a binární vstupně-výstupní operace lze provést u těchto typů.  Skalární typy, například int jsou také typy POD. Typy POD, které jsou třídy může mít pouze typy POD jako nestatické datové členy.

## <a name="example"></a>Příklad

Následující příklad ukazuje rozdíly mezi triviální, standardního rozložení a typy POD:

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

## <a name="literal_types"></a> Typy literálu

Typ literálu je jedním jehož rozložení se dá určit v době kompilace. Toto jsou typy literálu:

- void
- skalární typy
- odkazy
- Pole typu void, Skalární typy nebo naopak odkazuje na
- Třída, která má destruktor triviální a jeden nebo více constexpr konstruktorů, které nejsou přesuňte nebo zkopírujte konstruktory. Kromě toho všechny nestatické datové členy a základních tříd musí být typy literálu a není typu volatile.

## <a name="see-also"></a>Viz také:
 [Základní koncepty](../cpp/basic-concepts-cpp.md)