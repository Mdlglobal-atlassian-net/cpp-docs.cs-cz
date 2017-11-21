---
title: "unordered_map – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- unordered_map/std::unordered_map
- unordered_map/std::unordered_map::allocator_type
- unordered_map/std::unordered_map::const_iterator
- unordered_map/std::unordered_map::const_local_iterator
- unordered_map/std::unordered_map::const_pointer
- unordered_map/std::unordered_map::const_reference
- unordered_map/std::unordered_map::difference_type
- unordered_map/std::unordered_map::hasher
- unordered_map/std::unordered_map::iterator
- unordered_map/std::unordered_map::key_equal
- unordered_map/std::unordered_map::key_type
- unordered_map/std::unordered_map::local_iterator
- unordered_map/std::unordered_map::mapped_type
- unordered_map/std::unordered_map::pointer
- unordered_map/std::unordered_map::reference
- unordered_map/std::unordered_map::size_type
- unordered_map/std::unordered_map::value_type
- unordered_map/std::unordered_map::at
- unordered_map/std::unordered_map::begin
- unordered_map/std::unordered_map::bucket
- unordered_map/std::unordered_map::bucket_count
- unordered_map/std::unordered_map::bucket_size
- unordered_map/std::unordered_map::cbegin
- unordered_map/std::unordered_map::cend
- unordered_map/std::unordered_map::clear
- unordered_map/std::unordered_map::count
- unordered_map/std::unordered_map::emplace
- unordered_map/std::unordered_map::emplace_hint
- unordered_map/std::unordered_map::empty
- unordered_map/std::unordered_map::end
- unordered_map/std::unordered_map::equal_range
- unordered_map/std::unordered_map::erase
- unordered_map/std::unordered_map::find
- unordered_map/std::unordered_map::get_allocator
- unordered_map/std::unordered_map::hash
- unordered_map/std::unordered_map::insert
- unordered_map/std::unordered_map::key_eq
- unordered_map/std::unordered_map::load_factor
- unordered_map/std::unordered_map::max_bucket_count
- unordered_map/std::unordered_map::max_load_factor
- unordered_map/std::unordered_map::max_size
- unordered_map/std::unordered_map::rehash
- unordered_map/std::unordered_map::size
- unordered_map/std::unordered_map::swap
- unordered_map/std::unordered_map::unordered_map
- unordered_map/std::unordered_map::hash_function
dev_langs: C++
helpviewer_keywords:
- std::unordered_map
- std::unordered_map::allocator_type
- std::unordered_map::const_iterator
- std::unordered_map::const_local_iterator
- std::unordered_map::const_pointer
- std::unordered_map::const_reference
- std::unordered_map::difference_type
- std::unordered_map::hasher
- std::unordered_map::iterator
- std::unordered_map::key_equal
- std::unordered_map::key_type
- std::unordered_map::local_iterator
- std::unordered_map::mapped_type
- std::unordered_map::pointer
- std::unordered_map::reference
- std::unordered_map::size_type
- std::unordered_map::value_type
- std::unordered_map::at
- std::unordered_map::begin
- std::unordered_map::bucket
- std::unordered_map::bucket_count
- std::unordered_map::bucket_size
- std::unordered_map::cbegin
- std::unordered_map::cend
- std::unordered_map::clear
- std::unordered_map::count
- std::unordered_map::emplace
- std::unordered_map::emplace_hint
- std::unordered_map::empty
- std::unordered_map::end
- std::unordered_map::equal_range
- std::unordered_map::erase
- std::unordered_map::find
- std::unordered_map::get_allocator
- std::unordered_map::hash
- std::unordered_map::insert
- std::unordered_map::key_eq
- std::unordered_map::load_factor
- std::unordered_map::max_bucket_count
- std::unordered_map::max_load_factor
- std::unordered_map::max_size
- std::unordered_map::rehash
- std::unordered_map::size
- std::unordered_map::swap
- std::unordered_map::unordered_map
- std::unordered_map::allocator_type
- std::unordered_map::const_iterator
- std::unordered_map::const_local_iterator
- std::unordered_map::const_pointer
- std::unordered_map::const_reference
- std::unordered_map::difference_type
- std::unordered_map::hasher
- std::unordered_map::iterator
- std::unordered_map::key_equal
- std::unordered_map::key_type
- std::unordered_map::local_iterator
- std::unordered_map::mapped_type
- std::unordered_map::pointer
- std::unordered_map::reference
- std::unordered_map::size_type
- std::unordered_map::value_type
- std::unordered_map::at
- std::unordered_map::begin
- std::unordered_map::bucket
- std::unordered_map::bucket_count
- std::unordered_map::bucket_size
- std::unordered_map::cbegin
- std::unordered_map::cend
- std::unordered_map::clear
- std::unordered_map::count
- std::unordered_map::emplace
- std::unordered_map::emplace_hint
- std::unordered_map::empty
- std::unordered_map::end
- std::unordered_map::equal_range
- std::unordered_map::erase
- std::unordered_map::find
- std::unordered_map::get_allocator
- std::unordered_map::hash_function
- std::unordered_map::insert
- std::unordered_map::key_eq
- std::unordered_map::load_factor
- std::unordered_map::max_bucket_count
- std::unordered_map::max_load_factor
- std::unordered_map::max_size
- std::unordered_map::rehash
- std::unordered_map::size
- std::unordered_map::swap
ms.assetid: 7cf7cfa1-16e7-461c-a9b2-3b8d8ec24e0d
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: d37edf7f526104fa0bb9333daebeba975e4076d4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="unorderedmap-class"></a>unordered_map – třída
Šablony třídy popisuje objekt, který určuje posloupnost různých délka elementy typu `std::pair<const Key, Ty>`. Sekvence je slabě seřazená podle funkce hash, která sekvenci rozděluje do uspořádané sady dílčích sekvencí, které se nazývají kbelíky. V rámci každého kbelíku funkce porovnání určuje, zda má nějaká dvojice prvků odpovídající řazení. Každý prvek obsahuje dva objekty, klíč řazení a hodnotu. Sekvence je reprezentována způsobem, který umožňuje vyhledat, vložit a odebrat libovolný prvek s několika operacemi, které mohou být nezávislé na počtu prvků v sekvenci (konstantní čas), alespoň pokud všechny kbelíky mají přibližně stejnou délku. V nejhorším případě platí, že když jsou všechny prvky v jednom kbelíku, je počet operací úměrný počtu prvků v sekvenci (lineární čas). Vkládání prvků navíc nezruší platnost žádných iterátorů a odstranění prvku zruší platnost pouze těch iterátorů, které odkazují na odstraněný prvek.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <class Key,  
    class Ty,  
    class Hash = std::hash<Key>,  
    class Pred = std::equal_to<Key>,  
    class Alloc = std::allocator<std::pair<const Key, Ty>>>  
class unordered_map;  
```  
  
#### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Popis|  
|`Key`|Klíčový typ|  
|`Ty`|Mapovaný typ|  
|`Hash`|Typ objektu hashovací funkce|  
|`Pred`|Typ objektu funkce porovnání rovnosti|  
|`Alloc`|Třída alokátoru|  
  
## <a name="members"></a>Členové  
  
|||  
|-|-|  
|Definice typu|Popis|  
|[allocator_type –](#allocator_type)|Typ alokátoru pro správu úložiště|  
|[const_iterator –](#const_iterator)|Typ konstantního iterátoru řízené sekvence|  
|[const_local_iterator –](#const_local_iterator)|Typ konstantního iterátoru kbelíku řízené sekvence|  
|[const_pointer –](#const_pointer)|Typ konstantního ukazatele na prvek|  
|[const_reference –](#const_reference)|Typ konstantního odkazu na prvek|  
|[difference_type –](#difference_type)|Typ vzdálenosti se znaménkem mezi dvěma prvky|  
|[hasher](#hasher)|Typ hashovací funkce|  
|[iterator](#iterator)|Typ iterátoru řízené sekvence|  
|[key_equal –](#key_equal)|Typ funkce porovnání|  
|[key_type –](#key_type)|Typ klíče řazení|  
|[local_iterator –](#local_iterator)|Typ iterátoru kbelíku řízené sekvence|  
|[mapped_type –](#mapped_type)|Typ mapované hodnoty přiřazené ke každému klíči|  
|[ukazatele](#pointer)|Typ ukazatele na prvek|  
|[referenční dokumentace](#reference)|Typ odkazu na prvek|  
|[size_type –](#size_type)|Typ vzdálenosti bez znaménka mezi dvěma prvky|  
|[value_type](#value_type)|Typ prvku|  
  
|||  
|-|-|  
|Členská funkce|Popis|  
|[v](#at)|Vyhledá prvek se zadaným klíčem.|  
|[začít](#begin)|Určuje začátek řízené sekvence.|  
|[sady](#bucket)|Získá číslo kbelíku pro hodnotu klíče.|  
|[bucket_count –](#bucket_count)|Získá počet kbelíků.|  
|[bucket_size –](#bucket_size)|Získá velikost kbelíku.|  
|[cbegin –](#cbegin)|Určuje začátek řízené sekvence.|  
|[cend –](#cend)|Určuje konec řízené sekvence.|  
|[Vymazat](#clear)|Odebere všechny prvky.|  
|[počet](#count)|Zjistí počet prvků odpovídající zadanému klíči.|  
|[emplace –](#emplace)|Přidá prvek vytvořený v místě.|  
|[emplace_hint –](#emplace_hint)|Přidá prvek vytvořený v místě s nápovědou.|  
|[prázdný](#empty)|Zkouší, zda nejsou přítomny žádné prvky.|  
|[end](#end)|Určuje konec řízené sekvence.|  
|[equal_range –](#equal_range)|Najde rozsah, který odpovídá zadanému klíči.|  
|[vymazání](#erase)|Odebere prvky v určených pozicích.|  
|[Najít](#find)|Vyhledá prvek, který odpovídá zadanému klíči.|  
|[get_allocator –](#get_allocator)|Získá uložený objekt alokátoru.|  
|[hash_function –](#hash)|Získá uložený objekt hashovací funkce.|  
|[Vložení](#insert)|Přidá prvky.|  
|[key_eq –](#key_eq)|Získá uložený objekt funkce porovnání.|  
|[load_factor –](#load_factor)|Spočítá průměrný počet prvků na kbelík.|  
|[max_bucket_count –](#max_bucket_count)|Získá maximální počet kbelíků.|  
|[max_load_factor –](#max_load_factor)|Získá nebo nastaví maximální počet prvků na kbelík.|  
|[max_size –](#max_size)|Získá maximální velikost řízené sekvence.|  
|[rehash –](#rehash)|Znovu vytvoří hashovací tabulku.|  
|[velikost](#size)|Spočítá počet prvků.|  
|[swap](#swap)|Zamění obsah dvou kontejnerů.|  
|[unordered_map –](#unordered_map)|Sestaví objekt kontejneru.|  
  
|||  
|-|-|  
|Operátor|Popis|  
|[[unordered_map::Operator]](#op_at)|Vyhledá nebo vloží prvek se zadaným klíčem.|  
|[unordered_map::Operator =](#op_eq)|Zkopíruje tabulku hash.|  
  
## <a name="remarks"></a>Poznámky  
 Objekt řadí pořadí jimi řídí voláním dva uložené objekty, objekt funkci porovnání typu [unordered_map::key_equal](#key_equal) a objekt funkce algoritmu hash typu [unordered_map::hasher](#hasher). Přístup je první objekt uložené voláním členské funkce [unordered_map::key_eq](#key_eq)`()`; a přístup druhý objekt uložené voláním členské funkce [unordered_map::hash_function](#hash) `()`. Konkrétně pro všechny hodnoty `X` a `Y` typu `Key`, volání `key_eq()(X, Y)` vrátí hodnotu true pouze v případě hodnoty dvou argument ekvivalentní řazení; volání `hash_function()(keyval)` vypočítá distribuci hodnot typu `size_t`. Na rozdíl od třídy šablony [unordered_multimap – třída](../standard-library/unordered-multimap-class.md), objekt třídy šablony `unordered_map` zajistí, že `key_eq()(X, Y)` je vždy hodnotu false pro všechny dva elementy řízené sekvenci. (Klíče jsou jedinečné).  
  
 Objekt také uchovává faktor maximálního zatížení, který určuje maximální požadovaný průměrný počet prvků na kbelík. Pokud vkládání element způsobí [unordered_map::load_factor](#load_factor) `()` delší než maximální zatížení faktor, zvyšuje počet intervalů a podle potřeby znovu sestaví zatřiďovací tabulku kontejneru.  
  
 Skutečné pořadí prvků v řízené sekvenci závisí na hashovací funkci, funkci porovnání, pořadí vkládání, faktoru maximálního zatížení a aktuálním počtu kbelíků. Pořadí prvků v řízené sekvenci obecně nelze předvídat. Můžete si však vždy být jisti, že všechny dílčí množiny prvků, které mají ekvivalentní řazení, v řízené sekvenci sousedí.  
  
 Objekt přiděluje a uvolní úložiště pro pořadí jimi řídí prostřednictvím objektu uložené allocator typu [unordered_map::allocator_type](#allocator_type). Takový objekt allocator musí mít stejné externí rozhraní jako objekt třídy šablony `allocator`. Všimněte si, že uložený objekt alokátoru není zkopírován při přiřazení objektu kontejneru.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<unordered_map >  
  
 **Namespace:** – std  
  
##  <a name="allocator_type"></a>unordered_map::allocator_type  
 Typ alokátoru pro správu úložiště  
  
```  
typedef Alloc allocator_type;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ je synonymum pro parametr šablony `Alloc`.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// std__unordered_map__unordered_map_allocator_type.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   
  
typedef std::unordered_map<char, int> Mymap;
typedef std::allocator<std::pair<const char, int> > Myalloc;
int main()
{
    Mymap c1;

    Mymap::allocator_type al = c1.get_allocator();
    std::cout << "al == std::allocator() is "
        << std::boolalpha << (al == Myalloc()) << std::endl;

    return (0);
}
  
```  
  
```Output  
al == std::allocator() is true  
```  
  
##  <a name="at"></a>unordered_map::AT  
 Vyhledá element v unordered_map se zadanou hodnotou klíče.  
  
```  
Ty& at(const Key& key);
const Ty& at(const Key& key) const;
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Popis|  
|`key`|Hodnota klíče najít.|  
  
### <a name="return-value"></a>Návratová hodnota  
 Odkaz na hodnotu dat nalezen prvek.  
  
### <a name="remarks"></a>Poznámky  
 Pokud není nalezena hodnota klíče argument, pak funkce vyvolá objekt třídy `out_of_range`.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// unordered_map_at.cpp  
// compile with: /EHsc  
#include <unordered_map>  
#include <iostream>  
  
typedef std::unordered_map<char, int> Mymap;   
typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // find and show elements  
    std::cout << "c1.at('a') == " << c1.at('a') << std::endl;
    std::cout << "c1.at('b') == " << c1.at('b') << std::endl;
    std::cout << "c1.at('c') == " << c1.at('c') << std::endl;

    return (0);
}  
```  
  
##  <a name="begin"></a>unordered_map::begin  
 Označuje začátek řízené sekvenci nebo blok.  
  
```  
iterator begin();
const_iterator begin() const; 
local_iterator begin(size_type nbucket);
const_local_iterator begin(size_type nbucket) const;
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Popis|  
|`nbucket`|Počet kbelíků.|  
  
### <a name="remarks"></a>Poznámky  
 První dva členské funkce vrátí dopředného iterator této body v prvním elementem pořadí (nebo jenom přesahuje za konec prázdnou sekvencí). Poslední dva členské funkce vrátí dopředného iterator odkazující na první prvek sady `nbucket` (nebo jenom přesahuje za konec prázdný sady).  
  
### <a name="example"></a>Příklad  
  
```cpp  
// std__unordered_map__unordered_map_begin.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   
  
#typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"   
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    // inspect first two items " [c 3] [b 2]"   
    Mymap::iterator it2 = c1.begin();
    std::cout << " [" << it2->first << ", " << it2->second << "]";
    ++it2;
    std::cout << " [" << it2->first << ", " << it2->second << "]";
    std::cout << std::endl;

    // inspect bucket containing 'a'   
    Mymap::const_local_iterator lit = c1.begin(c1.bucket('a'));
    std::cout << " [" << lit->first << ", " << lit->second << "]";

    return (0);
}
```  
  
```Output  
[c, 3] [b, 2] [a, 1]  
[c, 3] [b, 2]  
[a, 1]  
```  
  
##  <a name="bucket"></a>unordered_map::Bucket  
 Získá číslo kbelíku pro hodnotu klíče.  
  
```  
size_type bucket(const Key& keyval) const;
```  
  
### <a name="parameters"></a>Parametry  
 `keyval`  
 Hodnota klíče pro mapování.  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce vrátí číslo sady aktuálně odpovídající hodnotě klíče `keyval`.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// std__unordered_map__unordered_map_bucket.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   
  
typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"   
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    // display buckets for keys   
    Mymap::size_type bs = c1.bucket('a');
    std::cout << "bucket('a') == " << bs << std::endl;
    std::cout << "bucket_size(" << bs << ") == " << c1.bucket_size(bs)
        << std::endl;

    return (0);
}
```  
  
```Output  
 [c, 3] [b, 2] [a, 1]  
bucket('a') == 7  
bucket_size(7) == 1  
```  
  
##  <a name="bucket_count"></a>unordered_map::bucket_count  
 Získá počet kbelíků.  
  
```  
size_type bucket_count() const;
```  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce vrátí aktuální počet intervalů.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// std__unordered_map__unordered_map_bucket_count.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   
  
typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"   
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
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
[c, 3][b, 2][a, 1]
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
  
##  <a name="bucket_size"></a>unordered_map::bucket_size  
 Získá velikost blok  
  
```  
size_type bucket_size(size_type nbucket) const;
```  
  
### <a name="parameters"></a>Parametry  
 `nbucket`  
 Počet kbelíků.  
  
### <a name="remarks"></a>Poznámky  
 Členské funkce vrátí velikost sady číslo `nbucket`.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// std__unordered_map__unordered_map_bucket_size.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   
  
typedef std::unordered_map<char, int> Mymap;   
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"   
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    // display buckets for keys   
    Mymap::size_type bs = c1.bucket('a');
    std::cout << "bucket('a') == " << bs << std::endl;
    std::cout << "bucket_size(" << bs << ") == " << c1.bucket_size(bs)
        << std::endl;

    return (0);
}
```  
  
```Output  
 [c, 3] [b, 2] [a, 1]  
bucket('a') == 7  
bucket_size(7) == 1  
```  
  
##  <a name="cbegin"></a>unordered_map::cbegin  
 Vrátí `const` iterator, která řeší prvním elementem v rozsahu.  
  
```  
const_iterator cbegin() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 A `const` iterator předat dál přístup, který odkazuje na první prvek rozsahu nebo umístění právě přesahuje za konec prázdného rozsahu (pro prázdného rozsahu, `cbegin() == cend()`).  
  
### <a name="remarks"></a>Poznámky  
 S návratovou hodnotou `cbegin`, nemůže být upravena elementů v rozsahu.  
  
 Můžete použít tuto funkci člen místě `begin()` – členská funkce zaručit, že je návratovou hodnotu `const_iterator`. Obvykle se používá ve spojení s [automaticky](../cpp/auto-cpp.md) odvození – klíčové slovo, zadejte, jak je znázorněno v následujícím příkladu. V příkladu, vezměte v úvahu `Container` upravitelná (jinou hodnotu než `const`) kontejneru libovolného typu, který podporuje `begin()` a `cbegin()`.  
  
```cpp  
auto i1 = Container.begin();
// i1 is Container<T>::iterator   
auto i2 = Container.cbegin();

// i2 is Container<T>::const_iterator  
```  
  
##  <a name="cend"></a>unordered_map::cend  
 Vrátí `const` iterator, která řeší umístění bezprostředně za posledním prvkem v rozsahu.  
  
```  
const_iterator cend() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 A `const` iterator předat dál přístup, který odkazuje právě přesahuje za konec rozsahu.  
  
### <a name="remarks"></a>Poznámky  
 `cend`slouží k ověření, zda iterovat uplynutí konec její rozsah.  
  
 Můžete použít tuto funkci člen místě `end()` – členská funkce zaručit, že je návratovou hodnotu `const_iterator`. Obvykle se používá ve spojení s [automaticky](../cpp/auto-cpp.md) odvození – klíčové slovo, zadejte, jak je znázorněno v následujícím příkladu. V příkladu, vezměte v úvahu `Container` upravitelná (jinou hodnotu než `const`) kontejneru libovolného typu, který podporuje `end()` a `cend()`.  
  
```cpp  
auto i1 = Container.end();
// i1 is Container<T>::iterator   
auto i2 = Container.cend();
// i2 is Container<T>::const_iterator  
```  
  
 Hodnoty vrácené `cend` by neměl být vyhodnoceny odkazy.  
  
##  <a name="clear"></a>unordered_map::clear  
 Odebere všechny prvky.  
  
```  
void clear();
```  
  
### <a name="remarks"></a>Poznámky  
 Volání členských funkcí [unordered_map::erase](#erase) `(` [unordered_map::begin](#begin) `(),` [unordered_map::end](#end)`())`.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// std__unordered_map__unordered_map_clear.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   
  
typedef std::unordered_map<char, int> Mymap;   
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"   
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    // clear the container and reinspect   
    c1.clear();
    std::cout << "size == " << c1.size() << std::endl;
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;
    std::cout << std::endl;

    c1.insert(Mymap::value_type('d', 4));
    c1.insert(Mymap::value_type('e', 5));

    // display contents " [e 5] [d 4]"   
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    std::cout << "size == " << c1.size() << std::endl;
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;

    return (0);
}
  
```  
  
```Output  
 [c, 3] [b, 2] [a, 1]  
size == 0  
empty() == true  
  
 [e, 5] [d, 4]  
size == 2  
empty() == false  
```  
  
##  <a name="const_iterator"></a>unordered_map::const_iterator  
 Typ konstantního iterátoru řízené sekvence  
  
```  
typedef T1 const_iterator;  
```  
  
### <a name="remarks"></a>Poznámky  
 Popisuje typ objektu, který může sloužit jako konstantní dopředného iterator pro řízené sekvenci. Je popsán sem jako synonymum pro typ definované implementací `T1`.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// std__unordered_map__unordered_map_const_iterator.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   
  
typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"   
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    return (0);
}
  
```  
  
```Output  
[c, 3] [b, 2] [a, 1]  
```  
  
##  <a name="const_local_iterator"></a>unordered_map::const_local_iterator  
 Typ konstantního iterátoru kbelíku řízené sekvence  
  
```  
typedef T5 const_local_iterator;  
```  
  
### <a name="remarks"></a>Poznámky  
 Popisuje typ objektu, který může sloužit jako konstantní dopředného iterator sady. Je popsán sem jako synonymum pro typ definované implementací `T5`.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// std__unordered_map__unordered_map_const_local_iterator.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"   
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    // inspect bucket containing 'a'   
    Mymap::const_local_iterator lit = c1.begin(c1.bucket('a'));
    std::cout << " [" << lit->first << ", " << lit->second << "]";

    return (0);
}
  
```  
  
```Output  
[c, 3] [b, 2] [a, 1]  
[a, 1]  
```  
  
##  <a name="const_pointer"></a>unordered_map::const_pointer  
 Typ konstantního ukazatele na prvek  
  
```  
typedef Alloc::const_pointer const_pointer;  
```  
  
### <a name="remarks"></a>Poznámky  
 Popisuje typ objektu, který může sloužit jako konstantní ukazatel na element řízené sekvenci.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// std__unordered_map__unordered_map_const_pointer.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"   
    for (Mymap::iterator it = c1.begin();
        it != c1.end(); ++it)
    {
        Mymap::const_pointer p = &*it;
        std::cout << " [" << p->first << ", " << p->second << "]";
    }
    std::cout << std::endl;

    return (0);
}
  
```  
  
```Output  
[c, 3] [b, 2] [a, 1]  
```  
  
##  <a name="const_reference"></a>unordered_map::const_reference  
 Typ konstantního odkazu na prvek  
  
```  
typedef Alloc::const_reference const_reference;  
```  
  
### <a name="remarks"></a>Poznámky  
 Popisuje typ objektu, který může sloužit jako konstantní odkaz na element řízené sekvenci.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// std__unordered_map__unordered_map_const_reference.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   
  
typedef std::unordered_map<char, int> Mymap;   
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"   
    for (Mymap::iterator it = c1.begin();
        it != c1.end(); ++it)
    {
        Mymap::const_reference ref = *it;
        std::cout << " [" << ref.first << ", " << ref.second << "]";
    }
    std::cout << std::endl;

    return (0);
}

```  
  
```Output  
[c, 3] [b, 2] [a, 1]  
```  
  
##  <a name="count"></a>unordered_map::Count  
 Zjistí počet prvků odpovídající zadanému klíči.  
  
```  
size_type count(const Key& keyval) const;
```  
  
### <a name="parameters"></a>Parametry  
 `keyval`  
 Hodnota klíče pro vyhledávání.  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce vrátí počet prvků v rozsahu oddělená [unordered_map::equal_range](#equal_range)`(keyval)`.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// std__unordered_map__unordered_map_count.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   
  
typedef std::unordered_map<char, int> Mymap;   
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"   
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    std::cout << "count('A') == " << c1.count('A') << std::endl;
    std::cout << "count('b') == " << c1.count('b') << std::endl;
    std::cout << "count('C') == " << c1.count('C') << std::endl;

    return (0);
}

```  
  
```Output  
 [c, 3] [b, 2] [a, 1]  
count('A') == 0  
count('b') == 1  
count('C') == 0  
```  
  
##  <a name="difference_type"></a>unordered_map::difference_type  
 Typ vzdálenosti se znaménkem mezi dvěma prvky  
  
```  
typedef T3 difference_type;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ se znaménkem popisuje objekt, který může představovat rozdíl mezi dvěma prvky v řízené sekvenci adresy. Je popsán sem jako synonymum pro typ definované implementací `T3`.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// std__unordered_map__unordered_map_difference_type.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   
  
typedef std::unordered_map<char, int> Mymap;   
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"   
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    // compute positive difference   
    Mymap::difference_type diff = 0;
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        ++diff;
    std::cout << "end()-begin() == " << diff << std::endl;

    // compute negative difference   
    diff = 0;
    for (Mymap::const_iterator it = c1.end();
        it != c1.begin(); --it)
        --diff;
    std::cout << "begin()-end() == " << diff << std::endl;

    return (0);
}
```  
  
```Output  
 [c, 3] [b, 2] [a, 1]  
end()-begin() == 3  
begin()-end() == -3  
```  
  
##  <a name="emplace"></a>unordered_map::emplace  
 Vloží element sestavený na místě (žádné kopírování nebo přesunutí operací) do unordered_map.  
  
```  
template <class... Args>  
pair<iterator, bool>  emplace( Args&&... args);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Popis|  
|`args`|Argumenty předané vytvořit element, který má být vložena do unordered_map, pokud již obsahuje element, jehož hodnota je ekvivalentně řazení.|  
  
### <a name="return-value"></a>Návratová hodnota  
 A `pair` jejichž `bool` součást vrátí hodnotu true, pokud došlo vložení a v případě false `unordered_map` už obsažený element, jehož klíč měl ekvivalentní hodnotu v pořadí, jejichž součástí iterator vrátí adresu tam, kde je to nový Element vložení nebo kde byl element již nachází.  
  
 Pro přístup k iterator součást pár `pr` vrácené funkcí tento člen, použijte `pr.first`a pokud chcete ho dereference, použijte `*(pr.first)`. Abyste měli přístup `bool` součásti z dvojice `pr` vrácené funkcí tento člen, použijte `pr.second`.  
  
### <a name="remarks"></a>Poznámky  
 Pomocí této funkce jsou zneplatněny žádné iterátory nebo odkazy.  
  
 Během vkládání Pokud je vyvolána výjimku, ale nedochází v kontejneru funkce hash, kontejneru nezměnil. Pokud je vyvolána výjimka ve funkci hash, výsledek není definován.  
  
 Příklad kódu, najdete v části [map::emplace](../standard-library/map-class.md#emplace).  
  
##  <a name="emplace_hint"></a>unordered_map::emplace_hint  
 Vloží element sestavený na místě (žádné kopírování nebo přesunutí operací), s pomocným parametrem umístění.  
  
```  
template <class... Args>  
iterator emplace_hint(const_iterator where, Args&&... args);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Popis|  
|`args`|Argumenty předané vytvořit element vložit do unordered_map – Pokud unordered_map již obsahuje daný element nebo obecně platí, pokud ji už obsahuje element, jehož klíč je ekvivalentně řazení.|  
|`where`|Nápovědu ohledně místní zahájeno hledání správné bod vložení.|  
  
### <a name="return-value"></a>Návratová hodnota  
 Iterátor do nově vloženou elementu.  
  
 Pokud vložení selhalo, protože element již existuje, vrátí iterovat do existujícího elementu.  
  
### <a name="remarks"></a>Poznámky  
 Pomocí této funkce jsou zneplatněny žádné odkazy.  
  
 Během vkládání Pokud je vyvolána výjimku, ale nedochází v kontejneru funkce hash, kontejneru nezměnil. Pokud je vyvolána výjimka ve funkci hash, výsledek není definován.  
  
 [Value_type](../standard-library/map-class.md#value_type) elementu je pár, aby bude použita hodnota elementu dvojici seřazené s první součást, která je rovna hodnotě klíče a druhá součást, která je rovna hodnotě dat prvku.  
  
 Příklad kódu, najdete v části [map::emplace_hint](../standard-library/map-class.md#emplace_hint).  
  
##  <a name="empty"></a>unordered_map::Empty  
 Zkouší, zda nejsou přítomny žádné prvky.  
  
```  
bool empty() const;
```  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce vrátí hodnotu true pro prázdný řízené sekvenci.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// std__unordered_map__unordered_map_empty.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   
  
typedef std::unordered_map<char, int> Mymap;   
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"   
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    // clear the container and reinspect   
    c1.clear();
    std::cout << "size == " << c1.size() << std::endl;
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;
    std::cout << std::endl;

    c1.insert(Mymap::value_type('d', 4));
    c1.insert(Mymap::value_type('e', 5));

    // display contents " [e 5] [d 4]"   
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    std::cout << "size == " << c1.size() << std::endl;
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;

    return (0);
}
```  
  
```Output  
 [c, 3] [b, 2] [a, 1]  
size == 0  
empty() == true  
  
 [e, 5] [d, 4]  
size == 2  
empty() == false  
```  
  
##  <a name="end"></a>unordered_map::end  
 Určuje konec řízené sekvence.  
  
```  
iterator end();
const_iterator end() const; 
local_iterator end(size_type nbucket);
const_local_iterator end(size_type nbucket) const;
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Popis|  
|`nbucket`|Počet kbelíků.|  
  
### <a name="remarks"></a>Poznámky  
 První dva členské funkce vrátí dopředného iterator této body právě přesahuje za konec sekvenci. Poslední dva členské funkce vrátí dopředného iterator této body právě přesahuje za konec sady `nbucket`.  
  
##  <a name="equal_range"></a>unordered_map::equal_range  
 Najde rozsah, který odpovídá zadanému klíči.  
  
```  
std::pair<iterator, iterator>  equal_range(const Key& keyval);
std::pair<const_iterator, const_iterator>  equal_range(const Key& keyval) const;
```  
  
### <a name="parameters"></a>Parametry  
 `keyval`  
 Hodnota klíče pro vyhledávání.  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce vrátí pár iterátory `X` tak, aby `[X.first, X.second)` vymezuje pouze tyto elementy řízené sekvenci, které mají ekvivalentní řazení s `keyval`. Pokud neexistuje žádný takový prvek, jsou obě iterátory `end()`.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// std__unordered_map__unordered_map_equal_range.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   
  
typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"   
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    // display results of failed search   
    std::pair<Mymap::iterator, Mymap::iterator> pair1 =
        c1.equal_range('x');
    std::cout << "equal_range('x'):";
    for (; pair1.first != pair1.second; ++pair1.first)
        std::cout << " [" << pair1.first->first
        << ", " << pair1.first->second << "]";
    std::cout << std::endl;

    // display results of successful search   
    pair1 = c1.equal_range('b');
    std::cout << "equal_range('b'):";
    for (; pair1.first != pair1.second; ++pair1.first)
        std::cout << " [" << pair1.first->first
        << ", " << pair1.first->second << "]";
    std::cout << std::endl;

    return (0);
}

```  
  
```Output  
 [c, 3] [b, 2] [a, 1]  
equal_range('x'):  
equal_range('b'): [b, 2]  
```  
  
##  <a name="erase"></a>unordered_map::Erase  
 Odebere element nebo rozsah elementů v unordered_map ze zadaných pozic nebo odebere prvky, které odpovídají zadaným klíčem.  
  
```  
iterator erase(const_iterator Where);
iterator erase(const_iterator First, const_iterator Last);
size_type erase(const key_type& Key);
```  
  
### <a name="parameters"></a>Parametry  
 `Where`  
 Pozice prvku, který má být odebrán.  
  
 `First`  
 Pozice prvního prvku, který má být odebrán.  
  
 `Last`  
 Pozice bezprostředně za posledním prvkem, který má být odebrán.  
  
 `Key`  
 Hodnota klíče prvků, které mají být odebrány.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pro první dva členské funkce obousměrné iterator, označí první prvek zbývající nad rámec žádné elementy, odebrat nebo element, který je konci mapy, pokud neexistuje žádný takový prvek.  
  
 Pro třetí – členská funkce vrátí počet prvků, které byly odebrány z unordered_map.  
  
### <a name="remarks"></a>Poznámky  
 Příklad kódu, najdete v části [map::erase](../standard-library/map-class.md#erase).  
  
##  <a name="find"></a>unordered_map::Find  
 Vyhledá prvek, který odpovídá zadanému klíči.  
  
```  
const_iterator find(const Key& keyval) const;
```  
  
### <a name="parameters"></a>Parametry  
 `keyval`  
 Hodnota klíče pro vyhledávání.  
  
### <a name="remarks"></a>Poznámky  
 Členské funkce vrátí hodnotu [unordered_map::equal_range](#equal_range)`(keyval).first`.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// std__unordered_map__unordered_map_find.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   
  
typedef std::unordered_map<char, int> Mymap;   
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"   
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    // try to find and fail   
    std::cout << "find('A') == "
        << std::boolalpha << (c1.find('A') != c1.end()) << std::endl;

    // try to find and succeed   
    Mymap::iterator it = c1.find('b');
    std::cout << "find('b') == "
        << std::boolalpha << (it != c1.end())
        << ": [" << it->first << ", " << it->second << "]" << std::endl;

    return (0);
}

```  
  
```Output  
 [c, 3] [b, 2] [a, 1]  
find('A') == false  
find('b') == true: [b, 2]  
```  
  
##  <a name="get_allocator"></a>unordered_map::get_allocator  
 Získá uložený objekt alokátoru.  
  
```  
Alloc get_allocator() const;
```  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce vrátí objekt uložené přidělení.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// std__unordered_map__unordered_map_get_allocator.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   
  
typedef std::unordered_map<char, int> Mymap;   
typedef std::allocator<std::pair<const char, int> > Myalloc;
int main()
{
    Mymap c1;

    Mymap::allocator_type al = c1.get_allocator();
    std::cout << "al == std::allocator() is "
        << std::boolalpha << (al == Myalloc()) << std::endl;

    return (0);
}

```  
  
```Output  
al == std::allocator() is true  
```  
  
##  <a name="hash"></a>unordered_map::hash_function  
 Získá uložený objekt hashovací funkce.  
  
```  
Hash hash_function() const;
```  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce vrátí objekt funkce uložené hodnoty hash.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// std__unordered_map__unordered_map_hash_function.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   
  
typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    Mymap::hasher hfn = c1.hash_function();
    std::cout << "hfn('a') == " << hfn('a') << std::endl;
    std::cout << "hfn('b') == " << hfn('b') << std::endl;

    return (0);
}
  
```  
  
```Output  
hfn('a') == 1630279  
hfn('b') == 1647086  
```  
  
##  <a name="hasher"></a>unordered_map::hasher  
 Typ hashovací funkce  
  
```  
typedef Hash hasher;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ je synonymum pro parametr šablony `Hash`.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// std__unordered_map__unordered_map_hasher.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   
  
typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    Mymap::hasher hfn = c1.hash_function();
    std::cout << "hfn('a') == " << hfn('a') << std::endl;
    std::cout << "hfn('b') == " << hfn('b') << std::endl;

    return (0);
}

```  
  
```Output  
hfn('a') == 1630279  
hfn('b') == 1647086  
```  
  
##  <a name="insert"></a>unordered_map::Insert  
 Vloží prvek nebo rozsah prvků do objektu unordered_map.  
  
```  
// (1) single element  
pair<iterator, bool> insert(    const value_type& Val);

 
// (2) single element, perfect forwarded  
template <class ValTy>  
pair<iterator, bool>  
insert(    ValTy&& Val);

 
// (3) single element with hint  
iterator insert(    const_iterator Where,  
    const value_type& Val);

 
// (4) single element, perfect forwarded, with hint  
template <class ValTy>  
iterator insert(    const_iterator Where,  
    ValTy&& Val);

 
// (5) range   
template <class InputIterator>   
void insert(InputIterator First,  
    InputIterator Last);

 
// (6) initializer list  
void insert(initializer_list<value_type>  
IList);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Popis|  
|`Val`|Hodnota prvku, který má být vložen do objektu unordered_map, pokud již neobsahuje prvek, jehož klíč je ekvivalentně seřazen.|  
|`Where`|Místo zahájení vyhledání správného bodu vložení.|  
|`ValTy`|Parametr šablony, která určuje typ argument, který unordered_map můžete použít k vytvoření element [value_type](../standard-library/map-class.md#value_type)a představuje výhodu předávání `Val` jako argument.|  
|`First`|Pozice prvního prvku, který chcete zkopírovat.|  
|`Last`|Pozice bezprostředně za posledním prvkem, který chcete zkopírovat.|  
|`InputIterator`|Argument funkce šablony, který splňuje požadavky [vstupní iterator](../standard-library/input-iterator-tag-struct.md) který odkazuje na elementy typu, který slouží k vytvoření [value_type](../standard-library/map-class.md#value_type) objekty.|  
|`IList`|[Initializer_list](../standard-library/initializer-list.md) ze kterého chcete kopírovat prvky.|  
  
### <a name="return-value"></a>Návratová hodnota  
 Jedné položce členské funkce (1) a (2), vrátí [pár](../standard-library/pair-structure.md) jejichž `bool` součást je hodnota true, pokud došlo vložení a hodnotu false, pokud unordered_map už obsažený element, jehož klíč měl ekvivalentní hodnotu v řazení. Komponenta iterátoru dvojice návratové hodnoty odkazuje na nově vložený prvek, pokud má komponenta `bool` hodnotu true, nebo na existující prvek, pokud má komponenta `bool` hodnotu false.  
  
 Jeden element s nápovědu členské funkce, (3) a (4) vrátí iterátor, který odkazuje na umístění, kde nového elementu byl vložen do unordered_map nebo, pokud již existuje element s klíčem ekvivalentní, do existujícího elementu.  
  
### <a name="remarks"></a>Poznámky  
 Touto funkcí nejsou zneplatněny žádné iterátory, ukazatele ani odkazy.  
  
 Pokud je při vložení pouze jednoho prvku vyvolána výjimka, ale nenastane v kontejneru funkce hash, stav kontejneru se nezmění. Pokud je vyvolána výjimka ve funkci hash, výsledek není definován. Pokud je při vkládání více prvků vyvolána výjimka, kontejner zůstane v neurčeném, ale platném stavu.  
  
 Pro přístup k komponenta iterator `pair` `pr` je vrácený jedné položce členské funkce, použijte `pr.first`; chcete dereference iterator v rámci vrácený pár, použijte `*pr.first`, budete elementu. Chcete-li přistupovat ke komponentě `bool`, použijte `pr.second`. Příklad naleznete v ukázce kódu dále v tomto článku.  
  
 [Value_type](../standard-library/map-class.md#value_type) kontejner je typedef, který patří do kontejneru a pro mapu, `map<K, V>::value_type` je `pair<const K, V>`. Hodnota prvku je seřazená dvojice, ve které je první komponenta rovna hodnotě klíče a druhá komponenta je rovna datové hodnotě prvku.  
  
 Členská funkce rozsahu (5) vloží pořadí hodnot element do unordered_map, která odpovídá každý prvek řešené pomocí iterace v rozsahu `[First, Last)`; proto `Last` získat nevloží. Členská funkce kontejneru `end()` se vztahuje k pozici hned za posledním prvkem v kontejneru, například příkaz `m.insert(v.begin(), v.end());` se pokusí vložit všechny prvky `v` do `m`. Vkládají se pouze prvky, které v rozsahu obsahují jedinečné hodnoty. Duplicitní hodnoty jsou ignorovány. Chcete-li sledovat, které prvky jsou odmítnuty, použijte jednoprvkovou verzi funkce `insert`.  
  
 (6) používá funkce člena inicializátoru seznamu [initializer_list](../standard-library/initializer-list.md) chcete zkopírovat do unordered_map elementy.  
  
 Pro vkládání elementu sestavený na místě – to znamená, se provádí žádné operace kopírování nebo přesunutí – najdete v části [unordered_map::emplace](#emplace) a [unordered_map::emplace_hint](#emplace_hint).  
  
 Příklad kódu, najdete v části [map::insert](../standard-library/map-class.md#insert).  
  
##  <a name="iterator"></a>unordered_map::iterator  
 Typ iterátoru řízené sekvence  
  
```  
typedef T0 iterator;  
```  
  
### <a name="remarks"></a>Poznámky  
 Popisuje typ objektu, který může sloužit jako dopředného iterator pro řízené sekvenci. Je popsán sem jako synonymum pro typ definované implementací `T0`.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// std__unordered_map__unordered_map_iterator.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   
  
typedef std::unordered_map<char, int> Mymap;   
int main()   
    {   
    Mymap c1;   
  
    c1.insert(Mymap::value_type('a', 1));   
    c1.insert(Mymap::value_type('b', 2));   
    c1.insert(Mymap::value_type('c', 3));   
  
// display contents " [c 3] [b 2] [a 1]"   
    for (Mymap::iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << it->first << ", " << it->second << "]";   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
[c, 3] [b, 2] [a, 1]  
```  
  
##  <a name="key_eq"></a>unordered_map::key_eq  
 Získá uložený objekt funkce porovnání.  
  
```  
Pred key_eq() const;
```  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce vrátí objekt funkce uložené porovnání.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// std__unordered_map__unordered_map_key_eq.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   
  
typedef std::unordered_map<char, int> Mymap;   
int main()   
    {   
    Mymap c1;   
  
    Mymap::key_equal cmpfn = c1.key_eq();   
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
  
##  <a name="key_equal"></a>unordered_map::key_equal  
 Typ funkce porovnání  
  
```  
typedef Pred key_equal;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ je synonymum pro parametr šablony `Pred`.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// std__unordered_map__unordered_map_key_equal.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   
  
typedef std::unordered_map<char, int> Mymap;   
int main()   
    {   
    Mymap c1;   
  
    Mymap::key_equal cmpfn = c1.key_eq();   
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
  
##  <a name="key_type"></a>unordered_map::key_type  
 Typ klíče řazení  
  
```  
typedef Key key_type;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ je synonymum pro parametr šablony `Key`.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// std__unordered_map__unordered_map_key_type.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   
  
typedef std::unordered_map<char, int> Mymap;   
int main()   
    {   
    Mymap c1;   
  
    c1.insert(Mymap::value_type('a', 1));   
    c1.insert(Mymap::value_type('b', 2));   
    c1.insert(Mymap::value_type('c', 3));   
  
// display contents " [c 3] [b 2] [a 1]"   
    for (Mymap::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << it->first << ", " << it->second << "]";   
    std::cout << std::endl;   
  
// add a value and reinspect   
    Mymap::key_type key = 'd';   
    Mymap::mapped_type mapped = 4;   
    Mymap::value_type val = Mymap::value_type(key, mapped);   
    c1.insert(val);   
  
    for (Mymap::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << it->first << ", " << it->second << "]";   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
[c, 3] [b, 2] [a, 1]  
[d, 4] [c, 3] [b, 2] [a, 1]  
```  
  
##  <a name="load_factor"></a>unordered_map::load_factor  
 Spočítá průměrný počet prvků na kbelík.  
  
```  
float load_factor() const;
```  
  
### <a name="remarks"></a>Poznámky  
 Členské funkce vrátí hodnotu `(float)` [unordered_map::size](#size)`() / (float)`[unordered_map::bucket_count](#bucket_count)`()`, průměrný počet elementy pro sady.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// std__unordered_map__unordered_map_load_factor.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   
  
typedef std::unordered_map<char, int> Mymap;   
int main()   
    {   
    Mymap c1;   
  
    c1.insert(Mymap::value_type('a', 1));   
    c1.insert(Mymap::value_type('b', 2));   
    c1.insert(Mymap::value_type('c', 3));   
  
// display contents " [c 3] [b 2] [a 1]"   
    for (Mymap::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << it->first << ", " << it->second << "]";   
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
 [c, 3] [b, 2] [a, 1]  
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
  
##  <a name="local_iterator"></a>unordered_map::local_iterator  
 Typ sady iterator.  
  
```  
typedef T4 local_iterator;  
```  
  
### <a name="remarks"></a>Poznámky  
 Popisuje typ objektu, který může sloužit jako dopředného iterator sady. Je popsán sem jako synonymum pro typ definované implementací `T4`.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// std__unordered_map__unordered_map_local_iterator.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   
  
typedef std::unordered_map<char, int> Mymap;   
int main()   
    {   
    Mymap c1;   
  
    c1.insert(Mymap::value_type('a', 1));   
    c1.insert(Mymap::value_type('b', 2));   
    c1.insert(Mymap::value_type('c', 3));   
  
// display contents " [c 3] [b 2] [a 1]"   
    for (Mymap::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << it->first << ", " << it->second << "]";   
    std::cout << std::endl;   
  
// inspect bucket containing 'a'   
    Mymap::local_iterator lit = c1.begin(c1.bucket('a'));   
    std::cout << " [" << lit->first << ", " << lit->second << "]";   
  
    return (0);   
    }  
  
```  
  
```Output  
[c, 3] [b, 2] [a, 1]  
[a, 1]  
```  
  
##  <a name="mapped_type"></a>unordered_map::mapped_type  
 Typ mapované hodnoty přiřazené ke každému klíči  
  
```  
typedef Ty mapped_type;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ je synonymum pro parametr šablony `Ty`.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// std__unordered_map__unordered_map_mapped_type.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   
  
typedef std::unordered_map<char, int> Mymap;   
int main()   
    {   
    Mymap c1;   
  
    c1.insert(Mymap::value_type('a', 1));   
    c1.insert(Mymap::value_type('b', 2));   
    c1.insert(Mymap::value_type('c', 3));   
  
// display contents " [c 3] [b 2] [a 1]"   
    for (Mymap::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << it->first << ", " << it->second << "]";   
    std::cout << std::endl;   
  
// add a value and reinspect   
    Mymap::key_type key = 'd';   
    Mymap::mapped_type mapped = 4;   
    Mymap::value_type val = Mymap::value_type(key, mapped);   
    c1.insert(val);   
  
    for (Mymap::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << it->first << ", " << it->second << "]";   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
[c, 3] [b, 2] [a, 1]  
[d, 4] [c, 3] [b, 2] [a, 1]  
```  
  
##  <a name="max_bucket_count"></a>unordered_map::max_bucket_count  
 Získá maximální počet kbelíků.  
  
```  
size_type max_bucket_count() const;
```  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce vrátí maximální počet intervalů, které jsou aktuálně povoleny.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// std__unordered_map__unordered_map_max_bucket_count.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   
  
typedef std::unordered_map<char, int> Mymap;   
int main()   
    {   
    Mymap c1;   
  
    c1.insert(Mymap::value_type('a', 1));   
    c1.insert(Mymap::value_type('b', 2));   
    c1.insert(Mymap::value_type('c', 3));   
  
// display contents " [c 3] [b 2] [a 1]"   
    for (Mymap::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << it->first << ", " << it->second << "]";   
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
 [c, 3] [b, 2] [a, 1]  
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
  
##  <a name="max_load_factor"></a>unordered_map::max_load_factor  
 Získá nebo nastaví maximální počet prvků na kbelík.  
  
```  
float max_load_factor() const;

 
void max_load_factor(float factor);
```  
  
### <a name="parameters"></a>Parametry  
 `factor`  
 Na nové faktor maximální zatížení.  
  
### <a name="remarks"></a>Poznámky  
 První člen funkce vrátí Multi-Factor uložené maximální zatížení. Druhý členská funkce nahrazuje faktory uložené maximální zatížení s `factor`.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// std__unordered_map__unordered_map_max_load_factor.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   
  
typedef std::unordered_map<char, int> Mymap;   
int main()   
    {   
    Mymap c1;   
  
    c1.insert(Mymap::value_type('a', 1));   
    c1.insert(Mymap::value_type('b', 2));   
    c1.insert(Mymap::value_type('c', 3));   
  
// display contents " [c 3] [b 2] [a 1]"   
    for (Mymap::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << it->first << ", " << it->second << "]";   
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
 [c, 3] [b, 2] [a, 1]  
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
  
##  <a name="max_size"></a>unordered_map::max_size  
 Získá maximální velikost řízené sekvence.  
  
```  
size_type max_size() const;
```  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce vrátí délku nejdelší pořadí, které můžete řídit objekt.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// std__unordered_map__unordered_map_max_size.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   
  
typedef std::unordered_map<char, int> Mymap;   
int main()   
    {   
    Mymap c1;   
  
    std::cout << "max_size() == " << c1.max_size() << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
max_size() == 536870911  
```  
  
##  <a name="op_at"></a>[unordered_map::Operator]  
 Vyhledá nebo vloží prvek se zadaným klíčem.  
  
```  
Ty& operator[](const Key& keyval);

Ty& operator[](Key&& keyval);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Popis|  
|`Keyval`|Hodnota klíče, kterou chcete vyhledat nebo vložit.|  
  
### <a name="return-value"></a>Návratová hodnota  
 Odkaz na hodnotu dat vloženého prvku.  
  
### <a name="remarks"></a>Poznámky  
 Pokud není nalezena hodnota klíče argumentu, je vložen spolu s výchozí hodnotou datového typu.  
  
 `operator[]`slouží k vložení elementy do mapy *m* pomocí *m*[_ *klíč*] = `DataValue`, kde `DataValue` je hodnota `mapped_type` elementu s hodnotu klíče \_ *klíč*.  
  
 Při použití `operator[]` Pokud chcete vložit elementy, vrácený odkaz neindikuje, zda je vložení Změna existující element nebo vytvořením nové. Členské funkce [najít](../standard-library/map-class.md#find) a [vložit](../standard-library/map-class.md#insert) slouží k určení, zda element se zadaným klíčem již nachází před vložení.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// std__unordered_map__unordered_map_operator_sub.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   
#include <string>  
  
typedef std::unordered_map<char, int> Mymap;   
int main()   
    {   
    Mymap c1;   
  
    c1.insert(Mymap::value_type('a', 1));   
    c1.insert(Mymap::value_type('b', 2));   
    c1.insert(Mymap::value_type('c', 3));   
  
// display contents " [c 3] [b 2] [a 1]"   
    for (Mymap::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << it->first << ", " << it->second << "]";   
    std::cout << std::endl;   
  
// try to find and fail   
    std::cout << "c1['A'] == " << c1['A'] << std::endl;   
  
// try to find and succeed   
    std::cout << "c1['a'] == " << c1['a'] << std::endl;   
  
// redisplay contents   
    for (Mymap::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << it->first << ", " << it->second << "]";   
    std::cout << std::endl;   
  
// insert by moving key  
    std::unordered_map<string, int> c2;  
    std::string str("abc");  
    std::cout << "c2[std::move(str)] == " << c2[std::move(str)] << std::endl;  
    std::cout << "c2["abc"] == " << c2["abc"] << std::endl;  
  
    return (0);   
    }  
  
```  
  
```Output  
 [c, 3] [b, 2] [a, 1]  
c1['A'] == 0  
c1['a'] == 1  
 [c, 3] [b, 2] [A, 0] [a, 1]  
c2[move(str)] == 0  
c2["abc"] == 1  
```  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce určuje iteraci `where` jako návratová hodnota [unordered_map::insert](#insert) `(` [unordered_map::value_type](#value_type)`(keyval, Ty())`. (Pokud neexistuje žádný takový prvek, vloží prvek se zadaným klíčem.) Pak vrátí odkaz na `(*where).second`.  
  
##  <a name="op_eq"></a>unordered_map::Operator =  
 Nahradí elementy tento unordered_map pomocí elementů z jiné unordered_map.  
  
```  
unordered_map& operator=(const unordered_map& right);

unordered_map& operator=(unordered_map&& right);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Popis|  
|`right`|Unordered_map –, který přiřazuje funkce operátor obsah z.|  
  
### <a name="remarks"></a>Poznámky  
 První verze zkopíruje všechny elementy ze `right` k této unordered_map.  
  
 Druhá verze přesune všechny elementy z `right` k této unordered_map.  
  
 Všechny prvky, které jsou v této unordered_map před `operator`= provede se zahodí.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// unordered_map_operator_as.cpp  
// compile with: /EHsc  
#include <unordered_map>  
#include <iostream>  
  
int main( )  
   {  
   using namespace std;  
   unordered_map<int, int> v1, v2, v3;  
   unordered_map<int, int>::iterator iter;  
  
   v1.insert(pair<int, int>(1, 10));  
  
   cout << "v1 = " ;  
   for (iter = v1.begin(); iter != v1.end(); iter++)  
      cout << iter->second << " ";  
   cout << endl;  
  
   v2 = v1;  
   cout << "v2 = ";  
   for (iter = v2.begin(); iter != v2.end(); iter++)  
      cout << iter->second << " ";  
   cout << endl;  
  
// move v1 into v2  
   v2.clear();  
   v2 = move(v1);  
   cout << "v2 = ";  
   for (iter = v2.begin(); iter != v2.end(); iter++)  
      cout << iter->second << " ";  
   cout << endl;  
   }  
```  
  
##  <a name="pointer"></a>unordered_map::Pointer  
 Typ ukazatele na prvek  
  
```  
typedef Alloc::pointer pointer;  
```  
  
### <a name="remarks"></a>Poznámky  
 Popisuje typ objektu, který může sloužit jako ukazatel na element řízené sekvenci.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// std__unordered_map__unordered_map_pointer.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   
  
typedef std::unordered_map<char, int> Mymap;   
int main()   
    {   
    Mymap c1;   
  
    c1.insert(Mymap::value_type('a', 1));   
    c1.insert(Mymap::value_type('b', 2));   
    c1.insert(Mymap::value_type('c', 3));   
  
// display contents " [c 3] [b 2] [a 1]"   
    for (Mymap::iterator it = c1.begin();   
        it != c1.end(); ++it)   
        {   
        Mymap::pointer p = &*it;   
        std::cout << " [" << p->first << ", " << p->second << "]";   
        }   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
[c, 3] [b, 2] [a, 1]  
```  
  
##  <a name="reference"></a>unordered_map::Reference  
 Typ odkazu na prvek  
  
```  
typedef Alloc::reference reference;  
```  
  
### <a name="remarks"></a>Poznámky  
 Popisuje typ objektu, který může sloužit jako odkaz na element řízené sekvenci.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// std__unordered_map__unordered_map_reference.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   
  
typedef std::unordered_map<char, int> Mymap;   
int main()   
    {   
    Mymap c1;   
  
    c1.insert(Mymap::value_type('a', 1));   
    c1.insert(Mymap::value_type('b', 2));   
    c1.insert(Mymap::value_type('c', 3));   
  
// display contents " [c 3] [b 2] [a 1]"   
    for (Mymap::iterator it = c1.begin();   
        it != c1.end(); ++it)   
        {   
        Mymap::reference ref = *it;   
        std::cout << " [" << ref.first << ", " << ref.second << "]";   
        }   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
[c, 3] [b, 2] [a, 1]  
```  
  
##  <a name="rehash"></a>unordered_map::rehash  
 Znovu vytvoří hashovací tabulku.  
  
```  
void rehash(size_type nbuckets);
```  
  
### <a name="parameters"></a>Parametry  
 `nbuckets`  
 Požadovaného počtu kbelíků.  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce mění počet intervalů nejméně `nbuckets` a znovu sestaví zatřiďovací tabulce podle potřeby.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// std__unordered_map__unordered_map_rehash.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   
  
typedef std::unordered_map<char, int> Mymap;   
int main()   
    {   
    Mymap c1;   
  
    c1.insert(Mymap::value_type('a', 1));   
    c1.insert(Mymap::value_type('b', 2));   
    c1.insert(Mymap::value_type('c', 3));   
  
// display contents " [c 3] [b 2] [a 1]"   
    for (Mymap::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << it->first << ", " << it->second << "]";   
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
 [c, 3] [b, 2] [a, 1]  
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
  
##  <a name="size"></a>unordered_map::size  
 Spočítá počet prvků.  
  
```  
size_type size() const;
```  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce vrátí délku řízené sekvenci.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// std__unordered_map__unordered_map_size.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   
  
typedef std::unordered_map<char, int> Mymap;   
int main()   
    {   
    Mymap c1;   
  
    c1.insert(Mymap::value_type('a', 1));   
    c1.insert(Mymap::value_type('b', 2));   
    c1.insert(Mymap::value_type('c', 3));   
  
// display contents " [c 3] [b 2] [a 1]"   
    for (Mymap::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << it->first << ", " << it->second << "]";   
    std::cout << std::endl;   
  
// clear the container and reinspect   
    c1.clear();   
    std::cout << "size == " << c1.size() << std::endl;   
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;   
    std::cout << std::endl;   
  
    c1.insert(Mymap::value_type('d', 4));   
    c1.insert(Mymap::value_type('e', 5));   
  
// display contents " [e 5] [d 4]"   
    for (Mymap::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << it->first << ", " << it->second << "]";   
    std::cout << std::endl;   
  
    std::cout << "size == " << c1.size() << std::endl;   
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
 [c, 3] [b, 2] [a, 1]  
size == 0  
empty() == true  
  
 [e, 5] [d, 4]  
size == 2  
empty() == false  
```  
  
##  <a name="size_type"></a>unordered_map::size_type  
 Typ vzdálenosti bez znaménka mezi dvěma prvky  
  
```  
typedef T2 size_type;  
```  
  
### <a name="remarks"></a>Poznámky  
 Zadejte celé číslo bez znaménka popisuje objekt, který může představovat délka žádné řízené sekvenci. Je popsán sem jako synonymum pro typ definované implementací `T2`.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// std__unordered_map__unordered_map_size_type.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   
  
typedef std::unordered_map<char, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    Mymap::size_type sz = c1.size();   
  
    std::cout << "size == " << sz << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
size == 0  
```  
  
##  <a name="swap"></a>unordered_map::swap  
 Zamění obsah dvou kontejnerů.  
  
```  
void swap(unordered_map& right);
```  
  
### <a name="parameters"></a>Parametry  
 `right`  
 Kontejner se Prohodit s.  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce prohození řízené pořadí mezi `*this` a `right`. Pokud [unordered_map::get_allocator](#get_allocator)`() == right.get_allocator()`tak neobsahuje konstantní včas, vyhodí výjimku pouze v důsledku kopírování objekt uložené vlastnosti typu `Tr`, a by způsobila neplatnost žádné odkazy na ukazatele, nebo iterátory, které určit elementů ve dvou řízené pořadí. Jinak provede několik element přiřazení a volá konstruktor úměrná počet elementů ve dvou řízené pořadí.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// std__unordered_map__unordered_map_swap.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   
  
typedef std::unordered_map<char, int> Mymap;   
int main()   
    {   
    Mymap c1;   
  
    c1.insert(Mymap::value_type('a', 1));   
    c1.insert(Mymap::value_type('b', 2));   
    c1.insert(Mymap::value_type('c', 3));   
  
// display contents " [c 3] [b 2] [a 1]"   
    for (Mymap::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << it->first << ", " << it->second << "]";   
    std::cout << std::endl;   
  
    Mymap c2;   
  
    c2.insert(Mymap::value_type('d', 4));   
    c2.insert(Mymap::value_type('e', 5));   
    c2.insert(Mymap::value_type('f', 6));   
  
    c1.swap(c2);   
  
// display contents " [f 6] [e 5] [d 4]"   
    for (Mymap::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << it->first << ", " << it->second << "]";   
    std::cout << std::endl;   
  
    swap(c1, c2);   
  
// display contents " [c 3] [b 2] [a 1]"   
    for (Mymap::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << it->first << ", " << it->second << "]";   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
[c, 3] [b, 2] [a, 1]  
[f, 6] [e, 5] [d, 4]  
[c, 3] [b, 2] [a, 1]  
```  
  
##  <a name="unordered_map"></a>unordered_map::unordered_map  
 Sestaví objekt kontejneru.  
  
```  
unordered_map(const unordered_map& Right);

explicit unordered_map(
    size_type Bucket_count = N0,  
    const Hash& Hash = Hash(),  
    const Comp& Comp = Comp(),  
    const Allocator& Al = Allocator());

unordered_map(unordered_map&& Right);
unordered_map(initializer_list<Type> IList);
unordered_map(initializer_list<Type> IList, size_type Bucket_count);

unordered_map(
    initializer_list<Type> IList,   
    size_type Bucket_count,   
    const Hash& Hash);

unordered_map(
    initializer_list<Type> IList,   
    size_type Bucket_count,   
    const Hash& Hash,  
    KeyEqual& equal);

unordered_map(
    initializer_list<Type> IList,   
    size_type Bucket_count,  
    const Hash& Hash,  
    KeyEqual& Equal  
    const Allocator& Al);

template <class InIt>  
unordered_map(
 InputIterator First,   
    InputIterator Last,  
    size_type Bucket_count = N0,  
    const Hash& Hash = Hash(),  
    const Comp& Comp = Comp(),  
    const Allocator& Al = Alloc());
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Popis|  
|`Al`|Objekt alokátoru, který se má uložit.|  
|`Comp`|Objekt funkce porovnání, který se má uložit.|  
|`Hash`|Objekt hashovací funkce, který se má uložit.|  
|`Bucket_count`|Minimální počet kbelíků.|  
|`Right`|Kontejner, který se má kopírovat.|  
|`First`||  
|`Last`||  
|`IList`|Initializer_list, který obsahuje prvky, které mají být zkopírovány.|  
  
### <a name="remarks"></a>Poznámky  
 Určuje první konstruktor kopii pořadí řízené `right`. Druhý konstruktor určuje prázdnou řízenou sekvenci. Třetí konstruktor vloží pořadí hodnot element `[first, last)`. Čtvrtý konstruktor určuje kopii pořadí přesunutím `right`.  
  
 Všechny konstruktory také inicializují několik uložených hodnot. Pro konstruktor copy, hodnoty jsou získávány z `Right`. V opačném případě:  
  
 Minimální počet kbelíků je argument `Bucket_count`, pokud existuje; jinak hodnota je výchozí hodnota popsané sem jako hodnota definované implementací `N0`.  
  
 Objekt funkce algoritmu hash je argument `Hash`, pokud existuje; jinak hodnota je `Hash()`.  
  
 Argument je objekt funkce porovnání `Comp`, pokud existuje; jinak hodnota je `Pred()`.  
  
 Je objekt allocator argument `Al`, pokud existuje; jinak hodnota, je `Alloc()`.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// std__unordered_map__unordered_map_construct.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   
#include <initializer_list>  
  
using namespace std;  
  
using Mymap = unordered_map<char, int>;  
  
int main()  
{  
    Mymap c1;  
  
    c1.insert(Mymap::value_type('a', 1));  
    c1.insert(Mymap::value_type('b', 2));  
    c1.insert(Mymap::value_type('c', 3));  
  
    // display contents " [c 3] [b 2] [a 1]"   
    for (const auto& c : c1) {  
        cout << " [" << c.first << ", " << c.second << "]";  
    }  
    cout << endl;  
  
    Mymap c2(8,  
        hash<char>(),  
        equal_to<char>(),  
        allocator<pair<const char, int> >());  
  
    c2.insert(Mymap::value_type('d', 4));  
    c2.insert(Mymap::value_type('e', 5));  
    c2.insert(Mymap::value_type('f', 6));  
  
    // display contents " [f 6] [e 5] [d 4]"   
    for (const auto& c : c2) {  
        cout << " [" << c.first << ", " << c.second << "]";  
    }  
    cout << endl;  
  
    Mymap c3(c1.begin(),  
        c1.end(),  
        8,  
        hash<char>(),  
        equal_to<char>(),  
        allocator<pair<const char, int> >());  
  
    // display contents " [c 3] [b 2] [a 1]"   
    for (const auto& c : c3) {  
        cout << " [" << c.first << ", " << c.second << "]";  
    }  
    cout << endl;  
  
    Mymap c4(move(c3));  
  
    // display contents " [c 3] [b 2] [a 1]"   
    for (const auto& c : c4) {  
        cout << " [" << c.first << ", " << c.second << "]";  
    }  
    cout << endl;  
    cout << endl;  
  
    // Construct with an initializer_list  
    unordered_map<int, char> c5({ { 5, 'g' }, { 6, 'h' }, { 7, 'i' }, { 8, 'j' } });  
    for (const auto& c : c5) {  
        cout << " [" << c.first << ", " << c.second << "]";  
    }  
    cout << endl;  
  
    // Initializer_list plus size  
    unordered_map<int, char> c6({ { 5, 'g' }, { 6, 'h' }, { 7, 'i' }, { 8, 'j' } }, 4);  
    for (const auto& c : c1) {  
        cout << " [" << c.first << ", " << c.second << "]";  
    }  
    cout << endl;  
    cout << endl;  
  
    // Initializer_list plus size and hash  
    unordered_map<int, char, hash<char>> c7(  
        { { 5, 'g' }, { 6, 'h' }, { 7, 'i' }, { 8, 'j' } },   
        4,   
        hash<char>()  
    );  
  
    for (const auto& c : c1) {  
        cout << " [" << c.first << ", " << c.second << "]";  
    }  
    cout << endl;  
  
    // Initializer_list plus size, hash, and key_equal  
    unordered_map<int, char, hash<char>, equal_to<char>> c8(  
        { { 5, 'g' }, { 6, 'h' }, { 7, 'i' }, { 8, 'j' } },   
        4,   
        hash<char>(),   
        equal_to<char>()  
    );  
  
    for (const auto& c : c1) {  
        cout << " [" << c.first << ", " << c.second << "]";  
    }  
    cout << endl;  
  
    // Initializer_list plus size, hash, key_equal, and allocator  
    unordered_map<int, char, hash<char>, equal_to<char>> c9(  
        { { 5, 'g' }, { 6, 'h' }, { 7, 'i' }, { 8, 'j' } },  
        4,  
        hash<char>(),  
        equal_to<char>(),  
        allocator<pair<const char, int> >()  
    );  
  
    for (const auto& c : c1) {  
        cout << " [" << c.first << ", " << c.second << "]";  
    }  
    cout << endl;  
}  
```  
  
```Output  
 [a, 1] [b, 2] [c, 3]
 [d, 4] [e, 5] [f, 6]
 [a, 1] [b, 2] [c, 3]
 [a, 1] [b, 2] [c, 3]

 [5, g] [6, h] [7, i] [8, j]
 [a, 1] [b, 2] [c, 3]

 [a, 1] [b, 2] [c, 3]
 [a, 1] [b, 2] [c, 3]
 [a, 1] [b, 2] [c, 3]
 ```  
  
##  <a name="value_type"></a>unordered_map::value_type  
 Typ prvku  
  
```  
typedef std::pair<const Key, Ty> value_type;  
```  
  
### <a name="remarks"></a>Poznámky  
 Popisuje typ elementu řízené sekvenci.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// std__unordered_map__unordered_map_value_type.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   
  
typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"   
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    // add a value and reinspect   
    Mymap::key_type key = 'd';
    Mymap::mapped_type mapped = 4;
    Mymap::value_type val = Mymap::value_type(key, mapped);
    c1.insert(val);

    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    return (0);
}

```  
  
```Output  
[c, 3] [b, 2] [a, 1]  
[d, 4] [c, 3] [b, 2] [a, 1]  
```  
  
## <a name="see-also"></a>Viz také  
 [< unordered_map >](../standard-library/unordered-map.md)   
 [Kontejnery](../cpp/containers-modern-cpp.md)   
 [Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Standardní C++ – referenční dokumentace knihoven](../standard-library/cpp-standard-library-reference.md)

