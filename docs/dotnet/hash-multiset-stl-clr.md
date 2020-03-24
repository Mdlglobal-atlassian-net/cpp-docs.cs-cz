---
title: hash_multiset (STL/CLR)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cliext::hash_multiset
- cliext::hash_multiset::begin
- cliext::hash_multiset::bucket_count
- cliext::hash_multiset::clear
- cliext::hash_multiset::const_iterator
- cliext::hash_multiset::const_reference
- cliext::hash_multiset::const_reverse_iterator
- cliext::hash_multiset::count
- cliext::hash_multiset::difference_type
- cliext::hash_multiset::empty
- cliext::hash_multiset::end
- cliext::hash_multiset::equal_range
- cliext::hash_multiset::erase
- cliext::hash_multiset::find
- cliext::hash_multiset::generic_container
- cliext::hash_multiset::generic_iterator
- cliext::hash_multiset::generic_reverse_iterator
- cliext::hash_multiset::generic_value
- cliext::hash_multiset::hash_delegate
- cliext::hash_multiset::hash_multiset
- cliext::hash_multiset::hasher
- cliext::hash_multiset::insert
- cliext::hash_multiset::iterator
- cliext::hash_multiset::key_comp
- cliext::hash_multiset::key_compare
- cliext::hash_multiset::key_type
- cliext::hash_multiset::load_factor
- cliext::hash_multiset::lower_bound
- cliext::hash_multiset::make_value
- cliext::hash_multiset::max_load_factor
- cliext::hash_multiset::operator=
- cliext::hash_multiset::rbegin
- cliext::hash_multiset::reference
- cliext::hash_multiset::rehash
- cliext::hash_multiset::rend
- cliext::hash_multiset::reverse_iterator
- cliext::hash_multiset::size
- cliext::hash_multiset::size_type
- cliext::hash_multiset::swap
- cliext::hash_multiset::to_array
- cliext::hash_multiset::upper_bound
- cliext::hash_multiset::value_comp
- cliext::hash_multiset::value_compare
- cliext::hash_multiset::value_type
helpviewer_keywords:
- <cliext/hash_set> header [STL/CLR]
- hash_multiset class [STL/CLR]
- <hash_set> header [STL/CLR]
- begin member [STL/CLR]
- bucket_count member [STL/CLR]
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
- hash_delegate member [STL/CLR]
- hash_multiset member [STL/CLR]
- hasher member [STL/CLR]
- insert member [STL/CLR]
- iterator member [STL/CLR]
- key_comp member [STL/CLR]
- key_compare member [STL/CLR]
- key_type member [STL/CLR]
- load_factor member [STL/CLR]
- lower_bound member [STL/CLR]
- make_value member [STL/CLR]
- max_load_factor member [STL/CLR]
- operator= member [STL/CLR]
- rbegin member [STL/CLR]
- reference member [STL/CLR]
- rehash member [STL/CLR]
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
ms.assetid: 8462bd21-6829-4dd3-ac81-c42d6fdf92f0
ms.openlocfilehash: 87315a24f314222f91e6aa0536ca442bf00f012c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80208687"
---
# <a name="hash_multiset-stlclr"></a>hash_multiset (STL/CLR)

Třída šablony popisuje objekt, který ovládá proměnlivou délku posloupnosti prvků, které mají obousměrný přístup. Použijete `hash_multiset` kontejneru ke správě sekvence prvků jako zatřiďovací tabulky, každý záznam v tabulce, který ukládá obousměrný propojený seznam uzlů, a každý uzel, který ukládá jeden element. Hodnota každého prvku se používá jako klíč pro řazení sekvence.

V popisu níže je `GValue` stejné jako `GKey`, která je naopak stejná jako *klíč* , pokud se jedná o typ REF, v takovém případě je to `Key^`.

## <a name="syntax"></a>Syntaxe

```cpp
template<typename Key>
    ref class hash_multiset
        :   public
        System::ICloneable,
        System::Collections::IEnumerable,
        System::Collections::ICollection,
        System::Collections::Generic::IEnumerable<GValue>,
        System::Collections::Generic::ICollection<GValue>,
        System::Collections::Generic::IList<GValue>,
        Microsoft::VisualC::StlClr::IHash<Gkey, GValue>
    { ..... };
```

### <a name="parameters"></a>Parametry

*Klíč*<br/>
Typ klíčové součásti prvku v řízené sekvenci.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<cliext –/hash_set >

**Obor názvů:** cliext –

## <a name="declarations"></a>Deklarace

|Definice typu|Popis|
|---------------------|-----------------|
|[hash_multiset::const_iterator (STL/CLR)](#const_iterator)|Typ konstantního iterátoru řízené sekvence|
|[hash_multiset::const_reference (STL/CLR)](#const_reference)|Typ konstantního odkazu na prvek|
|[hash_multiset::const_reverse_iterator (STL/CLR)](#const_reverse_iterator)|Typ konstantního reverzního iterátoru řízené sekvence.|
|[hash_multiset::difference_type (STL/CLR)](#difference_type)|Typ (možná znaménko) vzdálenosti mezi dvěma prvky.|
|[hash_multiset::generic_container (STL/CLR)](#generic_container)|Typ obecného rozhraní pro kontejner.|
|[hash_multiset::generic_iterator (STL/CLR)](#generic_iterator)|Typ iterátoru pro obecné rozhraní kontejneru.|
|[hash_multiset::generic_reverse_iterator (STL/CLR)](#generic_reverse_iterator)|Typ reverzního iterátoru pro obecné rozhraní kontejneru.|
|[hash_multiset::generic_value (STL/CLR)](#generic_value)|Typ elementu pro obecné rozhraní kontejneru.|
|[hash_multiset::hasher (STL/CLR)](#hasher)|Delegát algoritmu hash pro klíč|
|[hash_multiset::iterator (STL/CLR)](#iterator)|Typ iterátoru řízené sekvence|
|[hash_multiset::key_compare (STL/CLR)](#key_compare)|Delegát řazení pro dva klíče.|
|[hash_multiset::key_type (STL/CLR)](#key_type)|Typ klíče řazení|
|[hash_multiset::reference (STL/CLR)](#reference)|Typ odkazu na prvek|
|[hash_multiset::reverse_iterator (STL/CLR)](#reverse_iterator)|Typ reverzního iterátoru řízené sekvence.|
|[hash_multiset::size_type (STL/CLR)](#size_type)|Typ (nezáporné) vzdálenosti mezi dvěma prvky.|
|[hash_multiset::value_compare (STL/CLR)](#value_compare)|Delegát řazení pro dvě hodnoty elementu.|
|[hash_multiset::value_type (STL/CLR)](#value_type)|Typ prvku|

|Členská funkce|Popis|
|---------------------|-----------------|
|[hash_multiset::begin (STL/CLR)](#begin)|Určuje začátek řízené sekvence.|
|[hash_multiset::bucket_count (STL/CLR)](#bucket_count)|Spočítá počet intervalů.|
|[hash_multiset::clear (STL/CLR)](#clear)|Odebere všechny prvky.|
|[hash_multiset::count (STL/CLR)](#count)|Spočítá prvky, které odpovídají zadanému klíči.|
|[hash_multiset::empty (STL/CLR)](#empty)|Zkouší, zda nejsou přítomny žádné prvky.|
|[hash_multiset::end (STL/CLR)](#end)|Určuje konec řízené sekvence.|
|[hash_multiset::equal_range (STL/CLR)](#equal_range)|Najde rozsah, který odpovídá zadanému klíči.|
|[hash_multiset::erase (STL/CLR)](#erase)|Odebere prvky v určených pozicích.|
|[hash_multiset::find (STL/CLR)](#find)|Vyhledá prvek, který odpovídá zadanému klíči.|
|[hash_multiset::hash_delegate (STL/CLR)](#hash_delegate)|Zkopíruje delegáta algoritmu hash na klíč.|
|[hash_multiset::hash_multiset (STL/CLR)](#hash_multiset)|Sestaví objekt kontejneru.|
|[hash_multiset::insert (STL/CLR)](#insert)|Přidá prvky.|
|[hash_multiset::key_comp (STL/CLR)](#key_comp)|Zkopíruje delegáta řazení dvou klíčů.|
|[hash_multiset::load_factor (STL/CLR)](#load_factor)|Spočítá průměrný počet prvků na kbelík.|
|[hash_multiset::lower_bound (STL/CLR)](#lower_bound)|Vyhledá začátek rozsahu, který odpovídá zadanému klíči.|
|[hash_multiset::make_value (STL/CLR)](#make_value)|Vytvoří objekt hodnoty.|
|[hash_multiset::max_load_factor (STL/CLR)](#max_load_factor)|Získá nebo nastaví maximální počet prvků na kbelík.|
|[hash_multiset::rbegin (STL/CLR)](#rbegin)|Určuje začátek obrácené kontrolované sekvence.|
|[hash_multiset::rehash (STL/CLR)](#rehash)|Znovu vytvoří hashovací tabulku.|
|[hash_multiset::rend (STL/CLR)](#rend)|Určuje konec reverzní kontrolované sekvence.|
|[hash_multiset::size (STL/CLR)](#size)|Spočítá počet prvků.|
|[hash_multiset::swap (STL/CLR)](#swap)|Zamění obsah dvou kontejnerů.|
|[hash_multiset::to_array (STL/CLR)](#to_array)|Zkopíruje řízenou sekvenci do nového pole.|
|[hash_multiset::upper_bound (STL/CLR)](#upper_bound)|Najde konec rozsahu, který odpovídá zadanému klíči.|
|[hash_multiset::value_comp (STL/CLR)](#value_comp)|Zkopíruje delegáta řazení pro dvě hodnoty elementu.|

|Operátor|Popis|
|--------------|-----------------|
|[hash_multiset::operator= (STL/CLR)](#op)|Nahradí řízenou sekvenci.|

## <a name="interfaces"></a>Rozhraní

|Rozhraní|Popis|
|---------------|-----------------|
|<xref:System.ICloneable>|Duplikuje objekt.|
|<xref:System.Collections.IEnumerable>|Sekvence prostřednictvím prvků.|
|<xref:System.Collections.ICollection>|Udržovat skupinu prvků.|
|<xref:System.Collections.Generic.IEnumerable%601>|Sekvence prostřednictvím typových elementů.|
|<xref:System.Collections.Generic.ICollection%601>|Udržovat skupinu typových elementů.|
|IHash\<klíč, hodnota >|Udržujte obecný kontejner.|

## <a name="remarks"></a>Poznámky

Objekt přiděluje a uvolňuje úložiště pro sekvenci, která řídí jako jednotlivé uzly v obousměrném propojeném seznamu. Chcete-li zrychlit přístup, objekt také udržuje pole ukazatelů s proměnlivou délkou v seznamu (zatřiďovací tabulka) a efektivně spravuje celý seznam jako posloupnost podseznamů nebo kontejnerů. Vloží prvky do kontejneru, který je pořízen, změnou propojení mezi uzly, nikdy kopírováním obsahu jednoho uzlu do druhého. To znamená, že můžete vkládat a odebírat prvky volně bez narušování zbývajících prvků.

Objekt seřadí jednotlivé ovládací prvky IT pomocí volání uloženého objektu delegáta typu [hash_set:: key_compare (STL/CLR)](../dotnet/hash-set-key-compare-stl-clr.md). Uložený objekt delegáta lze zadat při vytváření hash_set; Pokud nezadáte žádný delegovaný objekt, výchozí hodnota je porovnávání `operator<=(key_type, key_type)`.

K uloženému objektu delegáta přistupujete voláním členské funkce [hash_set:: key_comp (STL/CLR)](../dotnet/hash-set-key-comp-stl-clr.md)`()`. Takový objekt delegáta musí definovat ekvivalentní řazení mezi klíči typu [hash_set:: key_type (STL/CLR)](../dotnet/hash-set-key-type-stl-clr.md). To znamená, že pro všechny dva klíče `X` a `Y`:

`key_comp()(X, Y)` vrací stejný logický výsledek při každém volání.

Pokud má `key_comp()(X, Y) && key_comp()(Y, X)` hodnotu true, pak `X` a `Y` se říká, že mají ekvivalentní řazení.

Každé pravidlo řazení, které se chová jako `operator<=(key_type, key_type)`, `operator>=(key_type, key_type)` nebo `operator==(key_type, key_type)` definuje řazení eqivalent.

Všimněte si, že kontejner zajišťuje pouze prvky, jejichž klíče mají ekvivalentní řazení (a algoritmus hash na stejnou celočíselnou hodnotu) sousedící v rámci intervalu. Na rozdíl od třídy template [hash_set (STL/CLR)](../dotnet/hash-set-stl-clr.md), objekt `hash_multiset` třídy šablony nevyžaduje, aby klíče pro všechny elementy byly jedinečné. (Dva nebo více klíčů může mít ekvivalentní řazení.)

Objekt určuje, který kontejner by měl obsahovat daný klíč řazení voláním uloženého objektu delegáta typu [hash_set:: hash (STL/CLR)](../dotnet/hash-set-hasher-stl-clr.md). K tomuto uloženému objektu přistupujete voláním členské funkce [hash_set:: hash_delegate (STL/CLR)](../dotnet/hash-set-hash-delegate-stl-clr.md)`()` k získání celočíselné hodnoty, která závisí na hodnotě klíče. Uložený objekt delegáta lze zadat při vytváření hash_set; Pokud nezadáte žádný delegovaný objekt, výchozí hodnota je funkce `System::Object::hash_value(key_type)`. To znamená, že u všech klíčů `X` a `Y`:

`hash_delegate()(X)` vrátí stejný celočíselný výsledek při každém volání.

Pokud `X` a `Y` mají ekvivalentní řazení, `hash_delegate()(X)` by měl vrátit stejný celočíselný výsledek jako `hash_delegate()(Y)`.

Každý prvek slouží jako klíč i hodnota. Sekvence je reprezentována způsobem, který umožňuje vyhledávání, vkládání a odebírání libovolného prvku s řadou operací, které jsou nezávislé na počtu prvků v sekvenci (konstantní čas), a to alespoň v nejlepším případě. Vkládání prvků navíc nezruší platnost žádných iterátorů a odstranění prvku zruší platnost pouze těch iterátorů, které odkazují na odstraněný prvek.

Pokud se hodnoty hash nestejnoměrně distribuují, může se vygenerovat zatřiďovací tabulka. V extrémním – pro funkci hash, která vždy vrací stejnou hodnotu – vyhledávání, vkládání a odebírání, je úměrné počtu prvků v sekvenci (lineární čas). Kontejner budoucna k výběru přiměřené funkce hash, střední velikosti intervalu a velikosti tabulky hash (celkový počet intervalů), ale můžete přepsat všechny nebo všechny tyto možnosti. Podívejte se například na funkce [hash_set:: max_load_factor (STL/CLR)](../dotnet/hash-set-max-load-factor-stl-clr.md) a [hash_set:: rehash (STL/CLR)](../dotnet/hash-set-rehash-stl-clr.md).

Hash_multiset podporuje obousměrné iterátory, což znamená, že můžete krokovat s sousedícími prvky daným iterátorem, který určuje prvek v řízené sekvenci. Speciální hlavní uzel odpovídá iterátoru vrácenému funkcí [hash_multiset:: end (STL/CLR)](../dotnet/hash-multiset-end-stl-clr.md)`()`. Tento iterátor můžete snížit tak, aby se dosáhlo posledního prvku v řízené sekvenci, pokud je k dispozici. Můžete zvýšit hash_multiset iterátoru tak, aby se dosáhlo hlavního uzlu, a pak se porovná `end()`. Nemůžete ale odkázat na iterátor vrácený `end()`.

Všimněte si, že nemůžete odkazovat na hash_multiset element přímo za jeho číselnou pozici, která vyžaduje iterátor náhodného přístupu.

Hash_multiset iterátor ukládá popisovač ke svému přidruženému hash_multiset uzlu, který zase ukládá popisovač do přidruženého kontejneru. Iterátory lze použít pouze u jejich přidružených objektů kontejneru. Iterátor hash_multiset zůstává platný, pokud je přidružený hash_multiset uzel spojen s některými hash_multiset. Kromě toho je možné, že platný iterátor je deodkazování – můžete ho použít pro přístup k hodnotě prvku, kterou Určuje, a k její změně, pokud to není rovno `end()`.

Při mazání nebo odebírání elementu se volá destruktor pro jeho uloženou hodnotu. Zničení kontejneru smaže všechny prvky. Proto kontejner, jehož typ elementu je ref class, zajistí, že kontejner neobsahuje žádné prvky. Upozorňujeme však, že kontejner popisovačů *nezničí své* prvky.

## <a name="members"></a>Členové

## <a name="hash_multisetbegin-stlclr"></a><a name="begin"></a>hash_multiset:: begin (STL/CLR)

Určuje začátek řízené sekvence.

### <a name="syntax"></a>Syntaxe

```cpp
iterator begin();
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí obousměrný iterátor, který určuje první prvek řízené sekvence nebo těsně za konec prázdné sekvence. Použijete ho k získání iterátoru, který určuje `current` začátek řízené sekvence, ale jeho stav se může změnit, pokud se změní délka kontrolované sekvence.

### <a name="example"></a>Příklad

```cpp
// cliext_hash_multiset_begin.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect first two items
    Myhash_multiset::iterator it = c1.begin();
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

## <a name="hash_multisetbucket_count-stlclr"></a><a name="bucket_count"></a>hash_multiset:: bucket_count (STL/CLR)

Spočítá počet intervalů.

### <a name="syntax"></a>Syntaxe

```cpp
int bucket_count();
```

### <a name="remarks"></a>Poznámky

Členské funkce vrátí aktuální počet intervalů. Použijete ji k určení velikosti zatřiďovací tabulky.

### <a name="example"></a>Příklad

```cpp
// cliext_hash_multiset_bucket_count.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect current parameters
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());
    System::Console::WriteLine("max_load_factor() = {0}",
        c1.max_load_factor());
    System::Console::WriteLine();

    // change max_load_factor and redisplay
    c1.max_load_factor(0.25f);
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());
    System::Console::WriteLine("max_load_factor() = {0}",
        c1.max_load_factor());
    System::Console::WriteLine();

    // rehash and redisplay
    c1.rehash(100);
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());
    System::Console::WriteLine("max_load_factor() = {0}",
        c1.max_load_factor());
    return (0);
    }
```

```Output
a b c
bucket_count() = 16
load_factor() = 0.1875
max_load_factor() = 4

bucket_count() = 16
load_factor() = 0.1875
max_load_factor() = 0.25

bucket_count() = 128
load_factor() = 0.0234375
max_load_factor() = 0.25
```

## <a name="hash_multisetclear-stlclr"></a><a name="clear"></a>hash_multiset:: Clear (STL/CLR)

Odebere všechny prvky.

### <a name="syntax"></a>Syntaxe

```cpp
void clear();
```

### <a name="remarks"></a>Poznámky

Členská funkce efektivně volá [hash_multiset:: Erase (STL/CLR)](../dotnet/hash-multiset-erase-stl-clr.md)`(` [hash_multiset:: begin (STL/clr)](../dotnet/hash-multiset-begin-stl-clr.md)`(),` [HASH_MULTISET:: end (STL/CLR)](../dotnet/hash-multiset-end-stl-clr.md)`())`. Použijete ho k zajištění, aby řízená sekvence byla prázdná.

### <a name="example"></a>Příklad

```cpp
// cliext_hash_multiset_clear.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
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

## <a name="hash_multisetconst_iterator-stlclr"></a><a name="const_iterator"></a>hash_multiset:: const_iterator (STL/CLR)

Typ konstantního iterátoru řízené sekvence

### <a name="syntax"></a>Syntaxe

```cpp
typedef T2 const_iterator;
```

### <a name="remarks"></a>Poznámky

Typ popisuje objekt nespecifikovaného typu `T2`, který může sloužit jako konstantní obousměrný iterátor pro řízenou sekvenci.

### <a name="example"></a>Příklad

```cpp
// cliext_hash_multiset_const_iterator.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    Myhash_multiset::const_iterator cit = c1.begin();
    for (; cit != c1.end(); ++cit)
        System::Console::Write("{0} ", *cit);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="hash_multisetconst_reference-stlclr"></a><a name="const_reference"></a>hash_multiset:: const_reference (STL/CLR)

Typ konstantního odkazu na prvek

### <a name="syntax"></a>Syntaxe

```cpp
typedef value_type% const_reference;
```

### <a name="remarks"></a>Poznámky

Typ popisuje konstantní odkaz na prvek.

### <a name="example"></a>Příklad

```cpp
// cliext_hash_multiset_const_reference.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    Myhash_multiset::const_iterator cit = c1.begin();
    for (; cit != c1.end(); ++cit)
        {   // get a const reference to an element
        Myhash_multiset::const_reference cref = *cit;
        System::Console::Write("{0} ", cref);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="hash_multisetconst_reverse_iterator-stlclr"></a><a name="const_reverse_iterator"></a>hash_multiset:: const_reverse_iterator (STL/CLR)

Typ konstantního reverzního iterátoru řízené sekvence.

### <a name="syntax"></a>Syntaxe

```cpp
typedef T4 const_reverse_iterator;
```

### <a name="remarks"></a>Poznámky

Typ popisuje objekt nespecifikovaného typu `T4`, který může sloužit jako konstantní reverzní iterátor pro řízenou sekvenci.

### <a name="example"></a>Příklad

```cpp
// cliext_hash_multiset_const_reverse_iterator.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c" reversed
    Myhash_multiset::const_reverse_iterator crit = c1.rbegin();
    for (; crit != c1.rend(); ++crit)
        System::Console::Write("{0} ", *crit);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c b a
```

## <a name="hash_multisetcount-stlclr"></a><a name="count"></a>hash_multiset:: Count (STL/CLR)

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
// cliext_hash_multiset_count.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
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

## <a name="hash_multisetdifference_type-stlclr"></a><a name="difference_type"></a>hash_multiset::d ifference_type (STL/CLR)

Typy podepsané vzdálenosti mezi dvěma prvky.

### <a name="syntax"></a>Syntaxe

```cpp
typedef int difference_type;
```

### <a name="remarks"></a>Poznámky

Typ popisuje pravděpodobně negativní počet prvků.

### <a name="example"></a>Příklad

```cpp
// cliext_hash_multiset_difference_type.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // compute positive difference
    Myhash_multiset::difference_type diff = 0;
    for (Myhash_multiset::iterator it = c1.begin(); it != c1.end(); ++it)
        ++diff;
    System::Console::WriteLine("end()-begin() = {0}", diff);

    // compute negative difference
    diff = 0;
    for (Myhash_multiset::iterator it = c1.end(); it != c1.begin(); --it)
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

## <a name="hash_multisetempty-stlclr"></a><a name="empty"></a>hash_multiset:: Empty (STL/CLR)

Zkouší, zda nejsou přítomny žádné prvky.

### <a name="syntax"></a>Syntaxe

```cpp
bool empty();
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí hodnotu true pro prázdnou řízenou sekvenci. Je ekvivalentní [hash_multiset:: Size (STL/CLR)](../dotnet/hash-multiset-size-stl-clr.md)`() == 0`. Použijete ho k otestování, jestli je hash_multiset prázdné.

### <a name="example"></a>Příklad

```cpp
// cliext_hash_multiset_empty.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
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

## <a name="hash_multisetend-stlclr"></a><a name="end"></a>hash_multiset:: end (STL/CLR)

Určuje konec řízené sekvence.

### <a name="syntax"></a>Syntaxe

```cpp
iterator end();
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí obousměrný iterátor, který odkazuje hned za konec řízené sekvence. Použijete ho k získání iterátoru, který označuje konec řízené sekvence. jeho stav se nemění, pokud se změní délka kontrolované sekvence.

### <a name="example"></a>Příklad

```cpp
// cliext_hash_multiset_end.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect last two items
    Myhash_multiset::iterator it = c1.end();
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

## <a name="hash_multisetequal_range-stlclr"></a><a name="equal_range"></a>hash_multiset:: equal_range (STL/CLR)

Najde rozsah, který odpovídá zadanému klíči.

### <a name="syntax"></a>Syntaxe

```cpp
cliext::pair<iterator, iterator> equal_range(key_type key);
```

#### <a name="parameters"></a>Parametry

*key*<br/>
Hodnota klíče, která se má vyhledat

### <a name="remarks"></a>Poznámky

Členská funkce vrací dvojici iterátorů `cliext::pair<iterator, iterator>(` [hash_multiset:: lower_bound (STL/CLR)](../dotnet/hash-multiset-lower-bound-stl-clr.md)`(key),` hash_multiset [:: Upper_bound (STL/CLR)](../dotnet/hash-multiset-upper-bound-stl-clr.md)`(key))`. Použijete ji k určení rozsahu prvků, které jsou aktuálně v řízené sekvenci, která odpovídá zadanému klíči.

### <a name="example"></a>Příklad

```cpp
// cliext_hash_multiset_equal_range.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
typedef Myhash_multiset::pair_iter_iter Pairii;
int main()
    {
    Myhash_multiset c1;
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

## <a name="hash_multiseterase-stlclr"></a><a name="erase"></a>hash_multiset:: Erase (STL/CLR)

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

První členská funkce odstraní prvek kontrolované sekvence, na kterou ukazuje, *kde*a vrátí iterátor, který určí první prvek zbývající za odebraný element, nebo [hash_multiset:: end (STL/CLR)](../dotnet/hash-multiset-end-stl-clr.md)`()`, pokud žádný takový prvek neexistuje. Použijete ho k odebrání jednoho elementu.

Druhá členská funkce odstraní prvky kontrolované sekvence v rozsahu [`first`, `last`) a vrátí iterátor, který určí první prvek zbývající za odebranými prvky, nebo `end()`, pokud žádný takový prvek neexistuje.. Použijete ho k odebrání nuly nebo více souvislých prvků.

Třetí členská funkce odebere všechny prvky kontrolované sekvence, jejichž klíč má ekvivalentní řazení *klíče*, a vrátí počet odebraných prvků. Použijete ho k odebrání a počítání všech prvků, které odpovídají zadanému klíči.

Každé mazání elementu trvá čas úměrný logaritmu počtu prvků v řízené sekvenci.

### <a name="example"></a>Příklad

```cpp
// cliext_hash_multiset_erase.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
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
    Myhash_multiset::iterator it = c1.end();
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

## <a name="hash_multisetfind-stlclr"></a><a name="find"></a>hash_multiset:: Find (STL/CLR)

Vyhledá prvek, který odpovídá zadanému klíči.

### <a name="syntax"></a>Syntaxe

```cpp
iterator find(key_type key);
```

#### <a name="parameters"></a>Parametry

*key*<br/>
Hodnota klíče, která se má vyhledat

### <a name="remarks"></a>Poznámky

Pokud alespoň jeden prvek kontrolované sekvence má ekvivalentní řazení s *klíčem*, vrátí členská funkce iterátor s označením jednoho z těchto elementů. v opačném případě vrátí [hash_multiset:: end (STL/CLR)](../dotnet/hash-multiset-end-stl-clr.md)`()`. Použijete ji k vyhledání prvku, který je aktuálně v řízené sekvenci, která odpovídá zadanému klíči.

### <a name="example"></a>Příklad

```cpp
// cliext_hash_multiset_find.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
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

## <a name="hash_multisetgeneric_container-stlclr"></a><a name="generic_container"></a>hash_multiset:: generic_container (STL/CLR)

Typ obecného rozhraní pro kontejner.

### <a name="syntax"></a>Syntaxe

```cpp
typedef Microsoft::VisualC::StlClr::
    IHash<GKey, GValue>
    generic_container;
```

### <a name="remarks"></a>Poznámky

Typ popisuje obecné rozhraní pro tuto třídu kontejneru šablony.

### <a name="example"></a>Příklad

```cpp
// cliext_hash_multiset_generic_container.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct a generic container
    Myhash_multiset::generic_container^ gc1 = %c1;
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

## <a name="hash_multisetgeneric_iterator-stlclr"></a><a name="generic_iterator"></a>hash_multiset:: generic_iterator (STL/CLR)

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
// cliext_hash_multiset_generic_iterator.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct a generic container
    Myhash_multiset::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // get an element and display it
    Myhash_multiset::generic_iterator gcit = gc1->begin();
    Myhash_multiset::generic_value gcval = *gcit;
    System::Console::WriteLine("{0} ", gcval);
    return (0);
    }
```

```Output
a b c
a b c
a
```

## <a name="hash_multisetgeneric_reverse_iterator-stlclr"></a><a name="generic_reverse_iterator"></a>hash_multiset:: generic_reverse_iterator (STL/CLR)

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
// cliext_hash_multiset_generic_reverse_iterator.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct a generic container
    Myhash_multiset::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // get an element and display it
    Myhash_multiset::generic_reverse_iterator gcit = gc1->rbegin();
    Myhash_multiset::generic_value gcval = *gcit;
    System::Console::WriteLine("{0} ", gcval);
    return (0);
    }
```

```Output
a b c
a b c
c
```

## <a name="hash_multisetgeneric_value-stlclr"></a><a name="generic_value"></a>hash_multiset:: generic_value (STL/CLR)

Typ elementu pro použití s obecným rozhraním pro kontejner.

### <a name="syntax"></a>Syntaxe

```cpp
typedef GValue generic_value;
```

### <a name="remarks"></a>Poznámky

Typ popisuje objekt typu `GValue`, který popisuje hodnotu uloženého elementu pro použití s obecným rozhraním pro tuto třídu kontejneru šablony.

### <a name="example"></a>Příklad

```cpp
// cliext_hash_multiset_generic_value.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct a generic container
    Myhash_multiset::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // get an element and display it
    Myhash_multiset::generic_iterator gcit = gc1->begin();
    Myhash_multiset::generic_value gcval = *gcit;
    System::Console::WriteLine("{0} ", gcval);
    return (0);
    }
```

```Output
a b c
a b c
a
```

## <a name="hash_multisethash_delegate-stlclr"></a><a name="hash_delegate"></a>hash_multiset:: hash_delegate (STL/CLR)

Vyhledá prvek, který odpovídá zadanému klíči.

### <a name="syntax"></a>Syntaxe

```cpp
hasher^ hash_delegate();
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí delegáta, který se používá k převodu hodnoty klíče na celé číslo. Použijete ho k vytvoření hodnoty hash klíče.

### <a name="example"></a>Příklad

```cpp
// cliext_hash_multiset_hash_delegate.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    Myhash_multiset::hasher^ myhash = c1.hash_delegate();

    System::Console::WriteLine("hash(L'a') = {0}", myhash(L'a'));
    System::Console::WriteLine("hash(L'b') = {0}", myhash(L'b'));
    return (0);
    }
```

```Output
hash(L'a') = 1616896120
hash(L'b') = 570892832
```

## <a name="hash_multisethash_multiset-stlclr"></a><a name="hash_multiset"></a>hash_multiset:: hash_multiset (STL/CLR)

Sestaví objekt kontejneru.

### <a name="syntax"></a>Syntaxe

```cpp
hash_multiset();
explicit hash_multiset(key_compare^ pred);
hash_multiset(key_compare^ pred, hasher^ hashfn);
hash_multiset(hash_multiset<Key>% right);
hash_multiset(hash_multiset<Key>^ right);
template<typename InIter>
    hash_multiset(InIter first, InIter last);
template<typename InIter>
    hash_multiset(InIter first, InIter last,
        key_compare^ pred);
template<typename InIter>
    hash_multiset(InIter first, InIter last,
        key_compare^ pred, hasher^ hashfn);
hash_multiset(System::Collections::Generic::IEnumerable<GValue>^ right);
hash_multiset(System::Collections::Generic::IEnumerable<GValue>^ right,
    key_compare^ pred);
hash_multiset(System::Collections::Generic::IEnumerable<GValue>^ right,
    key_compare^ pred, hasher^ hashfn);
```

#### <a name="parameters"></a>Parametry

*první*<br/>
Začátek rozsahu, který se má vložit

*hashfn*<br/>
Funkce hash pro mapování klíčů na intervaly

*posledního*<br/>
Konec rozsahu, který má být vložen.

*čekání*<br/>
Predikát řazení pro řízenou sekvenci.

*Kliknutím*<br/>
Objekt nebo rozsah, který chcete vložit.

### <a name="remarks"></a>Poznámky

Konstruktor:

`hash_multiset();`

Inicializuje řízená sekvence bez elementů s výchozím predikátem řazení `key_compare()`a s výchozí funkcí hash. Použijete ji k zadání prázdné počáteční řízené sekvence s výchozím predikátem řazení a funkcí hash.

Konstruktor:

`explicit hash_multiset(key_compare^ pred);`

Inicializuje řízená sekvence bez elementů s predikátem řazení *před*a s výchozí funkcí hash. Použijete ji k zadání prázdné počáteční řízené sekvence se zadaným predikátem řazení a výchozí funkcí hash.

Konstruktor:

`hash_multiset(key_compare^ pred, hasher^ hashfn);`

Inicializuje řízená sekvence bez elementů s predikátem řazení *před*a s funkcí hash *hashfn*. Použijete ji k zadání prázdné počáteční řízené sekvence se zadaným predikátem řazení a funkcí hash.

Konstruktor:

`hash_multiset(hash_multiset<Key>% right);`

Inicializuje řízenou sekvenci pomocí sekvence [`right.begin()`, `right.end()`), s výchozím predikátem řazení a s výchozí funkcí hash. Použijete ji k určení počáteční řízené sekvence, která je kopií sekvence řízené objektem hash_multiset *vpravo*s výchozím predikátem řazení a funkcí hash.

Konstruktor:

`hash_multiset(hash_multiset<Key>^ right);`

Inicializuje řízenou sekvenci pomocí sekvence [`right->begin()`, `right->end()`), s výchozím predikátem řazení a s výchozí funkcí hash. Použijete ji k určení počáteční řízené sekvence, která je kopií sekvence řízené objektem hash_multiset *vpravo*s výchozím predikátem řazení a funkcí hash.

Konstruktor:

`template<typename InIter> hash_multiset(InIter first, InIter last);`

Inicializuje řízenou sekvenci pomocí sekvence [`first`, `last`), s výchozím predikátem řazení a s výchozí funkcí hash. Použijete ji k tomu, aby řízená sekvence zkopírovala jinou sekvenci s výchozím predikátem řazení a funkcí hash.

Konstruktor:

`template<typename InIter> hash_multiset(InIter first, InIter last, key_compare^ pred);`

Inicializuje řízenou sekvenci pomocí sekvence [`first`, `last`), s predikátem řazení *před*a s výchozí funkcí hash. Použijete ho k tomu, aby řízená sekvence zkopírovala jinou sekvenci, se zadaným predikátem řazení a výchozí funkcí hash.

Konstruktor:

`template<typename InIter> hash_multiset(InIter first, InIter last, key_compare^ pred, hasher^ hashfn);`

Inicializuje řízenou sekvenci pomocí sekvence [`first`, `last`), s predikátem řazení *před*a *hashfn*funkcí hash. Použijete ji k tomu, aby řízená sekvence zkopírovala jinou sekvenci, se zadaným predikátem řazení a funkcí hash.

Konstruktor:

`hash_multiset(System::Collections::Generic::IEnumerable<Key>^ right);`

Inicializuje řízenou sekvenci sekvencí, která je určena *přípravou*, s výchozím predikátem řazení a s výchozí funkcí hash. Použijete ho k tomu, aby řízená sekvence zkopírovala jinou sekvenci popsanou enumerátorem s výchozím predikátem řazení a funkcí hash.

Konstruktor:

`hash_multiset(System::Collections::Generic::IEnumerable<Key>^ right, key_compare^ pred);`

Inicializuje řízenou sekvenci sekvencí, která je určena *přípravou*, s predikátem řazení *před*a s výchozí funkcí hash. Použijete ho k tomu, aby řízená sekvence zkopírovala jinou sekvenci popsanou enumerátorem, se zadaným predikátem řazení a výchozí funkcí hash.

Konstruktor:

`hash_multiset(System::Collections::Generic::IEnumerable<Key>^ right, key_compare^ pred, hasher^ hashfn);`

Inicializuje řízenou sekvenci sekvencí, která je určena *přípravou*, s predikátem řazení *před*a s funkcí hash *hashfn*. Použijete ho k tomu, aby řízená sekvence zkopírovala jinou sekvenci popsanou enumerátorem, se zadaným predikátem řazení a funkcí hash.

### <a name="example"></a>Příklad

```cpp
// cliext_hash_multiset_construct.cpp
// compile with: /clr
#include <cliext/hash_set>

int myfun(wchar_t key)
    { // hash a key
    return (key ^ 0xdeadbeef);
    }

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
// construct an empty container
    Myhash_multiset c1;
    System::Console::WriteLine("size() = {0}", c1.size());

    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an ordering rule
    Myhash_multiset c2 = cliext::greater_equal<wchar_t>();
    System::Console::WriteLine("size() = {0}", c2.size());

    c2.insert(c1.begin(), c1.end());
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an ordering rule and hash function
    Myhash_multiset c2h(cliext::greater_equal<wchar_t>(),
        gcnew Myhash_multiset::hasher(&myfun));
    System::Console::WriteLine("size() = {0}", c2h.size());

    c2h.insert(c1.begin(), c1.end());
    for each (wchar_t elem in c2h)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    System::Console::WriteLine();

    // construct with an iterator range
    Myhash_multiset c3(c1.begin(), c1.end());
    for each (wchar_t elem in c3)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an iterator range and an ordering rule
    Myhash_multiset c4(c1.begin(), c1.end(),
        cliext::greater_equal<wchar_t>());
    for each (wchar_t elem in c4)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an iterator range and an ordering rule and hash function
    Myhash_multiset c4h(c1.begin(), c1.end(),
        cliext::greater_equal<wchar_t>(),
        gcnew Myhash_multiset::hasher(&myfun));
    for each (wchar_t elem in c4h)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    System::Console::WriteLine();

    // construct with an enumeration
    Myhash_multiset c5(   // NOTE: cast is not needed
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3);
    for each (wchar_t elem in c5)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an enumeration and an ordering rule
    Myhash_multiset c6(   // NOTE: cast is not needed
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3,
            cliext::greater_equal<wchar_t>());
    for each (wchar_t elem in c6)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an enumeration and an ordering rule and hash function
    Myhash_multiset c6h(   // NOTE: cast is not needed
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3,
            cliext::greater_equal<wchar_t>(),
                gcnew Myhash_multiset::hasher(&myfun));
    for each (wchar_t elem in c6h)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    System::Console::WriteLine();

    // construct from a generic container
    Myhash_multiset c7(c4);
    for each (wchar_t elem in c7)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct by copying another container
    Myhash_multiset c8(%c3);
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
a b c
size() = 0
c b a

a b c
a b c
c b a

a b c
a b c
c b a

a b c
a b c
```

## <a name="hash_multisethasher-stlclr"></a><a name="hasher"></a>hash_multiset:: hash (STL/CLR)

Delegát algoritmu hash pro klíč

### <a name="syntax"></a>Syntaxe

```cpp
Microsoft::VisualC::StlClr::UnaryDelegate<GKey, int>
    hasher;
```

### <a name="remarks"></a>Poznámky

Typ popisuje delegáta, který převede hodnotu klíče na celé číslo.

### <a name="example"></a>Příklad

```cpp
// cliext_hash_multiset_hasher.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    Myhash_multiset::hasher^ myhash = c1.hash_delegate();

    System::Console::WriteLine("hash(L'a') = {0}", myhash(L'a'));
    System::Console::WriteLine("hash(L'b') = {0}", myhash(L'b'));
    return (0);
    }
```

```Output
hash(L'a') = 1616896120
hash(L'b') = 570892832
```

## <a name="hash_multisetinsert-stlclr"></a><a name="insert"></a>hash_multiset:: Insert (STL/CLR)

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
// cliext_hash_multiset_insert.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
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
    Myhash_multiset c2;
    Myhash_multiset::iterator it = c1.end();
    c2.insert(c1.begin(), --it);
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // insert an enumeration
    Myhash_multiset c3;
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

## <a name="hash_multisetiterator-stlclr"></a><a name="iterator"></a>hash_multiset:: iterátor (STL/CLR)

Typ iterátoru řízené sekvence

### <a name="syntax"></a>Syntaxe

```cpp
typedef T1 iterator;
```

### <a name="remarks"></a>Poznámky

Typ popisuje objekt nespecifikovaného typu `T1`, který může sloužit jako obousměrný iterátor pro řízenou sekvenci.

### <a name="example"></a>Příklad

```cpp
// cliext_hash_multiset_iterator.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    Myhash_multiset::iterator it = c1.begin();
    for (; it != c1.end(); ++it)
        System::Console::Write("{0} ", *it);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="hash_multisetkey_comp-stlclr"></a><a name="key_comp"></a>hash_multiset:: key_comp (STL/CLR)

Zkopíruje delegáta řazení dvou klíčů.

### <a name="syntax"></a>Syntaxe

```cpp
key_compare^key_comp();
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí delegáta řazení, který se používá k seřazení řízené sekvence. Použijete ho k porovnání dvou klíčů.

### <a name="example"></a>Příklad

```cpp
// cliext_hash_multiset_key_comp.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    Myhash_multiset::key_compare^ kcomp = c1.key_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        kcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        kcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        kcomp(L'b', L'a'));
    System::Console::WriteLine();

    // test a different ordering rule
    Myhash_multiset c2 = cliext::greater<wchar_t>();
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
compare(L'a', L'a') = True
compare(L'a', L'b') = True
compare(L'b', L'a') = False

compare(L'a', L'a') = False
compare(L'a', L'b') = False
compare(L'b', L'a') = True
```

## <a name="hash_multisetkey_compare-stlclr"></a><a name="key_compare"></a>hash_multiset:: key_compare (STL/CLR)

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
// cliext_hash_multiset_key_compare.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    Myhash_multiset::key_compare^ kcomp = c1.key_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        kcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        kcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        kcomp(L'b', L'a'));
    System::Console::WriteLine();

    // test a different ordering rule
    Myhash_multiset c2 = cliext::greater<wchar_t>();
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
compare(L'a', L'a') = True
compare(L'a', L'b') = True
compare(L'b', L'a') = False

compare(L'a', L'a') = False
compare(L'a', L'b') = False
compare(L'b', L'a') = True
```

## <a name="hash_multisetkey_type-stlclr"></a><a name="key_type"></a>hash_multiset:: key_type (STL/CLR)

Typ klíče řazení

### <a name="syntax"></a>Syntaxe

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro *klíč*parametru šablony.

### <a name="example"></a>Příklad

```cpp
// cliext_hash_multiset_key_type.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c" using key_type
    for (Myhash_multiset::iterator it = c1.begin(); it != c1.end(); ++it)
        {   // store element in key_type object
        Myhash_multiset::key_type val = *it;

        System::Console::Write("{0} ", val);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="hash_multisetload_factor-stlclr"></a><a name="load_factor"></a>hash_multiset:: load_factor (STL/CLR)

Spočítá průměrný počet prvků na kbelík.

### <a name="syntax"></a>Syntaxe

```cpp
float load_factor();
```

### <a name="remarks"></a>Poznámky

Členská funkce vrací `(float)`[hash_multiset:: Size (STL/CLR)](../dotnet/hash-multiset-size-stl-clr.md)`() /` [hash_multiset:: bucket_count (STL/CLR)](../dotnet/hash-multiset-bucket-count-stl-clr.md)`()`. Použijete ji k určení průměrné velikosti intervalu.

### <a name="example"></a>Příklad

```cpp
// cliext_hash_multiset_load_factor.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect current parameters
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());
    System::Console::WriteLine("max_load_factor() = {0}",
        c1.max_load_factor());
    System::Console::WriteLine();

    // change max_load_factor and redisplay
    c1.max_load_factor(0.25f);
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());
    System::Console::WriteLine("max_load_factor() = {0}",
        c1.max_load_factor());
    System::Console::WriteLine();

    // rehash and redisplay
    c1.rehash(100);
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());
    System::Console::WriteLine("max_load_factor() = {0}",
        c1.max_load_factor());
    return (0);
    }
```

```Output
a b c
bucket_count() = 16
load_factor() = 0.1875
max_load_factor() = 4

bucket_count() = 16
load_factor() = 0.1875
max_load_factor() = 0.25

bucket_count() = 128
load_factor() = 0.0234375
max_load_factor() = 0.25
```

## <a name="hash_multisetlower_bound-stlclr"></a><a name="lower_bound"></a>hash_multiset:: lower_bound (STL/CLR)

Vyhledá začátek rozsahu, který odpovídá zadanému klíči.

### <a name="syntax"></a>Syntaxe

```cpp
iterator lower_bound(key_type key);
```

#### <a name="parameters"></a>Parametry

*key*<br/>
Hodnota klíče, která se má vyhledat

### <a name="remarks"></a>Poznámky

Členská funkce určuje první prvek `X` v řízené sekvenci, který vyhodnotí hodnoty hash ke stejnému kontejneru jako *klíč* a má stejné řazení jako *klíč*. Pokud žádný takový prvek neexistuje, vrátí [hash_multiset:: end (STL/CLR)](../dotnet/hash-multiset-end-stl-clr.md)`()`; v opačném případě vrátí iterátor, který určí `X`. Použijete ji k vyhledání začátku sekvence prvků, které jsou aktuálně v řízené sekvenci, která odpovídá zadanému klíči.

### <a name="example"></a>Příklad

```cpp
// cliext_hash_multiset_lower_bound.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
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

## <a name="hash_multisetmake_value-stlclr"></a><a name="make_value"></a>hash_multiset:: make_value (STL/CLR)

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
// cliext_hash_multiset_make_value.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(Myhash_multiset::make_value(L'a'));
    c1.insert(Myhash_multiset::make_value(L'b'));
    c1.insert(Myhash_multiset::make_value(L'c'));

    // display contents " a b c"
    for each (Myhash_multiset::value_type elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="hash_multisetmax_load_factor-stlclr"></a><a name="max_load_factor"></a>hash_multiset:: max_load_factor (STL/CLR)

Získá nebo nastaví maximální počet prvků na kbelík.

### <a name="syntax"></a>Syntaxe

```cpp
float max_load_factor();
void max_load_factor(float new_factor);
```

#### <a name="parameters"></a>Parametry

*new_factor*<br/>
Nový faktor maximálního zatížení, který se má uložit.

### <a name="remarks"></a>Poznámky

První členská funkce vrátí aktuální uložený faktor zatížení. Použijete ji k určení maximální průměrné velikosti intervalu.

Druhá členská funkce nahrazuje faktor maximálního zatížení úložiště *new_factor*. K automatickému opakovanému hashování nedochází až po následném vložení.

### <a name="example"></a>Příklad

```cpp
// cliext_hash_multiset_max_load_factor.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect current parameters
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());
    System::Console::WriteLine("max_load_factor() = {0}",
        c1.max_load_factor());
    System::Console::WriteLine();

    // change max_load_factor and redisplay
    c1.max_load_factor(0.25f);
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());
    System::Console::WriteLine("max_load_factor() = {0}",
        c1.max_load_factor());
    System::Console::WriteLine();

    // rehash and redisplay
    c1.rehash(100);
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());
    System::Console::WriteLine("max_load_factor() = {0}",
        c1.max_load_factor());
    return (0);
    }
```

```Output
a b c
bucket_count() = 16
load_factor() = 0.1875
max_load_factor() = 4

bucket_count() = 16
load_factor() = 0.1875
max_load_factor() = 0.25

bucket_count() = 128
load_factor() = 0.0234375
max_load_factor() = 0.25
```

## <a name="hash_multisetoperator-stlclr"></a><a name="op"></a>hash_multiset:: operator = (STL/CLR)

Nahradí řízenou sekvenci.

### <a name="syntax"></a>Syntaxe

```cpp
hash_multiset<Key>% operator=(hash_multiset<Key>% right);
```

#### <a name="parameters"></a>Parametry

*Kliknutím*<br/>
Kontejner ke zkopírování.

### <a name="remarks"></a>Poznámky

Operátor členu kopíruje *přímo* na objekt a potom vrátí `*this`. Použijete ji k nahrazení kontrolované sekvence kopií kontrolované sekvence *vpravo*.

### <a name="example"></a>Příklad

```cpp
// cliext_hash_multiset_operator_as.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    for each (Myhash_multiset::value_type elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    Myhash_multiset c2;
    c2 = c1;
// display contents " a b c"
    for each (Myhash_multiset::value_type elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a b c
```

## <a name="hash_multisetrbegin-stlclr"></a><a name="rbegin"></a>hash_multiset:: rbegin (STL/CLR)

Určuje začátek obrácené kontrolované sekvence.

### <a name="syntax"></a>Syntaxe

```cpp
reverse_iterator rbegin();
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí reverzní iterátor, který určuje poslední prvek řízené sekvence nebo těsně za začátek prázdné sekvence. Proto určuje `beginning` reverzní sekvence. Použijete ho k získání iterátoru, který určí `current` začátkem kontrolované sekvence v obráceném pořadí, ale jeho stav se může změnit, pokud se změní délka kontrolované sekvence.

### <a name="example"></a>Příklad

```cpp
// cliext_hash_multiset_rbegin.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect first two items in reversed sequence
    Myhash_multiset::reverse_iterator rit = c1.rbegin();
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

## <a name="hash_multisetreference-stlclr"></a><a name="reference"></a>hash_multiset:: Reference (STL/CLR)

Typ odkazu na prvek

### <a name="syntax"></a>Syntaxe

```cpp
typedef value_type% reference;
```

### <a name="remarks"></a>Poznámky

Typ popisuje odkaz na prvek.

### <a name="example"></a>Příklad

```cpp
// cliext_hash_multiset_reference.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    Myhash_multiset::iterator it = c1.begin();
    for (; it != c1.end(); ++it)
        {   // get a reference to an element
        Myhash_multiset::reference ref = *it;
        System::Console::Write("{0} ", ref);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="hash_multisetrehash-stlclr"></a><a name="rehash"></a>hash_multiset:: rehash (STL/CLR)

Znovu vytvoří hashovací tabulku.

### <a name="syntax"></a>Syntaxe

```cpp
void rehash();
```

### <a name="remarks"></a>Poznámky

Členská funkce znovu sestaví zatřiďovací tabulku, což zajišťuje, že [hash_multiset:: load_factor (STL/CLR)](../dotnet/hash-multiset-load-factor-stl-clr.md)`() <=` [hash_multiset:: max_load_factor (STL/CLR)](../dotnet/hash-multiset-max-load-factor-stl-clr.md). V opačném případě se tabulka hash zvětšuje velikost pouze podle potřeby po vložení. (Nikdy se velikost automaticky nezmenší.) Použijete ho k úpravě velikosti zatřiďovací tabulky.

### <a name="example"></a>Příklad

```cpp
// cliext_hash_multiset_rehash.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect current parameters
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());
    System::Console::WriteLine("max_load_factor() = {0}",
        c1.max_load_factor());
    System::Console::WriteLine();

    // change max_load_factor and redisplay
    c1.max_load_factor(0.25f);
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());
    System::Console::WriteLine("max_load_factor() = {0}",
        c1.max_load_factor());
    System::Console::WriteLine();

    // rehash and redisplay
    c1.rehash(100);
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());
    System::Console::WriteLine("max_load_factor() = {0}",
        c1.max_load_factor());
    return (0);
    }
```

```Output
a b c
bucket_count() = 16
load_factor() = 0.1875
max_load_factor() = 4

bucket_count() = 16
load_factor() = 0.1875
max_load_factor() = 0.25

bucket_count() = 128
load_factor() = 0.0234375
max_load_factor() = 0.25
```

## <a name="hash_multisetrend-stlclr"></a><a name="rend"></a>hash_multiset:: rend (STL/CLR)

Určuje konec reverzní kontrolované sekvence.

### <a name="syntax"></a>Syntaxe

```cpp
reverse_iterator rend();
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí reverzní iterátor, který odkazuje hned za začátek řízené sekvence. Proto určuje `end` reverzní sekvence. Použijete ho k získání iterátoru, který určuje `current` konec řízené sekvence v obráceném pořadí, ale jeho stav se může změnit, pokud se změní délka kontrolované sekvence.

### <a name="example"></a>Příklad

```cpp
// cliext_hash_multiset_rend.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect first two items
    Myhash_multiset::reverse_iterator rit = c1.rend();
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

## <a name="hash_multisetreverse_iterator-stlclr"></a><a name="reverse_iterator"></a>hash_multiset:: reverse_iterator (STL/CLR)

Typ reverzního iterátoru řízené sekvence.

### <a name="syntax"></a>Syntaxe

```cpp
typedef T3 reverse_iterator;
```

### <a name="remarks"></a>Poznámky

Typ popisuje objekt nespecifikovaného typu `T3`, který může sloužit jako reverzní iterátor pro řízenou sekvenci.

### <a name="example"></a>Příklad

```cpp
// cliext_hash_multiset_reverse_iterator.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c" reversed
    Myhash_multiset::reverse_iterator rit = c1.rbegin();
    for (; rit != c1.rend(); ++rit)
        System::Console::Write("{0} ", *rit);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c b a
```

## <a name="hash_multisetsize-stlclr"></a><a name="size"></a>hash_multiset:: Size (STL/CLR)

Spočítá počet prvků.

### <a name="syntax"></a>Syntaxe

```cpp
size_type size();
```

### <a name="remarks"></a>Poznámky

Členská funkce vrací délku řízené sekvence. Použijete ji k určení počtu prvků, které jsou aktuálně v řízené sekvenci. Pokud vás zajímá, zda má sekvence nenulovou velikost, přečtěte si téma [hash_multiset:: Empty (STL/CLR)](../dotnet/hash-multiset-empty-stl-clr.md)`()`.

### <a name="example"></a>Příklad

```cpp
// cliext_hash_multiset_size.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
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

## <a name="hash_multisetsize_type-stlclr"></a><a name="size_type"></a>hash_multiset:: size_type (STL/CLR)

Typ podepsané vzdálenosti mezi dvěma prvky.

### <a name="syntax"></a>Syntaxe

```cpp
typedef int size_type;
```

### <a name="remarks"></a>Poznámky

Typ popisuje nezáporný počet prvků.

### <a name="example"></a>Příklad

```cpp
// cliext_hash_multiset_size_type.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // compute positive difference
    Myhash_multiset::size_type diff = 0;
    for (Myhash_multiset::iterator it = c1.begin(); it != c1.end(); ++it)
        ++diff;
    System::Console::WriteLine("end()-begin() = {0}", diff);
    return (0);
    }
```

```Output
a b c
end()-begin() = 3
```

## <a name="hash_multisetswap-stlclr"></a><a name="swap"></a>hash_multiset:: swap (STL/CLR)

Zamění obsah dvou kontejnerů.

### <a name="syntax"></a>Syntaxe

```cpp
void swap(hash_multiset<Key>% right);
```

#### <a name="parameters"></a>Parametry

*Kliknutím*<br/>
Kontejner pro prohození obsahu pomocí.

### <a name="remarks"></a>Poznámky

Členská funkce přemění kontrolované sekvence mezi `this` a *pravou*. Provede to v konstantním čase a nevyvolává žádné výjimky. Použijete ho jako rychlý způsob, jak vyměňovat obsah dvou kontejnerů.

### <a name="example"></a>Příklad

```cpp
// cliext_hash_multiset_swap.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct another container with repetition of values
    Myhash_multiset c2;
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

## <a name="hash_multisetto_array-stlclr"></a><a name="to_array"></a>hash_multiset:: to_array (STL/CLR)

Zkopíruje řízenou sekvenci do nového pole.

### <a name="syntax"></a>Syntaxe

```cpp
cli::array<value_type>^ to_array();
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí pole obsahující řízenou sekvenci. Použijete ho k získání kopie řízené sekvence ve formuláři Array.

### <a name="example"></a>Příklad

```cpp
// cliext_hash_multiset_to_array.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
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

## <a name="hash_multisetupper_bound-stlclr"></a><a name="upper_bound"></a>hash_multiset:: upper_bound (STL/CLR)

Najde konec rozsahu, který odpovídá zadanému klíči.

### <a name="syntax"></a>Syntaxe

```cpp
iterator upper_bound(key_type key);
```

#### <a name="parameters"></a>Parametry

*key*<br/>
Hodnota klíče, která se má vyhledat

### <a name="remarks"></a>Poznámky

Členská funkce určuje poslední prvek `X` v řízené sekvenci, který vyhodnotí hodnoty hash ke stejnému kontejneru jako *klíč* a má stejné řazení jako *klíč*. Pokud žádný takový prvek neexistuje nebo pokud `X` je posledním prvkem kontrolované sekvence, vrátí [hash_multiset:: end (STL/CLR)](../dotnet/hash-multiset-end-stl-clr.md)`()`; v opačném případě vrátí iterátor, který určí první prvek nad rámec `X`. Použijete ho k vyhledání konce posloupnosti prvků, které jsou aktuálně v řízené sekvenci, která odpovídá zadanému klíči.

### <a name="example"></a>Příklad

```cpp
// cliext_hash_multiset_upper_bound.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
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

## <a name="hash_multisetvalue_comp-stlclr"></a><a name="value_comp"></a>hash_multiset:: value_comp (STL/CLR)

Zkopíruje delegáta řazení pro dvě hodnoty elementu.

### <a name="syntax"></a>Syntaxe

```cpp
value_compare^ value_comp();
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí delegáta řazení, který se používá k seřazení řízené sekvence. Použijete ho k porovnání dvou hodnot prvků.

### <a name="example"></a>Příklad

```cpp
// cliext_hash_multiset_value_comp.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    Myhash_multiset::value_compare^ kcomp = c1.value_comp();

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
compare(L'a', L'a') = True
compare(L'a', L'b') = True
compare(L'b', L'a') = False
```

## <a name="hash_multisetvalue_compare-stlclr"></a><a name="value_compare"></a>hash_multiset:: value_compare (STL/CLR)

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
// cliext_hash_multiset_value_compare.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    Myhash_multiset::value_compare^ kcomp = c1.value_comp();

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
compare(L'a', L'a') = True
compare(L'a', L'b') = True
compare(L'b', L'a') = False
```

## <a name="hash_multisetvalue_type-stlclr"></a><a name="value_type"></a>hash_multiset:: value_type (STL/CLR)

Typ prvku

### <a name="syntax"></a>Syntaxe

```cpp
typedef generic_value value_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro `generic_value`.

### <a name="example"></a>Příklad

```cpp
// cliext_hash_multiset_value_type.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c" using value_type
    for (Myhash_multiset::iterator it = c1.begin(); it != c1.end(); ++it)
        {   // store element in value_type object
        Myhash_multiset::value_type val = *it;

        System::Console::Write("{0} ", val);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```
