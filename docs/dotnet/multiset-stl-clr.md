---
title: multiset (STL/CLR)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cliext::multiset
- cliext::multiset::begin
- cliext::multiset::clear
- cliext::multiset::const_iterator
- cliext::multiset::const_reference
- cliext::multiset::const_reverse_iterator
- cliext::multiset::count
- cliext::multiset::difference_type
- cliext::multiset::empty
- cliext::multiset::end
- cliext::multiset::equal_range
- cliext::multiset::erase
- cliext::multiset::find
- cliext::multiset::generic_container
- cliext::multiset::generic_iterator
- cliext::multiset::generic_reverse_iterator
- cliext::multiset::generic_value
- cliext::multiset::insert
- cliext::multiset::iterator
- cliext::multiset::key_comp
- cliext::multiset::key_compare
- cliext::multiset::key_type
- cliext::multiset::lower_bound
- cliext::multiset::make_value
- cliext::multiset::multiset
- cliext::multiset::operator=
- cliext::multiset::rbegin
- cliext::multiset::reference
- cliext::multiset::rend
- cliext::multiset::reverse_iterator
- cliext::multiset::size
- cliext::multiset::size_type
- cliext::multiset::swap
- cliext::multiset::to_array
- cliext::multiset::upper_bound
- cliext::multiset::value_comp
- cliext::multiset::value_compare
- cliext::multiset::value_type
- cliext::multiset::operator!=
- cliext::multiset::operator<
- cliext::multiset::operator<=
- cliext::multiset::operator==
- cliext::multiset::operator>
- cliext::multiset::operator>=
helpviewer_keywords:
- <cliext/set> header [STL/CLR]
- <set> header [STL/CLR]
- multiset class [STL/CLR]
- begin member [STL/CLR]
- clear member [STL/CLR]
- const_iterator member [STL/CLR]
- const_reference member [STL/CLR]
- const_reverse_iterator member [STL/CLR]
- count member [STL/CLR]
- difference_type member [STL/CLR]
- empty member [STL/CLR]
- end member [STL/CLR]
- equal_range member [STL/CLR]
- erase member [STL/CLR]
- find member [STL/CLR]
- generic_container member [STL/CLR]
- generic_iterator member [STL/CLR]
- generic_reverse_iterator member [STL/CLR]
- generic_value member [STL/CLR]
- insert member [STL/CLR]
- iterator member [STL/CLR]
- key_comp member [STL/CLR]
- key_compare member [STL/CLR]
- key_type member [STL/CLR]
- lower_bound member [STL/CLR]
- make_value member [STL/CLR]
- map member [STL/CLR]
- mapped_type member [STL/CLR]
- operator= member [STL/CLR]
- operator member [STL/CLR]
- rbegin member [STL/CLR]
- reference member [STL/CLR]
- rend member [STL/CLR]
- reverse_iterator member [STL/CLR]
- size member [STL/CLR]
- size_type member [STL/CLR]
- swap member [STL/CLR]
- to_array member [STL/CLR]
- upper_bound member [STL/CLR]
- value_comp member [STL/CLR]
- value_compare member [STL/CLR]
- value_type member [STL/CLR]
- operator!= member [STL/CLR]
- operator< member [STL/CLR]
- operator<= member [STL/CLR]
- operator== member [STL/CLR]
- operator> member [STL/CLR]
- operator>= member [STL/CLR]
ms.assetid: 7c46e2b4-cd88-49b7-a9e6-63ad5ae7feb5
ms.openlocfilehash: e7a0551c1d75993d588f5dbb369989c42a71d903
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50557727"
---
# <a name="multiset-stlclr"></a>multiset (STL/CLR)

Třída šablony popisuje objekt, který řídí různé délky sekvence elementů, která má obousměrný přístup. Použití kontejneru `multiset` , spravovat řadu prvků, jako větve (téměř) s vyrovnáváním seřazených uzlů, každý ukládání jeden element.

V popisu níže `GValue` je stejný jako `GKey`, který je stejný jako *klíč* Pokud je typ odkazu, v takovém případě je `Key^`.

## <a name="syntax"></a>Syntaxe

```cpp
template<typename Key>
    ref class multiset
        :   public
        System::ICloneable,
        System::Collections::IEnumerable,
        System::Collections::ICollection,
        System::Collections::Generic::IEnumerable<GValue>,
        System::Collections::Generic::ICollection<GValue>,
        System::Collections::Generic::IList<GValue>,
        Microsoft::VisualC::StlClr::ITree<Gkey, GValue>
    { ..... };
```

### <a name="parameters"></a>Parametry

*Key*<br/>
Typ klíčovou komponentou elementu v řízené sekvenci.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<cliext – / set >

**Namespace:** cliext –

## <a name="declarations"></a>Deklarace

|Definice typu|Popis|
|---------------------|-----------------|
|[multiset::const_iterator (STL/CLR)](#const_iterator)|Typ konstantního iterátoru řízené sekvence|
|[multiset::const_reference (STL/CLR)](#const_reference)|Typ konstantního odkazu na prvek|
|[multiset::const_reverse_iterator (STL/CLR)](#const_reverse_iterator)|Typ konstantního zpětného iterátoru řízené sekvence.|
|[multiset::difference_type (STL/CLR)](#difference_type)|Typ (může být podepsaná) vzdálenosti mezi dvěma prvky.|
|[multiset::generic_container (STL/CLR)](#generic_container)|Typ obecné rozhraní pro kontejner.|
|[multiset::generic_iterator (STL/CLR)](#generic_iterator)|Typ iterátoru pro obecné rozhraní pro kontejner.|
|[multiset::generic_reverse_iterator (STL/CLR)](#generic_reverse_iterator)|Typ "reverse iterator" pro obecné rozhraní pro kontejner.|
|[multiset::generic_value (STL/CLR)](#generic_value)|Typ elementu pro obecné rozhraní pro kontejner.|
|[multiset::iterator (STL/CLR)](#iterator)|Typ iterátoru řízené sekvence|
|[multiset::key_compare (STL/CLR)](#key_compare)|Pořadí delegáta pro dva klíče.|
|[multiset::key_type (STL/CLR)](#key_type)|Typ klíče řazení|
|[multiset::reference (STL/CLR)](#reference)|Typ odkazu na prvek|
|[multiset::reverse_iterator (STL/CLR)](#reverse_iterator)|Typ "reverse iterator" pro řízenou sekvenci.|
|[multiset::size_type (STL/CLR)](#size_type)|Typ vzdálenosti (nezáporné) mezi dvěma prvky.|
|[multiset::value_compare (STL/CLR)](#value_compare)|Pořadí delegáta pro dvě hodnoty prvků.|
|[multiset::value_type (STL/CLR)](#value_type)|Typ prvku|

|Členská funkce|Popis|
|---------------------|-----------------|
|[multiset::begin (STL/CLR)](#begin)|Určuje začátek řízené sekvence.|
|[multiset::clear (STL/CLR)](#clear)|Odebere všechny prvky.|
|[multiset::count (STL/CLR)](#count)|Vrátí počet prvků odpovídající zadanému klíči.|
|[multiset::empty (STL/CLR)](#empty)|Zkouší, zda nejsou přítomny žádné prvky.|
|[multiset::end (STL/CLR)](#end)|Určuje konec řízené sekvence.|
|[multiset::equal_range (STL/CLR)](#equal_range)|Najde rozsah, který odpovídá zadanému klíči.|
|[multiset::erase (STL/CLR)](#erase)|Odebere prvky v určených pozicích.|
|[multiset::find (STL/CLR)](#find)|Vyhledá prvek, který odpovídá zadanému klíči.|
|[multiset::insert (STL/CLR)](#insert)|Přidá prvky.|
|[multiset::key_comp (STL/CLR)](#key_comp)|Zkopíruje pořadí delegáta pro dva klíče.|
|[multiset::lower_bound (STL/CLR)](#lower_bound)|Vyhledá počátek rozsahu, který odpovídá zadanému klíči.|
|[multiset::make_value (STL/CLR)](#make_value)|Vytvoří objekt hodnoty.|
|[multiset::multiset (STL/CLR)](#multiset)|Sestaví objekt kontejneru.|
|[multiset::rbegin (STL/CLR)](#rbegin)|Určuje začátek řízené obrácené sekvenci.|
|[multiset::rend (STL/CLR)](#rend)|Určuje konec řízené obrácené sekvenci.|
|[multiset::size (STL/CLR)](#size)|Spočítá počet prvků.|
|[multiset::swap (STL/CLR)](#swap)|Zamění obsah dvou kontejnerů.|
|[multiset::to_array (STL/CLR)](#to_array)|Zkopíruje do nového pole řízené sekvence.|
|[multiset::upper_bound (STL/CLR)](#upper_bound)|Najde konec rozsahu, který odpovídá zadanému klíči.|
|[multiset::value_comp (STL/CLR)](#value_comp)|Zkopíruje pořadí delegáta pro dvě hodnoty prvků.|

|Operátor|Popis|
|--------------|-----------------|
|[multiset::operator= (STL/CLR)](#op_as)|Nahradí řízené sekvence.|
|[operator!= (multiset) (STL/CLR)](#op_neq)|Určuje, zda `multiset` není roven jinému objektu `multiset` objektu.|
|[operator< (multiset) (STL/CLR)](#op_lt)|Určuje, zda `multiset` je menší než jiný objekt `multiset` objektu.|
|[operator<= (multiset) (STL/CLR)](#op_lteq)|Určuje, zda `multiset` objekt je menší nebo rovna jiné `multiset` objektu.|
|[operator== (multiset) (STL/CLR)](#op_eq)|Určuje, zda `multiset` je roven jinému objektu `multiset` objektu.|
|[operator> (multiset) (STL/CLR)](#op_gt)|Určuje, zda `multiset` je větší než jiný objekt `multiset` objektu.|
|[operator>= (multiset) (STL/CLR)](#op_gteq)|Určuje, zda `multiset` objekt je větší než nebo roven jinému `multiset` objektu.|

## <a name="interfaces"></a>Rozhraní

|Rozhraní|Popis|
|---------------|-----------------|
|<xref:System.ICloneable>|Duplicitní objektu.|
|<xref:System.Collections.IEnumerable>|Pořadí mezi prvky.|
|<xref:System.Collections.ICollection>|Údržba skupiny prvků.|
|<xref:System.Collections.Generic.IEnumerable%601>|Pořadí pomocí zadané elementy.|
|<xref:System.Collections.Generic.ICollection%601>|Údržba skupiny zadané elementy.|
|ITree\<klíč, hodnota >|Udržujte obecný kontejneru.|

## <a name="remarks"></a>Poznámky

Objekt přiděluje a uvolňuje úložiště pro sekvenci, ovládací prvky jako jednotlivé uzly. Vloží prvky do (téměř) s vyrovnáváním strom, který udržuje seřazený tím, že změna vazby mezi uzly, nikdy zkopírováním obsah jednoho uzlu do jiného. To znamená, že můžete vložit a odebrat elementy volně bez narušení zbývající prvky.

Objekt seřadí sekvence pomocí volání uloženého delegáta objekt typu [multiset::key_compare (STL/CLR)](../dotnet/multiset-key-compare-stl-clr.md). Můžete zadat objekt uložené delegáta při konstrukci multiset; Pokud chcete zadat žádný objekt. delegát, výchozí hodnota je porovnání `operator<(key_type, key_type)`. Přístup k tomuto uloženého objektu voláním členské funkce [multiset::key_comp (STL/CLR)](../dotnet/multiset-key-comp-stl-clr.md)`()`.

Takový objekt delegáta musí uložit přísné slabé seřazení klíčů typu [multiset::key_type (STL/CLR)](../dotnet/multiset-key-type-stl-clr.md). To znamená pro jakékoli dva klíče `X` a `Y`:

`key_comp()(X, Y)` Vrátí výsledek stejný datový typ Boolean při každém volání.

Pokud `key_comp()(X, Y)` má hodnotu true, pak `key_comp()(Y, X)` musí mít hodnotu false.

Pokud `key_comp()(X, Y)` má hodnotu true, pak `X` říká, že je řazen před `Y`.

Pokud `!key_comp()(X, Y) && !key_comp()(Y, X)` má hodnotu true, pak `X` a `Y` se říká, že mají ekvivalentní řazení.

Pro libovolný element `X` , která předchází `Y` v řízené sekvenci `key_comp()(Y, X)` má hodnotu false. (Pro výchozí objekt delegáta, klíče nikdy snížení hodnoty.) Na rozdíl od třídy šablony [nastavit (STL/CLR)](../dotnet/set-stl-clr.md), objekt třídy šablony `multiset` nevyžaduje, aby byly jedinečné klíče pro všechny elementy. (Dva nebo více klíčů může mít odpovídající řazení.)

Každý prvek slouží jako ey a hodnotu. Sekvence je reprezentována způsobem, který umožňuje vyhledávání, vkládání a odstranění libovolný prvek s počtem operací úměrný logaritmu počtu prvků v sekvenci (logaritmické čas). Vkládání prvků navíc nezruší platnost žádných iterátorů a odstranění prvku zruší platnost pouze těch iterátorů, které odkazují na odstraněný prvek.

Použita třída multiset podporuje obousměrné iterátory, což znamená, že přejdete na sousedící prvky zadaný iterátor, který určuje elementu v řízené sekvenci. Speciální hlavního uzlu odpovídá iterátorů vrácené [multiset::end (STL/CLR)](../dotnet/multiset-end-stl-clr.md)`()`. Tento iterátor, který má přístup po posledním prvku v řízené sekvenci lze snížit, pokud jsou k dispozici. Můžete zvýšit multiset – iterátor, který má přístup k hlavnímu uzlu a budou pak porovnat rovna `end()`. Nelze přistoupit přes ukazatel vrátí iterátor, ale `end()`.

Všimněte si, že nemůže odkazovat na prvek multiset – přímo zadané pozici číselné –, který vyžaduje iterátor náhodného přístupu.

Multiset – iterátoru uloží popisovač do přidružené multiset – uzlu, který je pak uloží popisovač pro jeho přiřazeným kontejnerem. Iterátory lze použít pouze objekty, které přiřazeným kontejnerem. Pokud je jeho přidružený uzel multiset – přidružené nějaké multiset iterátor multiset – zůstává v platnosti. Kromě toho je platný iterátoru přesměrovat – slouží k přístupu nebo změnit hodnotu prvku jmenuje--tak dlouho, dokud se nerovná `end()`.

Smazání nebo odstranění prvku volá destruktor pro jeho uložené hodnotě. Zničení kontejneru vymaže všechny prvky. Kontejner, jehož typ prvku je třídy ref class tak, zajišťuje, že žádné elementy něj kontejneru. Mějte na paměti, ale, že kontejner zpracovává nemá *není* zničit jeho prvků.

## <a name="members"></a>Členové

## <a name="begin"></a> multiset::begin (STL/CLR)

Určuje začátek řízené sekvence.

### <a name="syntax"></a>Syntaxe

```cpp
iterator begin();
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí obousměrný iterátor, který určuje první prvek řízenou sekvenci nebo přesně za konec k prázdné sekvenci. Můžete ji použít k získání iterátor, který určuje `current` začátek řízené sekvence, ale jeho stav můžete změnit, pokud se změní délka řízené sekvence.

### <a name="example"></a>Příklad

```cpp
// cliext_multiset_begin.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect first two items
    Mymultiset::iterator it = c1.begin();
    System::Console::WriteLine("*begin() = {0}", *it);
    System::Console::WriteLine("*++begin() = {0}", *++it);
    return (0);
    }
```

```Output
a b c
*begin() = a
*++begin() = b
```

## <a name="clear"></a> multiset::clear (STL/CLR)

Odebere všechny prvky.

### <a name="syntax"></a>Syntaxe

```cpp
void clear();
```

### <a name="remarks"></a>Poznámky

Členská funkce efektivně volá [multiset::erase (STL/CLR)](../dotnet/multiset-erase-stl-clr.md) `(` [multiset::begin (STL/CLR)](../dotnet/multiset-begin-stl-clr.md) `(),` [multiset::end (STL/CLR)](../dotnet/multiset-end-stl-clr.md) `())`. Použijete ji k zajištění, že je prázdná řízené sekvence.

### <a name="example"></a>Příklad

```cpp
// cliext_multiset_clear.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // clear the container and reinspect
    c1.clear();
    System::Console::WriteLine("size() = {0}", c1.size());

    // add elements and clear again
    c1.insert(L'a');
    c1.insert(L'b');

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

## <a name="const_iterator"></a> multiset::const_iterator (STL/CLR)

Typ konstantního iterátoru řízené sekvence

### <a name="syntax"></a>Syntaxe

```cpp
typedef T2 const_iterator;
```

### <a name="remarks"></a>Poznámky

Typ popisuje objekt neurčeného typu `T2` , který může sloužit jako konstantní obousměrného iterátoru řízené sekvence.

### <a name="example"></a>Příklad

```cpp
// cliext_multiset_const_iterator.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    Mymultiset::const_iterator cit = c1.begin();
    for (; cit != c1.end(); ++cit)
        System::Console::Write("{0} ", *cit);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="const_reference"></a> multiset::const_reference (STL/CLR)

Typ konstantního odkazu na prvek

### <a name="syntax"></a>Syntaxe

```cpp
typedef value_type% const_reference;
```

### <a name="remarks"></a>Poznámky

Typ, který popisuje konstantní odkaz na element.

### <a name="example"></a>Příklad

```cpp
// cliext_multiset_const_reference.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    Mymultiset::const_iterator cit = c1.begin();
    for (; cit != c1.end(); ++cit)
        {   // get a const reference to an element
        Mymultiset::const_reference cref = *cit;
        System::Console::Write("{0} ", cref);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="const_reverse_iterator"></a> multiset::const_reverse_iterator (STL/CLR)

Typ konstantního zpětného iterátoru řízené sekvence...

### <a name="syntax"></a>Syntaxe

```cpp
typedef T4 const_reverse_iterator;
```

### <a name="remarks"></a>Poznámky

Typ popisuje objekt neurčeného typu `T4` , který může sloužit jako konstantní zpětného iterátoru řízené sekvence.

### <a name="example"></a>Příklad

```cpp
// cliext_multiset_const_reverse_iterator.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c" reversed
    Mymultiset::const_reverse_iterator crit = c1.rbegin();
    for (; crit != c1.rend(); ++crit)
        System::Console::Write("{0} ", *crit);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c b a
```

## <a name="count"></a> multiset::Count (STL/CLR)

Zjistí počet prvků odpovídající zadanému klíči.

### <a name="syntax"></a>Syntaxe

```cpp
size_type count(key_type key);
```

#### <a name="parameters"></a>Parametry

*Klíč*<br/>
Hodnota klíče pro hledání.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí počet prvků v řízené sekvenci, která mají stejné pořadí s *klíč*. Použijete ji k určení počtu prvků v řízené sekvenci aktuálně, které odpovídají zadanému klíči.

### <a name="example"></a>Příklad

```cpp
// cliext_multiset_count.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("count(L'A') = {0}", c1.count(L'A'));
    System::Console::WriteLine("count(L'b') = {0}", c1.count(L'b'));
    System::Console::WriteLine("count(L'C') = {0}", c1.count(L'C'));
    return (0);
    }
```

```Output
a b c
count(L'A') = 0
count(L'b') = 1
count(L'C') = 0
```

## <a name="difference_type"></a> multiset::difference_type (STL/CLR)

Typ vzdálenosti se znaménkem mezi dvěma prvky.

### <a name="syntax"></a>Syntaxe

```cpp
typedef int difference_type;
```

### <a name="remarks"></a>Poznámky

Typ, který popisuje element může být záporný počet.

### <a name="example"></a>Příklad

```cpp
// cliext_multiset_difference_type.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // compute positive difference
    Mymultiset::difference_type diff = 0;
    for (Mymultiset::iterator it = c1.begin(); it != c1.end(); ++it)
        ++diff;
    System::Console::WriteLine("end()-begin() = {0}", diff);

    // compute negative difference
    diff = 0;
    for (Mymultiset::iterator it = c1.end(); it != c1.begin(); --it)
        --diff;
    System::Console::WriteLine("begin()-end() = {0}", diff);
    return (0);
    }
```

```Output
a b c
end()-begin() = 3
begin()-end() = -3
```

## <a name="empty"></a> multiset::Empty (STL/CLR)

Zkouší, zda nejsou přítomny žádné prvky.

### <a name="syntax"></a>Syntaxe

```cpp
bool empty();
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí hodnotu true pro prázdnou řízenou sekvenci. Je ekvivalentní [multiset::size (STL/CLR)](../dotnet/multiset-size-stl-clr.md)`() == 0`. Použijete ji k ověření, zda třída multiset je prázdný.

### <a name="example"></a>Příklad

```cpp
// cliext_multiset_empty.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

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

## <a name="end"></a> multiset::end (STL/CLR)

Určuje konec řízené sekvence.

### <a name="syntax"></a>Syntaxe

```cpp
iterator end();
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí obousměrný iterátor, který ukazuje za konec řízené sekvence. Můžete ji použít k získání iterátor, který určuje konec řízené sekvence; jeho stav kódu ne změnit, pokud se změní délka řízené sekvence.

### <a name="example"></a>Příklad

```cpp
// cliext_multiset_end.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect last two items
    Mymultiset::iterator it = c1.end();
    --it;
    System::Console::WriteLine("*-- --end() = {0}", *--it);
    System::Console::WriteLine("*--end() = {0}", *++it);
    return (0);
    }
```

```Output
a b c
*-- --end() = b
*--end() = c
```

## <a name="equal_range"></a> multiset::equal_range (STL/CLR)

Najde rozsah, který odpovídá zadanému klíči.

### <a name="syntax"></a>Syntaxe

```cpp
cliext::pair<iterator, iterator> equal_range(key_type key);
```

#### <a name="parameters"></a>Parametry

*Klíč*<br/>
Hodnota klíče pro hledání.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí pár iterátorů `cliext::pair<iterator, iterator>(` [multiset::lower_bound (STL/CLR)](../dotnet/multiset-lower-bound-stl-clr.md) `(key),` [multiset::upper_bound (STL/CLR)](../dotnet/multiset-upper-bound-stl-clr.md)`(key))`. Použijete ji k určení rozsahu prvků v řízené sekvenci aktuálně, které odpovídají zadanému klíči.

### <a name="example"></a>Příklad

```cpp
// cliext_multiset_equal_range.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
typedef Mymultiset::pair_iter_iter Pairii;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // display results of failed search
    Pairii pair1 = c1.equal_range(L'x');
    System::Console::WriteLine("equal_range(L'x') empty = {0}",
        pair1.first == pair1.second);

    // display results of successful search
    pair1 = c1.equal_range(L'b');
    for (; pair1.first != pair1.second; ++pair1.first)
        System::Console::Write("{0} ", *pair1.first);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
equal_range(L'x') empty = True
b
```

## <a name="erase"></a> multiset::Erase (STL/CLR)

Odebere prvky v určených pozicích.

### <a name="syntax"></a>Syntaxe

```cpp
iterator erase(iterator where);
iterator erase(iterator first, iterator last);
size_type erase(key_type key)
```

#### <a name="parameters"></a>Parametry

*první*<br/>
Začátek rozsahu vymazat.

*Klíč*<br/>
Hodnota klíče vymazat.

*poslední*<br/>
Konec rozsahu vymazat.

*kde*<br/>
Element vymazat.

### <a name="remarks"></a>Poznámky

První členská funkce odstraní prvek řízené sekvence, na které odkazuje *kde*a vrátí iterátor, který určuje první prvek zbývající za prvkem, který odebere, nebo [multiset::end (STL / CLR)](../dotnet/multiset-end-stl-clr.md) `()` Pokud žádný takový prvek neexistuje. Použijete ji k odebrání jeden element.

Druhá členská funkce odebere prvky řízené sekvence v rozsahu [`first`, `last`) a vrátí iterátor, který určuje první prvek zbývající za všemi odstraněnými prvky, nebo `end()` Pokud žádný takový prvek existuje... Použijete ji k odebrání nula nebo více souvislých prvků.

Třetí členská funkce odstraní libovolný prvek řízenou sekvenci, jehož klíč má ekvivalentní řazení na *klíč*a vrátí počet prvků, které jsou odebrány. Použijete ho odebrat a spočítat všechny elementy, které odpovídají zadanému klíči.

Každý prvek mazání trvá určitou dobu úměrný logaritmu počtu prvků v řízené sekvenci.

### <a name="example"></a>Příklad

```cpp
// cliext_multiset_erase.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // erase an element and reinspect
    System::Console::WriteLine("erase(begin()) = {0}",
        *c1.erase(c1.begin()));

    // add elements and display " b c d e"
    c1.insert(L'd');
    c1.insert(L'e');
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // erase all but end
    Mymultiset::iterator it = c1.end();
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

## <a name="find"></a> multiset::Find (STL/CLR)

Vyhledá prvek, který odpovídá zadanému klíči.

### <a name="syntax"></a>Syntaxe

```cpp
iterator find(key_type key);
```

#### <a name="parameters"></a>Parametry

*Klíč*<br/>
Hodnota klíče pro hledání.

### <a name="remarks"></a>Poznámky

Pokud má alespoň jeden element v řízené sekvenci s odpovídající řazení *klíč*, členská funkce vrátí iterátor určit jeden z těchto elementů; v opačném případě vrátí [multiset::end (STL/CLR)](../dotnet/multiset-end-stl-clr.md) `()`. Použijete ji k aktuálně vyhledejte elementu v řízené sekvenci, která odpovídá zadanému klíči.

### <a name="example"></a>Příklad

```cpp
// cliext_multiset_find.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("find {0} = {1}",
        L'A', c1.find(L'A') != c1.end());
    System::Console::WriteLine("find {0} = {1}",
        L'b', *c1.find(L'b'));
    System::Console::WriteLine("find {0} = {1}",
        L'C', c1.find(L'C') != c1.end());
    return (0);
    }
```

```Output
a b c
find A = False
find b = b
find C = False
```

## <a name="generic_container"></a> multiset::generic_container (STL/CLR)

Typ obecné rozhraní pro kontejner.

### <a name="syntax"></a>Syntaxe

```cpp
typedef Microsoft::VisualC::StlClr::
    ITree<GKey, GValue>
    generic_container;
```

### <a name="remarks"></a>Poznámky

Typ, který popisuje obecné rozhraní pro tuto třídu šablony kontejneru.

### <a name="example"></a>Příklad

```cpp
// cliext_multiset_generic_container.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct a generic container
    Mymultiset::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // modify generic and display original
    gc1->insert(L'd');
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // modify original and display generic
    c1.insert(L'e');
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
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

## <a name="generic_iterator"></a> multiset::generic_iterator (STL/CLR)

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
// cliext_multiset_generic_iterator.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct a generic container
    Mymultiset::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // get an element and display it
    Mymultiset::generic_iterator gcit = gc1->begin();
    Mymultiset::generic_value gcval = *gcit;
    System::Console::WriteLine("{0} ", gcval);
    return (0);
    }
```

```Output
a b c
a b c
a
```

## <a name="generic_reverse_iterator"></a> multiset::generic_reverse_iterator (STL/CLR)

Typ "reverse iterator" pro použití s obecné rozhraní pro kontejner.

### <a name="syntax"></a>Syntaxe

```cpp
typedef Microsoft::VisualC::StlClr::Generic::
    ReverseRandomAccessIterator<generic_value>
    generic_reverse_iterator;
```

### <a name="remarks"></a>Poznámky

Typ, který popisuje obecný zpětný iterátor, který jde použít s obecné rozhraní pro tuto třídu šablony kontejneru.

### <a name="example"></a>Příklad

```cpp
// cliext_multiset_generic_reverse_iterator.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct a generic container
    Mymultiset::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // get an element and display it
    Mymultiset::generic_reverse_iterator gcit = gc1->rbegin();
    Mymultiset::generic_value gcval = *gcit;
    System::Console::WriteLine("{0} ", gcval);
    return (0);
    }
```

```Output
a b c
a b c
c
```

## <a name="generic_value"></a> multiset::generic_value (STL/CLR)

Typ elementu pro použití s obecné rozhraní pro kontejner.

### <a name="syntax"></a>Syntaxe

```cpp
typedef GValue generic_value;
```

### <a name="remarks"></a>Poznámky

Typ, který popisuje objekt typu `GValue` hodnoty uložené elementu pro použití s obecné rozhraní pro tuto třídu šablony kontejneru, který popisuje.

### <a name="example"></a>Příklad

```cpp
// cliext_multiset_generic_value.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct a generic container
    Mymultiset::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // get an element and display it
    Mymultiset::generic_iterator gcit = gc1->begin();
    Mymultiset::generic_value gcval = *gcit;
    System::Console::WriteLine("{0} ", gcval);
    return (0);
    }
```

```Output
a b c
a b c
a
```

## <a name="insert"></a> multiset::Insert (STL/CLR)

Přidá prvky.

### <a name="syntax"></a>Syntaxe

```cpp
iterator insert(value_type val);
iterator insert(iterator where, value_type val);
template<typename InIter>
    void insert(InIter first, InIter last);
void insert(System::Collections::Generic::IEnumerable<value_type>^ right);
```

#### <a name="parameters"></a>Parametry

*první*<br/>
Začátek rozsahu pro vložení.

*poslední*<br/>
Konec rozsahu pro vložení.

*doprava*<br/>
Výčet pro vložení.

*Val*<br/>
Hodnota klíče pro vložení.

*kde*<br/>
Kde v kontejneru pro vložení (jenom pro pomocný parametr).

### <a name="remarks"></a>Poznámky

Každá z členské funkce vloží pořadí určeném zbývající operandy.

První členská funkce vloží prvek s hodnotou *val*a vrátí iterátor, který určuje nově vložený prvek. Použijete ji k vložení jeden element.

Druhá členská funkce vloží prvek s hodnotou *val*s použitím *kde* jako Nápověda (ke zlepšení výkonu) a vrátí iterátor, který určuje nově vložený prvek. Použijete ji k vložení jeden element, který může být vedle elementu, které už znáte.

Třetí členská funkce vloží sekvenci [`first`, `last`). Použijete ji k vložení nula nebo více elementů zkopírovaných z jiné pořadí.

Čtvrtá členská funkce vloží pořadí určeném *správné*. Použijete ji k vložení pořadí popsal enumerátor.

Každý prvek vložení trvá určitou dobu úměrný logaritmu počtu prvků v řízené sekvenci. Vložení situace může nastat v amortizovaném konstantním času, ale zadaný pomocného parametru, který určuje prvek vedle kurzor.

### <a name="example"></a>Příklad

```cpp
// cliext_multiset_insert.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // insert a single value, unique and duplicate
    System::Console::WriteLine("insert(L'x') = {0}",
        *c1.insert(L'x'));

    System::Console::WriteLine("insert(L'b') = {0}",
        *c1.insert(L'b'));

    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // insert a single value with hint
    System::Console::WriteLine("insert(begin(), L'y') = {0}",
        *c1.insert(c1.begin(), L'y'));
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // insert an iterator range
    Mymultiset c2;
    Mymultiset::iterator it = c1.end();
    c2.insert(c1.begin(), --it);
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // insert an enumeration
    Mymultiset c3;
    c3.insert(   // NOTE: cast is not needed
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c1);
    for each (wchar_t elem in c3)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
insert(L'x') = x
insert(L'b') = b
a b b c x
insert(begin(), L'y') = y
a b b c x y
a b b c x
a b b c x y
```

## <a name="iterator"></a> multiset::iterator (STL/CLR)

Typ iterátoru řízené sekvence

### <a name="syntax"></a>Syntaxe

```cpp
typedef T1 iterator;
```

### <a name="remarks"></a>Poznámky

Typ popisuje objekt neurčeného typu `T1` , který může sloužit jako obousměrný iterátor, který řízené sekvence.

### <a name="example"></a>Příklad

```cpp
// cliext_multiset_iterator.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    Mymultiset::iterator it = c1.begin();
    for (; it != c1.end(); ++it)
        System::Console::Write("{0} ", *it);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="key_comp"></a> multiset::key_comp (STL/CLR)

Zkopíruje pořadí delegáta pro dva klíče.

### <a name="syntax"></a>Syntaxe

```cpp
key_compare^key_comp();
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí pořadí delegáta, který slouží k seřazení řízené sekvence. Použijete ji k porovnat dva klíče.

### <a name="example"></a>Příklad

```cpp
// cliext_multiset_key_comp.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    Mymultiset::key_compare^ kcomp = c1.key_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        kcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        kcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        kcomp(L'b', L'a'));
    System::Console::WriteLine();

    // test a different ordering rule
    Mymultiset c2 = cliext::greater<wchar_t>();
    kcomp = c2.key_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        kcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        kcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        kcomp(L'b', L'a'));
    return (0);
    }
```

```Output
compare(L'a', L'a') = False
compare(L'a', L'b') = True
compare(L'b', L'a') = False

compare(L'a', L'a') = False
compare(L'a', L'b') = False
compare(L'b', L'a') = True
```

## <a name="key_compare"></a> multiset::key_compare (STL/CLR)

Pořadí delegáta pro dva klíče.

### <a name="syntax"></a>Syntaxe

```cpp
Microsoft::VisualC::StlClr::BinaryDelegate<GKey, GKey, bool>
    key_compare;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro delegáta, který určuje řazení klíče argumenty.

### <a name="example"></a>Příklad

```cpp
// cliext_multiset_key_compare.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    Mymultiset::key_compare^ kcomp = c1.key_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        kcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        kcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        kcomp(L'b', L'a'));
    System::Console::WriteLine();

    // test a different ordering rule
    Mymultiset c2 = cliext::greater<wchar_t>();
    kcomp = c2.key_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        kcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        kcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        kcomp(L'b', L'a'));
    return (0);
    }
```

```Output
compare(L'a', L'a') = False
compare(L'a', L'b') = True
compare(L'b', L'a') = False

compare(L'a', L'a') = False
compare(L'a', L'b') = False
compare(L'b', L'a') = True
```

## <a name="key_type"></a> multiset::key_type (STL/CLR)

Typ klíče řazení

### <a name="syntax"></a>Syntaxe

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro parametr šablony *klíč*.

### <a name="example"></a>Příklad

```cpp
// cliext_multiset_key_type.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c" using key_type
    for (Mymultiset::iterator it = c1.begin(); it != c1.end(); ++it)
        {   // store element in key_type object
        Mymultiset::key_type val = *it;

        System::Console::Write("{0} ", val);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="lower_bound"></a> multiset::lower_bound (STL/CLR)

Vyhledá počátek rozsahu, který odpovídá zadanému klíči.

### <a name="syntax"></a>Syntaxe

```cpp
iterator lower_bound(key_type key);
```

#### <a name="parameters"></a>Parametry

*Klíč*<br/>
Hodnota klíče pro hledání.

### <a name="remarks"></a>Poznámky

Členská funkce určuje první prvek `X` v řízené sekvenci, která má stejné pořadí na *klíč*. Pokud žádný takový prvek neexistuje, vrátí [multiset::end (STL/CLR)](../dotnet/multiset-end-stl-clr.md)`()`; v opačném případě vrátí iterátor, který určuje `X`. Použijete ji k aktuálně vyhledejte na začátek pořadí prvků v řízené sekvenci, které odpovídají zadanému klíči.

### <a name="example"></a>Příklad

```cpp
// cliext_multiset_lower_bound.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("lower_bound(L'x')==end() = {0}",
        c1.lower_bound(L'x') == c1.end());

    System::Console::WriteLine("*lower_bound(L'a') = {0}",
        *c1.lower_bound(L'a'));
    System::Console::WriteLine("*lower_bound(L'b') = {0}",
        *c1.lower_bound(L'b'));
    return (0);
    }
```

```Output
a b c
lower_bound(L'x')==end() = True
*lower_bound(L'a') = a
*lower_bound(L'b') = b
```

## <a name="make_value"></a> multiset::make_value (STL/CLR)

Vytvoří objekt hodnoty.

### <a name="syntax"></a>Syntaxe

```cpp
static value_type make_value(key_type key);
```

#### <a name="parameters"></a>Parametry

*Klíč*<br/>
Hodnota klíče používat.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí `value_type` objekt, jehož klíč je *klíč*. Použijete ji k vytvoření objektu vhodný pro použití s několika další členské funkce.

### <a name="example"></a>Příklad

```cpp
// cliext_multiset_make_value.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(Mymultiset::make_value(L'a'));
    c1.insert(Mymultiset::make_value(L'b'));
    c1.insert(Mymultiset::make_value(L'c'));

    // display contents " a b c"
    for each (Mymultiset::value_type elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="multiset"></a> multiset::multiset (STL/CLR)

Sestaví objekt kontejneru.

### <a name="syntax"></a>Syntaxe

```cpp
multiset();
explicit multiset(key_compare^ pred);
multiset(multiset<Key>% right);
multiset(multiset<Key>^ right);
template<typename InIter>
    multisetmultiset(InIter first, InIter last);
template<typename InIter>
    multiset(InIter first, InIter last,
        key_compare^ pred);
multiset(System::Collections::Generic::IEnumerable<GValue>^ right);
multiset(System::Collections::Generic::IEnumerable<GValue>^ right,
    key_compare^ pred);
```

#### <a name="parameters"></a>Parametry

*první*<br/>
Začátek rozsahu pro vložení.

*poslední*<br/>
Konec rozsahu pro vložení.

*Před*<br/>
Řazení predikátu řízené sekvence.

*doprava*<br/>
Objekt nebo rozsahu pro vložení.

### <a name="remarks"></a>Poznámky

Konstruktor:

`multiset();`

Inicializuje výchozí řazení predikátu řízené sekvence bez prvků `key_compare()`. Použijete ji k určení prázdnou počáteční řízenou sekvenci, s výchozí řazení predikátu.

Konstruktor:

`explicit multiset(key_compare^ pred);`

Inicializuje řízené sekvence bez prvků pořadí predikátem *před*. Použít prázdnou počáteční řízenou sekvenci, určit se zadanou predikát pořadí.

Konstruktor:

`multiset(multiset<Key>% right);`

Inicializuje řízené sekvence s pořadím [`right.begin()`, `right.end()`), s výchozí řazení predikátu. Můžete ji použít k určení počáteční řízené sekvence, který je kopii sekvence řízenou parametrem multiset – objekt *správné*, s výchozí řazení predikátu.

Konstruktor:

`multiset(multiset<Key>^ right);`

Inicializuje řízené sekvence s pořadím [`right->begin()`, `right->end()`), s výchozí řazení predikátu. Můžete ji použít k určení počáteční řízené sekvence, který je kopii sekvence řízenou parametrem multiset – objekt *správné*, s výchozí řazení predikátu.

Konstruktor:

`template<typename InIter> multiset(InIter first, InIter last);`

Inicializuje řízené sekvence s pořadím [`first`, `last`), s výchozí řazení predikátu. Používejte aby řízené sekvence kopii jiné pořadí, s výchozí řazení predikátu.

Konstruktor:

`template<typename InIter> multiset(InIter first, InIter last, key_compare^ pred);`

Inicializuje řízené sekvence s pořadím [`first`, `last`), pořadí predikátem *před*. Použijete ji k vytvoření kopie jiné pořadí se zadanou predikát pořadí řízené sekvence.

Konstruktor:

`multiset(System::Collections::Generic::IEnumerable<Key>^ right);`

Inicializuje řízené sekvence s pořadí určeném enumerátor *správné*, s výchozí řazení predikátu. Použijete ji k vytvoření kopie jiné pořadí popsal čítače, s výchozí řazení predikátu řízené sekvence.

Konstruktor:

`multiset(System::Collections::Generic::IEnumerable<Key>^ right, key_compare^ pred);`

Inicializuje řízené sekvence s pořadí určeném enumerátor *správné*, pořadí predikátem *před*. Použijete ji k vytvoření kopie jiné pořadí popsal enumerátor se zadanou predikát pořadí řízené sekvence.

### <a name="example"></a>Příklad

```cpp
// cliext_multiset_construct.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
// construct an empty container
    Mymultiset c1;
    System::Console::WriteLine("size() = {0}", c1.size());

    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an ordering rule
    Mymultiset c2 = cliext::greater_equal<wchar_t>();
    System::Console::WriteLine("size() = {0}", c2.size());

    c2.insert(c1.begin(), c1.end());
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an iterator range
    Mymultiset c3(c1.begin(), c1.end());
    for each (wchar_t elem in c3)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an iterator range and an ordering rule
    Mymultiset c4(c1.begin(), c1.end(),
        cliext::greater_equal<wchar_t>());
    for each (wchar_t elem in c4)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an enumeration
    Mymultiset c5(   // NOTE: cast is not needed
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3);
    for each (wchar_t elem in c5)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an enumeration and an ordering rule
    Mymultiset c6(   // NOTE: cast is not needed
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3,
            cliext::greater_equal<wchar_t>());
    for each (wchar_t elem in c6)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct from a generic container
    Mymultiset c7(c4);
    for each (wchar_t elem in c7)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct by copying another container
    Mymultiset c8(%c3);
    for each (wchar_t elem in c8)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
size() = 0
a b c
size() = 0
c b a
a b c
c b a
a b c
c b a
c b a
a b c
```

## <a name="op_as"></a> multiset::Operator = (STL/CLR)

Nahradí řízené sekvence.

### <a name="syntax"></a>Syntaxe

```cpp
multiset<Key>% operator=(multiset<Key>% right);
```

#### <a name="parameters"></a>Parametry

*doprava*<br/>
Kontejner pro kopírování.

### <a name="remarks"></a>Poznámky

Kopie členský operátor *správné* na objekt, vrátí `*this`. Můžete použít k nahraďte kopii řízené sekvence v řízené sekvenci *správné*.

### <a name="example"></a>Příklad

```cpp
// cliext_multiset_operator_as.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    for each (Mymultiset::value_type elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    Mymultiset c2;
    c2 = c1;
// display contents " a b c"
    for each (Mymultiset::value_type elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a b c
```

## <a name="rbegin"></a> multiset::rbegin (STL/CLR)

Určuje začátek řízené obrácené sekvenci.

### <a name="syntax"></a>Syntaxe

```cpp
reverse_iterator rbegin();
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí zpětný iterátor, který určuje poslední prvek řízenou sekvenci nebo hned za začátku k prázdné sekvenci. Proto, označí `beginning` reverzní pořadí. Můžete ji použít k získání iterátor, který určuje `current` začátek řízené sekvence viděli v obráceném pořadí, ale jeho stav můžete změnit, pokud se změní délka řízené sekvence.

### <a name="example"></a>Příklad

```cpp
// cliext_multiset_rbegin.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect first two items in reversed sequence
    Mymultiset::reverse_iterator rit = c1.rbegin();
    System::Console::WriteLine("*rbegin() = {0}", *rit);
    System::Console::WriteLine("*++rbegin() = {0}", *++rit);
    return (0);
    }
```

```Output
a b c
*rbegin() = c
*++rbegin() = b
```

## <a name="reference"></a> multiset::Reference (STL/CLR)

Typ odkazu na prvek

### <a name="syntax"></a>Syntaxe

```cpp
typedef value_type% reference;
```

### <a name="remarks"></a>Poznámky

Typ, který popisuje odkaz na element.

### <a name="example"></a>Příklad

```cpp
// cliext_multiset_reference.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    Mymultiset::iterator it = c1.begin();
    for (; it != c1.end(); ++it)
        {   // get a reference to an element
        Mymultiset::reference ref = *it;
        System::Console::Write("{0} ", ref);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="rend"></a> multiset::rend (STL/CLR)

Určuje konec řízené obrácené sekvenci.

### <a name="syntax"></a>Syntaxe

```cpp
reverse_iterator rend();
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí "reverse iterator", který ukazuje za začátek řízené sekvence. Proto, označí `end` reverzní pořadí. Můžete ji použít k získání iterátor, který určuje `current` konec řízené sekvence viděli v obráceném pořadí, ale jeho stav můžete změnit, pokud se změní délka řízené sekvence.

### <a name="example"></a>Příklad

```cpp
// cliext_multiset_rend.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect first two items
    Mymultiset::reverse_iterator rit = c1.rend();
    --rit;
    System::Console::WriteLine("*-- --rend() = {0}", *--rit);
    System::Console::WriteLine("*--rend() = {0}", *++rit);
    return (0);
    }
```

```Output
a b c
*-- --rend() = b
*--rend() = a
```

## <a name="reverse_iterator"></a> multiset::reverse_iterator (STL/CLR)

Typ "reverse iterator" pro řízenou sekvenci.

### <a name="syntax"></a>Syntaxe

```cpp
typedef T3 reverse_iterator;
```

### <a name="remarks"></a>Poznámky

Typ popisuje objekt neurčeného typu `T3` , který může sloužit jako "reverse iterator" pro řízenou sekvenci.

### <a name="example"></a>Příklad

```cpp
// cliext_multiset_reverse_iterator.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c" reversed
    Mymultiset::reverse_iterator rit = c1.rbegin();
    for (; rit != c1.rend(); ++rit)
        System::Console::Write("{0} ", *rit);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c b a
```

## <a name="size"></a> multiset::size (STL/CLR)

Spočítá počet prvků.

### <a name="syntax"></a>Syntaxe

```cpp
size_type size();
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí délku objektu řízené sekvence. Použijete ji k určení počtu prvků v řízené sekvenci aktuálně. Pokud vás zajímá, jestli je pořadí má nenulovou velikost, naleznete v tématu [multiset::empty (STL/CLR)](../dotnet/multiset-empty-stl-clr.md)`()`.

### <a name="example"></a>Příklad

```cpp
// cliext_multiset_size.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    System::Console::WriteLine("size() = {0} starting with 3", c1.size());

    // clear the container and reinspect
    c1.clear();
    System::Console::WriteLine("size() = {0} after clearing", c1.size());

    // add elements and clear again
    c1.insert(L'a');
    c1.insert(L'b');
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

## <a name="size_type"></a> multiset::size_type (STL/CLR)

Typ vzdálenosti se znaménkem mezi dvěma elementu.

### <a name="syntax"></a>Syntaxe

```cpp
typedef int size_type;
```

### <a name="remarks"></a>Poznámky

Typ, který popisuje počet prvků záporná.

### <a name="example"></a>Příklad

```cpp
// cliext_multiset_size_type.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // compute positive difference
    Mymultiset::size_type diff = 0;
    for (Mymultiset::iterator it = c1.begin(); it != c1.end(); ++it)
        ++diff;
    System::Console::WriteLine("end()-begin() = {0}", diff);
    return (0);
    }
```

```Output
a b c
end()-begin() = 3
```

## <a name="swap"></a> multiset::swap (STL/CLR)

Zamění obsah dvou kontejnerů.

### <a name="syntax"></a>Syntaxe

```cpp
void swap(multiset<Key>% right);
```

#### <a name="parameters"></a>Parametry

*doprava*<br/>
Kontejner pro obsah s.

### <a name="remarks"></a>Poznámky

Členská funkce Zamění řízené sekvence mezi `this` a *správné*. Provádí se v konstantním času a vyvolá žádné výjimky. Můžete použít jako rychlý způsob, jak Zamění obsah dvou kontejnerů.

### <a name="example"></a>Příklad

```cpp
// cliext_multiset_swap.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct another container with repetition of values
    Mymultiset c2;
    c2.insert(L'd');
    c2.insert(L'e');
    c2.insert(L'f');
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
d e f
d e f
a b c
```

## <a name="to_array"></a> multiset::to_array (STL/CLR)

Zkopíruje do nového pole řízené sekvence.

### <a name="syntax"></a>Syntaxe

```cpp
cli::array<value_type>^ to_array();
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí pole obsahující řízené sekvence. Použijete ji získat kopii řízenou sekvenci pole formuláře.

### <a name="example"></a>Příklad

```cpp
// cliext_multiset_to_array.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // copy the container and modify it
    cli::array<wchar_t>^ a1 = c1.to_array();

    c1.insert(L'd');
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

## <a name="upper_bound"></a> multiset::upper_bound (STL/CLR)

Najde konec rozsahu, který odpovídá zadanému klíči.

### <a name="syntax"></a>Syntaxe

```cpp
iterator upper_bound(key_type key);
```

#### <a name="parameters"></a>Parametry

*Klíč*<br/>
Hodnota klíče pro hledání.

### <a name="remarks"></a>Poznámky

Členská funkce určuje poslední prvek `X` v řízené sekvenci, která má stejné pořadí na *klíč*. Pokud žádný takový prvek neexistuje, nebo pokud `X` je po posledním prvku v řízené sekvenci vrátí [multiset::end (STL/CLR)](../dotnet/multiset-end-stl-clr.md)`()`; v opačném případě vrátí iterátor, který určuje prvního prvku mimo `X`. Pomocí aktuálně najít konec pořadí prvků v řízené sekvenci, které odpovídají zadanému klíči.

### <a name="example"></a>Příklad

```cpp
// cliext_multiset_upper_bound.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("upper_bound(L'x')==end() = {0}",
        c1.upper_bound(L'x') == c1.end());

    System::Console::WriteLine("*upper_bound(L'a') = {0}",
        *c1.upper_bound(L'a'));
    System::Console::WriteLine("*upper_bound(L'b') = {0}",
        *c1.upper_bound(L'b'));
    return (0);
    }
```

```Output
a b c
upper_bound(L'x')==end() = True
*upper_bound(L'a') = b
*upper_bound(L'b') = c
```

## <a name="value_comp"></a> multiset::value_comp (STL/CLR)

Zkopíruje pořadí delegáta pro dvě hodnoty prvků.

### <a name="syntax"></a>Syntaxe

```cpp
value_compare^ value_comp();
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí pořadí delegáta, který slouží k seřazení řízené sekvence. Použijete ji k porovnat dvě hodnoty prvků.

### <a name="example"></a>Příklad

```cpp
// cliext_multiset_value_comp.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    Mymultiset::value_compare^ kcomp = c1.value_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        kcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        kcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        kcomp(L'b', L'a'));
    System::Console::WriteLine();
    return (0);
    }
```

```Output
compare(L'a', L'a') = False
compare(L'a', L'b') = True
compare(L'b', L'a') = False
```

## <a name="value_compare"></a> multiset::value_compare (STL/CLR)

Pořadí delegáta pro dvě hodnoty prvků.

### <a name="syntax"></a>Syntaxe

```cpp
Microsoft::VisualC::StlClr::BinaryDelegate<generic_value, generic_value, bool>
    value_compare;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro delegáta, který určuje pořadí z argumentů hodnotu.

### <a name="example"></a>Příklad

```cpp
// cliext_multiset_value_compare.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    Mymultiset::value_compare^ kcomp = c1.value_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        kcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        kcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        kcomp(L'b', L'a'));
    System::Console::WriteLine();
    return (0);
    }
```

```Output
compare(L'a', L'a') = False
compare(L'a', L'b') = True
compare(L'b', L'a') = False
```

## <a name="value_type"></a> multiset::value_type (STL/CLR)

Typ prvku

### <a name="syntax"></a>Syntaxe

```cpp
typedef generic_value value_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro `generic_value`.

### <a name="example"></a>Příklad

```cpp
// cliext_multiset_value_type.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c" using value_type
    for (Mymultiset::iterator it = c1.begin(); it != c1.end(); ++it)
        {   // store element in value_type object
        Mymultiset::value_type val = *it;

        System::Console::Write("{0} ", val);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="op_neq"></a> Operator! = (multiset) (STL/CLR)

Seznam není rovno porovnání.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Key>
    bool operator!=(multiset<Key>% left,
        multiset<Key>% right);
```

#### <a name="parameters"></a>Parametry

*doleva*<br/>
Levé kontejner k porovnání.

*doprava*<br/>
Správném kontejneru pro porovnání.

### <a name="remarks"></a>Poznámky

Vrátí funkci operátoru `!(left == right)`. Pomocí něho můžete testovat, zda *levé* není stejný jako seřazené *správné* když jsou dvě multisets porovnání elementu pomocí elementu.

### <a name="example"></a>Příklad

```cpp
// cliext_multiset_operator_ne.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    Mymultiset c2;
    c2.insert(L'a');
    c2.insert(L'b');
    c2.insert(L'd');

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

## <a name="op_lt"></a> operátor&lt; (multiset) (STL/CLR)

Seznam menší než porovnání.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Key>
    bool operator<(multiset<Key>% left,
        multiset<Key>% right);
```

#### <a name="parameters"></a>Parametry

*doleva*<br/>
Levé kontejner k porovnání.

*doprava*<br/>
Správném kontejneru pro porovnání.

### <a name="remarks"></a>Poznámky

Operátoru funkce vrátí hodnota true v případě, pro nejnižší pozici `i` pro kterou `!(right[i] < left[i])` je také hodnotu true, který `left[i] < right[i]`. V opačném případě vrátí `left->size() < right->size()` pomocí něho můžete testovat, zda *levé* je řazen před *správné* když jsou dvě multisets porovnání elementu pomocí elementu.

### <a name="example"></a>Příklad

```cpp
// cliext_multiset_operator_lt.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    Mymultiset c2;
    c2.insert(L'a');
    c2.insert(L'b');
    c2.insert(L'd');

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

## <a name="op_lteq"></a> operátor&lt;= (multiset) (STL/CLR)

Seznam menší nebo rovna porovnání.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Key>
    bool operator<=(multiset<Key>% left,
        multiset<Key>% right);
```

#### <a name="parameters"></a>Parametry

*doleva*<br/>
Levé kontejner k porovnání.

*doprava*<br/>
Správném kontejneru pro porovnání.

### <a name="remarks"></a>Poznámky

Vrátí funkci operátoru `!(right < left)`. Pomocí něho můžete testovat, zda *levé* není seřazené po *správné* když jsou dvě multisets porovnání elementu pomocí elementu.

### <a name="example"></a>Příklad

```cpp
// cliext_multiset_operator_le.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    Mymultiset c2;
    c2.insert(L'a');
    c2.insert(L'b');
    c2.insert(L'd');

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

## <a name="op_eq"></a> Operator == (multiset) (STL/CLR)

Porovnání rovna seznamu.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Key>
    bool operator==(multiset<Key>% left,
        multiset<Key>% right);
```

#### <a name="parameters"></a>Parametry

*doleva*<br/>
Levé kontejner k porovnání.

*doprava*<br/>
Správném kontejneru pro porovnání.

### <a name="remarks"></a>Poznámky

Funkce operátoru vrátí hodnotu true pouze v případě, že řídí sekvencí *levé* a *správné* mít stejnou délku a pro každou pozici `i`, `left[i] ==` `right[i]`. Pomocí něho můžete testovat, zda *levé* je stejný jako seřazené *správné* když jsou dvě multisets porovnání elementu pomocí elementu.

### <a name="example"></a>Příklad

```cpp
// cliext_multiset_operator_eq.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    Mymultiset c2;
    c2.insert(L'a');
    c2.insert(L'b');
    c2.insert(L'd');

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

## <a name="op_gt"></a> operátor&gt; (multiset) (STL/CLR)

Seznam je větší než porovnání.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Key>
    bool operator>(multiset<Key>% left,
        multiset<Key>% right);
```

#### <a name="parameters"></a>Parametry

*doleva*<br/>
Levé kontejner k porovnání.

*doprava*<br/>
Správném kontejneru pro porovnání.

### <a name="remarks"></a>Poznámky

Vrátí funkci operátoru `right` `<` `left`. Pomocí něho můžete testovat, zda *levé* seřazené po *správné* když jsou dvě multisets porovnání elementu pomocí elementu.

### <a name="example"></a>Příklad

```cpp
// cliext_multiset_operator_gt.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    Mymultiset c2;
    c2.insert(L'a');
    c2.insert(L'b');
    c2.insert(L'd');

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

## <a name="op_gteq"></a> operátor&gt;= (multiset) (STL/CLR)

Seznam větší než nebo rovna porovnání.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Key>
    bool operator>=(multiset<Key>% left,
        multiset<Key>% right);
```

#### <a name="parameters"></a>Parametry

*doleva*<br/>
Levé kontejner k porovnání.

*doprava*<br/>
Správném kontejneru pro porovnání.

### <a name="remarks"></a>Poznámky

Vrátí funkci operátoru `!(left < right)`. Pomocí něho můžete testovat, zda *levé* není řazen před *správné* když jsou dvě multisets porovnání elementu pomocí elementu.

### <a name="example"></a>Příklad

```cpp
// cliext_multiset_operator_ge.cpp
// compile with: /clr
#include <cliext/set>

typedef cliext::multiset<wchar_t> Mymultiset;
int main()
    {
    Mymultiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    Mymultiset c2;
    c2.insert(L'a');
    c2.insert(L'b');
    c2.insert(L'd');

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