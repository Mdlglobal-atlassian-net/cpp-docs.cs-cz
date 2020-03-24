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
ms.openlocfilehash: 811b96cca1fbf661def181d16dcb6a02c6c398d8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80208491"
---
# <a name="multiset-stlclr"></a>multiset (STL/CLR)

Třída šablony popisuje objekt, který ovládá proměnlivou délku posloupnosti prvků, které mají obousměrný přístup. Pomocí `multiset` kontejnerů můžete spravovat sekvenci prvků jako (skoro) vyvážený uspořádaný strom uzlů, z nichž každý ukládá jeden element.

V popisu níže je `GValue` stejné jako `GKey`, která je naopak stejná jako *klíč* , pokud se jedná o typ REF, v takovém případě je to `Key^`.

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

*Klíč*<br/>
Typ klíčové součásti prvku v řízené sekvenci.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<cliext –/set >

**Obor názvů:** cliext –

## <a name="declarations"></a>Deklarace

|Definice typu|Popis|
|---------------------|-----------------|
|[multiset::const_iterator (STL/CLR)](#const_iterator)|Typ konstantního iterátoru řízené sekvence|
|[multiset::const_reference (STL/CLR)](#const_reference)|Typ konstantního odkazu na prvek|
|[multiset::const_reverse_iterator (STL/CLR)](#const_reverse_iterator)|Typ konstantního reverzního iterátoru řízené sekvence.|
|[multiset::difference_type (STL/CLR)](#difference_type)|Typ (možná znaménko) vzdálenosti mezi dvěma prvky.|
|[multiset::generic_container (STL/CLR)](#generic_container)|Typ obecného rozhraní pro kontejner.|
|[multiset::generic_iterator (STL/CLR)](#generic_iterator)|Typ iterátoru pro obecné rozhraní kontejneru.|
|[multiset::generic_reverse_iterator (STL/CLR)](#generic_reverse_iterator)|Typ reverzního iterátoru pro obecné rozhraní kontejneru.|
|[multiset::generic_value (STL/CLR)](#generic_value)|Typ elementu pro obecné rozhraní kontejneru.|
|[multiset::iterator (STL/CLR)](#iterator)|Typ iterátoru řízené sekvence|
|[multiset::key_compare (STL/CLR)](#key_compare)|Delegát řazení pro dva klíče.|
|[multiset::key_type (STL/CLR)](#key_type)|Typ klíče řazení|
|[multiset::reference (STL/CLR)](#reference)|Typ odkazu na prvek|
|[multiset::reverse_iterator (STL/CLR)](#reverse_iterator)|Typ reverzního iterátoru řízené sekvence.|
|[multiset::size_type (STL/CLR)](#size_type)|Typ (nezáporné) vzdálenosti mezi dvěma prvky.|
|[multiset::value_compare (STL/CLR)](#value_compare)|Delegát řazení pro dvě hodnoty elementu.|
|[multiset::value_type (STL/CLR)](#value_type)|Typ prvku|

|Členská funkce|Popis|
|---------------------|-----------------|
|[multiset::begin (STL/CLR)](#begin)|Určuje začátek řízené sekvence.|
|[multiset::clear (STL/CLR)](#clear)|Odebere všechny prvky.|
|[multiset::count (STL/CLR)](#count)|Spočítá prvky, které odpovídají zadanému klíči.|
|[multiset::empty (STL/CLR)](#empty)|Zkouší, zda nejsou přítomny žádné prvky.|
|[multiset::end (STL/CLR)](#end)|Určuje konec řízené sekvence.|
|[multiset::equal_range (STL/CLR)](#equal_range)|Najde rozsah, který odpovídá zadanému klíči.|
|[multiset::erase (STL/CLR)](#erase)|Odebere prvky v určených pozicích.|
|[multiset::find (STL/CLR)](#find)|Vyhledá prvek, který odpovídá zadanému klíči.|
|[multiset::insert (STL/CLR)](#insert)|Přidá prvky.|
|[multiset::key_comp (STL/CLR)](#key_comp)|Zkopíruje delegáta řazení dvou klíčů.|
|[multiset::lower_bound (STL/CLR)](#lower_bound)|Vyhledá začátek rozsahu, který odpovídá zadanému klíči.|
|[multiset::make_value (STL/CLR)](#make_value)|Vytvoří objekt hodnoty.|
|[multiset::multiset (STL/CLR)](#multiset)|Sestaví objekt kontejneru.|
|[multiset::rbegin (STL/CLR)](#rbegin)|Určuje začátek obrácené kontrolované sekvence.|
|[multiset::rend (STL/CLR)](#rend)|Určuje konec reverzní kontrolované sekvence.|
|[multiset::size (STL/CLR)](#size)|Spočítá počet prvků.|
|[multiset::swap (STL/CLR)](#swap)|Zamění obsah dvou kontejnerů.|
|[multiset::to_array (STL/CLR)](#to_array)|Zkopíruje řízenou sekvenci do nového pole.|
|[multiset::upper_bound (STL/CLR)](#upper_bound)|Najde konec rozsahu, který odpovídá zadanému klíči.|
|[multiset::value_comp (STL/CLR)](#value_comp)|Zkopíruje delegáta řazení pro dvě hodnoty elementu.|

|Operátor|Popis|
|--------------|-----------------|
|[multiset::operator= (STL/CLR)](#op_as)|Nahradí řízenou sekvenci.|
|[operator!= (multiset) (STL/CLR)](#op_neq)|Určuje, zda `multiset` objekt není roven jinému objektu `multiset`.|
|[operator< (multiset) (STL/CLR)](#op_lt)|Určuje, zda je objekt `multiset` menší než jiný objekt `multiset`.|
|[operator<= (multiset) (STL/CLR)](#op_lteq)|Určuje, zda je objekt `multiset` menší nebo roven jinému objektu `multiset`.|
|[operator== (multiset) (STL/CLR)](#op_eq)|Určuje, zda je objekt `multiset` roven jinému objektu `multiset`.|
|[operator> (multiset) (STL/CLR)](#op_gt)|Určuje, zda je objekt `multiset` větší než jiný objekt `multiset`.|
|[operator>= (multiset) (STL/CLR)](#op_gteq)|Určuje, zda je objekt `multiset` větší nebo roven jinému objektu `multiset`.|

## <a name="interfaces"></a>Rozhraní

|Rozhraní|Popis|
|---------------|-----------------|
|<xref:System.ICloneable>|Duplikuje objekt.|
|<xref:System.Collections.IEnumerable>|Sekvence prostřednictvím prvků.|
|<xref:System.Collections.ICollection>|Udržovat skupinu prvků.|
|<xref:System.Collections.Generic.IEnumerable%601>|Sekvence prostřednictvím typových elementů.|
|<xref:System.Collections.Generic.ICollection%601>|Udržovat skupinu typových elementů.|
|ITree\<klíč, hodnota >|Udržujte obecný kontejner.|

## <a name="remarks"></a>Poznámky

Objekt přiděluje a uvolňuje úložiště pro sekvenci, která ovládá jako jednotlivé uzly. Vloží prvky do (skoro) vyvážené stromové struktury, které jsou uspořádány pomocí změny propojení mezi uzly, nikdy kopírováním obsahu jednoho uzlu do druhého. To znamená, že můžete vkládat a odebírat prvky volně bez narušování zbývajících prvků.

Objekt seřadí sekvenci, kterou ovládá, voláním uloženého objektu delegáta typu [multiset:: key_compare (STL/CLR)](../dotnet/multiset-key-compare-stl-clr.md). Uložený objekt delegáta lze zadat při vytváření multiset; Pokud nezadáte žádný delegovaný objekt, výchozí hodnota je porovnávání `operator<(key_type, key_type)`. K tomuto uloženému objektu přistupujete voláním členské funkce [multiset:: key_comp (STL/CLR)](../dotnet/multiset-key-comp-stl-clr.md)`()`.

Takový objekt delegáta musí mít přísně slabé řazení klíčů typu [multiset:: key_type (STL/CLR)](../dotnet/multiset-key-type-stl-clr.md). To znamená, že pro všechny dva klíče `X` a `Y`:

`key_comp()(X, Y)` vrací stejný logický výsledek při každém volání.

Pokud má `key_comp()(X, Y)` hodnotu true, `key_comp()(Y, X)` musí mít hodnotu false.

Pokud má `key_comp()(X, Y)` hodnotu true, `X` se říká, že se má seřadit před `Y`.

Pokud má `!key_comp()(X, Y) && !key_comp()(Y, X)` hodnotu true, pak `X` a `Y` se říká, že mají ekvivalentní řazení.

U všech prvků `X`, které předcházejí `Y` v řízené sekvenci, `key_comp()(Y, X)` má hodnotu false. (Pro výchozí objekt delegáta klíče nikdy nesnižují hodnotu.) Na rozdíl od sady tříd šablon [(STL/CLR)](../dotnet/set-stl-clr.md)objekt třídy šablony `multiset` nevyžaduje, aby klíče pro všechny elementy byly jedinečné. (Dva nebo více klíčů může mít ekvivalentní řazení.)

Každý prvek slouží jako enalezen i jako hodnota. Sekvence je reprezentována způsobem, který umožňuje vyhledávání, vkládání a odebírání libovolného prvku s řadou operací, které jsou úměrné logaritmu počtu prvků v sekvenci (logaritmický čas). Vkládání prvků navíc nezruší platnost žádných iterátorů a odstranění prvku zruší platnost pouze těch iterátorů, které odkazují na odstraněný prvek.

Multiset podporuje obousměrné iterátory, což znamená, že můžete krokovat s sousedícími prvky daným iterátorem, který určuje prvek v řízené sekvenci. Speciální hlavní uzel odpovídá iterátoru vrácenému funkcí [multiset:: end (STL/CLR)](../dotnet/multiset-end-stl-clr.md)`()`. Tento iterátor můžete snížit tak, aby se dosáhlo posledního prvku v řízené sekvenci, pokud je k dispozici. Můžete zvýšit multiset iterátor, abyste dosáhli hlavního uzlu, a pak se porovná `end()`. Nemůžete ale odkázat na iterátor vrácený `end()`.

Všimněte si, že nemůžete odkazovat na element multiset přímo za jeho číselnou pozici, která vyžaduje iterátor náhodného přístupu.

Iterátor multiset ukládá popisovač do přidruženého uzlu multiset, který zase ukládá popisovač do přidruženého kontejneru. Iterátory lze použít pouze u jejich přidružených objektů kontejneru. Iterátor multiset zůstává platný, pokud je přidružený uzel multiset spojen s některými multiset. Kromě toho je možné, že platný iterátor je deodkazování – můžete ho použít pro přístup k hodnotě prvku, kterou Určuje, a k její změně, pokud to není rovno `end()`.

Při mazání nebo odebírání elementu se volá destruktor pro jeho uloženou hodnotu. Zničení kontejneru smaže všechny prvky. Proto kontejner, jehož typ elementu je ref class, zajistí, že kontejner neobsahuje žádné prvky. Upozorňujeme však, že kontejner popisovačů *nezničí své* prvky.

## <a name="members"></a>Členové

## <a name="multisetbegin-stlclr"></a><a name="begin"></a>multiset:: begin (STL/CLR)

Určuje začátek řízené sekvence.

### <a name="syntax"></a>Syntaxe

```cpp
iterator begin();
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí obousměrný iterátor, který určuje první prvek řízené sekvence nebo těsně za konec prázdné sekvence. Použijete ho k získání iterátoru, který určuje `current` začátek řízené sekvence, ale jeho stav se může změnit, pokud se změní délka kontrolované sekvence.

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

## <a name="multisetclear-stlclr"></a><a name="clear"></a>multiset:: Clear (STL/CLR)

Odebere všechny prvky.

### <a name="syntax"></a>Syntaxe

```cpp
void clear();
```

### <a name="remarks"></a>Poznámky

Členská funkce efektivně volá [multiset:: Erase (STL/CLR)](../dotnet/multiset-erase-stl-clr.md)`(` [multiset:: begin (STL/CLR)](../dotnet/multiset-begin-stl-clr.md)`(),` [MULTISET:: end (STL/CLR)](../dotnet/multiset-end-stl-clr.md)`())`. Použijete ho k zajištění, aby řízená sekvence byla prázdná.

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

## <a name="multisetconst_iterator-stlclr"></a><a name="const_iterator"></a>multiset:: const_iterator (STL/CLR)

Typ konstantního iterátoru řízené sekvence

### <a name="syntax"></a>Syntaxe

```cpp
typedef T2 const_iterator;
```

### <a name="remarks"></a>Poznámky

Typ popisuje objekt nespecifikovaného typu `T2`, který může sloužit jako konstantní obousměrný iterátor pro řízenou sekvenci.

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

## <a name="multisetconst_reference-stlclr"></a><a name="const_reference"></a>multiset:: const_reference (STL/CLR)

Typ konstantního odkazu na prvek

### <a name="syntax"></a>Syntaxe

```cpp
typedef value_type% const_reference;
```

### <a name="remarks"></a>Poznámky

Typ popisuje konstantní odkaz na prvek.

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

## <a name="multisetconst_reverse_iterator-stlclr"></a><a name="const_reverse_iterator"></a>multiset:: const_reverse_iterator (STL/CLR)

Typ konstantního reverzního iterátoru řízené sekvence.

### <a name="syntax"></a>Syntaxe

```cpp
typedef T4 const_reverse_iterator;
```

### <a name="remarks"></a>Poznámky

Typ popisuje objekt nespecifikovaného typu `T4`, který může sloužit jako konstantní reverzní iterátor pro řízenou sekvenci.

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

## <a name="multisetcount-stlclr"></a><a name="count"></a>multiset:: Count (STL/CLR)

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

## <a name="multisetdifference_type-stlclr"></a><a name="difference_type"></a>multiset::d ifference_type (STL/CLR)

Typy podepsané vzdálenosti mezi dvěma prvky.

### <a name="syntax"></a>Syntaxe

```cpp
typedef int difference_type;
```

### <a name="remarks"></a>Poznámky

Typ popisuje pravděpodobně negativní počet prvků.

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

## <a name="multisetempty-stlclr"></a><a name="empty"></a>multiset:: Empty (STL/CLR)

Zkouší, zda nejsou přítomny žádné prvky.

### <a name="syntax"></a>Syntaxe

```cpp
bool empty();
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí hodnotu true pro prázdnou řízenou sekvenci. Je ekvivalentem [multiset:: Size (STL/CLR)](../dotnet/multiset-size-stl-clr.md)`() == 0`. Použijete ho k otestování, jestli je multiset prázdné.

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

## <a name="multisetend-stlclr"></a><a name="end"></a>multiset:: end (STL/CLR)

Určuje konec řízené sekvence.

### <a name="syntax"></a>Syntaxe

```cpp
iterator end();
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí obousměrný iterátor, který odkazuje hned za konec řízené sekvence. Použijete ho k získání iterátoru, který označuje konec řízené sekvence. jeho stav se nemění, pokud se změní délka kontrolované sekvence.

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

## <a name="multisetequal_range-stlclr"></a><a name="equal_range"></a>multiset:: equal_range (STL/CLR)

Najde rozsah, který odpovídá zadanému klíči.

### <a name="syntax"></a>Syntaxe

```cpp
cliext::pair<iterator, iterator> equal_range(key_type key);
```

#### <a name="parameters"></a>Parametry

*key*<br/>
Hodnota klíče, která se má vyhledat

### <a name="remarks"></a>Poznámky

Členská funkce vrací dvojici iterátorů `cliext::pair<iterator, iterator>(` [multiset:: lower_bound (STL/CLR)](../dotnet/multiset-lower-bound-stl-clr.md)`(key),` [multiset:: Upper_bound (STL/CLR)](../dotnet/multiset-upper-bound-stl-clr.md)`(key))`. Použijete ji k určení rozsahu prvků, které jsou aktuálně v řízené sekvenci, která odpovídá zadanému klíči.

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

## <a name="multiseterase-stlclr"></a><a name="erase"></a>multiset:: Erase (STL/CLR)

Odebere prvky v určených pozicích.

### <a name="syntax"></a>Syntaxe

```cpp
iterator erase(iterator where);
iterator erase(iterator first, iterator last);
size_type erase(key_type key)
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

První členská funkce odstraní prvek řízené sekvence, na kterou ukazuje, *kde*a vrátí iterátor, který určí první prvek zbývající za odebraný element, nebo [multiset:: end (STL/CLR)](../dotnet/multiset-end-stl-clr.md)`()`, pokud žádný takový prvek neexistuje. Použijete ho k odebrání jednoho elementu.

Druhá členská funkce odstraní prvky kontrolované sekvence v rozsahu [`first`, `last`) a vrátí iterátor, který určí první prvek zbývající za odebranými prvky, nebo `end()`, pokud žádný takový prvek neexistuje.. Použijete ho k odebrání nuly nebo více souvislých prvků.

Třetí členská funkce odebere všechny prvky kontrolované sekvence, jejichž klíč má ekvivalentní řazení *klíče*, a vrátí počet odebraných prvků. Použijete ho k odebrání a počítání všech prvků, které odpovídají zadanému klíči.

Každé mazání elementu trvá čas úměrný logaritmu počtu prvků v řízené sekvenci.

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

## <a name="multisetfind-stlclr"></a><a name="find"></a>multiset:: Find (STL/CLR)

Vyhledá prvek, který odpovídá zadanému klíči.

### <a name="syntax"></a>Syntaxe

```cpp
iterator find(key_type key);
```

#### <a name="parameters"></a>Parametry

*key*<br/>
Hodnota klíče, která se má vyhledat

### <a name="remarks"></a>Poznámky

Pokud alespoň jeden prvek kontrolované sekvence má ekvivalentní řazení s *klíčem*, vrátí členská funkce iterátor s označením jednoho z těchto elementů. v opačném případě vrátí [multiset:: end (STL/CLR)](../dotnet/multiset-end-stl-clr.md)`()`. Použijete ji k vyhledání prvku, který je aktuálně v řízené sekvenci, která odpovídá zadanému klíči.

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

## <a name="multisetgeneric_container-stlclr"></a><a name="generic_container"></a>multiset:: generic_container (STL/CLR)

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

## <a name="multisetgeneric_iterator-stlclr"></a><a name="generic_iterator"></a>multiset:: generic_iterator (STL/CLR)

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

## <a name="multisetgeneric_reverse_iterator-stlclr"></a><a name="generic_reverse_iterator"></a>multiset:: generic_reverse_iterator (STL/CLR)

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

## <a name="multisetgeneric_value-stlclr"></a><a name="generic_value"></a>multiset:: generic_value (STL/CLR)

Typ elementu pro použití s obecným rozhraním pro kontejner.

### <a name="syntax"></a>Syntaxe

```cpp
typedef GValue generic_value;
```

### <a name="remarks"></a>Poznámky

Typ popisuje objekt typu `GValue`, který popisuje hodnotu uloženého elementu pro použití s obecným rozhraním pro tuto třídu kontejneru šablony.

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

## <a name="multisetinsert-stlclr"></a><a name="insert"></a>multiset:: Insert (STL/CLR)

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

První členská funkce vloží element s hodnotou *Val*a vrátí iterátor, který určí nově vložený element. Použijete ho k vložení jediného elementu.

Druhá členská funkce vloží element s hodnotou *Val*, pomocí *WHERE* jako pomocný parametr (pro zlepšení výkonu) a vrátí iterátor, který určí nově vložený element. Použijete ho k vložení jednoho prvku, který může být sousedící s prvkem, který znáte.

Třetí členská funkce vloží sekvenci [`first`, `last`). Použijete ho k vložení nula nebo více prvků zkopírovaných z jiné sekvence.

Čtvrtá členská funkce vloží sekvenci určenou *vpravo*. Použijete ho k vložení sekvence popsané enumerátorem.

Každé vložení elementu trvá čas úměrný logaritmu počtu prvků v řízené sekvenci. Vložení se může objevit v čase konstantního času, avšak s použitím pomocného parametru, který určuje prvek sousedící s bodem vložení.

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

## <a name="multisetiterator-stlclr"></a><a name="iterator"></a>multiset:: iterátor (STL/CLR)

Typ iterátoru řízené sekvence

### <a name="syntax"></a>Syntaxe

```cpp
typedef T1 iterator;
```

### <a name="remarks"></a>Poznámky

Typ popisuje objekt nespecifikovaného typu `T1`, který může sloužit jako obousměrný iterátor pro řízenou sekvenci.

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

## <a name="multisetkey_comp-stlclr"></a><a name="key_comp"></a>multiset:: key_comp (STL/CLR)

Zkopíruje delegáta řazení dvou klíčů.

### <a name="syntax"></a>Syntaxe

```cpp
key_compare^key_comp();
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí delegáta řazení, který se používá k seřazení řízené sekvence. Použijete ho k porovnání dvou klíčů.

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

## <a name="multisetkey_compare-stlclr"></a><a name="key_compare"></a>multiset:: key_compare (STL/CLR)

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

## <a name="multisetkey_type-stlclr"></a><a name="key_type"></a>multiset:: key_type (STL/CLR)

Typ klíče řazení

### <a name="syntax"></a>Syntaxe

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro *klíč*parametru šablony.

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

## <a name="multisetlower_bound-stlclr"></a><a name="lower_bound"></a>multiset:: lower_bound (STL/CLR)

Vyhledá začátek rozsahu, který odpovídá zadanému klíči.

### <a name="syntax"></a>Syntaxe

```cpp
iterator lower_bound(key_type key);
```

#### <a name="parameters"></a>Parametry

*key*<br/>
Hodnota klíče, která se má vyhledat

### <a name="remarks"></a>Poznámky

Členská funkce určuje první prvek `X` v řízené sekvenci, která má ekvivalentní řazení *klíče*. Pokud žádný takový prvek neexistuje, vrátí [multiset:: end (STL/CLR)](../dotnet/multiset-end-stl-clr.md)`()`; v opačném případě vrátí iterátor, který určí `X`. Použijete ji k vyhledání začátku sekvence prvků, které jsou aktuálně v řízené sekvenci, která odpovídá zadanému klíči.

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

## <a name="multisetmake_value-stlclr"></a><a name="make_value"></a>multiset:: make_value (STL/CLR)

Vytvoří objekt hodnoty.

### <a name="syntax"></a>Syntaxe

```cpp
static value_type make_value(key_type key);
```

#### <a name="parameters"></a>Parametry

*key*<br/>
Hodnota klíče, která se má použít

### <a name="remarks"></a>Poznámky

Členská funkce vrátí objekt `value_type`, jehož klíč je *klíč*. Použijete ho k vytvoření objektu vhodného pro použití s několika dalšími členskými funkcemi.

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

## <a name="multisetmultiset-stlclr"></a><a name="multiset"></a>multiset:: multiset (STL/CLR)

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
Začátek rozsahu, který se má vložit

*posledního*<br/>
Konec rozsahu, který má být vložen.

*čekání*<br/>
Predikát řazení pro řízenou sekvenci.

*Kliknutím*<br/>
Objekt nebo rozsah, který chcete vložit.

### <a name="remarks"></a>Poznámky

Konstruktor:

`multiset();`

Inicializuje řízenou sekvenci bez elementů s výchozím predikátem řazení `key_compare()`. Použijete ji k zadání prázdné počáteční řízené sekvence s výchozím predikátem řazení.

Konstruktor:

`explicit multiset(key_compare^ pred);`

Inicializuje řízená sekvence bez elementů s predikátem řazení *před*. Použijete ji k zadání prázdné počáteční řízené sekvence se zadaným predikátem řazení.

Konstruktor:

`multiset(multiset<Key>% right);`

Inicializuje řízenou sekvenci pomocí sekvence [`right.begin()`, `right.end()`) s výchozím predikátem řazení. Použijete ji k určení počáteční řízené sekvence, která je kopií sekvence *řízené objektem*multiset, s výchozím predikátem řazení.

Konstruktor:

`multiset(multiset<Key>^ right);`

Inicializuje řízenou sekvenci pomocí sekvence [`right->begin()`, `right->end()`) s výchozím predikátem řazení. Použijete ji k určení počáteční řízené sekvence, která je kopií sekvence *řízené objektem*multiset, s výchozím predikátem řazení.

Konstruktor:

`template<typename InIter> multiset(InIter first, InIter last);`

Inicializuje řízenou sekvenci pomocí sekvence [`first`, `last`) s výchozím predikátem řazení. Použijete ji k tomu, aby řízená sekvence zkopírovala jinou sekvenci s výchozím predikátem řazení.

Konstruktor:

`template<typename InIter> multiset(InIter first, InIter last, key_compare^ pred);`

Inicializuje řízenou sekvenci pomocí sekvence [`first`, `last`) s predikátem řazení *před*. Použijete ji k tomu, aby řízená sekvence zkopírovala jinou sekvenci se zadaným predikátem řazení.

Konstruktor:

`multiset(System::Collections::Generic::IEnumerable<Key>^ right);`

Inicializuje řízenou sekvenci sekvencí, která je určena *přípravou*, s výchozím predikátem řazení. Použijete ho k tomu, aby řízená sekvence zkopírovala jinou sekvenci popsanou enumerátorem s výchozím predikátem řazení.

Konstruktor:

`multiset(System::Collections::Generic::IEnumerable<Key>^ right, key_compare^ pred);`

Inicializuje řízená sekvence sekvencí, která je určena *přípravou*, s predikátem řazení *před*. Použijete ho k tomu, aby řízená sekvence zkopírovala jinou sekvenci popsanou enumerátorem, se zadaným predikátem řazení.

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

## <a name="multisetoperator-stlclr"></a><a name="op_as"></a>multiset:: operator = – operátor (STL/CLR)

Nahradí řízenou sekvenci.

### <a name="syntax"></a>Syntaxe

```cpp
multiset<Key>% operator=(multiset<Key>% right);
```

#### <a name="parameters"></a>Parametry

*Kliknutím*<br/>
Kontejner ke zkopírování.

### <a name="remarks"></a>Poznámky

Operátor členu kopíruje *přímo* na objekt a potom vrátí `*this`. Použijete ji k nahrazení kontrolované sekvence kopií kontrolované sekvence *vpravo*.

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

## <a name="multisetrbegin-stlclr"></a><a name="rbegin"></a>multiset:: rbegin (STL/CLR)

Určuje začátek obrácené kontrolované sekvence.

### <a name="syntax"></a>Syntaxe

```cpp
reverse_iterator rbegin();
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí reverzní iterátor, který určuje poslední prvek řízené sekvence nebo těsně za začátek prázdné sekvence. Proto určuje `beginning` reverzní sekvence. Použijete ho k získání iterátoru, který určí `current` začátkem kontrolované sekvence v obráceném pořadí, ale jeho stav se může změnit, pokud se změní délka kontrolované sekvence.

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

## <a name="multisetreference-stlclr"></a><a name="reference"></a>multiset:: Reference (STL/CLR)

Typ odkazu na prvek

### <a name="syntax"></a>Syntaxe

```cpp
typedef value_type% reference;
```

### <a name="remarks"></a>Poznámky

Typ popisuje odkaz na prvek.

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

## <a name="multisetrend-stlclr"></a><a name="rend"></a>multiset:: rend (STL/CLR)

Určuje konec reverzní kontrolované sekvence.

### <a name="syntax"></a>Syntaxe

```cpp
reverse_iterator rend();
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí reverzní iterátor, který odkazuje hned za začátek řízené sekvence. Proto určuje `end` reverzní sekvence. Použijete ho k získání iterátoru, který určuje `current` konec řízené sekvence v obráceném pořadí, ale jeho stav se může změnit, pokud se změní délka kontrolované sekvence.

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

## <a name="multisetreverse_iterator-stlclr"></a><a name="reverse_iterator"></a>multiset:: reverse_iterator (STL/CLR)

Typ reverzního iterátoru řízené sekvence.

### <a name="syntax"></a>Syntaxe

```cpp
typedef T3 reverse_iterator;
```

### <a name="remarks"></a>Poznámky

Typ popisuje objekt nespecifikovaného typu `T3`, který může sloužit jako reverzní iterátor pro řízenou sekvenci.

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

## <a name="multisetsize-stlclr"></a><a name="size"></a>multiset:: Size (STL/CLR)

Spočítá počet prvků.

### <a name="syntax"></a>Syntaxe

```cpp
size_type size();
```

### <a name="remarks"></a>Poznámky

Členská funkce vrací délku řízené sekvence. Použijete ji k určení počtu prvků, které jsou aktuálně v řízené sekvenci. Pokud vás zajímá, zda má sekvence nenulovou velikost, přečtěte si téma [multiset:: Empty (STL/CLR)](../dotnet/multiset-empty-stl-clr.md)`()`.

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

## <a name="multisetsize_type-stlclr"></a><a name="size_type"></a>multiset:: size_type (STL/CLR)

Typ podepsané vzdálenosti mezi dvěma prvky.

### <a name="syntax"></a>Syntaxe

```cpp
typedef int size_type;
```

### <a name="remarks"></a>Poznámky

Typ popisuje nezáporný počet prvků.

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

## <a name="multisetswap-stlclr"></a><a name="swap"></a>multiset:: swap (STL/CLR)

Zamění obsah dvou kontejnerů.

### <a name="syntax"></a>Syntaxe

```cpp
void swap(multiset<Key>% right);
```

#### <a name="parameters"></a>Parametry

*Kliknutím*<br/>
Kontejner pro prohození obsahu pomocí.

### <a name="remarks"></a>Poznámky

Členská funkce přemění kontrolované sekvence mezi `this` a *pravou*. Provede to v konstantním čase a nevyvolává žádné výjimky. Použijete ho jako rychlý způsob, jak vyměňovat obsah dvou kontejnerů.

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

## <a name="multisetto_array-stlclr"></a><a name="to_array"></a>multiset:: to_array (STL/CLR)

Zkopíruje řízenou sekvenci do nového pole.

### <a name="syntax"></a>Syntaxe

```cpp
cli::array<value_type>^ to_array();
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí pole obsahující řízenou sekvenci. Použijete ho k získání kopie řízené sekvence ve formuláři Array.

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

## <a name="multisetupper_bound-stlclr"></a><a name="upper_bound"></a>multiset:: upper_bound (STL/CLR)

Najde konec rozsahu, který odpovídá zadanému klíči.

### <a name="syntax"></a>Syntaxe

```cpp
iterator upper_bound(key_type key);
```

#### <a name="parameters"></a>Parametry

*key*<br/>
Hodnota klíče, která se má vyhledat

### <a name="remarks"></a>Poznámky

Členská funkce určuje poslední prvek `X` v řízené sekvenci, která má ekvivalentní řazení *klíče*. Pokud žádný takový prvek neexistuje nebo pokud `X` je posledním prvkem kontrolované sekvence, vrátí [multiset:: end (STL/CLR)](../dotnet/multiset-end-stl-clr.md)`()`; v opačném případě vrátí iterátor, který určí první prvek nad rámec `X`. Použijete ho k vyhledání konce posloupnosti prvků, které jsou aktuálně v řízené sekvenci, která odpovídá zadanému klíči.

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

## <a name="multisetvalue_comp-stlclr"></a><a name="value_comp"></a>multiset:: value_comp (STL/CLR)

Zkopíruje delegáta řazení pro dvě hodnoty elementu.

### <a name="syntax"></a>Syntaxe

```cpp
value_compare^ value_comp();
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí delegáta řazení, který se používá k seřazení řízené sekvence. Použijete ho k porovnání dvou hodnot prvků.

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

## <a name="multisetvalue_compare-stlclr"></a><a name="value_compare"></a>multiset:: value_compare (STL/CLR)

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

## <a name="multisetvalue_type-stlclr"></a><a name="value_type"></a>multiset:: value_type (STL/CLR)

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

## <a name="operator-multiset-stlclr"></a><a name="op_neq"></a>operator! = (multiset) – operátor (STL/CLR)

Seznam se neshoduje s porovnáním.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Key>
    bool operator!=(multiset<Key>% left,
        multiset<Key>% right);
```

#### <a name="parameters"></a>Parametry

*zbývá*<br/>
Levý kontejner, který se má porovnat

*Kliknutím*<br/>
Pravý kontejner, který se má porovnat

### <a name="remarks"></a>Poznámky

Funkce operátoru vrací `!(left == right)`. Použijete ho k otestování, jestli *vlevo* není seřazené stejně jako *právo* , když se obě množiny porovnají s elementy podle elementu.

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

## <a name="operatorlt-multiset-stlclr"></a><a name="op_lt"></a>operator&lt; (multiset) – operátor (STL/CLR)

Seznam je menší než porovnání.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Key>
    bool operator<(multiset<Key>% left,
        multiset<Key>% right);
```

#### <a name="parameters"></a>Parametry

*zbývá*<br/>
Levý kontejner, který se má porovnat

*Kliknutím*<br/>
Pravý kontejner, který se má porovnat

### <a name="remarks"></a>Poznámky

Funkce operator vrátí hodnotu true, pokud `i` nejnižší pozice, pro kterou `!(right[i] < left[i])` je také true `left[i] < right[i]`. V opačném případě vrátí `left->size() < right->size()` použijete k otestování *, zda je* před *pravou* seřazena druhá množina obou množin podle elementu.

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

## <a name="operatorlt-multiset-stlclr"></a><a name="op_lteq"></a>operator&lt;= (multiset) – operátor (STL/CLR)

Seznam je menší nebo roven hodnotě porovnání.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Key>
    bool operator<=(multiset<Key>% left,
        multiset<Key>% right);
```

#### <a name="parameters"></a>Parametry

*zbývá*<br/>
Levý kontejner, který se má porovnat

*Kliknutím*<br/>
Pravý kontejner, který se má porovnat

### <a name="remarks"></a>Poznámky

Funkce operátoru vrací `!(right < left)`. Použijete ho k otestování *, jestli není* po *pravé straně* při porovnání obou množin podle prvku nařazeno.

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

## <a name="operator-multiset-stlclr"></a><a name="op_eq"></a>operator = = (multiset) – operátor (STL/CLR)

Seznam se stejným porovnáním

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Key>
    bool operator==(multiset<Key>% left,
        multiset<Key>% right);
```

#### <a name="parameters"></a>Parametry

*zbývá*<br/>
Levý kontejner, který se má porovnat

*Kliknutím*<br/>
Pravý kontejner, který se má porovnat

### <a name="remarks"></a>Poznámky

Funkce operator vrátí hodnotu true pouze v případě, že sekvence řízené *levou* a *pravou* mají stejnou délku a pro každou pozici `i``left[i] ==` `right[i]`. Použijete ji k otestování, zda je *levé* řazení stejné jako *pravé* , pokud jsou obě množiny porovnány podle elementu.

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

## <a name="operatorgt-multiset-stlclr"></a><a name="op_gt"></a>operator&gt; (multiset) – operátor (STL/CLR)

Seznam je větší než porovnání.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Key>
    bool operator>(multiset<Key>% left,
        multiset<Key>% right);
```

#### <a name="parameters"></a>Parametry

*zbývá*<br/>
Levý kontejner, který se má porovnat

*Kliknutím*<br/>
Pravý kontejner, který se má porovnat

### <a name="remarks"></a>Poznámky

Funkce operator vrací `right` `<` `left`. Použijete ji k otestování *, zda je* po *pravé straně* při porovnání obou množin podle prvku pořízena druhá.

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

## <a name="operatorgt-multiset-stlclr"></a><a name="op_gteq"></a>operator&gt;= (multiset) – operátor (STL/CLR)

Seznam je větší než nebo rovno porovnání.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename Key>
    bool operator>=(multiset<Key>% left,
        multiset<Key>% right);
```

#### <a name="parameters"></a>Parametry

*zbývá*<br/>
Levý kontejner, který se má porovnat

*Kliknutím*<br/>
Pravý kontejner, který se má porovnat

### <a name="remarks"></a>Poznámky

Funkce operátoru vrací `!(left < right)`. Použijete ji k otestování, zda je *ponechána* před *pravou* , pokud obě množiny jsou porovnány s elementy podle elementu.

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
