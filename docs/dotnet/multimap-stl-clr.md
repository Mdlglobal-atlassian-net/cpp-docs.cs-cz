---
title: multimap (STL/CLR)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cliext::multimap
- cliext::multimap::begin
- cliext::multimap::clear
- cliext::multimap::const_iterator
- cliext::multimap::const_reference
- cliext::multimap::const_reverse_iterator
- cliext::multimap::count
- cliext::multimap::difference_type
- cliext::multimap::empty
- cliext::multimap::end
- cliext::multimap::equal_range
- cliext::multimap::erase
- cliext::multimap::find
- cliext::multimap::generic_container
- cliext::multimap::generic_iterator
- cliext::multimap::generic_reverse_iterator
- cliext::multimap::generic_value
- cliext::multimap::insert
- cliext::multimap::iterator
- cliext::multimap::key_comp
- cliext::multimap::key_compare
- cliext::multimap::key_type
- cliext::multimap::lower_bound
- cliext::multimap::make_value
- cliext::multimap::mapped_type
- cliext::multimap::multimap
- cliext::multimap::operator=
- cliext::multimap::rbegin
- cliext::multimap::reference
- cliext::multimap::rend
- cliext::multimap::reverse_iterator
- cliext::multimap::size
- cliext::multimap::size_type
- cliext::multimap::swap
- cliext::multimap::to_array
- cliext::multimap::upper_bound
- cliext::multimap::value_comp
- cliext::multimap::value_compare
- cliext::multimap::value_type
- cliext::mutlimap::operator!=
- cliext::mutlimap::operator<
- cliext::mutlimap::operator<=
- cliext::mutlimap::operator==
- cliext::mutlimap::operator>
- cliext::mutlimap::operator>=
helpviewer_keywords:
- <map> header [STL/CLR]
- <cliext/map> header [STL/CLR]
- multimap class [STL/CLR]
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
- mapped_type member [STL/CLR]
- multimap member [STL/CLR]
- operator= member [STL/CLR]
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
ms.assetid: 3dfe329d-a078-462a-b050-7999ce6110ad
ms.openlocfilehash: 9cc7dd32f222e68abb45fe8c518d9f378453b372
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50641529"
---
# <a name="multimap-stlclr"></a>multimap (STL/CLR)

Třída šablony popisuje objekt, který řídí různé délky sekvence elementů, která má obousměrný přístup. Použití kontejneru `multimap` , spravovat řadu prvků, jako větve (téměř) s vyrovnáváním seřazených uzlů, každý ukládání jeden element. Element se skládá z klíče pro seřazení, pořadí a mapované hodnoty, které nenastane pravé.

V popisu níže `GValue` je stejný jako:

`Microsoft::VisualC::StlClr::GenericPair<GKey, GMapped>`

kde:

`GKey` je stejný jako *klíč* Pokud je typ odkazu, v takovém případě je `Key^`

`GMapped` je stejný jako *mapované* Pokud je typ odkazu, v takovém případě je `Mapped^`

## <a name="syntax"></a>Syntaxe

```cpp
template<typename Key,
    typename Mapped>
    ref class multimap
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

*Mapovat*<br/>
Typ elementu v řízené sekvenci další komponenty.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<cliext – / map >

**Namespace:** cliext –

## <a name="declarations"></a>Deklarace

|Definice typu|Popis|
|---------------------|-----------------|
|[multimap::const_iterator (STL/CLR)](#const_iterator)|Typ konstantního iterátoru řízené sekvence|
|[multimap::const_reference (STL/CLR)](#const_reference)|Typ konstantního odkazu na prvek|
|[multimap::const_reverse_iterator (STL/CLR)](#const_reverse_iterator)|Typ konstantního zpětného iterátoru řízené sekvence.|
|[multimap::difference_type (STL/CLR)](#difference_type)|Typ (může být podepsaná) vzdálenosti mezi dvěma prvky.|
|[multimap::generic_container (STL/CLR)](#generic_container)|Typ obecné rozhraní pro kontejner.|
|[multimap::generic_iterator (STL/CLR)](#generic_iterator)|Typ iterátoru pro obecné rozhraní pro kontejner.|
|[multimap::generic_reverse_iterator (STL/CLR)](#generic_reverse_iterator)|Typ "reverse iterator" pro obecné rozhraní pro kontejner.|
|[multimap::generic_value (STL/CLR)](#generic_value)|Typ elementu pro obecné rozhraní pro kontejner.|
|[multimap::iterator (STL/CLR)](#iterator)|Typ iterátoru řízené sekvence|
|[multimap::key_compare (STL/CLR)](#key_compare)|Pořadí delegáta pro dva klíče.|
|[multimap::key_type (STL/CLR)](#key_type)|Typ klíče řazení|
|[multimap::mapped_type (STL/CLR)](#mapped_type)|Typ mapované hodnoty přiřazené ke každému klíči.|
|[multimap::reference (STL/CLR)](#reference)|Typ odkazu na prvek|
|[multimap::reverse_iterator (STL/CLR)](#reverse_iterator)|Typ "reverse iterator" pro řízenou sekvenci.|
|[multimap::size_type (STL/CLR)](#size_type)|Typ vzdálenosti (nezáporné) mezi dvěma prvky.|
|[multimap::value_compare (STL/CLR)](#value_compare)|Pořadí delegáta pro dvě hodnoty prvků.|
|[multimap::value_type (STL/CLR)](#value_type)|Typ prvku|

|Členská funkce|Popis|
|---------------------|-----------------|
|[multimap::begin (STL/CLR)](#begin)|Určuje začátek řízené sekvence.|
|[multimap::clear (STL/CLR)](#clear)|Odebere všechny prvky.|
|[multimap::count (STL/CLR)](#count)|Vrátí počet prvků odpovídající zadanému klíči.|
|[multimap::empty (STL/CLR)](#empty)|Zkouší, zda nejsou přítomny žádné prvky.|
|[multimap::end (STL/CLR)](#end)|Určuje konec řízené sekvence.|
|[multimap::equal_range (STL/CLR)](#equal_range)|Najde rozsah, který odpovídá zadanému klíči.|
|[multimap::erase (STL/CLR)](#erase)|Odebere prvky v určených pozicích.|
|[multimap::find (STL/CLR)](#find)|Vyhledá prvek, který odpovídá zadanému klíči.|
|[multimap::insert (STL/CLR)](#insert)|Přidá prvky.|
|[multimap::key_comp (STL/CLR)](#key_comp)|Zkopíruje pořadí delegáta pro dva klíče.|
|[multimap::lower_bound (STL/CLR)](#lower_bound)|Vyhledá počátek rozsahu, který odpovídá zadanému klíči.|
|[multimap::make_value (STL/CLR)](#make_value)|Vytvoří objekt hodnoty.|
|[multimap::multimap (STL/CLR)](#multimap)|Sestaví objekt kontejneru.|
|[multimap::rbegin (STL/CLR)](#rbegin)|Určuje začátek řízené obrácené sekvenci.|
|[multimap::rend (STL/CLR)](#rend)|Určuje konec řízené obrácené sekvenci.|
|[multimap::size (STL/CLR)](#size)|Spočítá počet prvků.|
|[multimap::swap (STL/CLR)](#swap)|Zamění obsah dvou kontejnerů.|
|[multimap::to_array (STL/CLR)](#to_array)|Zkopíruje do nového pole řízené sekvence.|
|[multimap::upper_bound (STL/CLR)](#upper_bound)|Najde konec rozsahu, který odpovídá zadanému klíči.|
|[multimap::value_comp (STL/CLR)](#value_comp)|Zkopíruje pořadí delegáta pro dvě hodnoty prvků.|

|Operátor|Popis|
|--------------|-----------------|
|[multimap::operator= (STL/CLR)](#op_as)|Nahradí řízené sekvence.|
|[operator!= (multimap) (STL/CLR)](#op_neq)|Určuje, zda `multimap` není roven jinému objektu `multimap` objektu.|
|[operator< (multimap) (STL/CLR)](#op_lt)|Určuje, zda `multimap` je menší než jiný objekt `multimap` objektu.|
|[operator<= (multimap) (STL/CLR)](#op_lteq)|Určuje, zda `multimap` objekt je menší nebo rovna jiné `multimap` objektu.|
|[operator== (multimap) (STL/CLR)](#op_eq)|Určuje, zda `multimap` je roven jinému objektu `multimap` objektu.|
|[operator> (multimap) (STL/CLR)](#op_gt)|Určuje, zda `multimap` je větší než jiný objekt `multimap` objektu.|
|[operator>= (multimap) (STL/CLR)](#op_gteq)|Určuje, zda `multimap` objekt je větší než nebo roven jinému `multimap` objektu.|

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

Objekt seřadí sekvence pomocí volání uloženého delegáta objekt typu [multimap::key_compare (STL/CLR)](../dotnet/multimap-key-compare-stl-clr.md). Při vytváření objektu multimap; můžete zadat objekt uložené delegáta Pokud chcete zadat žádný objekt. delegát, výchozí hodnota je porovnání `operator<(key_type, key_type)`. Přístup k tomuto uloženého objektu voláním členské funkce [multimap::key_comp (STL/CLR)](../dotnet/multimap-key-comp-stl-clr.md)`()`.

Takový objekt delegáta musí uložit přísné slabé seřazení klíčů typu [multimap::key_type (STL/CLR)](../dotnet/multimap-key-type-stl-clr.md). To znamená pro jakékoli dva klíče `X` a `Y`:

`key_comp()(X, Y)` Vrátí výsledek stejný datový typ Boolean při každém volání.

Pokud `key_comp()(X, Y)` má hodnotu true, pak `key_comp()(Y, X)` musí mít hodnotu false.

Pokud `key_comp()(X, Y)` má hodnotu true, pak `X` říká, že je řazen před `Y`.

Pokud `!key_comp()(X, Y) && !key_comp()(Y, X)` má hodnotu true, pak `X` a `Y` se říká, že mají ekvivalentní řazení.

Pro libovolný element `X` , která předchází `Y` v řízené sekvenci `key_comp()(Y, X)` má hodnotu false. (Pro výchozí objekt delegáta, klíče nikdy snížení hodnoty.) Na rozdíl od třídy šablony [mapy (STL/CLR)](../dotnet/map-stl-clr.md), objekt třídy šablony `multimap` nevyžaduje, aby byly jedinečné klíče pro všechny elementy. (Dva nebo více klíčů může mít odpovídající řazení.)

Každý prvek obsahuje samostatný klíč a hodnotu pro mapovanou. Sekvence je reprezentována způsobem, který umožňuje vyhledávání, vkládání a odstranění libovolný prvek s počtem operací úměrný logaritmu počtu prvků v sekvenci (logaritmické čas). Vkládání prvků navíc nezruší platnost žádných iterátorů a odstranění prvku zruší platnost pouze těch iterátorů, které odkazují na odstraněný prvek.

Multimap podporuje obousměrné iterátory, což znamená, že přejdete na sousedící prvky zadaný iterátor, který určuje elementu v řízené sekvenci. Speciální hlavního uzlu odpovídá iterátorů vrácené [multimap::end (STL/CLR)](../dotnet/multimap-end-stl-clr.md)`()`. Tento iterátor, který má přístup po posledním prvku v řízené sekvenci lze snížit, pokud jsou k dispozici. Můžete zvýšit multimap iterátor, který má přístup k hlavnímu uzlu a budou pak porovnat rovna `end()`. Nelze přistoupit přes ukazatel vrátí iterátor, ale `end()`.

Všimněte si, že nemůže odkazovat na prvek multimap přímo zadané pozici číselné –, který vyžaduje iterátor náhodného přístupu.

Multimap – iterátoru uloží popisovač do přidružené multimap uzlu, který je pak uloží popisovač pro jeho přiřazeným kontejnerem. Iterátory lze použít pouze objekty, které přiřazeným kontejnerem. Multimap – iterátoru zůstává v platnosti tak dlouho, dokud jeho přidružený uzel multimap souvisí s některé multimap. Kromě toho je platný iterátoru přesměrovat – slouží k přístupu nebo změnit hodnotu prvku jmenuje--tak dlouho, dokud se nerovná `end()`.

Smazání nebo odstranění prvku volá destruktor pro jeho uložené hodnotě. Zničení kontejneru vymaže všechny prvky. Kontejner, jehož typ prvku je třídy ref class tak, zajišťuje, že žádné elementy něj kontejneru. Mějte na paměti, ale, že kontejner zpracovává nemá *není* zničit jeho prvků.

## <a name="members"></a>Členové

## <a name="begin"></a> multimap::begin (STL/CLR)

Určuje začátek řízené sekvence.

### <a name="syntax"></a>Syntaxe

```cpp
iterator begin();
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí obousměrný iterátor, který určuje první prvek řízenou sekvenci nebo přesně za konec k prázdné sekvenci. Můžete ji použít k získání iterátor, který určuje `current` začátek řízené sekvence, ale jeho stav můžete změnit, pokud se změní délka řízené sekvence.

### <a name="example"></a>Příklad

```cpp
// cliext_multimap_begin.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymultimap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // inspect first two items
    Mymultimap::iterator it = c1.begin();
    System::Console::WriteLine("*begin() = [{0} {1}]",
        it->first, it->second);
    ++it;
    System::Console::WriteLine("*++begin() = [{0} {1}]",
        it->first, it->second);
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
*begin() = [a 1]
*++begin() = [b 2]
```

## <a name="clear"></a> multimap::clear (STL/CLR)

Odebere všechny prvky.

### <a name="syntax"></a>Syntaxe

```cpp
void clear();
```

### <a name="remarks"></a>Poznámky

Členská funkce efektivně volá [multimap::erase (STL/CLR)](../dotnet/multimap-erase-stl-clr.md) `(` [multimap::begin (STL/CLR)](../dotnet/multimap-begin-stl-clr.md) `(),` [multimap::end (STL/CLR)](../dotnet/multimap-end-stl-clr.md) `())`. Použijete ji k zajištění, že je prázdná řízené sekvence.

### <a name="example"></a>Příklad

```cpp
// cliext_multimap_clear.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymultimap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // clear the container and reinspect
    c1.clear();
    System::Console::WriteLine("size() = {0}", c1.size());

    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));

    // display contents " [a 1] [b 2]"
    for each (Mymultimap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();
    c1.clear();
    System::Console::WriteLine("size() = {0}", c1.size());
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
size() = 0
[a 1] [b 2]
size() = 0
```

## <a name="const_iterator"></a> multimap::const_iterator (STL/CLR)

Typ konstantního iterátoru řízené sekvence

### <a name="syntax"></a>Syntaxe

```cpp
typedef T2 const_iterator;
```

### <a name="remarks"></a>Poznámky

Typ popisuje objekt neurčeného typu `T2` , který může sloužit jako konstantní obousměrného iterátoru řízené sekvence.

### <a name="example"></a>Příklad

```cpp
// cliext_multimap_const_iterator.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    Mymultimap::const_iterator cit = c1.begin();
    for (; cit != c1.end(); ++cit)
        System::Console::Write("[{0} {1}] ", cit->first, cit->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
```

## <a name="const_reference"></a> multimap::const_reference (STL/CLR)

Typ konstantního odkazu na prvek

### <a name="syntax"></a>Syntaxe

```cpp
typedef value_type% const_reference;
```

### <a name="remarks"></a>Poznámky

Typ, který popisuje konstantní odkaz na element.

### <a name="example"></a>Příklad

```cpp
// cliext_multimap_const_reference.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    Mymultimap::const_iterator cit = c1.begin();
    for (; cit != c1.end(); ++cit)
        {   // get a const reference to an element
        Mymultimap::const_reference cref = *cit;
        System::Console::Write("[{0} {1}] ", cref->first, cref->second);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
```

## <a name="const_reverse_iterator"></a> multimap::const_reverse_iterator (STL/CLR)

Typ konstantního zpětného iterátoru řízené sekvence.

### <a name="syntax"></a>Syntaxe

```cpp
typedef T4 const_reverse_iterator;
```

### <a name="remarks"></a>Poznámky

Typ popisuje objekt neurčeného typu `T4` , který může sloužit jako konstantní zpětného iterátoru řízené sekvence.

### <a name="example"></a>Příklad

```cpp
// cliext_multimap_const_reverse_iterator.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]" reversed
    Mymultimap::const_reverse_iterator crit = c1.rbegin();
    for (; crit != c1.rend(); ++crit)
        System::Console::Write("[{0} {1}] ", crit->first, crit->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[c 3] [b 2] [a 1]
```

## <a name="count"></a> multimap::Count (STL/CLR)

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
// cliext_multimap_count.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymultimap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    System::Console::WriteLine("count(L'A') = {0}", c1.count(L'A'));
    System::Console::WriteLine("count(L'b') = {0}", c1.count(L'b'));
    System::Console::WriteLine("count(L'C') = {0}", c1.count(L'C'));
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
count(L'A') = 0
count(L'b') = 1
count(L'C') = 0
```

## <a name="difference_type"></a> multimap::difference_type (STL/CLR)

Typ vzdálenosti se znaménkem mezi dvěma prvky.

### <a name="syntax"></a>Syntaxe

```cpp
typedef int difference_type;
```

### <a name="remarks"></a>Poznámky

Typ, který popisuje element může být záporný počet.

### <a name="example"></a>Příklad

```cpp
// cliext_multimap_difference_type.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymultimap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // compute positive difference
    Mymultimap::difference_type diff = 0;
    for (Mymultimap::iterator it = c1.begin(); it != c1.end(); ++it)
        ++diff;
    System::Console::WriteLine("end()-begin() = {0}", diff);

    // compute negative difference
    diff = 0;
    for (Mymultimap::iterator it = c1.end(); it != c1.begin(); --it)
        --diff;
    System::Console::WriteLine("begin()-end() = {0}", diff);
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
end()-begin() = 3
begin()-end() = -3
```

## <a name="empty"></a> multimap::Empty (STL/CLR)

Zkouší, zda nejsou přítomny žádné prvky.

### <a name="syntax"></a>Syntaxe

```cpp
bool empty();
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí hodnotu true pro prázdnou řízenou sekvenci. Je ekvivalentní [multimap::size (STL/CLR)](../dotnet/multimap-size-stl-clr.md)`() == 0`. Použijete ji k ověření, zda je prázdný objektu multimap.

### <a name="example"></a>Příklad

```cpp
// cliext_multimap_empty.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymultimap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
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
[a 1] [b 2] [c 3]
size() = 3
empty() = False
size() = 0
empty() = True
```

## <a name="end"></a> multimap::end (STL/CLR)

Určuje konec řízené sekvence.

### <a name="syntax"></a>Syntaxe

```cpp
iterator end();
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí obousměrný iterátor, který ukazuje za konec řízené sekvence. Můžete ji použít k získání iterátor, který určuje konec řízené sekvence; jeho stav kódu ne změnit, pokud se změní délka řízené sekvence.

### <a name="example"></a>Příklad

```cpp
// cliext_multimap_end.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymultimap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // inspect last two items
    Mymultimap::iterator it = c1.end();
    --it;
    --it;
    System::Console::WriteLine("*-- --end() = [{0} {1}]",
        it->first, it->second);
    ++it;
    System::Console::WriteLine("*--end() = [{0} {1}]",
        it->first, it->second);
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
*-- --end() = [b 2]
*--end() = [c 3]
```

## <a name="equal_range"></a> multimap::equal_range (STL/CLR)

Najde rozsah, který odpovídá zadanému klíči.

### <a name="syntax"></a>Syntaxe

```cpp
pair_iter_iter equal_range(key_type _Keyval);
```

#### <a name="parameters"></a>Parametry

*_Keyval*<br/>
Hodnota klíče pro hledání.

### <a name="remarks"></a>Poznámky

Metoda vrátí pár iterátorů `-` [multimap::lower_bound (STL/CLR)](../dotnet/multimap-lower-bound-stl-clr.md) `(_Keyval),` [multimap::upper_bound (STL/CLR)](../dotnet/multimap-upper-bound-stl-clr.md)`(_Keyval)`. Použijete ji k určení rozsahu prvků v řízené sekvenci aktuálně, které odpovídají zadanému klíči.

### <a name="example"></a>Příklad

```cpp
// cliext_multimap_equal_range.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
typedef Mymultimap::pair_iter_iter Pairii;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymultimap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // display results of failed search
    Pairii pair1 = c1.equal_range(L'x');
    System::Console::WriteLine("equal_range(L'x') empty = {0}",
        pair1.first == pair1.second);

    // display results of successful search
    pair1 = c1.equal_range(L'b');
    for (; pair1.first != pair1.second; ++pair1.first)
        System::Console::Write("[{0} {1}] ",
            pair1.first->first, pair1.first->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
equal_range(L'x') empty = True
[b 2]
```

## <a name="erase"></a> multimap::Erase (STL/CLR)

Odebere prvky v určených pozicích.

### <a name="syntax"></a>Syntaxe

```cpp
iterator erase(iterator where);
iterator erase(iterator first, iterator last);
bool erase(key_type key)
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

První členská funkce odstraní prvek řízené sekvence, na které odkazuje *kde*a vrátí iterátor, který určuje první prvek zbývající za prvkem, který odebere, nebo [multimap::end (STL / CLR)](../dotnet/multimap-end-stl-clr.md) `()` Pokud žádný takový prvek neexistuje. Použijete ji k odebrání jeden element.

Druhá členská funkce odebere prvky řízené sekvence v rozsahu [`first`, `last`) a vrátí iterátor, který určuje první prvek zbývající za všemi odstraněnými prvky, nebo `end()` Pokud žádný takový prvek existuje... Použijete ji k odebrání nula nebo více souvislých prvků.

Třetí členská funkce odstraní libovolný prvek řízenou sekvenci, jehož klíč má ekvivalentní řazení na *klíč*a vrátí počet prvků, které jsou odebrány. Použijete ho odebrat a spočítat všechny elementy, které odpovídají zadanému klíči.

Každý prvek mazání trvá určitou dobu úměrný logaritmu počtu prvků v řízené sekvenci.

### <a name="example"></a>Příklad

```cpp
// cliext_multimap_erase.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    cliext::multimap<wchar_t, int> c1;
    c1.insert(cliext::multimap<wchar_t, int>::make_value(L'a', 1));
    c1.insert(cliext::multimap<wchar_t, int>::make_value(L'b', 2));
    c1.insert(cliext::multimap<wchar_t, int>::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (cliext::multimap<wchar_t, int>::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // erase an element and reinspect
    cliext::multimap<wchar_t, int>::iterator it =
        c1.erase(c1.begin());
    System::Console::WriteLine("erase(begin()) = [{0} {1}]",
        it->first, it->second);

    // add elements and display " b c d e"
    c1.insert(cliext::multimap<wchar_t, int>::make_value(L'd', 4));
    c1.insert(cliext::multimap<wchar_t, int>::make_value(L'e', 5));
    for each (cliext::multimap<wchar_t, int>::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // erase all but end
    it = c1.end();
    it = c1.erase(c1.begin(), --it);
    System::Console::WriteLine("erase(begin(), end()-1) = [{0} {1}]",
        it->first, it->second);
    System::Console::WriteLine("size() = {0}", c1.size());

    // erase end
    System::Console::WriteLine("erase(L'x') = {0}", c1.erase(L'x'));
    System::Console::WriteLine("erase(L'e') = {0}", c1.erase(L'e'));
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
erase(begin()) = [b 2]
[b 2] [c 3] [d 4] [e 5]
erase(begin(), end()-1) = [e 5]
size() = 1
erase(L'x') = 0
erase(L'e') = 1
```

## <a name="find"></a> multimap::Find (STL/CLR)

Vyhledá prvek, který odpovídá zadanému klíči.

### <a name="syntax"></a>Syntaxe

```cpp
iterator find(key_type key);
```

#### <a name="parameters"></a>Parametry

*Klíč*<br/>
Hodnota klíče pro hledání.

### <a name="remarks"></a>Poznámky

Pokud má alespoň jeden element v řízené sekvenci s odpovídající řazení *klíč*, členská funkce vrátí iterátor určit jeden z těchto elementů; v opačném případě vrátí [multimap::end (STL/CLR)](../dotnet/multimap-end-stl-clr.md) `()`. Použijete ji k aktuálně vyhledejte elementu v řízené sekvenci, která odpovídá zadanému klíči.

### <a name="example"></a>Příklad

```cpp
// cliext_multimap_find.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymultimap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    System::Console::WriteLine("find {0} = {1}",
        L'A', c1.find(L'A') != c1.end());

    Mymultimap::iterator it = c1.find(L'b');
    System::Console::WriteLine("find {0} = [{1} {2}]",
        L'b', it->first, it->second);

    System::Console::WriteLine("find {0} = {1}",
        L'C', c1.find(L'C') != c1.end());
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
find A = False
find b = [b 2]
find C = False
```

## <a name="generic_container"></a> multimap::generic_container (STL/CLR)

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
// cliext_multimap_generic_container.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymultimap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct a generic container
    Mymultimap::generic_container^ gc1 = %c1;
    for each (Mymultimap::value_type elem in gc1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // modify generic and display original
    gc1->insert(Mymultimap::make_value(L'd', 4));
    for each (Mymultimap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // modify original and display generic
    c1.insert(Mymultimap::make_value(L'e', 5));
    for each (Mymultimap::value_type elem in gc1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
[a 1] [b 2] [c 3]
[a 1] [b 2] [c 3] [d 4]
[a 1] [b 2] [c 3] [d 4] [e 5]
```

## <a name="generic_iterator"></a> multimap::generic_iterator (STL/CLR)

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
// cliext_multimap_generic_iterator.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymultimap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct a generic container
    Mymultimap::generic_container^ gc1 = %c1;
    for each (Mymultimap::value_type elem in gc1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // get an element and display it
    Mymultimap::generic_iterator gcit = gc1->begin();
    Mymultimap::generic_value gcval = *gcit;
    System::Console::Write("[{0} {1}] ", gcval->first, gcval->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
[a 1] [b 2] [c 3]
[a 1]
```

## <a name="generic_reverse_iterator"></a> multimap::generic_reverse_iterator (STL/CLR)

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
// cliext_multimap_generic_reverse_iterator.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymultimap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct a generic container
    Mymultimap::generic_container^ gc1 = %c1;
    for each (Mymultimap::value_type elem in gc1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // get an element and display it
    Mymultimap::generic_reverse_iterator gcit = gc1->rbegin();
    Mymultimap::generic_value gcval = *gcit;
    System::Console::WriteLine("[{0} {1}] ", gcval->first, gcval->second);
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
[a 1] [b 2] [c 3]
[c 3]
```

## <a name="generic_value"></a> multimap::generic_value (STL/CLR)

Typ elementu pro použití s obecné rozhraní pro kontejner.

### <a name="syntax"></a>Syntaxe

```cpp
typedef GValue generic_value;
```

### <a name="remarks"></a>Poznámky

Typ, který popisuje objekt typu `GValue` hodnoty uložené elementu pro použití s obecné rozhraní pro tuto třídu šablony kontejneru, který popisuje.

### <a name="example"></a>Příklad

```cpp
// cliext_multimap_generic_value.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymultimap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct a generic container
    Mymultimap::generic_container^ gc1 = %c1;
    for each (Mymultimap::value_type elem in gc1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // get an element and display it
    Mymultimap::generic_iterator gcit = gc1->begin();
    Mymultimap::generic_value gcval = *gcit;
    System::Console::WriteLine("[{0} {1}] ", gcval->first, gcval->second);
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
[a 1] [b 2] [c 3]
[a 1]
```

## <a name="insert"></a> multimap::Insert (STL/CLR)

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
// cliext_multimap_insert.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymultimap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // insert a single value, unique and duplicate
    Mymultimap::iterator it =
        c1.insert(Mymultimap::make_value(L'x', 24));
    System::Console::WriteLine("insert([L'x' 24]) = [{0} {1}]",
        it->first, it->second);

    it = c1.insert(Mymultimap::make_value(L'b', 2));
    System::Console::WriteLine("insert([L'b' 2]) = [{0} {1}]",
        it->first, it->second);

    for each (Mymultimap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // insert a single value with hint
    it = c1.insert(c1.begin(), Mymultimap::make_value(L'y', 25));
    System::Console::WriteLine("insert(begin(), [L'y' 25]) = [{0} {1}]",
        it->first, it->second);
    for each (Mymultimap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // insert an iterator range
    Mymultimap c2;
    it = c1.end();
    c2.insert(c1.begin(), --it);
    for each (Mymultimap::value_type elem in c2)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // insert an enumeration
    Mymultimap c3;
    c3.insert(   // NOTE: cast is not needed
        (System::Collections::Generic::
            IEnumerable<Mymultimap::value_type>^)%c1);
    for each (Mymultimap::value_type elem in c3)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
insert([L'x' 24]) = [x 24]
insert([L'b' 2]) = [b 2]
[a 1] [b 2] [b 2] [c 3] [x 24]
insert(begin(), [L'y' 25]) = [y 25]
[a 1] [b 2] [b 2] [c 3] [x 24] [y 25]
[a 1] [b 2] [b 2] [c 3] [x 24]
[a 1] [b 2] [b 2] [c 3] [x 24] [y 25]
```

## <a name="iterator"></a> multimap::iterator (STL/CLR)

Typ iterátoru řízené sekvence

### <a name="syntax"></a>Syntaxe

```cpp
typedef T1 iterator;
```

### <a name="remarks"></a>Poznámky

Typ popisuje objekt neurčeného typu `T1` , který může sloužit jako obousměrný iterátor, který řízené sekvence.

### <a name="example"></a>Příklad

```cpp
// cliext_multimap_iterator.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    Mymultimap::iterator it = c1.begin();
    for (; it != c1.end(); ++it)
        System::Console::Write("[{0} {1}] ", it->first, it->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
```

## <a name="key_comp"></a> multimap::key_comp (STL/CLR)

Zkopíruje pořadí delegáta pro dva klíče.

### <a name="syntax"></a>Syntaxe

```cpp
key_compare^key_comp();
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí pořadí delegáta, který slouží k seřazení řízené sekvence. Použijete ji k porovnat dva klíče.

### <a name="example"></a>Příklad

```cpp
// cliext_multimap_key_comp.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    Mymultimap::key_compare^ kcomp = c1.key_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        kcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        kcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        kcomp(L'b', L'a'));
    System::Console::WriteLine();

    // test a different ordering rule
    Mymultimap c2 = cliext::greater<wchar_t>();
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

## <a name="key_compare"></a> multimap::key_compare (STL/CLR)

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
// cliext_multimap_key_compare.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    Mymultimap::key_compare^ kcomp = c1.key_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        kcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        kcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        kcomp(L'b', L'a'));
    System::Console::WriteLine();

    // test a different ordering rule
    Mymultimap c2 = cliext::greater<wchar_t>();
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

## <a name="key_type"></a> multimap::key_type (STL/CLR)

Typ klíče řazení

### <a name="syntax"></a>Syntaxe

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro parametr šablony *klíč*.

### <a name="example"></a>Příklad

```cpp
// cliext_multimap_key_type.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]" using key_type
    for (Mymultimap::iterator it = c1.begin(); it != c1.end(); ++it)
        {   // store element in key_type object
        Mymultimap::key_type val = it->first;

        System::Console::Write("{0} ", val);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="lower_bound"></a> multimap::lower_bound (STL/CLR)

Vyhledá počátek rozsahu, který odpovídá zadanému klíči.

### <a name="syntax"></a>Syntaxe

```cpp
iterator lower_bound(key_type key);
```

#### <a name="parameters"></a>Parametry

*Klíč*<br/>
Hodnota klíče pro hledání.

### <a name="remarks"></a>Poznámky

Členská funkce určuje první prvek `X` v řízené sekvenci, která má stejné pořadí na *klíč*. Pokud žádný takový prvek neexistuje, vrátí [multimap::end (STL/CLR)](../dotnet/multimap-end-stl-clr.md)`()`; v opačném případě vrátí iterátor, který určuje `X`. Použijete ji k aktuálně vyhledejte na začátek pořadí prvků v řízené sekvenci, které odpovídají zadanému klíči.

### <a name="example"></a>Příklad

```cpp
// cliext_multimap_lower_bound.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymultimap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    System::Console::WriteLine("lower_bound(L'x')==end() = {0}",
        c1.lower_bound(L'x') == c1.end());

    Mymultimap::iterator it = c1.lower_bound(L'a');
    System::Console::WriteLine("*lower_bound(L'a') = [{0} {1}]",
        it->first, it->second);
    it = c1.lower_bound(L'b');
    System::Console::WriteLine("*lower_bound(L'b') = [{0} {1}]",
        it->first, it->second);
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
lower_bound(L'x')==end() = True
*lower_bound(L'a') = [a 1]
*lower_bound(L'b') = [b 2]
```

## <a name="make_value"></a> multimap::make_value (STL/CLR)

Vytvoří objekt hodnoty.

### <a name="syntax"></a>Syntaxe

```cpp
static value_type make_value(key_type key, mapped_type mapped);
```

#### <a name="parameters"></a>Parametry

*Klíč*<br/>
Hodnota klíče používat.

*Mapovat*<br/>
Mapovaná hledanou hodnotu.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí `value_type` objekt, jehož klíč je *klíč* a jejichž mapované hodnoty se *namapované*. Použijete ji k vytvoření objektu vhodný pro použití s několika další členské funkce.

### <a name="example"></a>Příklad

```cpp
// cliext_multimap_make_value.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymultimap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
```

## <a name="mapped_type"></a> multimap::mapped_type (STL/CLR)

Typ mapované hodnoty přiřazené ke každému klíči

### <a name="syntax"></a>Syntaxe

```cpp
typedef Mapped mapped_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro parametr šablony *mapované*.

### <a name="example"></a>Příklad

```cpp
// cliext_multimap_mapped_type.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]" using mapped_type
    for (Mymultimap::iterator it = c1.begin(); it != c1.end(); ++it)
        {   // store element in mapped_type object
        Mymultimap::mapped_type val = it->second;

        System::Console::Write("{0} ", val);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
1 2 3
```

## <a name="multimap"></a> multimap::multimap (STL/CLR)

Sestaví objekt kontejneru.

### <a name="syntax"></a>Syntaxe

```cpp
multimap();
explicit multimap(key_compare^ pred);
multimap(multimap<Key, Mapped>% right);
multimap(multimap<Key, Mapped>^ right);
template<typename InIter>
    multimapmultimap(InIter first, InIter last);
template<typename InIter>
    multimap(InIter first, InIter last,
        key_compare^ pred);
multimap(System::Collections::Generic::IEnumerable<GValue>^ right);
multimap(System::Collections::Generic::IEnumerable<GValue>^ right,
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

`multimap();`

Inicializuje výchozí řazení predikátu řízené sekvence bez prvků `key_compare()`. Použijete ji k určení prázdnou počáteční řízenou sekvenci, s výchozí řazení predikátu.

Konstruktor:

`explicit multimap(key_compare^ pred);`

Inicializuje řízené sekvence bez prvků pořadí predikátem *před*. Použít prázdnou počáteční řízenou sekvenci, určit se zadanou predikát pořadí.

Konstruktor:

`multimap(multimap<Key, Mapped>% right);`

Inicializuje řízené sekvence s pořadím [`right.begin()`, `right.end()`), s výchozí řazení predikátu. Můžete použít k určení počáteční řízené sekvence, který je kopii sekvence řízenou parametrem objektu multimap *správné*, s výchozí řazení predikátu.

Konstruktor:

`multimap(multimap<Key, Mapped>^ right);`

Inicializuje řízené sekvence s pořadím [`right->begin()`, `right->end()`), s výchozí řazení predikátu. Můžete použít k určení počáteční řízené sekvence, který je kopii sekvence řízenou parametrem objektu multimap *správné*, s výchozí řazení predikátu.

Konstruktor:

`template<typename InIter> multimap(InIter first, InIter last);`

Inicializuje řízené sekvence s pořadím [`first`, `last`), s výchozí řazení predikátu. Používejte aby řízené sekvence kopii jiné pořadí, s výchozí řazení predikátu.

Konstruktor:

`template<typename InIter> multimap(InIter first, InIter last, key_compare^ pred);`

Inicializuje řízené sekvence s pořadím [`first`, `last`), pořadí predikátem *před*. Použijete ji k vytvoření kopie jiné pořadí se zadanou predikát pořadí řízené sekvence.

Konstruktor:

`multimap(System::Collections::Generic::IEnumerable<Key>^ right);`

Inicializuje řízené sekvence s pořadí určeném enumerátor *správné*, s výchozí řazení predikátu. Použijete ji k vytvoření kopie jiné pořadí popsal čítače, s výchozí řazení predikátu řízené sekvence.

Konstruktor:

`multimap(System::Collections::Generic::IEnumerable<Key>^ right, key_compare^ pred);`

Inicializuje řízené sekvence s pořadí určeném enumerátor *správné*, pořadí predikátem *před*. Použijete ji k vytvoření kopie jiné pořadí popsal enumerátor se zadanou predikát pořadí řízené sekvence.

### <a name="example"></a>Příklad

```cpp
// cliext_multimap_construct.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
// construct an empty container
    Mymultimap c1;
    System::Console::WriteLine("size() = {0}", c1.size());

    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));
    for each (Mymultimap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct with an ordering rule
    Mymultimap c2 = cliext::greater_equal<wchar_t>();
    System::Console::WriteLine("size() = {0}", c2.size());

    c2.insert(c1.begin(), c1.end());
    for each (Mymultimap::value_type elem in c2)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct with an iterator range
    Mymultimap c3(c1.begin(), c1.end());
    for each (Mymultimap::value_type elem in c3)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct with an iterator range and an ordering rule
    Mymultimap c4(c1.begin(), c1.end(),
        cliext::greater_equal<wchar_t>());
    for each (Mymultimap::value_type elem in c4)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct with an enumeration
    Mymultimap c5(   // NOTE: cast is not needed
        (System::Collections::Generic::IEnumerable<
            Mymultimap::value_type>^)%c3);
    for each (Mymultimap::value_type elem in c5)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct with an enumeration and an ordering rule
    Mymultimap c6(   // NOTE: cast is not needed
        (System::Collections::Generic::IEnumerable<
            Mymultimap::value_type>^)%c3,
                cliext::greater_equal<wchar_t>());
    for each (Mymultimap::value_type elem in c6)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct by copying another container
    Mymultimap c7(c4);
    for each (Mymultimap::value_type elem in c7)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct by copying a container handle
    Mymultimap c8(%c3);
    for each (Mymultimap::value_type elem in c8)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
size() = 0
[a 1] [b 2] [c 3]
size() = 0
[c 3] [b 2] [a 1]
[a 1] [b 2] [c 3]
[c 3] [b 2] [a 1]
[a 1] [b 2] [c 3]
[c 3] [b 2] [a 1]
[c 3] [b 2] [a 1]
[a 1] [b 2] [c 3]
```

## <a name="op_as"></a> multimap::Operator = (STL/CLR)

Nahradí řízené sekvence.

### <a name="syntax"></a>Syntaxe

```cpp
multimap<Key, Mapped>% operator=(multimap<Key, Mapped>% right);
```

#### <a name="parameters"></a>Parametry

*doprava*<br/>
Kontejner pro kopírování.

### <a name="remarks"></a>Poznámky

Kopie členský operátor *správné* na objekt, vrátí `*this`. Můžete použít k nahraďte kopii řízené sekvence v řízené sekvenci *správné*.

### <a name="example"></a>Příklad

```cpp
// cliext_multimap_operator_as.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymultimap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // assign to a new container
    Mymultimap c2;
    c2 = c1;
// display contents " [a 1] [b 2] [c 3]"
    for each (Mymultimap::value_type elem in c2)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
[a 1] [b 2] [c 3]
```

## <a name="rbegin"></a> multimap::rbegin (STL/CLR)

Určuje začátek řízené obrácené sekvenci.

### <a name="syntax"></a>Syntaxe

```cpp
reverse_iterator rbegin();
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí zpětný iterátor, který určuje poslední prvek řízenou sekvenci nebo hned za začátku k prázdné sekvenci. Proto, označí `beginning` reverzní pořadí. Můžete ji použít k získání iterátor, který určuje `current` začátek řízené sekvence viděli v obráceném pořadí, ale jeho stav můžete změnit, pokud se změní délka řízené sekvence.

### <a name="example"></a>Příklad

```cpp
// cliext_multimap_rbegin.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymultimap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // inspect first two items in reversed sequence
    Mymultimap::reverse_iterator rit = c1.rbegin();
    System::Console::WriteLine("*rbegin() = [{0} {1}]",
        rit->first, rit->second);
    ++rit;
    System::Console::WriteLine("*++rbegin() = [{0} {1}]",
        rit->first, rit->second);
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
*rbegin() = [c 3]
*++rbegin() = [b 2]
```

## <a name="reference"></a> multimap::Reference (STL/CLR)

Typ odkazu na prvek

### <a name="syntax"></a>Syntaxe

```cpp
typedef value_type% reference;
```

### <a name="remarks"></a>Poznámky

Typ, který popisuje odkaz na element.

### <a name="example"></a>Příklad

```cpp
// cliext_multimap_reference.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    Mymultimap::iterator it = c1.begin();
    for (; it != c1.end(); ++it)
        {   // get a reference to an element
        Mymultimap::reference ref = *it;
        System::Console::Write("[{0} {1}] ", ref->first, ref->second);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
```

## <a name="rend"></a> multimap::rend (STL/CLR)

Určuje konec řízené obrácené sekvenci.

### <a name="syntax"></a>Syntaxe

```cpp
reverse_iterator rend();
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí "reverse iterator", který ukazuje za začátek řízené sekvence. Proto, označí `end` reverzní pořadí. Můžete ji použít k získání iterátor, který určuje `current` konec řízené sekvence viděli v obráceném pořadí, ale jeho stav můžete změnit, pokud se změní délka řízené sekvence.

### <a name="example"></a>Příklad

```cpp
// cliext_multimap_rend.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymultimap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // inspect first two items in reversed sequence
    Mymultimap::reverse_iterator rit = c1.rend();
    --rit;
    --rit;
    System::Console::WriteLine("*-- --rend() = [{0} {1}]",
        rit->first, rit->second);
    ++rit;
    System::Console::WriteLine("*--rend() = [{0} {1}]",
        rit->first, rit->second);
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
*-- --rend() = [b 2]
*--rend() = [a 1]
```

## <a name="reverse_iterator"></a> multimap::reverse_iterator (STL/CLR)

Typ "reverse iterator" pro řízenou sekvenci.

### <a name="syntax"></a>Syntaxe

```cpp
typedef T3 reverse_iterator;
```

### <a name="remarks"></a>Poznámky

Typ popisuje objekt neurčeného typu `T3` , který může sloužit jako "reverse iterator" pro řízenou sekvenci.

### <a name="example"></a>Příklad

```cpp
// cliext_multimap_reverse_iterator.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]" reversed
    Mymultimap::reverse_iterator rit = c1.rbegin();
    for (; rit != c1.rend(); ++rit)
        System::Console::Write("[{0} {1}] ", rit->first, rit->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[c 3] [b 2] [a 1]
```

## <a name="size"></a> multimap::size (STL/CLR)

Spočítá počet prvků.

### <a name="syntax"></a>Syntaxe

```cpp
size_type size();
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí délku objektu řízené sekvence. Použijete ji k určení počtu prvků v řízené sekvenci aktuálně. Pokud vás zajímá, jestli je pořadí má nenulovou velikost, naleznete v tématu [multimap::empty (STL/CLR)](../dotnet/multimap-empty-stl-clr.md)`()`.

### <a name="example"></a>Příklad

```cpp
// cliext_multimap_size.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymultimap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // clear the container and reinspect
    c1.clear();
    System::Console::WriteLine("size() = {0} after clearing", c1.size());

    // add elements and clear again
    c1.insert(Mymultimap::make_value(L'd', 4));
    c1.insert(Mymultimap::make_value(L'e', 5));
    System::Console::WriteLine("size() = {0} after adding 2", c1.size());
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
size() = 0 after clearing
size() = 2 after adding 2
```

## <a name="size_type"></a> multimap::size_type (STL/CLR)

Typ vzdálenosti se znaménkem mezi dvěma elementu.

### <a name="syntax"></a>Syntaxe

```cpp
typedef int size_type;
```

### <a name="remarks"></a>Poznámky

Typ, který popisuje počet prvků záporná.

### <a name="example"></a>Příklad

```cpp
// cliext_multimap_size_type.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymultimap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // compute positive difference
    Mymultimap::size_type diff = 0;
    for (Mymultimap::iterator it = c1.begin(); it != c1.end(); ++it)
        ++diff;
    System::Console::WriteLine("end()-begin() = {0}", diff);
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
end()-begin() = 3
```

## <a name="swap"></a> multimap::swap (STL/CLR)

Zamění obsah dvou kontejnerů.

### <a name="syntax"></a>Syntaxe

```cpp
void swap(multimap<Key, Mapped>% right);
```

#### <a name="parameters"></a>Parametry

*doprava*<br/>
Kontejner pro obsah s.

### <a name="remarks"></a>Poznámky

Členská funkce Zamění řízené sekvence mezi `this` a *správné*. Provádí se v konstantním času a vyvolá žádné výjimky. Můžete použít jako rychlý způsob, jak Zamění obsah dvou kontejnerů.

### <a name="example"></a>Příklad

```cpp
// cliext_multimap_swap.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymultimap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct another container with repetition of values
    Mymultimap c2;
    c2.insert(Mymultimap::make_value(L'd', 4));
    c2.insert(Mymultimap::make_value(L'e', 5));
    c2.insert(Mymultimap::make_value(L'f', 6));
    for each (Mymultimap::value_type elem in c2)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // swap and redisplay
    c1.swap(c2);
    for each (Mymultimap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    for each (Mymultimap::value_type elem in c2)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
[d 4] [e 5] [f 6]
[d 4] [e 5] [f 6]
[a 1] [b 2] [c 3]
```

## <a name="to_array"></a> multimap::to_array (STL/CLR)

Zkopíruje do nového pole řízené sekvence.

### <a name="syntax"></a>Syntaxe

```cpp
cli::array<value_type>^ to_array();
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí pole obsahující řízené sekvence. Použijete ji získat kopii řízenou sekvenci pole formuláře.

### <a name="example"></a>Příklad

```cpp
// cliext_multimap_to_array.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // copy the container and modify it
    cli::array<Mymultimap::value_type>^ a1 = c1.to_array();

    c1.insert(Mymultimap::make_value(L'd', 4));
    for each (Mymultimap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // display the earlier array copy
    for each (Mymultimap::value_type elem in a1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3] [d 4]
[a 1] [b 2] [c 3]
```

## <a name="upper_bound"></a> multimap::upper_bound (STL/CLR)

Najde konec rozsahu, který odpovídá zadanému klíči.

### <a name="syntax"></a>Syntaxe

```cpp
iterator upper_bound(key_type key);
```

#### <a name="parameters"></a>Parametry

*Klíč*<br/>
Hodnota klíče pro hledání.

### <a name="remarks"></a>Poznámky

Členská funkce určuje poslední prvek `X` v řízené sekvenci, která má stejné pořadí na *klíč*. Pokud žádný takový prvek neexistuje, nebo pokud `X` je po posledním prvku v řízené sekvenci vrátí [multimap::end (STL/CLR)](../dotnet/multimap-end-stl-clr.md)`()`; v opačném případě vrátí iterátor, který určuje prvního prvku mimo `X`. Pomocí aktuálně najít konec pořadí prvků v řízené sekvenci, které odpovídají zadanému klíči.

### <a name="example"></a>Příklad

```cpp
// cliext_multimap_upper_bound.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymultimap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    System::Console::WriteLine("upper_bound(L'x')==end() = {0}",
        c1.upper_bound(L'x') == c1.end());

    Mymultimap::iterator it = c1.upper_bound(L'a');
    System::Console::WriteLine("*upper_bound(L'a') = [{0} {1}]",
        it->first, it->second);
    it = c1.upper_bound(L'b');
    System::Console::WriteLine("*upper_bound(L'b') = [{0} {1}]",
        it->first, it->second);
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
upper_bound(L'x')==end() = True
*upper_bound(L'a') = [b 2]
*upper_bound(L'b') = [c 3]
```

## <a name="value_comp"></a> multimap::value_comp (STL/CLR)

Zkopíruje pořadí delegáta pro dvě hodnoty prvků.

### <a name="syntax"></a>Syntaxe

```cpp
value_compare^ value_comp();
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí pořadí delegáta, který slouží k seřazení řízené sekvence. Použijete ji k porovnat dvě hodnoty prvků.

### <a name="example"></a>Příklad

```cpp
// cliext_multimap_value_comp.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    Mymultimap::value_compare^ kcomp = c1.value_comp();

    System::Console::WriteLine("compare([L'a', 1], [L'a', 1]) = {0}",
        kcomp(Mymultimap::make_value(L'a', 1),
            Mymultimap::make_value(L'a', 1)));
    System::Console::WriteLine("compare([L'a', 1], [L'b', 2]) = {0}",
        kcomp(Mymultimap::make_value(L'a', 1),
            Mymultimap::make_value(L'b', 2)));
    System::Console::WriteLine("compare([L'b', 2], [L'a', 1]) = {0}",
        kcomp(Mymultimap::make_value(L'b', 2),
            Mymultimap::make_value(L'a', 1)));
    System::Console::WriteLine();
    return (0);
    }
```

```Output
compare([L'a', 1], [L'a', 1]) = False
compare([L'a', 1], [L'b', 2]) = True
compare([L'b', 2], [L'a', 1]) = False
```

## <a name="value_compare"></a> multimap::value_compare (STL/CLR)

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
// cliext_multimap_value_compare.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    Mymultimap::value_compare^ kcomp = c1.value_comp();

    System::Console::WriteLine("compare([L'a', 1], [L'a', 1]) = {0}",
        kcomp(Mymultimap::make_value(L'a', 1),
            Mymultimap::make_value(L'a', 1)));
    System::Console::WriteLine("compare([L'a', 1], [L'b', 2]) = {0}",
        kcomp(Mymultimap::make_value(L'a', 1),
            Mymultimap::make_value(L'b', 2)));
    System::Console::WriteLine("compare([L'b', 2], [L'a', 1]) = {0}",
        kcomp(Mymultimap::make_value(L'b', 2),
            Mymultimap::make_value(L'a', 1)));
    System::Console::WriteLine();
    return (0);
    }
```

```Output
compare([L'a', 1], [L'a', 1]) = False
compare([L'a', 1], [L'b', 2]) = True
compare([L'b', 2], [L'a', 1]) = False
```

## <a name="value_type"></a> multimap::value_type (STL/CLR)

Typ prvku

### <a name="syntax"></a>Syntaxe

```cpp
typedef generic_value value_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro `generic_value`.

### <a name="example"></a>Příklad

```cpp
// cliext_multimap_value_type.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]" using value_type
    for (Mymultimap::iterator it = c1.begin(); it != c1.end(); ++it)
        {   // store element in value_type object
        Mymultimap::value_type val = *it;
        System::Console::Write("[{0} {1}] ", val->first, val->second);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
```

## <a name="op_neq"></a> Operator! = (multimap) (STL/CLR)

Seznam není rovno porovnání.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Key,
    typename Mapped>
    bool operator!=(multimap<Key, Mapped>% left,
        multimap<Key, Mapped>% right);
```

#### <a name="parameters"></a>Parametry

*doleva*<br/>
Levé kontejner k porovnání.

*doprava*<br/>
Správném kontejneru pro porovnání.

### <a name="remarks"></a>Poznámky

Vrátí funkci operátoru `!(left == right)`. Pomocí něho můžete testovat, zda *levé* není stejný jako seřazené *správné* když jsou dvě multimaps porovnání elementu pomocí elementu.

### <a name="example"></a>Příklad

```cpp
// cliext_multimap_operator_ne.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymultimap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // assign to a new container
    Mymultimap c2;
    c2.insert(Mymultimap::make_value(L'a', 1));
    c2.insert(Mymultimap::make_value(L'b', 2));
    c2.insert(Mymultimap::make_value(L'd', 4));

    // display contents " [a 1] [b 2] [d 4]"
    for each (Mymultimap::value_type elem in c2)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    System::Console::WriteLine("[a b c] != [a b c] is {0}",
        c1 != c1);
    System::Console::WriteLine("[a b c] != [a b d] is {0}",
        c1 != c2);
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
[a 1] [b 2] [d 4]
[a b c] != [a b c] is False
[a b c] != [a b d] is True
```

## <a name="op_lt"></a> operátor&lt; (multimap) (STL/CLR)

Seznam menší než porovnání.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Key,
    typename Mapped>
    bool operator<(multimap<Key, Mapped>% left,
        multimap<Key, Mapped>% right);
```

#### <a name="parameters"></a>Parametry

*doleva*<br/>
Levé kontejner k porovnání.

*doprava*<br/>
Správném kontejneru pro porovnání.

### <a name="remarks"></a>Poznámky

Operátoru funkce vrátí hodnota true v případě, pro nejnižší pozici `i` pro kterou `!(right[i] < left[i])` je také hodnotu true, který `left[i] < right[i]`. V opačném případě vrátí `left->size() < right->size()` pomocí něho můžete testovat, zda *levé* je řazen před *správné* když jsou dvě multimaps porovnání elementu pomocí elementu.

### <a name="example"></a>Příklad

```cpp
// cliext_multimap_operator_lt.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymultimap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // assign to a new container
    Mymultimap c2;
    c2.insert(Mymultimap::make_value(L'a', 1));
    c2.insert(Mymultimap::make_value(L'b', 2));
    c2.insert(Mymultimap::make_value(L'd', 4));

    // display contents " [a 1] [b 2] [d 4]"
    for each (Mymultimap::value_type elem in c2)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    System::Console::WriteLine("[a b c] < [a b c] is {0}",
        c1 < c1);
    System::Console::WriteLine("[a b c] < [a b d] is {0}",
        c1 < c2);
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
[a 1] [b 2] [d 4]
[a b c] < [a b c] is False
[a b c] < [a b d] is True
```

## <a name="op_lteq"></a> operátor&lt;= (multimap) (STL/CLR)

Seznam menší nebo rovna porovnání.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Key,
    typename Mapped>
    bool operator<=(multimap<Key, Mapped>% left,
        multimap<Key, Mapped>% right);
```

#### <a name="parameters"></a>Parametry

*doleva*<br/>
Levé kontejner k porovnání.

*doprava*<br/>
Správném kontejneru pro porovnání.

### <a name="remarks"></a>Poznámky

Vrátí funkci operátoru `!(right < left)`. Pomocí něho můžete testovat, zda *levé* není seřazené po *správné* když jsou dvě multimaps porovnání elementu pomocí elementu.

### <a name="example"></a>Příklad

```cpp
// cliext_multimap_operator_le.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymultimap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // assign to a new container
    Mymultimap c2;
    c2.insert(Mymultimap::make_value(L'a', 1));
    c2.insert(Mymultimap::make_value(L'b', 2));
    c2.insert(Mymultimap::make_value(L'd', 4));

    // display contents " [a 1] [b 2] [d 4]"
    for each (Mymultimap::value_type elem in c2)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    System::Console::WriteLine("[a b c] <= [a b c] is {0}",
        c1 <= c1);
    System::Console::WriteLine("[a b d] <= [a b c] is {0}",
        c2 <= c1);
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
[a 1] [b 2] [d 4]
[a b c] <= [a b c] is True
[a b d] <= [a b c] is False
```

## <a name="op_eq"></a> Operator == (multimap) (STL/CLR)

Porovnání rovna seznamu.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Key,
    typename Mapped>
    bool operator==(multimap<Key, Mapped>% left,
        multimap<Key, Mapped>% right);
```

#### <a name="parameters"></a>Parametry

*doleva*<br/>
Levé kontejner k porovnání.

*doprava*<br/>
Správném kontejneru pro porovnání.

### <a name="remarks"></a>Poznámky

Funkce operátoru vrátí hodnotu true pouze v případě, že řídí sekvencí *levé* a *správné* mít stejnou délku a pro každou pozici `i`, `left[i] ==` `right[i]`. Pomocí něho můžete testovat, zda *levé* je stejný jako seřazené *správné* když jsou dvě multimaps porovnání elementu pomocí elementu.

### <a name="example"></a>Příklad

```cpp
// cliext_multimap_operator_eq.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymultimap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // assign to a new container
    Mymultimap c2;
    c2.insert(Mymultimap::make_value(L'a', 1));
    c2.insert(Mymultimap::make_value(L'b', 2));
    c2.insert(Mymultimap::make_value(L'd', 4));

    // display contents " [a 1] [b 2] [d 4]"
    for each (Mymultimap::value_type elem in c2)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    System::Console::WriteLine("[a b c] == [a b c] is {0}",
        c1 == c1);
    System::Console::WriteLine("[a b c] == [a b d] is {0}",
        c1 == c2);
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
[a 1] [b 2] [d 4]
[a b c] == [a b c] is True
[a b c] == [a b d] is False
```

## <a name="op_gt"></a> operátor&gt; (multimap) (STL/CLR)

Seznam je větší než porovnání.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Key,
    typename Mapped>
    bool operator>(multimap<Key, Mapped>% left,
        multimap<Key, Mapped>% right);
```

#### <a name="parameters"></a>Parametry

*doleva*<br/>
Levé kontejner k porovnání.

*doprava*<br/>
Správném kontejneru pro porovnání.

### <a name="remarks"></a>Poznámky

Vrátí funkci operátoru `right` `<` `left`. Pomocí něho můžete testovat, zda *levé* seřazené po *správné* když jsou dvě multimaps porovnání elementu pomocí elementu.

### <a name="example"></a>Příklad

```cpp
// cliext_multimap_operator_gt.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymultimap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // assign to a new container
    Mymultimap c2;
    c2.insert(Mymultimap::make_value(L'a', 1));
    c2.insert(Mymultimap::make_value(L'b', 2));
    c2.insert(Mymultimap::make_value(L'd', 4));

    // display contents " [a 1] [b 2] [d 4]"
    for each (Mymultimap::value_type elem in c2)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    System::Console::WriteLine("[a b c] > [a b c] is {0}",
        c1 > c1);
    System::Console::WriteLine("[a b d] > [a b c] is {0}",
        c2 > c1);
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
[a 1] [b 2] [d 4]
[a b c] > [a b c] is False
[a b d] > [a b c] is True
```

## <a name="op_gteq"></a> operátor&gt;= (multimap) (STL/CLR)

Seznam větší než nebo rovna porovnání.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Key,
    typename Mapped>
    bool operator>=(multimap<Key, Mapped>% left,
        multimap<Key, Mapped>% right);
```

#### <a name="parameters"></a>Parametry

*doleva*<br/>
Levé kontejner k porovnání.

*doprava*<br/>
Správném kontejneru pro porovnání.

### <a name="remarks"></a>Poznámky

Vrátí funkci operátoru `!(left` `<` `right)`. Pomocí něho můžete testovat, zda *levé* není řazen před *správné* když jsou dvě multimaps porovnání elementu pomocí elementu.

### <a name="example"></a>Příklad

```cpp
// cliext_multimap_operator_ge.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymultimap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // assign to a new container
    Mymultimap c2;
    c2.insert(Mymultimap::make_value(L'a', 1));
    c2.insert(Mymultimap::make_value(L'b', 2));
    c2.insert(Mymultimap::make_value(L'd', 4));

    // display contents " [a 1] [b 2] [d 4]"
    for each (Mymultimap::value_type elem in c2)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    System::Console::WriteLine("[a b c] >= [a b c] is {0}",
        c1 >= c1);
    System::Console::WriteLine("[a b c] >= [a b d] is {0}",
        c1 >= c2);
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
[a 1] [b 2] [d 4]
[a b c] >= [a b c] is True
[a b c] >= [a b d] is False
```