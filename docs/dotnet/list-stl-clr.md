---
title: list (STL/CLR)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cliext::list
- cliext::list::assign
- cliext::list::assign
- cliext::list::back
- cliext::list::back_item
- cliext::list::begin
- cliext::list::clear
- cliext::list::const_iterator
- cliext::list::const_reference
- cliext::list::const_reverse_iterator
- cliext::list::difference_type
- cliext::list::empty
- cliext::list::end
- cliext::list::erase
- cliext::list::front
- cliext::list::front_item
- cliext::list::generic_container
- cliext::list::generic_iterator
- cliext::list::generic_reverse_iterator
- cliext::list::generic_value
- cliext::list::insert
- cliext::list::iterator
- cliext::list::list
- cliext::list::merge
- cliext::list::operator=
- cliext::list::pop_back
- cliext::list::pop_front
- cliext::list::push_back
- cliext::list::push_front
- cliext::list::rbegin
- cliext::list::reference
- cliext::list::remove
- cliext::list::remove_if
- cliext::list::rend
- cliext::list::resize
- cliext::list::reverse
- cliext::list::reverse_iterator
- cliext::list::size
- cliext::list::size_type
- cliext::list::sort
- cliext::list::splice
- cliext::list::swap
- cliext::list::to_array
- cliext::list::unique
- cliext::list::value_type
- cliext::operator!=(list)
- cliext::operator<(list)
- cliext::operator<=(list)
- cliext::operator==(list)
- cliext::operator>(list)
- cliext::operator>=(list)
helpviewer_keywords:
- <cliext/list> header [STL/CLR]
- list class [STL/CLR]
- <list> header [STL/CLR]
- assign member [STL/CLR]
- assign member [STL/CLR]
- back member [STL/CLR]
- back_item member [STL/CLR]
- begin member [STL/CLR]
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
- list member [STL/CLR]
- merge member [STL/CLR]
- operator= member [STL/CLR]
- pop_back member [STL/CLR]
- pop_front member [STL/CLR]
- push_back member [STL/CLR]
- push_front member [STL/CLR]
- rbegin member [STL/CLR]
- reference member [STL/CLR]
- remove member [STL/CLR]
- remove_if member [STL/CLR]
- rend member [STL/CLR]
- resize member [STL/CLR]
- reverse member [STL/CLR]
- reverse_iterator member [STL/CLR]
- size member [STL/CLR]
- size_type member [STL/CLR]
- sort member [STL/CLR]
- splice member [STL/CLR]
- swap member [STL/CLR]
- to_array member [STL/CLR]
- unique member [STL/CLR]
- value_type member [STL/CLR]
- operator!=(list) member [STL/CLR]
- operator<(list) member [STL/CLR]
- operator<=(list) member [STL/CLR]
- operator==(list) member [STL/CLR]
- operator>(list) member [STL/CLR]
- operator>=(list) member [STL/CLR]
ms.assetid: a70c45c8-a257-4f6b-8434-b27ff6685bac
ms.openlocfilehash: 8350e8b7036731cf3e09b9ce26278b2a656d80be
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50569582"
---
# <a name="list-stlclr"></a>list (STL/CLR)

Třída šablony popisuje objekt, který řídí různé délky sekvence elementů, která má obousměrný přístup. Použití kontejneru `list` , spravovat řadu prvků, jako obousměrný propojený seznam uzlů, každý ukládání jeden element.

V popisu níže `GValue` je stejný jako *hodnotu* Pokud je typ odkazu, v takovém případě je `Value^`.

## <a name="syntax"></a>Syntaxe

```cpp
template<typename Value>
    ref class list
        :   public
        System::ICloneable,
        System::Collections::IEnumerable,
        System::Collections::ICollection,
        System::Collections::Generic::IEnumerable<GValue>,
        System::Collections::Generic::ICollection<GValue>,
        Microsoft::VisualC::StlClr::IList<GValue>
    { ..... };
```

### <a name="parameters"></a>Parametry

*Hodnota*<br/>
Typ elementu v řízené sekvenci

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<cliext – / list >

**Namespace:** cliext –

## <a name="declarations"></a>Deklarace

|Definice typu|Popis|
|---------------------|-----------------|
|[list::const_iterator (STL/CLR)](#const_iterator)|Typ konstantního iterátoru řízené sekvence|
|[list::const_reference (STL/CLR)](#const_reference)|Typ konstantního odkazu na prvek|
|[list::const_reverse_iterator (STL/CLR)](#const_reverse_iterator)|Typ konstantního zpětného iterátoru řízené sekvence.|
|[list::difference_type (STL/CLR)](#difference_type)|Typ vzdálenosti se znaménkem mezi dvěma prvky|
|[list::generic_container (STL/CLR)](#generic_container)|Typ obecné rozhraní pro kontejner.|
|[list::generic_iterator (STL/CLR)](#generic_iterator)|Typ iterátoru pro obecné rozhraní pro kontejner.|
|[list::generic_reverse_iterator (STL/CLR)](#generic_reverse_iterator)|Typ "reverse iterator" pro obecné rozhraní pro kontejner.|
|[list::generic_value (STL/CLR)](#generic_value)|Typ elementu pro obecné rozhraní pro kontejner.|
|[list::iterator (STL/CLR)](#iterator)|Typ iterátoru řízené sekvence|
|[list::reference (STL/CLR)](#reference)|Typ odkazu na prvek|
|[list::reverse_iterator (STL/CLR)](#reverse_iterator)|Typ "reverse iterator" pro řízenou sekvenci.|
|[list::size_type (STL/CLR)](#size_type)|Typ vzdálenosti se znaménkem mezi dvěma prvky|
|[list::value_type (STL/CLR)](#value_type)|Typ prvku|

|Členská funkce|Popis|
|---------------------|-----------------|
|[list::assign (STL/CLR)](#assign)|Nahradí všechny elementy.|
|[list::back (STL/CLR)](#back)|Přistupuje k poslední prvek.|
|[list::begin (STL/CLR)](#begin)|Určuje začátek řízené sekvence.|
|[list::clear (STL/CLR)](#clear)|Odebere všechny prvky.|
|[list::empty (STL/CLR)](#empty)|Zkouší, zda nejsou přítomny žádné prvky.|
|[list::end (STL/CLR)](#end)|Určuje konec řízené sekvence.|
|[list::erase (STL/CLR)](#erase)|Odebere prvky v určených pozicích.|
|[list::front (STL/CLR)](#front)|Přistupuje k první prvek.|
|[list::insert (STL/CLR)](#insert)|Přidá prvky na zadané pozici.|
|[list::list (STL/CLR)](#list)|Sestaví objekt kontejneru.|
|[list::merge (STL/CLR)](#merge)|Sloučí dvě seřazené řízené sekvence.|
|[list::pop_back (STL/CLR)](#pop_back)|Odstraní poslední prvek.|
|[list::pop_front (STL/CLR)](#pop_front)|Odebere první prvek.|
|[list::push_back (STL/CLR)](#push_back)|Přidá nový poslední prvek.|
|[list::push_front (STL/CLR)](#push_front)|Přidá nový prvek první.|
|[list::rbegin (STL/CLR)](#rbegin)|Určuje začátek řízené obrácené sekvenci.|
|[list::remove (STL/CLR)](#remove)|Odebere element se zadanou hodnotou.|
|[list::remove_if (STL/CLR)](#remove_if)|Odebere prvky, které předávají zadaný testovací.|
|[list::rend (STL/CLR)](#rend)|Určuje konec řízené obrácené sekvenci.|
|[list::resize (STL/CLR)](#resize)|Počet prvků, které se změní.|
|[list::reverse (STL/CLR)](#reverse)|Obrátí řízené sekvence.|
|[list::size (STL/CLR)](#size)|Spočítá počet prvků.|
|[list::sort (STL/CLR)](#sort)|Seřadí řízené sekvence.|
|[list::splice (STL/CLR)](#splice)|Restitches propojení mezi uzly.|
|[list::swap (STL/CLR)](#swap)|Zamění obsah dvou kontejnerů.|
|[list::to_array (STL/CLR)](#to_array)|Zkopíruje do nového pole řízené sekvence.|
|[list::unique (STL/CLR)](#unique)|Odebere sousedící prvky, které předávají zadaný testovací.|

|Vlastnost|Popis|
|--------------|-----------------|
|[list::back_item (STL/CLR)](#back_item)|Přistupuje k poslední prvek.|
|[list::front_item (STL/CLR)](#front_item)|Přistupuje k první prvek.|

|Operátor|Popis|
|--------------|-----------------|
|[list::operator= (STL/CLR)](#op_as)|Nahradí řízené sekvence.|
|[operator!= (list) (STL/CLR)](#op_neq)|Určuje, zda `list` není roven jinému objektu `list` objektu.|
|[operator< (list) (STL/CLR)](#op_lt)|Určuje, zda `list` je menší než jiný objekt `list` objektu.|
|[operator<= (list) (STL/CLR)](#op_lteq)|Určuje, zda `list` objekt je menší nebo rovna jiné `list` objektu.|
|[operator== (list) (STL/CLR)](#op_eq)|Určuje, zda `list` je roven jinému objektu `list` objektu.|
|[operator> (list) (STL/CLR)](#op_gt)|Určuje, zda `list` je větší než jiný objekt `list` objektu.|
|[operator>= (list) (STL/CLR)](#op_gteq)|Určuje, zda `list` objekt je větší než nebo roven jinému `list` objektu.|

## <a name="interfaces"></a>Rozhraní

|Rozhraní|Popis|
|---------------|-----------------|
|<xref:System.ICloneable>|Duplicitní objektu.|
|<xref:System.Collections.IEnumerable>|Pořadí mezi prvky.|
|<xref:System.Collections.ICollection>|Údržba skupiny prvků.|
|<xref:System.Collections.Generic.IEnumerable%601>|Pořadí pomocí zadané elementy.|
|<xref:System.Collections.Generic.ICollection%601>|Údržba skupiny zadané elementy.|
|IList\<hodnotu >|Udržujte obecný kontejneru.|

## <a name="remarks"></a>Poznámky

Objekt přiděluje a uvolňuje úložiště pro ovládací prvky jako jednotlivým uzlům v seznamu odkazů obousměrné pořadí. Ho znovu uspořádá prvky změnou vazby mezi uzly, nikdy zkopírováním obsah jednoho uzlu do jiného. To znamená, že můžete vložit a odebrat elementy volně bez narušení zbývající prvky. Díky tomu se seznam je vhodným kandidátem pro základní kontejner pro třídu šablony [fronty (STL/CLR)](../dotnet/queue-stl-clr.md) nebo třída šablony [zásobníku (STL/CLR)](../dotnet/stack-stl-clr.md).

A `list` objekt podporuje obousměrné iterátory, což znamená, že přejdete na sousedící prvky zadaný iterátor, který určuje elementu v řízené sekvenci. Speciální hlavního uzlu odpovídá iterátorů vrácené [list::end (STL/CLR)](../dotnet/list-end-stl-clr.md)`()`. Tento iterátor, který má přístup po posledním prvku v řízené sekvenci lze snížit, pokud jsou k dispozici. Můžete zvýšit seznamu iterátor pro přístup k hlavnímu uzlu a budou pak porovnat rovna `end()`. Nelze přistoupit přes ukazatel vrátí iterátor, ale `end()`.

Všimněte si, že nemůže odkazovat na prvek seznamu přímo zadané pozici číselné –, který vyžaduje iterátor náhodného přístupu. Takže seznam *není* použít jako základní kontejner šablony třídy [priority_queue – (STL/CLR)](../dotnet/priority-queue-stl-clr.md).

Iterátor seznamu uloží popisovač do uzlu přidružený seznam, který je pak uloží popisovač pro jeho přiřazeným kontejnerem. Iterátory lze použít pouze objekty, které přiřazeným kontejnerem. Iterátor seznamu je platná tak dlouho, dokud jeho přidružený seznam uzlu souvisí s některé seznamu. Kromě toho je platný iterátoru přesměrovat – slouží k přístupu nebo změnit hodnotu prvku jmenuje--tak dlouho, dokud se nerovná `end()`.

Smazání nebo odstranění prvku volá destruktor pro jeho uložené hodnotě. Zničení kontejneru vymaže všechny prvky. Kontejner, jehož typ prvku je třídy ref class tak, zajišťuje, že žádné elementy něj kontejneru. Mějte na paměti, ale, že kontejner zpracovává nemá *není* zničit jeho prvků.

## <a name="members"></a>Členové

## <a name="assign"></a> list::Assign (STL/CLR)

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
// cliext_list_assign.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // assign a repetition of values
    cliext::list<wchar_t> c2;
    c2.assign(6, L'x');
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign an iterator range
    cliext::list<wchar_t>::iterator it = c1.end();
    c2.assign(c1.begin(), --it);
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

## <a name="back"></a> list::back (STL/CLR)

Přistupuje k poslední prvek.

### <a name="syntax"></a>Syntaxe

```cpp
reference back();
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí odkaz na poslední prvek řízené sekvence, která musí být neprázdný. Použijete ho pro přístup k posledního prvku, když víte, že existuje.

### <a name="example"></a>Příklad

```cpp
// cliext_list_back.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
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

## <a name="back_item"></a> list::back_item (STL/CLR)

Přistupuje k poslední prvek.

### <a name="syntax"></a>Syntaxe

```cpp
property value_type back_item;
```

### <a name="remarks"></a>Poznámky

Vlastnost má přístup k poslední prvek řízené sekvence, která musí být neprázdný. Můžete použít ke čtení nebo zápisu posledního prvku, když víte, že existuje.

### <a name="example"></a>Příklad

```cpp
// cliext_list_back_item.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
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

## <a name="begin"></a> list::begin (STL/CLR)

Určuje začátek řízené sekvence.

### <a name="syntax"></a>Syntaxe

```cpp
iterator begin();
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí iterátor náhodného přístupu, který určuje první prvek řízenou sekvenci nebo přesně za konec k prázdné sekvenci. Můžete ji použít k získání iterátor, který určuje `current` začátek řízené sekvence, ale jeho stav můžete změnit, pokud se změní délka řízené sekvence.

### <a name="example"></a>Příklad

```cpp
// cliext_list_begin.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect first two items
    cliext::list<wchar_t>::iterator it = c1.begin();
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

## <a name="clear"></a> list::clear (STL/CLR)

Odebere všechny prvky.

### <a name="syntax"></a>Syntaxe

```cpp
void clear();
```

### <a name="remarks"></a>Poznámky

Členská funkce efektivně volá [list::erase (STL/CLR)](../dotnet/list-erase-stl-clr.md) `(` [list::begin (STL/CLR)](../dotnet/list-begin-stl-clr.md) `(),` [list::end (STL/CLR)](../dotnet/list-end-stl-clr.md) `())`. Použijete ji k zajištění, že je prázdná řízené sekvence.

### <a name="example"></a>Příklad

```cpp
// cliext_list_clear.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
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

## <a name="const_iterator"></a> list::const_iterator (STL/CLR)

Typ konstantního iterátoru řízené sekvence

### <a name="syntax"></a>Syntaxe

```cpp
typedef T2 const_iterator;
```

### <a name="remarks"></a>Poznámky

Typ popisuje objekt neurčeného typu `T2` , který může sloužit jako konstantní iterátor s náhodným přístupem řízené sekvence.

### <a name="example"></a>Příklad

```cpp
// cliext_list_const_iterator.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    cliext::list<wchar_t>::const_iterator cit = c1.begin();
    for (; cit != c1.end(); ++cit)
        System::Console::Write("{0} ", *cit);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="const_reference"></a> list::const_reference (STL/CLR)

Typ konstantního odkazu na prvek

### <a name="syntax"></a>Syntaxe

```cpp
typedef value_type% const_reference;
```

### <a name="remarks"></a>Poznámky

Typ, který popisuje konstantní odkaz na element.

### <a name="example"></a>Příklad

```cpp
// cliext_list_const_reference.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    cliext::list<wchar_t>::const_iterator cit = c1.begin();
    for (; cit != c1.end(); ++cit)
        {   // get a const reference to an element
        cliext::list<wchar_t>::const_reference cref = *cit;
        System::Console::Write("{0} ", cref);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="const_reverse_iterator"></a> list::const_reverse_iterator (STL/CLR)

Typ konstantního zpětného iterátoru řízené sekvence...

### <a name="syntax"></a>Syntaxe

```cpp
typedef T4 const_reverse_iterator;
```

### <a name="remarks"></a>Poznámky

Typ popisuje objekt neurčeného typu `T4` , který může sloužit jako konstantní zpětného iterátoru řízené sekvence.

### <a name="example"></a>Příklad

```cpp
// cliext_list_const_reverse_iterator.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c" reversed
    cliext::list<wchar_t>::const_reverse_iterator crit = c1.rbegin();
    cliext::list<wchar_t>::const_reverse_iterator crend = c1.rend();
    for (; crit != crend; ++crit)
        System::Console::Write("{0} ", *crit);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c b a
```

## <a name="difference_type"></a> list::difference_type (STL/CLR)

Typ vzdálenosti se znaménkem mezi dvěma prvky.

### <a name="syntax"></a>Syntaxe

```cpp
typedef int difference_type;
```

### <a name="remarks"></a>Poznámky

Typ, který popisuje počet podepsaný prvků.

### <a name="example"></a>Příklad

```cpp
// cliext_list_difference_type.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // compute positive difference
    cliext::list<wchar_t>::difference_type diff = 0;
    for (cliext::list<wchar_t>::iterator it = c1.begin();
        it != c1.end(); ++it) ++diff;
    System::Console::WriteLine("end()-begin() = {0}", diff);

    // compute negative difference
    diff = 0;
    for (cliext::list<wchar_t>::iterator it = c1.end();
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

## <a name="empty"></a> list::Empty (STL/CLR)

Zkouší, zda nejsou přítomny žádné prvky.

### <a name="syntax"></a>Syntaxe

```cpp
bool empty();
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí hodnotu true pro prázdnou řízenou sekvenci. Je ekvivalentní [list::size (STL/CLR)](../dotnet/list-size-stl-clr.md)`() == 0`. Použijete ji k ověření, zda je seznam prázdný.

### <a name="example"></a>Příklad

```cpp
// cliext_list_empty.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
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

## <a name="end"></a> list::end (STL/CLR)

Určuje konec řízené sekvence.

### <a name="syntax"></a>Syntaxe

```cpp
iterator end();
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí iterátor náhodného přístupu, na kterou odkazuje přesně za konec řízené sekvence. Můžete ji použít k získání iterátor, který určuje konec řízené sekvence; jeho stav kódu ne změnit, pokud se změní délka řízené sekvence.

### <a name="example"></a>Příklad

```cpp
// cliext_list_end.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect last two items
    cliext::list<wchar_t>::iterator it = c1.end();
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

## <a name="erase"></a> list::Erase (STL/CLR)

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

Obě členské funkce vrátí iterátor, který určuje první prvek zbývající za všemi odstraněnými prvky, nebo [list::end (STL/CLR)](../dotnet/list-end-stl-clr.md) `()` Pokud žádný takový prvek neexistuje.

Při mazání prvků, je počet kopií prvku lineární v počtu prvků mezi koncem mazání a bližšího konci sekvence. (Při mazání jeden nebo více prvků na jednom konci pořadí, žádný element kopie nastat.)

### <a name="example"></a>Příklad

```cpp
// cliext_list_erase.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
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
    cliext::list<wchar_t>::iterator it = c1.end();
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

## <a name="front"></a> list::front (STL/CLR)

Přistupuje k první prvek.

### <a name="syntax"></a>Syntaxe

```cpp
reference front();
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí odkaz na první prvek řízené sekvence, která musí být neprázdný. Můžete použít ke čtení nebo zápisu prvního prvku, když víte, že existuje.

### <a name="example"></a>Příklad

```cpp
// cliext_list_front.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
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

## <a name="front_item"></a> list::front_item (STL/CLR)

Přistupuje k první prvek.

### <a name="syntax"></a>Syntaxe

```cpp
property value_type front_item;
```

### <a name="remarks"></a>Poznámky

Vlastnost přistupuje k první prvek řízené sekvence, která musí být neprázdný. Můžete použít ke čtení nebo zápisu prvního prvku, když víte, že existuje.

### <a name="example"></a>Příklad

```cpp
// cliext_list_front_item.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
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

## <a name="generic_container"></a> list::generic_container (STL/CLR)

Typ obecné rozhraní pro kontejner.

### <a name="syntax"></a>Syntaxe

```cpp
typedef Microsoft::VisualC::StlClr::
    IList<generic_value>
    generic_container;
```

### <a name="remarks"></a>Poznámky

Typ, který popisuje obecné rozhraní pro tuto třídu šablony kontejneru.

### <a name="example"></a>Příklad

```cpp
// cliext_list_generic_container.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct a generic container
    cliext::list<wchar_t>::generic_container^ gc1 = %c1;
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

## <a name="generic_iterator"></a> list::generic_iterator (STL/CLR)

Typ iterátoru pro použití s obecné rozhraní pro kontejner.

### <a name="syntax"></a>Syntaxe

```cpp
typedef Microsoft::VisualC::StlClr::Generic::
    ContainerBidirectionalIterator<generic_value>
    generic_iterator;
```

### <a name="remarks"></a>Poznámky

Typ, který popisuje obecný iterátoru, který jde použít s obecné rozhraní pro tuto třídu šablony kontejneru.

### <a name="example"></a>Příklad

```cpp
// cliext_list_generic_iterator.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct a generic container
    cliext::list<wchar_t>::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // modify generic and display original
    cliext::list<wchar_t>::generic_iterator gcit = gc1->begin();
    cliext::list<wchar_t>::generic_value gcval = *gcit;
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

## <a name="generic_reverse_iterator"></a> list::generic_reverse_iterator (STL/CLR)

Typ "reverse iterator" pro použití s obecné rozhraní pro kontejner.

### <a name="syntax"></a>Syntaxe

```cpp
typedef Microsoft::VisualC::StlClr::Generic::
    ReverseBidirectionalIterator<generic_value> generic_reverse_iterator;
```

### <a name="remarks"></a>Poznámky

Typ, který popisuje obecný zpětný iterátor, který jde použít s obecné rozhraní pro tuto třídu šablony kontejneru.

### <a name="example"></a>Příklad

```cpp
// cliext_list_generic_reverse_iterator.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct a generic container
    cliext::list<wchar_t>::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // modify generic and display original
    cliext::list<wchar_t>::generic_reverse_iterator gcit = gc1->rbegin();
    cliext::list<wchar_t>::generic_value gcval = *gcit;
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

## <a name="generic_value"></a> list::generic_value (STL/CLR)

Typ elementu pro použití s obecné rozhraní pro kontejner.

### <a name="syntax"></a>Syntaxe

```cpp
typedef GValue generic_value;
```

### <a name="remarks"></a>Poznámky

Typ, který popisuje objekt typu `GValue` hodnoty uložené elementu pro použití s obecné rozhraní pro tuto třídu šablony kontejneru, který popisuje.

### <a name="example"></a>Příklad

```cpp
// cliext_list_generic_value.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct a generic container
    cliext::list<wchar_t>::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // modify generic and display original
    cliext::list<wchar_t>::generic_iterator gcit = gc1->begin();
    cliext::list<wchar_t>::generic_value gcval = *gcit;
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

## <a name="insert"></a> list::Insert (STL/CLR)

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
// cliext_list_insert.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // insert a single value using iterator
    cliext::list<wchar_t>::iterator it = c1.begin();
    System::Console::WriteLine("insert(begin()+1, L'x') = {0}",
        *c1.insert(++it, L'x'));
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // insert a repetition of values
    cliext::list<wchar_t> c2;
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

    // insert a single value using index
    it = c2.begin();
    ++it, ++it, ++it;
    c2.insert(it, L'z');
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

## <a name="iterator"></a> list::iterator (STL/CLR)

Typ iterátoru řízené sekvence

### <a name="syntax"></a>Syntaxe

```cpp
typedef T1 iterator;
```

### <a name="remarks"></a>Poznámky

Typ popisuje objekt neurčeného typu `T1` , který může sloužit jako iterátor náhodného přístupu řízené sekvence.

### <a name="example"></a>Příklad

```cpp
// cliext_list_iterator.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    cliext::list<wchar_t>::iterator it = c1.begin();
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

## <a name="list"></a> list::list (STL/CLR)

Sestaví objekt kontejneru.

### <a name="syntax"></a>Syntaxe

```cpp
list();
list(list<Value>% right);
list(list<Value>^ right);
explicit list(size_type count);
list(size_type count, value_type val);
template<typename InIt>
    list(InIt first, InIt last);
list(System::Collections::Generic::IEnumerable<Value>^ right);
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

`list();`

Inicializuje se žádné prvky řízené sekvence. Použijete ji k určení počáteční prázdnou řízenou sekvenci.

Konstruktor:

`list(list<Value>% right);`

Inicializuje řízené sekvence s pořadím [`right.begin()`, `right.end()`). Můžete ji použít k určení počáteční řízené sekvence, který je kopii sekvence řízenou objektem seznamu *správné*.

Konstruktor:

`list(list<Value>^ right);`

Inicializuje řízené sekvence s pořadím [`right->begin()`, `right->end()`). Můžete ji použít k určení počáteční řízené sekvence, který je kopii sekvence řízenou objektem seznamu, jehož popisovač je *správné*.

Konstruktor:

`explicit list(size_type count);`

Inicializuje řízené sekvence s *počet* elementy s hodnotou `value_type()`. Použijete ji k vyplnilo kontejner s prvky všechny mají výchozí hodnotu.

Konstruktor:

`list(size_type count, value_type val);`

Inicializuje řízené sekvence s *počet* elementy s hodnotou *val*. Použijete ji k vyplnilo kontejner s prvky všechny mají stejnou hodnotu.

Konstruktor:

`template<typename InIt>`

`list(InIt first, InIt last);`

Inicializuje řízené sekvence s pořadím [`first`, `last`). Použijte k vytvoření kopie jiné pořadí řízené sekvence.

Konstruktor:

`list(System::Collections::Generic::IEnumerable<Value>^ right);`

Inicializuje řízené sekvence s pořadí určeném enumerátor *správné*. Použijete ji k vytvoření kopie jiné pořadí popsal enumerátor řízené sekvence.

### <a name="example"></a>Příklad

```cpp
// cliext_list_construct.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
// construct an empty container
    cliext::list<wchar_t> c1;
    System::Console::WriteLine("size() = {0}", c1.size());

    // construct with a repetition of default values
    cliext::list<wchar_t> c2(3);
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", (int)elem);
    System::Console::WriteLine();

    // construct with a repetition of values
    cliext::list<wchar_t> c3(6, L'x');
    for each (wchar_t elem in c3)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an iterator range
    cliext::list<wchar_t>::iterator it = c3.end();
    cliext::list<wchar_t> c4(c3.begin(), --it);
    for each (wchar_t elem in c4)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an enumeration
    cliext::list<wchar_t> c5(   // NOTE: cast is not needed
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3);
    for each (wchar_t elem in c5)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct by copying another container
    cliext::list<wchar_t> c7(c3);
    for each (wchar_t elem in c7)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct by copying a container handle
    cliext::list<wchar_t> c8(%c3);
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

## <a name="merge"></a> list::merge (STL/CLR)

Sloučí dvě seřazené řízené sekvence.

### <a name="syntax"></a>Syntaxe

```cpp
void merge(list<Value>% right);
template<typename Pred2>
    void merge(list<Value>% right, Pred2 pred);
```

#### <a name="parameters"></a>Parametry

*Před*<br/>
Procedura pro prvek dvojice.

*doprava*<br/>
Sloučení v kontejneru.

### <a name="remarks"></a>Poznámky

První členská funkce odebere všechny prvky ze sekvence řízenou parametrem *správné* a vložit je do řízené sekvence. Oba pořadí musí být dříve seřazené podle `operator<` – elementy se nesmí zmenšovat v hodnotě po absolvování buď pořadí. Výsledné pořadí je také seřazené podle `operator<`. Tuto funkci člena můžete použít ke sloučení dvou sekvencí, které zvyšují v hodnotě v sekvenci, která se také zvýší v hodnotě.

Druhá členská funkce se chová stejně jako první, s tím rozdílem, že sekvence jsou řazeny podle `pred`  --  `pred(X, Y)` musí mít hodnotu false pro libovolný element `X` , který následuje prvku `Y` v sekvenci. Použijete ji chcete-li sloučit dvě pořadí řazení podle funkce predikátu nebo delegát, který zadáte.

Jak funkce provést stabilní sloučení – žádná dvojice prvků v některém z původní řízené sekvence je obrácený ve výsledné řízené sekvence. Navíc pokud dvojici prvků `X` a `Y` ve výsledné řízené sekvence má stejné pořadí – `!(X < Y) && !(X < Y)` – prvek z původní řízené sekvence se zobrazí před elementem ze sekvence řízenou parametrem *správné*.

### <a name="example"></a>Příklad

```cpp
// cliext_list_merge.cpp
// compile with: /clr
#include <cliext/list>

typedef cliext::list<wchar_t> Mylist;
int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'c');
    c1.push_back(L'e');

    // display initial contents " a c e"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    cliext::list<wchar_t> c2;
    c2.push_back(L'b');
    c2.push_back(L'd');
    c2.push_back(L'f');

    // display initial contents " b d f"
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // merge and display
    cliext::list<wchar_t> c3(c1);
    c3.merge(c2);
    for each (wchar_t elem in c3)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    System::Console::WriteLine("c2.size() = {0}", c2.size());

    // sort descending, merge descending, and redisplay
    c1.sort(cliext::greater<wchar_t>());
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    c3.sort(cliext::greater<wchar_t>());
    for each (wchar_t elem in c3)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    c3.merge(c1, cliext::greater<wchar_t>());
    for each (wchar_t elem in c3)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    System::Console::WriteLine("c1.size() = {0}", c1.size());
    return (0);
    }
```

```Output
a c e
b d f
a b c d e f
c2.size() = 0
e c a
f e d c b a
f e e d c c b a a
c1.size() = 0
```

## <a name="op_as"></a> list::Operator = (STL/CLR)

Nahradí řízené sekvence.

### <a name="syntax"></a>Syntaxe

```
list<Value>% operator=(list<Value>% right);
```

#### <a name="parameters"></a>Parametry

*doprava*<br/>
Kontejner pro kopírování.

### <a name="remarks"></a>Poznámky

Kopie členský operátor *správné* na objekt, vrátí `*this`. Můžete použít k nahraďte kopii řízené sekvence v řízené sekvenci *správné*.

### <a name="example"></a>Příklad

```cpp
// cliext_list_operator_as.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    cliext::list<wchar_t> c2;
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

## <a name="pop_back"></a> list::pop_back (STL/CLR)

Odstraní poslední prvek.

### <a name="syntax"></a>Syntaxe

```cpp
void pop_back();
```

### <a name="remarks"></a>Poznámky

Členská funkce odstraní poslední prvek řízené sekvence, která musí být neprázdný. Použijte ke zkrácení seznamu jeden element na pozadí.

### <a name="example"></a>Příklad

```cpp
// cliext_list_pop_back.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
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

## <a name="pop_front"></a> list::pop_front (STL/CLR)

Odebere první prvek.

### <a name="syntax"></a>Syntaxe

```cpp
void pop_front();
```

### <a name="remarks"></a>Poznámky

Členská funkce odstraní první prvek řízené sekvence, která musí být neprázdný. Použijte ke zkrácení seznamu jeden prvek v popředí.

### <a name="example"></a>Příklad

```cpp
// cliext_list_pop_front.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // pop an element and redisplay
    c1.pop_front();
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
b c
```

## <a name="push_back"></a> list::push_back (STL/CLR)

Přidá nový poslední prvek.

### <a name="syntax"></a>Syntaxe

```cpp
void push_back(value_type val);
```

### <a name="remarks"></a>Poznámky

Členská funkce vloží prvek s hodnotou `val` na konci řízené sekvence. Můžete použít k připojení jiný element do seznamu.

### <a name="example"></a>Příklad

```cpp
// cliext_list_push_back.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
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

## <a name="push_front"></a> list::push_front (STL/CLR)

Přidá nový prvek první.

### <a name="syntax"></a>Syntaxe

```cpp
void push_front(value_type val);
```

### <a name="remarks"></a>Poznámky

Členská funkce vloží prvek s hodnotou `val` na začátek řízené sekvence. Použijete ji k předřaďte jiný element do seznamu.

### <a name="example"></a>Příklad

```cpp
// cliext_list_push_front.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_front(L'a');
    c1.push_front(L'b');
    c1.push_front(L'c');

    // display contents " c b a"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c b a
```

## <a name="rbegin"></a> list::rbegin (STL/CLR)

Určuje začátek řízené obrácené sekvenci.

### <a name="syntax"></a>Syntaxe

```cpp
reverse_iterator rbegin();
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí zpětný iterátor, který určuje poslední prvek řízenou sekvenci nebo hned za začátku k prázdné sekvenci. Proto, označí `beginning` reverzní pořadí. Můžete ji použít k získání iterátor, který určuje `current` začátek řízené sekvence viděli v obráceném pořadí, ale jeho stav můžete změnit, pokud se změní délka řízené sekvence.

### <a name="example"></a>Příklad

```cpp
// cliext_list_rbegin.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect first two items in reversed sequence
    cliext::list<wchar_t>::reverse_iterator rit = c1.rbegin();
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

## <a name="reference"></a> list::Reference (STL/CLR)

Typ odkazu na prvek

### <a name="syntax"></a>Syntaxe

```cpp
typedef value_type% reference;
```

### <a name="remarks"></a>Poznámky

Typ, který popisuje odkaz na element.

### <a name="example"></a>Příklad

```cpp
// cliext_list_reference.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    cliext::list<wchar_t>::iterator it = c1.begin();
    for (; it != c1.end(); ++it)
        {   // get a reference to an element
        cliext::list<wchar_t>::reference ref = *it;
        System::Console::Write("{0} ", ref);
        }
    System::Console::WriteLine();

    // modify contents " a b c"
    for (it = c1.begin(); it != c1.end(); ++it)
        {   // get a reference to an element
        cliext::list<wchar_t>::reference ref = *it;

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

## <a name="remove"></a> list::Remove (STL/CLR)

Odebere element se zadanou hodnotou.

### <a name="syntax"></a>Syntaxe

```cpp
void remove(value_type val);
```

#### <a name="parameters"></a>Parametry

*Val*<br/>
Hodnota elementu, který chcete odebrat.

### <a name="remarks"></a>Poznámky

Členská funkce odstraní prvek v řízené sekvenci, pro kterou `((System::Object^)val)->Equals((System::Object^)x)` má hodnotu true (pokud existuje). Použijete ji vymazat libovolný prvek se zadanou hodnotou.

### <a name="example"></a>Příklad

```cpp
// cliext_list_remove.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // fail to remove and redisplay
    c1.remove(L'A');
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // remove and redisplay
    c1.remove(L'b');
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a b c
a c
```

## <a name="remove_if"></a> list::remove_if (STL/CLR)

Odebere prvky, které předávají zadaný testovací.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Pred1>
    void remove_if(Pred1 pred);
```

#### <a name="parameters"></a>Parametry

*Před*<br/>
Test pro prvky, které chcete odebrat.

### <a name="remarks"></a>Poznámky

Členská funkce odebere z řízené sekvence (maže) každý prvek `X` pro kterou `pred(X)` má hodnotu true. Použijete ji k odebrání všech prvků, které splňují podmínku, že zadáte jako funkce nebo delegáta.

### <a name="example"></a>Příklad

```cpp
// cliext_list_remove_if.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'b');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b b b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // fail to remove and redisplay
    c1.remove_if(cliext::binder2nd<cliext::equal_to<wchar_t> >(
        cliext::equal_to<wchar_t>(), L'd'));
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // remove and redisplay
    c1.remove_if(cliext::binder2nd<cliext::not_equal_to<wchar_t> >(
        cliext::not_equal_to<wchar_t>(), L'b'));
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b b b c
a b b b c
b b b
```

## <a name="rend"></a> list::rend (STL/CLR)

Určuje konec řízené obrácené sekvenci.

### <a name="syntax"></a>Syntaxe

```cpp
reverse_iterator rend();
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí "reverse iterator", který ukazuje za začátek řízené sekvence. Proto, označí `end` reverzní pořadí. Můžete ji použít k získání iterátor, který určuje `current` konec řízené sekvence viděli v obráceném pořadí, ale jeho stav můžete změnit, pokud se změní délka řízené sekvence.

### <a name="example"></a>Příklad

```cpp
// cliext_list_rend.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect first two items
    cliext::list<wchar_t>::reverse_iterator rit = c1.rend();
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

## <a name="resize"></a> list::Resize (STL/CLR)

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

Členské funkce obou Ujistěte se, že [list::size (STL/CLR)](../dotnet/list-size-stl-clr.md) `()` od nynějška vrátí *new_size*. Pokud je třeba provést řízené sekvence delší, první členská funkce přidá prvky s hodnotou `value_type()`, zatímco druhá členská funkce přidá prvky s hodnotou *val*. Chcete-li řízené sekvence kratší, i členské funkce efektivně vymazat poslední prvek [list::size (STL/CLR)](../dotnet/list-size-stl-clr.md) `() -` `new_size` časy. Použít zajistit, že velikost řízené sekvence *new_size*, ořezávání nebo odsazení aktuální řízené sekvence.

### <a name="example"></a>Příklad

```cpp
// cliext_list_resize.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
// construct an empty container and pad with default values
    cliext::list<wchar_t> c1;
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

## <a name="reverse"></a> list::reverse (STL/CLR)

Obrátí řízené sekvence.

### <a name="syntax"></a>Syntaxe

```cpp
void reverse();
```

### <a name="remarks"></a>Poznámky

Členská funkce obrátí pořadí všech prvků v řízené sekvenci. Použijete ji tak, aby odrážely seznam prvků.

### <a name="example"></a>Příklad

```cpp
// cliext_list_reverse.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // reverse and redisplay
    c1.reverse();
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
c b a
```

## <a name="reverse_iterator"></a> list::reverse_iterator (STL/CLR)

Typ "reverse iterator" pro řízenou sekvenci.

### <a name="syntax"></a>Syntaxe

```cpp
typedef T3 reverse_iterator;
```

### <a name="remarks"></a>Poznámky

Typ popisuje objekt neurčeného typu `T3` , který může sloužit jako "reverse iterator" pro řízenou sekvenci.

### <a name="example"></a>Příklad

```cpp
// cliext_list_reverse_iterator.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c" reversed
    cliext::list<wchar_t>::reverse_iterator rit = c1.rbegin();
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

## <a name="size"></a> list::size (STL/CLR)

Spočítá počet prvků.

### <a name="syntax"></a>Syntaxe

```cpp
size_type size();
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí délku objektu řízené sekvence. Použijete ji k určení počtu prvků v řízené sekvenci aktuálně. Pokud vás zajímá, jestli je pořadí má nenulovou velikost, naleznete v tématu [list::empty (STL/CLR)](../dotnet/list-empty-stl-clr.md)`()`.

### <a name="example"></a>Příklad

```cpp
// cliext_list_size.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
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

## <a name="size_type"></a> list::size_type (STL/CLR)

Typ vzdálenosti se znaménkem mezi dvěma elementu.

### <a name="syntax"></a>Syntaxe

```cpp
typedef int size_type;
```

### <a name="remarks"></a>Poznámky

Typ, který popisuje počet prvků záporná.

### <a name="example"></a>Příklad

```cpp
// cliext_list_size_type.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // compute positive difference
    cliext::list<wchar_t>::size_type diff = 0;
    for (cliext::list<wchar_t>::iterator it = c1.begin();
        it != c1.end(); ++it)
        ++diff;
    System::Console::WriteLine("end()-begin() = {0}", diff);
    return (0);
    }
```

```Output
a b c
end()-begin() = 3
```

## <a name="sort"></a> list::sort (STL/CLR)

Seřadí řízené sekvence.

### <a name="syntax"></a>Syntaxe

```cpp
void sort();
template<typename Pred2>
    void sort(Pred2 pred);
```

#### <a name="parameters"></a>Parametry

*Před*<br/>
Procedura pro prvek dvojice.

### <a name="remarks"></a>Poznámky

První členská funkce pořadí prvků v řízené sekvenci tak, že jsou řazeny podle `operator<` – elementy v hodnotě nesnižujte po absolvování sekvence. Tuto funkci člena použít k seřazení pořadí ve vzestupném pořadí.

Druhá členská funkce se chová stejně jako první, s tím rozdílem, že je pořadí jsou seřazená podle `pred`  --  `pred(X, Y)` má hodnotu false pro libovolný element `X` , který následuje prvku `Y` ve výsledné pořadí. Použijete ji k seřazení pořadí v pořadí, které zadáte pomocí funkce predikátu nebo delegáta.

Jak provádět funkce stabilní řazení – žádná dvojice prvků v řízené sekvenci původní je obrácený ve výsledné řízené sekvence.

### <a name="example"></a>Příklad

```cpp
// cliext_list_sort.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // sort descending and redisplay
    c1.sort(cliext::greater<wchar_t>());
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // sort ascending and redisplay
    c1.sort();
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
c b a
a b c
```

## <a name="splice"></a> list::splice (STL/CLR)

Restitch propojení mezi uzly.

### <a name="syntax"></a>Syntaxe

```cpp
void splice(iterator where, list<Value>% right);
void splice(iterator where, list<Value>% right,
    iterator first);
void splice(iterator where, list<Value>% right,
    iterator first, iterator last);
```

#### <a name="parameters"></a>Parametry

*první*<br/>
Začátek rozsahu splice

*poslední*<br/>
Konec rozsahu splice.

*doprava*<br/>
Splice z kontejneru.

*kde*<br/>
Kde v kontejneru splice před.

### <a name="remarks"></a>Poznámky

První členská funkce vloží sekvenci řízené *správné* před elementu v řízené sekvenci ukazuje *kde*. Zároveň se tím odebere všechny prvky z *správné*. (`%right` nesmí být stejný jako `this`.) Použijete ji k splice vše z jednoho seznamu do jiného.

Druhá členská funkce odstraní prvek, na které odkazuje *první* v sekvenci řízené *správné* a vloží ho před elementu v řízené sekvenci ukazuje *kde* . (Pokud `where` `==` `first` `||` `where` `== ++first`, nedošlo k žádné změně.) Použijete ji k splice jeden element z jednoho seznamu do jiného.

Třetí členská funkce vloží určený dílčí sadu [`first`, `last`) ze sekvence řízenou parametrem *správné* před elementu v řízené sekvenci ukazuje *kde*. Zároveň se tím odebere původní dílčí sadu ze sekvence řízenou parametrem *správné*. (Pokud `right` `==` `this`, rozsah [`first`, `last`) nesmí obsahovat prvek, na které odkazuje *kde*.) Použijete ji k splice dílčí sekvenci z nuly nebo více prvků z jednoho seznamu do jiného.

### <a name="example"></a>Příklad

```cpp
// cliext_list_splice.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // splice to a new list
    cliext::list<wchar_t> c2;
    c2.splice(c2.begin(), c1);
    System::Console::WriteLine("c1.size() = {0}", c1.size());
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // return one element
    c1.splice(c1.end(), c2, c2.begin());
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // return remaining elements
    c1.splice(c1.begin(), c2, c2.begin(), c2.end());
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    System::Console::WriteLine("c2.size() = {0}", c2.size());
    return (0);
    }
```

```Output
a b c
c1.size() = 0
a b c
a
b c
b c a
c2.size() = 0
```

## <a name="swap"></a> list::swap (STL/CLR)

Zamění obsah dvou kontejnerů.

### <a name="syntax"></a>Syntaxe

```cpp
void swap(list<Value>% right);
```

#### <a name="parameters"></a>Parametry

*doprava*<br/>
Kontejner pro obsah s.

### <a name="remarks"></a>Poznámky

Členská funkce Zamění řízené sekvence mezi `*this` a *správné*. Provádí se v konstantním času a vyvolá žádné výjimky. Můžete použít jako rychlý způsob, jak Zamění obsah dvou kontejnerů.

### <a name="example"></a>Příklad

```cpp
// cliext_list_swap.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct another container with repetition of values
    cliext::list<wchar_t> c2(5, L'x');
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

## <a name="to_array"></a> list::to_array (STL/CLR)

Zkopíruje do nového pole řízené sekvence.

### <a name="syntax"></a>Syntaxe

```cpp
cli::array<Value>^ to_array();
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí pole obsahující řízené sekvence. Použijete ji získat kopii řízenou sekvenci pole formuláře.

### <a name="example"></a>Příklad

```cpp
// cliext_list_to_array.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
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

## <a name="unique"></a> list::Unique (STL/CLR)

Odebere sousedící prvky, které předávají zadaný testovací.

### <a name="syntax"></a>Syntaxe

```cpp
void unique();
template<typename Pred2>
    void unique(Pred2 pred);
```

#### <a name="parameters"></a>Parametry

*Před*<br/>
Procedura pro prvek dvojice.

### <a name="remarks"></a>Poznámky

První členská funkce odebere z řízené sekvence (maže) každý element, který porovnává rovná jeho předchozí prvek – Pokud elementu `X` předchází element `Y` a `X == Y`, členská funkce odebere `Y`. Použijete ho odebrat všechny kopie krom jedné každý dílčí sekvenci sousedícími elementy tohoto porovnání rovnosti. Všimněte si, že pokud řízené sekvence je seřazen, například jak voláním [list::sort (STL/CLR)](../dotnet/list-sort-stl-clr.md)`()`, členské funkce ponechá pouze elementy s jedinečnými hodnotami. (Tedy název).

Druhá členská funkce se chová stejně jako první, s tím rozdílem, že odebere každý prvek `Y` následující element `X` pro kterou `pred(X, Y)`. Použijete ji odebrat všechny kopie krom jedné každý dílčí sekvenci sousedící prvky, které splňují predikát funkce nebo delegát, který zadáte. Všimněte si, že pokud řízené sekvence je seřazen, například jak voláním `sort(pred)`, členské funkce ponechá pouze prvky, které nemají ekvivalentní řazení s jinými prvky.

### <a name="example"></a>Příklad

```cpp
// cliext_list_unique.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // display contents after unique
    cliext::list<wchar_t> c2(c1);
    c2.unique();
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // display contents after unique(not_equal_to)
    c2 = c1;
    c2.unique(cliext::not_equal_to<wchar_t>());
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a a b c
a b c
a a
```

## <a name="value_type"></a> list::value_type (STL/CLR)

Typ prvku

### <a name="syntax"></a>Syntaxe

```cpp
typedef Value value_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro parametr šablony *hodnota*.

### <a name="example"></a>Příklad

```cpp
// cliext_list_value_type.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c" using value_type
    for (cliext::list<wchar_t>::iterator it = c1.begin();
        it != c1.end(); ++it)
        {   // store element in value_type object
        cliext::list<wchar_t>::value_type val = *it;

        System::Console::Write("{0} ", val);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="op_neq"></a> Operator! = (list) (STL/CLR)

Seznam není rovno porovnání.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Value>
    bool operator!=(list<Value>% left,
        list<Value>% right);
```

#### <a name="parameters"></a>Parametry

*doleva*<br/>
Levé kontejner k porovnání.

*doprava*<br/>
Správném kontejneru pro porovnání.

### <a name="remarks"></a>Poznámky

Vrátí funkci operátoru `!(left == right)`. Pomocí něho můžete testovat, zda *levé* není stejný jako seřazené *správné* když dva seznamy jsou ve srovnání elementu pomocí elementu.

### <a name="example"></a>Příklad

```cpp
// cliext_list_operator_ne.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    cliext::list<wchar_t> c2;
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

## <a name="op_lt"></a> operátor&lt; (list) (STL/CLR)

Seznam menší než porovnání.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Value>
    bool operator<(list<Value>% left,
        list<Value>% right);
```

#### <a name="parameters"></a>Parametry

*doleva*<br/>
Levé kontejner k porovnání.

*doprava*<br/>
Správném kontejneru pro porovnání.

### <a name="remarks"></a>Poznámky

Operátoru funkce vrátí hodnota true v případě, pro nejnižší pozici `i` pro kterou `!(right[i] < left[i])` je také hodnotu true, který `left[i] < right[i]`. V opačném případě vrátí `left->size() < right->size()` pomocí něho můžete testovat, zda *levé* je řazen před *správné* když dva seznamy jsou ve srovnání elementu pomocí elementu.

### <a name="example"></a>Příklad

```cpp
// cliext_list_operator_lt.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    cliext::list<wchar_t> c2;
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

## <a name="op_lteq"></a> operátor&lt;= (list) (STL/CLR)

Seznam menší nebo rovna porovnání.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Value>
    bool operator<=(list<Value>% left,
        list<Value>% right);
```

#### <a name="parameters"></a>Parametry

*doleva*<br/>
Levé kontejner k porovnání.

*doprava*<br/>
Správném kontejneru pro porovnání.

### <a name="remarks"></a>Poznámky

Vrátí funkci operátoru `!(right < left)`. Pomocí něho můžete testovat, zda *levé* není seřazené po *správné* když dva seznamy jsou ve srovnání elementu pomocí elementu.

### <a name="example"></a>Příklad

```cpp
// cliext_list_operator_le.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    cliext::list<wchar_t> c2;
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

## <a name="op_eq"></a> Operator == (list) (STL/CLR)

Porovnání rovna seznamu.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Value>
    bool operator==(list<Value>% left,
        list<Value>% right);
```

#### <a name="parameters"></a>Parametry

*doleva*<br/>
Levé kontejner k porovnání.

*doprava*<br/>
Správném kontejneru pro porovnání.

### <a name="remarks"></a>Poznámky

Funkce operátoru vrátí hodnotu true pouze v případě, že řídí sekvencí *levé* a *správné* mít stejnou délku a pro každou pozici `i`, `left[i] ==` `right[i]`. Pomocí něho můžete testovat, zda *levé* je stejný jako seřazené *správné* když dva seznamy jsou ve srovnání elementu pomocí elementu.

### <a name="example"></a>Příklad

```cpp
// cliext_list_operator_eq.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    cliext::list<wchar_t> c2;
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

## <a name="op_gt"></a> operátor&gt; (list) (STL/CLR)

Seznam je větší než porovnání.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Value>
    bool operator>(list<Value>% left,
        list<Value>% right);
```

#### <a name="parameters"></a>Parametry

*doleva*<br/>
Levé kontejner k porovnání.

*doprava*<br/>
Správném kontejneru pro porovnání.

### <a name="remarks"></a>Poznámky

Vrátí funkci operátoru `right` `<` `left`. Pomocí něho můžete testovat, zda *levé* seřazené po *správné* když dva seznamy jsou ve srovnání elementu pomocí elementu.

### <a name="example"></a>Příklad

```cpp
// cliext_list_operator_gt.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    cliext::list<wchar_t> c2;
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

## <a name="op_gteq"></a> operátor&gt;= (list) (STL/CLR)

Seznam větší než nebo rovna porovnání.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Value>
    bool operator>=(list<Value>% left,
        list<Value>% right);
```

#### <a name="parameters"></a>Parametry

*doleva*<br/>
Levé kontejner k porovnání.

*doprava*<br/>
Správném kontejneru pro porovnání.

### <a name="remarks"></a>Poznámky

Vrátí funkci operátoru `!(left` `<` `right)`. Pomocí něho můžete testovat, zda *levé* není řazen před *správné* když dva seznamy jsou ve srovnání elementu pomocí elementu.

### <a name="example"></a>Příklad

```cpp
// cliext_list_operator_ge.cpp
// compile with: /clr
#include <cliext/list>

int main()
    {
    cliext::list<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    cliext::list<wchar_t> c2;
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