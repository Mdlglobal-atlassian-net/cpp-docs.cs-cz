---
title: deque (STL/CLR)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cliext::deque
- cliext::deque::assign
- cliext::deque::at
- cliext::deque::back
- cliext::deque::back_item
- cliext::deque::begin
- cliext::deque::clear
- cliext::deque::const_iterator
- cliext::deque::const_reference
- cliext::deque::const_reverse_iterator
- cliext::deque::deque
- cliext::deque::difference_type
- cliext::deque::empty
- cliext::deque::end
- cliext::deque::erase
- cliext::deque::front
- cliext::deque::front_item
- cliext::deque::generic_container
- cliext::deque::generic_iterator
- cliext::deque::generic_reverse_iterator
- cliext::deque::generic_value
- cliext::deque::insert
- cliext::deque::iterator
- cliext::deque::operator!=
- cliext::deque::operator[]
- cliext::deque::pop_back
- cliext::deque::pop_front
- cliext::deque::push_back
- cliext::deque::push_front
- cliext::deque::rbegin
- cliext::deque::reference
- cliext::deque::rend
- cliext::deque::resize
- cliext::deque::reverse_iterator
- cliext::deque::size
- cliext::deque::size_type
- cliext::deque::swap
- cliext::deque::to_array
- cliext::deque::value_type
- cliext::deque::operator<
- cliext::deque::operator<=
- cliext::deque::operator=
- cliext::deque::operator==
- cliext::deque::operator>
- cliext::deque::operator>=
helpviewer_keywords:
- deque class [STL/CLR]
- <deque> header [STL/CLR]
- <cliext/deque> header [STL/CLR]
- assign member [STL/CLR]
- assign member [STL/CLR]
- at member [STL/CLR]
- back member [STL/CLR]
- back_item member [STL/CLR]
- begin member [STL/CLR]
- clear member [STL/CLR]
- const_iterator member [STL/CLR]
- const_reference member [STL/CLR]
- const_reverse_iterator member [STL/CLR]
- deque member [STL/CLR]
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
- operator!= member [STL/CLR]
- operator member [] [STL/CLR]
- pop_back member [STL/CLR]
- pop_front member [STL/CLR]
- push_back member [STL/CLR]
- push_front member [STL/CLR]
- rbegin member [STL/CLR]
- reference member [STL/CLR]
- rend member [STL/CLR]
- resize member [STL/CLR]
- reverse_iterator member [STL/CLR]
- size member [STL/CLR]
- size_type member [STL/CLR]
- swap member [STL/CLR]
- to_array member [STL/CLR]
- value_type member [STL/CLR]
- operator< member [STL/CLR]
- operator<= member [STL/CLR]
- operator= member [STL/CLR]
- operator== member [STL/CLR]
- operator> member [STL/CLR]
- operator>= member [STL/CLR]
ms.assetid: dd669da3-3c0e-45e9-8596-f6b483720941
ms.openlocfilehash: 74fb98d99e0aba94c40dce9ad1bcd6af83394231
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80208765"
---
# <a name="deque-stlclr"></a>deque (STL/CLR)

Třída šablony popisuje objekt, který řídí proměnlivou délku sekvence prvků, které mají náhodný přístup. Kontejner `deque` slouží ke správě sekvence prvků, které vypadají jako souvislý blok úložiště, ale které lze zvětšovat nebo zmenšovat na obou koncích bez nutnosti kopírovat zbývající prvky. Proto může implementovat efektivně `double-ended queue`. (Tedy název.)

V popisu níže je `GValue` stejné jako `Value`, pokud se jedná o typ ref. v takovém případě je to `Value^`.

## <a name="syntax"></a>Syntaxe

```cpp
template<typename Value>
    ref class deque
        :   public
        System::ICloneable,
        System::Collections::IEnumerable,
        System::Collections::ICollection,
        System::Collections::Generic::IEnumerable<GValue>,
        System::Collections::Generic::ICollection<GValue>,
        System::Collections::Generic::IList<GValue>,
        Microsoft::VisualC::StlClr::IDeque<GValue>
    { ..... };
```

### <a name="parameters"></a>Parametry

*GValue*<br/>
Obecný typ prvku v řízené sekvenci.

*Hodnota*<br/>
Typ elementu v řízené sekvenci

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<cliext –/deque >

**Obor názvů:** cliext –

## <a name="declarations"></a>Deklarace

|Definice typu|Popis|
|---------------------|-----------------|
|[deque::const_iterator (STL/CLR)](#const_iterator)|Typ konstantního iterátoru řízené sekvence|
|[deque::const_reference (STL/CLR)](#const_reference)|Typ konstantního odkazu na prvek|
|[deque::const_reverse_iterator (STL/CLR)](#const_reverse_iterator)|Typ konstantního reverzního iterátoru řízené sekvence.|
|[deque::difference_type (STL/CLR)](#difference_type)|Typ vzdálenosti se znaménkem mezi dvěma prvky|
|[deque::generic_container (STL/CLR)](#generic_container)|Typ obecného rozhraní pro kontejner.|
|[deque::generic_iterator (STL/CLR)](#generic_iterator)|Typ iterátoru pro obecné rozhraní kontejneru.|
|[deque::generic_reverse_iterator (STL/CLR)](#generic_reverse_iterator)|Typ reverzního iterátoru pro obecné rozhraní kontejneru.|
|[deque::generic_value (STL/CLR)](#generic_value)|Typ elementu pro obecné rozhraní kontejneru.|
|[deque::iterator (STL/CLR)](#iterator)|Typ iterátoru řízené sekvence|
|[deque::reference (STL/CLR)](#reference)|Typ odkazu na prvek|
|[deque::reverse_iterator (STL/CLR)](#reverse_iterator)|Typ reverzního iterátoru řízené sekvence.|
|[deque::size_type (STL/CLR)](#size_type)|Typ vzdálenosti se znaménkem mezi dvěma prvky|
|[deque::value_type (STL/CLR)](#value_type)|Typ prvku|

|Členská funkce|Popis|
|---------------------|-----------------|
|[deque::assign (STL/CLR)](#assign)|Nahradí všechny prvky.|
|[deque::at (STL/CLR)](#at)|Přistupuje k elementu na zadané pozici.|
|[deque::back (STL/CLR)](#back)|Přistupuje k poslednímu prvku.|
|[deque::begin (STL/CLR)](#begin)|Určuje začátek řízené sekvence.|
|[deque::clear (STL/CLR)](#clear)|Odebere všechny prvky.|
|[deque::deque (STL/CLR)](#deque)|Sestaví objekt kontejneru.|
|[deque::empty (STL/CLR)](#empty)|Zkouší, zda nejsou přítomny žádné prvky.|
|[deque::end (STL/CLR)](#end)|Určuje konec řízené sekvence.|
|[deque::erase (STL/CLR)](#erase)|Odebere prvky v určených pozicích.|
|[deque::front (STL/CLR)](#front)|Přistupuje k prvnímu prvku.|
|[deque::insert (STL/CLR)](#insert)|Přidá prvky na zadanou pozici.|
|[deque::pop_back (STL/CLR)](#pop_back)|Odstraní poslední prvek.|
|[deque::pop_front (STL/CLR)](#pop_front)|Odstraní první prvek.|
|[deque::push_back (STL/CLR)](#push_back)|Přidá nový poslední prvek.|
|[deque::push_front (STL/CLR)](#push_front)|Přidá nový první prvek.|
|[deque::rbegin (STL/CLR)](#rbegin)|Určuje začátek obrácené kontrolované sekvence.|
|[deque::rend (STL/CLR)](#rend)|Určuje konec reverzní kontrolované sekvence.|
|[deque::resize (STL/CLR)](#resize)|Změní počet prvků.|
|[deque::size (STL/CLR)](#size)|Spočítá počet prvků.|
|[deque::swap (STL/CLR)](#swap)|Zamění obsah dvou kontejnerů.|
|[deque::to_array (STL/CLR)](#to_array)|Zkopíruje řízenou sekvenci do nového pole.|

|Vlastnost|Popis|
|--------------|-----------------|
|[deque::back_item (STL/CLR)](#back_item)|Přistupuje k poslednímu prvku.|
|[deque::front_item (STL/CLR)](#front_item)|Přistupuje k prvnímu prvku.|

|Operátor|Popis|
|--------------|-----------------|
|[deque::operator!= (STL/CLR)](#op_neq)|Určuje, zda nejsou dva objekty `deque` stejné.|
|[deque::operator(STL/CLR)](#operator)|Přistupuje k elementu na zadané pozici.|
|[operator< (deque) (STL/CLR)](#op_lt)|Určuje, zda je objekt `deque` menší než jiný objekt `deque`.|
|[operator<= (deque) (STL/CLR)](#op_lteq)|Určuje, zda je objekt `deque` menší nebo roven jinému objektu `deque`.|
|[operator= (deque) (STL/CLR)](#op_as)|Nahradí řízenou sekvenci.|
|[operator== (deque) (STL/CLR)](#op_eq)|Určuje, zda je objekt `deque` roven jinému objektu `deque`.|
|[operator> (deque) (STL/CLR)](#op_gt)|Určuje, zda je objekt `deque` větší než jiný objekt `deque`.|
|[operator>= (deque) (STL/CLR)](#op_gteq)|Určuje, zda je objekt `deque` větší nebo roven jinému objektu `deque`.|

## <a name="interfaces"></a>Rozhraní

|Rozhraní|Popis|
|---------------|-----------------|
|<xref:System.ICloneable>|Duplikuje objekt.|
|<xref:System.Collections.IEnumerable>|Sekvence prostřednictvím prvků.|
|<xref:System.Collections.ICollection>|Udržovat skupinu prvků.|
|<xref:System.Collections.Generic.IEnumerable%601>|Sekvence prostřednictvím typových elementů.|
|<xref:System.Collections.Generic.ICollection%601>|Udržovat skupinu typových elementů.|
|<xref:System.Collections.Generic.IList%601>|Udržovat uspořádanou skupinu typových prvků.|
|IDeque hodnota <\>|Udržujte obecný kontejner.|

## <a name="remarks"></a>Poznámky

Objekt přiděluje a uvolňuje úložiště pro sekvenci, kterou ovládá, pomocí uloženého pole popisovačů, které určují bloky `Value` prvků. Pole roste na vyžádání. Růst probíhá takovým způsobem, že náklady na buď nedokončený nebo připojení nového prvku jsou konstantní čas a žádné zbývající prvky nejsou rušeny. Můžete také odebrat prvek buď na konci v konstantním čase, a bez narušení zbývajících prvků. Proto je deque vhodným kandidátem pro základní kontejner pro třídu šablony Class [(STL/CLR)](../dotnet/queue-stl-clr.md) nebo zásobník tříd šablon [(STL/CLR)](../dotnet/stack-stl-clr.md).

Objekt `deque` podporuje iterátory s náhodným přístupem, což znamená, že můžete odkazovat na prvek přímo z jeho číselné pozice a počítat z nuly pro první (přední) prvek, do [deque:: Size (STL/CLR)](#size)`() - 1` pro poslední (zadní) prvek. Také to znamená, že deque je vhodným kandidátem pro základní kontejner třídy template [priority_queue (STL/CLR)](../dotnet/priority-queue-stl-clr.md).

Iterátor deque ukládá popisovač ke svému přidruženému objektu deque spolu s posunem elementu, který označuje. Iterátory lze použít pouze u jejich přidružených objektů kontejneru. Posun elementu deque *není nutně stejný* jako jeho poloha. První element vložený má nulovou odchylku, další připojený prvek má posun 1, ale další přidaný prvek má posun-1.

Vložení nebo mazání prvků v obou koncích *nemění hodnotu* elementu uloženého v jakémkoli platném posunu. Vložení nebo mazání vnitřního prvku však *může* změnit hodnotu elementu uloženou v daném posunu, takže hodnotu určenou iterátorem lze také změnit. (Kontejner může muset zkopírovat prvky nahoru nebo dolů a vytvořit díru před vložením nebo vyplněním otvoru po vymazání.) Nicméně iterátor deque zůstává platný, pokud jeho posun určuje platný element. Navíc platí, že platný iterátor zůstává neodkazný – můžete ho použít pro přístup k hodnotě prvku, kterou Určuje, a k jejímu změně, a to i v případě, že se její posun nerovná posunu pro iterátor vrácený `end()`.

Při mazání nebo odebírání elementu se volá destruktor pro jeho uloženou hodnotu. Zničení kontejneru smaže všechny prvky. Proto kontejner, jehož typ elementu je ref class, zajistí, že kontejner neobsahuje žádné prvky. Upozorňujeme však, že kontejner popisovačů *nezničí své* prvky.

## <a name="members"></a>Členové

## <a name="dequeassign-stlclr"></a><a name="assign"></a>deque:: assign (STL/CLR)

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
// cliext_deque_assign.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // assign a repetition of values
    cliext::deque<wchar_t> c2;
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

## <a name="dequeat-stlclr"></a><a name="at"></a>deque:: at (STL/CLR)

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
// cliext_deque_at.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
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

## <a name="dequeback-stlclr"></a><a name="back"></a>deque:: Back (STL/CLR)

Přistupuje k poslednímu prvku.

### <a name="syntax"></a>Syntaxe

```cpp
reference back();
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí odkaz na poslední prvek řízené sekvence, který nesmí být prázdný. Použijete ho k přístupu k poslednímu prvku, když víte, že existuje.

### <a name="example"></a>Příklad

```cpp
// cliext_deque_back.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
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

## <a name="dequeback_item-stlclr"></a><a name="back_item"></a>deque:: back_item (STL/CLR)

Přistupuje k poslednímu prvku.

### <a name="syntax"></a>Syntaxe

```cpp
property value_type back_item;
```

### <a name="remarks"></a>Poznámky

Vlastnost přistupuje k poslednímu prvku kontrolované sekvence, který nesmí být prázdný. Použijete ho ke čtení nebo zápisu posledního prvku, když víte, že existuje.

### <a name="example"></a>Příklad

```cpp
// cliext_deque_back_item.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
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

## <a name="dequebegin-stlclr"></a><a name="begin"></a>deque:: begin (STL/CLR)

Určuje začátek řízené sekvence.

### <a name="syntax"></a>Syntaxe

```cpp
iterator begin();
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí iterátor náhodného přístupu, který určuje první prvek řízené sekvence nebo těsně za konec prázdné sekvence. Použijete ho k získání iterátoru, který určuje `current` začátek řízené sekvence, ale jeho stav se může změnit, pokud se změní délka kontrolované sekvence.

### <a name="example"></a>Příklad

```cpp
// cliext_deque_begin.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect first two items
    cliext::deque<wchar_t>::iterator it = c1.begin();
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

## <a name="dequeclear-stlclr"></a><a name="clear"></a>deque:: Clear (STL/CLR)

Odebere všechny prvky.

### <a name="syntax"></a>Syntaxe

```cpp
void clear();
```

### <a name="remarks"></a>Poznámky

Členská funkce efektivně volá [deque:: Erase (STL/CLR)](#erase)`(` [deque:: begin (STL/CLR)](#begin)`(),` [DEQUE:: end (STL/CLR)](#end)`())`. Použijete ho k zajištění, aby řízená sekvence byla prázdná.

### <a name="example"></a>Příklad

```cpp
// cliext_deque_clear.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
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

## <a name="dequeconst_iterator-stlclr"></a><a name="const_iterator"></a>deque:: const_iterator (STL/CLR)

Typ konstantního iterátoru řízené sekvence

### <a name="syntax"></a>Syntaxe

```cpp
typedef T2 const_iterator;
```

### <a name="remarks"></a>Poznámky

Typ popisuje objekt nespecifikovaného typu `T2`, který může sloužit jako konstantní iterátor náhodného přístupu pro řízenou sekvenci.

### <a name="example"></a>Příklad

```cpp
// cliext_deque_const_iterator.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    cliext::deque<wchar_t>::const_iterator cit = c1.begin();
    for (; cit != c1.end(); ++cit)
        System::Console::Write("{0} ", *cit);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="dequeconst_reference-stlclr"></a><a name="const_reference"></a>deque:: const_reference (STL/CLR)

Typ konstantního odkazu na prvek

### <a name="syntax"></a>Syntaxe

```cpp
typedef value_type% const_reference;
```

### <a name="remarks"></a>Poznámky

Typ popisuje konstantní odkaz na prvek.

### <a name="example"></a>Příklad

```cpp
// cliext_deque_const_reference.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    cliext::deque<wchar_t>::const_iterator cit = c1.begin();
    for (; cit != c1.end(); ++cit)
        {   // get a const reference to an element
        cliext::deque<wchar_t>::const_reference cref = *cit;
        System::Console::Write("{0} ", cref);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="dequeconst_reverse_iterator-stlclr"></a><a name="const_reverse_iterator"></a>deque:: const_reverse_iterator (STL/CLR)

Typ konstantního reverzního iterátoru řízené sekvence.

### <a name="syntax"></a>Syntaxe

```cpp
typedef T4 const_reverse_iterator;
```

### <a name="remarks"></a>Poznámky

Typ popisuje objekt nespecifikovaného typu `T4`, který může sloužit jako konstantní reverzní iterátor pro řízenou sekvenci.

### <a name="example"></a>Příklad

```cpp
// cliext_deque_const_reverse_iterator.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c" reversed
    cliext::deque<wchar_t>::const_reverse_iterator crit = c1.rbegin();
    cliext::deque<wchar_t>::const_reverse_iterator crend = c1.rend();
    for (; crit != crend; ++crit)
        System::Console::Write("{0} ", *crit);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c b a
```

## <a name="dequedeque-stlclr"></a><a name="deque"></a>deque::d eque (STL/CLR)

Sestaví objekt kontejneru.

### <a name="syntax"></a>Syntaxe

```cpp
deque();
deque(deque<Value>% right);
deque(deque<Value>^ right);
explicit deque(size_type count);
deque(size_type count, value_type val);
template<typename InIt>
    deque(InIt first, InIt last);
deque(System::Collections::Generic::IEnumerable<Value>^ right);
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

`deque();`

Inicializuje řízenou sekvenci bez prvků. Použijete ji k zadání prázdné počáteční řízené sekvence.

Konstruktor:

`deque(deque<Value>% right);`

Inicializuje řízenou sekvenci pomocí sekvence [`right.begin()`, `right.end()`). Použijete ji k určení počáteční řízené sekvence, která je kopií sekvence řízené objektem deque *vpravo*. Další informace o iterátorech naleznete v tématu [deque:: begin (STL/CLR)](#begin) a [deque:: end (STL/CLR)](#end).

Konstruktor:

`deque(deque<Value>^ right);`

Inicializuje řízenou sekvenci pomocí sekvence [`right->begin()`, `right->end()`). Použijete ji k určení počáteční řízené sekvence, která je kopií sekvence řízené objektem deque, jehož popisovač je *pravý*.

Konstruktor:

`explicit deque(size_type count);`

Inicializuje řízenou sekvenci pomocí prvků *Count* s hodnotou `value_type()`. Použijete ho k vyplnění kontejneru všemi prvky, které mají výchozí hodnotu.

Konstruktor:

`deque(size_type count, value_type val);`

Inicializuje řízenou sekvenci pomocí *počtu* elementů s hodnotou *Val*. Použijete ho k vyplnění kontejneru všemi prvky, které mají stejnou hodnotu.

Konstruktor:

`template<typename InIt>`

`deque(InIt first, InIt last);`

Inicializuje řízenou sekvenci pomocí sekvence [`first`, `last`). Použijete ho k tomu, aby řízená sekvence kopírovala jinou sekvenci.

Konstruktor:

`deque(System::Collections::Generic::IEnumerable<Value>^ right);`

Inicializuje řízenou sekvenci sekvencí, která je určena *přípravou*výčtu. Použijete ho k tomu, aby řízená sekvence zkopírovala jinou sekvenci popsanou enumerátorem.

### <a name="example"></a>Příklad

```cpp
// cliext_deque_construct.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
// construct an empty container
    cliext::deque<wchar_t> c1;
    System::Console::WriteLine("size() = {0}", c1.size());

    // construct with a repetition of default values
    cliext::deque<wchar_t> c2(3);
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", (int)elem);
    System::Console::WriteLine();

    // construct with a repetition of values
    cliext::deque<wchar_t> c3(6, L'x');
    for each (wchar_t elem in c3)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an iterator range
    cliext::deque<wchar_t>::iterator it = c3.end();
    cliext::deque<wchar_t> c4(c3.begin(), --it);
    for each (wchar_t elem in c4)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an enumeration
    cliext::deque<wchar_t> c5(   // NOTE: cast is not needed
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3);
    for each (wchar_t elem in c5)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct by copying another container
    cliext::deque<wchar_t> c7(c3);
    for each (wchar_t elem in c7)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct by copying a container handle
    cliext::deque<wchar_t> c8(%c3);
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

## <a name="dequedifference_type-stlclr"></a><a name="difference_type"></a>deque::d ifference_type (STL/CLR)

Typy podepsané vzdálenosti mezi dvěma prvky.

### <a name="syntax"></a>Syntaxe

```cpp
typedef int difference_type;
```

### <a name="remarks"></a>Poznámky

Typ popisuje počet podepsaných prvků.

### <a name="example"></a>Příklad

```cpp
// cliext_deque_difference_type.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // compute positive difference
    cliext::deque<wchar_t>::difference_type diff = 0;
    for (cliext::deque<wchar_t>::iterator it = c1.begin();
        it != c1.end(); ++it) ++diff;
    System::Console::WriteLine("end()-begin() = {0}", diff);

    // compute negative difference
    diff = 0;
    for (cliext::deque<wchar_t>::iterator it = c1.end();
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

## <a name="dequeempty-stlclr"></a><a name="empty"></a>deque:: Empty (STL/CLR)

Zkouší, zda nejsou přítomny žádné prvky.

### <a name="syntax"></a>Syntaxe

```cpp
bool empty();
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí hodnotu true pro prázdnou řízenou sekvenci. Je ekvivalentem [deque:: Size (STL/CLR)](#size)`() == 0`. Použijete ho k otestování, jestli je deque prázdné.

### <a name="example"></a>Příklad

```cpp
// cliext_deque_empty.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
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

## <a name="dequeend-stlclr"></a><a name="end"></a>deque:: end (STL/CLR)

Určuje konec řízené sekvence.

### <a name="syntax"></a>Syntaxe

```cpp
iterator end();
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí iterátor náhodného přístupu, který odkazuje hned za konec řízené sekvence. Použijete ho k získání iterátoru, který určuje `current` konec řízené sekvence, ale jeho stav se může změnit, pokud se změní délka kontrolované sekvence.

### <a name="example"></a>Příklad

```cpp
// cliext_deque_end.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect last two items
    cliext::deque<wchar_t>::iterator it = c1.end();
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

## <a name="dequeerase-stlclr"></a><a name="erase"></a>deque:: Erase (STL/CLR)

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

Oba členské funkce vrací iterátor, který určuje první prvek zbývající za odebranými prvky, nebo [deque:: end (STL/CLR)](#end)`()`, pokud žádný takový prvek neexistuje.

Při mazání prvků je počet kopií elementu lineární v počtu prvků mezi koncem mazání a koncem koncového čísla sekvence. (Při mazání jednoho nebo více prvků na konci sekvence nedojde k žádnému kopírování prvků.)

### <a name="example"></a>Příklad

```cpp
// cliext_deque_erase.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
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
    cliext::deque<wchar_t>::iterator it = c1.end();
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

## <a name="dequefront-stlclr"></a><a name="front"></a>deque:: front (STL/CLR)

Přistupuje k prvnímu prvku.

### <a name="syntax"></a>Syntaxe

```cpp
reference front();
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí odkaz na první prvek řízené sekvence, který nesmí být prázdný. Použijete ho ke čtení nebo zápisu prvního prvku, když víte, že existuje.

### <a name="example"></a>Příklad

```cpp
// cliext_deque_front.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
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

## <a name="dequefront_item-stlclr"></a><a name="front_item"></a>deque:: front_item (STL/CLR)

Přistupuje k prvnímu prvku.

### <a name="syntax"></a>Syntaxe

```cpp
property value_type front_item;
```

### <a name="remarks"></a>Poznámky

Vlastnost přistupuje k prvnímu prvku kontrolované sekvence, který nesmí být prázdný. Použijete ho ke čtení nebo zápisu prvního prvku, když víte, že existuje.

### <a name="example"></a>Příklad

```cpp
// cliext_deque_front_item.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
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

## <a name="dequegeneric_container-stlclr"></a><a name="generic_container"></a>deque:: generic_container (STL/CLR)

Typ obecného rozhraní pro kontejner.

### <a name="syntax"></a>Syntaxe

```cpp
typedef Microsoft::VisualC::StlClr::
    IDeque<generic_value>
    generic_container;
```

### <a name="remarks"></a>Poznámky

Typ popisuje obecné rozhraní pro tuto třídu kontejneru šablony.

### <a name="example"></a>Příklad

```cpp
// cliext_deque_generic_container.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct a generic container
    cliext::deque<wchar_t>::generic_container^ gc1 = %c1;
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

## <a name="dequegeneric_iterator-stlclr"></a><a name="generic_iterator"></a>deque:: generic_iterator (STL/CLR)

Typ iterátoru pro použití s obecným rozhraním pro kontejner.

### <a name="syntax"></a>Syntaxe

```cpp
typedef Microsoft::VisualC::StlClr::Generic::
    ContainerRandomAccessIterator<generic_value> generic_iterator;
```

### <a name="remarks"></a>Poznámky

Typ popisuje obecný iterátor, který lze použít s obecným rozhraním pro tuto třídu kontejneru šablony.

### <a name="example"></a>Příklad

```cpp
// cliext_deque_generic_iterator.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct a generic container
    cliext::deque<wchar_t>::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // modify generic and display original
    cliext::deque<wchar_t>::generic_iterator gcit = gc1->begin();
    cliext::deque<wchar_t>::generic_value gcval = *gcit;
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

## <a name="dequegeneric_reverse_iterator-stlclr"></a><a name="generic_reverse_iterator"></a>deque:: generic_reverse_iterator (STL/CLR)

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
// cliext_deque_generic_reverse_iterator.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct a generic container
    cliext::deque<wchar_t>::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // modify generic and display original
    cliext::deque<wchar_t>::generic_reverse_iterator gcit = gc1->rbegin();
    cliext::deque<wchar_t>::generic_value gcval = *gcit;
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

## <a name="dequegeneric_value-stlclr"></a><a name="generic_value"></a>deque:: generic_value (STL/CLR)

Typ elementu pro použití s obecným rozhraním pro kontejner.

### <a name="syntax"></a>Syntaxe

```cpp
typedef GValue generic_value;
```

### <a name="remarks"></a>Poznámky

Typ popisuje objekt typu `GValue`, který popisuje hodnotu uloženého elementu pro použití s obecným rozhraním pro tuto třídu kontejneru šablony.

### <a name="example"></a>Příklad

```cpp
// cliext_deque_generic_value.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct a generic container
    cliext::deque<wchar_t>::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // modify generic and display original
    cliext::deque<wchar_t>::generic_iterator gcit = gc1->begin();
    cliext::deque<wchar_t>::generic_value gcval = *gcit;
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

## <a name="dequeinsert-stlclr"></a><a name="insert"></a>deque:: Insert (STL/CLR)

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
// cliext_deque_insert.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // insert a single value using iterator
    cliext::deque<wchar_t>::iterator it = c1.begin();
    System::Console::WriteLine("insert(begin()+1, L'x') = {0}",
        *c1.insert(++it, L'x'));
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // insert a repetition of values
    cliext::deque<wchar_t> c2;
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

## <a name="dequeiterator-stlclr"></a><a name="iterator"></a>deque:: iterátor (STL/CLR)

Typ iterátoru řízené sekvence

### <a name="syntax"></a>Syntaxe

```cpp
typedef T1 iterator;
```

### <a name="remarks"></a>Poznámky

Typ popisuje objekt nespecifikovaného typu `T1`, který může sloužit jako iterátor náhodného přístupu pro řízenou sekvenci.

### <a name="example"></a>Příklad

```cpp
// cliext_deque_iterator.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    cliext::deque<wchar_t>::iterator it = c1.begin();
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

## <a name="dequeoperator-stlclr"></a><a name="op_neq"></a>deque:: operator! = – operátor (STL/CLR)

Deque se bez porovnání.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Value>
    bool operator!=(deque<Value>% left,
        deque<Value>% right);
```

#### <a name="parameters"></a>Parametry

*zbývá*<br/>
Levý kontejner, který se má porovnat

*Kliknutím*<br/>
Pravý kontejner, který se má porovnat

### <a name="remarks"></a>Poznámky

Funkce operátoru vrací `!(left == right)`. Použijete ji k otestování, zda *Left* není seřazena stejně jako *právo* , pokud jsou obě deques porovnány podle prvku.

### <a name="example"></a>Příklad

```cpp
// cliext_deque_operator_ne.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    cliext::deque<wchar_t> c2;
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

## <a name="dequeoperatorstlclr"></a><a name="operator"></a>deque:: – operátor (STL/CLR)

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
// cliext_deque_operator_sub.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
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

## <a name="dequepop_back-stlclr"></a><a name="pop_back"></a>deque::p op_back (STL/CLR)

Odstraní poslední prvek.

### <a name="syntax"></a>Syntaxe

```cpp
void pop_back();
```

### <a name="remarks"></a>Poznámky

Členská funkce odstraní poslední prvek kontrolované sekvence, který nesmí být prázdný. Použijete ho k zkrácení deque podle jednoho prvku na pozadí.

### <a name="example"></a>Příklad

```cpp
// cliext_deque_pop_back.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
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

## <a name="dequepop_front-stlclr"></a><a name="pop_front"></a>deque::p op_front (STL/CLR)

Odstraní první prvek.

### <a name="syntax"></a>Syntaxe

```cpp
void pop_front();
```

### <a name="remarks"></a>Poznámky

Členská funkce odstraní první prvek kontrolované sekvence, který nesmí být prázdný. Použijete ho k zkrácení deque o jeden prvek v popředí.

### <a name="example"></a>Příklad

```cpp
// cliext_deque_pop_front.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
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

## <a name="dequepush_back-stlclr"></a><a name="push_back"></a>deque::p ush_back (STL/CLR)

Přidá nový poslední prvek.

### <a name="syntax"></a>Syntaxe

```cpp
void push_back(value_type val);
```

### <a name="remarks"></a>Poznámky

Členská funkce vloží element s hodnotou `val` na konci řízené sekvence. Použijete ho k připojení jiného elementu k deque.

### <a name="example"></a>Příklad

```cpp
// cliext_deque_push_back.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
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

## <a name="dequepush_front-stlclr"></a><a name="push_front"></a>deque::p ush_front (STL/CLR)

Přidá nový první prvek.

### <a name="syntax"></a>Syntaxe

```cpp
void push_front(value_type val);
```

### <a name="remarks"></a>Poznámky

Členská funkce vloží prvek s hodnotou `val` na začátku řízené sekvence. Použijete ho k předřazení jiného elementu deque.

### <a name="example"></a>Příklad

```cpp
// cliext_deque_push_front.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
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

## <a name="dequerbegin-stlclr"></a><a name="rbegin"></a>deque:: rbegin (STL/CLR)

Určuje začátek obrácené kontrolované sekvence.

### <a name="syntax"></a>Syntaxe

```cpp
reverse_iterator rbegin();
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí reverzní iterátor, který určuje poslední prvek řízené sekvence nebo těsně za začátek prázdné sekvence. Proto určuje `beginning` reverzní sekvence. Použijete ho k získání iterátoru, který určí `current` začátkem kontrolované sekvence v obráceném pořadí, ale jeho stav se může změnit, pokud se změní délka kontrolované sekvence.

### <a name="example"></a>Příklad

```cpp
// cliext_deque_rbegin.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect first two items in reversed sequence
    cliext::deque<wchar_t>::reverse_iterator rit = c1.rbegin();
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

## <a name="dequereference-stlclr"></a><a name="reference"></a>deque:: Reference (STL/CLR)

Typ odkazu na prvek

### <a name="syntax"></a>Syntaxe

```cpp
typedef value_type% reference;
```

### <a name="remarks"></a>Poznámky

Typ popisuje odkaz na prvek.

### <a name="example"></a>Příklad

```cpp
// cliext_deque_reference.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    cliext::deque<wchar_t>::iterator it = c1.begin();
    for (; it != c1.end(); ++it)
        {   // get a reference to an element
        cliext::deque<wchar_t>::reference ref = *it;
        System::Console::Write("{0} ", ref);
        }
    System::Console::WriteLine();

    // modify contents " a b c"
    for (it = c1.begin(); it != c1.end(); ++it)
        {   // get a reference to an element
        cliext::deque<wchar_t>::reference ref = *it;

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

## <a name="dequerend-stlclr"></a><a name="rend"></a>deque:: rend (STL/CLR)

Určuje konec reverzní kontrolované sekvence.

### <a name="syntax"></a>Syntaxe

```cpp
reverse_iterator rend();
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí reverzní iterátor, který odkazuje hned za začátek řízené sekvence. Proto určuje `end` reverzní sekvence. Použijete ho k získání iterátoru, který určuje `current` konec řízené sekvence v obráceném pořadí, ale jeho stav se může změnit, pokud se změní délka kontrolované sekvence.

### <a name="example"></a>Příklad

```cpp
// cliext_deque_rend.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect first two items
    cliext::deque<wchar_t>::reverse_iterator rit = c1.rend();
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

## <a name="dequeresize-stlclr"></a><a name="resize"></a>deque:: Resize (STL/CLR)

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

Členské funkce zajistí, že [deque:: Size (STL/CLR)](#size)`()` vrátí *new_size*. Je-li nutné řídit sekvenci déle, První členská funkce připojí prvky s hodnotou `value_type()`, zatímco druhá členská funkce připojí prvky s hodnotou *Val*. Chcete-li nastavit kratší sekvenci, obě členské funkce efektivně vymažou poslední prvek [deque:: Size (STL/CLR)](#size)`() -` `new_size` časy. Slouží k zajištění, že řízená sekvence má velikost *new_size*, buď oříznutím nebo odsazením aktuálně řízené sekvence.

### <a name="example"></a>Příklad

```cpp
// cliext_deque_resize.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
// construct an empty container and pad with default values
    cliext::deque<wchar_t> c1;
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

## <a name="dequereverse_iterator-stlclr"></a><a name="reverse_iterator"></a>deque:: reverse_iterator (STL/CLR)

Typ reverzního iterátoru řízené sekvence.

### <a name="syntax"></a>Syntaxe

```cpp
typedef T3 reverse_iterator;
```

### <a name="remarks"></a>Poznámky

Typ popisuje objekt nespecifikovaného typu `T3`, který může sloužit jako reverzní iterátor pro řízenou sekvenci.

### <a name="example"></a>Příklad

```cpp
// cliext_deque_reverse_iterator.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c" reversed
    cliext::deque<wchar_t>::reverse_iterator rit = c1.rbegin();
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

## <a name="dequesize-stlclr"></a><a name="size"></a>deque:: Size (STL/CLR)

Spočítá počet prvků.

### <a name="syntax"></a>Syntaxe

```cpp
size_type size();
```

### <a name="remarks"></a>Poznámky

Členská funkce vrací délku řízené sekvence. Použijete ji k určení počtu prvků, které jsou aktuálně v řízené sekvenci. Pokud vás zajímá, zda má sekvence nenulovou velikost, přečtěte si téma [deque:: Empty (STL/CLR)](#empty)`()`.

### <a name="example"></a>Příklad

```cpp
// cliext_deque_size.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
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

## <a name="dequesize_type-stlclr"></a><a name="size_type"></a>deque:: size_type (STL/CLR)

Typ podepsané vzdálenosti mezi dvěma prvky.

### <a name="syntax"></a>Syntaxe

```cpp
typedef int size_type;
```

### <a name="remarks"></a>Poznámky

Typ popisuje nezáporný počet prvků.

### <a name="example"></a>Příklad

```cpp
// cliext_deque_size_type.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // compute positive difference
    cliext::deque<wchar_t>::size_type diff = c1.end() - c1.begin();
    System::Console::WriteLine("end()-begin() = {0}", diff);
    return (0);
    }
```

```Output
a b c
end()-begin() = 3
```

## <a name="dequeswap-stlclr"></a><a name="swap"></a>deque:: swap (STL/CLR)

Zamění obsah dvou kontejnerů.

### <a name="syntax"></a>Syntaxe

```cpp
void swap(deque<Value>% right);
```

#### <a name="parameters"></a>Parametry

*Kliknutím*<br/>
Kontejner pro prohození obsahu pomocí.

### <a name="remarks"></a>Poznámky

Členská funkce přemění kontrolované sekvence mezi `*this` a *pravou*. Provede to v konstantním čase a nevyvolává žádné výjimky. Použijete ho jako rychlý způsob, jak vyměňovat obsah dvou kontejnerů.

### <a name="example"></a>Příklad

```cpp
// cliext_deque_swap.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct another container with repetition of values
    cliext::deque<wchar_t> c2(5, L'x');
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

## <a name="dequeto_array-stlclr"></a><a name="to_array"></a>deque:: to_array (STL/CLR)

Zkopíruje řízenou sekvenci do nového pole.

### <a name="syntax"></a>Syntaxe

```cpp
cli::array<Value>^ to_array();
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí pole obsahující řízenou sekvenci. Použijete ho k získání kopie řízené sekvence ve formuláři Array.

### <a name="example"></a>Příklad

```cpp
// cliext_deque_to_array.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
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

## <a name="dequevalue_type-stlclr"></a><a name="value_type"></a>deque:: value_type (STL/CLR)

Typ prvku

### <a name="syntax"></a>Syntaxe

```cpp
typedef Value value_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro *hodnotu*parametru šablony.

### <a name="example"></a>Příklad

```cpp
// cliext_deque_value_type.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c" using value_type
    for (cliext::deque<wchar_t>::iterator it = c1.begin();
        it != c1.end(); ++it)
        {   // store element in value_type object
        cliext::deque<wchar_t>::value_type val = *it;

        System::Console::Write("{0} ", val);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="operatorlt-deque-stlclr"></a><a name="op_lt"></a>operator&lt; (deque) – operátor (STL/CLR)

Deque je menší než porovnání.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Value>
    bool operator<(deque<Value>% left,
        deque<Value>% right);
```

#### <a name="parameters"></a>Parametry

*zbývá*<br/>
Levý kontejner, který se má porovnat

*Kliknutím*<br/>
Pravý kontejner, který se má porovnat

### <a name="remarks"></a>Poznámky

Funkce operator vrátí hodnotu true, pokud `i` nejnižší pozice, pro kterou `!(right[i] < left[i])` je také true `left[i] < right[i]`. V opačném případě vrátí `left->size() < right->size()` použijete k otestování, zda je před *pravou* seřazena druhá *deques, pokud* jsou tyto dva prvky porovnány.

### <a name="example"></a>Příklad

```cpp
// cliext_deque_operator_lt.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    cliext::deque<wchar_t> c2;
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

## <a name="operatorlt-deque-stlclr"></a><a name="op_lteq"></a>operator&lt;= (deque) – operátor (STL/CLR)

Deque je menší než nebo rovno porovnání.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Value>
    bool operator<=(deque<Value>% left,
        deque<Value>% right);
```

#### <a name="parameters"></a>Parametry

*zbývá*<br/>
Levý kontejner, který se má porovnat

*Kliknutím*<br/>
Pravý kontejner, který se má porovnat

### <a name="remarks"></a>Poznámky

Funkce operátoru vrací `!(right < left)`. Použijete ho k otestování *, jestli není* po *pravé straně* , když jsou tyto dva deques porovnávány, v porovnání s elementy podle elementu.

### <a name="example"></a>Příklad

```cpp
// cliext_deque_operator_le.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    cliext::deque<wchar_t> c2;
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

## <a name="operator-deque-stlclr"></a><a name="op_as"></a>operator = (deque) – operátor (STL/CLR)

Nahradí řízenou sekvenci.

### <a name="syntax"></a>Syntaxe

```cpp
deque<Value>% operator=(deque<Value>% right);
```

#### <a name="parameters"></a>Parametry

*Kliknutím*<br/>
Kontejner ke zkopírování.

### <a name="remarks"></a>Poznámky

Operátor členu kopíruje *přímo* na objekt a potom vrátí `*this`. Použijete ji k nahrazení kontrolované sekvence kopií kontrolované sekvence *vpravo*.

### <a name="example"></a>Příklad

```cpp
// cliext_deque_operator_as.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    cliext::deque<wchar_t> c2;
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

## <a name="operator-deque-stlclr"></a><a name="op_eq"></a>operator = = (deque) – operátor (STL/CLR)

Deque stejné porovnání.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Value>
    bool operator==(deque<Value>% left,
        deque<Value>% right);
```

#### <a name="parameters"></a>Parametry

*zbývá*<br/>
Levý kontejner, který se má porovnat

*Kliknutím*<br/>
Pravý kontejner, který se má porovnat

### <a name="remarks"></a>Poznámky

Funkce operator vrátí hodnotu true pouze v případě, že sekvence řízené *levou* a *pravou* mají stejnou délku a pro každou pozici `i``left[i] ==` `right[i]`. Použijete ji k otestování, zda je *levé* řazení stejné jako *pravé* , pokud jsou obě deques porovnány podle prvku.

### <a name="example"></a>Příklad

```cpp
// cliext_deque_operator_eq.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    cliext::deque<wchar_t> c2;
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

## <a name="operatorgt-deque-stlclr"></a><a name="op_gt"></a>operator&gt; (deque) – operátor (STL/CLR)

Deque je větší než porovnání.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Value>
    bool operator>(deque<Value>% left,
        deque<Value>% right);
```

#### <a name="parameters"></a>Parametry

*zbývá*<br/>
Levý kontejner, který se má porovnat

*Kliknutím*<br/>
Pravý kontejner, který se má porovnat

### <a name="remarks"></a>Poznámky

Funkce operator vrací `right` `<` `left`. Použijete ho k otestování *, zda je* po *pravé* době řazení obou deques porovnáváno na prvek podle prvku.

### <a name="example"></a>Příklad

```cpp
// cliext_deque_operator_gt.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    cliext::deque<wchar_t> c2;
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

## <a name="operatorgt-deque-stlclr"></a><a name="op_gteq"></a>operator&gt;= (deque) – operátor (STL/CLR)

Deque je větší než nebo rovno porovnání.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Value>
    bool operator>=(deque<Value>% left,
        deque<Value>% right);
```

#### <a name="parameters"></a>Parametry

*zbývá*<br/>
Levý kontejner, který se má porovnat

*Kliknutím*<br/>
Pravý kontejner, který se má porovnat

### <a name="remarks"></a>Poznámky

Funkce operator vrací `!(left` `<` `right)`. Použijete ji k otestování, zda je *ponecháno* před *pravou* , pokud jsou obě deques porovnány s prvkem podle elementu.

### <a name="example"></a>Příklad

```cpp
// cliext_deque_operator_ge.cpp
// compile with: /clr
#include <cliext/deque>

int main()
    {
    cliext::deque<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    cliext::deque<wchar_t> c2;
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
