---
title: map (STL/CLR)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cliext::map
- cliext::map::begin
- cliext::map::clear
- cliext::map::const_iterator
- cliext::map::const_reference
- cliext::map::const_reverse_iterator
- cliext::map::count
- cliext::map::difference_type
- cliext::map::empty
- cliext::map::end
- cliext::map::equal_range
- cliext::map::erase
- cliext::map::find
- cliext::map::generic_container
- cliext::map::generic_iterator
- cliext::map::generic_reverse_iterator
- cliext::map::generic_value
- cliext::map::insert
- cliext::map::iterator
- cliext::map::key_comp
- cliext::map::key_compare
- cliext::map::key_type
- cliext::map::lower_bound
- cliext::map::make_value
- cliext::map::map
- cliext::map::mapped_type
- cliext::map::operator=
- cliext::map::operator
- cliext::map::rbegin
- cliext::map::reference
- cliext::map::rend
- cliext::map::reverse_iterator
- cliext::map::size
- cliext::map::size_type
- cliext::map::swap
- cliext::map::to_array
- cliext::map::upper_bound
- cliext::map::value_comp
- cliext::map::value_compare
- cliext::map::value_type
- cliext::operator!= (map)
- cliext::operator< (map)
- cliext::operator<= (map)
- cliext::operator== (map)
- cliext::operator> (map)
- cliext::operator>= (map)
helpviewer_keywords:
- <map> header [STL/CLR]
- map class [STL/CLR]
- <cliext/map> header [STL/CLR]
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
- operator!= (map) member [STL/CLR]
- operator< (map) member [STL/CLR]
- operator<= (map) member [STL/CLR]
- operator== (map) member [STL/CLR]
- operator> (map) member [STL/CLR]
- operator>= (map) member [STL/CLR]
ms.assetid: 8b0a7764-b5e4-4175-a802-82b72eb8662a
ms.openlocfilehash: 19b450e256a428769ca6588227e9249e4e21f51d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80208543"
---
# <a name="map-stlclr"></a>map (STL/CLR)

Třída šablony popisuje objekt, který ovládá proměnlivou délku posloupnosti prvků, které mají obousměrný přístup. Pomocí `map` kontejnerů můžete spravovat sekvenci prvků jako (skoro) vyvážený uspořádaný strom uzlů, z nichž každý ukládá jeden element. Prvek se skládá z klíče pro objednávání sekvence a mapované hodnoty, které jsou společně pro jízdní.

V popisu níže je `GValue` stejné jako:

`Microsoft::VisualC::StlClr::GenericPair<GKey, GMapped>`

kde:

`GKey` je stejný jako *klíč* , pokud se jedná o typ REF, v takovém případě je `Key^`

`GMapped` je stejná jako *mapovaná* , pokud se jedná o typ REF, v takovém případě je `Mapped^`

## <a name="syntax"></a>Syntaxe

```cpp
template<typename Key,
    typename Mapped>
    ref class map
        :   public
        System::ICloneable,
        System::Collections::IEnumerable,
        System::Collections::ICollection,
        System::Collections::Generic::IEnumerable<GValue>,
        System::Collections::Generic::ICollection<GValue>,
        System::Collections::Generic::IList<GValue>,
        System::Collections::Generic::IDictionary<Gkey, GMapped>,
        Microsoft::VisualC::StlClr::ITree<Gkey, GValue>
    { ..... };
```

### <a name="parameters"></a>Parametry

*Klíč*<br/>
Typ klíčové součásti prvku v řízené sekvenci.

*Mapovaný*<br/>
Typ dodatečné součásti prvku v řízené sekvenci.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<cliext –/map >

**Obor názvů:** cliext –

## <a name="declarations"></a>Deklarace

|Definice typu|Popis|
|---------------------|-----------------|
|[map::const_iterator (STL/CLR)](#const_iterator)|Typ konstantního iterátoru řízené sekvence|
|[map::const_reference (STL/CLR)](#const_reference)|Typ konstantního odkazu na prvek|
|[map::const_reverse_iterator (STL/CLR)](#const_reverse_iterator)|Typ konstantního reverzního iterátoru řízené sekvence.|
|[map::difference_type (STL/CLR)](#difference_type)|Typ (možná znaménko) vzdálenosti mezi dvěma prvky.|
|[map::generic_container (STL/CLR)](#generic_container)|Typ obecného rozhraní pro kontejner.|
|[map::generic_iterator (STL/CLR)](#generic_iterator)|Typ iterátoru pro obecné rozhraní kontejneru.|
|[map::generic_reverse_iterator (STL/CLR)](#generic_reverse_iterator)|Typ reverzního iterátoru pro obecné rozhraní kontejneru.|
|[map::generic_value (STL/CLR)](#generic_value)|Typ elementu pro obecné rozhraní kontejneru.|
|[map::iterator (STL/CLR)](#iterator)|Typ iterátoru řízené sekvence|
|[map::key_compare (STL/CLR)](#key_compare)|Delegát řazení pro dva klíče.|
|[map::key_type (STL/CLR)](#key_type)|Typ klíče řazení|
|[map::mapped_type (STL/CLR)](#mapped_type)|Typ mapované hodnoty přidružené k jednotlivým klíčům.|
|[map::reference (STL/CLR)](#reference)|Typ odkazu na prvek|
|[map::reverse_iterator (STL/CLR)](#reverse_iterator)|Typ reverzního iterátoru řízené sekvence.|
|[map::size_type (STL/CLR)](#size_type)|Typ (nezáporné) vzdálenosti mezi dvěma prvky.|
|[map::value_compare (STL/CLR)](#value_compare)|Delegát řazení pro dvě hodnoty elementu.|
|[map::value_type (STL/CLR)](#value_type)|Typ prvku|

|Členská funkce|Popis|
|---------------------|-----------------|
|[map::begin (STL/CLR)](#begin)|Určuje začátek řízené sekvence.|
|[map::clear (STL/CLR)](#clear)|Odebere všechny prvky.|
|[map::count (STL/CLR)](#count)|Spočítá prvky, které odpovídají zadanému klíči.|
|[map::empty (STL/CLR)](#empty)|Zkouší, zda nejsou přítomny žádné prvky.|
|[map::end (STL/CLR)](#end)|Určuje konec řízené sekvence.|
|[map::equal_range (STL/CLR)](#equal_range)|Najde rozsah, který odpovídá zadanému klíči.|
|[map::erase (STL/CLR)](#erase)|Odebere prvky v určených pozicích.|
|[map::find (STL/CLR)](#find)|Vyhledá prvek, který odpovídá zadanému klíči.|
|[map::insert (STL/CLR)](#insert)|Přidá prvky.|
|[map::key_comp (STL/CLR)](#key_comp)|Zkopíruje delegáta řazení dvou klíčů.|
|[map::lower_bound (STL/CLR)](#lower_bound)|Vyhledá začátek rozsahu, který odpovídá zadanému klíči.|
|[map::make_value (STL/CLR)](#make_value)|Vytvoří objekt hodnoty.|
|[map::map (STL/CLR)](#map)|Sestaví objekt kontejneru.|
|[map::rbegin (STL/CLR)](#rbegin)|Určuje začátek obrácené kontrolované sekvence.|
|[map::rend (STL/CLR)](#rend)|Určuje konec reverzní kontrolované sekvence.|
|[map::size (STL/CLR)](#size)|Spočítá počet prvků.|
|[map::swap (STL/CLR)](#swap)|Zamění obsah dvou kontejnerů.|
|[map::to_array (STL/CLR)](#to_array)|Zkopíruje řízenou sekvenci do nového pole.|
|[map::upper_bound (STL/CLR)](#upper_bound)|Najde konec rozsahu, který odpovídá zadanému klíči.|
|[map::value_comp (STL/CLR)](#value_comp)|Zkopíruje delegáta řazení pro dvě hodnoty elementu.|

|Operátor|Popis|
|--------------|-----------------|
|[map::operator= (STL/CLR)](#op_as)|Nahradí řízenou sekvenci.|
|[map::operator(STL/CLR)](#op)|Mapuje klíč na jeho přidruženou mapovanou hodnotu.|
|[operator!= (map) (STL/CLR)](#op_neq)|Určuje, zda `map` objekt není roven jinému objektu `map`.|
|[operator< (map) (STL/CLR)](#op_lt)|Určuje, zda je objekt `map` menší než jiný objekt `map`.|
|[operator<= (map) (STL/CLR)](#op_lteq)|Určuje, zda je objekt `map` menší nebo roven jinému objektu `map`.|
|[operator== (map) (STL/CLR)](#op_eq)|Určuje, zda je objekt `map` roven jinému objektu `map`.|
|[operator> (map) (STL/CLR)](#op_gt)|Určuje, zda je objekt `map` větší než jiný objekt `map`.|
|[operator>= (map) (STL/CLR)](#op_gteq)|Určuje, zda je objekt `map` větší nebo roven jinému objektu `map`.|

## <a name="interfaces"></a>Rozhraní

|Rozhraní|Popis|
|---------------|-----------------|
|<xref:System.ICloneable>|Duplikuje objekt.|
|<xref:System.Collections.IEnumerable>|Sekvence prostřednictvím prvků.|
|<xref:System.Collections.ICollection>|Udržovat skupinu prvků.|
|<xref:System.Collections.Generic.IEnumerable%601>|Sekvence prostřednictvím typových elementů.|
|<xref:System.Collections.Generic.ICollection%601>|Udržovat skupinu typových elementů.|
|<xref:System.Collections.Generic.IDictionary%602>|Udržuje skupinu dvojic {Key, Value}.|
|ITree < klíč, hodnota >|Udržujte obecný kontejner.|

## <a name="remarks"></a>Poznámky

Objekt přiděluje a uvolňuje úložiště pro sekvenci, která ovládá jako jednotlivé uzly. Vloží prvky do (skoro) vyvážené stromové struktury, které jsou uspořádány pomocí změny propojení mezi uzly, nikdy kopírováním obsahu jednoho uzlu do druhého. To znamená, že můžete vkládat a odebírat prvky volně bez narušování zbývajících prvků.

Objekt seřadí sekvenci, kterou ovládá, voláním uloženého objektu delegáta typu [map:: key_compare (STL/CLR)](../dotnet/map-key-compare-stl-clr.md). Uložený objekt delegáta lze zadat při vytváření mapy. Pokud nezadáte žádný delegovaný objekt, výchozí hodnota je porovnávání `operator<(key_type, key_type)`. K tomuto uloženému objektu přistupujete voláním funkce mapa členské funkce [:: key_comp (STL/CLR)](../dotnet/map-key-comp-stl-clr.md)`()`.

Takový objekt delegáta musí mít přísně slabé řazení klíčů typu [map:: key_type (STL/CLR)](../dotnet/map-key-type-stl-clr.md). To znamená, že pro všechny dva klíče `X` a `Y`:

`key_comp()(X, Y)` vrací stejný logický výsledek při každém volání.

Pokud má `key_comp()(X, Y)` hodnotu true, `key_comp()(Y, X)` musí mít hodnotu false.

Pokud má `key_comp()(X, Y)` hodnotu true, `X` se říká, že se má seřadit před `Y`.

Pokud má `!key_comp()(X, Y) && !key_comp()(Y, X)` hodnotu true, pak `X` a `Y` se říká, že mají ekvivalentní řazení.

U všech prvků `X`, které předcházejí `Y` v řízené sekvenci, `key_comp()(Y, X)` má hodnotu false. (Pro výchozí objekt delegáta klíče nikdy nesnižují hodnotu.) Na rozdíl od [mapy](../dotnet/map-stl-clr.md)třídy šablony, objekt `map` třídy šablony nevyžaduje, aby klíče pro všechny elementy byly jedinečné. (Dva nebo více klíčů může mít ekvivalentní řazení.)

Každý prvek obsahuje samostatný klíč a namapovanou hodnotu. Sekvence je reprezentována způsobem, který umožňuje vyhledávání, vkládání a odebírání libovolného prvku s řadou operací, které jsou úměrné logaritmu počtu prvků v sekvenci (logaritmický čas). Vkládání prvků navíc nezruší platnost žádných iterátorů a odstranění prvku zruší platnost pouze těch iterátorů, které odkazují na odstraněný prvek.

Mapa podporuje obousměrné iterátory, což znamená, že můžete krokovat s sousedícími prvky daným iterátorem, který určuje prvek v řízené sekvenci. Speciální hlavní uzel odpovídá iterátoru vrácenému funkcí [map:: end (STL/CLR)](../dotnet/map-end-stl-clr.md)`()`. Tento iterátor můžete snížit tak, aby se dosáhlo posledního prvku v řízené sekvenci, pokud je k dispozici. Můžete zvýšit iterátor mapy tak, aby se dosáhlo hlavního uzlu, a pak bude porovnán se `end()`. Nemůžete ale odkázat na iterátor vrácený `end()`.

Všimněte si, že nemůžete odkazovat na prvek mapy přímo podle jeho číselné pozice – to vyžaduje iterátor náhodného přístupu.

Iterátor mapování ukládá popisovač do přidruženého uzlu map, který zase ukládá popisovač do přidruženého kontejneru. Iterátory lze použít pouze u jejich přidružených objektů kontejneru. Iterátor mapy zůstává platný, pokud je jeho přidružený uzel mapy spojen s určitou mapou. Kromě toho je možné, že platný iterátor je deodkazování – můžete ho použít pro přístup k hodnotě prvku, kterou Určuje, a k její změně, pokud to není rovno `end()`.

Při mazání nebo odebírání elementu se volá destruktor pro jeho uloženou hodnotu. Zničení kontejneru smaže všechny prvky. Proto kontejner, jehož typ elementu je ref class, zajistí, že kontejner neobsahuje žádné prvky. Upozorňujeme však, že kontejner popisovačů *nezničí své* prvky.

## <a name="members"></a>Členové

## <a name="mapbegin-stlclr"></a><a name="begin"></a>map:: begin (STL/CLR)

Určuje začátek řízené sekvence.

### <a name="syntax"></a>Syntaxe

```cpp
iterator begin();
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí obousměrný iterátor, který určuje první prvek řízené sekvence nebo těsně za konec prázdné sekvence. Použijete ho k získání iterátoru, který určuje `current` začátek řízené sekvence, ale jeho stav se může změnit, pokud se změní délka kontrolované sekvence.

### <a name="example"></a>Příklad

```cpp
// cliext_map_begin.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // inspect first two items
    Mymap::iterator it = c1.begin();
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

## <a name="mapclear-stlclr"></a><a name="clear"></a>map:: Clear (STL/CLR)

Odebere všechny prvky.

### <a name="syntax"></a>Syntaxe

```cpp
void clear();
```

### <a name="remarks"></a>Poznámky

Členská funkce efektivně volá [map:: Erase (STL/CLR)](../dotnet/map-erase-stl-clr.md)`(` [map:: begin (STL/CLR)](../dotnet/map-begin-stl-clr.md)`(),` [map:: end (STL/CLR)](../dotnet/map-end-stl-clr.md)`())`. Použijete ho k zajištění, aby řízená sekvence byla prázdná.

### <a name="example"></a>Příklad

```cpp
// cliext_map_clear.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // clear the container and reinspect
    c1.clear();
    System::Console::WriteLine("size() = {0}", c1.size());

    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));

    // display contents " [a 1] [b 2]"
    for each (Mymap::value_type elem in c1)
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

## <a name="mapconst_iterator-stlclr"></a><a name="const_iterator"></a>map:: const_iterator (STL/CLR)

Typ konstantního iterátoru řízené sekvence

### <a name="syntax"></a>Syntaxe

```cpp
typedef T2 const_iterator;
```

### <a name="remarks"></a>Poznámky

Typ popisuje objekt nespecifikovaného typu `T2`, který může sloužit jako konstantní obousměrný iterátor pro řízenou sekvenci.

### <a name="example"></a>Příklad

```cpp
// cliext_map_const_iterator.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    Mymap::const_iterator cit = c1.begin();
    for (; cit != c1.end(); ++cit)
        System::Console::Write("[{0} {1}] ", cit->first, cit->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
```

## <a name="mapconst_reference-stlclr"></a><a name="const_reference"></a>map:: const_reference (STL/CLR)

Typ konstantního odkazu na prvek

### <a name="syntax"></a>Syntaxe

```cpp
typedef value_type% const_reference;
```

### <a name="remarks"></a>Poznámky

Typ popisuje konstantní odkaz na prvek.

### <a name="example"></a>Příklad

```cpp
// cliext_map_const_reference.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    Mymap::const_iterator cit = c1.begin();
    for (; cit != c1.end(); ++cit)
        {   // get a const reference to an element
        Mymap::const_reference cref = *cit;
        System::Console::Write("[{0} {1}] ", cref->first, cref->second);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
```

## <a name="mapconst_reverse_iterator-stlclr"></a><a name="const_reverse_iterator"></a>map:: const_reverse_iterator (STL/CLR)

Typ konstantního reverzního iterátoru řízené sekvence.

### <a name="syntax"></a>Syntaxe

```cpp
typedef T4 const_reverse_iterator;
```

### <a name="remarks"></a>Poznámky

Typ popisuje objekt nespecifikovaného typu `T4`, který může sloužit jako konstantní reverzní iterátor pro řízenou sekvenci.

### <a name="example"></a>Příklad

```cpp
// cliext_map_const_reverse_iterator.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]" reversed
    Mymap::const_reverse_iterator crit = c1.rbegin();
    for (; crit != c1.rend(); ++crit)
        System::Console::Write("[{0} {1}] ", crit->first, crit->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[c 3] [b 2] [a 1]
```

## <a name="mapcount-stlclr"></a><a name="count"></a>map:: Count (STL/CLR)

Zjistí počet prvků odpovídající zadanému klíči.

### <a name="syntax"></a>Syntaxe

```cpp
size_type count(key_type key);
```

#### <a name="parameters"></a>Parametry

*key*<br/>
Hodnota klíče, která se má vyhledat

### <a name="remarks"></a>Poznámky

Členská funkce vrátí počet prvků v řízené sekvenci, které mají ekvivalentní řazení s *klíčem*. Použijete ji k určení počtu prvků, které jsou aktuálně v řízené sekvenci, které odpovídají zadanému klíči.

### <a name="example"></a>Příklad

```cpp
// cliext_map_count.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
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

## <a name="mapdifference_type-stlclr"></a><a name="difference_type"></a>map::d ifference_type (STL/CLR)

Typy podepsané vzdálenosti mezi dvěma prvky.

### <a name="syntax"></a>Syntaxe

```cpp
typedef int difference_type;
```

### <a name="remarks"></a>Poznámky

Typ popisuje pravděpodobně negativní počet prvků.

### <a name="example"></a>Příklad

```cpp
// cliext_map_difference_type.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // compute positive difference
    Mymap::difference_type diff = 0;
    for (Mymap::iterator it = c1.begin(); it != c1.end(); ++it)
        ++diff;
    System::Console::WriteLine("end()-begin() = {0}", diff);

    // compute negative difference
    diff = 0;
    for (Mymap::iterator it = c1.end(); it != c1.begin(); --it)
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

## <a name="mapempty-stlclr"></a><a name="empty"></a>map:: Empty (STL/CLR)

Zkouší, zda nejsou přítomny žádné prvky.

### <a name="syntax"></a>Syntaxe

```cpp
bool empty();
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí hodnotu true pro prázdnou řízenou sekvenci. Je ekvivalentní k [mapě:: Size (STL/CLR)](../dotnet/map-size-stl-clr.md)`() == 0`. Použijete ho k otestování, jestli je mapa prázdná.

### <a name="example"></a>Příklad

```cpp
// cliext_map_empty.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
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

## <a name="mapend-stlclr"></a><a name="end"></a>map:: end (STL/CLR)

Určuje konec řízené sekvence.

### <a name="syntax"></a>Syntaxe

```cpp
iterator end();
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí obousměrný iterátor, který odkazuje hned za konec řízené sekvence. Použijete ho k získání iterátoru, který označuje konec řízené sekvence. jeho stav se nemění, pokud se změní délka kontrolované sekvence.

### <a name="example"></a>Příklad

```cpp
// cliext_map_end.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // inspect last two items
    Mymap::iterator it = c1.end();
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

## <a name="mapequal_range-stlclr"></a><a name="equal_range"></a>map:: equal_range (STL/CLR)

Najde rozsah, který odpovídá zadanému klíči.

### <a name="syntax"></a>Syntaxe

```cpp
cliext::pair<iterator, iterator> equal_range(key_type key);
```

#### <a name="parameters"></a>Parametry

*key*<br/>
Hodnota klíče, která se má vyhledat

### <a name="remarks"></a>Poznámky

Členská funkce vrací dvojici iterátorů `cliext::pair<iterator, iterator>(` [map:: lower_bound (STL/CLR)](../dotnet/map-lower-bound-stl-clr.md)`(key),` [map:: Upper_bound (STL/CLR)](../dotnet/map-upper-bound-stl-clr.md)`(key))`. Použijete ji k určení rozsahu prvků, které jsou aktuálně v řízené sekvenci, která odpovídá zadanému klíči.

### <a name="example"></a>Příklad

```cpp
// cliext_map_equal_range.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
typedef Mymap::pair_iter_iter Pairii;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
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

## <a name="maperase-stlclr"></a><a name="erase"></a>map:: Erase (STL/CLR)

Odebere prvky v určených pozicích.

### <a name="syntax"></a>Syntaxe

```cpp
iterator erase(iterator where);
iterator erase(iterator first, iterator last);
bool erase(key_type key)
```

#### <a name="parameters"></a>Parametry

*první*<br/>
Začátek rozsahu, který se má vymazat

*key*<br/>
Hodnota klíče, která se má vymazat

*posledního*<br/>
Konec rozsahu, který se má vymazat

*,*<br/>
Prvek k vymazání.

### <a name="remarks"></a>Poznámky

První členská funkce odstraní prvek řízené sekvence, na kterou ukazuje, *kde*a vrátí iterátor, který určí první prvek zbývající za odebraný element nebo [map:: end (STL/CLR)](../dotnet/map-end-stl-clr.md)`()`, pokud žádný takový prvek neexistuje. Použijete ho k odebrání jednoho elementu.

Druhá členská funkce odstraní prvky kontrolované sekvence v rozsahu [`first`, `last`) a vrátí iterátor, který určí první prvek zbývající za odebranými prvky, nebo `end()`, pokud žádný takový prvek neexistuje.. Použijete ho k odebrání nuly nebo více souvislých prvků.

Třetí členská funkce odebere všechny prvky kontrolované sekvence, jejichž klíč má ekvivalentní řazení *klíče*, a vrátí počet odebraných prvků. Použijete ho k odebrání a počítání všech prvků, které odpovídají zadanému klíči.

Každé mazání elementu trvá čas úměrný logaritmu počtu prvků v řízené sekvenci.

### <a name="example"></a>Příklad

```cpp
// cliext_map_erase.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    cliext::map<wchar_t, int> c1;
    c1.insert(cliext::map<wchar_t, int>::make_value(L'a', 1));
    c1.insert(cliext::map<wchar_t, int>::make_value(L'b', 2));
    c1.insert(cliext::map<wchar_t, int>::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (cliext::map<wchar_t, int>::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // erase an element and reinspect
    cliext::map<wchar_t, int>::iterator it =
        c1.erase(c1.begin());
    System::Console::WriteLine("erase(begin()) = [{0} {1}]",
        it->first, it->second);

    // add elements and display " b c d e"
    c1.insert(cliext::map<wchar_t, int>::make_value(L'd', 4));
    c1.insert(cliext::map<wchar_t, int>::make_value(L'e', 5));
    for each (cliext::map<wchar_t, int>::value_type elem in c1)
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

## <a name="mapfind-stlclr"></a><a name="find"></a>map:: Find (STL/CLR)

Vyhledá prvek, který odpovídá zadanému klíči.

### <a name="syntax"></a>Syntaxe

```cpp
iterator find(key_type key);
```

#### <a name="parameters"></a>Parametry

*key*<br/>
Hodnota klíče, která se má vyhledat

### <a name="remarks"></a>Poznámky

Pokud alespoň jeden prvek kontrolované sekvence má ekvivalentní řazení s *klíčem*, vrátí členská funkce iterátor s označením jednoho z těchto elementů. v opačném případě vrací`()`[map:: end (STL/CLR)](../dotnet/map-end-stl-clr.md) . Použijete ji k vyhledání prvku, který je aktuálně v řízené sekvenci, která odpovídá zadanému klíči.

### <a name="example"></a>Příklad

```cpp
// cliext_map_find.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    System::Console::WriteLine("find {0} = {1}",
        L'A', c1.find(L'A') != c1.end());

    Mymap::iterator it = c1.find(L'b');
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

## <a name="mapgeneric_container-stlclr"></a><a name="generic_container"></a>map:: generic_container (STL/CLR)

Typ obecného rozhraní pro kontejner.

### <a name="syntax"></a>Syntaxe

```cpp
typedef Microsoft::VisualC::StlClr::
    ITree<GKey, GValue>
    generic_container;
```

### <a name="remarks"></a>Poznámky

Typ popisuje obecné rozhraní pro tuto třídu kontejneru šablony.

### <a name="example"></a>Příklad

```cpp
// cliext_map_generic_container.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct a generic container
    Mymap::generic_container^ gc1 = %c1;
    for each (Mymap::value_type elem in gc1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // modify generic and display original
    gc1->insert(Mymap::make_value(L'd', 4));
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // modify original and display generic
    c1.insert(Mymap::make_value(L'e', 5));
    for each (Mymap::value_type elem in gc1)
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

## <a name="mapgeneric_iterator-stlclr"></a><a name="generic_iterator"></a>map:: generic_iterator (STL/CLR)

Typ iterátoru pro použití s obecným rozhraním pro kontejner.

### <a name="syntax"></a>Syntaxe

```cpp
typedef Microsoft::VisualC::StlClr::Generic::
    ContainerBidirectionalIterator<generic_value>
    generic_iterator;
```

### <a name="remarks"></a>Poznámky

Typ popisuje obecný iterátor, který lze použít s obecným rozhraním pro tuto třídu kontejneru šablony.

### <a name="example"></a>Příklad

```cpp
// cliext_map_generic_iterator.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct a generic container
    Mymap::generic_container^ gc1 = %c1;
    for each (Mymap::value_type elem in gc1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // get an element and display it
    Mymap::generic_iterator gcit = gc1->begin();
    Mymap::generic_value gcval = *gcit;
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

## <a name="mapgeneric_reverse_iterator-stlclr"></a><a name="generic_reverse_iterator"></a>map:: generic_reverse_iterator (STL/CLR)

Typ reverzního iterátoru pro použití s obecným rozhraním pro kontejner.

### <a name="syntax"></a>Syntaxe

```cpp
typedef Microsoft::VisualC::StlClr::Generic::
    ReverseRandomAccessIterator<generic_value>
    generic_reverse_iterator;
```

### <a name="remarks"></a>Poznámky

Typ popisuje obecný reverzní iterátor, který lze použít s obecným rozhraním pro tuto třídu kontejneru šablony.

### <a name="example"></a>Příklad

```cpp
// cliext_map_generic_reverse_iterator.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct a generic container
    Mymap::generic_container^ gc1 = %c1;
    for each (Mymap::value_type elem in gc1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // get an element and display it
    Mymap::generic_reverse_iterator gcit = gc1->rbegin();
    Mymap::generic_value gcval = *gcit;
    System::Console::WriteLine("[{0} {1}] ", gcval->first, gcval->second);
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
[a 1] [b 2] [c 3]
[c 3]
```

## <a name="mapgeneric_value-stlclr"></a><a name="generic_value"></a>map:: generic_value (STL/CLR)

Typ elementu pro použití s obecným rozhraním pro kontejner.

### <a name="syntax"></a>Syntaxe

```cpp
typedef GValue generic_value;
```

### <a name="remarks"></a>Poznámky

Typ popisuje objekt typu `GValue`, který popisuje hodnotu uloženého elementu pro použití s obecným rozhraním pro tuto třídu kontejneru šablony.

### <a name="example"></a>Příklad

```cpp
// cliext_map_generic_value.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct a generic container
    Mymap::generic_container^ gc1 = %c1;
    for each (Mymap::value_type elem in gc1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // get an element and display it
    Mymap::generic_iterator gcit = gc1->begin();
    Mymap::generic_value gcval = *gcit;
    System::Console::WriteLine("[{0} {1}] ", gcval->first, gcval->second);
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
[a 1] [b 2] [c 3]
[a 1]
```

## <a name="mapinsert-stlclr"></a><a name="insert"></a>map:: Insert (STL/CLR)

Přidá prvky.

### <a name="syntax"></a>Syntaxe

```cpp
cliext::pair<iterator, bool> insert(value_type val);
iterator insert(iterator where, value_type val);
template<typename InIter>
    void insert(InIter first, InIter last);
void insert(System::Collections::Generic::IEnumerable<value_type>^ right);
```

#### <a name="parameters"></a>Parametry

*první*<br/>
Začátek rozsahu, který se má vložit

*posledního*<br/>
Konec rozsahu, který má být vložen.

*Kliknutím*<br/>
Výčet pro vložení.

*počítává*<br/>
Hodnota klíče, která se má vložit

*,*<br/>
Kam umístit do kontejneru (jenom Nápověda)

### <a name="remarks"></a>Poznámky

Každá z členských funkcí vloží sekvenci určenou zbývajícími operandy.

První členská funkce budoucna pro vložení elementu s hodnotou *Val*a vrátí dvojici hodnot `X`. Pokud `X.second` má hodnotu true, `X.first` označí nově vložený element; jinak `X.first` určí element s ekvivalentním řazením, které již existuje, a žádný nový prvek není vložen. Použijete ho k vložení jediného elementu.

Druhá členská funkce vloží element s hodnotou *Val*, pomocí *WHERE* jako pomocný parametr (pro zlepšení výkonu) a vrátí iterátor, který určí nově vložený element. Použijete ho k vložení jednoho prvku, který může být sousedící s prvkem, který znáte.

Třetí členská funkce vloží sekvenci [`first`, `last`). Použijete ho k vložení nula nebo více prvků zkopírovaných z jiné sekvence.

Čtvrtá členská funkce vloží sekvenci určenou *vpravo*. Použijete ho k vložení sekvence popsané enumerátorem.

Každé vložení elementu trvá čas úměrný logaritmu počtu prvků v řízené sekvenci. Vložení se může objevit v čase konstantního času, avšak s použitím pomocného parametru, který určuje prvek sousedící s bodem vložení.

### <a name="example"></a>Příklad

```cpp
// cliext_map_insert.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
typedef Mymap::pair_iter_bool Pairib;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // insert a single value, unique and duplicate
// insert a single value, success and failure
    Pairib pair1 = c1.insert(Mymap::make_value(L'x', 24));
    System::Console::WriteLine("insert([L'x' 24]) = [[{0} {1}] {2}]",
        pair1.first->first, pair1.first->second, pair1.second);

    pair1 = c1.insert(Mymap::make_value(L'b', 2));
    System::Console::WriteLine("insert([L'b' 2]) = [[{0} {1}] {2}]",
        pair1.first->first, pair1.first->second, pair1.second);

    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // insert a single value with hint
    Mymap::iterator it =
        c1.insert(c1.begin(), Mymap::make_value(L'y', 25));
    System::Console::WriteLine("insert(begin(), [L'y' 25]) = [{0} {1}]",
        it->first, it->second);
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // insert an iterator range
    Mymap c2;
    it = c1.end();
    c2.insert(c1.begin(), --it);
    for each (Mymap::value_type elem in c2)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // insert an enumeration
    Mymap c3;
    c3.insert(   // NOTE: cast is not needed
        (System::Collections::Generic::
            IEnumerable<Mymap::value_type>^)%c1);
    for each (Mymap::value_type elem in c3)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
insert([L'x' 24]) = [[x 24] True]
insert([L'b' 2]) = [[b 2] False]
[a 1] [b 2] [c 3] [x 24]
insert(begin(), [L'y' 25]) = [y 25]
[a 1] [b 2] [c 3] [x 24] [y 25]
[a 1] [b 2] [c 3] [x 24]
[a 1] [b 2] [c 3] [x 24] [y 25]
```

## <a name="mapiterator-stlclr"></a><a name="iterator"></a>map:: iterátor (STL/CLR)

Typ iterátoru řízené sekvence

### <a name="syntax"></a>Syntaxe

```cpp
typedef T1 iterator;
```

### <a name="remarks"></a>Poznámky

Typ popisuje objekt nespecifikovaného typu `T1`, který může sloužit jako obousměrný iterátor pro řízenou sekvenci.

### <a name="example"></a>Příklad

```cpp
// cliext_map_iterator.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    Mymap::iterator it = c1.begin();
    for (; it != c1.end(); ++it)
        System::Console::Write("[{0} {1}] ", it->first, it->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
```

## <a name="mapkey_comp-stlclr"></a><a name="key_comp"></a>map:: key_comp (STL/CLR)

Zkopíruje delegáta řazení dvou klíčů.

### <a name="syntax"></a>Syntaxe

```cpp
key_compare^key_comp();
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí delegáta řazení, který se používá k seřazení řízené sekvence. Použijete ho k porovnání dvou klíčů.

### <a name="example"></a>Příklad

```cpp
// cliext_map_key_comp.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    Mymap::key_compare^ kcomp = c1.key_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        kcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        kcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        kcomp(L'b', L'a'));
    System::Console::WriteLine();

    // test a different ordering rule
    Mymap c2 = cliext::greater<wchar_t>();
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

## <a name="mapkey_compare-stlclr"></a><a name="key_compare"></a>map:: key_compare (STL/CLR)

Delegát řazení pro dva klíče.

### <a name="syntax"></a>Syntaxe

```cpp
Microsoft::VisualC::StlClr::BinaryDelegate<GKey, GKey, bool>
    key_compare;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro delegáta, který určuje pořadí jeho klíčových argumentů.

### <a name="example"></a>Příklad

```cpp
// cliext_map_key_compare.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    Mymap::key_compare^ kcomp = c1.key_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        kcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        kcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        kcomp(L'b', L'a'));
    System::Console::WriteLine();

    // test a different ordering rule
    Mymap c2 = cliext::greater<wchar_t>();
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

## <a name="mapkey_type-stlclr"></a><a name="key_type"></a>map:: key_type (STL/CLR)

Typ klíče řazení

### <a name="syntax"></a>Syntaxe

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro *klíč*parametru šablony.

### <a name="example"></a>Příklad

```cpp
// cliext_map_key_type.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]" using key_type
    for (Mymap::iterator it = c1.begin(); it != c1.end(); ++it)
        {   // store element in key_type object
        Mymap::key_type val = it->first;

        System::Console::Write("{0} ", val);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="maplower_bound-stlclr"></a><a name="lower_bound"></a>map:: lower_bound (STL/CLR)

Vyhledá začátek rozsahu, který odpovídá zadanému klíči.

### <a name="syntax"></a>Syntaxe

```cpp
iterator lower_bound(key_type key);
```

#### <a name="parameters"></a>Parametry

*key*<br/>
Hodnota klíče, která se má vyhledat

### <a name="remarks"></a>Poznámky

Členská funkce určuje první prvek `X` v řízené sekvenci, která má ekvivalentní řazení *klíče*. Pokud žádný takový prvek neexistuje, vrátí [map:: end (STL/CLR)](../dotnet/map-end-stl-clr.md)`()`; v opačném případě vrátí iterátor, který určí `X`. Použijete ji k vyhledání začátku sekvence prvků, které jsou aktuálně v řízené sekvenci, která odpovídá zadanému klíči.

### <a name="example"></a>Příklad

```cpp
// cliext_map_lower_bound.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    System::Console::WriteLine("lower_bound(L'x')==end() = {0}",
        c1.lower_bound(L'x') == c1.end());

    Mymap::iterator it = c1.lower_bound(L'a');
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

## <a name="mapmake_value-stlclr"></a><a name="make_value"></a>map:: make_value (STL/CLR)

Vytvoří objekt hodnoty.

### <a name="syntax"></a>Syntaxe

```cpp
static value_type make_value(key_type key, mapped_type mapped);
```

#### <a name="parameters"></a>Parametry

*key*<br/>
Hodnota klíče, která se má použít

*mapovaný*<br/>
Namapovaná hodnota, která se má vyhledat

### <a name="remarks"></a>Poznámky

Členská funkce vrátí objekt `value_type`, jehož klíč je *klíč* , a jehož mapovaná hodnota je *namapovaná*. Použijete ho k vytvoření objektu vhodného pro použití s několika dalšími členskými funkcemi.

### <a name="example"></a>Příklad

```cpp
// cliext_map_make_value.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
```

## <a name="mapmap-stlclr"></a><a name="map"></a>map:: map (STL/CLR)

Sestaví objekt kontejneru.

### <a name="syntax"></a>Syntaxe

```cpp
map();
explicit map(key_compare^ pred);
map(map<Key, Mapped>% right);
map(map<Key, Mapped>^ right);
template<typename InIter>
    mapmap(InIter first, InIter last);
template<typename InIter>
    map(InIter first, InIter last,
        key_compare^ pred);
map(System::Collections::Generic::IEnumerable<GValue>^ right);
map(System::Collections::Generic::IEnumerable<GValue>^ right,
    key_compare^ pred);
```

#### <a name="parameters"></a>Parametry

*první*<br/>
Začátek rozsahu, který se má vložit

*posledního*<br/>
Konec rozsahu, který má být vložen.

*čekání*<br/>
Predikát řazení pro řízenou sekvenci.

*Kliknutím*<br/>
Objekt nebo rozsah, který chcete vložit.

### <a name="remarks"></a>Poznámky

Konstruktor:

`map();`

Inicializuje řízenou sekvenci bez elementů s výchozím predikátem řazení `key_compare()`. Použijete ji k zadání prázdné počáteční řízené sekvence s výchozím predikátem řazení.

Konstruktor:

`explicit map(key_compare^ pred);`

Inicializuje řízená sekvence bez elementů s predikátem řazení *před*. Použijete ji k zadání prázdné počáteční řízené sekvence se zadaným predikátem řazení.

Konstruktor:

`map(map<Key, Mapped>% right);`

Inicializuje řízenou sekvenci pomocí sekvence [`right.begin()`, `right.end()`) s výchozím predikátem řazení. Použijete ji k určení počáteční řízené sekvence, která je kopií sekvence řízené objektem map *vpravo*s výchozím predikátem řazení.

Konstruktor:

`map(map<Key, Mapped>^ right);`

Inicializuje řízenou sekvenci pomocí sekvence [`right->begin()`, `right->end()`) s výchozím predikátem řazení. Použijete ji k určení počáteční řízené sekvence, která je kopií sekvence řízené objektem map *vpravo*s výchozím predikátem řazení.

Konstruktor:

`template<typename InIter> map(InIter first, InIter last);`

Inicializuje řízenou sekvenci pomocí sekvence [`first`, `last`) s výchozím predikátem řazení. Použijete ji k tomu, aby řízená sekvence zkopírovala jinou sekvenci s výchozím predikátem řazení.

Konstruktor:

`template<typename InIter> map(InIter first, InIter last, key_compare^ pred);`

Inicializuje řízenou sekvenci pomocí sekvence [`first`, `last`) s predikátem řazení *před*. Použijete ji k tomu, aby řízená sekvence zkopírovala jinou sekvenci se zadaným predikátem řazení.

Konstruktor:

`map(System::Collections::Generic::IEnumerable<Key>^ right);`

Inicializuje řízenou sekvenci sekvencí, která je určena *přípravou*, s výchozím predikátem řazení. Použijete ho k tomu, aby řízená sekvence zkopírovala jinou sekvenci popsanou enumerátorem s výchozím predikátem řazení.

Konstruktor:

`map(System::Collections::Generic::IEnumerable<Key>^ right, key_compare^ pred);`

Inicializuje řízená sekvence sekvencí, která je určena *přípravou*, s predikátem řazení *před*. Použijete ho k tomu, aby řízená sekvence zkopírovala jinou sekvenci popsanou enumerátorem, se zadaným predikátem řazení.

### <a name="example"></a>Příklad

```cpp
// cliext_map_construct.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
// construct an empty container
    Mymap c1;
    System::Console::WriteLine("size() = {0}", c1.size());

    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct with an ordering rule
    Mymap c2 = cliext::greater_equal<wchar_t>();
    System::Console::WriteLine("size() = {0}", c2.size());

    c2.insert(c1.begin(), c1.end());
    for each (Mymap::value_type elem in c2)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct with an iterator range
    Mymap c3(c1.begin(), c1.end());
    for each (Mymap::value_type elem in c3)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct with an iterator range and an ordering rule
    Mymap c4(c1.begin(), c1.end(),
        cliext::greater_equal<wchar_t>());
    for each (Mymap::value_type elem in c4)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct with an enumeration
    Mymap c5(   // NOTE: cast is not needed
        (System::Collections::Generic::IEnumerable<
            Mymap::value_type>^)%c3);
    for each (Mymap::value_type elem in c5)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct with an enumeration and an ordering rule
    Mymap c6(   // NOTE: cast is not needed
        (System::Collections::Generic::IEnumerable<
            Mymap::value_type>^)%c3,
                cliext::greater_equal<wchar_t>());
    for each (Mymap::value_type elem in c6)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct by copying another container
    Mymap c7(c4);
    for each (Mymap::value_type elem in c7)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct by copying a container handle
    Mymap c8(%c3);
    for each (Mymap::value_type elem in c8)
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

## <a name="mapmapped_type-stlclr"></a><a name="mapped_type"></a>map:: mapped_type (STL/CLR)

Typ mapované hodnoty přiřazené ke každému klíči

### <a name="syntax"></a>Syntaxe

```cpp
typedef Mapped mapped_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro *mapovaný*parametr šablony.

### <a name="example"></a>Příklad

```cpp
// cliext_map_mapped_type.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]" using mapped_type
    for (Mymap::iterator it = c1.begin(); it != c1.end(); ++it)
        {   // store element in mapped_type object
        Mymap::mapped_type val = it->second;

        System::Console::Write("{0} ", val);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
1 2 3
```

## <a name="mapoperator-stlclr"></a><a name="op_as"></a>map:: operator = (STL/CLR)

Nahradí řízenou sekvenci.

### <a name="syntax"></a>Syntaxe

```cpp
map<Key, Mapped>% operator=(map<Key, Mapped>% right);
```

#### <a name="parameters"></a>Parametry

*Kliknutím*<br/>
Kontejner ke zkopírování.

### <a name="remarks"></a>Poznámky

Operátor členu kopíruje *přímo* na objekt a potom vrátí `*this`. Použijete ji k nahrazení kontrolované sekvence kopií kontrolované sekvence *vpravo*.

### <a name="example"></a>Příklad

```cpp
// cliext_map_operator_as.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // assign to a new container
    Mymap c2;
    c2 = c1;
    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c2)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
[a 1] [b 2] [c 3]
```

## <a name="mapoperatorstlclr"></a><a name="op"></a>map:: – operátor (STL/CLR)

Mapuje klíč na jeho přidruženou mapovanou hodnotu.

### <a name="syntax"></a>Syntaxe

```cpp
mapped_type operator[](key_type key);
```

#### <a name="parameters"></a>Parametry

*key*<br/>
Hodnota klíče, která se má vyhledat

### <a name="remarks"></a>Poznámky

Členské funkce budoucna k nalezení prvku s ekvivalentním řazením *klíče*. Pokud nalezne jednu, vrátí přidruženou mapovanou hodnotu; v opačném případě vloží `value_type(key, mapped_type())` a vrátí přidruženou (výchozí) mapovanou hodnotu. Použijete ji k vyhledání mapované hodnoty, která má přiřazený klíč, nebo k zajištění toho, že pro klíč existuje položka, pokud žádná není nalezena.

### <a name="example"></a>Příklad

```cpp
// cliext_map_operator_sub.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    System::Console::WriteLine("c1[{0}] = {1}",
        L'A', c1[L'A']);
    System::Console::WriteLine("c1[{0}] = {1}",
        L'b', c1[L'b']);

    // redisplay altered contents
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // alter mapped values and redisplay
    c1[L'A'] = 10;
    c1[L'c'] = 13;
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
c1[A] = 0
c1[b] = 2
[A 0] [a 1] [b 2] [c 3]
[A 10] [a 1] [b 2] [c 13]
```

## <a name="maprbegin-stlclr"></a><a name="rbegin"></a>map:: rbegin (STL/CLR)

Určuje začátek obrácené kontrolované sekvence.

### <a name="syntax"></a>Syntaxe

```cpp
reverse_iterator rbegin();
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí reverzní iterátor, který určuje poslední prvek řízené sekvence nebo těsně za začátek prázdné sekvence. Proto určuje `beginning` reverzní sekvence. Použijete ho k získání iterátoru, který určí `current` začátkem kontrolované sekvence v obráceném pořadí, ale jeho stav se může změnit, pokud se změní délka kontrolované sekvence.

### <a name="example"></a>Příklad

```cpp
// cliext_map_rbegin.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // inspect first two items in reversed sequence
    Mymap::reverse_iterator rit = c1.rbegin();
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

## <a name="mapreference-stlclr"></a><a name="reference"></a>map:: Reference (STL/CLR)

Typ odkazu na prvek

### <a name="syntax"></a>Syntaxe

```cpp
typedef value_type% reference;
```

### <a name="remarks"></a>Poznámky

Typ popisuje odkaz na prvek.

### <a name="example"></a>Příklad

```cpp
// cliext_map_reference.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    Mymap::iterator it = c1.begin();
    for (; it != c1.end(); ++it)
        {   // get a reference to an element
        Mymap::reference ref = *it;
        System::Console::Write("[{0} {1}] ", ref->first, ref->second);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
```

## <a name="maprend-stlclr"></a><a name="rend"></a>map:: rend (STL/CLR)

Určuje konec reverzní kontrolované sekvence.

### <a name="syntax"></a>Syntaxe

```cpp
reverse_iterator rend();
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí reverzní iterátor, který odkazuje hned za začátek řízené sekvence. Proto určuje `end` reverzní sekvence. Použijete ho k získání iterátoru, který určuje `current` konec řízené sekvence v obráceném pořadí, ale jeho stav se může změnit, pokud se změní délka kontrolované sekvence.

### <a name="example"></a>Příklad

```cpp
// cliext_map_rend.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // inspect first two items in reversed sequence
    Mymap::reverse_iterator rit = c1.rend();
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

## <a name="mapreverse_iterator-stlclr"></a><a name="reverse_iterator"></a>map:: reverse_iterator (STL/CLR)

Typ reverzního iterátoru řízené sekvence.

### <a name="syntax"></a>Syntaxe

```
typedef T3 reverse_iterator;
```

### <a name="remarks"></a>Poznámky

Typ popisuje objekt nespecifikovaného typu `T3`, který může sloužit jako reverzní iterátor pro řízenou sekvenci.

### <a name="example"></a>Příklad

```cpp
// cliext_map_reverse_iterator.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]" reversed
    Mymap::reverse_iterator rit = c1.rbegin();
    for (; rit != c1.rend(); ++rit)
        System::Console::Write("[{0} {1}] ", rit->first, rit->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[c 3] [b 2] [a 1]
```

## <a name="mapsize-stlclr"></a><a name="size"></a>map:: Size (STL/CLR)

Spočítá počet prvků.

### <a name="syntax"></a>Syntaxe

```cpp
size_type size();
```

### <a name="remarks"></a>Poznámky

Členská funkce vrací délku řízené sekvence. Použijete ji k určení počtu prvků, které jsou aktuálně v řízené sekvenci. Pokud vás zajímá, zda má sekvence nenulovou velikost, přečtěte si téma [map:: Empty (STL/CLR)](../dotnet/map-empty-stl-clr.md)`()`.

### <a name="example"></a>Příklad

```cpp
// cliext_map_size.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // clear the container and reinspect
    c1.clear();
    System::Console::WriteLine("size() = {0} after clearing", c1.size());

    // add elements and clear again
    c1.insert(Mymap::make_value(L'd', 4));
    c1.insert(Mymap::make_value(L'e', 5));
    System::Console::WriteLine("size() = {0} after adding 2", c1.size());
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
size() = 0 after clearing
size() = 2 after adding 2
```

## <a name="mapsize_type-stlclr"></a><a name="size_type"></a>map:: size_type (STL/CLR)

Typ podepsané vzdálenosti mezi dvěma prvky.

### <a name="syntax"></a>Syntaxe

```cpp
typedef int size_type;
```

### <a name="remarks"></a>Poznámky

Typ popisuje nezáporný počet prvků.

### <a name="example"></a>Příklad

```cpp
// cliext_map_size_type.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // compute positive difference
    Mymap::size_type diff = 0;
    for (Mymap::iterator it = c1.begin(); it != c1.end(); ++it)
        ++diff;
    System::Console::WriteLine("end()-begin() = {0}", diff);
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
end()-begin() = 3
```

## <a name="mapswap-stlclr"></a><a name="swap"></a>map:: swap (STL/CLR)

Zamění obsah dvou kontejnerů.

### <a name="syntax"></a>Syntaxe

```cpp
void swap(map<Key, Mapped>% right);
```

#### <a name="parameters"></a>Parametry

*Kliknutím*<br/>
Kontejner pro prohození obsahu pomocí.

### <a name="remarks"></a>Poznámky

Členská funkce přemění kontrolované sekvence mezi `this` a *pravou*. Provede to v konstantním čase a nevyvolává žádné výjimky. Použijete ho jako rychlý způsob, jak vyměňovat obsah dvou kontejnerů.

### <a name="example"></a>Příklad

```cpp
// cliext_map_swap.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct another container with repetition of values
    Mymap c2;
    c2.insert(Mymap::make_value(L'd', 4));
    c2.insert(Mymap::make_value(L'e', 5));
    c2.insert(Mymap::make_value(L'f', 6));
    for each (Mymap::value_type elem in c2)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // swap and redisplay
    c1.swap(c2);
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    for each (Mymap::value_type elem in c2)
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

## <a name="mapto_array-stlclr"></a><a name="to_array"></a>map:: to_array (STL/CLR)

Zkopíruje řízenou sekvenci do nového pole.

### <a name="syntax"></a>Syntaxe

```cpp
cli::array<value_type>^ to_array();
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí pole obsahující řízenou sekvenci. Použijete ho k získání kopie řízené sekvence ve formuláři Array.

### <a name="example"></a>Příklad

```cpp
// cliext_map_to_array.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // copy the container and modify it
    cli::array<Mymap::value_type>^ a1 = c1.to_array();

    c1.insert(Mymap::make_value(L'd', 4));
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // display the earlier array copy
    for each (Mymap::value_type elem in a1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3] [d 4]
[a 1] [b 2] [c 3]
```

## <a name="mapupper_bound-stlclr"></a><a name="upper_bound"></a>map:: upper_bound (STL/CLR)

Najde konec rozsahu, který odpovídá zadanému klíči.

### <a name="syntax"></a>Syntaxe

```cpp
iterator upper_bound(key_type key);
```

#### <a name="parameters"></a>Parametry

*key*<br/>
Hodnota klíče, která se má vyhledat

### <a name="remarks"></a>Poznámky

Členská funkce určuje poslední prvek `X` v řízené sekvenci, která má ekvivalentní řazení *klíče*. Pokud žádný takový prvek neexistuje nebo pokud je `X` posledním prvkem řízené sekvence, vrátí [map:: end (STL/CLR)](../dotnet/map-end-stl-clr.md)`()`; v opačném případě vrátí iterátor, který určí první prvek nad rámec `X`. Použijete ho k vyhledání konce posloupnosti prvků, které jsou aktuálně v řízené sekvenci, která odpovídá zadanému klíči.

### <a name="example"></a>Příklad

```cpp
// cliext_map_upper_bound.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    System::Console::WriteLine("upper_bound(L'x')==end() = {0}",
        c1.upper_bound(L'x') == c1.end());

    Mymap::iterator it = c1.upper_bound(L'a');
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

## <a name="mapvalue_comp-stlclr"></a><a name="value_comp"></a>map:: value_comp (STL/CLR)

Zkopíruje delegáta řazení pro dvě hodnoty elementu.

### <a name="syntax"></a>Syntaxe

```cpp
value_compare^ value_comp();
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí delegáta řazení, který se používá k seřazení řízené sekvence. Použijete ho k porovnání dvou hodnot prvků.

### <a name="example"></a>Příklad

```cpp
// cliext_map_value_comp.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    Mymap::value_compare^ kcomp = c1.value_comp();

    System::Console::WriteLine("compare([L'a', 1], [L'a', 1]) = {0}",
        kcomp(Mymap::make_value(L'a', 1),
            Mymap::make_value(L'a', 1)));
    System::Console::WriteLine("compare([L'a', 1], [L'b', 2]) = {0}",
        kcomp(Mymap::make_value(L'a', 1),
            Mymap::make_value(L'b', 2)));
    System::Console::WriteLine("compare([L'b', 2], [L'a', 1]) = {0}",
        kcomp(Mymap::make_value(L'b', 2),
            Mymap::make_value(L'a', 1)));
    System::Console::WriteLine();
    return (0);
    }
```

```Output
compare([L'a', 1], [L'a', 1]) = False
compare([L'a', 1], [L'b', 2]) = True
compare([L'b', 2], [L'a', 1]) = False
```

## <a name="mapvalue_compare-stlclr"></a><a name="value_compare"></a>map:: value_compare (STL/CLR)

Delegát řazení pro dvě hodnoty elementu.

### <a name="syntax"></a>Syntaxe

```cpp
Microsoft::VisualC::StlClr::BinaryDelegate<generic_value, generic_value, bool>
    value_compare;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro delegáta, který určuje řazení jeho hodnotových argumentů.

### <a name="example"></a>Příklad

```cpp
// cliext_map_value_compare.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    Mymap::value_compare^ kcomp = c1.value_comp();

    System::Console::WriteLine("compare([L'a', 1], [L'a', 1]) = {0}",
        kcomp(Mymap::make_value(L'a', 1),
            Mymap::make_value(L'a', 1)));
    System::Console::WriteLine("compare([L'a', 1], [L'b', 2]) = {0}",
        kcomp(Mymap::make_value(L'a', 1),
            Mymap::make_value(L'b', 2)));
    System::Console::WriteLine("compare([L'b', 2], [L'a', 1]) = {0}",
        kcomp(Mymap::make_value(L'b', 2),
            Mymap::make_value(L'a', 1)));
    System::Console::WriteLine();
    return (0);
    }
```

```Output
compare([L'a', 1], [L'a', 1]) = False
compare([L'a', 1], [L'b', 2]) = True
compare([L'b', 2], [L'a', 1]) = False
```

## <a name="mapvalue_type-stlclr"></a><a name="value_type"></a>map:: value_type (STL/CLR)

Typ prvku

### <a name="syntax"></a>Syntaxe

```cpp
typedef generic_value value_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro `generic_value`.

### <a name="example"></a>Příklad

```cpp
// cliext_map_value_type.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]" using value_type
    for (Mymap::iterator it = c1.begin(); it != c1.end(); ++it)
        {   // store element in value_type object
        Mymap::value_type val = *it;
        System::Console::Write("[{0} {1}] ", val->first, val->second);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
```

## <a name="operator-map-stlclr"></a><a name="op_neq"></a>operator! = (map) – operátor (STL/CLR)

Seznam se neshoduje s porovnáním.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Key,
    typename Mapped>
    bool operator!=(map<Key, Mapped>% left,
        map<Key, Mapped>% right);
```

#### <a name="parameters"></a>Parametry

*zbývá*<br/>
Levý kontejner, který se má porovnat

*Kliknutím*<br/>
Pravý kontejner, který se má porovnat

### <a name="remarks"></a>Poznámky

Funkce operátoru vrací `!(left == right)`. Použijete ho k otestování, jestli *vlevo* není seřazené stejně jako *právo* , pokud jsou tyto dvě mapy porovnány s elementy podle elementu.

### <a name="example"></a>Příklad

```cpp
// cliext_map_operator_ne.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // assign to a new container
    Mymap c2;
    c2.insert(Mymap::make_value(L'a', 1));
    c2.insert(Mymap::make_value(L'b', 2));
    c2.insert(Mymap::make_value(L'd', 4));

    // display contents " [a 1] [b 2] [d 4]"
    for each (Mymap::value_type elem in c2)
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

## <a name="operatorlt-map-stlclr"></a><a name="op_lt"></a>operator&lt; (map) – operátor (STL/CLR)

Seznam je menší než porovnání.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Key,
    typename Mapped>
    bool operator<(map<Key, Mapped>% left,
        map<Key, Mapped>% right);
```

#### <a name="parameters"></a>Parametry

*zbývá*<br/>
Levý kontejner, který se má porovnat

*Kliknutím*<br/>
Pravý kontejner, který se má porovnat

### <a name="remarks"></a>Poznámky

Funkce operator vrátí hodnotu true, pokud `i` nejnižší pozice, pro kterou `!(right[i] < left[i])` je také true `left[i] < right[i]`. V opačném případě vrátí `left->size() < right->size()` použijete k otestování *, zda je* před *pravou* seřazena druhá mapa, pokud jsou obě mapy porovnány elementem.

### <a name="example"></a>Příklad

```cpp
// cliext_map_operator_lt.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // assign to a new container
    Mymap c2;
    c2.insert(Mymap::make_value(L'a', 1));
    c2.insert(Mymap::make_value(L'b', 2));
    c2.insert(Mymap::make_value(L'd', 4));

    // display contents " [a 1] [b 2] [d 4]"
    for each (Mymap::value_type elem in c2)
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

## <a name="operatorlt-map-stlclr"></a><a name="op_lteq"></a>operator&lt;= (map) – operátor (STL/CLR)

Seznam je menší nebo roven hodnotě porovnání.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Key,
    typename Mapped>
    bool operator<=(map<Key, Mapped>% left,
        map<Key, Mapped>% right);
```

#### <a name="parameters"></a>Parametry

*zbývá*<br/>
Levý kontejner, který se má porovnat

*Kliknutím*<br/>
Pravý kontejner, který se má porovnat

### <a name="remarks"></a>Poznámky

Funkce operátoru vrací `!(right < left)`. Použijete ho k otestování *, jestli není* po *pravé straně* , když jsou tyto dvě mapy porovnány s elementy podle elementu, k disobjednávce.

### <a name="example"></a>Příklad

```cpp
// cliext_map_operator_le.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // assign to a new container
    Mymap c2;
    c2.insert(Mymap::make_value(L'a', 1));
    c2.insert(Mymap::make_value(L'b', 2));
    c2.insert(Mymap::make_value(L'd', 4));

    // display contents " [a 1] [b 2] [d 4]"
    for each (Mymap::value_type elem in c2)
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

## <a name="operator-map-stlclr"></a><a name="op_eq"></a>operator = = (map) – operátor (STL/CLR)

Seznam se stejným porovnáním

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Key,
    typename Mapped>
    bool operator==(map<Key, Mapped>% left,
        map<Key, Mapped>% right);
```

#### <a name="parameters"></a>Parametry

*zbývá*<br/>
Levý kontejner, který se má porovnat

*Kliknutím*<br/>
Pravý kontejner, který se má porovnat

### <a name="remarks"></a>Poznámky

Funkce operator vrátí hodnotu true pouze v případě, že sekvence řízené *levou* a *pravou* mají stejnou délku a pro každou pozici `i``left[i] ==` `right[i]`. Použijete ho k otestování, jestli je *levé* *, pokud jsou* tyto dvě mapy porovnány s elementy podle elementu.

### <a name="example"></a>Příklad

```cpp
// cliext_map_operator_eq.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // assign to a new container
    Mymap c2;
    c2.insert(Mymap::make_value(L'a', 1));
    c2.insert(Mymap::make_value(L'b', 2));
    c2.insert(Mymap::make_value(L'd', 4));

    // display contents " [a 1] [b 2] [d 4]"
    for each (Mymap::value_type elem in c2)
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

## <a name="operatorgt-map-stlclr"></a><a name="op_gt"></a>operator&gt; (map) – operátor (STL/CLR)

Seznam je větší než porovnání.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Key,
    typename Mapped>
    bool operator>(map<Key, Mapped>% left,
        map<Key, Mapped>% right);
```

#### <a name="parameters"></a>Parametry

*zbývá*<br/>
Levý kontejner, který se má porovnat

*Kliknutím*<br/>
Pravý kontejner, který se má porovnat

### <a name="remarks"></a>Poznámky

Funkce operator vrací `right` `<` `left`. Použijete ji k otestování, *zda je* po *pravé straně* porovnávána tato dvě mapování na prvky podle prvku.

### <a name="example"></a>Příklad

```cpp
// cliext_map_operator_gt.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // assign to a new container
    Mymap c2;
    c2.insert(Mymap::make_value(L'a', 1));
    c2.insert(Mymap::make_value(L'b', 2));
    c2.insert(Mymap::make_value(L'd', 4));

    // display contents " [a 1] [b 2] [d 4]"
    for each (Mymap::value_type elem in c2)
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

## <a name="operatorgt-map-stlclr"></a><a name="op_gteq"></a>operator&gt;= (map) – operátor (STL/CLR)

Seznam je větší než nebo rovno porovnání.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Key,
    typename Mapped>
    bool operator>=(map<Key, Mapped>% left,
        map<Key, Mapped>% right);
```

#### <a name="parameters"></a>Parametry

*zbývá*<br/>
Levý kontejner, který se má porovnat

*Kliknutím*<br/>
Pravý kontejner, který se má porovnat

### <a name="remarks"></a>Poznámky

Funkce operator vrací `!(left` `<` `right)`. Použijete ji k otestování, zda je *ponechána* před *pravou* , pokud jsou obě mapy porovnány podle elementu.

### <a name="example"></a>Příklad

```cpp
// cliext_map_operator_ge.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // assign to a new container
    Mymap c2;
    c2.insert(Mymap::make_value(L'a', 1));
    c2.insert(Mymap::make_value(L'b', 2));
    c2.insert(Mymap::make_value(L'd', 4));

    // display contents " [a 1] [b 2] [d 4]"
    for each (Mymap::value_type elem in c2)
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
