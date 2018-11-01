---
title: vector (STL/CLR)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cliext::vector
- cliext::operator!=
- cliext::operator<
- cliext::operator<=
- cliext::operator==
- cliext::operator>
- cliext::operator>=
- cliext::vector::assign
- cliext::vector::at
- cliext::vector::back
- cliext::vector::back_item
- cliext::vector::begin
- cliext::vector::capacity
- cliext::vector::clear
- cliext::vector::const_iterator
- cliext::vector::const_reference
- cliext::vector::const_reverse_iterator
- cliext::vector::difference_type
- cliext::vector::empty
- cliext::vector::end
- cliext::vector::erase
- cliext::vector::front
- cliext::vector::front_item
- cliext::vector::generic_container
- cliext::vector::generic_iterator
- cliext::vector::generic_reverse_iterator
- cliext::vector::generic_value
- cliext::vector::insert
- cliext::vector::iterator
- cliext::vector::operator=
- cliext::vector::operator
- cliext::vector::pop_back
- cliext::vector::push_back
- cliext::vector::rbegin
- cliext::vector::reference
- cliext::vector::rend
- cliext::vector::reserve
- cliext::vector::resize
- cliext::vector::reverse_iterator
- cliext::vector::size
- cliext::vector::size_type
- cliext::vector::swap
- cliext::vector::to_array
- cliext::vector::value_type
- cliext::vector::vector
helpviewer_keywords:
- vector class [STL/CLR]
- <cliext/vector> header [STL/CLR]
- <vector> header [STL/CLR]
- operator!= member [STL/CLR]
- operator< member [STL/CLR]
- operator<= member [STL/CLR]
- operator== member [STL/CLR]
- operator> (vector) member [STL/CLR]
- operator>= member [STL/CLR]
- assign member [STL/CLR]
- at member [STL/CLR]
- back member [STL/CLR]
- back_item member [STL/CLR]
- begin member [STL/CLR]
- capacity member [STL/CLR]
- clear member [STL/CLR]
- const_iterator member [STL/CLR]
- const_reference member [STL/CLR]
- const_reverse_iterator member [STL/CLR]
- difference_type member [STL/CLR]
- empty member [STL/CLR]
- end member [STL/CLR]
- erase member [STL/CLR]
- front member [STL/CLR]
- front_item member [STL/CLR]
- generic_container member [STL/CLR]
- generic_iterator member [STL/CLR]
- generic_reverse_iterator member [STL/CLR]
- generic_value member [STL/CLR]
- insert member [STL/CLR]
- iterator member [STL/CLR]
- operator= member [STL/CLR]
- operator member [STL/CLR]
- pop_back member [STL/CLR]
- push_back member [STL/CLR]
- rbegin member [STL/CLR]
- reference member [STL/CLR]
- rend member [STL/CLR]
- reserve member [STL/CLR]
- resize member [STL/CLR]
- reverse_iterator member [STL/CLR]
- size member [STL/CLR]
- size_type member [STL/CLR]
- swap member [STL/CLR]
- to_array member [STL/CLR]
- value_type member [STL/CLR]
- vector member [STL/CLR]
ms.assetid: f90060d5-097a-4e9d-9a26-a634b5b9c6c2
ms.openlocfilehash: 09a0919cd47937960736c6cccf31343c5e12087d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50640710"
---
# <a name="vector-stlclr"></a>vector (STL/CLR)

Třída šablony popisuje objekt, který řídí různé délky sekvence elementů, s náhodným přístupem. Použití kontejneru `vector` spravovat řadu prvků, jako souvislý blok úložiště. Blok je implementovaný jako pole, které roste na požádání.

V popisu níže `GValue` je stejný jako *hodnotu* Pokud je typ odkazu, v takovém případě je `Value^`.

## <a name="syntax"></a>Syntaxe

```cpp
template<typename Value>
    ref class vector
        :   public
        System::ICloneable,
        System::Collections::IEnumerable,
        System::Collections::ICollection,
        System::Collections::Generic::IEnumerable<GValue>,
        System::Collections::Generic::ICollection<GValue>,
        System::Collections::Generic::IList<GValue>,
        Microsoft::VisualC::StlClr::IVector<GValue>
    { ..... };
```

### <a name="parameters"></a>Parametry

*Hodnota*<br/>
Typ elementu v řízené sekvenci

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<cliext – / vektoru >

**Namespace:** cliext –

## <a name="declarations"></a>Deklarace

|Definice typu|Popis|
|---------------------|-----------------|
|[vector::const_iterator (STL/CLR)](#const_iterator)|Typ konstantního iterátoru řízené sekvence|
|[vector::const_reference (STL/CLR)](#const_reference)|Typ konstantního odkazu na prvek|
|[vector::const_reverse_iterator (STL/CLR)](#const_reverse_iterator)|Typ konstantního zpětného iterátoru řízené sekvence.|
|[vector::difference_type (STL/CLR)](#difference_type)|Typ vzdálenosti se znaménkem mezi dvěma prvky|
|[vector::generic_container (STL/CLR)](#generic_container)|Typ obecné rozhraní pro kontejner.|
|[vector::generic_iterator (STL/CLR)](#generic_iterator)|Typ iterátoru pro obecné rozhraní pro kontejner.|
|[vector::generic_reverse_iterator (STL/CLR)](#generic_reverse_iterator)|Typ "reverse iterator" pro obecné rozhraní pro kontejner.|
|[vector::generic_value (STL/CLR)](#generic_value)|Typ elementu pro obecné rozhraní pro kontejner.|
|[vector::iterator (STL/CLR)](#iterator)|Typ iterátoru řízené sekvence|
|[vector::reference (STL/CLR)](#reference)|Typ odkazu na prvek|
|[vector::reverse_iterator (STL/CLR)](#reverse_iterator)|Typ "reverse iterator" pro řízenou sekvenci.|
|[vector::size_type (STL/CLR)](#size_type)|Typ vzdálenosti se znaménkem mezi dvěma prvky|
|[vector::value_type (STL/CLR)](#value_type)|Typ prvku|

|Členská funkce|Popis|
|---------------------|-----------------|
|[vector::assign (STL/CLR)](#assign)|Nahradí všechny elementy.|
|[vector::at (STL/CLR)](#at)|Přistupuje k element na určené pozici.|
|[vector::back (STL/CLR)](#back)|Přistupuje k poslední prvek.|
|[vector::begin (STL/CLR)](#begin)|Určuje začátek řízené sekvence.|
|[vector::capacity (STL/CLR)](#capacity)|Oznamuje velikost přidělené úložiště pro kontejner.|
|[vector::clear (STL/CLR)](#clear)|Odebere všechny prvky.|
|[vector::empty (STL/CLR)](#empty)|Zkouší, zda nejsou přítomny žádné prvky.|
|[vector::end (STL/CLR)](#end)|Určuje konec řízené sekvence.|
|[vector::erase (STL/CLR)](#erase)|Odebere prvky v určených pozicích.|
|[vector::front (STL/CLR)](#front)|Přistupuje k první prvek.|
|[vector::insert (STL/CLR)](#insert)|Přidá prvky na zadané pozici.|
|[vector::pop_back (STL/CLR)](#pop_back)|Odstraní poslední prvek.|
|[vector::push_back (STL/CLR)](#push_back)|Přidá nový poslední prvek.|
|[vector::rbegin (STL/CLR)](#rbegin)|Určuje začátek řízené obrácené sekvenci.|
|[vector::rend (STL/CLR)](#rend)|Určuje konec řízené obrácené sekvenci.|
|[vector::reserve (STL/CLR)](#reserve)|Zajišťuje minimální růstu kapacity pro kontejner.|
|[vector::resize (STL/CLR)](#resize)|Počet prvků, které se změní.|
|[vector::size (STL/CLR)](#size)|Spočítá počet prvků.|
|[vector::swap (STL/CLR)](#swap)|Zamění obsah dvou kontejnerů.|
|[vector::to_array (STL/CLR)](#to_array)|Zkopíruje do nového pole řízené sekvence.|
|[vector::vector (STL/CLR)](#vector)|Sestaví objekt kontejneru.|

|Vlastnost|Popis|
|--------------|-----------------|
|[vector::back_item (STL/CLR)](#back_item)|Přistupuje k poslední prvek.|
|[vector::front_item (STL/CLR)](#front_item)|Přistupuje k první prvek.|

|Operátor|Popis|
|--------------|-----------------|
|[vector::operator= (STL/CLR)](#op_as)|Nahradí řízené sekvence.|
|[vector::operator(STL/CLR)](#op)|Přistupuje k element na určené pozici.|
|[operator!= (vector) (STL/CLR)](#op_neq)|Určuje, zda `vector` není roven jinému objektu `vector` objektu.|
|[operator< (vector) (STL/CLR)](#op_lt)|Určuje, zda `vector` je menší než jiný objekt `vector` objektu.|
|[operator<= (vector) (STL/CLR)](#op_lteq)|Určuje, zda `vector` objekt je menší nebo rovna jiné `vector` objektu.|
|[operator== (vector) (STL/CLR)](#op_eq)|Určuje, zda `vector` je roven jinému objektu `vector` objektu.|
|[operator> (vector) (STL/CLR)](#op_gt)|Určuje, zda `vector` je větší než jiný objekt `vector` objektu.|
|[operator>= (vector) (STL/CLR)](#op_gteq)|Určuje, zda `vector` objekt je větší než nebo roven jinému `vector` objektu.|

## <a name="interfaces"></a>Rozhraní

|Rozhraní|Popis|
|---------------|-----------------|
|<xref:System.ICloneable>|Duplicitní objektu.|
|<xref:System.Collections.IEnumerable>|Pořadí mezi prvky.|
|<xref:System.Collections.ICollection>|Údržba skupiny prvků.|
|<xref:System.Collections.Generic.IEnumerable%601>|Pořadí pomocí zadané elementy.|
|<xref:System.Collections.Generic.ICollection%601>|Údržba skupiny zadané elementy.|
|<xref:System.Collections.Generic.IList%601>|Údržba seřazený skupiny zadané elementy.|
|IVector < hodnota\>|Udržujte obecný kontejneru.|

## <a name="remarks"></a>Poznámky

Objekt přiděluje a uvolňuje úložiště pro sekvenci řídí, prostřednictvím uloženého pole *hodnotu* elementy, které roste na požádání. Vyvolá se v takovým způsobem, že náklady na přidání nového elementu je amortizovaném konstantním času růstu. Jinými slovy náklady na přidání prvků na konci nezvyšuje, v průměru jako délku větší řízené sekvence získá. Proto vektor je vhodným kandidátem pro základní kontejner pro třídu šablony [zásobníku (STL/CLR)](../dotnet/stack-stl-clr.md).

A `vector` iterátory s náhodným přístupem podporuje, což znamená, že mohou odkazovat na prvek přímo zadané pozici číselné počítáno od nuly pro první prvek (popředí) na `size() - 1` pro poslední prvek (zpět). To také znamená, že vektor je vhodným kandidátem pro základní kontejner pro třídu šablony [priority_queue – (STL/CLR)](../dotnet/priority-queue-stl-clr.md).

Iterátor vektoru uloží popisovač pro jeho přidružené vektorový objekt, spolu s zkreslení elementu, které určí. Iterátory lze použít pouze objekty, které přiřazeným kontejnerem. Posun prvku vektoru je stejný jako jeho pozice.

Vložení nebo mazání prvků můžete změnit hodnotu prvku uložená na dané pozici, takže můžete také změnit hodnotu určeném iterátor. (Kontejner může být nutné zkopírovat elementy nahoru nebo dolů k vytvoření hole před vložení nebo tak, aby vyplnil díry po vymazání.) Nicméně iterátor vektoru zůstává v platnosti tak dlouho, dokud je její posun v rozsahu `[0, size()]`. Kromě toho vám zůstane platný iterátoru přesměrovat – slouží k přístupu nebo změnit hodnotu prvku jmenuje--tak dlouho, dokud jeho posun není shodný s `size()`.

Smazání nebo odstranění prvku volá destruktor pro jeho uložené hodnotě. Zničení kontejneru vymaže všechny prvky. Kontejner, jehož typ prvku je třídy ref class tak, zajišťuje, že žádné elementy něj kontejneru. Upozorňujeme však, že kontejner zpracovává nezničí jeho prvků.

## <a name="members"></a>Členové

## <a name="assign"></a> Vector::Assign (STL/CLR)

Nahradí všechny elementy.

### <a name="syntax"></a>Syntaxe

```cpp
void assign(size_type count, value_type val);
template<typename InIt>
    void assign(InIt first, InIt last);
void assign(System::Collections::Generic::IEnumerable<Value>^ right);
```

#### <a name="parameters"></a>Parametry

*Počet*<br/>
Počet elementů k vložení.

*první*<br/>
Začátek rozsahu pro vložení.

*poslední*<br/>
Konec rozsahu pro vložení.

*doprava*<br/>
Výčet pro vložení.

*Val*<br/>
Hodnota elementu, který chcete vložit.

### <a name="remarks"></a>Poznámky

První členská funkce nahradí řízené sekvence opakování *počet* prvků hodnoty *val*. Použijete ji k vyplnilo kontejner s prvky všechny mají stejnou hodnotu.

Pokud `InIt` je celočíselný typ, druhá členská funkce se chová stejně jako `assign((size_type)first, (value_type)last)`. V opačném případě ji nahradí řízené sekvence sekvence [`first`, `last`). Použijete ji provést řízené sekvence kopii jiné pořadí.

Třetí členská funkce nahradí řízené sekvence pořadí určeném enumerátor *správné*. Použijete ji k vytvořte kopii sekvence popsal enumerátor řízené sekvence.

### <a name="example"></a>Příklad

```cpp
// cliext_vector_assign.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// assign a repetition of values
    cliext::vector<wchar_t> c2;
    c2.assign(6, L'x');
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign an iterator range
    c2.assign(c1.begin(), c1.end() - 1);
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign an enumeration
    c2.assign(   // NOTE: cast is not needed
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c1);
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
x x x x x x
a b
a b c
```

## <a name="at"></a> Vector::AT (STL/CLR)

Přistupuje k element na určené pozici.

### <a name="syntax"></a>Syntaxe

```cpp
reference at(size_type pos);
```

#### <a name="parameters"></a>Parametry

*POS*<br/>
Pozice prvku přístup.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí odkaz na prvek řízené sekvence na pozici *pos*. Můžete použít ke čtení nebo zápisu elementu, jehož pozice znáte.

### <a name="example"></a>Příklad

```cpp
// cliext_vector_at.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c" using at
    for (int i = 0; i < c1.size(); ++i)
        System::Console::Write("{0} ", c1.at(i));
    System::Console::WriteLine();

// change an entry and redisplay
    c1.at(1) = L'x';
    for (int i = 0; i < c1.size(); ++i)
        System::Console::Write("{0} ", c1[i]);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a x c
```

## <a name="back"></a> Vector::back (STL/CLR)

Přistupuje k poslední prvek.

### <a name="syntax"></a>Syntaxe

```cpp
reference back();
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí odkaz na poslední prvek řízené sekvence, která musí být neprázdný. Použijete ho pro přístup k posledního prvku, když víte, že existuje.

### <a name="example"></a>Příklad

```cpp
// cliext_vector_back.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// inspect last item
    System::Console::WriteLine("back() = {0}", c1.back());

// alter last item and reinspect
    c1.back() = L'x';
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
back() = c
a b x
```

## <a name="back_item"></a> Vector::back_item (STL/CLR)

Přistupuje k poslední prvek.

### <a name="syntax"></a>Syntaxe

```cpp
property value_type back_item;
```

### <a name="remarks"></a>Poznámky

Vlastnost má přístup k poslední prvek řízené sekvence, která musí být neprázdný. Můžete použít ke čtení nebo zápisu posledního prvku, když víte, že existuje.

### <a name="example"></a>Příklad

```cpp
// cliext_vector_back_item.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// inspect last item
    System::Console::WriteLine("back_item = {0}", c1.back_item);

// alter last item and reinspect
    c1.back_item = L'x';
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
back_item = c
a b x
```

## <a name="begin"></a> Vector::begin (STL/CLR)

Určuje začátek řízené sekvence.

### <a name="syntax"></a>Syntaxe

```cpp
iterator begin();
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí iterátor náhodného přístupu, který určuje první prvek řízenou sekvenci nebo přesně za konec k prázdné sekvenci. Můžete ji použít k získání iterátor, který určuje `current` začátek řízené sekvence, ale jeho stav můžete změnit, pokud se změní délka řízené sekvence.

### <a name="example"></a>Příklad

```cpp
// cliext_vector_begin.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// inspect first two items
    cliext::vector<wchar_t>::iterator it = c1.begin();
    System::Console::WriteLine("*begin() = {0}", *it);
    System::Console::WriteLine("*++begin() = {0}", *++it);

// alter first two items and reinspect
    *--it = L'x';
    *++it = L'y';
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
*begin() = a
*++begin() = b
x y c
```

## <a name="capacity"></a> Vector::Capacity (STL/CLR)

Oznamuje velikost přidělené úložiště pro kontejner.

### <a name="syntax"></a>Syntaxe

```cpp
size_type capacity();
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí úložiště aktuálně přidělené pro uložení řízené sekvence přinejmenším stejně velká jako hodnota [vector::size (STL/CLR)](../dotnet/vector-size-stl-clr.md)`()`. Použijete ji k určení, kolik kontejneru můžou růst předtím, než ji musíte znovu přidělte úložiště řízené sekvence.

### <a name="example"></a>Příklad

```cpp
// cliext_vector_capacity.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display initial contents " a b c"
    for (int i = 0; i < c1.size(); ++i)
        System::Console::Write("{0} ", c1.at(i));
    System::Console::WriteLine();

// increase capacity
    cliext::vector<wchar_t>::size_type cap = c1.capacity();
    System::Console::WriteLine("capacity() = {0}, ok = {1}",
        cap, c1.size() <= cap);
    c1.reserve(cap + 5);
    System::Console::WriteLine("capacity() = {0}, ok = {1}",
        c1.capacity(), cap + 5 <= c1.capacity());
    return (0);
    }
```

```Output
a b c
capacity() = 4, ok = True
capacity() = 9, ok = True
```

## <a name="clear"></a> Vector::clear (STL/CLR)

Odebere všechny prvky.

### <a name="syntax"></a>Syntaxe

```cpp
void clear();
```

### <a name="remarks"></a>Poznámky

Členská funkce efektivně volá [vector::erase (STL/CLR)](../dotnet/vector-erase-stl-clr.md) `(` [vector::begin (STL/CLR)](../dotnet/vector-begin-stl-clr.md) `(),` [vector::end (STL/CLR)](../dotnet/vector-end-stl-clr.md) `())`. Použijete ji k zajištění, že je prázdná řízené sekvence.

### <a name="example"></a>Příklad

```cpp
// cliext_vector_clear.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// clear the container and reinspect
    c1.clear();
    System::Console::WriteLine("size() = {0}", c1.size());

// add elements and clear again
    c1.push_back(L'a');
    c1.push_back(L'b');

    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    c1.clear();
    System::Console::WriteLine("size() = {0}", c1.size());
    return (0);
    }
```

```Output
a b c
size() = 0
a b
size() = 0
```

## <a name="const_iterator"></a> Vector::const_iterator (STL/CLR)

Typ konstantního iterátoru řízené sekvence

### <a name="syntax"></a>Syntaxe

```cpp
typedef T2 const_iterator;
```

### <a name="remarks"></a>Poznámky

Typ popisuje objekt neurčeného typu `T2` , který může sloužit jako konstantní iterátor s náhodným přístupem řízené sekvence.

### <a name="example"></a>Příklad

```cpp
// cliext_vector_const_iterator.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c"
    cliext::vector<wchar_t>::const_iterator cit = c1.begin();
    for (; cit != c1.end(); ++cit)
        System::Console::Write("{0} ", *cit);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="const_reference"></a> Vector::const_reference (STL/CLR)

Typ konstantního odkazu na prvek

### <a name="syntax"></a>Syntaxe

```cpp
typedef value_type% const_reference;
```

### <a name="remarks"></a>Poznámky

Typ, který popisuje konstantní odkaz na element.

### <a name="example"></a>Příklad

```cpp
// cliext_vector_const_reference.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display initial contents " a b c"
    cliext::vector<wchar_t>::const_iterator cit = c1.begin();
    for (; cit != c1.end(); ++cit)
        {   // get a const reference to an element
        cliext::vector<wchar_t>::const_reference cref = *cit;
        System::Console::Write("{0} ", cref);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="const_reverse_iterator"></a> Vector::const_reverse_iterator (STL/CLR)

Typ konstantního zpětného iterátoru řízené sekvence...

### <a name="syntax"></a>Syntaxe

```cpp
typedef T4 const_reverse_iterator;
```

### <a name="remarks"></a>Poznámky

Typ popisuje objekt neurčeného typu `T4` , který může sloužit jako konstantní zpětného iterátoru řízené sekvence.

### <a name="example"></a>Příklad

```cpp
// cliext_vector_const_reverse_iterator.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c" reversed
    cliext::vector<wchar_t>::const_reverse_iterator crit = c1.rbegin();
    cliext::vector<wchar_t>::const_reverse_iterator crend = c1.rend();
    for (; crit != crend; ++crit)
        System::Console::Write("{0} ", *crit);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c b a
```

## <a name="difference_type"></a> Vector::difference_type (STL/CLR)

Typ vzdálenosti se znaménkem mezi dvěma prvky.

### <a name="syntax"></a>Syntaxe

```cpp
typedef int difference_type;
```

### <a name="remarks"></a>Poznámky

Typ, který popisuje počet podepsaný prvků.

### <a name="example"></a>Příklad

```cpp
// cliext_vector_difference_type.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// compute positive difference
    cliext::vector<wchar_t>::difference_type diff = 0;
    for (cliext::vector<wchar_t>::iterator it = c1.begin();
        it != c1.end(); ++it) ++diff;
    System::Console::WriteLine("end()-begin() = {0}", diff);

// compute negative difference
    diff = 0;
    for (cliext::vector<wchar_t>::iterator it = c1.end();
        it != c1.begin(); --it) --diff;
    System::Console::WriteLine("begin()-end() = {0}", diff);
    return (0);
    }
```

```Output
a b c
end()-begin() = 3
begin()-end() = -3
```

## <a name="empty"></a> Vector::Empty (STL/CLR)

Zkouší, zda nejsou přítomny žádné prvky.

### <a name="syntax"></a>Syntaxe

```cpp
bool empty();
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí hodnotu true pro prázdnou řízenou sekvenci. Je ekvivalentní [vector::size (STL/CLR)](../dotnet/vector-size-stl-clr.md)`() == 0`. Použijete ji k ověření, zda je prázdný vektor.

### <a name="example"></a>Příklad

```cpp
// cliext_vector_empty.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    System::Console::WriteLine("size() = {0}", c1.size());
    System::Console::WriteLine("empty() = {0}", c1.empty());

// clear the container and reinspect
    c1.clear();
    System::Console::WriteLine("size() = {0}", c1.size());
    System::Console::WriteLine("empty() = {0}", c1.empty());
    return (0);
    }
```

```Output
a b c
size() = 3
empty() = False
size() = 0
empty() = True
```

## <a name="end"></a> Vector::end (STL/CLR)

Určuje konec řízené sekvence.

### <a name="syntax"></a>Syntaxe

```cpp
iterator end();
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí iterátor náhodného přístupu, na kterou odkazuje přesně za konec řízené sekvence. Můžete ji použít k získání iterátor, který určuje `current` konec řízené sekvence, ale jeho stav můžete změnit, pokud se změní délka řízené sekvence.

### <a name="example"></a>Příklad

```cpp
// cliext_vector_end.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// inspect last two items
    cliext::vector<wchar_t>::iterator it = c1.end();
    --it;
    System::Console::WriteLine("*-- --end() = {0}", *--it);
    System::Console::WriteLine("*--end() = {0}", *++it);

// alter first two items and reinspect
    *--it = L'x';
    *++it = L'y';
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
*-- --end() = b
*--end() = c
a x y
```

## <a name="erase"></a> Vector::Erase (STL/CLR)

Odebere prvky v určených pozicích.

### <a name="syntax"></a>Syntaxe

```cpp
iterator erase(iterator where);
iterator erase(iterator first, iterator last);
```

#### <a name="parameters"></a>Parametry

*první*<br/>
Začátek rozsahu vymazat.

*poslední*<br/>
Konec rozsahu vymazat.

*kde*<br/>
Element vymazat.

### <a name="remarks"></a>Poznámky

První členská funkce odstraní prvek řízené sekvence, na které odkazuje *kde*. Použijete ji k odebrání jeden element.

Druhá členská funkce odebere prvky řízené sekvence v rozsahu [`first`, `last`). Použijete ji k odebrání nula nebo více souvislých prvků.

Obě členské funkce vrátí iterátor, který určuje první prvek zbývající za všemi odstraněnými prvky, nebo [vector::end (STL/CLR)](../dotnet/vector-end-stl-clr.md) `()` Pokud žádný takový prvek neexistuje.

Při mazání prvků, je počet kopií prvku lineární v počtu prvků mezi koncem mazání a bližšího konci sekvence. (Při mazání jeden nebo více prvků na jednom konci pořadí, žádný element kopie nastat.)

### <a name="example"></a>Příklad

```cpp
// cliext_vector_erase.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// erase an element and reinspect
    System::Console::WriteLine("erase(begin()) = {0}",
        *c1.erase(c1.begin()));

// add elements and display " b c d e"
    c1.push_back(L'd');
    c1.push_back(L'e');
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// erase all but end
    cliext::vector<wchar_t>::iterator it = c1.end();
    System::Console::WriteLine("erase(begin(), end()-1) = {0}",
        *c1.erase(c1.begin(), --it));
    System::Console::WriteLine("size() = {0}", c1.size());
    return (0);
    }
```

```Output
a b c
erase(begin()) = b
b c d e
erase(begin(), end()-1) = e
size() = 1
```

## <a name="front"></a> Vector::front (STL/CLR)

Přistupuje k první prvek.

### <a name="syntax"></a>Syntaxe

```cpp
reference front();
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí odkaz na první prvek řízené sekvence, která musí být neprázdný. Můžete použít ke čtení nebo zápisu prvního prvku, když víte, že existuje.

### <a name="example"></a>Příklad

```cpp
// cliext_vector_front.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// inspect first item
    System::Console::WriteLine("front() = {0}", c1.front());

// alter first item and reinspect
    c1.front() = L'x';
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
front() = a
x b c
```

# <a name="front_item"></a> Vector::front_item (STL/CLR)
Přistupuje k první prvek.

### <a name="syntax"></a>Syntaxe

```cpp
property value_type front_item;
```

### <a name="remarks"></a>Poznámky

Vlastnost přistupuje k první prvek řízené sekvence, která musí být neprázdný. Můžete použít ke čtení nebo zápisu prvního prvku, když víte, že existuje.

### <a name="example"></a>Příklad

```cpp
// cliext_vector_front_item.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// inspect first item
    System::Console::WriteLine("front_item = {0}", c1.front_item);

// alter first item and reinspect
    c1.front_item = L'x';
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
front_item = a
x b c
```

# <a name="generic_container"></a> Vector::generic_container (STL/CLR)
Typ obecné rozhraní pro kontejner.

### <a name="syntax"></a>Syntaxe

```cpp
typedef Microsoft::VisualC::StlClr::
    IVector<generic_value>
    generic_container;
```

### <a name="remarks"></a>Poznámky

Typ, který popisuje obecné rozhraní pro tuto třídu šablony kontejneru.

### <a name="example"></a>Příklad

```cpp
// cliext_vector_generic_container.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct a generic container
    cliext::vector<wchar_t>::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// modify generic and display original
    gc1->insert(gc1->end(), L'd');
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// modify original and display generic
    c1.push_back(L'e');

    System::Collections::IEnumerator^ enum1 =
        gc1->GetEnumerator();
    while (enum1->MoveNext())
        System::Console::Write("{0} ", enum1->Current);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a b c
a b c d
a b c d e
```

## <a name="generic_iterator"></a> Vector::generic_iterator (STL/CLR)

Typ iterátoru pro použití s obecné rozhraní pro kontejner.

### <a name="syntax"></a>Syntaxe

```cpp
typedef Microsoft::VisualC::StlClr::Generic::
    ContainerRandomAccessIterator<generic_value>
    generic_iterator;
```

### <a name="remarks"></a>Poznámky

Typ, který popisuje obecný iterátoru, který jde použít s obecné rozhraní pro tuto třídu šablony kontejneru.

### <a name="example"></a>Příklad

```cpp
// cliext_vector_generic_iterator.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct a generic container
    cliext::vector<wchar_t>::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// modify generic and display original
    cliext::vector<wchar_t>::generic_iterator gcit = gc1->begin();
    cliext::vector<wchar_t>::generic_value gcval = *gcit;
    *++gcit = gcval;
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a b c
a a c
```

# <a name="generic_reverse_iterator"></a> Vector::generic_reverse_iterator (STL/CLR)
Typ "reverse iterator" pro použití s obecné rozhraní pro kontejner.

### <a name="syntax"></a>Syntaxe

```cpp
typedef Microsoft::VisualC::StlClr::Generic::
    ReverseRandomAccessIterator<generic_value> generic_reverse_iterator;
```

### <a name="remarks"></a>Poznámky

Typ, který popisuje obecný zpětný iterátor, který jde použít s obecné rozhraní pro tuto třídu šablony kontejneru.

### <a name="example"></a>Příklad

```cpp
// cliext_vector_generic_reverse_iterator.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct a generic container
    cliext::vector<wchar_t>::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// modify generic and display original
    cliext::vector<wchar_t>::generic_reverse_iterator gcit = gc1->rbegin();
    cliext::vector<wchar_t>::generic_value gcval = *gcit;
    *++gcit = gcval;
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a b c
a c c
```

## <a name="generic_value"></a> Vector::generic_value (STL/CLR)

Typ elementu pro použití s obecné rozhraní pro kontejner.

### <a name="syntax"></a>Syntaxe

```cpp
typedef GValue generic_value;
```

### <a name="remarks"></a>Poznámky

Typ, který popisuje objekt typu `GValue` hodnoty uložené elementu pro použití s obecné rozhraní pro tuto třídu šablony kontejneru, který popisuje.

### <a name="example"></a>Příklad

```cpp
// cliext_vector_generic_value.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct a generic container
    cliext::vector<wchar_t>::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// modify generic and display original
    cliext::vector<wchar_t>::generic_iterator gcit = gc1->begin();
    cliext::vector<wchar_t>::generic_value gcval = *gcit;
    *++gcit = gcval;
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a b c
a a c
```

## <a name="insert"></a> Vector::Insert (STL/CLR)

Přidá prvky na zadané pozici.

### <a name="syntax"></a>Syntaxe

```cpp
iterator insert(iterator where, value_type val);
void insert(iterator where, size_type count, value_type val);
template<typename InIt>
    void insert(iterator where, InIt first, InIt last);
void insert(iterator where,
    System::Collections::Generic::IEnumerable<Value>^ right);
```

#### <a name="parameters"></a>Parametry

*Počet*<br/>
Počet elementů k vložení.

*první*<br/>
Začátek rozsahu pro vložení.

*poslední*<br/>
Konec rozsahu pro vložení.

*doprava*<br/>
Výčet pro vložení.

*Val*<br/>
Hodnota elementu, který chcete vložit.

*kde*<br/>
Kde v kontejneru vložit před

### <a name="remarks"></a>Poznámky

Každý člen funkce vložení před element, na které odkazuje *kde* v řízené sekvenci sekvence určené zbývající operandy.

První členská funkce vloží prvek s hodnotou *val* a vrátí iterátor, který určuje nově vložený prvek. Použijete ji k vložení jediný prvek před místo, kde došlo ke shodě podle iterátor.

Druhá členská funkce vloží opakování *počet* prvků hodnoty *val*. Použijete ji k vložení nula nebo více souvislých prvků, které jsou všechny kopie stejnou hodnotu.

Pokud `InIt` je celočíselný typ, třetí členská funkce se chová stejně jako `insert(where, (size_type)first, (value_type)last)`. V opačném případě vloží sekvenci [`first`, `last`). Použijete ji k vložení nula nebo více souvislých prvků, které jsou kopírovány z jiné pořadí.

Čtvrtá členská funkce vloží pořadí určeném *správné*. Použijete ji k vložení pořadí popsal enumerátor.

Při vkládání jeden element, počet kopií prvku je lineární v počtu prvků mezi kurzoru a bližšího konci sekvence. (Při vkládání jeden nebo více prvků na jednom konci pořadí, žádný element kopie nastat.) Pokud `InIt` je vstupní iterátor, třetí členská funkce efektivně provede jednu vložení pro každý prvek v sekvenci. Jinak, při vkládání `N` prvky, počet kopií prvku je lineární `N` plus počet prvků mezi kurzoru a bližšího konci sekvence.

### <a name="example"></a>Příklad

```cpp
// cliext_vector_insert.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// insert a single value using iterator
    cliext::vector<wchar_t>::iterator it = c1.begin();
    System::Console::WriteLine("insert(begin()+1, L'x') = {0}",
        *c1.insert(++it, L'x'));
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// insert a repetition of values
    cliext::vector<wchar_t> c2;
    c2.insert(c2.begin(), 2, L'y');
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// insert an iterator range
    it = c1.end();
    c2.insert(c2.end(), c1.begin(), --it);
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// insert an enumeration
    c2.insert(c2.begin(),   // NOTE: cast is not needed
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c1);
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
insert(begin()+1, L'x') = x
a x b c
y y
y y a x b
a x b c y y a x b
```

## <a name="iterator"></a> Vector::iterator (STL/CLR)

Typ iterátoru řízené sekvence

### <a name="syntax"></a>Syntaxe

```cpp
typedef T1 iterator;
```

### <a name="remarks"></a>Poznámky

Typ popisuje objekt neurčeného typu `T1` , který může sloužit jako iterátor náhodného přístupu řízené sekvence.

### <a name="example"></a>Příklad

```cpp
// cliext_vector_iterator.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c"
    cliext::vector<wchar_t>::iterator it = c1.begin();
    for (; it != c1.end(); ++it)
        System::Console::Write("{0} ", *it);
    System::Console::WriteLine();

// alter first element and redisplay
    it = c1.begin();
    *it = L'x';
    for (; it != c1.end(); ++it)
        System::Console::Write("{0} ", *it);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
x b c
```

## <a name="op_as"></a> Vector::Operator = (STL/CLR)

Nahradí řízené sekvence.

### <a name="syntax"></a>Syntaxe

```cpp
vector<Value>% operator=(vector<Value>% right);
```

#### <a name="parameters"></a>Parametry

*doprava*<br/>
Kontejner pro kopírování.

### <a name="remarks"></a>Poznámky

Kopie členský operátor *správné* na objekt, vrátí `*this`. Můžete použít k nahraďte kopii řízené sekvence v řízené sekvenci *správné*.

### <a name="example"></a>Příklad

```cpp
// cliext_vector_operator_as.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    cliext::vector<wchar_t> c2;
    c2 = c1;
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a b c
```

## <a name="op"></a> Vector::Operator(STL/CLR)

Přistupuje k element na určené pozici.

### <a name="syntax"></a>Syntaxe

```cpp
reference operator[](size_type pos);
```

#### <a name="parameters"></a>Parametry

*POS*<br/>
Pozice prvku přístup.

### <a name="remarks"></a>Poznámky

Členský operátor vrátí prvek na pozici referene *pos*. Použít pro přístup k elementu, jehož pozice znáte.

### <a name="example"></a>Příklad

```cpp
// cliext_vector_operator_sub.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c" using subscripting
    for (int i = 0; i < c1.size(); ++i)
        System::Console::Write("{0} ", c1[i]);
    System::Console::WriteLine();

// change an entry and redisplay
    c1[1] = L'x';
    for (int i = 0; i < c1.size(); ++i)
        System::Console::Write("{0} ", c1[i]);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a x c
```

## <a name="pop_back"></a> Vector::pop_back (STL/CLR)

Odstraní poslední prvek.

### <a name="syntax"></a>Syntaxe

```cpp
void pop_back();
```

### <a name="remarks"></a>Poznámky

Členská funkce odstraní poslední prvek řízené sekvence, která musí být neprázdný. Použijte ke zkrácení vektoru jeden element na pozadí.

### <a name="example"></a>Příklad

```cpp
// cliext_vector_pop_back.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// pop an element and redisplay
    c1.pop_back();
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a b
```

## <a name="push_back"></a> Vector::push_back (STL/CLR)

Přidá nový poslední prvek.

### <a name="syntax"></a>Syntaxe

```cpp
void push_back(value_type val);
```

### <a name="remarks"></a>Poznámky

Členská funkce vloží prvek s hodnotou `val` na konci řízené sekvence. Použijete ji k připojení jiný prvek vektoru.

### <a name="example"></a>Příklad

```cpp
// cliext_vector_push_back.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="rbegin"></a> Vector::rbegin (STL/CLR)

Určuje začátek řízené obrácené sekvenci.

### <a name="syntax"></a>Syntaxe

```cpp
reverse_iterator rbegin();
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí zpětný iterátor, který určuje poslední prvek řízenou sekvenci nebo hned za začátku k prázdné sekvenci. Proto, označí `beginning` reverzní pořadí. Můžete ji použít k získání iterátor, který určuje `current` začátek řízené sekvence viděli v obráceném pořadí, ale jeho stav můžete změnit, pokud se změní délka řízené sekvence.

### <a name="example"></a>Příklad

```cpp
// cliext_vector_rbegin.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// inspect first two items in reversed sequence
    cliext::vector<wchar_t>::reverse_iterator rit = c1.rbegin();
    System::Console::WriteLine("*rbegin() = {0}", *rit);
    System::Console::WriteLine("*++rbegin() = {0}", *++rit);

// alter first two items and reinspect
    *--rit = L'x';
    *++rit = L'y';
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
*rbegin() = c
*++rbegin() = b
a y x
```

## <a name="reference"></a> Vector::Reference (STL/CLR)

Typ odkazu na prvek

### <a name="syntax"></a>Syntaxe

```cpp
typedef value_type% reference;
```

### <a name="remarks"></a>Poznámky

Typ, který popisuje odkaz na element.

### <a name="example"></a>Příklad

```cpp
// cliext_vector_reference.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display initial contents " a b c"
    cliext::vector<wchar_t>::iterator it = c1.begin();
    for (; it != c1.end(); ++it)
        {   // get a reference to an element
        cliext::vector<wchar_t>::reference ref = *it;
        System::Console::Write("{0} ", ref);
        }
    System::Console::WriteLine();

// modify contents " a b c"
    for (it = c1.begin(); it != c1.end(); ++it)
        {   // get a reference to an element
        cliext::vector<wchar_t>::reference ref = *it;

        ref += (wchar_t)(L'A' - L'a');
        System::Console::Write("{0} ", ref);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
A B C
```

## <a name="rend"></a> Vector::rend (STL/CLR)

Určuje konec řízené obrácené sekvenci.

### <a name="syntax"></a>Syntaxe

```cpp
reverse_iterator rend();
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí "reverse iterator", který ukazuje za začátek řízené sekvence. Proto, označí `end` reverzní pořadí. Můžete ji použít k získání iterátor, který určuje `current` konec řízené sekvence viděli v obráceném pořadí, ale jeho stav můžete změnit, pokud se změní délka řízené sekvence.

### <a name="example"></a>Příklad

```cpp
// cliext_vector_rend.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// inspect first two items
    cliext::vector<wchar_t>::reverse_iterator rit = c1.rend();
    --rit;
    System::Console::WriteLine("*-- --rend() = {0}", *--rit);
    System::Console::WriteLine("*--rend() = {0}", *++rit);

// alter first two items and reinspect
    *--rit = L'x';
    *++rit = L'y';
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
*-- --rend() = b
*--rend() = a
y x c
```

## <a name="reserve"></a> Vector::Reserve (STL/CLR)

Zajišťuje minimální růstu kapacity pro kontejner.

### <a name="syntax"></a>Syntaxe

```cpp
void reserve(size_type count);
```

#### <a name="parameters"></a>Parametry

*Počet*<br/>
Nový minimální kapacitu kontejneru.

### <a name="remarks"></a>Poznámky

Členská funkce zajišťuje, že `capacity()` od nynějška vrátí alespoň *počet*. Použijete ji k zajištění, že kontejner nemusí znovu přidělte úložiště řízené sekvence dokud se rozrostl a zadané velikosti.

### <a name="example"></a>Příklad

```cpp
// cliext_vector_reserve.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display initial contents " a b c"
    for (int i = 0; i < c1.size(); ++i)
        System::Console::Write("{0} ", c1.at(i));
    System::Console::WriteLine();

// increase capacity
    cliext::vector<wchar_t>::size_type cap = c1.capacity();
    System::Console::WriteLine("capacity() = {0}, ok = {1}",
        cap, c1.size() <= cap);
    c1.reserve(cap + 5);
    System::Console::WriteLine("capacity() = {0}, ok = {1}",
        c1.capacity(), cap + 5 <= c1.capacity());
    return (0);
    }
```

```Output
a b c
capacity() = 4, ok = True
capacity() = 9, ok = True
```

## <a name="resize"></a> Vector::Resize (STL/CLR)

Počet prvků, které se změní.

### <a name="syntax"></a>Syntaxe

```cpp
void resize(size_type new_size);
void resize(size_type new_size, value_type val);
```

#### <a name="parameters"></a>Parametry

*new_size*<br/>
Nová velikost řízené sekvence.

*Val*<br/>
Hodnota elementu odsazení.

### <a name="remarks"></a>Poznámky

Členské funkce obou Ujistěte se, že [vector::size (STL/CLR)](../dotnet/vector-size-stl-clr.md) `()` od nynějška vrátí *new_size*. Pokud je třeba provést řízené sekvence delší, první členská funkce přidá prvky s hodnotou `value_type()`, zatímco druhá členská funkce přidá prvky s hodnotou *val*. Chcete-li řízené sekvence kratší, i členské funkce efektivně vymazat poslední prvek [vector::size (STL/CLR)](../dotnet/vector-size-stl-clr.md) `() -` `new_size` časy. Použít zajistit, že velikost řízené sekvence *new_size*, ořezávání nebo odsazení aktuální řízené sekvence.

### <a name="example"></a>Příklad

```cpp
// cliext_vector_resize.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
// construct an empty container and pad with default values
    cliext::vector<wchar_t> c1;
    System::Console::WriteLine("size() = {0}", c1.size());
    c1.resize(4);
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", (int)elem);
    System::Console::WriteLine();

// resize to empty
    c1.resize(0);
    System::Console::WriteLine("size() = {0}", c1.size());

// resize and pad
    c1.resize(5, L'x');
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
size() = 0
0 0 0 0
size() = 0
x x x x x
```

## <a name="reverse_iterator"></a> Vector::reverse_iterator (STL/CLR)

Typ "reverse iterator" pro řízenou sekvenci.

### <a name="syntax"></a>Syntaxe

```cpp
typedef T3 reverse_iterator;
```

### <a name="remarks"></a>Poznámky

Typ popisuje objekt neurčeného typu `T3` , který může sloužit jako "reverse iterator" pro řízenou sekvenci.

### <a name="example"></a>Příklad

```cpp
// cliext_vector_reverse_iterator.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c" reversed
    cliext::vector<wchar_t>::reverse_iterator rit = c1.rbegin();
    for (; rit != c1.rend(); ++rit)
        System::Console::Write("{0} ", *rit);
    System::Console::WriteLine();

// alter first element and redisplay
    rit = c1.rbegin();
    *rit = L'x';
    for (; rit != c1.rend(); ++rit)
        System::Console::Write("{0} ", *rit);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c b a
x b a
```

## <a name="size"></a> Vector::size (STL/CLR)

Spočítá počet prvků.

### <a name="syntax"></a>Syntaxe

```cpp
size_type size();
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí délku objektu řízené sekvence. Použijete ji k určení počtu prvků v řízené sekvenci aktuálně. Pokud vás zajímá, jestli je pořadí má nenulovou velikost, naleznete v tématu [vector::empty (STL/CLR)](../dotnet/vector-empty-stl-clr.md)`()`.

### <a name="example"></a>Příklad

```cpp
// cliext_vector_size.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    System::Console::WriteLine("size() = {0} starting with 3", c1.size());

// clear the container and reinspect
    c1.clear();
    System::Console::WriteLine("size() = {0} after clearing", c1.size());

// add elements and clear again
    c1.push_back(L'a');
    c1.push_back(L'b');
    System::Console::WriteLine("size() = {0} after adding 2", c1.size());
    return (0);
    }
```

```Output
a b c
size() = 3 starting with 3
size() = 0 after clearing
size() = 2 after adding 2
```

## <a name="size_type"></a> Vector::size_type (STL/CLR)

Typ vzdálenosti se znaménkem mezi dvěma prvky

### <a name="syntax"></a>Syntaxe

```cpp
typedef int size_type;
```

### <a name="remarks"></a>Poznámky

Typ, který popisuje počet prvků záporná.

### <a name="example"></a>Příklad

```cpp
// cliext_vector_size_type.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// compute positive difference
    cliext::vector<wchar_t>::size_type diff = c1.end() - c1.begin();
    System::Console::WriteLine("end()-begin() = {0}", diff);
    return (0);
    }
```

```Output
a b c
end()-begin() = 3
```

## <a name="swap"></a> Vector::swap (STL/CLR)

Zamění obsah dvou kontejnerů.

### <a name="syntax"></a>Syntaxe

```cpp
void swap(vector<Value>% right);
```

#### <a name="parameters"></a>Parametry

*doprava*<br/>
Kontejner pro obsah s.

### <a name="remarks"></a>Poznámky

Členská funkce Zamění řízené sekvence mezi `*this` a *správné*. Provádí se v konstantním času a vyvolá žádné výjimky. Můžete použít jako rychlý způsob, jak Zamění obsah dvou kontejnerů.

### <a name="example"></a>Příklad

```cpp
// cliext_vector_swap.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct another container with repetition of values
    cliext::vector<wchar_t> c2(5, L'x');
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// swap and redisplay
    c1.swap(c2);
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
x x x x x
x x x x x
a b c
```

## <a name="to_array"></a> Vector::to_array (STL/CLR)

Zkopíruje do nového pole řízené sekvence.

### <a name="syntax"></a>Syntaxe

```cpp
cli::array<Value>^ to_array();
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí pole obsahující řízené sekvence. Použijete ji získat kopii řízenou sekvenci pole formuláře.

### <a name="example"></a>Příklad

```cpp
// cliext_vector_to_array.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// copy the container and modify it
    cli::array<wchar_t>^ a1 = c1.to_array();

    c1.push_back(L'd');
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// display the earlier array copy
    for each (wchar_t elem in a1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c d
a b c
```

## <a name="value_type"></a> Vector::value_type (STL/CLR)

Typ prvku

### <a name="syntax"></a>Syntaxe

```cpp
typedef Value value_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro parametr šablony *hodnota*.

### <a name="example"></a>Příklad

```cpp
// cliext_vector_value_type.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c" using value_type
    for (cliext::vector<wchar_t>::iterator it = c1.begin();
        it != c1.end(); ++it)
        {   // store element in value_type object
        cliext::vector<wchar_t>::value_type val = *it;

        System::Console::Write("{0} ", val);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="vector"></a> Vector::Vector (STL/CLR)

Sestaví objekt kontejneru.

### <a name="syntax"></a>Syntaxe

```cpp
vector();
vector(vector<Value>% right);
vector(vector<Value>^ right);
explicit vector(size_type count);
vector(size_type count, value_type val);
template<typename InIt>
    vector(InIt first, InIt last);
vector(System::Collections::Generic::IEnumerable<Value>^ right);
```

#### <a name="parameters"></a>Parametry

*Počet*<br/>
Počet elementů k vložení.

*první*<br/>
Začátek rozsahu pro vložení.

*poslední*<br/>
Konec rozsahu pro vložení.

*doprava*<br/>
Objekt nebo rozsahu pro vložení.

*Val*<br/>
Hodnota elementu, který chcete vložit.

### <a name="remarks"></a>Poznámky

Konstruktor:

`vector();`

Inicializuje se žádné prvky řízené sekvence. Použijete ji k určení počáteční prázdnou řízenou sekvenci.

Konstruktor:

`vector(vector<Value>% right);`

Inicializuje řízené sekvence s pořadím [`right.begin()`, `right.end()`). Můžete ji použít k určení počáteční řízené sekvence, který je kopii sekvence řízenou parametrem vektorový objekt *správné*.

Konstruktor:

`vector(vector<Value>^ right);`

Inicializuje řízené sekvence s pořadím [`right->begin()`, `right->end()`). Můžete ji použít k určení počáteční řízené sekvence, který je kopii sekvence řízenou parametrem vektorový objekt, jehož popisovač je *správné*.

Konstruktor:

`explicit vector(size_type count);`

Inicializuje řízené sekvence s *počet* elementy s hodnotou `value_type()`. Použijete ji k vyplnilo kontejner s prvky všechny mají výchozí hodnotu.

Konstruktor:

`vector(size_type count, value_type val);`

Inicializuje řízené sekvence s *počet* elementy s hodnotou *val*. Použijete ji k vyplnilo kontejner s prvky všechny mají stejnou hodnotu.

Konstruktor:

`template<typename InIt>`

`vector(InIt first, InIt last);`

Inicializuje řízené sekvence s pořadím [`first`, `last`). Použijte k vytvoření kopie jiné pořadí řízené sekvence.

Konstruktor:

`vector(System::Collections::Generic::IEnumerable<Value>^ right);`

Inicializuje řízené sekvence s pořadí určeném enumerátor *správné*. Použijete ji k vytvoření kopie jiné pořadí popsal enumerátor řízené sekvence.

### <a name="example"></a>Příklad

```cpp
// cliext_vector_construct.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
// construct an empty container
    cliext::vector<wchar_t> c1;
    System::Console::WriteLine("size() = {0}", c1.size());

// construct with a repetition of default values
    cliext::vector<wchar_t> c2(3);
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", (int)elem);
    System::Console::WriteLine();

// construct with a repetition of values
    cliext::vector<wchar_t> c3(6, L'x');
    for each (wchar_t elem in c3)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct with an iterator range
    cliext::vector<wchar_t>::iterator it = c3.end();
    cliext::vector<wchar_t> c4(c3.begin(), --it);
    for each (wchar_t elem in c4)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct with an enumeration
    cliext::vector<wchar_t> c5(   // NOTE: cast is not needed
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3);
    for each (wchar_t elem in c5)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct by copying another container
    cliext::vector<wchar_t> c7(c3);
    for each (wchar_t elem in c7)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct by copying a container handle
    cliext::vector<wchar_t> c8(%c3);
    for each (wchar_t elem in c8)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    return (0);
    }
```

```Output
size() = 0
0 0 0
x x x x x x
x x x x x
x x x x x x
x x x x x x
x x x x x x
```

## <a name="op_neq"></a> Operator! = (vector) (STL/CLR)

Vector – nerovná porovnání.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Value>
    bool operator!=(vector<Value>% left,
        vector<Value>% right);
```

#### <a name="parameters"></a>Parametry

*doleva*<br/>
Levé kontejner k porovnání.

*doprava*<br/>
Správném kontejneru pro porovnání.

### <a name="remarks"></a>Poznámky

Vrátí funkci operátoru `!(left == right)`. Pomocí něho můžete testovat, zda *levé* není stejný jako seřazené *správné* způsob porovnání elementu pomocí elementu dvěma vektory.

### <a name="example"></a>Příklad

```cpp
// cliext_vector_operator_ne.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    cliext::vector<wchar_t> c2;
    c2.push_back(L'a');
    c2.push_back(L'b');
    c2.push_back(L'd');

// display contents " a b d"
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("[a b c] != [a b c] is {0}",
        c1 != c1);
    System::Console::WriteLine("[a b c] != [a b d] is {0}",
        c1 != c2);
    return (0);
    }
```

```Output
a b c
a b d
[a b c] != [a b c] is False
[a b c] != [a b d] is True
```

## <a name="op_lt"></a> operátor&lt; (vector) (STL/CLR)

Vektor menší než porovnání.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Value>
    bool operator<(vector<Value>% left,
        vector<Value>% right);
```

#### <a name="parameters"></a>Parametry

*doleva*<br/>
Levé kontejner k porovnání.

*doprava*<br/>
Správném kontejneru pro porovnání.

### <a name="remarks"></a>Poznámky

Operátoru funkce vrátí hodnota true v případě, pro nejnižší pozici `i` pro kterou `!(right[i] < left[i])` je také hodnotu true, který `left[i] < right[i]`. V opačném případě vrátí `left->size() < right->size()` pomocí něho můžete testovat, zda *levé* je řazen před *správné* způsob porovnání elementu pomocí elementu dvěma vektory.

### <a name="example"></a>Příklad

```cpp
// cliext_vector_operator_lt.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    cliext::vector<wchar_t> c2;
    c2.push_back(L'a');
    c2.push_back(L'b');
    c2.push_back(L'd');

// display contents " a b d"
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("[a b c] < [a b c] is {0}",
        c1 < c1);
    System::Console::WriteLine("[a b c] < [a b d] is {0}",
        c1 < c2);
    return (0);
    }
```

```Output
a b c
a b d
[a b c] < [a b c] is False
[a b c] < [a b d] is True
```

## <a name="op_lteq"></a> operátor&lt;= (vector) (STL/CLR)

Vector – menší nebo rovna porovnání.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Value>
    bool operator<=(vector<Value>% left,
        vector<Value>% right);
```

#### <a name="parameters"></a>Parametry

*doleva*<br/>
Levé kontejner k porovnání.

*doprava*<br/>
Správném kontejneru pro porovnání.

### <a name="remarks"></a>Poznámky

Vrátí funkci operátoru `!(right < left)`. Pomocí něho můžete testovat, zda *levé* není seřazené po *správné* způsob porovnání elementu pomocí elementu dvěma vektory.

### <a name="example"></a>Příklad

```cpp
// cliext_vector_operator_le.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    cliext::vector<wchar_t> c2;
    c2.push_back(L'a');
    c2.push_back(L'b');
    c2.push_back(L'd');

// display contents " a b d"
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("[a b c] <= [a b c] is {0}",
        c1 <= c1);
    System::Console::WriteLine("[a b d] <= [a b c] is {0}",
        c2 <= c1);
    return (0);
    }
```

```Output
a b c
a b d
[a b c] <= [a b c] is True
[a b d] <= [a b c] is False
```

## <a name="op_eq"></a> Operator == (vector) (STL/CLR)

Porovnání rovna vektoru.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Value>
    bool operator==(vector<Value>% left,
        vector<Value>% right);
```

#### <a name="parameters"></a>Parametry

*doleva*<br/>
Levé kontejner k porovnání.

*doprava*<br/>
Správném kontejneru pro porovnání.

### <a name="remarks"></a>Poznámky

Funkce operátoru vrátí hodnotu true pouze v případě, že řídí sekvencí *levé* a *správné* mít stejnou délku a pro každou pozici `i`, `left[i] ==` `right[i]`. Pomocí něho můžete testovat, zda *levé* je stejný jako seřazené *správné* způsob porovnání elementu pomocí elementu dvěma vektory.

### <a name="example"></a>Příklad

```cpp
// cliext_vector_operator_eq.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    cliext::vector<wchar_t> c2;
    c2.push_back(L'a');
    c2.push_back(L'b');
    c2.push_back(L'd');

// display contents " a b d"
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("[a b c] == [a b c] is {0}",
        c1 == c1);
    System::Console::WriteLine("[a b c] == [a b d] is {0}",
        c1 == c2);
    return (0);
    }
```

```Output
a b c
a b d
[a b c] == [a b c] is True
[a b c] == [a b d] is False
```

## <a name="op_gt"></a> operátor&gt; (vector) (STL/CLR)

Vektor je větší než porovnání.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Value>
    bool operator>(vector<Value>% left,
        vector<Value>% right);
```

#### <a name="parameters"></a>Parametry

*doleva*<br/>
Levé kontejner k porovnání.

*doprava*<br/>
Správném kontejneru pro porovnání.

### <a name="remarks"></a>Poznámky

Vrátí funkci operátoru `right` `<` `left`. Pomocí něho můžete testovat, zda *levé* seřazené po *správné* způsob porovnání elementu pomocí elementu dvěma vektory.

### <a name="example"></a>Příklad

```cpp
// cliext_vector_operator_gt.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    cliext::vector<wchar_t> c2;
    c2.push_back(L'a');
    c2.push_back(L'b');
    c2.push_back(L'd');

// display contents " a b d"
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("[a b c] > [a b c] is {0}",
        c1 > c1);
    System::Console::WriteLine("[a b d] > [a b c] is {0}",
        c2 > c1);
    return (0);
    }
```

```Output
a b c
a b d
[a b c] > [a b c] is False
[a b d] > [a b c] is True
```

## <a name="op_gteq"></a> operátor&gt;= (vector) (STL/CLR)

Vektor větší než nebo rovna porovnání.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Value>
    bool operator>=(vector<Value>% left,
        vector<Value>% right);
```

#### <a name="parameters"></a>Parametry

*doleva*<br/>
Levé kontejner k porovnání.

*doprava*<br/>
Správném kontejneru pro porovnání.

### <a name="remarks"></a>Poznámky

Vrátí funkci operátoru `!(left < right)`. Pomocí něho můžete testovat, zda *levé* není řazen před *správné* způsob porovnání elementu pomocí elementu dvěma vektory.

### <a name="example"></a>Příklad

```cpp
// cliext_vector_operator_ge.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    cliext::vector<wchar_t> c2;
    c2.push_back(L'a');
    c2.push_back(L'b');
    c2.push_back(L'd');

// display contents " a b d"
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("[a b c] >= [a b c] is {0}",
        c1 >= c1);
    System::Console::WriteLine("[a b c] >= [a b d] is {0}",
        c1 >= c2);
    return (0);
    }
```

```Output
a b c
a b d
[a b c] >= [a b c] is True
[a b c] >= [a b d] is False
```