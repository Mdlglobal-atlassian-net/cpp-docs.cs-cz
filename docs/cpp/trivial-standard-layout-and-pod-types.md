---
title: Trivial, standard rozložení, POD a typy literálu | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.topic: language-reference
ms.assetid: 2b23a7be-9bad-49fc-8298-31a9a7c556b0
ms.openlocfilehash: 7a80db109df1d9aa25f471312a9ff7103b90df7b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32424848"
---
# <a name="trivial-standard-layout-pod-and-literal-types"></a>Trivial, standard rozložení, POD a typy literálu

Termín *rozložení* odkazuje na uspořádání členům v objektu třída, struktura nebo typu union ve paměti. V některých případech je dobře definovaný podle specifikace jazyka rozložení. Ale pokud třídě nebo struktuře obsahuje určitých funkcí jazyka C++ jako virtuální základní třídy, virtuální funkce, členy pomocí řízení přístupu na jiný, kompilátor je bezplatná vybrat rozložení. Tento rozložení se mohou lišit v závislosti na tom, jaké optimalizace se provádí a v mnoha případech nemusí objektu i zabírají souvislý oblast paměti. Například pokud třída má virtuální funkce, všechny instance této třídy může sdílet tabulku jedné virtuální funkce. Tyto typy jsou samozřejmě velmi užitečné, ale mají omezení. Protože není definován rozložení nelze předat programy, které jsou napsané v jiných jazycích, například C, a protože ty můžou být nesouvislé jejich nelze kopírovat spolehlivě s funkcí Rychlé nízké úrovně, jako `memcopy` nebo serializovat přes síť.

 Kompilátory a také C++ – programy a metaprograms do důvod k vhodnosti pro typ pro operace, které závisí na konkrétní paměti rozložení povolit, C ++ 14 zavedená jednoduché tříd a struktur tří kategorií: *trivial*, *standard rozložení*, a *POD* nebo prostý stará Data. Standardní knihovna obsahuje šablony funkce `is_trivial<T>`, `is_standard_layout<T>` a `is_pod<T>` určující, zda se daný typ patří do dané kategorie.

## <a name="trivial-types"></a>Trivial typy

 Pokud třídě nebo struktuře v jazyce C++ má zadaná kompilátoru nebo explicitně uvedena speciální členské funkce, pak je trivial typu. Zabírá oblasti souvislé paměti. Může mít členy s jinou přístup ke specifikátorům. V jazyce C++ kompilátor může vybrat, jak k uspořádání členů v této situaci. Proto můžete memcopy tyto objekty, ale nemůžete spotřebovat spolehlivě je z programu C. Trivial typu t. můžete zkopírovat do pole char nebo unsigned char a bezpečně zkopírovat zpět do proměnné T. Všimněte si, že se z důvodu požadavky na zarovnání, může být bajtů odsazení mezi členy typu.

 Trivial typy mít trivial výchozí konstruktor, trivial kopírovacího konstruktoru, operátor přiřazení trivial kopírování, trivial destruktor. V každém případě *trivial* znamená konstruktor nebo operátor nebo destruktor není zadaný uživatelem a patří do třídy, která má

- žádné virtuální funkce nebo základní virtuální třídy

- žádné základní třídy s odpovídající konstruktor nebo operátor nebo destruktor

- žádné datové členy typu třídy s odpovídající konstruktor nebo operátor nebo destruktor

Následující příklady ukazují trivial typy. V Trivial2 přítomnost `Trivial2(int a, int b)` konstruktor vyžaduje zadání výchozí konstruktor. Pro typ pro kvalifikaci jako trivial musí explicitně výchozí tento konstruktor.

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

## <a name="standard-layout-types"></a>Rozložení Standardní typy

 Když třídě nebo struktuře neobsahuje určitých funkcí jazyka C++, jako je například virtuální funkce, které nebyly nalezeny v jazyce C a mít všichni členové stejné řízení přístupu, je typu standard rozložení. To bude možné memcopy a rozložení je dostatečně definované, mohou být využívány službou programy C. Typy Standard rozložení může mít uživatelem definované speciální členské funkce. Standardní rozložení typy kromě toho mají tyto charakteristiky:

- žádné virtuální funkce nebo základní virtuální třídy

- Všichni členové nestatické dat mít stejné řízení přístupu

- Standardní rozložení se všichni její členové nestatické typu třídy

- všechny základní třídy jsou standardní rozložení

- nemá žádné základní třídy stejného typu jako první člen nestatické data.

- splňuje jednu z těchto podmínek:

  - žádné nestatické datový člen v většinou odvozených tříd a více než jedné základní třídu s nestatické datových členů, nebo

  - nemá žádné základní třídy s nestatické datové členy

Následující kód ukazuje Příkladem typu standard rozložení:

```cpp
struct SL
{
   // All members have same access:
   int i;
   int j;
   SL(int a, int b) : i(a), j(b) {} // User-defined constructor OK
};

```

 Požadavky na posledních dvou lze případně lépe ukázat pomocí kódu. V následujícím příkladu, i když základní je standard rozložení `Derived` není standardní rozložení, protože it i (Většina odvozených tříd) a `Base` mít data nestatické členy:

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

 V tomto příkladu `Derived` je standard rozložení protože `Base` nemá žádné členy nestatické dat:

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

 Odvozené by také standardní rozložení Pokud `Base` měl datových členů a `Derived` měl pouze členské funkce.

## <a name="pod-types"></a>POD typy

 Když třídě nebo struktuře trivial i standardní rozložení, je typu POD (prostý stará Data). Proto je souvislé paměti rozložení POD typy a každý člen má adresu vyšší než člena, který byl deklarován před, tak, aby bytech zkopíruje a binární vstupně-výstupních operací lze provést na tyto typy.  Skalární typy, jako je například int jsou také POD typy. POD typy, které jsou třídy může mít pouze POD typy jako nestatické datových členů.

## <a name="example"></a>Příklad

Následující příklad ukazuje rozdíly mezi trivial, standard rozložení a POD typy:

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

Typ literálu je jedním jejichž uspořádání se dá určit v době kompilace. Tady jsou typy literálu:

- void
- skalární typy
- odkazy
- Pole void Skalární typy nebo naopak odkazuje na
- Třída, která má trivial destruktor a jeden nebo více constexpr konstruktory, které nejsou přesuňte nebo zkopírujte konstruktory. Kromě toho všechny její členy nestatické dat a základní třídy musí být typy literálu a není volatile.

## <a name="see-also"></a>Viz také

 [Základní koncepty](../cpp/basic-concepts-cpp.md)