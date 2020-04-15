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
ms.openlocfilehash: 8888f393e1058e3cd5ff968d9433b5306cac4949
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370655"
---
# <a name="hash_multiset-class"></a>hash_multiset – třída

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_multiset Class](../standard-library/unordered-multiset-class.md).

Třída kontejneru hash_multiset je rozšíření standardní knihovny Jazyka C++ a používá se pro ukládání a rychlé načítání dat z kolekce, ve které hodnoty obsažené prvky slouží jako klíčové hodnoty a nemusí být jedinečné.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Key, class Traits =hash_compare<Key, less <Key>>, class Allocator =allocator <Key>>
class hash_multiset
```

### <a name="parameters"></a>Parametry

*Klíč*\
Datový typ prvku, který má být uložen v hash_multiset.

*Vlastnosti*\
Typ, který obsahuje dva objekty funkce, jeden z třídy porovnat, který je binární predikát schopen porovnat dva element hodnoty jako klíče řazení k určení jejich relativní pořadí a `size_t`hash funkce, která je unární predikát mapování klíčových hodnot prvků neznatelná celá čísla typu . Tento argument je volitelný `hash_compare<Key, less<Key> >` a je výchozí hodnota.

*Přidělování*\
Typ, který představuje uložený objekt přidělování, který zapouzdřuje podrobnosti o přidělení hash_multiset a přidělení paměti. Tento argument je volitelný a `allocator<Key>`výchozí hodnota je .

## <a name="remarks"></a>Poznámky

Hash_multiset je:

- Asociativní kontejner, což je kontejner proměnné velikosti, který podporuje efektivní načtení hodnoty prvku založené na přiřazené hodnotě klíče. Dále je to jednoduchý asociativní kontejner, protože jeho hodnoty prvku jsou jeho hodnoty klíče.

- Oboustranný, protože poskytuje obousměrný iterátor pro přístup k jeho prvkům.

- Hashed, protože jeho prvky jsou seskupeny do bloků na základě hodnoty funkce hash aplikované na klíčové hodnoty prvků.

- Jedinečný v tom smyslu, že každý z jeho prvků musí mít jedinečný klíč. Vzhledem k tomu, hash_multiset je také jednoduchý asociativní kontejner, jeho prvky jsou také jedinečné.

- Šablona třídy, protože funkce, které poskytuje, je obecná a tak nezávislá na konkrétním typu dat obsažených jako prvky nebo klíče. Datové typy použité pro prvky a klíče jsou místo toho zadány jako parametry v šabloně třídy společně s funkcí porovnání a alokátorem.

Hlavní výhodou zapisování přes řazení je větší efektivita: úspěšné zapisování provádí vložení, odstranění a najde v konstantní mzda v průměru ve srovnání s časem úměrným logaritmu počet prvků v kontejneru pro řazení techniky. Hodnotu prvku v sadě nelze změnit přímo. Místo toho musíte odstranit staré hodnoty a vložit prvky s novými hodnotami.

Volba typu kontejneru by měla obecně vycházet z typu vyhledávání a vkládání vyžadovaného aplikací. Hashed asociativní kontejnery jsou optimalizovány pro operace vyhledávání, vkládání a odstraňování. Členské funkce, které explicitně podporují tyto operace jsou efektivní při použití s dobře navržené funkce hash, jejich provádění v čase, který je v průměru konstantní a není závislý na počtu prvků v kontejneru. Dobře navržená funkce hash vytváří rovnoměrné rozložení hodnot hash a minimalizuje počet kolizí, kde se říká, že ke kolizi dochází, když jsou odlišné hodnoty klíče mapovány na stejnou hodnotu hash. V nejhorším případě s nejhorší možnou funkcí hash je počet operací úměrný počtu prvků v sekvenci (lineární čas).

Hash_multiset by měl být asociativní kontejner volby při podmínky přisouvání hodnoty s jejich klíče jsou splněny aplikací. Prvky hash_multiset může být více a slouží jako jejich vlastní klíče řazení, takže klíče nejsou jedinečné. Model pro tento typ struktury je uspořádaný seznam slov, v němž se slova mohou vyskytovat více než jednou. Pokud by nebylo povoleno více výskytů slov, byla by hash_set příslušnou strukturou kontejneru. Pokud byly jedinečné definice připojeny jako hodnoty k seznamu jedinečných klíčových slov, pak by hash_map byla vhodnou strukturou pro obsahující tato data. Pokud místo toho definice nebyly jedinečné, pak hash_multimap by kontejner volby.

Hash_multiset seřídí sekvenci, kterou řídí voláním uloženého objektu vlastností hash typu [value_compare](#value_compare). K tomuto uloženému objektu lze přistupovat voláním key_comp členské [funkce](#key_comp). Takový objekt funkce se musí chovat stejně `hash_compare<Key, less<Key> >`jako objekt třídy . Konkrétně pro všechny *Key* hodnoty `Key`Key typu `Trait(Key)` , volání dává rozdělení `size_t`hodnot typu .

Obecně, tyto prvky musí být menší než srovnatelné pro toto pořadí, což znamená, že když jsou uvedeny dva prvky, může být stanoveno, zda jsou ekvivalentní (v tom smyslu, že ani jeden není menší než ten druhý), nebo že jeden je menší než druhý. To má za výsledek řazení mezi neekvivalentními prvky. Technicky je funkce porovnání binárním predikátem, který indukuje přísné slabé řazení, standardním matematickým způsobem. Binární predikát *f*( *x*, *y*) je objekt funkce, který má dva argumenty objekty x a y a vrácenou hodnotu true nebo false. Řazení uložené na hash_multiset je přísné slabé řazení, pokud je binární predikát nereflexivní, antisymetrický a tranzitivní a pokud je rovnocennost přenositá, kde jsou dva objekty x a y definovány jako rovnocenné, pokud jsou oba *f*( *x*, *y*) a *f*( *y*, *x*) false. Pokud silnější podmínka rovnosti mezi klíči nahradí ekvivalenci, stane se pořadí celkovým (v tom smyslu, že všechny prvky jsou uspořádány ve vztahu k sobě navzájem) a odpovídající klíče budou od sebe nerozeznatelné.

Skutečné pořadí prvků v řízené sekvenci závisí na funkci hash, funkci řazení a aktuální velikost tabulky hash uložené v objektu kontejneru. Nelze určit aktuální velikost tabulky hash, takže obecně nelze předpovědět pořadí prvků v řízené sekvenci. Vkládání prvků nezruší platnost žádných iterátorů a odstranění prvků zruší platnost pouze těch iterátorů, které výslovně odkazovaly na odstraněné prvky.

Iterátor poskytované hash_multiset třídy je obousměrný iterátor, ale funkce členů třídy vložit a hash_multiset mít verze, které berou jako parametry šablony slabší vstupní iterátor, jehož požadavky na funkčnost jsou minimální než ty, které jsou zaručeny třídou obousměrné iterátory. Různé koncepty iterátorů tvoří rodinu týkající se upřesnění jejich funkčnosti. Každý koncept iterátoru má své vlastní hash_multiset požadavků a algoritmy, které s nimi pracují, musí omezit své předpoklady na požadavky poskytované tímto typem iterátoru. Lze předpokládat, že ke vstupnímu iterátoru lze přistoupit přes ukazatel pro odkazování na některý objekt a že může být zvýšen na další iterátor v pořadí. Jedná se o minimální hash_multiset funkčnosti, ale stačí, abyste mohli smysluplně hovořit o `first`řadě iterátorů [ , `last`) v kontextu funkcí členů třídy.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[hash_multiset](#hash_multiset)|Konstrukce, `hash_multiset` který je prázdný nebo který je kopií celé `hash_multiset`nebo části některé jiné .|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[allocator_type](#allocator_type)|Typ, který `allocator` představuje třídu `hash_multiset` pro objekt.|
|[const_iterator](#const_iterator)|Typ, který poskytuje obousměrný iterátor, který může číst `hash_multiset` **const** prvek v .|
|[const_pointer](#const_pointer)|Typ, který poskytuje ukazatel na **const** element v `hash_multiset`.|
|[const_reference](#const_reference)|Typ, který poskytuje odkaz na **const** `hash_multiset` prvek uložený v a pro čtení a provádění **const** operací.|
|[const_reverse_iterator](#const_reverse_iterator)|Typ, který poskytuje obousměrný iterátor, který může číst `hash_multiset`libovolný **prvek const** v .|
|[difference_type](#difference_type)|Podepsaný typ celé číslo, který poskytuje rozdíl mezi dvěma iterátory, které adresují prvky v rámci stejného `hash_multiset`.|
|[Iterace](#iterator)|Typ, který poskytuje obousměrný iterátor, který může číst `hash_multiset`nebo upravovat libovolný prvek v rozhraní .|
|[key_compare](#key_compare)|Typ, který poskytuje objekt funkce, který může porovnat dva klíče řazení `hash_multiset`k určení relativní pořadí dvou prvků v .|
|[key_type](#key_type)|Typ, který popisuje objekt uložený jako `hash_set` prvek v jeho kapacitě jako klíč řazení.|
|[ukazatel](#pointer)|Typ, který poskytuje ukazatel na `hash_multiset`prvek v .|
|[Odkaz](#reference)|Typ, který poskytuje odkaz na prvek `hash_multiset`uložený v .|
|[reverse_iterator](#reverse_iterator)|Typ, který poskytuje obousměrný iterátor, který může číst nebo `hash_multiset`upravovat prvek v obráceném .|
|[size_type](#size_type)|Nepodepsaný podnosný typ, který může představovat počet prvků v . `hash_multiset`|
|[value_compare](#value_compare)|Typ, který poskytuje dva objekty funkce, binární predikát třídy `hash_multiset` porovnat, které lze porovnat dva elementové hodnoty a k určení jejich relativní pořadí a unární predikát, který zařazuje hodnoty prvků.|
|[value_type](#value_type)|Typ, který popisuje objekt uložený jako `hash_multiset` prvek v jeho kapacitě jako hodnotu.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[Začít](#begin)|Vrátí iterátor, který řeší první prvek `hash_multiset`v rozhraní .|
|[cbegin](#cbegin)|Vrátí const iterator adresující první `hash_multiset`prvek v rozhraní .|
|[cend](#cend)|Vrátí const iterátor, který řeší umístění, které následuje `hash_multiset`poslední prvek v .|
|[Jasné](#clear)|Vymaže všechny `hash_multiset`prvky .|
|[Počet](#count)|Vrátí počet prvků v `hash_multiset` klíči, jejichž klíč odpovídá klíči zadanému parametrem.|
|[crbegin](#crbegin)|Vrátí const iterator adresování první `hash_multiset`prvek v obrácené .|
|[crend](#crend)|Vrátí const iterator, který řeší umístění, které následuje `hash_multiset`poslední prvek v obráceném .|
|[místo](#emplace)|Vloží prvek vytvořený na místě `hash_multiset`do .|
|[emplace_hint](#emplace_hint)|Vloží prvek vytvořený na místě `hash_multiset`do aplikace s nápovědou k umístění.|
|[empty](#empty)|Testuje, `hash_multiset` pokud je prázdný.|
|[Konec](#end)|Vrátí iterátor, který řeší umístění, které následuje `hash_multiset`poslední prvek v rozhraní .|
|[equal_range](#equal_range)|Vrátí dvojici iterátorů respektive první prvek v `hash_multiset` klíč s klíčem, který je větší než zadaný klíč a na první prvek s `hash_multiset` klíčem, který je roven nebo větší než klíč.|
|[Vymazat](#erase)|Odebere prvek nebo rozsah prvků `hash_multiset` v a ze zadané pozice nebo odebere prvky, které odpovídají zadanému klíči.|
|[find](#find)|Vrátí iterátor adresování umístění prvku `hash_multiset` v, který má klíč ekvivalentní zadaný klíč.|
|[get_allocator](#get_allocator)|Vrátí kopii `allocator` objektu použitého `hash_multiset`k vytvoření .|
|[Vložit](#insert)|Vloží prvek nebo rozsah prvků do `hash_multiset`.|
|[key_comp](#key_compare)|Načte kopii objektu porovnání použitého `hash_multiset`k objednání klíčů v .|
|[lower_bound](#lower_bound)|Vrátí iterátor k prvnímu prvku `hash_multiset` v a s klíčem, který je roven nebo větší než zadaný klíč.|
|[max_size](#max_size)|Vrátí maximální délku `hash_multiset`.|
|[rbegin](#rbegin)|Vrátí iterátor adresující první prvek `hash_multiset`v obráceném .|
|[rend](#rend)|Vrátí iterátor, který řeší umístění, které následuje poslední `hash_multiset`prvek v obráceném .|
|[Velikost](#size)|Vrátí počet prvků v `hash_multiset`rozhraní .|
|[Swap](#swap)|Vyměňuje prvky `hash_multiset`dvou s.|
|[upper_bound](#upper_bound)|Vrátí iterátor prvnímu prvku v `hash_multiset` a, který s klíčem, který je roven nebo větší než zadaný klíč.|
|[value_comp](#value_comp)|Načte kopii objektu vlastností hash použitého k hodnotám `hash_multiset`klíče hash a objednaného prvku v rozhraní .|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[hash_multiset::operátor=](#op_eq)|Nahradí prvky hash_multiset kopií jiného hash_multiset.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<> hash_set

**Obor názvů:** stdext

## <a name="hash_multisetallocator_type"></a><a name="allocator_type"></a>hash_multiset::allocator_type

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_multiset Class](../standard-library/unordered-multiset-class.md).

Typ, který představuje třídu alokátoru pro objekt hash_multiset.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::allocator_type allocator_type;
```

### <a name="example"></a>Příklad

Viz příklad pro [get_allocator](#get_allocator) příklad pomocí`allocator_type`

## <a name="hash_multisetbegin"></a><a name="begin"></a>hash_multiset::začátek

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_multiset Class](../standard-library/unordered-multiset-class.md).

Vrátí iterátor, který řeší první prvek v hash_multiset.

```cpp
const_iterator begin() const;

iterator begin();
```

### <a name="return-value"></a>Návratová hodnota

Obousměrný itečelní objekt adresující první prvek v hash_multiset nebo umístění, které následuje prázdný hash_multiset.

### <a name="remarks"></a>Poznámky

Pokud `begin` je vrácená hodnota `const_iterator`přiřazena k , prvky v objektu hash_multiset nelze změnit. Pokud `begin` je vrácená hodnota `iterator`přiřazena k , prvky v objektu hash_multiset lze změnit.

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

## <a name="hash_multisetcbegin"></a><a name="cbegin"></a>hash_multiset::cbegin

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_multiset Class](../standard-library/unordered-multiset-class.md).

Vrátí const iterator, který řeší první prvek v hash_multiset.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>Návratová hodnota

Konstovat obousměrný iterátor adresování první prvek v [hash_multiset](../standard-library/hash-multiset-class.md) nebo `hash_multiset`umístění, které následuje prázdné .

### <a name="remarks"></a>Poznámky

S vrácenou `cbegin`hodnotou , `hash_multiset` prvky v objektu nelze změnit.

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

## <a name="hash_multisetcend"></a><a name="cend"></a>hash_multiset::cenzura

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_multiset Class](../standard-library/unordered-multiset-class.md).

Vrátí const iterator, který řeší umístění, které následuje poslední prvek v hash_multiset.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>Návratová hodnota

Konstovat obousměrný iterátor, který řeší umístění, které následuje poslední prvek v [hash_multiset](../standard-library/hash-multiset-class.md). Pokud `hash_multiset` je prázdný, `hash_multiset::cend == hash_multiset::begin`pak .

### <a name="remarks"></a>Poznámky

`cend`se používá k testování, zda iterátor dosáhl `hash_multiset`konce svého . Hodnota vrácená `cend` by neměla být odkazována.

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

## <a name="hash_multisetclear"></a><a name="clear"></a>hash_multiset::vymazat

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_multiset Class](../standard-library/unordered-multiset-class.md).

Vymaže všechny prvky hash_multiset.

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

## <a name="hash_multisetconst_iterator"></a><a name="const_iterator"></a>hash_multiset::const_iterator

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_multiset Class](../standard-library/unordered-multiset-class.md).

Typ, který poskytuje obousměrný iterátor, který může číst **const** prvek v hash_multiset.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_iterator const_iterator;
```

### <a name="remarks"></a>Poznámky

Typ `const_iterator` nelze použít ke změně hodnoty prvku.

### <a name="example"></a>Příklad

Viz příklad pro [začátek](#begin) pro příklad pomocí `const_iterator`.

## <a name="hash_multisetconst_pointer"></a><a name="const_pointer"></a>hash_multiset::const_pointer

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_multiset Class](../standard-library/unordered-multiset-class.md).

Typ, který poskytuje ukazatel na **const** prvek v hash_multiset.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::const_pointer const_pointer;
```

### <a name="remarks"></a>Poznámky

Typ `const_pointer` nelze použít ke změně hodnoty prvku.

Ve většině případů by měl být [použit const_iterator](#const_iterator) pro přístup k prvkům v **objektu const** hash_multiset.

## <a name="hash_multisetconst_reference"></a><a name="const_reference"></a>hash_multiset::const_reference

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_multiset Class](../standard-library/unordered-multiset-class.md).

Typ, který poskytuje odkaz na **prvek const** uložený v hash_multiset pro čtení a provádění operací **const.**

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

## <a name="hash_multisetconst_reverse_iterator"></a><a name="const_reverse_iterator"></a>hash_multiset::const_reverse_iterator

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_multiset Class](../standard-library/unordered-multiset-class.md).

Typ, který poskytuje obousměrný iterátor, který může číst libovolný **prvek const** v hash_multiset.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_reverse_iterator const_reverse_iterator;
```

### <a name="remarks"></a>Poznámky

Typ `const_reverse_iterator` nemůže změnit hodnotu prvku a používá se k iterátu přes hash_multiset v opačném pořadí.

### <a name="example"></a>Příklad

Příklad pro [rend](#rend) naleznete v příkladu, jak `const_reverse_iterator`deklarovat a používat .

## <a name="hash_multisetcount"></a><a name="count"></a>hash_multiset::počet

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_multiset Class](../standard-library/unordered-multiset-class.md).

Vrátí počet prvků v hash_multiset jehož klíč odpovídá klíči zadanému parametrem.

```cpp
size_type count(const Key& key) const;
```

### <a name="parameters"></a>Parametry

*Klíč*\
Klíč prvků, které mají být uzavřeno z hash_multiset.

### <a name="return-value"></a>Návratová hodnota

Počet prvků v hash_multiset s klíčem zadaným parametrem.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí počet prvků v následujícím rozsahu:

\[lower_bound(*klíč),* upper_bound(*klíč*).

### <a name="example"></a>Příklad

Následující příklad ukazuje použití hash_multiset::count členské funkce.

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

## <a name="hash_multisetcrbegin"></a><a name="crbegin"></a>hash_multiset::crbegin

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_multiset Class](../standard-library/unordered-multiset-class.md).

Vrátí const iterator adresování první prvek v obrácené matné hash_multiset.

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>Návratová hodnota

Const reverzní obousměrný iterátor adresování první prvek v obrácené [hash_multiset](../standard-library/hash-multiset-class.md) nebo řešení toho, co bylo poslední prvek v unreverse `hash_multiset`.

### <a name="remarks"></a>Poznámky

`crbegin`se používá s `hash_multiset` obráceným stejně [jako hash_multiset::begin](#begin) se používá s `hash_multiset`.

S vrácenou `crbegin`hodnotou `hash_multiset` aplikace nelze objekt změnit.

`crbegin`lze použít k iterovat přes `hash_multiset` dozadu.

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

## <a name="hash_multisetcrend"></a><a name="crend"></a>hash_multiset::crend

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_multiset Class](../standard-library/unordered-multiset-class.md).

Vrátí const iterátor, který řeší umístění, které následuje poslední prvek v obráceném hash_multiset.

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>Návratová hodnota

Const reverzní obousměrný iterátor, který řeší umístění, které následuje poslední prvek v obrácené [morhash_multiset](../standard-library/hash-multiset-class.md) (umístění, které předcházelo první prvek v unreverse). `hash_multiset`

### <a name="remarks"></a>Poznámky

`crend`se používá s `hash_multiset` obráceným stejně [jako hash_multiset::end](#end) se používá s `hash_multiset`.

S vrácenou `crend`hodnotou `hash_multiset` aplikace nelze objekt změnit.

`crend`lze použít k testování, zda reverzní iterátor dosáhl konce svého hash_multiset.

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

## <a name="hash_multisetdifference_type"></a><a name="difference_type"></a>hash_multiset::difference_type

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_multiset Class](../standard-library/unordered-multiset-class.md).

Podepsaný typ celé číslo, který poskytuje rozdíl mezi dvěma iterátory, které adresují prvky v rámci stejné hash_multiset.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::difference_type difference_type;
```

### <a name="remarks"></a>Poznámky

Je `difference_type` typ vrácena při odečtení nebo zvýšení prostřednictvím iterátory kontejneru. Obvykle `difference_type` se používá k reprezentaci počtu prvků `first` `last`v rozsahu [ , `first` ) `last`mezi iterátory `first` a , zahrnuje prvek, na který se vztahuje, a rozsah prvků až do prvku, na který je však `last`nezahrnuto.

Všimněte `difference_type` si, že i když je k dispozici pro všechny iterátory, které splňují požadavky vstupníitekor, který zahrnuje třídu obousměrné iterátory podporované reverzibilní kontejnery, jako je sada. Odčítání mezi iterátory je podporováno pouze iterátory s náhodným přístupem poskytovaným kontejnerem s náhodným přístupem, jako je vektor nebo deque.

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

## <a name="hash_multisetemplace"></a><a name="emplace"></a>hash_multiset::emplace

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_multiset Class](../standard-library/unordered-multiset-class.md).

Vloží prvek vytvořený na místě do hash_multiset.

```cpp
template <class ValTy>
iterator insert(ValTy&& val);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|-|-|
|*Val*|Hodnota prvku, který má být [hash_multiset](../standard-library/hash-multiset-class.md) vložen do `hash_multiset` hash_multiset pokud již obsahuje tento prvek nebo obecněji prvek, jehož klíč je ekvivalentní objednané.|

### <a name="return-value"></a>Návratová hodnota

Členská `emplace` funkce vrátí iterátor, který odkazuje na pozici, kde byl vložen nový prvek.

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

## <a name="hash_multisetemplace_hint"></a><a name="emplace_hint"></a>hash_multiset::emplace_hint

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_multiset Class](../standard-library/unordered-multiset-class.md).

Vloží prvek vytvořený na místě do hash_multiset s nápovědou k umístění.

```cpp
template <class ValTy>
iterator insert(
    const_iterator where,
    ValTy&& val);
```

### <a name="parameters"></a>Parametry

*Val*\
Hodnota prvku, který má být [hash_multiset](../standard-library/hash-multiset-class.md) vložen do `hash_multiset` hash_multiset pokud již obsahuje tento prvek nebo obecněji prvek, jehož klíč je ekvivalentní objednané.

*Kde*\
Místo zahájení vyhledání správného bodu vložení. (Vložení může dojít v amortizované konstantní čas, namísto logaritmického času, pokud kurzor bezprostředně *následuje, kde*.)

### <a name="return-value"></a>Návratová hodnota

Funkce [hash_multiset::emplace](#emplace) vrátí iterátor, který odkazuje na pozici, kde byl `hash_multiset`vložen nový prvek do .

### <a name="remarks"></a>Poznámky

Vložení může dojít v amortizované konstantní čas, namísto logaritmického času, pokud kurzor bezprostředně následuje *kde*.

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

## <a name="hash_multisetempty"></a><a name="empty"></a>hash_multiset::prázdný

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_multiset Class](../standard-library/unordered-multiset-class.md).

Testuje, pokud je hash_multiset prázdný.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Návratová hodnota

**true,** pokud je hash_multiset prázdná; **false,** pokud hash_multiset není prázdný.

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

## <a name="hash_multisetend"></a><a name="end"></a>hash_multiset::konec

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_multiset Class](../standard-library/unordered-multiset-class.md).

Vrátí iterátor, který řeší umístění, které následuje poslední prvek v hash_multiset.

```cpp
const_iterator end() const;

iterator end();
```

### <a name="return-value"></a>Návratová hodnota

Obousměrný iterátor, který řeší umístění, které následuje poslední prvek v hash_multiset. Pokud je hash_multiset prázdný, pak hash_multiset::end == hash_multiset::begin.

### <a name="remarks"></a>Poznámky

`end`se používá k testování, zda iterátor dosáhl konce svého hash_multiset. Hodnota vrácená `end` by neměla být odkazována.

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

## <a name="hash_multisetequal_range"></a><a name="equal_range"></a>hash_multiset::equal_range

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_multiset Class](../standard-library/unordered-multiset-class.md).

Vrátí dvojici iterátorů respektive první prvek v hash_multiset s klíčem, který je větší než zadaný klíč a první prvek v hash_multiset s klíčem, který je roven nebo větší než klíč.

```cpp
pair <const_iterator, const_iterator> equal_range (const Key& key) const;

pair <iterator, iterator> equal_range (const Key& key);
```

### <a name="parameters"></a>Parametry

*Klíč*\
Klíč argumentu, který má být porovnán s klíčem řazení prvku z hash_multiset prohledáván.

### <a name="return-value"></a>Návratová hodnota

Dvojice iterátorů, kde první je [lower_bound](#lower_bound) klíče a druhá je [upper_bound](#upper_bound) klíče.

Chcete-li získat přístup k prvnímu iterátoru `pr` `pr`dvojice vrácené členovou funkcí, použijte . **nejprve** a dereference dolní mez iterátoru, použití \*( `pr`. **první**). Chcete-li získat přístup k druhému iterátoru `pr` `pr`dvojice vrácené členovou funkcí, použijte . **a** pro dereferenci horní mez iterátoru, použití \*( `pr`. **za druhé**).

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

## <a name="hash_multiseterase"></a><a name="erase"></a>hash_multiset::vymazat

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_multiset Class](../standard-library/unordered-multiset-class.md).

Odebere prvek nebo rozsah prvků v hash_multiset ze zadaných pozic nebo odebere prvky, které odpovídají zadanému klíči.

```cpp
iterator erase(iterator where);

iterator erase(iterator first, iterator last);

size_type erase(const key_type& key);
```

### <a name="parameters"></a>Parametry

*Kde*\
Umístění prvku, který má být odebrán z hash_multiset.

*První*\
Pozice prvního prvku odstraněného z hash_multiset.

*Poslední*\
Umístěte těsně za poslední prvek odstraněný z hash_multiset.

*Klíč*\
Klíč prvků, které mají být odstraněny z hash_multiset.

### <a name="return-value"></a>Návratová hodnota

Pro první dvě členské funkce obousměrný iterátor, který označuje první prvek zbývající za všechny prvky odebrány nebo ukazatel na konec hash_multiset pokud žádný takový prvek neexistuje. Pro třetí členskou funkci počet prvků, které byly odebrány z hash_multiset.

### <a name="remarks"></a>Poznámky

Členské funkce nikdy vyvolat výjimku.

### <a name="example"></a>Příklad

Následující příklad ukazuje použití hash_multiset::erase členské funkce.

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

## <a name="hash_multisetfind"></a><a name="find"></a>hash_multiset::najít

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_multiset Class](../standard-library/unordered-multiset-class.md).

Vrátí iterátor adresování umístění prvku v hash_multiset, který má klíč ekvivalentní zadaný klíč.

```cpp
iterator find(const Key& key);

const_iterator find(const Key& key) const;
```

### <a name="parameters"></a>Parametry

*Klíč*\
Klíč argumentu, který má být porovnán s klíčem řazení prvku z hash_multiset prohledáván.

### <a name="return-value"></a>Návratová hodnota

[Iterátor](#iterator) nebo [const_iterator,](#const_iterator) který řeší umístění prvku ekvivalentního zadanému klíči nebo který řeší umístění, které následuje poslední prvek v hash_multiset pokud pro klíč není nalezena žádná shoda.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí iterátor, který řeší prvek v hash_multiset `equivalent` jehož klíč řazení je klíč argumentu pod binární predikát, který indukuje řazení na základě méně než vztah srovnatelnosti.

Pokud `find` je vrácená hodnota `const_iterator`přiřazena aplikaci , nelze objekt hash_multiset změnit. Pokud `find` je vrácená hodnota `iterator`přiřazena k aplikaci , lze změnit objekt hash_multiset.

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

## <a name="hash_multisetget_allocator"></a><a name="get_allocator"></a>hash_multiset::get_allocator

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_multiset Class](../standard-library/unordered-multiset-class.md).

Vrátí kopii objektu alokátoru použitého ke vytvoření hash_multiset.

```cpp
Allocator get_allocator() const;
```

### <a name="return-value"></a>Návratová hodnota

Alokátor používaný hash_multiset ke správě paměti, což je parametr `Allocator`šablony třídy .

Další informace `Allocator`naleznete v části Poznámky v tématu [hash_multiset třída.](../standard-library/hash-multiset-class.md)

### <a name="remarks"></a>Poznámky

Alokátory pro třídu hash_multiset určují, jak třída spravuje úložiště. Výchozí alokátory dodávané s třídami kontejneru standardní knihovny jazyka C++ jsou dostatečné pro většinu potřeb programování. Psaní a používání vlastní třídy přidělování je pokročilé téma jazyka C++.

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

## <a name="hash_multisethash_multiset"></a><a name="hash_multiset"></a>hash_multiset::hash_multiset

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_multiset Class](../standard-library/unordered-multiset-class.md).

Konstrukce, `hash_multiset` který je prázdný nebo který je kopií celé `hash_multiset`nebo části některé jiné .

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

*Al*\
Třída alokátoru úložiště, která `hash_multiset` má být použita `Allocator`pro tento objekt, který je ve výchozím nastavení .

*Comp*\
Funkce porovnání typu `const Traits` použitého k seřizování prvků v rozhraní `hash_multiset`, které jsou ve výchozím nastavení . `hash_compare`

*Právo*\
Z `hash_multiset` nichž je `hash_multiset` konstruována kopie.

*První*\
Umístění prvního prvku v rozsahu prvků, které mají být zkopírovány.

*Poslední*\
Pozice první prvek mimo rozsah prvků, které mají být zkopírovány.

*Ilist*\
Initializer_list, který obsahuje prvky, které mají být zkopírovány.

### <a name="remarks"></a>Poznámky

Všechny konstruktory uložit typ objektu alokátoru, který `hash_multiset` spravuje úložiště paměti pro a které mohou být později vráceny voláním [hash_multiset::get_allocator](#get_allocator). Parametr allocator je často v deklaraci třídy vynechán a makra předběžného zpracování jsou použita k nahrazení alternativních alokátorů.

Všechny konstruktory inicializují své hash_multisets.

Všechny konstruktory uložit objekt `Traits` funkce typu, který se používá k `hash_multiset` vytvoření pořadí mezi klíči a které mohou být později vráceny voláním [hash_multiset::key_comp](#key_comp). Další informace `Traits` naleznete v tématu [hash_multiset třídy.](../standard-library/hash-multiset-class.md)

První tři konstruktory určují `hash_multiset`prázdnou iniciálu , druhou určující typ funkce porovnání (*Comp),* která má být použita při stanovení pořadí prvků, a třetí explicitně specifikuje typ alokátoru (*Al*), který má být použit. Klíčové slovo **explicitní** potlačí určité druhy automatického převodu typu.

Čtvrtý konstruktor přesune `hash_multiset` `Right`.

Pátý, šestý a sedmý konstruktory používají initializer_list.

Poslední tři konstruktory zkopírují `first` `last`rozsah [ `hash_multiset` , ) s rostoucí explicitní při určování typu funkce porovnání třídy Porovnání a přidělování.

Skutečné pořadí prvků v kontejneru hash set závisí na funkci hash, funkci řazení a aktuální velikost tabulky hash a obecně nelze předpovědět, jak by to mohlo s kontejnerem sady, kde bylo určeno pouze funkcí řazení.

## <a name="hash_multisetinsert"></a><a name="insert"></a>hash_multiset::vložit

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_multiset Class](../standard-library/unordered-multiset-class.md).

Vloží prvek nebo rozsah prvků do hash_multiset.

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

*Hodnotu*\
Hodnota prvku, který má být vložen do hash_multiset, pokud hash_multiset již obsahuje tento prvek nebo obecněji prvek, jehož klíč je ekvivalentní objednané.

*Kde*\
Místo zahájení vyhledání správného bodu vložení. (Vložení může dojít v amortizované konstantní čas, namísto logaritmického času, pokud kurzor bezprostředně *následuje, kde*.)

*První*\
Pozice prvního prvku, který má být zkopírován z hash_multiset.

*Poslední*\
Pozice těsně za poslední prvek, který má být zkopírován z hash_multiset.

*Ilist*\
initializer_list, který obsahuje prvky ke kopírování.

### <a name="return-value"></a>Návratová hodnota

První dvě funkce vložit člen vrátí iterátor, který odkazuje na pozici, kde byl vložen nový prvek.

Další tři členské funkce používají initializer_list.

Třetí členská funkce vloží posloupnost hodnot prvků do hash_multiset odpovídající každému prvku, který je `first` `last`adresován iterátorem v rozsahu [ , ) zadaného hash_multiset.

### <a name="remarks"></a>Poznámky

Vložení může dojít v amortizované konstantní čas pro nápovědu verzi vložit, namísto logaritmického času, pokud kurzor bezprostředně následuje *kde*.

## <a name="hash_multisetiterator"></a><a name="iterator"></a>hash_multiset::iterátor

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_multiset Class](../standard-library/unordered-multiset-class.md).

Typ, který poskytuje obousměrný iterátor, který může číst nebo upravovat libovolný prvek v hash_multiset.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::iterator iterator;
```

### <a name="remarks"></a>Poznámky

Typ `iterator` lze změnit hodnotu prvku.

### <a name="example"></a>Příklad

Viz příklad pro [začátek](#begin) pro příklad, `iterator`jak deklarovat a používat .

## <a name="hash_multisetkey_comp"></a><a name="key_comp"></a>hash_multiset::key_comp

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_multiset Class](../standard-library/unordered-multiset-class.md).

Načte kopii objektu porovnání použitého k objednání klíčů v hash_multiset.

```cpp
key_compare key_comp() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hash_multiset parametr šablony *Vlastnosti*, který obsahuje objekty funkce, které se používají k hash a pořadí prvků kontejneru.

Další informace o *vlastnostech* naleznete v tématu [hash_multiset třída.](../standard-library/hash-multiset-class.md)

### <a name="remarks"></a>Poznámky

Uložený objekt definuje členovou funkci:

`bool operator<(const Key& _xVal, const Key& _yVal);`

který vrátí `_xVal` **hodnotu true,** pokud `_yVal` předchází, a není rovna v pořadí řazení.

Všimněte si, že [key_compare](#key_compare) i [value_compare](#value_compare) jsou synonyma pro *vlastnosti*parametru šablony . Oba typy jsou k dispozici pro třídy hash_multiset a hash_multiset, kde jsou identické, pro kompatibilitu s hash_map a hash_multimap třídy, kde jsou odlišné.

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

## <a name="hash_multisetkey_compare"></a><a name="key_compare"></a>hash_multiset::key_compare

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_multiset Class](../standard-library/unordered-multiset-class.md).

Typ, který poskytuje dva objekty funkce, binární predikát třídy porovnat, které lze porovnat dva elementové hodnoty hash_multiset k určení jejich relativní pořadí a unární predikát, který hodnoty zatříděny prvky.

```cpp
typedef Traits key_compare;
```

### <a name="remarks"></a>Poznámky

`key_compare`je synonymem pro parametr znakové *vlastnosti*šablony .

Další informace o *vlastnostech* naleznete v tématu [hash_multiset třída.](../standard-library/hash-multiset-class.md)

Všimněte `key_compare` si, že oba a value_compare jsou synonyma pro *vlastnosti*parametru šablony . Oba typy jsou k dispozici pro třídy hash_set a hash_multiset, kde jsou identické, pro kompatibilitu s hash_map a hash_multimap třídy, kde jsou odlišné.

### <a name="example"></a>Příklad

Příklad pro [key_comp](#key_comp) naleznete příklad deklarace `key_compare`a používání .

## <a name="hash_multisetkey_type"></a><a name="key_type"></a>hash_multiset::key_type

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_multiset Class](../standard-library/unordered-multiset-class.md).

Typ, který poskytuje objekt funkce, který může porovnat klíče řazení k určení relativní pořadí dvou prvků v hash_multiset.

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>Poznámky

`key_type`je synonymem pro parametr šablony *Klíč*.

Všimněte `key_type` si, že oba a [value_type](../standard-library/hash-set-class.md#value_type) jsou synonyma pro parametr šablony *Key*. Oba typy jsou k dispozici pro set a vícesetové třídy, kde jsou identické, pro kompatibilitu s map a multimap třídy, kde jsou odlišné.

Další informace o *klíči*naleznete v části Poznámky v tématu [hash_multiset třídy.](../standard-library/hash-multiset-class.md)

### <a name="example"></a>Příklad

Příklad pro [value_type](#value_type) například, jak deklarovat a používat `key_type`.

## <a name="hash_multisetlower_bound"></a><a name="lower_bound"></a>hash_multiset::lower_bound

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_multiset Class](../standard-library/unordered-multiset-class.md).

Vrátí iterátor prvnímu prvku v hash_multiset s klíčem, který je roven nebo větší než zadaný klíč.

```cpp
const_iterator lower_bound(const Key& key) const;

iterator lower_bound(const Key& key);
```

### <a name="parameters"></a>Parametry

*Klíč*\
Klíč argumentu, který má být porovnán s klíčem řazení prvku z hash_multiset prohledáván.

### <a name="return-value"></a>Návratová hodnota

[Iterátor](#iterator) nebo [const_iterator,](#const_iterator) který řeší umístění prvního prvku v hash_multiset s klíčem, který je roven nebo větší než klíč argumentu nebo který řeší umístění, které následuje poslední prvek v hash_multiset pokud pro klíč není nalezena žádná shoda.

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

## <a name="hash_multisetmax_size"></a><a name="max_size"></a>hash_multiset::max_size

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_multiset Class](../standard-library/unordered-multiset-class.md).

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

## <a name="hash_multisetoperator"></a><a name="op_eq"></a>hash_multiset::operátor=

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_multiset Class](../standard-library/unordered-multiset-class.md).

Nahradí prvky hash_multiset kopií jiného hash_multiset.

```cpp
hash_multiset& operator=(const hash_multiset& right);

hash_multiset& operator=(hash_multiset&& right);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|-|-|
|*Právo*|Hash_multiset [hash_multiset](../standard-library/hash-multiset-class.md) zkopírován `hash_multiset`do .|

### <a name="remarks"></a>Poznámky

Po vymazání všech existujících `hash_multiset` `operator=` prvků v aplikaci zkopíruje `hash_multiset`nebo přesune obsah *vpravo* do .

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

## <a name="hash_multisetpointer"></a><a name="pointer"></a>hash_multiset::pointer

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_multiset Class](../standard-library/unordered-multiset-class.md).

Typ, který poskytuje ukazatel na prvek v hash_multiset.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::pointer pointer;
```

### <a name="remarks"></a>Poznámky

Typ `pointer` lze změnit hodnotu prvku.

Ve většině případů [iterátor](#iterator) by měl být použit pro přístup k prvkům v objektu více sad.

## <a name="hash_multisetrbegin"></a><a name="rbegin"></a>hash_multiset::začátek

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_multiset Class](../standard-library/unordered-multiset-class.md).

Vrátí iterátor adresující první prvek v obráceném hash_multiset.

```cpp
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```

### <a name="return-value"></a>Návratová hodnota

Reverzní obousměrný iterátor adresování první prvek v obrácené hash_multiset nebo adresování, co bylo poslední prvek v unreverse hash_multiset.

### <a name="remarks"></a>Poznámky

`rbegin`se používá s obráceným hash_multiset stejně jako [začátek](#begin) se používá s hash_multiset.

Pokud `rbegin` je vrácená hodnota `const_reverse_iterator`přiřazena aplikaci , nelze hash_multiset objekt změnit. Pokud `rbegin` je vrácená hodnota `reverse_iterator`přiřazena k , pak hash_multiset objekt upravil.

`rbegin`lze itetovat přes hash_multiset dozadu.

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

## <a name="hash_multisetreference"></a><a name="reference"></a>hash_multiset::odkaz

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_multiset Class](../standard-library/unordered-multiset-class.md).

Typ, který poskytuje odkaz na prvek uložený v hash_multiset.

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

## <a name="hash_multisetrend"></a><a name="rend"></a>hash_multiset::rend

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_multiset Class](../standard-library/unordered-multiset-class.md).

Vrátí iterátor, který řeší umístění, které následuje poslední prvek v obráceném hash_multiset.

```cpp
const_reverse_iterator rend() const;

reverse_iterator rend();
```

### <a name="return-value"></a>Návratová hodnota

Reverzní obousměrný iterátor, který řeší umístění, které následuje poslední prvek v obráceném hash_multiset (umístění, které předcházelo prvnímu prvku v neobrácené masce hash_multiset).

### <a name="remarks"></a>Poznámky

`rend`se používá s obráceným hash_multiset [stejně](#end) jako konec se používá s hash_multiset.

Pokud `rend` je vrácená hodnota `const_reverse_iterator`přiřazena aplikaci , nelze hash_multiset objekt změnit. Pokud `rend` je vrácená hodnota `reverse_iterator`přiřazena k , pak hash_multiset objekt upravil. Hodnota vrácená `rend` by neměla být odkazována.

`rend`lze použít k testování, zda reverzní iterátor dosáhl konce svého hash_multiset.

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

## <a name="hash_multisetreverse_iterator"></a><a name="reverse_iterator"></a>hash_multiset::reverse_iterator

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_multiset Class](../standard-library/unordered-multiset-class.md).

Typ, který poskytuje obousměrný iterátor, který může číst nebo upravovat prvek v obráceném hash_multiset.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::reverse_iterator reverse_iterator;
```

### <a name="remarks"></a>Poznámky

Typ `reverse_iterator` se používá k iterátu přes hash_multiset v opačném směru.

### <a name="example"></a>Příklad

Příklad pro [rbegin](#rbegin) pro příklad, jak `reverse_iterator`deklarovat a používat .

## <a name="hash_multisetsize"></a><a name="size"></a>hash_multiset::velikost

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_multiset Class](../standard-library/unordered-multiset-class.md).

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

## <a name="hash_multisetsize_type"></a><a name="size_type"></a>hash_multiset::size_type

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_multiset Class](../standard-library/unordered-multiset-class.md).

Nepodepsaný podčíslení typ, který může představovat počet prvků v hash_multiset.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::size_type size_type;
```

### <a name="remarks"></a>Poznámky

### <a name="example"></a>Příklad

Příklad [velikosti](#size) naleznete v příkladu, jak deklarovat a používat`size_type`

## <a name="hash_multisetswap"></a><a name="swap"></a>hash_multiset::swap

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_multiset Class](../standard-library/unordered-multiset-class.md).

Vyměňuje prvky dvou hash_multisets.

```cpp
void swap(hash_multiset& right);
```

### <a name="parameters"></a>Parametry

*Právo*\
Argument hash_multiset poskytuje prvky, které mají být vyměněny za cílovou hash_multiset.

### <a name="remarks"></a>Poznámky

Členská funkce zruší platnost žádné odkazy, ukazatele nebo iterátory, které označují prvky ve dvou hash_multisets, jejichž prvky jsou vyměňovány.

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

## <a name="hash_multisetupper_bound"></a><a name="upper_bound"></a>hash_multiset::upper_bound

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_multiset Class](../standard-library/unordered-multiset-class.md).

Vrátí iterátor prvnímu prvku v hash_multiset s klíčem, který je větší než zadaný klíč.

```cpp
const_iterator upper_bound(const Key& key) const;

iterator upper_bound(const Key& key);
```

### <a name="parameters"></a>Parametry

*Klíč*\
Klíč argumentu, který má být porovnán s klíčem řazení prvku z hash_multiset prohledáván.

### <a name="return-value"></a>Návratová hodnota

[Iterátor](#iterator) nebo [const_iterator,](#const_iterator) který řeší umístění prvního prvku v hash_multiset s klíčem větším než klíč argumentu nebo který řeší umístění, které následuje poslední prvek v hash_multiset pokud pro klíč není nalezena žádná shoda.

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

## <a name="hash_multisetvalue_comp"></a><a name="value_comp"></a>hash_multiset::value_comp

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_multiset Class](../standard-library/unordered-multiset-class.md).

Načte kopii objektu porovnání použitého k pořadí hodnot prvků v hash_multiset.

```cpp
value_compare value_comp() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hash_multiset parametr šablony *Vlastnosti*, který obsahuje objekty funkce, které se používají k hash a pořadí prvků kontejneru.

Další informace o *vlastnostech* naleznete v tématu [hash_multiset třída.](../standard-library/hash-multiset-class.md)

### <a name="remarks"></a>Poznámky

Uložený objekt definuje členovou funkci:

**bool operátor** **(constKey&** `_xVal`, **const Key&** *_yVal);*

který vrátí `_xVal` **hodnotu true,** pokud `_yVal` předchází, a není rovna v pořadí řazení.

Všimněte si, že [key_compare](#key_compare) i [value_compare](#value_compare) jsou synonyma pro *vlastnosti*parametru šablony . Oba typy jsou k dispozici pro třídy hash_multiset a hash_multiset, kde jsou identické, pro kompatibilitu s hash_map a hash_multimap třídy, kde jsou odlišné.

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

## <a name="hash_multisetvalue_compare"></a><a name="value_compare"></a>hash_multiset::value_compare

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_multiset Class](../standard-library/unordered-multiset-class.md).

Typ, který poskytuje dva objekty funkce, binární predikát třídy porovnat, které lze porovnat dva elementové hodnoty hash_multiset k určení jejich relativní pořadí a unární predikát, který hodnoty zatříděny prvky.

```cpp
typedef key_compare value_compare;
```

### <a name="remarks"></a>Poznámky

`value_compare`je synonymem pro parametr znakové *vlastnosti*šablony .

Další informace o *vlastnostech* naleznete v tématu [hash_multiset třída.](../standard-library/hash-multiset-class.md)

Všimněte si, `value_compare` že oba [key_compare](#key_compare) a jsou synonyma pro *vlastnosti*parametru šablony . Oba typy jsou k dispozici pro sady tříd a multiset, kde jsou identické, pro kompatibilitu s mapa tříd a multimap, kde jsou odlišné.

### <a name="example"></a>Příklad

Příklad pro [value_comp](#value_comp) například, jak deklarovat a používat `value_compare`.

## <a name="hash_multisetvalue_type"></a><a name="value_type"></a>hash_multiset::value_type

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_multiset Class](../standard-library/unordered-multiset-class.md).

Typ, který popisuje objekt uložený jako prvek jako prvek hash_multiset v jeho kapacitě jako hodnotu.

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

## <a name="see-also"></a>Viz také

[Bezpečnost vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Referenční příručka standardní knihovny jazyka C++](../standard-library/cpp-standard-library-reference.md)
