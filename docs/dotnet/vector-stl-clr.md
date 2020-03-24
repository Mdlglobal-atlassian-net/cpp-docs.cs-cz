---
title: vector (STL/CLR)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cliext::vector
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
ms.openlocfilehash: bbd4d7b6e7e7668100b2694fdcf3b785d7681ca3
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80208270"
---
# <a name="vector-stlclr"></a>vector (STL/CLR)

Třída šablony popisuje objekt, který řídí proměnlivou délku sekvence prvků, které mají náhodný přístup. Pomocí `vector` kontejnerů můžete spravovat sekvenci prvků jako souvislý blok úložiště. Blok je implementován jako pole, které roste na vyžádání.

V popisu níže je `GValue` stejné jako *hodnota* , pokud se jedná o typ REF, v takovém případě je `Value^`.

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

**Záhlaví:** \<cliext –/Vector >

**Obor názvů:** cliext –

## <a name="declarations"></a>Deklarace

|Definice typu|Popis|
|---------------------|-----------------|
|[vector::const_iterator (STL/CLR)](#const_iterator)|Typ konstantního iterátoru řízené sekvence|
|[vector::const_reference (STL/CLR)](#const_reference)|Typ konstantního odkazu na prvek|
|[vector::const_reverse_iterator (STL/CLR)](#const_reverse_iterator)|Typ konstantního reverzního iterátoru řízené sekvence.|
|[vector::difference_type (STL/CLR)](#difference_type)|Typ vzdálenosti se znaménkem mezi dvěma prvky|
|[vector::generic_container (STL/CLR)](#generic_container)|Typ obecného rozhraní pro kontejner.|
|[vector::generic_iterator (STL/CLR)](#generic_iterator)|Typ iterátoru pro obecné rozhraní kontejneru.|
|[vector::generic_reverse_iterator (STL/CLR)](#generic_reverse_iterator)|Typ reverzního iterátoru pro obecné rozhraní kontejneru.|
|[vector::generic_value (STL/CLR)](#generic_value)|Typ elementu pro obecné rozhraní kontejneru.|
|[vector::iterator (STL/CLR)](#iterator)|Typ iterátoru řízené sekvence|
|[vector::reference (STL/CLR)](#reference)|Typ odkazu na prvek|
|[vector::reverse_iterator (STL/CLR)](#reverse_iterator)|Typ reverzního iterátoru řízené sekvence.|
|[vector::size_type (STL/CLR)](#size_type)|Typ vzdálenosti se znaménkem mezi dvěma prvky|
|[vector::value_type (STL/CLR)](#value_type)|Typ prvku|

|Členská funkce|Popis|
|---------------------|-----------------|
|[vector::assign (STL/CLR)](#assign)|Nahradí všechny prvky.|
|[vector::at (STL/CLR)](#at)|Přistupuje k elementu na zadané pozici.|
|[vector::back (STL/CLR)](#back)|Přistupuje k poslednímu prvku.|
|[vector::begin (STL/CLR)](#begin)|Určuje začátek řízené sekvence.|
|[vector::capacity (STL/CLR)](#capacity)|Oznamuje velikost přiděleného úložiště pro kontejner.|
|[vector::clear (STL/CLR)](#clear)|Odebere všechny prvky.|
|[vector::empty (STL/CLR)](#empty)|Zkouší, zda nejsou přítomny žádné prvky.|
|[vector::end (STL/CLR)](#end)|Určuje konec řízené sekvence.|
|[vector::erase (STL/CLR)](#erase)|Odebere prvky v určených pozicích.|
|[vector::front (STL/CLR)](#front)|Přistupuje k prvnímu prvku.|
|[vector::insert (STL/CLR)](#insert)|Přidá prvky na zadanou pozici.|
|[vector::pop_back (STL/CLR)](#pop_back)|Odstraní poslední prvek.|
|[vector::push_back (STL/CLR)](#push_back)|Přidá nový poslední prvek.|
|[vector::rbegin (STL/CLR)](#rbegin)|Určuje začátek obrácené kontrolované sekvence.|
|[vector::rend (STL/CLR)](#rend)|Určuje konec reverzní kontrolované sekvence.|
|[vector::reserve (STL/CLR)](#reserve)|Zajišťuje minimální kapacitu růstu pro kontejner.|
|[vector::resize (STL/CLR)](#resize)|Změní počet prvků.|
|[vector::size (STL/CLR)](#size)|Spočítá počet prvků.|
|[vector::swap (STL/CLR)](#swap)|Zamění obsah dvou kontejnerů.|
|[vector::to_array (STL/CLR)](#to_array)|Zkopíruje řízenou sekvenci do nového pole.|
|[vector::vector (STL/CLR)](#vector)|Sestaví objekt kontejneru.|

|Vlastnost|Popis|
|--------------|-----------------|
|[vector::back_item (STL/CLR)](#back_item)|Přistupuje k poslednímu prvku.|
|[vector::front_item (STL/CLR)](#front_item)|Přistupuje k prvnímu prvku.|

|Operátor|Popis|
|--------------|-----------------|
|[vector::operator= (STL/CLR)](#op_as)|Nahradí řízenou sekvenci.|
|[vector::operator(STL/CLR)](#op)|Přistupuje k elementu na zadané pozici.|
|[operator!= (vector) (STL/CLR)](#op_neq)|Určuje, zda `vector` objekt není roven jinému objektu `vector`.|
|[operator< (vector) (STL/CLR)](#op_lt)|Určuje, zda je objekt `vector` menší než jiný objekt `vector`.|
|[operator<= (vector) (STL/CLR)](#op_lteq)|Určuje, zda je objekt `vector` menší nebo roven jinému objektu `vector`.|
|[operator== (vector) (STL/CLR)](#op_eq)|Určuje, zda je objekt `vector` roven jinému objektu `vector`.|
|[operator> (vector) (STL/CLR)](#op_gt)|Určuje, zda je objekt `vector` větší než jiný objekt `vector`.|
|[operator>= (vector) (STL/CLR)](#op_gteq)|Určuje, zda je objekt `vector` větší nebo roven jinému objektu `vector`.|

## <a name="interfaces"></a>Rozhraní

|Rozhraní|Popis|
|---------------|-----------------|
|<xref:System.ICloneable>|Duplikuje objekt.|
|<xref:System.Collections.IEnumerable>|Sekvence prostřednictvím prvků.|
|<xref:System.Collections.ICollection>|Udržovat skupinu prvků.|
|<xref:System.Collections.Generic.IEnumerable%601>|Sekvence prostřednictvím typových elementů.|
|<xref:System.Collections.Generic.ICollection%601>|Udržovat skupinu typových elementů.|
|<xref:System.Collections.Generic.IList%601>|Udržovat uspořádanou skupinu typových prvků.|
|IVector hodnota <\>|Udržujte obecný kontejner.|

## <a name="remarks"></a>Poznámky

Objekt přiděluje a uvolňuje úložiště pro sekvenci, kterou ovládá, prostřednictvím uloženého pole *hodnotových* prvků, které roste na vyžádání. Růst probíhá takovým způsobem, že náklady na připojení nového prvku jsou konstantním časem. Jinými slovy, náklady na přidání prvků na konci nezvyšují průměrně, protože délka řízené sekvence je větší. Proto je vektor vhodným kandidátem pro základní kontejner pro zásobník tříd šablon [(STL/CLR)](../dotnet/stack-stl-clr.md).

`vector` podporuje iterátory s náhodným přístupem, což znamená, že můžete odkazovat na element přímo v rámci své číselné pozice, počítáno od nuly pro první (přední) prvek a `size() - 1` pro poslední (zadní) prvek. Také to znamená, že vektor je dobrým kandidátem pro základní kontejner pro třídu šablony [priority_queue (STL/CLR)](../dotnet/priority-queue-stl-clr.md).

Vektorový iterátor ukládá popisovač do svého přidruženého vektorového objektu spolu s posunem elementu, který označuje. Iterátory lze použít pouze u jejich přidružených objektů kontejneru. Posun prvku Vector je stejný jako jeho pozice.

Vložení nebo mazání prvků může změnit hodnotu prvku uloženou na dané pozici, aby mohla být hodnota určená iterátorem také změněna. (Kontejner může muset zkopírovat prvky nahoru nebo dolů a vytvořit díru před vložením nebo vyplněním otvoru po vymazání.) Nicméně vektorový iterátor zůstává platný, pokud je jeho posun v rozsahu `[0, size()]`. Navíc platí, že platný iterátor zůstává neodkazný – můžete ho použít k přístupu k hodnotě prvku, kterou určí, a k její změně, pokud se její posun nerovná `size()`.

Při mazání nebo odebírání elementu se volá destruktor pro jeho uloženou hodnotu. Zničení kontejneru smaže všechny prvky. Proto kontejner, jehož typ elementu je ref class, zajistí, že kontejner neobsahuje žádné prvky. Upozorňujeme však, že kontejner popisovačů nezničí své prvky.

## <a name="members"></a>Členové

## <a name="vectorassign-stlclr"></a><a name="assign"></a>Vector:: assign (STL/CLR)

Nahradí všechny prvky.

### <a name="syntax"></a>Syntaxe

```cpp
void assign(size_type count, value_type val);
template<typename InIt>
    void assign(InIt first, InIt last);
void assign(System::Collections::Generic::IEnumerable<Value>^ right);
```

#### <a name="parameters"></a>Parametry

*count*<br/>
Počet prvků, které mají být vloženy.

*první*<br/>
Začátek rozsahu, který se má vložit

*posledního*<br/>
Konec rozsahu, který má být vložen.

*Kliknutím*<br/>
Výčet pro vložení.

*počítává*<br/>
Hodnota prvku, který má být vložen.

### <a name="remarks"></a>Poznámky

První členská funkce nahradí řízenou sekvencí opakováním prvků *Count* hodnoty *Val*. Použijete ho k vyplnění kontejneru všemi prvky, které mají stejnou hodnotu.

Pokud `InIt` je celočíselný typ, druhá členská funkce se chová stejně jako `assign((size_type)first, (value_type)last)`. V opačném případě nahradí řízená sekvence sekvencí [`first`, `last`). Použijete ho k tomu, aby řízená sekvence zkopírovala jinou sekvenci.

Třetí členská funkce nahradí kontrolované sekvence sekvencí, která je určena *přípravou*výčtu. Použijete ho k tomu, aby řízená sekvence zkopírovala sekvenci popsanou enumerátorem.

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

## <a name="vectorat-stlclr"></a><a name="at"></a>Vector:: at (STL/CLR)

Přistupuje k elementu na zadané pozici.

### <a name="syntax"></a>Syntaxe

```cpp
reference at(size_type pos);
```

#### <a name="parameters"></a>Parametry

*POS*<br/>
Pozice prvku pro přístup

### <a name="remarks"></a>Poznámky

Členská funkce vrátí odkaz na prvek řízené sekvence na pozici pozice *POS*. Použijete ho ke čtení nebo zápisu elementu, jehož poloha znáte.

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

## <a name="vectorback-stlclr"></a><a name="back"></a>Vector:: Back (STL/CLR)

Přistupuje k poslednímu prvku.

### <a name="syntax"></a>Syntaxe

```cpp
reference back();
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí odkaz na poslední prvek řízené sekvence, který nesmí být prázdný. Použijete ho k přístupu k poslednímu prvku, když víte, že existuje.

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

## <a name="vectorback_item-stlclr"></a><a name="back_item"></a>Vector:: back_item (STL/CLR)

Přistupuje k poslednímu prvku.

### <a name="syntax"></a>Syntaxe

```cpp
property value_type back_item;
```

### <a name="remarks"></a>Poznámky

Vlastnost přistupuje k poslednímu prvku kontrolované sekvence, který nesmí být prázdný. Použijete ho ke čtení nebo zápisu posledního prvku, když víte, že existuje.

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

## <a name="vectorbegin-stlclr"></a><a name="begin"></a>Vector:: begin (STL/CLR)

Určuje začátek řízené sekvence.

### <a name="syntax"></a>Syntaxe

```cpp
iterator begin();
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí iterátor náhodného přístupu, který určuje první prvek řízené sekvence nebo těsně za konec prázdné sekvence. Použijete ho k získání iterátoru, který určuje `current` začátek řízené sekvence, ale jeho stav se může změnit, pokud se změní délka kontrolované sekvence.

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

## <a name="vectorcapacity-stlclr"></a><a name="capacity"></a>Vector:: Capacity (STL/CLR)

Oznamuje velikost přiděleného úložiště pro kontejner.

### <a name="syntax"></a>Syntaxe

```cpp
size_type capacity();
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí aktuálně přidělené úložiště, aby obsahovalo řízenou sekvenci, hodnotu aspoň tak velkou jako [Vector:: Size (STL/CLR)](../dotnet/vector-size-stl-clr.md)`()`. Můžete ji použít k určení, kolik kontejneru může růst, než musí znovu přidělit úložiště pro řízenou sekvenci.

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

## <a name="vectorclear-stlclr"></a><a name="clear"></a>Vector:: Clear (STL/CLR)

Odebere všechny prvky.

### <a name="syntax"></a>Syntaxe

```cpp
void clear();
```

### <a name="remarks"></a>Poznámky

Členská funkce efektivně volá [Vector:: Erase (STL/CLR)](../dotnet/vector-erase-stl-clr.md)`(` [Vector:: begin (STL/CLR)](../dotnet/vector-begin-stl-clr.md)`(),` [Vector:: end (STL/CLR](../dotnet/vector-end-stl-clr.md) )`())`. Použijete ho k zajištění, aby řízená sekvence byla prázdná.

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

## <a name="vectorconst_iterator-stlclr"></a><a name="const_iterator"></a>Vector:: const_iterator (STL/CLR)

Typ konstantního iterátoru řízené sekvence

### <a name="syntax"></a>Syntaxe

```cpp
typedef T2 const_iterator;
```

### <a name="remarks"></a>Poznámky

Typ popisuje objekt nespecifikovaného typu `T2`, který může sloužit jako konstantní iterátor náhodného přístupu pro řízenou sekvenci.

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

## <a name="vectorconst_reference-stlclr"></a><a name="const_reference"></a>Vector:: const_reference (STL/CLR)

Typ konstantního odkazu na prvek

### <a name="syntax"></a>Syntaxe

```cpp
typedef value_type% const_reference;
```

### <a name="remarks"></a>Poznámky

Typ popisuje konstantní odkaz na prvek.

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

## <a name="vectorconst_reverse_iterator-stlclr"></a><a name="const_reverse_iterator"></a>Vector:: const_reverse_iterator (STL/CLR)

Typ konstantního reverzního iterátoru řízené sekvence.

### <a name="syntax"></a>Syntaxe

```cpp
typedef T4 const_reverse_iterator;
```

### <a name="remarks"></a>Poznámky

Typ popisuje objekt nespecifikovaného typu `T4`, který může sloužit jako konstantní reverzní iterátor pro řízenou sekvenci.

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

## <a name="vectordifference_type-stlclr"></a><a name="difference_type"></a>Vector::d ifference_type (STL/CLR)

Typy podepsané vzdálenosti mezi dvěma prvky.

### <a name="syntax"></a>Syntaxe

```cpp
typedef int difference_type;
```

### <a name="remarks"></a>Poznámky

Typ popisuje počet podepsaných prvků.

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

## <a name="vectorempty-stlclr"></a><a name="empty"></a>Vector:: Empty (STL/CLR)

Zkouší, zda nejsou přítomny žádné prvky.

### <a name="syntax"></a>Syntaxe

```cpp
bool empty();
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí hodnotu true pro prázdnou řízenou sekvenci. Je ekvivalentní s`() == 0`[Vector:: Size (STL/CLR)](../dotnet/vector-size-stl-clr.md) . Použijete ho k otestování, jestli je vektor prázdný.

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

## <a name="vectorend-stlclr"></a><a name="end"></a>Vector:: end (STL/CLR)

Určuje konec řízené sekvence.

### <a name="syntax"></a>Syntaxe

```cpp
iterator end();
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí iterátor náhodného přístupu, který odkazuje hned za konec řízené sekvence. Použijete ho k získání iterátoru, který určuje `current` konec řízené sekvence, ale jeho stav se může změnit, pokud se změní délka kontrolované sekvence.

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

## <a name="vectorerase-stlclr"></a><a name="erase"></a>Vector:: Erase (STL/CLR)

Odebere prvky v určených pozicích.

### <a name="syntax"></a>Syntaxe

```cpp
iterator erase(iterator where);
iterator erase(iterator first, iterator last);
```

#### <a name="parameters"></a>Parametry

*první*<br/>
Začátek rozsahu, který se má vymazat

*posledního*<br/>
Konec rozsahu, který se má vymazat

*,*<br/>
Prvek k vymazání.

### <a name="remarks"></a>Poznámky

První členská funkce odstraní prvek řízené sekvence, na kterou ukazuje, *kde*. Použijete ho k odebrání jednoho elementu.

Druhá členská funkce odstraní prvky řízené sekvence v rozsahu [`first`, `last`). Použijete ho k odebrání nuly nebo více souvislých prvků.

Oba členské funkce vrací iterátor, který určuje první prvek zbývající za odebranými prvky, nebo [Vector:: end (STL/CLR)](../dotnet/vector-end-stl-clr.md)`()`, pokud žádný takový prvek neexistuje.

Při mazání prvků je počet kopií elementu lineární v počtu prvků mezi koncem mazání a koncem koncového čísla sekvence. (Při mazání jednoho nebo více prvků na konci sekvence nedojde k žádnému kopírování prvků.)

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

## <a name="vectorfront-stlclr"></a><a name="front"></a>Vector:: front (STL/CLR)

Přistupuje k prvnímu prvku.

### <a name="syntax"></a>Syntaxe

```cpp
reference front();
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí odkaz na první prvek řízené sekvence, který nesmí být prázdný. Použijete ho ke čtení nebo zápisu prvního prvku, když víte, že existuje.

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

## <a name="vectorfront_item-stlclr"></a><a name="front_item"></a>Vector:: front_item (STL/CLR)
Přistupuje k prvnímu prvku.

### <a name="syntax"></a>Syntaxe

```cpp
property value_type front_item;
```

### <a name="remarks"></a>Poznámky

Vlastnost přistupuje k prvnímu prvku kontrolované sekvence, který nesmí být prázdný. Použijete ho ke čtení nebo zápisu prvního prvku, když víte, že existuje.

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

## <a name="vectorgeneric_container-stlclr"></a><a name="generic_container"></a>Vector:: generic_container (STL/CLR)
Typ obecného rozhraní pro kontejner.

### <a name="syntax"></a>Syntaxe

```cpp
typedef Microsoft::VisualC::StlClr::
    IVector<generic_value>
    generic_container;
```

### <a name="remarks"></a>Poznámky

Typ popisuje obecné rozhraní pro tuto třídu kontejneru šablony.

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

## <a name="vectorgeneric_iterator-stlclr"></a><a name="generic_iterator"></a>Vector:: generic_iterator (STL/CLR)

Typ iterátoru pro použití s obecným rozhraním pro kontejner.

### <a name="syntax"></a>Syntaxe

```cpp
typedef Microsoft::VisualC::StlClr::Generic::
    ContainerRandomAccessIterator<generic_value>
    generic_iterator;
```

### <a name="remarks"></a>Poznámky

Typ popisuje obecný iterátor, který lze použít s obecným rozhraním pro tuto třídu kontejneru šablony.

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

## <a name="vectorgeneric_reverse_iterator-stlclr"></a><a name="generic_reverse_iterator"></a>Vector:: generic_reverse_iterator (STL/CLR)
Typ reverzního iterátoru pro použití s obecným rozhraním pro kontejner.

### <a name="syntax"></a>Syntaxe

```cpp
typedef Microsoft::VisualC::StlClr::Generic::
    ReverseRandomAccessIterator<generic_value> generic_reverse_iterator;
```

### <a name="remarks"></a>Poznámky

Typ popisuje obecný reverzní iterátor, který lze použít s obecným rozhraním pro tuto třídu kontejneru šablony.

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

## <a name="vectorgeneric_value-stlclr"></a><a name="generic_value"></a>Vector:: generic_value (STL/CLR)

Typ elementu pro použití s obecným rozhraním pro kontejner.

### <a name="syntax"></a>Syntaxe

```cpp
typedef GValue generic_value;
```

### <a name="remarks"></a>Poznámky

Typ popisuje objekt typu `GValue`, který popisuje hodnotu uloženého elementu pro použití s obecným rozhraním pro tuto třídu kontejneru šablony.

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

## <a name="vectorinsert-stlclr"></a><a name="insert"></a>Vector:: Insert (STL/CLR)

Přidá prvky na zadanou pozici.

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

*count*<br/>
Počet prvků, které mají být vloženy.

*první*<br/>
Začátek rozsahu, který se má vložit

*posledního*<br/>
Konec rozsahu, který má být vložen.

*Kliknutím*<br/>
Výčet pro vložení.

*počítává*<br/>
Hodnota prvku, který má být vložen.

*,*<br/>
Kam vložit do kontejneru.

### <a name="remarks"></a>Poznámky

Každá z členských funkcí vloží, před prvek, na který ukazuje, *kde* v řízené sekvenci je sekvence určená zbývajícími operandy.

První členská funkce vloží prvek s hodnotou *Val* a vrátí iterátor, který určí nově vložený element. Použijete ho pro vložení jednoho prvku před místo určené iterátorem.

Druhá členská funkce vloží opakování *počtu prvků Value* *Val*. Použijete ho k vložení nula nebo více souvislých prvků, které jsou kopie stejné hodnoty.

Pokud `InIt` je celočíselný typ, třetí členská funkce se chová stejně jako `insert(where, (size_type)first, (value_type)last)`. V opačném případě vloží sekvenci [`first``last`). Použijete ho k vložení nula nebo více sousedících prvků zkopírovaných z jiné sekvence.

Čtvrtá členská funkce vloží sekvenci určenou *vpravo*. Použijete ho k vložení sekvence popsané enumerátorem.

Při vkládání jednoho prvku je počet kopií elementu lineární v počtu elementů mezi kurzorem a koncem sekvence. (Při vložení jednoho nebo více prvků na konci sekvence nedojde k žádnému kopírování prvků.) Pokud je `InIt` vstupní iterátor, třetí členská funkce efektivně provede jedno vložení pro každý prvek v sekvenci. V opačném případě při vkládání `N` prvků je počet kopií prvku lineární v `N` plus počet prvků mezi kurzorem a koncem sekvence.

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

## <a name="vectoriterator-stlclr"></a><a name="iterator"></a>Vector:: iterátor (STL/CLR)

Typ iterátoru řízené sekvence

### <a name="syntax"></a>Syntaxe

```cpp
typedef T1 iterator;
```

### <a name="remarks"></a>Poznámky

Typ popisuje objekt nespecifikovaného typu `T1`, který může sloužit jako iterátor náhodného přístupu pro řízenou sekvenci.

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

## <a name="vectoroperator-stlclr"></a><a name="op_as"></a>Vector:: operator = – operátor (STL/CLR)

Nahradí řízenou sekvenci.

### <a name="syntax"></a>Syntaxe

```cpp
vector<Value>% operator=(vector<Value>% right);
```

#### <a name="parameters"></a>Parametry

*Kliknutím*<br/>
Kontejner ke zkopírování.

### <a name="remarks"></a>Poznámky

Operátor členu kopíruje *přímo* na objekt a potom vrátí `*this`. Použijete ji k nahrazení kontrolované sekvence kopií kontrolované sekvence *vpravo*.

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

## <a name="vectoroperatorstlclr"></a><a name="op"></a>Vector:: – operátor (STL/CLR)

Přistupuje k elementu na zadané pozici.

### <a name="syntax"></a>Syntaxe

```cpp
reference operator[](size_type pos);
```

#### <a name="parameters"></a>Parametry

*POS*<br/>
Pozice prvku pro přístup

### <a name="remarks"></a>Poznámky

Operátor member vrátí referene k elementu na pozici *POS*. Použijete ho pro přístup k elementu, jehož poloha znáte.

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

## <a name="vectorpop_back-stlclr"></a><a name="pop_back"></a>Vector::p op_back (STL/CLR)

Odstraní poslední prvek.

### <a name="syntax"></a>Syntaxe

```cpp
void pop_back();
```

### <a name="remarks"></a>Poznámky

Členská funkce odstraní poslední prvek kontrolované sekvence, který nesmí být prázdný. Použijete ho ke zkrácení vektoru o jeden prvek na pozadí.

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

## <a name="vectorpush_back-stlclr"></a><a name="push_back"></a>Vector::p ush_back (STL/CLR)

Přidá nový poslední prvek.

### <a name="syntax"></a>Syntaxe

```cpp
void push_back(value_type val);
```

### <a name="remarks"></a>Poznámky

Členská funkce vloží element s hodnotou `val` na konci řízené sekvence. Použijete ho k připojení jiného elementu ke vektoru.

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

## <a name="vectorrbegin-stlclr"></a><a name="rbegin"></a>Vector:: rbegin (STL/CLR)

Určuje začátek obrácené kontrolované sekvence.

### <a name="syntax"></a>Syntaxe

```cpp
reverse_iterator rbegin();
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí reverzní iterátor, který určuje poslední prvek řízené sekvence nebo těsně za začátek prázdné sekvence. Proto určuje `beginning` reverzní sekvence. Použijete ho k získání iterátoru, který určí `current` začátkem kontrolované sekvence v obráceném pořadí, ale jeho stav se může změnit, pokud se změní délka kontrolované sekvence.

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

## <a name="vectorreference-stlclr"></a><a name="reference"></a>Vector:: Reference (STL/CLR)

Typ odkazu na prvek

### <a name="syntax"></a>Syntaxe

```cpp
typedef value_type% reference;
```

### <a name="remarks"></a>Poznámky

Typ popisuje odkaz na prvek.

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

## <a name="vectorrend-stlclr"></a><a name="rend"></a>Vector:: rend (STL/CLR)

Určuje konec reverzní kontrolované sekvence.

### <a name="syntax"></a>Syntaxe

```cpp
reverse_iterator rend();
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí reverzní iterátor, který odkazuje hned za začátek řízené sekvence. Proto určuje `end` reverzní sekvence. Použijete ho k získání iterátoru, který určuje `current` konec řízené sekvence v obráceném pořadí, ale jeho stav se může změnit, pokud se změní délka kontrolované sekvence.

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

## <a name="vectorreserve-stlclr"></a><a name="reserve"></a>Vector:: Reserve (STL/CLR)

Zajišťuje minimální kapacitu růstu pro kontejner.

### <a name="syntax"></a>Syntaxe

```cpp
void reserve(size_type count);
```

#### <a name="parameters"></a>Parametry

*count*<br/>
Nová Minimální kapacita kontejneru.

### <a name="remarks"></a>Poznámky

Členská funkce zajišťuje, že `capacity()` funkce příště vrátí alespoň *počet*. Použijete ho k zajištění, aby kontejner nemusel znovu přidělit úložiště pro řízenou sekvenci, dokud se nezvětšil na určenou velikost.

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

## <a name="vectorresize-stlclr"></a><a name="resize"></a>Vector:: Resize (STL/CLR)

Změní počet prvků.

### <a name="syntax"></a>Syntaxe

```cpp
void resize(size_type new_size);
void resize(size_type new_size, value_type val);
```

#### <a name="parameters"></a>Parametry

*new_size*<br/>
Nová velikost řízené sekvence.

*počítává*<br/>
Hodnota elementu odsazení

### <a name="remarks"></a>Poznámky

Členské funkce zajišťují, že funkce [Vector:: Size (STL/CLR)](../dotnet/vector-size-stl-clr.md)`()` vrátí *new_size*. Je-li nutné řídit sekvenci déle, První členská funkce připojí prvky s hodnotou `value_type()`, zatímco druhá členská funkce připojí prvky s hodnotou *Val*. Chcete-li nastavit kratší sekvenci, obě členské funkce efektivně vymažou poslední prvek [Vector:: Size (STL/CLR)](../dotnet/vector-size-stl-clr.md)`() -` `new_size` časy. Slouží k zajištění, že řízená sekvence má velikost *new_size*, buď oříznutím nebo odsazením aktuálně řízené sekvence.

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

## <a name="vectorreverse_iterator-stlclr"></a><a name="reverse_iterator"></a>Vector:: reverse_iterator (STL/CLR)

Typ reverzního iterátoru řízené sekvence.

### <a name="syntax"></a>Syntaxe

```cpp
typedef T3 reverse_iterator;
```

### <a name="remarks"></a>Poznámky

Typ popisuje objekt nespecifikovaného typu `T3`, který může sloužit jako reverzní iterátor pro řízenou sekvenci.

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

## <a name="vectorsize-stlclr"></a><a name="size"></a>Vector:: Size (STL/CLR)

Spočítá počet prvků.

### <a name="syntax"></a>Syntaxe

```cpp
size_type size();
```

### <a name="remarks"></a>Poznámky

Členská funkce vrací délku řízené sekvence. Použijete ji k určení počtu prvků, které jsou aktuálně v řízené sekvenci. Pokud vše zajímáte o, zda má sekvence nenulovou velikost, přečtěte si téma [Vector:: Empty (STL/CLR)](../dotnet/vector-empty-stl-clr.md)`()`.

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

## <a name="vectorsize_type-stlclr"></a><a name="size_type"></a>Vector:: size_type (STL/CLR)

Typ vzdálenosti se znaménkem mezi dvěma prvky

### <a name="syntax"></a>Syntaxe

```cpp
typedef int size_type;
```

### <a name="remarks"></a>Poznámky

Typ popisuje nezáporný počet prvků.

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

## <a name="vectorswap-stlclr"></a><a name="swap"></a>Vector:: swap (STL/CLR)

Zamění obsah dvou kontejnerů.

### <a name="syntax"></a>Syntaxe

```cpp
void swap(vector<Value>% right);
```

#### <a name="parameters"></a>Parametry

*Kliknutím*<br/>
Kontejner pro prohození obsahu pomocí.

### <a name="remarks"></a>Poznámky

Členská funkce přemění kontrolované sekvence mezi `*this` a *pravou*. Provede to v konstantním čase a nevyvolává žádné výjimky. Použijete ho jako rychlý způsob, jak vyměňovat obsah dvou kontejnerů.

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

## <a name="vectorto_array-stlclr"></a><a name="to_array"></a>Vector:: to_array (STL/CLR)

Zkopíruje řízenou sekvenci do nového pole.

### <a name="syntax"></a>Syntaxe

```cpp
cli::array<Value>^ to_array();
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí pole obsahující řízenou sekvenci. Použijete ho k získání kopie řízené sekvence ve formuláři Array.

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

## <a name="vectorvalue_type-stlclr"></a><a name="value_type"></a>Vector:: value_type (STL/CLR)

Typ prvku

### <a name="syntax"></a>Syntaxe

```cpp
typedef Value value_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro *hodnotu*parametru šablony.

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

## <a name="vectorvector-stlclr"></a><a name="vector"></a>Vector:: Vector (STL/CLR)

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

*count*<br/>
Počet prvků, které mají být vloženy.

*první*<br/>
Začátek rozsahu, který se má vložit

*posledního*<br/>
Konec rozsahu, který má být vložen.

*Kliknutím*<br/>
Objekt nebo rozsah, který chcete vložit.

*počítává*<br/>
Hodnota prvku, který má být vložen.

### <a name="remarks"></a>Poznámky

Konstruktor:

`vector();`

Inicializuje řízenou sekvenci bez prvků. Použijete ji k zadání prázdné počáteční řízené sekvence.

Konstruktor:

`vector(vector<Value>% right);`

Inicializuje řízenou sekvenci pomocí sekvence [`right.begin()`, `right.end()`). Použijete ji k určení počáteční sekvence řízené sekvence, která je kopií sekvence řízené objektem vektoru *vpravo*.

Konstruktor:

`vector(vector<Value>^ right);`

Inicializuje řízenou sekvenci pomocí sekvence [`right->begin()`, `right->end()`). Použijete ji k určení počáteční řízené sekvence, která je kopií sekvence řízené objektem Vector, jejíž popisovač je *pravý*.

Konstruktor:

`explicit vector(size_type count);`

Inicializuje řízenou sekvenci pomocí prvků *Count* s hodnotou `value_type()`. Použijete ho k vyplnění kontejneru všemi prvky, které mají výchozí hodnotu.

Konstruktor:

`vector(size_type count, value_type val);`

Inicializuje řízenou sekvenci pomocí *počtu* elementů s hodnotou *Val*. Použijete ho k vyplnění kontejneru všemi prvky, které mají stejnou hodnotu.

Konstruktor:

`template<typename InIt>`

`vector(InIt first, InIt last);`

Inicializuje řízenou sekvenci pomocí sekvence [`first`, `last`). Použijete ho k tomu, aby řízená sekvence kopírovala jinou sekvenci.

Konstruktor:

`vector(System::Collections::Generic::IEnumerable<Value>^ right);`

Inicializuje řízenou sekvenci sekvencí, která je určena *přípravou*výčtu. Použijete ho k tomu, aby řízená sekvence zkopírovala jinou sekvenci popsanou enumerátorem.

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

## <a name="operator-vector-stlclr"></a><a name="op_neq"></a>operator! = (Vector) – operátor (STL/CLR)

Vektor se neshoduje s porovnáním.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Value>
    bool operator!=(vector<Value>% left,
        vector<Value>% right);
```

#### <a name="parameters"></a>Parametry

*zbývá*<br/>
Levý kontejner, který se má porovnat

*Kliknutím*<br/>
Pravý kontejner, který se má porovnat

### <a name="remarks"></a>Poznámky

Funkce operátoru vrací `!(left == right)`. Použijete ji k otestování, zda *Left* není seřazena stejně jako *právo* , pokud jsou tyto dva vektory porovnány s prvkem podle elementu.

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

## <a name="operatorlt-vector-stlclr"></a><a name="op_lt"></a>operator&lt; (Vector) – operátor (STL/CLR)

Vektor menší než porovnání.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Value>
    bool operator<(vector<Value>% left,
        vector<Value>% right);
```

#### <a name="parameters"></a>Parametry

*zbývá*<br/>
Levý kontejner, který se má porovnat

*Kliknutím*<br/>
Pravý kontejner, který se má porovnat

### <a name="remarks"></a>Poznámky

Funkce operator vrátí hodnotu true, pokud `i` nejnižší pozice, pro kterou `!(right[i] < left[i])` je také true `left[i] < right[i]`. V opačném případě vrátí `left->size() < right->size()` použijete k otestování, *zda je* před *pravou* seřazena druhá vektory, pokud jsou tyto dva vektory porovnány elementem.

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

## <a name="operatorlt-vector-stlclr"></a><a name="op_lteq"></a>operator&lt;= (Vector) – operátor (STL/CLR)

Vektor, který je menší nebo roven porovnání.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Value>
    bool operator<=(vector<Value>% left,
        vector<Value>% right);
```

#### <a name="parameters"></a>Parametry

*zbývá*<br/>
Levý kontejner, který se má porovnat

*Kliknutím*<br/>
Pravý kontejner, který se má porovnat

### <a name="remarks"></a>Poznámky

Funkce operátoru vrací `!(right < left)`. Použijete ho k otestování *, jestli není* po *pravé straně* , když jsou tyto dva vektory porovnány, na prvek podle elementu.

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

## <a name="operator-vector-stlclr"></a><a name="op_eq"></a>operator = = (Vector) – operátor (STL/CLR)

Stejné porovnání vektoru

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Value>
    bool operator==(vector<Value>% left,
        vector<Value>% right);
```

#### <a name="parameters"></a>Parametry

*zbývá*<br/>
Levý kontejner, který se má porovnat

*Kliknutím*<br/>
Pravý kontejner, který se má porovnat

### <a name="remarks"></a>Poznámky

Funkce operator vrátí hodnotu true pouze v případě, že sekvence řízené *levou* a *pravou* mají stejnou délku a pro každou pozici `i``left[i] ==` `right[i]`. Použijete ji k otestování, zda je *levé* řazení stejné jako *pravé* , pokud jsou dva vektory porovnány s prvkem podle prvku.

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

## <a name="operatorgt-vector-stlclr"></a><a name="op_gt"></a>operator&gt; (Vector) – operátor (STL/CLR)

Vektor větší než porovnání

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Value>
    bool operator>(vector<Value>% left,
        vector<Value>% right);
```

#### <a name="parameters"></a>Parametry

*zbývá*<br/>
Levý kontejner, který se má porovnat

*Kliknutím*<br/>
Pravý kontejner, který se má porovnat

### <a name="remarks"></a>Poznámky

Funkce operator vrací `right` `<` `left`. Použijete ji k otestování *, zda je* po *pravé* době řazení dvou vektorů porovnány prvky podle prvku.

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

## <a name="operatorgt-vector-stlclr"></a><a name="op_gteq"></a>operator&gt;= (Vector) – operátor (STL/CLR)

Vektor, který je větší než nebo rovno porovnání

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Value>
    bool operator>=(vector<Value>% left,
        vector<Value>% right);
```

#### <a name="parameters"></a>Parametry

*zbývá*<br/>
Levý kontejner, který se má porovnat

*Kliknutím*<br/>
Pravý kontejner, který se má porovnat

### <a name="remarks"></a>Poznámky

Funkce operátoru vrací `!(left < right)`. Použijete ji k otestování, zda je *ponecháno* před *pravou* , pokud jsou tyto dva vektory porovnány podle elementu.

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
