---
title: hash_multiset – třída
ms.date: 11/04/2016
f1_keywords:
- hash_set/stdext::hash_multiset
- hash_set/stdext::hash_multiset::allocator_type
- hash_set/stdext::hash_multiset::const_iterator
- hash_set/stdext::hash_multiset::const_pointer
- hash_set/stdext::hash_multiset::const_reference
- hash_set/stdext::hash_multiset::const_reverse_iterator
- hash_set/stdext::hash_multiset::difference_type
- hash_set/stdext::hash_multiset::iterator
- hash_set/stdext::hash_multiset::key_compare
- hash_set/stdext::hash_multiset::key_type
- hash_set/stdext::hash_multiset::pointer
- hash_set/stdext::hash_multiset::reference
- hash_set/stdext::hash_multiset::reverse_iterator
- hash_set/stdext::hash_multiset::size_type
- hash_set/stdext::hash_multiset::value_compare
- hash_set/stdext::hash_multiset::value_type
- hash_set/stdext::hash_multiset::begin
- hash_set/stdext::hash_multiset::cbegin
- hash_set/stdext::hash_multiset::cend
- hash_set/stdext::hash_multiset::clear
- hash_set/stdext::hash_multiset::count
- hash_set/stdext::hash_multiset::crbegin
- hash_set/stdext::hash_multiset::crend
- hash_set/stdext::hash_multiset::emplace
- hash_set/stdext::hash_multiset::emplace_hint
- hash_set/stdext::hash_multiset::empty
- hash_set/stdext::hash_multiset::end
- hash_set/stdext::hash_multiset::equal_range
- hash_set/stdext::hash_multiset::erase
- hash_set/stdext::hash_multiset::find
- hash_set/stdext::hash_multiset::get_allocator
- hash_set/stdext::hash_multiset::insert
- hash_set/stdext::hash_multiset::key_comp
- hash_set/stdext::hash_multiset::lower_bound
- hash_set/stdext::hash_multiset::max_size
- hash_set/stdext::hash_multiset::rbegin
- hash_set/stdext::hash_multiset::rend
- hash_set/stdext::hash_multiset::size
- hash_set/stdext::hash_multiset::swap
- hash_set/stdext::hash_multiset::upper_bound
- hash_set/stdext::hash_multiset::value_comp
helpviewer_keywords:
- stdext::hash_multiset
- stdext::hash_multiset::allocator_type
- stdext::hash_multiset::const_iterator
- stdext::hash_multiset::const_pointer
- stdext::hash_multiset::const_reference
- stdext::hash_multiset::const_reverse_iterator
- stdext::hash_multiset::difference_type
- stdext::hash_multiset::iterator
- stdext::hash_multiset::key_compare
- stdext::hash_multiset::key_type
- stdext::hash_multiset::pointer
- stdext::hash_multiset::reference
- stdext::hash_multiset::reverse_iterator
- stdext::hash_multiset::size_type
- stdext::hash_multiset::value_compare
- stdext::hash_multiset::value_type
- stdext::hash_multiset::begin
- stdext::hash_multiset::cbegin
- stdext::hash_multiset::cend
- stdext::hash_multiset::clear
- stdext::hash_multiset::count
- stdext::hash_multiset::crbegin
- stdext::hash_multiset::crend
- stdext::hash_multiset::emplace
- stdext::hash_multiset::emplace_hint
- stdext::hash_multiset::empty
- stdext::hash_multiset::end
- stdext::hash_multiset::equal_range
- stdext::hash_multiset::erase
- stdext::hash_multiset::find
- stdext::hash_multiset::get_allocator
- stdext::hash_multiset::insert
- stdext::hash_multiset::key_comp
- stdext::hash_multiset::lower_bound
- stdext::hash_multiset::max_size
- stdext::hash_multiset::rbegin
- stdext::hash_multiset::rend
- stdext::hash_multiset::size
- stdext::hash_multiset::swap
- stdext::hash_multiset::upper_bound
- stdext::hash_multiset::value_comp
ms.assetid: 0580397a-a76e-40ad-aea2-5c6f3a9d0a21
ms.openlocfilehash: 7881b1d6775206fbea40c3ba4b15572a6d4b3580
ms.sourcegitcommit: 4b0928a1a497648d0d327579c8262f25ed20d02e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2019
ms.locfileid: "72890087"
---
# <a name="hash_multiset-class"></a>hash_multiset – třída

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_multiset třída](../standard-library/unordered-multiset-class.md).

Třída kontejneru hash_multiset je rozšíření C++ standardní knihovny, které se používá pro úložiště a rychlé načítání dat z kolekce, ve které hodnoty prvků, které jsou obsaženy, slouží jako klíčové hodnoty a nejsou požadovány jako jedinečné.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Key, class Traits =hash_compare<Key, less <Key>>, class Allocator =allocator <Key>>
class hash_multiset
```

### <a name="parameters"></a>Parametry

\ *klíčů*
Typ dat prvku, který bude uložen v hash_multiset.

\ *vlastností*
Typ, který obsahuje dva objekty funkce, jedno z porovnání třídy, které je binární predikát schopný porovnat dvě hodnoty elementů jako klíče řazení pro určení jejich relativního pořadí a funkci hash, která je unárním predikátem mapování hodnot klíčů prvků na nepodepsané celá čísla typu `size_t`. Tento argument je nepovinný a `hash_compare<Key, less<Key> >` je výchozí hodnota.

\ *přidělování*
Typ, který představuje uložený objekt přidělování, který zapouzdřuje informace o přidělování hash_multiset's a navracení paměti. Tento argument je nepovinný a výchozí hodnota je `allocator<Key>`.

## <a name="remarks"></a>Poznámky

Hash_multiset je:

- Asociativní kontejner, což je kontejner proměnné velikosti, který podporuje efektivní načtení hodnoty prvku založené na přiřazené hodnotě klíče. Dále je to jednoduchý asociativní kontejner, protože jeho hodnoty prvku jsou jeho hodnoty klíče.

- Oboustranný, protože poskytuje obousměrný iterátor pro přístup k jeho prvkům.

- Hash, protože jeho prvky jsou seskupeny do kontejnerů na základě hodnoty funkce hash použité pro klíčové hodnoty prvků.

- Jedinečný v tom smyslu, že každý z jeho prvků musí mít jedinečný klíč. Vzhledem k tomu, že hash_multiset je také jednoduchý asociativní kontejner, jeho prvky jsou také jedinečné.

- Šablona třídy, protože funkce, které poskytuje, jsou obecné a nezávisle na konkrétním typu dat obsažených jako elementy nebo klíče. Datové typy použité pro prvky a klíče jsou místo toho zadány jako parametry v šabloně třídy společně s funkcí porovnání a alokátorem.

Hlavní výhodou použití algoritmu hash nad řazením je vyšší efektivita: úspěšné hashace provádí vložení, odstranění a vyhledává v konstantním průměrném čase v porovnání s časem, který je úměrný logaritmu počtu prvků v kontejneru pro řazení. technice. Hodnotu prvku v sadě nelze změnit přímo. Místo toho musíte odstranit staré hodnoty a vložit prvky s novými hodnotami.

Volba typu kontejneru by měla obecně vycházet z typu vyhledávání a vkládání vyžadovaného aplikací. Asociativní kontejnery s algoritmem hash jsou optimalizované pro operace vyhledávání, vkládání a odebírání. Členské funkce, které explicitně podporují tyto operace, jsou efektivní při použití s dobře navrženou funkcí hash a jejich provádění v čase s průměrnou konstantou a nezávisle na počtu prvků v kontejneru. Dobře navržená funkce hash vytváří jednotnou distribuci hodnot hash a minimalizuje počet kolizí, kde je zřejmé, že se vyskytne při mapování jedinečných klíčových hodnot na stejnou hodnotu hash. V nejhorším případě s nejhorší možnou funkcí hash je počet operací úměrný počtu prvků v sekvenci (lineární čas).

Hash_multiset by měl být asociativní kontejner výběru, pokud podmínky přidružování hodnot k jejich klíčům splňují požadavky aplikace. Prvky hash_multiset mohou být vícenásobné a slouží jako vlastní klíče řazení, takže klíče nejsou jedinečné. Model pro tento typ struktury je uspořádaný seznam slov, v němž se slova mohou vyskytovat více než jednou. Bylo překročeno více výskytů slov, takže hash_set by byla příslušná struktura kontejneru. Pokud byly jedinečné definice připojeny jako hodnoty k seznamu jedinečných klíčových slov, pak bude hash_map vhodnou strukturou, která bude tato data obsahovat. Pokud místo toho definice nejsou jedinečné, hash_multimap by byl kontejnerem volby.

Hash_multiset seřadí sekvenci, kterou řídí, voláním uloženého objektu hash znaků typu [value_compare](#value_compare). K tomuto uloženému objektu je možné přistupovat voláním členské funkce [key_comp](#key_comp). Takový objekt funkce se musí chovat stejně jako objekt třídy `hash_compare<Key, less<Key> >`. Konkrétně pro všechny hodnoty *klíče* typu `Key`volání `Trait(Key)` vypočítá distribuci hodnot typu `size_t`.

Obecně, tyto prvky musí být menší než srovnatelné pro toto pořadí, což znamená, že když jsou uvedeny dva prvky, může být stanoveno, zda jsou ekvivalentní (v tom smyslu, že ani jeden není menší než ten druhý), nebo že jeden je menší než druhý. To má za výsledek řazení mezi neekvivalentními prvky. Technicky je funkce porovnání binárním predikátem, který indukuje přísné slabé řazení, standardním matematickým způsobem. Binární predikát *f*( *x*, *y*) je objekt funkce, který má dva objekty argumentu x a y a návratovou hodnotu true nebo false. Řazení uložené na hash_multiset je přísné slabé seřazení, pokud je binární predikát Nereflexivní, antisymetrický a tranzitivní a je-li ekvivalence tranzitivní, kde jsou dva objekty x a y definovány jako ekvivalentní, když je v *f*( *x*, y).) a *f*( *y*, *x*) jsou false. Pokud silnější podmínka rovnosti mezi klíči nahradí ekvivalenci, stane se pořadí celkovým (v tom smyslu, že všechny prvky jsou uspořádány ve vztahu k sobě navzájem) a odpovídající klíče budou od sebe nerozeznatelné.

Skutečné pořadí prvků v řízené sekvenci závisí na funkci hash, funkci řazení a aktuální velikosti zatřiďovací tabulky uložené v objektu kontejneru. Nelze určit aktuální velikost zatřiďovací tabulky, takže nemůžete obecné předpovědět pořadí prvků v řízené sekvenci. Vkládání prvků nezruší platnost žádných iterátorů a odstranění prvků zruší platnost pouze těch iterátorů, které výslovně odkazovaly na odstraněné prvky.

Iterátor poskytnutý třídou hash_multiset je obousměrný iterátor, ale funkce členských funkcí INSERT a hash_multiset mají verze, které přebírají jako parametry šablony slabší vstupní iterátor, jehož požadavky na funkce jsou více minimální než Ty jsou zaručené třídou Obousměrných iterátorů. Různé koncepty iterátorů tvoří rodinu týkající se upřesnění jejich funkčnosti. Každý koncept iterátoru má vlastní hash_multiset požadavků a algoritmy, které s nimi pracují, musí omezit jejich předpoklady na požadavky poskytované tímto typem iterátoru. Lze předpokládat, že ke vstupnímu iterátoru lze přistoupit přes ukazatel pro odkazování na některý objekt a že může být zvýšen na další iterátor v pořadí. Jedná se o minimální hash_multiset funkce, ale stačí, abyste se mohli lépe spojit s rozsahem iterátorů [`first`, `last`) v kontextu funkcí členů třídy.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[hash_multiset](#hash_multiset)|Vytvoří `hash_multiset`, který je prázdný nebo který je kopií všech nebo částí jiných `hash_multiset`.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[allocator_type](#allocator_type)|Typ, který představuje třídu `allocator` pro objekt `hash_multiset`.|
|[const_iterator](#const_iterator)|Typ, který poskytuje obousměrný iterátor, který může číst prvek **const** v `hash_multiset`.|
|[const_pointer](#const_pointer)|Typ, který poskytuje ukazatel na prvek **const** v `hash_multiset`.|
|[const_reference](#const_reference)|Typ, který poskytuje odkaz na prvek **const** uložený v `hash_multiset` pro čtení a provádění operací **const** .|
|[const_reverse_iterator](#const_reverse_iterator)|Typ, který poskytuje obousměrný iterátor, který může číst libovolný prvek **const** v `hash_multiset`.|
|[difference_type](#difference_type)|Typ celého čísla se znaménkem, který poskytuje rozdíl mezi dvěma iterátory, které řeší prvky v rámci stejné `hash_multiset`.|
|[iterátor](#iterator)|Typ, který poskytuje obousměrný iterátor, který může číst nebo upravovat libovolný prvek v `hash_multiset`.|
|[key_compare](#key_compare)|Typ, který poskytuje objekt funkce, který může porovnat dva klíče řazení pro určení relativního pořadí dvou prvků v `hash_multiset`.|
|[key_type](#key_type)|Typ, který popisuje objekt uložený jako prvek `hash_set` v jeho kapacitě jako klíč řazení.|
|[ukazatele](#pointer)|Typ, který poskytuje ukazatel na prvek v `hash_multiset`.|
|[odkaz](#reference)|Typ, který poskytuje odkaz na prvek uložený v `hash_multiset`.|
|[reverse_iterator](#reverse_iterator)|Typ, který poskytuje obousměrný iterátor, který může číst nebo upravovat prvek v obráceném `hash_multiset`.|
|[size_type](#size_type)|Typ unsigned integer, který může představovat počet prvků v `hash_multiset`.|
|[value_compare](#value_compare)|Typ, který poskytuje dva objekty Functions, binární predikát porovnání třídy, který může porovnat dvě hodnoty prvku `hash_multiset` k určení jejich relativního pořadí a unární predikát, který prvky vyhodnotí.|
|[value_type](#value_type)|Typ, který popisuje objekt uložený jako prvek `hash_multiset` v jeho kapacitě jako hodnota.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[ifunctiondiscovery](#begin)|Vrátí iterátor, který adresuje první prvek v `hash_multiset`.|
|[cbegin](#cbegin)|Vrátí konstantní iterátor adresující první prvek v `hash_multiset`.|
|[cend](#cend)|Vrátí konstantní iterátor, který adresuje umístění následující po posledním prvku v `hash_multiset`.|
|[jejich](#clear)|Smaže všechny prvky `hash_multiset`.|
|[výpočtu](#count)|Vrátí počet prvků v `hash_multiset`, jejichž klíč odpovídá klíči zadanému parametru.|
|[crbegin –](#crbegin)|Vrátí konstantní iterátor adresující první prvek v obráceném `hash_multiset`.|
|[crend](#crend)|Vrátí konstantní iterátor, který adresuje umístění následující po posledním prvku v obráceném `hash_multiset`.|
|[emplace](#emplace)|Vloží prvek konstruovaný na místo do `hash_multiset`.|
|[emplace_hint](#emplace_hint)|Vloží prvek konstruovaný na místo do `hash_multiset`s pomocným parametrem umístění.|
|[obsahovat](#empty)|Testuje, zda je `hash_multiset` prázdné.|
|[účelu](#end)|Vrátí iterátor, který adresuje umístění následující po posledním prvku v `hash_multiset`.|
|[equal_range](#equal_range)|Vrátí dvojici iterátorů v uvedeném pořadí na první prvek v `hash_multiset` s klíčem, který je větší než zadaný klíč a na první prvek v `hash_multiset` s klíčem, který je roven nebo větší než klíč.|
|[ověřování](#erase)|Odebere prvek nebo rozsah prvků v `hash_multiset` ze zadané pozice nebo odstraní prvky, které odpovídají zadanému klíči.|
|[najít](#find)|Vrátí iterátor adresující umístění elementu v `hash_multiset`, který má klíč shodný se zadaným klíčem.|
|[get_allocator](#get_allocator)|Vrátí kopii objektu `allocator`, který se používá k vytvoření `hash_multiset`.|
|[zadat](#insert)|Vloží prvek nebo rozsah prvků do `hash_multiset`.|
|[key_comp](#key_compare)|Načte kopii objektu porovnání, která se používá k řazení klíčů v `hash_multiset`.|
|[lower_bound](#lower_bound)|Vrátí iterátor na první prvek v `hash_multiset` s klíčem, který je větší nebo roven zadanému klíči.|
|[max_size](#max_size)|Vrátí maximální délku `hash_multiset`.|
|[rbegin](#rbegin)|Vrátí iterátor adresující první prvek v obráceném `hash_multiset`.|
|[rend](#rend)|Vrátí iterátor, který adresuje umístění následující po posledním prvku v obráceném `hash_multiset`.|
|[hodnota](#size)|Vrátí počet prvků v `hash_multiset`.|
|[adresu](#swap)|Vyměňuje prvky dvou `hash_multiset`s.|
|[upper_bound](#upper_bound)|Vrátí iterátor na první prvek v `hash_multiset`, který má klíč, který je roven nebo větší než zadaný klíč.|
|[value_comp](#value_comp)|Načte kopii objektu zatřiďovacích vlastností, která se používá k hodnotě hash a seřazení hodnot klíčů elementu v `hash_multiset`.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[hash_multiset:: operator =](#op_eq)|Nahradí prvky hash_multiset kopií jiného hash_multiset.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<hash_set >

**Obor názvů:** stdext

## <a name="allocator_type"></a>hash_multiset::allocator_type

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_multiset třída](../standard-library/unordered-multiset-class.md).

Typ, který představuje třídu přidělování pro objekt hash_multiset.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::allocator_type allocator_type;
```

### <a name="example"></a>Příklad

Příklad použití `allocator_type` naleznete v tématu příklad pro [get_allocator](#get_allocator) .

## <a name="begin"></a>hash_multiset:: begin

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_multiset třída](../standard-library/unordered-multiset-class.md).

Vrátí iterátor, který adresuje první prvek v hash_multiset.

```cpp
const_iterator begin() const;

iterator begin();
```

### <a name="return-value"></a>Návratová hodnota

Obousměrný iterátor, který adresuje první prvek v hash_multiset nebo umístění, které je úspěšné pro prázdné hash_multiset.

### <a name="remarks"></a>Poznámky

Pokud je vrácená hodnota `begin` přiřazena k `const_iterator`, prvky v objektu hash_multiset nelze upravovat. Pokud je vrácená hodnota `begin` přiřazena k `iterator`, prvky v objektu hash_multiset lze upravit.

### <a name="example"></a>Příklad

```cpp
// hash_multiset_begin.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;
   hash_multiset <int>::iterator hms1_Iter;
   hash_multiset <int>::const_iterator hms1_cIter;

   hms1.insert( 1 );
   hms1.insert( 2 );
   hms1.insert( 3 );

   hms1_Iter = hms1.begin( );
   cout << "The first element of hms1 is " << *hms1_Iter << endl;

   hms1_Iter = hms1.begin( );
   hms1.erase( hms1_Iter );

   // The following 2 lines would err because the iterator is const
   // hms1_cIter = hms1.begin( );
   // hms1.erase( hms1_cIter );

   hms1_cIter = hms1.begin( );
   cout << "The first element of hms1 is now " << *hms1_cIter << endl;
}
```

```Output
The first element of hms1 is 1
The first element of hms1 is now 2
```

## <a name="cbegin"></a>hash_multiset:: cbegin

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_multiset třída](../standard-library/unordered-multiset-class.md).

Vrátí konstantní iterátor, který adresuje první prvek v hash_multiset.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>Návratová hodnota

Konstantní obousměrný iterátor, který adresuje první prvek v [hash_multiset](../standard-library/hash-multiset-class.md) nebo umístění, které je úspěšně prázdné `hash_multiset`.

### <a name="remarks"></a>Poznámky

S návratovou hodnotou `cbegin`nelze upravovat elementy v objektu `hash_multiset`.

### <a name="example"></a>Příklad

```cpp
// hash_multiset_cbegin.cpp
// compile with: /EHsc
#include <hash_multiset>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hs1;
   hash_multiset <int>::const_iterator hs1_cIter;

   hs1.insert( 1 );
   hs1.insert( 2 );
   hs1.insert( 3 );

   hs1_cIter = hs1.cbegin( );
   cout << "The first element of hs1 is " << *hs1_cIter << endl;
}
```

```Output
The first element of hs1 is 1
```

## <a name="cend"></a>hash_multiset:: cend

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_multiset třída](../standard-library/unordered-multiset-class.md).

Vrátí konstantní iterátor, který adresuje umístění následující po posledním prvku v hash_multiset.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>Návratová hodnota

Konstantní obousměrný iterátor, který adresuje umístění následující po posledním prvku v [hash_multiset](../standard-library/hash-multiset-class.md). Pokud je `hash_multiset` prázdné, `hash_multiset::cend == hash_multiset::begin`.

### <a name="remarks"></a>Poznámky

`cend` slouží k otestování, zda iterátor dosáhl konce jeho `hash_multiset`. Hodnota vrácená `cend` by neměla být zpětně odkazovaná.

### <a name="example"></a>Příklad

```cpp
// hash_multiset_cend.cpp
// compile with: /EHsc
#include <hash_multiset>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hs1;
   hash_multiset <int> :: const_iterator hs1_cIter;

   hs1.insert( 1 );
   hs1.insert( 2 );
   hs1.insert( 3 );

   hs1_cIter = hs1.cend( );
   hs1_cIter--;
   cout << "The last element of hs1 is " << *hs1_cIter << endl;
}
```

```Output
The last element of hs1 is 3
```

## <a name="clear"></a>hash_multiset:: Clear

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_multiset třída](../standard-library/unordered-multiset-class.md).

Smaže všechny prvky hash_multiset.

```cpp
void clear();
```

### <a name="remarks"></a>Poznámky

### <a name="example"></a>Příklad

```cpp
// hash_multiset_clear.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;

   hms1.insert( 1 );
   hms1.insert( 2 );

   cout << "The size of the hash_multiset is initially " << hms1.size( )
        << "." << endl;

   hms1.clear( );
   cout << "The size of the hash_multiset after clearing is "
        << hms1.size( ) << "." << endl;
}
```

```Output
The size of the hash_multiset is initially 2.
The size of the hash_multiset after clearing is 0.
```

## <a name="const_iterator"></a>hash_multiset::const_iterator

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_multiset třída](../standard-library/unordered-multiset-class.md).

Typ, který poskytuje obousměrný iterátor, který může číst prvek **const** v hash_multiset.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_iterator const_iterator;
```

### <a name="remarks"></a>Poznámky

Typ `const_iterator` nelze použít pro úpravu hodnoty prvku.

### <a name="example"></a>Příklad

Viz příklad pro [začátek](#begin) příkladu pomocí `const_iterator`.

## <a name="const_pointer"></a>hash_multiset::const_pointer

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_multiset třída](../standard-library/unordered-multiset-class.md).

Typ, který poskytuje ukazatel na prvek **const** v hash_multiset.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::const_pointer const_pointer;
```

### <a name="remarks"></a>Poznámky

Typ `const_pointer` nelze použít pro úpravu hodnoty prvku.

Ve většině případů by měl být [const_iterator](#const_iterator) použit pro přístup k prvkům v objektu **const** hash_multiset.

## <a name="const_reference"></a>hash_multiset::const_reference

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_multiset třída](../standard-library/unordered-multiset-class.md).

Typ, který poskytuje odkaz na prvek **const** uložený v hash_multiset pro čtení a provádění operací **const** .

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::const_reference const_reference;
```

### <a name="remarks"></a>Poznámky

### <a name="example"></a>Příklad

```cpp
// hash_multiset_const_reference.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;

   hms1.insert( 10 );
   hms1.insert( 20 );

   // Declare and initialize a const_reference &Ref1
   // to the 1st element
   const int &Ref1 = *hms1.begin( );

   cout << "The first element in the hash_multiset is "
        << Ref1 << "." << endl;

   // The following line would cause an error because the
   // const_reference cannot be used to modify the hash_multiset
   // Ref1 = Ref1 + 5;
}
```

```Output
The first element in the hash_multiset is 10.
```

## <a name="const_reverse_iterator"></a>hash_multiset::const_reverse_iterator

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_multiset třída](../standard-library/unordered-multiset-class.md).

Typ, který poskytuje obousměrný iterátor, který může číst libovolný element **const** v hash_multiset.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_reverse_iterator const_reverse_iterator;
```

### <a name="remarks"></a>Poznámky

Typ `const_reverse_iterator` nemůže změnit hodnotu prvku a použít k iteraci přes hash_multiset v obráceném pořadí.

### <a name="example"></a>Příklad

Příklad, jak deklarovat a použít `const_reverse_iterator`, naleznete v příkladu pro [rend](#rend) .

## <a name="count"></a>hash_multiset:: Count

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_multiset třída](../standard-library/unordered-multiset-class.md).

Vrátí počet prvků v hash_multiset, jejichž klíč odpovídá klíči určenému parametrem.

```cpp
size_type count(const Key& key) const;
```

### <a name="parameters"></a>Parametry

\ *klíčů*
Klíč prvků, které mají být porovnány s hash_multiset.

### <a name="return-value"></a>Návratová hodnota

Počet prvků v hash_multiset s klíčem zadaným parametrem.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí počet prvků v následujícím rozsahu:

\[ lower_bound (*klíč*), Upper_bound (*klíč*)).

### <a name="example"></a>Příklad

Následující příklad ukazuje použití členské funkce hash_multiset:: Count.

```cpp
// hash_multiset_count.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
    using namespace std;
    using namespace stdext;
    hash_multiset<int> hms1;
    hash_multiset<int>::size_type i;

    hms1.insert(1);
    hms1.insert(1);

    // Keys do not need to be unique in hash_multiset,
    // so duplicates may exist.
    i = hms1.count(1);
    cout << "The number of elements in hms1 with a sort key of 1 is: "
         << i << "." << endl;

    i = hms1.count(2);
    cout << "The number of elements in hms1 with a sort key of 2 is: "
         << i << "." << endl;
}
```

```Output
The number of elements in hms1 with a sort key of 1 is: 2.
The number of elements in hms1 with a sort key of 2 is: 0.
```

## <a name="crbegin"></a>hash_multiset:: crbegin –

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_multiset třída](../standard-library/unordered-multiset-class.md).

Vrátí konstantní iterátor adresující první prvek v obráceném hash_multisetě.

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>Návratová hodnota

Konstantní reverzní obousměrný iterátor, který adresuje první prvek v obráceném [hash_multiset](../standard-library/hash-multiset-class.md) nebo řeší, co byl poslední prvek v neobráceném `hash_multiset`.

### <a name="remarks"></a>Poznámky

`crbegin` se používá s obráceným `hash_multiset` stejně jako [hash_multiset:: begin](#begin) se používá s `hash_multiset`.

S návratovou hodnotou `crbegin`nelze změnit objekt `hash_multiset`.

`crbegin` lze použít k iteraci `hash_multiset` zpět.

### <a name="example"></a>Příklad

```cpp
// hash_multiset_crbegin.cpp
// compile with: /EHsc
#include <hash_multiset>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hs1;
   hash_multiset <int>::const_reverse_iterator hs1_crIter;

   hs1.insert( 10 );
   hs1.insert( 20 );
   hs1.insert( 30 );

   hs1_crIter = hs1.crbegin( );
   cout << "The first element in the reversed hash_multiset is "
        << *hs1_crIter << "." << endl;
}
```

```Output
The first element in the reversed hash_multiset is 30.
```

## <a name="crend"></a>hash_multiset:: crend

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_multiset třída](../standard-library/unordered-multiset-class.md).

Vrátí konstantní iterátor, který adresuje umístění následující po posledním prvku v obráceném hash_multisetě.

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>Návratová hodnota

Const reverzní obousměrný iterátor, který adresuje umístění následující po posledním prvku v obráceném [hash_multiset](../standard-library/hash-multiset-class.md) (umístění, které předchází první prvek v neobráceném `hash_multiset`).

### <a name="remarks"></a>Poznámky

`crend` se používá s obráceným `hash_multiset` stejně jako [hash_multiset:: end](#end) se používá s `hash_multiset`.

S návratovou hodnotou `crend`nelze změnit objekt `hash_multiset`.

`crend` lze použít k otestování, zda reverzní iterátor dosáhl konce jeho hash_multiset.

### <a name="example"></a>Příklad

```cpp
// hash_multiset_crend.cpp
// compile with: /EHsc
#include <hash_multiset>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hs1;
   hash_multiset <int>::const_reverse_iterator hs1_crIter;

   hs1.insert( 10 );
   hs1.insert( 20 );
   hs1.insert( 30 );

   hs1_crIter = hs1.crend( );
   hs1_crIter--;
   cout << "The last element in the reversed hash_multiset is "
        << *hs1_crIter << "." << endl;
}
```

```Output
The last element in the reversed hash_multiset is 10.
```

## <a name="difference_type"></a>hash_multiset::d ifference_type

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_multiset třída](../standard-library/unordered-multiset-class.md).

Typ celého čísla se znaménkem, který poskytuje rozdíl mezi dvěma iterátory, které řeší prvky ve stejném hash_multiset.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::difference_type difference_type;
```

### <a name="remarks"></a>Poznámky

`difference_type` je typ vrácený při odečítání nebo přírůstcích pomocí iterátorů kontejneru. `difference_type` se obvykle používá k reprezentaci počtu prvků v rozsahu [`first`, `last`) mezi iterátory `first` a `last`, zahrnuje element, na který odkazuje `first`, a rozsah prvků až po , ale nezahrnuje prvek, na který ukazuje `last`.

Všimněte si, že i když `difference_type` je k dispozici pro všechny iterátory, které splňují požadavky vstupního iterátoru, který zahrnuje třídu Obousměrných iterátorů podporovaných vratnými kontejnery, jako je například set. Odčítání mezi iterátory je podporováno pouze iterátory s náhodným přístupem, které jsou poskytovány kontejnerem s náhodným přístupem, jako je například Vector nebo deque.

### <a name="example"></a>Příklad

```cpp
// hash_multiset_diff_type.cpp
// compile with: /EHsc
#include <iostream>
#include <hash_set>
#include <algorithm>

int main( )
{
   using namespace std;
   using namespace stdext;

   hash_multiset <int> hms1;
   hash_multiset <int>::iterator hms1_Iter, hms1_bIter, hms1_eIter;

   hms1.insert( 20 );
   hms1.insert( 10 );

   // hash_multiset elements need not be unique
   hms1.insert( 20 );

   hms1_bIter = hms1.begin( );
   hms1_eIter = hms1.end( );

   hash_multiset <int>::difference_type   df_typ5, df_typ10,
        df_typ20;

   df_typ5 = count( hms1_bIter, hms1_eIter, 5 );
   df_typ10 = count( hms1_bIter, hms1_eIter, 10 );
   df_typ20 = count( hms1_bIter, hms1_eIter, 20 );

   // The keys & hence the elements of a hash_multiset
   // need not be unique and may occur multiple times
   cout << "The number '5' occurs " << df_typ5
        << " times in hash_multiset hms1.\n";
   cout << "The number '10' occurs " << df_typ10
        << " times in hash_multiset hms1.\n";
   cout << "The number '20' occurs " << df_typ20
        << " times in hash_multiset hms1.\n";

   // Count the number of elements in a hash_multiset
   hash_multiset <int>::difference_type  df_count = 0;
   hms1_Iter = hms1.begin( );
   while ( hms1_Iter != hms1_eIter)
   {
      df_count++;
      hms1_Iter++;
   }

   cout << "The number of elements in the hash_multiset hms1 is "
        << df_count << "." << endl;
}
```

```Output
The number '5' occurs 0 times in hash_multiset hms1.
The number '10' occurs 1 times in hash_multiset hms1.
The number '20' occurs 2 times in hash_multiset hms1.
The number of elements in the hash_multiset hms1 is 3.
```

## <a name="emplace"></a>hash_multiset:: emplace

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_multiset třída](../standard-library/unordered-multiset-class.md).

Vloží prvek konstruovaný na místo do hash_multiset.

```cpp
template <class ValTy>
iterator insert(ValTy&& val);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|-|-|
|*počítává*|Hodnota prvku, který má být vložen do objektu [hash_multiset](../standard-library/hash-multiset-class.md) , pokud `hash_multiset` již tento prvek neobsahuje, nebo obecněji, což je objekt, jehož klíč je ekvivalentně seřazený.|

### <a name="return-value"></a>Návratová hodnota

Členská funkce `emplace` vrací iterátor, který odkazuje na pozici, kam byl nový prvek vložen.

### <a name="remarks"></a>Poznámky

### <a name="example"></a>Příklad

```cpp
// hash_multiset_emplace.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>
#include <string>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset<string> hms3;
   string str1("a");

   hms3.emplace(move(str1));
   cout << "After the emplace insertion, hms3 contains "
      << *hms3.begin() << "." << endl;
}
```

```Output
After the emplace insertion, hms3 contains a.
```

## <a name="emplace_hint"></a>hash_multiset::emplace_hint

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_multiset třída](../standard-library/unordered-multiset-class.md).

Vloží prvek konstruovaný na místo do hash_multiset s pomocným parametrem umístění.

```cpp
template <class ValTy>
iterator insert(
    const_iterator where,
    ValTy&& val);
```

### <a name="parameters"></a>Parametry

\ *Val*
Hodnota prvku, který má být vložen do objektu [hash_multiset](../standard-library/hash-multiset-class.md) , pokud `hash_multiset` již tento prvek neobsahuje, nebo obecněji, což je objekt, jehož klíč je ekvivalentně seřazený.

*kde* \
Místo zahájení vyhledání správného bodu vložení. (Vložení se může vyskytnout v konstantním čase, namísto logaritmické doby, pokud se kurzor okamžitě sleduje *tam, kde*.)

### <a name="return-value"></a>Návratová hodnota

Členská funkce [hash_multiset:: emplace](#emplace) vrací iterátor, který odkazuje na pozici, kam byl nový prvek vložen do `hash_multiset`.

### <a name="remarks"></a>Poznámky

Vložení se může objevit v konstantním času v čase, namísto logaritmické doby, pokud se místo vložení hned následuje *tam, kde*.

### <a name="example"></a>Příklad

```cpp
// hash_multiset_emplace_hint.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>
#include <string>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset<string> hms1;
   string str1("a");

   hms1.insert(hms1.begin(), move(str1));
   cout << "After the emplace insertion, hms1 contains "
      << *hms1.begin() << "." << endl;
}
```

```Output
After the emplace insertion, hms1 contains a.
```

## <a name="empty"></a>hash_multiset:: Empty

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_multiset třída](../standard-library/unordered-multiset-class.md).

Testuje, zda je hash_multiset prázdné.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Návratová hodnota

**true** , pokud je hash_multiset prázdné; **false** , pokud je hash_multiset neprázdné.

### <a name="remarks"></a>Poznámky

### <a name="example"></a>Příklad

```cpp
// hash_multiset_empty.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1, hms2;
   hms1.insert ( 1 );

   if ( hms1.empty( ) )
      cout << "The hash_multiset hms1 is empty." << endl;
   else
      cout << "The hash_multiset hms1 is not empty." << endl;

   if ( hms2.empty( ) )
      cout << "The hash_multiset hms2 is empty." << endl;
   else
      cout << "The hash_multiset hms2 is not empty." << endl;
}
```

```Output
The hash_multiset hms1 is not empty.
The hash_multiset hms2 is empty.
```

## <a name="end"></a>hash_multiset:: end

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_multiset třída](../standard-library/unordered-multiset-class.md).

Vrátí iterátor, který adresuje umístění následující po posledním prvku v objektu hash_multiset.

```cpp
const_iterator end() const;

iterator end();
```

### <a name="return-value"></a>Návratová hodnota

Obousměrný iterátor, který adresuje umístění následující po posledním prvku v hash_multiset. Pokud je hash_multiset prázdné, potom hash_multiset:: end = = hash_multiset:: begin.

### <a name="remarks"></a>Poznámky

`end` slouží k otestování, zda iterátor dosáhl konce jeho hash_multiset. Hodnota vrácená `end` by neměla být zpětně odkazovaná.

### <a name="example"></a>Příklad

```cpp
// hash_multiset_end.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;
   hash_multiset <int> :: iterator hms1_Iter;
   hash_multiset <int> :: const_iterator hms1_cIter;

   hms1.insert( 1 );
   hms1.insert( 2 );
   hms1.insert( 3 );

   hms1_Iter = hms1.end( );
   hms1_Iter--;
   cout << "The last element of hms1 is " << *hms1_Iter << endl;

   hms1.erase( hms1_Iter );

   // The following 3 lines would err because the iterator is const
   // hms1_cIter = hms1.end( );
   // hms1_cIter--;
   // hms1.erase( hms1_cIter );

   hms1_cIter = hms1.end( );
   hms1_cIter--;
   cout << "The last element of hms1 is now " << *hms1_cIter << endl;
}
```

```Output
The last element of hms1 is 3
The last element of hms1 is now 2
```

## <a name="equal_range"></a>hash_multiset::equal_range

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_multiset třída](../standard-library/unordered-multiset-class.md).

Vrátí dvojici iterátorů v uvedeném pořadí na první prvek v hash_multiset s klíčem, který je větší než zadaný klíč a na první prvek v hash_multiset s klíčem, který je roven nebo větší než klíč.

```cpp
pair <const_iterator, const_iterator> equal_range (const Key& key) const;

pair <iterator, iterator> equal_range (const Key& key);
```

### <a name="parameters"></a>Parametry

\ *klíčů*
Klíč argumentu, který se má porovnat s klíčem řazení prvku z prohledávané hash_multisety.

### <a name="return-value"></a>Návratová hodnota

Pár iterátorů, kde první je [lower_bound](#lower_bound) klíče a druhý je [Upper_bound](#upper_bound) klíče.

Chcete-li získat přístup k prvnímu iterátoru páru `pr` vráceném členskou funkcí, použijte `pr`. **nejprve** a pro zpětnou vazbu dolního iterátoru použijte \* (`pr`. **první**). Pro přístup k druhému iterátoru páru `pr` vráceném členskou funkcí použijte `pr`. **sekundy** a pro zpětnou vazbu horního iterátoru, použijte \* (`pr`. **sekundy**).

### <a name="example"></a>Příklad

```cpp
// hash_multiset_equal_range.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   typedef hash_multiset<int> IntHSet;
   IntHSet hms1;
   hash_multiset <int> :: const_iterator hms1_RcIter;

   hms1.insert( 10 );
   hms1.insert( 20 );
   hms1.insert( 30 );

   pair <IntHSet::const_iterator, IntHSet::const_iterator> p1, p2;
   p1 = hms1.equal_range( 20 );

   cout << "The upper bound of the element with "
        << "a key of 20\nin the hash_multiset hms1 is: "
        << *(p1.second) << "." << endl;

   cout << "The lower bound of the element with "
        << "a key of 20\nin the hash_multiset hms1 is: "
        << *(p1.first) << "." << endl;

   // Compare the upper_bound called directly
   hms1_RcIter = hms1.upper_bound( 20 );
   cout << "A direct call of upper_bound( 20 ) gives "
        << *hms1_RcIter << "," << endl
        << "matching the 2nd element of the pair"
        << " returned by equal_range( 20 )." << endl;

   p2 = hms1.equal_range( 40 );

   // If no match is found for the key,
   // both elements of the pair return end( )
   if ( ( p2.first == hms1.end( ) )
      && ( p2.second == hms1.end( ) ) )
      cout << "The hash_multiset hms1 doesn't have an element "
           << "with a key less than 40." << endl;
   else
      cout << "The element of hash_multiset hms1"
           << "with a key >= 40 is: "
           << *(p1.first) << "." << endl;
}
```

```Output
The upper bound of the element with a key of 20
in the hash_multiset hms1 is: 30.
The lower bound of the element with a key of 20
in the hash_multiset hms1 is: 20.
A direct call of upper_bound( 20 ) gives 30,
matching the 2nd element of the pair returned by equal_range( 20 ).
The hash_multiset hms1 doesn't have an element with a key less than 40.
```

## <a name="erase"></a>hash_multiset:: Erase

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_multiset třída](../standard-library/unordered-multiset-class.md).

Odebere prvek nebo rozsah prvků v objektu hash_multiset ze zadané pozice nebo odstraní prvky, které odpovídají zadanému klíči.

```cpp
iterator erase(iterator where);

iterator erase(iterator first, iterator last);

size_type erase(const key_type& key);
```

### <a name="parameters"></a>Parametry

*kde* \
Pozice prvku, který má být odebrán z hash_multiset.

*první* \
Pozice prvního prvku byla odebrána z hash_multiset.

*poslední* \
Pozice hned za posledním prvkem odebraným z hash_multiset.

\ *klíčů*
Klíč prvků, které mají být odebrány z hash_multiset.

### <a name="return-value"></a>Návratová hodnota

Pro první dvě členské funkce obousměrný iterátor, který určuje první prvek zbývající za odebranými prvky, nebo ukazatel na konec hash_multiset, pokud žádný takový prvek neexistuje. Pro třetí členskou funkci počet prvků, které byly odebrány z hash_multiset.

### <a name="remarks"></a>Poznámky

Členské funkce nikdy nevyvolají výjimku.

### <a name="example"></a>Příklad

Následující příklad ukazuje použití členské funkce hash_multiset:: Erase.

```cpp
// hash_multiset_erase.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main()
{
    using namespace std;
    using namespace stdext;
    hash_multiset<int> hms1, hms2, hms3;
    hash_multiset<int> :: iterator pIter, Iter1, Iter2;
    int i;
    hash_multiset<int>::size_type n;

    for (i = 1; i < 5; i++)
    {
        hms1.insert(i);
        hms2.insert(i * i);
        hms3.insert(i - 1);
    }

    // The 1st member function removes an element at a given position
    Iter1 = ++hms1.begin();
    hms1.erase(Iter1);

    cout << "After the 2nd element is deleted,\n"
         << "the hash_multiset hms1 is:" ;
    for (pIter = hms1.begin(); pIter != hms1.end(); pIter++)
        cout << " " << *pIter;
    cout << "." << endl;

    // The 2nd member function removes elements
    // in the range [ first,  last)
    Iter1 = ++hms2.begin();
    Iter2 = --hms2.end();
    hms2.erase(Iter1, Iter2);

    cout << "After the middle two elements are deleted,\n"
         << "the hash_multiset hms2 is:" ;
    for (pIter = hms2.begin(); pIter != hms2.end(); pIter++)
        cout << " " << *pIter;
    cout << "." << endl;

    // The 3rd member function removes elements with a given  key
    n = hms3.erase(2);

    cout << "After the element with a key of 2 is deleted,\n"
         << "the hash_multiset hms3 is:" ;
    for (pIter = hms3.begin(); pIter != hms3.end(); pIter++)
        cout << " " << *pIter;
    cout << "." << endl;

    // The 3rd member function returns the number of elements removed
    cout << "The number of elements removed from hms3 is: "
         << n << "." << endl;

    // The dereferenced iterator can also be used to specify a key
    Iter1 = ++hms3.begin();
    hms3.erase(Iter1);

    cout << "After another element with a key "
         << "equal to that of the 2nd element\n"
         << "is deleted, the hash_multiset hms3 is:" ;
    for (pIter = hms3.begin(); pIter != hms3.end(); pIter++)
        cout << " " << *pIter;
    cout << "." << endl;
}
```

```Output
After the 2nd element is deleted,
the hash_multiset hms1 is: 1 3 4.
After the middle two elements are deleted,
the hash_multiset hms2 is: 16 4.
After the element with a key of 2 is deleted,
the hash_multiset hms3 is: 0 1 3.
The number of elements removed from hms3 is: 1.
After another element with a key equal to that of the 2nd element
is deleted, the hash_multiset hms3 is: 0 3.
```

## <a name="find"></a>hash_multiset:: Find

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_multiset třída](../standard-library/unordered-multiset-class.md).

Vrátí iterátor adresující umístění elementu v hash_multiset, který má klíč odpovídající zadanému klíči.

```cpp
iterator find(const Key& key);

const_iterator find(const Key& key) const;
```

### <a name="parameters"></a>Parametry

\ *klíčů*
Klíč argumentu, který se má shodovat s klíčem řazení prvku z prohledávané hash_multisety.

### <a name="return-value"></a>Návratová hodnota

[Iterátor](#iterator) nebo [const_iterator](#const_iterator) , které řeší umístění elementu, který odpovídá zadanému klíči, nebo který řeší umístění, které následuje po posledním prvku v hash_multiset, pokud se pro klíč nenajde žádná shoda.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí iterátor, který adresuje element v hash_multiset, jehož klíč řazení je `equivalent` k klíči argumentu pod binárním predikátem, který vystaví řazení na základě vztahu srovnatelnosti menšího než.

Pokud je vrácená hodnota `find` přiřazena k `const_iterator`, objekt hash_multiset nelze změnit. Pokud je vrácená hodnota `find` přiřazena k `iterator`, lze objekt hash_multiset upravit.

### <a name="example"></a>Příklad

```cpp
// hash_multiset_find.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;
   hash_multiset <int> :: const_iterator hms1_AcIter, hms1_RcIter;

   hms1.insert( 10 );
   hms1.insert( 20 );
   hms1.insert( 30 );

   hms1_RcIter = hms1.find( 20 );
   cout << "The element of hash_multiset hms1 with a key of 20 is: "
        << *hms1_RcIter << "." << endl;

   hms1_RcIter = hms1.find( 40 );

   // If no match is found for the key, end( ) is returned
   if ( hms1_RcIter == hms1.end( ) )
      cout << "The hash_multiset hms1 doesn't have an element "
           << "with a key of 40." << endl;
   else
      cout << "The element of hash_multiset hms1 with a key of 40 is: "
           << *hms1_RcIter << "." << endl;

   // The element at a specific location in the hash_multiset can be found
   // by using a dereferenced iterator addressing the location
   hms1_AcIter = hms1.end( );
   hms1_AcIter--;
   hms1_RcIter = hms1.find( *hms1_AcIter );
   cout << "The element of hms1 with a key matching "
        << "that of the last element is: "
        << *hms1_RcIter << "." << endl;
}
```

```Output
The element of hash_multiset hms1 with a key of 20 is: 20.
The hash_multiset hms1 doesn't have an element with a key of 40.
The element of hms1 with a key matching that of the last element is: 30.
```

## <a name="get_allocator"></a>hash_multiset::get_allocator

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_multiset třída](../standard-library/unordered-multiset-class.md).

Vrátí kopii objektu přidělování, která se používá k vytvoření hash_multiset.

```cpp
Allocator get_allocator() const;
```

### <a name="return-value"></a>Návratová hodnota

Alokátor používaný hash_multiset ke správě paměti, což je parametr šablony třídy `Allocator`.

Další informace o `Allocator`naleznete v části poznámky v tématu [Třída hash_multiset](../standard-library/hash-multiset-class.md) .

### <a name="remarks"></a>Poznámky

Přidělování pro třídu hash_multiset určují, jak Třída spravuje úložiště. Výchozí přidělující třídy kontejnerů C++ standardní knihovny jsou dostačující pro většinu programovacích potřeb. Psaní a používání vlastního třídy přidělování je pokročilým C++ tématem.

### <a name="example"></a>Příklad

```cpp
// hash_multiset_get_allocator.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;

   // The following lines declare objects
   // that use the default allocator.
   hash_multiset <int, hash_compare <int, less<int> > > hms1;
   hash_multiset <int, hash_compare <int, greater<int> > > hms2;
   hash_multiset <double, hash_compare <double,
      less<double> >, allocator<double> > hms3;

   hash_multiset <int, hash_compare <int,
      greater<int> > >::allocator_type hms2_Alloc;
   hash_multiset <double>::allocator_type hms3_Alloc;
   hms2_Alloc = hms2.get_allocator( );

   cout << "The number of integers that can be allocated"
        << endl << "before free memory is exhausted: "
        << hms1.max_size( ) << "." << endl;

   cout << "The number of doubles that can be allocated"
        << endl << "before free memory is exhausted: "
        << hms3.max_size( ) <<  "." << endl;

   // The following lines create a hash_multiset hms4
   // with the allocator of hash_multiset hms1.
   hash_multiset <int>::allocator_type hms4_Alloc;
   hash_multiset <int> hms4;
   hms4_Alloc = hms2.get_allocator( );

   // Two allocators are interchangeable if
   // storage allocated from each can be
   // deallocated by the other
   if( hms2_Alloc == hms4_Alloc )
   {
      cout << "The allocators are interchangeable."
           << endl;
   }
   else
   {
      cout << "The allocators are not interchangeable."
           << endl;
   }
}
```

## <a name="hash_multiset"></a>hash_multiset::hash_multiset

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_multiset třída](../standard-library/unordered-multiset-class.md).

Vytvoří `hash_multiset`, který je prázdný nebo který je kopií všech nebo částí jiných `hash_multiset`.

```cpp
hash_multiset();

explicit hash_multiset(
    const Traits& Comp);

hash_multiset(
    const Traits& Comp,
    const Allocator& Al);

hash_multiset(
    const hash_multiset<Key, Traits, Allocator>& Right);

hash_multiset(
    hash_multiset&& Right
};
hash_multiset (initializer_list<Type> IList);

hash_multiset(
    initializer_list<Tu[e> IList, const Compare& Comp):
hash_multiset(
    initializer_list<Type> IList, const Compare& Comp, const Allocator& Al);

template <class InputIterator>
hash_multiset(
    InputIterator first,
    InputIterator last);

template <class InputIterator>
hash_multiset(
    InputIterator first,
    InputIterator last,
    const Traits& Comp);

template <class InputIterator>
hash_multiset(
    InputIterator first,
    InputIterator last,
    const Traits& Comp,
    const Allocator& Al);
```

### <a name="parameters"></a>Parametry

*Al* \
Třída přidělování úložiště, která se má použít pro tento objekt `hash_multiset`, který má výchozí hodnotu `Allocator`.

\ *comp*
Funkce porovnání typu `const Traits` slouží k uspořádání prvků v `hash_multiset`, jejichž výchozí hodnota je `hash_compare`.

*Pravé* \
`hash_multiset`, ze kterého má být vytvořená `hash_multiset` kopie.

*první* \
Pozice prvního prvku v rozsahu prvků, které mají být zkopírovány.

*poslední* \
Pozice prvního prvku mimo rozsah prvků, které mají být zkopírovány.

\ *IList*
Initializer_list obsahující prvky, které mají být zkopírovány.

### <a name="remarks"></a>Poznámky

Všechny konstruktory ukládají typ objektu přidělování, který spravuje úložiště paměti pro `hash_multiset` a které mohou být později vráceny voláním [hash_multiset:: get_allocator](#get_allocator). Parametr allocator je často v deklaraci třídy vynechán a makra předběžného zpracování jsou použita k nahrazení alternativních alokátorů.

Všechny konstruktory inicializují své hash_multisets.

Všechny konstruktory ukládají objekt funkce typu `Traits`, který se používá k navázání objednávky mezi klíči `hash_multiset` a které mohou být později vráceny voláním [hash_multiset:: key_comp](#key_comp). Další informace o `Traits` naleznete v tématu [Třída hash_multiset](../standard-library/hash-multiset-class.md) .

První tři konstruktory určují prázdné počáteční `hash_multiset`, druhý, který určuje typ funkce porovnání (*comp*), který se použije při vytváření pořadí prvků a třetí, explicitně určující typ přidělování (*Al*), který se má pro. Klíčové slovo **Explicit** potlačí určité druhy automatických převodů typu.

Čtvrtý konstruktor přesune `hash_multiset` `Right`.

Pátý, šestý a sedmý konstruktor používají initializer_list.

Poslední tři konstruktory kopírují rozsah [`first`, `last`) `hash_multiset` se zvýšením explicitního určení typu funkce porovnání třídy Compare a Alokátor.

Skutečné pořadí prvků v kontejneru sady nastavení s hodnotou hash závisí na funkci hash, funkci řazení a aktuální velikosti zatřiďovací tabulky a nemůže obecně být předpokládaná, protože by mohla být s kontejnerem množiny, kde byla určena funkcí řazení. samy.

## <a name="insert"></a>hash_multiset:: INSERT

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_multiset třída](../standard-library/unordered-multiset-class.md).

Vloží prvek nebo rozsah prvků do objektu hash_multiset.

```cpp
iterator insert(
    const Type& value);

iterator insert(
    iterator where,
    const Type& Al);

void insert(
    initializer_list<Type> IList);

iterator insert(
    const Type& value);

iterator insert(
    Iterator where,
    const Type& value);

template <class InputIterator>
void insert(
    InputIterator first,
    InputIterator last);

template <class ValTy>
iterator insert(
    ValTy&& value);

template <class ValTy>
iterator insert(
    const_iterator where,
    ValTy&& value);
```

### <a name="parameters"></a>Parametry

*hodnota* \
Hodnota elementu, který má být vložen do hash_multiset, pokud hash_multiset již tento prvek neobsahuje, nebo obecněji, element, jehož klíč je ekvivalentně seřazen.

*kde* \
Místo zahájení vyhledání správného bodu vložení. (Vložení se může vyskytnout v konstantním čase, namísto logaritmické doby, pokud se kurzor okamžitě sleduje *tam, kde*.)

*první* \
Pozice prvního prvku, který má být zkopírován z hash_multiset.

*poslední* \
Pozice bezprostředně za posledním prvkem, který má být zkopírován z hash_multiset.

\ *IList*
Initializer_list obsahující prvky ke zkopírování.

### <a name="return-value"></a>Návratová hodnota

První dvě vložené členské funkce vrátí iterátor, který odkazuje na pozici, kam byl nový prvek vložen.

Další tři členské funkce používají initializer_list.

Třetí členská funkce vloží sekvenci hodnot prvků do hash_multiset odpovídající každému elementu, který je adresován v rozsahu [`first`, `last`) zadaného hash_multiset.

### <a name="remarks"></a>Poznámky

Vložení se může vyskytnout v konstantním konstantním čase pro verzi pomocného parametru pro vložení, namísto logaritmické doby, pokud se místo vložení hned následuje *tam, kde*.

## <a name="iterator"></a>hash_multiset:: iterátor

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_multiset třída](../standard-library/unordered-multiset-class.md).

Typ, který poskytuje obousměrný iterátor, který může číst nebo upravovat libovolný prvek v hash_multiset.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::iterator iterator;
```

### <a name="remarks"></a>Poznámky

Typ `iterator` lze použít pro úpravu hodnoty prvku.

### <a name="example"></a>Příklad

Viz příklad pro [začátek](#begin) pro příklad, jak deklarovat a používat `iterator`.

## <a name="key_comp"></a>hash_multiset::key_comp

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_multiset třída](../standard-library/unordered-multiset-class.md).

Načte kopii objektu porovnání, která se používá k řazení klíčů v hash_multiset.

```cpp
key_compare key_comp() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí *vlastnosti*parametru šablony hash_multiset, které obsahují objekty funkce, které jsou použity k hodnotě hash a k uspořádání prvků kontejneru.

Další informace o *vlastnostích* naleznete v tématu [třídy hash_multiset](../standard-library/hash-multiset-class.md) .

### <a name="remarks"></a>Poznámky

Uložený objekt definuje členskou funkci:

`bool operator<(const Key& _xVal, const Key& _yVal);`

Vrátí **hodnotu true** , pokud `_xVal` předchází a není rovna `_yVal` v pořadí řazení.

Všimněte si, že obě [key_compare](#key_compare) a [value_compare](#value_compare) jsou synonyma pro *vlastnosti*parametrů šablony. Oba typy jsou k dispozici pro třídy hash_multiset a hash_multiset, kde jsou identické, pro zajištění kompatibility s třídami hash_map a hash_multimap, kde jsou odlišné.

### <a name="example"></a>Příklad

```cpp
// hash_multiset_key_comp.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;

   hash_multiset <int, hash_compare < int, less<int> > >hms1;
   hash_multiset<int, hash_compare < int, less<int> > >::key_compare kc1
          = hms1.key_comp( ) ;
   bool result1 = kc1( 2, 3 ) ;
   if( result1 == true )
   {
      cout << "kc1( 2,3 ) returns value of true, "
           << "where kc1 is the function object of hms1."
           << endl;
   }
   else
   {
      cout << "kc1( 2,3 ) returns value of false "
           << "where kc1 is the function object of hms1."
        << endl;
   }

   hash_multiset <int, hash_compare < int, greater<int> > > hms2;
   hash_multiset<int, hash_compare < int, greater<int> > >::key_compare
         kc2 = hms2.key_comp( ) ;
   bool result2 = kc2( 2, 3 ) ;
   if( result2 == true )
   {
      cout << "kc2( 2,3 ) returns value of true, "
           << "where kc2 is the function object of hms2."
           << endl;
   }
   else
   {
      cout << "kc2( 2,3 ) returns value of false, "
           << "where kc2 is the function object of hms2."
           << endl;
   }
}
```

## <a name="key_compare"></a>hash_multiset::key_compare

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_multiset třída](../standard-library/unordered-multiset-class.md).

Typ, který poskytuje dva objekty Functions, binární predikát porovnání třídy, který může porovnat dvě hodnoty prvku hash_multiset a určit jejich relativní pořadí a unární predikát, který prvky vyhodnotí.

```cpp
typedef Traits key_compare;
```

### <a name="remarks"></a>Poznámky

`key_compare` je synonymum pro *vlastnosti*parametrů šablony.

Další informace o *vlastnostích* naleznete v tématu [třídy hash_multiset](../standard-library/hash-multiset-class.md) .

Všimněte si, že `key_compare` i value_compare jsou synonyma pro *vlastnosti*parametrů šablony. Oba typy jsou k dispozici pro třídy hash_set a hash_multiset, kde jsou identické, pro zajištění kompatibility s třídami hash_map a hash_multimap, kde jsou odlišné.

### <a name="example"></a>Příklad

Příklad, jak deklarovat a používat `key_compare`, naleznete v tématu příklad pro [key_comp](#key_comp) .

## <a name="key_type"></a>hash_multiset::key_type

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_multiset třída](../standard-library/unordered-multiset-class.md).

Typ, který poskytuje objekt funkce, který může porovnat klíče řazení pro určení relativního pořadí dvou prvků v hash_multiset.

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>Poznámky

`key_type` je synonymum pro *klíč*parametru šablony.

Všimněte si, že `key_type` i [value_type](../standard-library/hash-set-class.md#value_type) jsou synonyma pro *klíč*parametru šablony. Oba typy jsou k dispozici pro třídy set a multiset, kde jsou identické, pro kompatibilitu s třídami map a multimap, kde jsou odlišné.

Další informace o *klíči*naleznete v části poznámky v tématu [Třída hash_multiset](../standard-library/hash-multiset-class.md) .

### <a name="example"></a>Příklad

Příklad, jak deklarovat a používat `key_type`, naleznete v tématu příklad pro [value_type](#value_type) .

## <a name="lower_bound"></a>hash_multiset::lower_bound

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_multiset třída](../standard-library/unordered-multiset-class.md).

Vrátí iterátor na první prvek v hash_multiset s klíčem, který je větší nebo roven zadanému klíči.

```cpp
const_iterator lower_bound(const Key& key) const;

iterator lower_bound(const Key& key);
```

### <a name="parameters"></a>Parametry

\ *klíčů*
Klíč argumentu, který se má porovnat s klíčem řazení prvku z prohledávané hash_multisety.

### <a name="return-value"></a>Návratová hodnota

[Iterátor](#iterator) nebo [const_iterator](#const_iterator) , které řeší umístění prvního prvku v hash_multiset s klíčem, který je roven nebo větší než klíč argumentu nebo který řeší umístění, které následuje po posledním elementu v hash_multiset, pokud ne pro tento klíč se našla shoda.

### <a name="remarks"></a>Poznámky

### <a name="example"></a>Příklad

```cpp
// hash_multiset_lower_bound.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main() {
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;
   hash_multiset <int> :: const_iterator hms1_AcIter, hms1_RcIter;

   hms1.insert( 10 );
   hms1.insert( 20 );
   hms1.insert( 30 );

   hms1_RcIter = hms1.lower_bound( 20 );
   cout << "The element of hash_multiset hms1 with a key of 20 is: "
        << *hms1_RcIter << "." << endl;

   hms1_RcIter = hms1.lower_bound( 40 );

   // If no match is found for the key, end( ) is returned
   if ( hms1_RcIter == hms1.end( ) )
      cout << "The hash_multiset hms1 doesn't have an element "
           << "with a key of 40." << endl;
   else
      cout << "The element of hash_multiset hms1 with a key of 40 is: "
           << *hms1_RcIter << "." << endl;

   // An element at a specific location in the hash_multiset can be found
   // by using a dereferenced iterator that addresses the location
   hms1_AcIter = hms1.end( );
   hms1_AcIter--;
   hms1_RcIter = hms1.lower_bound( *hms1_AcIter );
   cout << "The element of hms1 with a key matching "
        << "that of the last element is: "
        << *hms1_RcIter << "." << endl;
}
```

## <a name="max_size"></a>hash_multiset::max_size

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_multiset třída](../standard-library/unordered-multiset-class.md).

Vrátí maximální délku hash_multiset.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>Návratová hodnota

Maximální možná délka hash_multiset.

### <a name="remarks"></a>Poznámky

### <a name="example"></a>Příklad

```cpp
// hash_multiset_max_size.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;
   hash_multiset <int>::size_type i;

   i = hms1.max_size( );
   cout << "The maximum possible length "
        << "of the hash_multiset is " << i << "." << endl;
}
```

## <a name="op_eq"></a>hash_multiset:: operator =

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_multiset třída](../standard-library/unordered-multiset-class.md).

Nahradí prvky hash_multiset kopií jiného hash_multiset.

```cpp
hash_multiset& operator=(const hash_multiset& right);

hash_multiset& operator=(hash_multiset&& right);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|-|-|
|*Kliknutím*|[Hash_multiset](../standard-library/hash-multiset-class.md) se kopíruje do `hash_multiset`.|

### <a name="remarks"></a>Poznámky

Po vymazání všech existujících prvků v `hash_multiset``operator=` buď zkopírování nebo přesunutí obsahu *přímo* do `hash_multiset`.

### <a name="example"></a>Příklad

```cpp
// hash_multiset_operator_as.cpp
// compile with: /EHsc
#include <hash_multiset>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset<int> v1, v2, v3;
   hash_multiset<int>::iterator iter;

   v1.insert(10);

   cout << "v1 = " ;
   for (iter = v1.begin(); iter != v1.end(); iter++)
      cout << iter << " ";
   cout << endl;

   v2 = v1;
   cout << "v2 = ";
   for (iter = v2.begin(); iter != v2.end(); iter++)
      cout << iter << " ";
   cout << endl;

// move v1 into v2
   v2.clear();
   v2 = move(v1);
   cout << "v2 = ";
   for (iter = v2.begin(); iter != v2.end(); iter++)
      cout << iter << " ";
   cout << endl;
}
```

## <a name="pointer"></a>hash_multiset::p ointer

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_multiset třída](../standard-library/unordered-multiset-class.md).

Typ, který poskytuje ukazatel na prvek v hash_multiset.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::pointer pointer;
```

### <a name="remarks"></a>Poznámky

Typ `pointer` lze použít pro úpravu hodnoty prvku.

Ve většině případů by měl být použit [iterátor](#iterator) pro přístup k prvkům v objektu multiset.

## <a name="rbegin"></a>hash_multiset:: rbegin

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_multiset třída](../standard-library/unordered-multiset-class.md).

Vrátí iterátor adresující první prvek v obráceném hash_multisetě.

```cpp
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```

### <a name="return-value"></a>Návratová hodnota

Reverzní obousměrný iterátor, který adresuje první prvek v obráceném hash_multiset nebo řeší, co byl posledním prvkem v neobráceném hash_multiset.

### <a name="remarks"></a>Poznámky

`rbegin` se používá s obráceným hash_multiset stejně jako [Begin](#begin) se používá s hash_multiset.

Pokud je vrácená hodnota `rbegin` přiřazena k `const_reverse_iterator`, objekt hash_multiset nelze změnit. Pokud je vrácená hodnota `rbegin` přiřazena k `reverse_iterator`, lze objekt hash_multiset upravit.

`rbegin` lze použít k iterování hash_multiset dozadu.

### <a name="example"></a>Příklad

```cpp
// hash_multiset_rbegin.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;
   hash_multiset <int>::iterator hms1_Iter;
   hash_multiset <int>::reverse_iterator hms1_rIter;

   hms1.insert( 10 );
   hms1.insert( 20 );
   hms1.insert( 30 );

   hms1_rIter = hms1.rbegin( );
   cout << "The first element in the reversed hash_multiset is "
        << *hms1_rIter << "." << endl;

   // begin can be used to start an iteration
   // through a hash_multiset in a forward order
   cout << "The hash_multiset is: ";
   for ( hms1_Iter = hms1.begin( ) ; hms1_Iter != hms1.end( );
         hms1_Iter++ )
      cout << *hms1_Iter << " ";
   cout << endl;

   // rbegin can be used to start an iteration
   // through a hash_multiset in a reverse order
   cout << "The reversed hash_multiset is: ";
   for ( hms1_rIter = hms1.rbegin( ) ; hms1_rIter != hms1.rend( );
         hms1_rIter++ )
      cout << *hms1_rIter << " ";
   cout << endl;

   // A hash_multiset element can be erased by dereferencing to its key
   hms1_rIter = hms1.rbegin( );
   hms1.erase ( *hms1_rIter );

   hms1_rIter = hms1.rbegin( );
   cout << "After the erasure, the first element "
        << "in the reversed hash_multiset is "<< *hms1_rIter << "."
        << endl;
}
```

```Output
The first element in the reversed hash_multiset is 30.
The hash_multiset is: 10 20 30
The reversed hash_multiset is: 30 20 10
After the erasure, the first element in the reversed hash_multiset is 20.
```

## <a name="reference"></a>hash_multiset:: Reference

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_multiset třída](../standard-library/unordered-multiset-class.md).

Typ, který poskytuje odkaz na prvek uložený v objektu hash_multiset.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::reference reference;
```

### <a name="remarks"></a>Poznámky

### <a name="example"></a>Příklad

```cpp
// hash_multiset_reference.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;

   hms1.insert( 10 );
   hms1.insert( 20 );

   // Declare and initialize a reference &Ref1 to the 1st element
   int &Ref1 = *hms1.begin( );

   cout << "The first element in the hash_multiset is "
        << Ref1 << "." << endl;

   // The value of the 1st element of the hash_multiset can be
   // changed by operating on its (non const) reference
   Ref1 = Ref1 + 5;

   cout << "The first element in the hash_multiset is now "
        << *hms1.begin() << "." << endl;
}
```

```Output
The first element in the hash_multiset is 10.
The first element in the hash_multiset is now 15.
```

## <a name="rend"></a>hash_multiset:: rend

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_multiset třída](../standard-library/unordered-multiset-class.md).

Vrátí iterátor, který adresuje umístění následující po posledním prvku v obráceném hash_multisetě.

```cpp
const_reverse_iterator rend() const;

reverse_iterator rend();
```

### <a name="return-value"></a>Návratová hodnota

Zpětný obousměrný iterátor, který adresuje umístění následující po posledním prvku v obráceném hash_multiset (umístění, které předchází prvnímu prvku v neobráceném hash_multiset).

### <a name="remarks"></a>Poznámky

`rend` se používá s obráceným hash_multiset stejně jako [End](#end) se používá s hash_multiset.

Pokud je vrácená hodnota `rend` přiřazena k `const_reverse_iterator`, objekt hash_multiset nelze změnit. Pokud je vrácená hodnota `rend` přiřazena k `reverse_iterator`, lze objekt hash_multiset upravit. Hodnota vrácená `rend` by neměla být zpětně odkazovaná.

`rend` lze použít k otestování, zda reverzní iterátor dosáhl konce jeho hash_multiset.

### <a name="example"></a>Příklad

```cpp
// hash_multiset_rend.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;
   hash_multiset <int>::iterator hms1_Iter;
   hash_multiset <int>::reverse_iterator hms1_rIter;
   hash_multiset <int>::const_reverse_iterator hms1_crIter;

   hms1.insert( 10 );
   hms1.insert( 20 );
   hms1.insert( 30 );

   hms1_rIter = hms1.rend( );
   hms1_rIter--;
   cout << "The last element in the reversed hash_multiset is "
        << *hms1_rIter << "." << endl;

   // end can be used to terminate an iteration
   // through a hash_multiset in a forward order
   cout << "The hash_multiset is: ";
   for ( hms1_Iter = hms1.begin( ) ; hms1_Iter != hms1.end( );
         hms1_Iter++ )
      cout << *hms1_Iter << " ";
   cout << "." << endl;

   // rend can be used to terminate an iteration
   // through a hash_multiset in a reverse order
   cout << "The reversed hash_multiset is: ";
   for ( hms1_rIter = hms1.rbegin( ) ; hms1_rIter != hms1.rend( );
         hms1_rIter++ )
      cout << *hms1_rIter << " ";
   cout << "." << endl;

   hms1_rIter = hms1.rend( );
   hms1_rIter--;
   hms1.erase ( *hms1_rIter );

   hms1_rIter = hms1.rend( );
   hms1_rIter--;
   cout << "After the erasure, the last element in the "
        << "reversed hash_multiset is " << *hms1_rIter << "."
        << endl;
}
```

```Output
The last element in the reversed hash_multiset is 10.
The hash_multiset is: 10 20 30 .
The reversed hash_multiset is: 30 20 10 .
After the erasure, the last element in the reversed hash_multiset is 20.
```

## <a name="reverse_iterator"></a>hash_multiset::reverse_iterator

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_multiset třída](../standard-library/unordered-multiset-class.md).

Typ, který poskytuje obousměrný iterátor, který může číst nebo upravovat prvek v obráceném hash_multisetě.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::reverse_iterator reverse_iterator;
```

### <a name="remarks"></a>Poznámky

Typ `reverse_iterator` slouží k iterování hash_multiset v obráceném pořadí.

### <a name="example"></a>Příklad

Příklad, jak deklarovat a používat `reverse_iterator`, naleznete v tématu příklad pro [rbegin](#rbegin) .

## <a name="size"></a>hash_multiset:: size

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_multiset třída](../standard-library/unordered-multiset-class.md).

Vrátí počet prvků v hash_multiset.

```cpp
size_type size() const;
```

### <a name="return-value"></a>Návratová hodnota

Aktuální délka hash_multiset.

### <a name="remarks"></a>Poznámky

### <a name="example"></a>Příklad

```cpp
// hash_multiset_size.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;
   hash_multiset <int> :: size_type i;

   hms1.insert( 1 );
   i = hms1.size( );
   cout << "The hash_multiset length is " << i << "." << endl;

   hms1.insert( 2 );
   i = hms1.size( );
   cout << "The hash_multiset length is now " << i << "." << endl;
}
```

```Output
The hash_multiset length is 1.
The hash_multiset length is now 2.
```

## <a name="size_type"></a>hash_multiset::size_type

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_multiset třída](../standard-library/unordered-multiset-class.md).

Typ unsigned integer, který může představovat počet prvků v objektu hash_multiset.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::size_type size_type;
```

### <a name="remarks"></a>Poznámky

### <a name="example"></a>Příklad

Viz příklad pro [Velikost](#size) pro příklad, jak deklarovat a použít `size_type`

## <a name="swap"></a>hash_multiset:: swap

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_multiset třída](../standard-library/unordered-multiset-class.md).

Vyměňuje prvky dvou hash_multisets.

```cpp
void swap(hash_multiset& right);
```

### <a name="parameters"></a>Parametry

*pravé* \
Argument hash_multiset, který poskytuje prvky, které mají být nahrazeny cílovým hash_multiset.

### <a name="remarks"></a>Poznámky

Členská funkce neověřuje žádné odkazy, ukazatele nebo iterátory, které určují elementy ve dvou hash_multisets, jejichž prvky se vyměňují.

### <a name="example"></a>Příklad

```cpp
// hash_multiset_swap.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1, hms2, hms3;
   hash_multiset <int>::iterator hms1_Iter;

   hms1.insert( 10 );
   hms1.insert( 20 );
   hms1.insert( 30 );
   hms2.insert( 100 );
   hms2.insert( 200 );
   hms3.insert( 300 );

   cout << "The original hash_multiset hms1 is:";
   for ( hms1_Iter = hms1.begin( ); hms1_Iter != hms1.end( );
         hms1_Iter++ )
         cout << " " << *hms1_Iter;
   cout   << "." << endl;

   // This is the member function version of swap
   hms1.swap( hms2 );

   cout << "After swapping with hms2, list hms1 is:";
   for ( hms1_Iter = hms1.begin( ); hms1_Iter != hms1.end( );
         hms1_Iter++ )
         cout << " " << *hms1_Iter;
   cout  << "." << endl;

   // This is the specialized template version of swap
   swap( hms1, hms3 );

   cout << "After swapping with hms3, list hms1 is:";
   for ( hms1_Iter = hms1.begin( ); hms1_Iter != hms1.end( );
         hms1_Iter++ )
         cout << " " << *hms1_Iter;
   cout   << "." << endl;
}
```

```Output
The original hash_multiset hms1 is: 10 20 30.
After swapping with hms2, list hms1 is: 200 100.
After swapping with hms3, list hms1 is: 300.
```

## <a name="upper_bound"></a>hash_multiset::upper_bound

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_multiset třída](../standard-library/unordered-multiset-class.md).

Vrátí iterátor na první prvek v hash_multiset s klíčem, který je větší než zadaný klíč.

```cpp
const_iterator upper_bound(const Key& key) const;

iterator upper_bound(const Key& key);
```

### <a name="parameters"></a>Parametry

\ *klíčů*
Klíč argumentu, který se má porovnat s klíčem řazení prvku z prohledávané hash_multisety.

### <a name="return-value"></a>Návratová hodnota

[Iterátor](#iterator) nebo [const_iterator](#const_iterator) , které řeší umístění prvního prvku v hash_multiset s klíčem větším, než je klíč argumentu, nebo který řeší umístění, které následuje po posledním elementu v hash_multiset, pokud se nenajde shoda pro zkrat.

### <a name="remarks"></a>Poznámky

### <a name="example"></a>Příklad

```cpp
// hash_multiset_upper_bound.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;
   hash_multiset <int> :: const_iterator hms1_AcIter, hms1_RcIter;

   hms1.insert( 10 );
   hms1.insert( 20 );
   hms1.insert( 30 );

   hms1_RcIter = hms1.upper_bound( 20 );
   cout << "The first element of hash_multiset hms1" << endl
        << "with a key greater than 20 is: "
        << *hms1_RcIter << "." << endl;

   hms1_RcIter = hms1.upper_bound( 30 );

   // If no match is found for the key, end( ) is returned
   if ( hms1_RcIter == hms1.end( ) )
      cout << "The hash_multiset hms1 doesn't have an element\n"
           << "with a key greater than 30." << endl;
   else
      cout << "The element of hash_multiset hms1"
           << "with a key > 40 is: "
           << *hms1_RcIter << "." << endl;

   // An element at a specific location in the hash_multiset can be
   // found by using a dereferenced iterator addressing the location
   hms1_AcIter = hms1.begin( );
   hms1_RcIter = hms1.upper_bound( *hms1_AcIter );
   cout << "The first element of hms1 with a key greater than "
        << endl << "that of the initial element of hms1 is: "
        << *hms1_RcIter << "." << endl;
}
```

```Output
The first element of hash_multiset hms1
with a key greater than 20 is: 30.
The hash_multiset hms1 doesn't have an element
with a key greater than 30.
The first element of hms1 with a key greater than
that of the initial element of hms1 is: 20.
```

## <a name="value_comp"></a>hash_multiset::value_comp

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_multiset třída](../standard-library/unordered-multiset-class.md).

Načte kopii objektu porovnání, která se používá k seřazení hodnot prvků v hash_multiset.

```cpp
value_compare value_comp() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí *vlastnosti*parametru šablony hash_multiset, které obsahují objekty funkce, které jsou použity k hodnotě hash a k uspořádání prvků kontejneru.

Další informace o *vlastnostích* naleznete v tématu [třídy hash_multiset](../standard-library/hash-multiset-class.md) .

### <a name="remarks"></a>Poznámky

Uložený objekt definuje členskou funkci:

**bool – operátor**( **constKey &** `_xVal`, **const Key &** *_yVal*);

Vrátí **hodnotu true** , pokud `_xVal` předchází a není rovna `_yVal` v pořadí řazení.

Všimněte si, že obě [key_compare](#key_compare) a [value_compare](#value_compare) jsou synonyma pro *vlastnosti*parametrů šablony. Oba typy jsou k dispozici pro třídy hash_multiset a hash_multiset, kde jsou identické, pro zajištění kompatibility s třídami hash_map a hash_multimap, kde jsou odlišné.

### <a name="example"></a>Příklad

```cpp
// hash_multiset_value_comp.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;

   hash_multiset <int, hash_compare < int, less<int> > > hms1;
   hash_multiset <int, hash_compare < int, less<int> > >::value_compare
      vc1 = hms1.value_comp( );
   bool result1 = vc1( 2, 3 );
   if( result1 == true )
   {
      cout << "vc1( 2,3 ) returns value of true, "
           << "where vc1 is the function object of hms1."
           << endl;
   }
   else
   {
      cout << "vc1( 2,3 ) returns value of false, "
           << "where vc1 is the function object of hms1."
           << endl;
   }

   hash_multiset <int, hash_compare < int, greater<int> > > hms2;
   hash_multiset<int, hash_compare < int, greater<int> > >::
           value_compare vc2 = hms2.value_comp( );
   bool result2 = vc2( 2, 3 );
   if( result2 == true )
   {
      cout << "vc2( 2,3 ) returns value of true, "
           << "where vc2 is the function object of hms2."
           << endl;
   }
   else
   {
      cout << "vc2( 2,3 ) returns value of false, "
           << "where vc2 is the function object of hms2."
           << endl;
   }
}
```

```Output
vc1( 2,3 ) returns value of true, where vc1 is the function object of hms1.
vc2( 2,3 ) returns value of false, where vc2 is the function object of hms2.
```

## <a name="value_compare"></a>hash_multiset::value_compare

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_multiset třída](../standard-library/unordered-multiset-class.md).

Typ, který poskytuje dva objekty Functions, binární predikát porovnání třídy, který může porovnat dvě hodnoty prvku hash_multiset a určit jejich relativní pořadí a unární predikát, který prvky vyhodnotí.

```cpp
typedef key_compare value_compare;
```

### <a name="remarks"></a>Poznámky

`value_compare` je synonymum pro *vlastnosti*parametrů šablony.

Další informace o *vlastnostích* naleznete v tématu [třídy hash_multiset](../standard-library/hash-multiset-class.md) .

Všimněte si, že [key_compare](#key_compare) i `value_compare` jsou synonyma pro *vlastnosti*parametrů šablony. Oba typy jsou k dispozici pro třídy nastavené a multiset, kde jsou identické, pro kompatibilitu s mapami tříd a multimap, kde jsou odlišné.

### <a name="example"></a>Příklad

Příklad, jak deklarovat a používat `value_compare`, naleznete v tématu příklad pro [value_comp](#value_comp) .

## <a name="value_type"></a>hash_multiset::value_type

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_multiset třída](../standard-library/unordered-multiset-class.md).

Typ, který popisuje objekt uložený jako prvek jako hash_multiset v jeho kapacitě jako hodnota.

```cpp
typedef Key value_type;
```

### <a name="example"></a>Příklad

```cpp
// hash_multiset_value_type.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;
   hash_multiset <int>::iterator hms1_Iter;

   // Declare value_type
   hash_multiset <int> :: value_type hmsvt_Int;

   hmsvt_Int = 10;   // Initialize value_type

   // Declare key_type
   hash_multiset <int> :: key_type hmskt_Int;
   hmskt_Int = 20;             // Initialize key_type

   hms1.insert( hmsvt_Int );         // Insert value into s1
   hms1.insert( hmskt_Int );         // Insert key into s1

   // A hash_multiset accepts key_types or value_types as elements
   cout << "The hash_multiset has elements:";
   for ( hms1_Iter = hms1.begin() ; hms1_Iter != hms1.end( );
         hms1_Iter++)
      cout << " " << *hms1_Iter;
      cout << "." << endl;
}
```

```Output
The hash_multiset has elements: 10 20.
```

## <a name="see-also"></a>Viz také:

[Bezpečnost vlákna ve C++ standardní knihovně](../standard-library/thread-safety-in-the-cpp-standard-library.md) \
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)
