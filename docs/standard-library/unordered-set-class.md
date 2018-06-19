---
title: unordered_set – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- unordered_set/std::unordered_set
- unordered_set/std::unordered_set::allocator_type
- unordered_set/std::unordered_set::const_iterator
- unordered_set/std::unordered_set::const_local_iterator
- unordered_set/std::unordered_set::const_pointer
- unordered_set/std::unordered_set::const_reference
- unordered_set/std::unordered_set::difference_type
- unordered_set/std::unordered_set::hasher
- unordered_set/std::unordered_set::iterator
- unordered_set/std::unordered_set::key_equal
- unordered_set/std::unordered_set::key_type
- unordered_set/std::unordered_set::local_iterator
- unordered_set/std::unordered_set::pointer
- unordered_set/std::unordered_set::reference
- unordered_set/std::unordered_set::size_type
- unordered_set/std::unordered_set::value_type
- unordered_set/std::unordered_set::begin
- unordered_set/std::unordered_set::bucket
- unordered_set/std::unordered_set::bucket_count
- unordered_set/std::unordered_set::bucket_size
- unordered_set/std::unordered_set::cbegin
- unordered_set/std::unordered_set::cend
- unordered_set/std::unordered_set::clear
- unordered_set/std::unordered_set::count
- unordered_set/std::unordered_set::emplace
- unordered_set/std::unordered_set::emplace_hint
- unordered_set/std::unordered_set::empty
- unordered_set/std::unordered_set::end
- unordered_set/std::unordered_set::equal_range
- unordered_set/std::unordered_set::erase
- unordered_set/std::unordered_set::find
- unordered_set/std::unordered_set::get_allocator
- unordered_set/std::unordered_set::hash
- unordered_set/std::unordered_set::insert
- unordered_set/std::unordered_set::key_eq
- unordered_set/std::unordered_set::load_factor
- unordered_set/std::unordered_set::max_bucket_count
- unordered_set/std::unordered_set::max_load_factor
- unordered_set/std::unordered_set::max_size
- unordered_set/std::unordered_set::rehash
- unordered_set/std::unordered_set::size
- unordered_set/std::unordered_set::swap
- unordered_set/std::unordered_set::unordered_set
- unordered_set/std::unordered_set::operator=
- unordered_set/std::unordered_set::hash_function
dev_langs:
- C++
helpviewer_keywords:
- std::unordered_set
- std::unordered_set::allocator_type
- std::unordered_set::const_iterator
- std::unordered_set::const_local_iterator
- std::unordered_set::const_pointer
- std::unordered_set::const_reference
- std::unordered_set::difference_type
- std::unordered_set::hasher
- std::unordered_set::iterator
- std::unordered_set::key_equal
- std::unordered_set::key_type
- std::unordered_set::local_iterator
- std::unordered_set::pointer
- std::unordered_set::reference
- std::unordered_set::size_type
- std::unordered_set::value_type
- std::unordered_set::begin
- std::unordered_set::bucket
- std::unordered_set::bucket_count
- std::unordered_set::bucket_size
- std::unordered_set::cbegin
- std::unordered_set::cend
- std::unordered_set::clear
- std::unordered_set::count
- std::unordered_set::emplace
- std::unordered_set::emplace_hint
- std::unordered_set::empty
- std::unordered_set::end
- std::unordered_set::equal_range
- std::unordered_set::erase
- std::unordered_set::find
- std::unordered_set::get_allocator
- std::unordered_set::hash
- std::unordered_set::insert
- std::unordered_set::key_eq
- std::unordered_set::load_factor
- std::unordered_set::max_bucket_count
- std::unordered_set::max_load_factor
- std::unordered_set::max_size
- std::unordered_set::rehash
- std::unordered_set::size
- std::unordered_set::swap
- std::unordered_set::unordered_set
- std::unordered_set::operator=
- std::unordered_set::allocator_type
- std::unordered_set::const_iterator
- std::unordered_set::const_local_iterator
- std::unordered_set::const_pointer
- std::unordered_set::const_reference
- std::unordered_set::difference_type
- std::unordered_set::hasher
- std::unordered_set::iterator
- std::unordered_set::key_equal
- std::unordered_set::key_type
- std::unordered_set::local_iterator
- std::unordered_set::pointer
- std::unordered_set::reference
- std::unordered_set::size_type
- std::unordered_set::value_type
- std::unordered_set::begin
- std::unordered_set::bucket
- std::unordered_set::bucket_count
- std::unordered_set::bucket_size
- std::unordered_set::cbegin
- std::unordered_set::cend
- std::unordered_set::clear
- std::unordered_set::count
- std::unordered_set::emplace
- std::unordered_set::emplace_hint
- std::unordered_set::empty
- std::unordered_set::end
- std::unordered_set::equal_range
- std::unordered_set::erase
- std::unordered_set::find
- std::unordered_set::get_allocator
- std::unordered_set::hash_function
- std::unordered_set::insert
- std::unordered_set::key_eq
- std::unordered_set::load_factor
- std::unordered_set::max_bucket_count
- std::unordered_set::max_load_factor
- std::unordered_set::max_size
- std::unordered_set::rehash
- std::unordered_set::size
- std::unordered_set::swap
ms.assetid: ac08084e-05a7-48c0-9ae4-d40c529922dd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e31c0eb559f36b1921660a900a6ade0ba095b6f8
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33862884"
---
# <a name="unorderedset-class"></a>unordered_set – třída

Šablony třídy popisuje objekt, který určuje posloupnost různých délka elementy typu `const Key`. Sekvence je slabě seřazená podle funkce hash, která sekvenci rozděluje do uspořádané sady dílčích sekvencí, které se nazývají kbelíky. V rámci každého kbelíku funkce porovnání určuje, zda má nějaká dvojice prvků odpovídající řazení. Každý prvek slouží jako klíč řazení i hodnota. Sekvence je reprezentována způsobem, který umožňuje vyhledat, vložit a odebrat libovolný prvek s několika operacemi, které mohou být nezávislé na počtu prvků v sekvenci (konstantní čas), alespoň pokud všechny kbelíky mají přibližně stejnou délku. V nejhorším případě platí, že když jsou všechny prvky v jednom kbelíku, je počet operací úměrný počtu prvků v sekvenci (lineární čas). Vkládání prvků navíc nezruší platnost žádných iterátorů a odstranění prvku zruší platnost pouze těch iterátorů, které odkazují na odstraněný prvek.

## <a name="syntax"></a>Syntaxe

```cpp
template <
   class Key,
   class Hash = std::hash<Key>,
   class Pred = std::equal_to<Key>,
   class Alloc = std::allocator<Key>>
class unordered_set;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|-|-|
|`Key`|Klíčový typ|
|`Hash`|Typ objektu hashovací funkce|
|`Pred`|Typ objektu funkce porovnání rovnosti|
|`Alloc`|Třída alokátoru|

## <a name="members"></a>Členové

|Definice typu|Popis|
|-|-|
|[allocator_type –](#allocator_type)|Typ alokátoru pro správu úložiště|
|[const_iterator](#const_iterator)|Typ konstantního iterátoru řízené sekvence|
|[const_local_iterator](#const_local_iterator)|Typ konstantního iterátoru kbelíku řízené sekvence|
|[const_pointer](#const_pointer)|Typ konstantního ukazatele na prvek|
|[const_reference](#const_reference)|Typ konstantního odkazu na prvek|
|[difference_type](#difference_type)|Typ vzdálenosti se znaménkem mezi dvěma prvky|
|[hasher](#hasher)|Typ hashovací funkce|
|[Iterator](#iterator)|Typ iterátoru řízené sekvence|
|[key_equal](#key_equal)|Typ funkce porovnání|
|[key_type](#key_type)|Typ klíče řazení|
|[local_iterator](#local_iterator)|Typ iterátoru kbelíku řízené sekvence|
|[Ukazatele](#pointer)|Typ ukazatele na prvek|
|[Referenční dokumentace](#reference)|Typ odkazu na prvek|
|[size_type](#size_type)|Typ vzdálenosti bez znaménka mezi dvěma prvky|
|[value_type](#value_type)|Typ prvku|

|Členská funkce|Popis|
|-|-|
|[Začátek](#begin)|Určuje začátek řízené sekvence.|
|[sady](#bucket)|Získá číslo kbelíku pro hodnotu klíče.|
|[bucket_count](#bucket_count)|Získá počet kbelíků.|
|[bucket_size](#bucket_size)|Získá velikost kbelíku.|
|[cbegin –](#cbegin)|Určuje začátek řízené sekvence.|
|[cend –](#cend)|Určuje konec řízené sekvence.|
|[Zrušte zaškrtnutí](#clear)|Odebere všechny prvky.|
|[Počet](#count)|Zjistí počet prvků odpovídající zadanému klíči.|
|[emplace –](#emplace)|Přidá prvek vytvořený v místě.|
|[emplace_hint –](#emplace_hint)|Přidá prvek vytvořený v místě s nápovědou.|
|[prázdný](#empty)|Zkouší, zda nejsou přítomny žádné prvky.|
|[End](#end)|Určuje konec řízené sekvence.|
|[equal_range](#equal_range)|Najde rozsah, který odpovídá zadanému klíči.|
|[vymazání](#erase)|Odebere prvky v určených pozicích.|
|[Najít](#find)|Vyhledá prvek, který odpovídá zadanému klíči.|
|[get_allocator](#get_allocator)|Získá uložený objekt alokátoru.|
|[hash_function –](#hash)|Získá uložený objekt hashovací funkce.|
|[Vložení](#insert)|Přidá prvky.|
|[key_eq](#key_eq)|Získá uložený objekt funkce porovnání.|
|[load_factor –](#load_factor)|Spočítá průměrný počet prvků na kbelík.|
|[max_bucket_count](#max_bucket_count)|Získá maximální počet kbelíků.|
|[max_load_factor](#max_load_factor)|Získá nebo nastaví maximální počet prvků na kbelík.|
|[max_size](#max_size)|Získá maximální velikost řízené sekvence.|
|[rehash –](#rehash)|Znovu vytvoří hashovací tabulku.|
|[Velikost](#size)|Spočítá počet prvků.|
|[Swap](#swap)|Zamění obsah dvou kontejnerů.|
|[unordered_set](#unordered_set)|Sestaví objekt kontejneru.|

|Operátory|Popis|
|-|-|
|[unordered_set::operator=](#op_eq)|Zkopíruje tabulku hash.|

## <a name="remarks"></a>Poznámky

Objekt řadí pořadí jimi řídí voláním dva uložené objekty, objekt funkci porovnání typu[unordered_set::key_equal](#key_equal) a objekt funkce algoritmu hash typu[unordered_set::hasher](#hasher). Přístup je první objekt uložené voláním členské funkce[unordered_set::key_eq](#key_eq)`()`; a přístup druhý objekt uložené voláním členské funkce[unordered_set::hash_function](#hash) `()`. Konkrétně pro všechny hodnoty `X` a `Y` typu `Key`, volání `key_eq()(X, Y)` vrátí hodnotu true pouze v případě hodnoty dvou argument ekvivalentní řazení; volání `hash_function()(keyval)` vypočítá distribuci hodnot typu `size_t`. Na rozdíl od třídy šablony[unordered_multiset – třída](../standard-library/unordered-multiset-class.md), objekt třídy šablony `unordered_set` zajistí, že `key_eq()(X, Y)` je vždy hodnotu false pro všechny dva elementy řízené sekvenci. (Klíče jsou jedinečné).

Objekt také uchovává faktor maximálního zatížení, který určuje maximální požadovaný průměrný počet prvků na kbelík. Pokud vkládání element způsobí[unordered_set::load_factor](#load_factor) `()` delší než maximální zatížení faktor, zvyšuje počet intervalů a podle potřeby znovu sestaví zatřiďovací tabulku kontejneru.

Skutečné pořadí prvků v řízené sekvenci závisí na hashovací funkci, funkci porovnání, pořadí vkládání, faktoru maximálního zatížení a aktuálním počtu kbelíků. Pořadí prvků v řízené sekvenci obecně nelze předvídat. Můžete si však vždy být jisti, že všechny dílčí množiny prvků, které mají ekvivalentní řazení, v řízené sekvenci sousedí.

Objekt přiděluje a uvolní úložiště pro pořadí jimi řídí prostřednictvím objektu uložené allocator typu[unordered_set::allocator_type](#allocator_type). Takový objekt allocator musí mít stejné externí rozhraní jako objekt třídy šablony `allocator`. Všimněte si, že uložený objekt alokátoru není zkopírován při přiřazení objektu kontejneru.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<unordered_set >

**Namespace:** – std

## <a name="allocator_type"></a>  unordered_set::allocator_type

Typ alokátoru pro správu úložiště

```cpp
typedef Alloc allocator_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro parametr šablony `Alloc`.

### <a name="example"></a>Příklad

```cpp
// std__unordered_set__unordered_set_allocator_type.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
typedef std::allocator<std::pair<const char, int> > Myalloc;
int main()
{
    Myset c1;

    Myset::allocator_type al = c1.get_allocator();
    std::cout << "al == std::allocator() is "
    << std::boolalpha << (al == Myalloc()) << std::endl;

    return (0);
}
```

```Output
al == std::allocator() is true
```

## <a name="begin"></a>  unordered_set::begin

Označuje začátek řízené sekvenci nebo blok.

```cpp
iterator begin();

const_iterator begin() const;

local_iterator begin(size_type nbucket);

const_local_iterator begin(size_type nbucket) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|-|-|
|`nbucket`|Počet kbelíků.|

### <a name="remarks"></a>Poznámky

První dva členské funkce vrátí dopředného iterator této body v prvním elementem pořadí (nebo jenom přesahuje za konec prázdnou sekvencí). Poslední dva členské funkce vrátí dopředného iterator odkazující na první prvek sady `nbucket` (nebo jenom přesahuje za konec prázdný sady).

### <a name="example"></a>Příklad

```cpp
// unordered_set_begin.cpp
// compile using: cl.exe /EHsc /nologo /W4 /MTd
#include <unordered_set>
#include <iostream>

using namespace std;

typedef unordered_set<char> MySet;

int main()
{
    MySet c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents using range-based for
    for (auto it : c1) {
    cout << " [" << it << "]";
    }

    cout << endl;

    // display contents using explicit for
    for (MySet::const_iterator it = c1.begin(); it != c1.end(); ++it) {
        cout << " [" << *it << "]";
    }

    cout << std::endl;

    // display first two items
    MySet::iterator it2 = c1.begin();
    cout << " [" << *it2 << "]";
    ++it2;
    cout << " [" << *it2 << "]";
    cout << endl;

    // display bucket containing 'a'
    MySet::const_local_iterator lit = c1.begin(c1.bucket('a'));
    cout << " [" << *lit << "]";

    return (0);
}
```

```Output
 [a] [b] [c]
 [a] [b] [c]
 [a] [b]
 [a]
```

## <a name="bucket"></a>  unordered_set::Bucket

Získá číslo kbelíku pro hodnotu klíče.

```cpp
size_type bucket(const Key& keyval) const;
```

### <a name="parameters"></a>Parametry

`keyval` Hodnota klíče pro mapování.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí číslo sady aktuálně odpovídající hodnotě klíče `keyval`.

### <a name="example"></a>Příklad

```cpp
// std__unordered_set__unordered_set_bucket.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents " [c] [b] [a]"
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << " [" << *it << "]";
    std::cout << std::endl;

    // display buckets for keys
    Myset::size_type bs = c1.bucket('a');
    std::cout << "bucket('a') == " << bs << std::endl;
    std::cout << "bucket_size(" << bs << ") == " << c1.bucket_size(bs)
    << std::endl;

    return (0);
}
```

```Output
 [c] [b] [a]
bucket('a') == 7
bucket_size(7) == 1
```

## <a name="bucket_count"></a>  unordered_set::bucket_count

Získá počet kbelíků.

```cpp
size_type bucket_count() const;
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí aktuální počet intervalů.

### <a name="example"></a>Příklad

```cpp
// std__unordered_set__unordered_set_bucket_count.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents " [c] [b] [a]"
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << " [" << *it << "]";
    std::cout << std::endl;

    // inspect current parameters
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_bucket_count() == "
    << c1.max_bucket_count() << std::endl;
    std::cout << "max_load_factor() == "
    << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

    // change max_load_factor and redisplay
    c1.max_load_factor(0.10f);
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_bucket_count() == "
    << c1.max_bucket_count() << std::endl;
    std::cout << "max_load_factor() == "
    << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

    // rehash and redisplay
    c1.rehash(100);
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_bucket_count() == "
    << c1.max_bucket_count() << std::endl;
    std::cout << "max_load_factor() == "
    << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

    return (0);
}
```

```Output
 [c] [b] [a]
bucket_count() == 8
load_factor() == 0.375
max_bucket_count() == 8
max_load_factor() == 4

bucket_count() == 8
load_factor() == 0.375
max_bucket_count() == 8
max_load_factor() == 0.1

bucket_count() == 128
load_factor() == 0.0234375
max_bucket_count() == 128
max_load_factor() == 0.1
```

## <a name="bucket_size"></a>  unordered_set::bucket_size

Získá velikost blok

```cpp
size_type bucket_size(size_type nbucket) const;
```

### <a name="parameters"></a>Parametry

`nbucket` Počet kbelíků.

### <a name="remarks"></a>Poznámky

Členské funkce vrátí velikost sady číslo `nbucket`.

### <a name="example"></a>Příklad

```cpp
// std__unordered_set__unordered_set_bucket_size.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents " [c] [b] [a]"
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << " [" << *it << "]";
    std::cout << std::endl;

    // display buckets for keys
    Myset::size_type bs = c1.bucket('a');
    std::cout << "bucket('a') == " << bs << std::endl;
    std::cout << "bucket_size(" << bs << ") == " << c1.bucket_size(bs)
    << std::endl;

    return (0);
}
```

```Output
 [c] [b] [a]
bucket('a') == 7
bucket_size(7) == 1
```

## <a name="cbegin"></a>  unordered_set::cbegin

Vrátí `const` iterator, která řeší prvním elementem v rozsahu.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>Návratová hodnota

A `const` iterator předat dál přístup, který odkazuje na první prvek rozsahu nebo umístění právě přesahuje za konec prázdného rozsahu (pro prázdného rozsahu, `cbegin() == cend()`).

### <a name="remarks"></a>Poznámky

S návratovou hodnotou `cbegin`, nemůže být upravena elementů v rozsahu.

Můžete použít tuto funkci člen místě `begin()` – členská funkce zaručit, že je návratovou hodnotu `const_iterator`. Obvykle se používá ve spojení s[automaticky](../cpp/auto-cpp.md) odvození – klíčové slovo, zadejte, jak je znázorněno v následujícím příkladu. V příkladu, vezměte v úvahu `Container` upravitelná (jinou hodnotu než `const`) kontejneru libovolného typu, který podporuje `begin()` a `cbegin()`.

```cpp
auto i1 = Container.begin();
// i1 isContainer<T>::iterator
auto i2 = Container.cbegin();

// i2 isContainer<T>::const_iterator
```

## <a name="cend"></a>  unordered_set::cend

Vrátí `const` iterator, která řeší umístění bezprostředně za posledním prvkem v rozsahu.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>Návratová hodnota

A `const` iterator předat dál přístup, který odkazuje právě přesahuje za konec rozsahu.

### <a name="remarks"></a>Poznámky

`cend` slouží k ověření, zda iterovat uplynutí konec její rozsah.

Můžete použít tuto funkci člen místě `end()` – členská funkce zaručit, že je návratovou hodnotu `const_iterator`. Obvykle se používá ve spojení s[automaticky](../cpp/auto-cpp.md) odvození – klíčové slovo, zadejte, jak je znázorněno v následujícím příkladu. V příkladu, vezměte v úvahu `Container` upravitelná (jinou hodnotu než `const`) kontejneru libovolného typu, který podporuje `end()` a `cend()`.

```cpp
auto i1 = Container.end();
// i1 isContainer<T>::iterator
auto i2 = Container.cend();

// i2 isContainer<T>::const_iterator
```

Hodnoty vrácené `cend` by neměl být vyhodnoceny odkazy.

## <a name="clear"></a>  unordered_set::clear

Odebere všechny prvky.

```cpp
void clear();
```

### <a name="remarks"></a>Poznámky

Volání členských funkcí[unordered_set::erase](#erase) `(` [unordered_set::begin](#begin) `(),` [unordered_set::end](#end)`())`.

### <a name="example"></a>Příklad

```cpp
// std__unordered_set__unordered_set_clear.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents " [c] [b] [a]"
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << " [" << *it << "]";
    std::cout << std::endl;

    // clear the container and reinspect
    c1.clear();
    std::cout << "size == " << c1.size() << std::endl;
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;
    std::cout << std::endl;

    c1.insert('d');
    c1.insert('e');

    // display contents " [e] [d]"
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << " [" << *it << "]";
    std::cout << std::endl;

    std::cout << "size == " << c1.size() << std::endl;
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;

    return (0);
}
```

```Output
 [c] [b] [a]
size == 0
empty() == true
 [e] [d]
size == 2
empty() == false
```

## <a name="const_iterator"></a>  unordered_set::const_iterator

Typ konstantního iterátoru řízené sekvence

```cpp
typedef T1 const_iterator;
```

### <a name="remarks"></a>Poznámky

Popisuje typ objektu, který může sloužit jako konstantní dopředného iterator pro řízené sekvenci. Je popsán sem jako synonymum pro typ definované implementací `T1`.

### <a name="example"></a>Příklad

```cpp
// std__unordered_set__unordered_set_const_iterator.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents " [c] [b] [a]"
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
    std::cout << " [" << *it << "]";
    std::cout << std::endl;

    return (0);
}
```

```Output
 [c] [b] [a]
```

## <a name="const_local_iterator"></a>  unordered_set::const_local_iterator

Typ konstantního iterátoru kbelíku řízené sekvence

```cpp
typedef T5 const_local_iterator;
```

### <a name="remarks"></a>Poznámky

Popisuje typ objektu, který může sloužit jako konstantní dopředného iterator sady. Je popsán sem jako synonymum pro typ definované implementací `T5`.

### <a name="example"></a>Příklad

```cpp
// std__unordered_set__unordered_set_const_local_iterator.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents " [c] [b] [a]"
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << " [" << *it << "]";
    std::cout << std::endl;

    // inspect bucket containing 'a'
    Myset::const_local_iterator lit = c1.begin(c1.bucket('a'));
    std::cout << " [" << *lit << "]";

    return (0);
}
```

```Output
 [c] [b] [a]
 [a]
```

## <a name="const_pointer"></a>  unordered_set::const_pointer

Typ konstantního ukazatele na prvek

```cpp
typedef Alloc::const_pointer const_pointer;
```

### <a name="remarks"></a>Poznámky

Popisuje typ objektu, který může sloužit jako konstantní ukazatel na element řízené sekvenci.

### <a name="example"></a>Příklad

```cpp
// std__unordered_set__unordered_set_const_pointer.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents " [c] [b] [a]"
    for (Myset::iterator it = c1.begin(); it != c1.end(); ++it)
    {
        Myset::const_pointer p = &*it;
        std::cout << " [" << *p << "]";
    }
    std::cout << std::endl;

    return (0);
}
```

```Output
 [c] [b] [a]
```

## <a name="const_reference"></a>  unordered_set::const_reference

Typ konstantního odkazu na prvek

```cpp
typedef Alloc::const_reference const_reference;
```

### <a name="remarks"></a>Poznámky

Popisuje typ objektu, který může sloužit jako konstantní odkaz na element řízené sekvenci.

### <a name="example"></a>Příklad

```cpp
// std__unordered_set__unordered_set_const_reference.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents " [c] [b] [a]"
    for (Myset::iterator it = c1.begin(); it != c1.end(); ++it)
    {
        Myset::const_reference ref = *it;
        std::cout << " [" << ref << "]";
    }
    std::cout << std::endl;

    return (0);
}
```

```Output
 [c] [b] [a]
```

## <a name="count"></a>  unordered_set::Count

Zjistí počet prvků odpovídající zadanému klíči.

```cpp
size_type count(const Key& keyval) const;
```

### <a name="parameters"></a>Parametry

`keyval` Hodnota klíče pro vyhledávání.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí počet prvků v rozsahu oddělená[unordered_set::equal_range](#equal_range)`(keyval)`.

### <a name="example"></a>Příklad

```cpp
// std__unordered_set__unordered_set_count.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents " [c] [b] [a]"
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << " [" << *it << "]";
    std::cout << std::endl;

    std::cout << "count('A') == " << c1.count('A') << std::endl;
    std::cout << "count('b') == " << c1.count('b') << std::endl;
    std::cout << "count('C') == " << c1.count('C') << std::endl;

    return (0);
}
```

```Output
 [c] [b] [a]
count('A') == 0
count('b') == 1
count('C') == 0
```

## <a name="difference_type"></a>  unordered_set::difference_type

Typ vzdálenosti se znaménkem mezi dvěma prvky

```cpp
typedef T3 difference_type;
```

### <a name="remarks"></a>Poznámky

Typ se znaménkem popisuje objekt, který může představovat rozdíl mezi dvěma prvky v řízené sekvenci adresy. Je popsán sem jako synonymum pro typ definované implementací `T3`.

### <a name="example"></a>Příklad

```cpp
// std__unordered_set__unordered_set_difference_type.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents " [c] [b] [a]"
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << " [" << *it << "]";
    std::cout << std::endl;

    // compute positive difference
    Myset::difference_type diff = 0;
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        ++diff;
    std::cout << "end()-begin() == " << diff << std::endl;

    // compute negative difference
    diff = 0;
    for (Myset::const_iterator it = c1.end(); it != c1.begin(); --it)
        --diff;
    std::cout << "begin()-end() == " << diff << std::endl;

    return (0);
}
```

```Output
 [c] [b] [a]
end()-begin() == 3
begin()-end() == -3
```

## <a name="emplace"></a>  unordered_set::emplace

Vloží element sestavený na místě (žádné kopírování nebo přesunutí operací).

```cpp
template <class... Args>
pair<iterator, bool>
emplace(
Args&&... args);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|-|-|
|`args`|Argumenty předané vytvořit element, který má být vložena do unordered_set, pokud již obsahuje element, jehož hodnota je ekvivalentně řazení.|

### <a name="return-value"></a>Návratová hodnota

A `pair` jejichž `bool` součást vrátí hodnotu true, pokud došlo vložení a v případě false `unordered_set` už obsažený element, jehož klíč měl ekvivalentní hodnotu v pořadí, jejichž součástí iterator vrátí adresu tam, kde je to nový Element vložení nebo kde byl element již nachází.

Pro přístup k iterator součást pár `pr` vrácené funkcí tento člen, použijte `pr.first`a pokud chcete ho dereference, použijte `*(pr.first)`. Abyste měli přístup `bool` součásti z dvojice `pr` vrácené funkcí tento člen, použijte `pr.second`.

### <a name="remarks"></a>Poznámky

Pomocí této funkce jsou zneplatněny žádné iterátory nebo odkazy.

Během vkládání Pokud je vyvolána výjimku, ale nedochází v kontejneru funkce hash, kontejneru nezměnil. Pokud je vyvolána výjimka ve funkci hash, výsledek není definován.

Příklad kódu, najdete v části[set::emplace](../standard-library/set-class.md#emplace).

## <a name="emplace_hint"></a>  unordered_set::emplace_hint

Vloží element sestavený na místě (žádné kopírování nebo přesunutí operací), s pomocným parametrem umístění.

```cpp
template <class... Args>
iterator emplace_hint(
const_iteratorwhere,
Args&&... args);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|-|-|
|`args`|Argumenty předané vytvořit element vložit do unordered_set – Pokud unordered_set již obsahuje daný element nebo obecně platí, pokud ji už obsahuje element, jehož klíč je ekvivalentně řazení.|
|`where`|Nápovědu ohledně místní zahájeno hledání správné bod vložení.|

### <a name="return-value"></a>Návratová hodnota

Iterátor do nově vloženou elementu.

Pokud vložení selhalo, protože element již existuje, vrátí iterovat do existujícího elementu.

### <a name="remarks"></a>Poznámky

Pomocí této funkce jsou zneplatněny žádné iterátory nebo odkazy.

Během vkládání Pokud je vyvolána výjimku, ale nedochází v kontejneru funkce hash, kontejneru nezměnil. Pokud je vyvolána výjimka ve funkci hash, výsledek není definován.

Příklad kódu, najdete v části[set::emplace_hint](../standard-library/set-class.md#emplace_hint).

## <a name="empty"></a>  unordered_set::Empty

Zkouší, zda nejsou přítomny žádné prvky.

```cpp
bool empty() const;
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí hodnotu true pro prázdný řízené sekvenci.

### <a name="example"></a>Příklad

```cpp
// std__unordered_set__unordered_set_empty.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents " [c] [b] [a]"
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << " [" << *it << "]";
    std::cout << std::endl;

    // clear the container and reinspect
    c1.clear();
    std::cout << "size == " << c1.size() << std::endl;
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;
    std::cout << std::endl;

    c1.insert('d');
    c1.insert('e');

    // display contents " [e] [d]"
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << " [" << *it << "]";
    std::cout << std::endl;

    std::cout << "size == " << c1.size() << std::endl;
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;

    return (0);
}
```

```Output
 [c] [b] [a]
size == 0
empty() == true
 [e] [d]
size == 2
empty() == false
```

## <a name="end"></a>  unordered_set::end

Určuje konec řízené sekvence.

```cpp
iterator end();

const_iterator end() const;

local_iterator end(size_type nbucket);

const_local_iterator end(size_type nbucket) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|-|-|
|`nbucket`|Počet kbelíků.|

### <a name="remarks"></a>Poznámky

První dva členské funkce vrátí dopředného iterator této body právě přesahuje za konec sekvenci. Poslední dva členské funkce vrátí dopředného iterator této body právě přesahuje za konec sady `nbucket`.

### <a name="example"></a>Příklad

```cpp
// std__unordered_set__unordered_set_end.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents " [c] [b] [a]"
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << " [" << *it << "]";
    std::cout << std::endl;

    // inspect last two items " [a] [b]"
    Myset::iterator it2 = c1.end();
    --it2;
    std::cout << " [" << *it2 << "]";
    --it2;
    std::cout << " [" << *it2 << "]";
    std::cout << std::endl;

    // inspect bucket containing 'a'
    Myset::const_local_iterator lit = c1.end(c1.bucket('a'));
    --lit;
    std::cout << " [" << *lit << "]";

    return (0);
}
```

```Output
 [c] [b] [a]
 [a] [b]
 [a]
```

## <a name="equal_range"></a>  unordered_set::equal_range

Najde rozsah, který odpovídá zadanému klíči.

```cpp
std::pair<iterator, iterator>
equal_range(const Key& keyval);

std::pair<const_iterator, const_iterator>
equal_range(const Key& keyval) const;
```

### <a name="parameters"></a>Parametry

`keyval` Hodnota klíče pro vyhledávání.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí pár iterátory `X` tak, aby`[X.first, X.second)` vymezuje pouze tyto elementy řízené sekvenci, které mají ekvivalentní řazení s `keyval`. Pokud neexistuje žádný takový prvek, jsou obě iterátory `end()`.

### <a name="example"></a>Příklad

```cpp
// std__unordered_set__unordered_set_equal_range.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents " [c] [b] [a]"
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << " [" << *it << "]";
    std::cout << std::endl;

    // display results of failed search
    std::pair<Myset::iterator, Myset::iterator> pair1 =
    c1.equal_range('x');
    std::cout << "equal_range('x'):";
    for (; pair1.first != pair1.second; ++pair1.first)
        std::cout << " [" << *pair1.first << "]";
    std::cout << std::endl;

    // display results of successful search
    pair1 = c1.equal_range('b');
    std::cout << "equal_range('b'):";
    for (; pair1.first != pair1.second; ++pair1.first)
        std::cout << " [" << *pair1.first << "]";
    std::cout << std::endl;

    return (0);
}
```

```Output
 [c] [b] [a]
equal_range('x'):
equal_range('b'): [b]
```

## <a name="erase"></a>  unordered_set::Erase

Odebere element nebo rozsah elementů v unordered_set ze zadaných pozic nebo odebere prvky, které odpovídají zadaným klíčem.

```cpp
iterator erase(const_iterator Where);

iterator erase(const_iterator First, const_iterator Last);

size_type erase(const key_type& Key);
```

### <a name="parameters"></a>Parametry

`Where` Pozice elementu, který chcete odebrat.

`First` Pozice prvního elementu, který chcete odebrat.

`Last` Pozice bezprostředně za posledním elementem odeberou.

`Key` Hodnota klíče elementů odeberou.

### <a name="return-value"></a>Návratová hodnota

Pro první dva členské funkce obousměrné iterator, označí první prvek zbývající nad rámec žádné elementy, odebrat nebo element, který je konci unordered_set, pokud neexistuje žádný takový prvek.

Pro třetí – členská funkce vrátí počet prvků, které byly odebrány z unordered_set.

### <a name="remarks"></a>Poznámky

Příklad kódu, najdete v části[set::erase](../standard-library/set-class.md#erase).

## <a name="find"></a>  unordered_set::Find

Vyhledá prvek, který odpovídá zadanému klíči.

```cpp
const_iterator find(const Key& keyval) const;
```

### <a name="parameters"></a>Parametry

`keyval` Hodnota klíče pro vyhledávání.

### <a name="remarks"></a>Poznámky

Členské funkce vrátí hodnotu[unordered_set::equal_range](#equal_range)`(keyval).first`.

### <a name="example"></a>Příklad

```cpp
// std__unordered_set__unordered_set_find.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents " [c] [b] [a]"
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << " [" << *it << "]";
    std::cout << std::endl;

    // try to find and fail
    std::cout << "find('A') == "
    << std::boolalpha << (c1.find('A') != c1.end()) << std::endl;

    // try to find and succeed
    Myset::iterator it = c1.find('b');
    std::cout << "find('b') == "
    << std::boolalpha << (it != c1.end())
    << ": [" << *it << "]" << std::endl;

    return (0);
}
```

```Output
 [c] [b] [a]
find('A') == false
find('b') == true: [b]
```

## <a name="get_allocator"></a>  unordered_set::get_allocator

Získá uložený objekt alokátoru.

```cpp
Alloc get_allocator() const;
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí objekt uložené přidělení.

### <a name="example"></a>Příklad

```cpp
// std__unordered_set__unordered_set_get_allocator.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
typedef std::allocator<std::pair<const char, int> > Myalloc;
int main()
{
    Myset c1;

    Myset::allocator_type al = c1.get_allocator();
    std::cout << "al == std::allocator() is "
    << std::boolalpha << (al == Myalloc()) << std::endl;

    return (0);
}
```

```Output
al == std::allocator() is true
```

## <a name="hash"></a>  unordered_set::hash_function

Získá uložený objekt hashovací funkce.

```cpp
Hash hash_function() const;
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí objekt funkce uložené hodnoty hash.

### <a name="example"></a>Příklad

```cpp
// std__unordered_set__unordered_set_hash_function.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    Myset::hasher hfn = c1.hash_function();
    std::cout << "hfn('a') == " << hfn('a') << std::endl;
    std::cout << "hfn('b') == " << hfn('b') << std::endl;

    return (0);
}
```

```Output
hfn('a') == 1630279
hfn('b') == 1647086
```

## <a name="hasher"></a>  unordered_set::hasher

Typ hashovací funkce

```cpp
typedef Hash hasher;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro parametr šablony `Hash`.

### <a name="example"></a>Příklad

```cpp
// std__unordered_set__unordered_set_hasher.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    Myset::hasher hfn = c1.hash_function();
    std::cout << "hfn('a') == " << hfn('a') << std::endl;
    std::cout << "hfn('b') == " << hfn('b') << std::endl;

    return (0);
}
```

```Output
hfn('a') == 1630279
hfn('b') == 1647086
```

## <a name="insert"></a>  unordered_set::Insert

Vloží do unordered_set elementu nebo rozsahu prvků.

```cpp
// (1) single element
pair<iterator, bool> insert(const value_type& Val);

// (2) single element, perfect forwarded
template <class ValTy>
pair<iterator, bool> insert(ValTy&& Val);

// (3) single element with hint
iterator insert(const_iterator Where, const value_type& Val);

// (4) single element, perfect forwarded, with hint
template <class ValTy>
iterator insert(const_iterator Where, ValTy&& Val);

// (5) range
template <class InputIterator>
void insert(InputIterator First, InputIterator Last);

// (6) initializer list
void insert(initializer_list<value_type> IList);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|-|-|
|`Val`|Hodnota elementu, který má být vložena do unordered_set, pokud již obsahuje element, jehož klíč je ekvivalentně řazení.|
|`Where`|Místo zahájení vyhledání správného bodu vložení.|
|`ValTy`|Parametr šablony, která určuje typ argument, který unordered_set můžete použít k vytvoření element[value_type](../standard-library/map-class.md#value_type)a představuje výhodu předávání `Val` jako argument.|
|`First`|Pozice prvního prvku, který chcete zkopírovat.|
|`Last`|Pozice bezprostředně za posledním prvkem, který chcete zkopírovat.|
|`InputIterator`|Argument funkce šablony, který splňuje požadavky[vstupní iterator](../standard-library/input-iterator-tag-struct.md) který odkazuje na elementy typu, který slouží k vytvoření[value_type](../standard-library/map-class.md#value_type) objekty.|
|`IList`|[Initializer_list](../standard-library/initializer-list.md) ze kterého chcete kopírovat prvky.|

### <a name="return-value"></a>Návratová hodnota

Jedné položce členské funkce (1) a (2), vrátí[pár](../standard-library/pair-structure.md) jejichž `bool` součást je hodnota true, pokud došlo vložení a hodnotu false, pokud unordered_set už obsažený element, jehož klíč měl ekvivalentní hodnotu v řazení. Komponenta iterátoru dvojice návratové hodnoty odkazuje na nově vložený prvek, pokud má komponenta `bool` hodnotu true, nebo na existující prvek, pokud má komponenta `bool` hodnotu false.

Jeden element s nápovědu členské funkce, (3) a (4) vrátí iterátor, který odkazuje na umístění, kde nového elementu byl vložen do unordered_set nebo, pokud již existuje element s klíčem ekvivalentní, do existujícího elementu.

### <a name="remarks"></a>Poznámky

Touto funkcí nejsou zneplatněny žádné iterátory, ukazatele ani odkazy.

Pokud je při vložení pouze jednoho prvku vyvolána výjimka, ale nenastane v kontejneru funkce hash, stav kontejneru se nezmění. Pokud je vyvolána výjimka ve funkci hash, výsledek není definován. Pokud je při vkládání více prvků vyvolána výjimka, kontejner zůstane v neurčeném, ale platném stavu.

Pro přístup k komponenta iterator `pair` `pr` je vrácený jedné položce členské funkce, použijte `pr.first`; chcete dereference iterator v rámci vrácený pár, použijte`*pr.first`, budete elementu. Chcete-li přistupovat ke komponentě `bool`, použijte `pr.second`. Příklad naleznete v ukázce kódu dále v tomto článku.

[Value_type](../standard-library/map-class.md#value_type) kontejner je typedef, který patří do kontejneru a pro sadu, `unordered_set<V>::value_type` je typ `const V`.

Členská funkce rozsahu (5) vloží pořadí hodnot element do unordered_set, která odpovídá každý prvek řešené pomocí iterace v rozsahu `[First, Last)`; proto `Last` získat nevloží. Členská funkce kontejneru `end()` se vztahuje k pozici hned za posledním prvkem v kontejneru, například příkaz `s.insert(v.begin(), v.end());` se pokusí vložit všechny prvky `v` do `s`. Vkládají se pouze prvky, které v rozsahu obsahují jedinečné hodnoty. Duplicitní hodnoty jsou ignorovány. Chcete-li sledovat, které prvky jsou odmítnuty, použijte jednoprvkovou verzi funkce `insert`.

(6) používá funkce člena inicializátoru seznamu[initializer_list](../standard-library/initializer-list.md) chcete zkopírovat do unordered_set elementy.

Pro vkládání elementu sestavený na místě – to znamená, se provádí žádné operace kopírování nebo přesunutí – najdete v části[set::emplace](../standard-library/set-class.md#emplace) a[set::emplace_hint](../standard-library/set-class.md#emplace_hint).

Příklad kódu, najdete v části[set::insert](../standard-library/set-class.md#insert).

## <a name="iterator"></a>  unordered_set::iterator

Typ, který poskytuje konstanta[dopředného iterator](../standard-library/forward-iterator-tag-struct.md) který může číst elementů v unordered_set.

```cpp
typedef implementation-defined iterator;
```

### <a name="example"></a>Příklad

Podívejte se na příklad pro[začít](../standard-library/set-class.md#begin) příklad toho, jak deklarace a používání**iterator**.

## <a name="key_eq"></a>  unordered_set::key_eq

Získá uložený objekt funkce porovnání.

```cpp
Pred key_eq() const;
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí objekt funkce uložené porovnání.

### <a name="example"></a>Příklad

```cpp
// std__unordered_set__unordered_set_key_eq.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    Myset::key_equal cmpfn = c1.key_eq();
    std::cout << "cmpfn('a', 'a') == "
    << std::boolalpha << cmpfn('a', 'a') << std::endl;
    std::cout << "cmpfn('a', 'b') == "
    << std::boolalpha << cmpfn('a', 'b') << std::endl;

    return (0);
}
```

```Output
cmpfn('a', 'a') == true
cmpfn('a', 'b') == false
```

## <a name="key_equal"></a>  unordered_set::key_equal

Typ funkce porovnání

```cpp
typedef Pred key_equal;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro parametr šablony `Pred`.

### <a name="example"></a>Příklad

```cpp
// std__unordered_set__unordered_set_key_equal.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    Myset::key_equal cmpfn = c1.key_eq();
    std::cout << "cmpfn('a', 'a') == "
    << std::boolalpha << cmpfn('a', 'a') << std::endl;
    std::cout << "cmpfn('a', 'b') == "
    << std::boolalpha << cmpfn('a', 'b') << std::endl;

    return (0);
}
```

```Output
cmpfn('a', 'a') == true
cmpfn('a', 'b') == false
```

## <a name="key_type"></a>  unordered_set::key_type

Typ klíče řazení

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro parametr šablony `Key`.

### <a name="example"></a>Příklad

```cpp
// std__unordered_set__unordered_set_key_type.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents " [c] [b] [a]"
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << " [" << *it << "]";
    std::cout << std::endl;

    // add a value and reinspect
    Myset::key_type key = 'd';
    Myset::value_type val = key;
    c1.insert(val);

    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << " [" << *it << "]";
    std::cout << std::endl;

    return (0);
}
```

```Output
 [c] [b] [a]
 [d] [c] [b] [a]
```

## <a name="load_factor"></a>  unordered_set::load_factor

Spočítá průměrný počet prvků na kbelík.

```cpp
float load_factor() const;
```

### <a name="remarks"></a>Poznámky

Členské funkce vrátí hodnotu`(float)`[unordered_set::size](#size)`() / (float)`[unordered_set::bucket_count](#bucket_count)`()`, průměrný počet elementy pro sady.

### <a name="example"></a>Příklad

```cpp
// std__unordered_set__unordered_set_load_factor.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents " [c] [b] [a]"
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << " [" << *it << "]";
    std::cout << std::endl;

    // inspect current parameters
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_bucket_count() == "
    << c1.max_bucket_count() << std::endl;
    std::cout << "max_load_factor() == "
    << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

    // change max_load_factor and redisplay
    c1.max_load_factor(0.10f);
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_bucket_count() == "
    << c1.max_bucket_count() << std::endl;
    std::cout << "max_load_factor() == "
    << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

    // rehash and redisplay
    c1.rehash(100);
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_bucket_count() == "
    << c1.max_bucket_count() << std::endl;
    std::cout << "max_load_factor() == "
    << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

    return (0);
}
```

```Output
 [c] [b] [a]
bucket_count() == 8
load_factor() == 0.375
max_bucket_count() == 8
max_load_factor() == 4

bucket_count() == 8
load_factor() == 0.375
max_bucket_count() == 8
max_load_factor() == 0.1

bucket_count() == 128
load_factor() == 0.0234375
max_bucket_count() == 128
max_load_factor() == 0.1
```

## <a name="local_iterator"></a>  unordered_set::local_iterator

Typ sady iterator.

```cpp
typedef T4 local_iterator;
```

### <a name="remarks"></a>Poznámky

Popisuje typ objektu, který může sloužit jako dopředného iterator sady. Je popsán sem jako synonymum pro typ definované implementací `T4`.

### <a name="example"></a>Příklad

```cpp
// std__unordered_set__unordered_set_local_iterator.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents " [c] [b] [a]"
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << " [" << *it << "]";
    std::cout << std::endl;

    // inspect bucket containing 'a'
    Myset::local_iterator lit = c1.begin(c1.bucket('a'));
    std::cout << " [" << *lit << "]";

    return (0);
}
```

```Output
 [c] [b] [a]
 [a]
```

## <a name="max_bucket_count"></a>  unordered_set::max_bucket_count

Získá maximální počet kbelíků.

```cpp
size_type max_bucket_count() const;
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí maximální počet intervalů, které jsou aktuálně povoleny.

### <a name="example"></a>Příklad

```cpp
// std__unordered_set__unordered_set_max_bucket_count.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents " [c] [b] [a]"
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << " [" << *it << "]";
    std::cout << std::endl;

    // inspect current parameters
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_bucket_count() == "
    << c1.max_bucket_count() << std::endl;
    std::cout << "max_load_factor() == "
    << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

    // change max_load_factor and redisplay
    c1.max_load_factor(0.10f);
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_bucket_count() == "
    << c1.max_bucket_count() << std::endl;
    std::cout << "max_load_factor() == "
    << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

    // rehash and redisplay
    c1.rehash(100);
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_bucket_count() == "
    << c1.max_bucket_count() << std::endl;
    std::cout << "max_load_factor() == "
    << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

    return (0);
}
```

```Output
 [c] [b] [a]
bucket_count() == 8
load_factor() == 0.375
max_bucket_count() == 8
max_load_factor() == 4

bucket_count() == 8
load_factor() == 0.375
max_bucket_count() == 8
max_load_factor() == 0.1

bucket_count() == 128
load_factor() == 0.0234375
max_bucket_count() == 128
max_load_factor() == 0.1
```

## <a name="max_load_factor"></a>  unordered_set::max_load_factor

Získá nebo nastaví maximální počet prvků na kbelík.

```cpp
float max_load_factor() const;

void max_load_factor(float factor);
```

### <a name="parameters"></a>Parametry

`factor` Na nové faktor maximální zatížení.

### <a name="remarks"></a>Poznámky

První člen funkce vrátí Multi-Factor uložené maximální zatížení. Druhý členská funkce nahrazuje faktory uložené maximální zatížení s `factor`.

### <a name="example"></a>Příklad

```cpp
// std__unordered_set__unordered_set_max_load_factor.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents " [c] [b] [a]"
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << " [" << *it << "]";
    std::cout << std::endl;

    // inspect current parameters
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_bucket_count() == "
    << c1.max_bucket_count() << std::endl;
    std::cout << "max_load_factor() == "
    << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

    // change max_load_factor and redisplay
    c1.max_load_factor(0.10f);
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_bucket_count() == "
    << c1.max_bucket_count() << std::endl;
    std::cout << "max_load_factor() == "
    << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

    // rehash and redisplay
    c1.rehash(100);
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_bucket_count() == "
    << c1.max_bucket_count() << std::endl;
    std::cout << "max_load_factor() == "
    << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

    return (0);
}
```

```Output
 [c] [b] [a]
bucket_count() == 8
load_factor() == 0.375
max_bucket_count() == 8
max_load_factor() == 4

bucket_count() == 8
load_factor() == 0.375
max_bucket_count() == 8
max_load_factor() == 0.1

bucket_count() == 128
load_factor() == 0.0234375
max_bucket_count() == 128
max_load_factor() == 0.1
```

## <a name="max_size"></a>  unordered_set::max_size

Získá maximální velikost řízené sekvence.

```cpp
size_type max_size() const;
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí délku nejdelší pořadí, které můžete řídit objekt.

### <a name="example"></a>Příklad

```cpp
// std__unordered_set__unordered_set_max_size.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    std::cout << "max_size() == " << c1.max_size() << std::endl;

    return (0);
}
```

```Output
max_size() == 4294967295
```

## <a name="op_eq"></a>  unordered_set::Operator =

Zkopíruje tabulku hash.

```cpp
unordered_set& operator=(const unordered_set& right);

unordered_set& operator=(unordered_set&& right);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|-|-|
|`right`|[Unordered_set](../standard-library/unordered-set-class.md) se zkopírují `unordered_set`.|

### <a name="remarks"></a>Poznámky

Po vymazání v žádné stávající elementy `unordered_set`, `operator=` buď kopíruje nebo přesouvá obsah `right` do `unordered_set`.

### <a name="example"></a>Příklad

```cpp
// unordered_set_operator_as.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

int main( )
{
    using namespace std;
    unordered_set<int> v1, v2, v3;
    unordered_set<int>::iterator iter;

    v1.insert(10);

    cout << "v1 = " ;
    for (iter = v1.begin(); iter != v1.end(); iter++)
        cout << *iter << " ";
    cout << endl;

    v2 = v1;
    cout << "v2 = ";
    for (iter = v2.begin(); iter != v2.end(); iter++)
        cout << *iter << " ";
    cout << endl;

    // move v1 into v2
    v2.clear();
    v2 = move(v1);
    cout << "v2 = ";
    for (iter = v2.begin(); iter != v2.end(); iter++)
        cout << *iter << " ";
    cout << endl;
}
```

## <a name="pointer"></a>  unordered_set::Pointer

Typ ukazatele na prvek

```cpp
typedef Alloc::pointer pointer;
```

### <a name="remarks"></a>Poznámky

Popisuje typ objektu, který může sloužit jako ukazatel na element řízené sekvenci.

### <a name="example"></a>Příklad

```cpp
// std__unordered_set__unordered_set_pointer.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents " [c] [b] [a]"
    for (Myset::iterator it = c1.begin(); it != c1.end(); ++it)
    {
        Myset::key_type key = *it;
        Myset::pointer p = &key;
        std::cout << " [" << *p << "]";
    }
    std::cout << std::endl;

    return (0);
}
```

```Output
 [c] [b] [a]
```

## <a name="reference"></a>  unordered_set::Reference

Typ odkazu na prvek

```cpp
typedef Alloc::reference reference;
```

### <a name="remarks"></a>Poznámky

Popisuje typ objektu, který může sloužit jako odkaz na element řízené sekvenci.

### <a name="example"></a>Příklad

```cpp
// std__unordered_set__unordered_set_reference.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents " [c] [b] [a]"
    for (Myset::iterator it = c1.begin(); it != c1.end(); ++it)
    {
        Myset::key_type key = *it;
        Myset::reference ref = key;
        std::cout << " [" << ref << "]";
    }
    std::cout << std::endl;

    return (0);
}
```

```Output
 [c] [b] [a]
```

## <a name="rehash"></a>  unordered_set::rehash

Znovu vytvoří hashovací tabulku.

```cpp
void rehash(size_type nbuckets);
```

### <a name="parameters"></a>Parametry

`nbuckets` Požadovaného počtu kbelíků.

### <a name="remarks"></a>Poznámky

Členská funkce mění počet intervalů nejméně `nbuckets` a znovu sestaví zatřiďovací tabulce podle potřeby.

### <a name="example"></a>Příklad

```cpp
// std__unordered_set__unordered_set_rehash.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents " [c] [b] [a]"
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << " [" << *it << "]";
    std::cout << std::endl;

    // inspect current parameters
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_load_factor() == " << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

    // change max_load_factor and redisplay
    c1.max_load_factor(0.10f);
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_load_factor() == " << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

    // rehash and redisplay
    c1.rehash(100);
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_load_factor() == " << c1.max_load_factor() << std::endl;

    return (0);
}
```

```Output
 [c] [b] [a]
bucket_count() == 8
load_factor() == 0.375
max_load_factor() == 4

bucket_count() == 8
load_factor() == 0.375
max_load_factor() == 0.1

bucket_count() == 128
load_factor() == 0.0234375
max_load_factor() == 0.1
```

## <a name="size"></a>  unordered_set::size

Spočítá počet prvků.

```cpp
size_type size() const;
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí délku řízené sekvenci.

### <a name="example"></a>Příklad

```cpp
// std__unordered_set__unordered_set_size.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents " [c] [b] [a]"
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << " [" << *it << "]";
    std::cout << std::endl;

    // clear the container and reinspect
    c1.clear();
    std::cout << "size == " << c1.size() << std::endl;
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;
    std::cout << std::endl;

    c1.insert('d');
    c1.insert('e');

    // display contents " [e] [d]"
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << " [" << *it << "]";
    std::cout << std::endl;

    std::cout << "size == " << c1.size() << std::endl;
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;

    return (0);
}
```

```Output
 [c] [b] [a]
size == 0
empty() == true

[e] [d]
size == 2
empty() == false
```

## <a name="size_type"></a>  unordered_set::size_type

Typ vzdálenosti bez znaménka mezi dvěma prvky

```cpp
typedef T2 size_type;
```

### <a name="remarks"></a>Poznámky

Zadejte celé číslo bez znaménka popisuje objekt, který může představovat délka žádné řízené sekvenci. Je popsán sem jako synonymum pro typ definované implementací `T2`.

### <a name="example"></a>Příklad

```cpp
// std__unordered_set__unordered_set_size_type.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;
    Myset::size_type sz = c1.size();

    std::cout << "size == " << sz << std::endl;

    return (0);
}
```

```Output
size == 0
```

## <a name="swap"></a>  unordered_set::swap

Zamění obsah dvou kontejnerů.

```cpp
void swap(unordered_set& right);
```

### <a name="parameters"></a>Parametry

`right` Kontejner se Prohodit s.

### <a name="remarks"></a>Poznámky

Členská funkce prohození řízené pořadí mezi `*this` a `right`. Pokud [unordered_set::get_allocator](#get_allocator)`() == right.get_allocator()`tak neobsahuje konstantní včas, vyhodí výjimku pouze v důsledku kopírování objekt uložené vlastnosti typu `Tr`, a by způsobila neplatnost žádné odkazy na ukazatele, nebo iterátory, které určit elementů ve dvou řízené pořadí. Jinak provede několik element přiřazení a volá konstruktor úměrná počet elementů ve dvou řízené pořadí.

### <a name="example"></a>Příklad

```cpp
// std__unordered_set__unordered_set_swap.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents " [c] [b] [a]"
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << " [" << *it << "]";
    std::cout << std::endl;

    Myset c2;

    c2.insert('d');
    c2.insert('e');
    c2.insert('f');

    c1.swap(c2);

    // display contents " [f] [e] [d]"
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << " [" << *it << "]";
    std::cout << std::endl;

    swap(c1, c2);

    // display contents " [c] [b] [a]"
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << " [" << *it << "]";
    std::cout << std::endl;

    return (0);
}
```

```Output
 [c] [b] [a]
 [f] [e] [d]
 [c] [b] [a]
```

## <a name="unordered_set"></a>  unordered_set::unordered_set

Sestaví objekt kontejneru.

```cpp
unordered_set(const unordered_set& Right);

explicit unordered_set(
    size_typebucket_count = N0,
    const Hash& Hash = Hash(),
    const Comp& Comp = Comp(),
    const Allocator& Al = Alloc());

unordered_set(unordered_set&& Right);

unordered_set(initializer_list<Type> IList);

unordered_set(initializer_list<Type> IList, size_typebucket_count);

unordered_set(
    initializer_list<Type> IList,
    size_typebucket_count,
    const Hash& Hash);

unordered_set(
    initializer_list<Type> IList,
    size_typebucket_count,
    const Hash& Hash,
    const Comp& Comp);

unordered_set(
    initializer_list<Type> IList,
    size_typebucket_count,
    const Hash& Hash,
    const Comp& Comp,
    const Allocator& Al);

template <class InputIterator>
unordered_set(
    InputIteratorfirst,
    InputIteratorlast,
    size_typebucket_count = N0,
    const Hash& Hash = Hash(),
    const Comp& Comp = Comp(),
    const Allocator& Al = Alloc());
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|-|-|
|`InputIterator`|Typ iterátoru.|
|`Al`|Objekt alokátoru, který se má uložit.|
|`Comp`|Objekt funkce porovnání, který se má uložit.|
|`Hash`|Objekt hashovací funkce, který se má uložit.|
|`bucket_count`|Minimální počet kbelíků.|
|`Right`|Kontejner, který se má kopírovat.|
|`IList`|Initializer_list obsahující prvky pro kopírování.|

### <a name="remarks"></a>Poznámky

Určuje první konstruktor kopii pořadí řízené `Right`. Druhý konstruktor určuje prázdnou řízenou sekvenci. Třetí konstruktor určuje kopii pořadí přesunutím `Right` čtvrtý prostřednictvím osmého konstruktory použijte initializer_list k určení elementy pro kopírování. Deváté konstruktor vloží pořadí hodnot element`[first, last)`.

Všechny konstruktory také inicializují několik uložených hodnot. Pro konstruktor copy, hodnoty jsou získávány z `Right`. V opačném případě:

Minimální počet kbelíků je argument `bucket_count`, pokud existuje; jinak hodnota je výchozí hodnota popsané sem jako hodnota definované implementací `N0`.

Objekt funkce algoritmu hash je argument `Hash`, pokud existuje; jinak hodnota je `Hash()`.

Argument je objekt funkce porovnání `Comp`, pokud existuje; jinak hodnota je `Comp()`.

Je objekt allocator argument `Al`, pokud existuje; jinak hodnota, je `Alloc()`.

## <a name="value_type"></a>  unordered_set::value_type

Typ prvku

```cpp
typedef Key value_type;
```

### <a name="remarks"></a>Poznámky

Popisuje typ elementu řízené sekvenci.

### <a name="example"></a>Příklad

```cpp
// std__unordered_set__unordered_set_value_type.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents " [c] [b] [a]"
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << " [" << *it << "]";
    std::cout << std::endl;

    // add a value and reinspect
    Myset::key_type key = 'd';
    Myset::value_type val = key;
    c1.insert(val);

    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << " [" << *it << "]";
    std::cout << std::endl;

    return (0);
}
```

```Output
 [c] [b] [a]
 [d] [c] [b] [a]
```

## <a name="see-also"></a>Viz také

[<unordered_set>](../standard-library/unordered-set.md)<br/>
[Kontejnery](../cpp/containers-modern-cpp.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)<br/>
