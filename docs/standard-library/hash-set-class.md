---
title: hash_set – třída
ms.date: 11/04/2016
f1_keywords:
- hash_set/stdext::hash_set
- hash_set/stdext::hash_set::allocator_type
- hash_set/stdext::hash_set::const_iterator
- hash_set/stdext::hash_set::const_pointer
- hash_set/stdext::hash_set::const_reference
- hash_set/stdext::hash_set::const_reverse_iterator
- hash_set/stdext::hash_set::difference_type
- hash_set/stdext::hash_set::iterator
- hash_set/stdext::hash_set::key_compare
- hash_set/stdext::hash_set::key_type
- hash_set/stdext::hash_set::pointer
- hash_set/stdext::hash_set::reference
- hash_set/stdext::hash_set::reverse_iterator
- hash_set/stdext::hash_set::size_type
- hash_set/stdext::hash_set::value_compare
- hash_set/stdext::hash_set::value_type
- hash_set/stdext::hash_set::begin
- hash_set/stdext::hash_set::cbegin
- hash_set/stdext::hash_set::cend
- hash_set/stdext::hash_set::clear
- hash_set/stdext::hash_set::count
- hash_set/stdext::hash_set::crbegin
- hash_set/stdext::hash_set::crend
- hash_set/stdext::hash_set::emplace
- hash_set/stdext::hash_set::emplace_hint
- hash_set/stdext::hash_set::empty
- hash_set/stdext::hash_set::end
- hash_set/stdext::hash_set::equal_range
- hash_set/stdext::hash_set::erase
- hash_set/stdext::hash_set::find
- hash_set/stdext::hash_set::get_allocator
- hash_set/stdext::hash_set::insert
- hash_set/stdext::hash_set::key_comp
- hash_set/stdext::hash_set::lower_bound
- hash_set/stdext::hash_set::max_size
- hash_set/stdext::hash_set::rbegin
- hash_set/stdext::hash_set::rend
- hash_set/stdext::hash_set::size
- hash_set/stdext::hash_set::swap
- hash_set/stdext::hash_set::upper_bound
- hash_set/stdext::hash_set::value_comp
helpviewer_keywords:
- stdext::hash_set
- stdext::hash_set::allocator_type
- stdext::hash_set::const_iterator
- stdext::hash_set::const_pointer
- stdext::hash_set::const_reference
- stdext::hash_set::const_reverse_iterator
- stdext::hash_set::difference_type
- stdext::hash_set::iterator
- stdext::hash_set::key_compare
- stdext::hash_set::key_type
- stdext::hash_set::pointer
- stdext::hash_set::reference
- stdext::hash_set::reverse_iterator
- stdext::hash_set::size_type
- stdext::hash_set::value_compare
- stdext::hash_set::value_type
- stdext::hash_set::begin
- stdext::hash_set::cbegin
- stdext::hash_set::cend
- stdext::hash_set::clear
- stdext::hash_set::count
- stdext::hash_set::crbegin
- stdext::hash_set::crend
- stdext::hash_set::emplace
- stdext::hash_set::emplace_hint
- stdext::hash_set::empty
- stdext::hash_set::end
- stdext::hash_set::equal_range
- stdext::hash_set::erase
- stdext::hash_set::find
- stdext::hash_set::get_allocator
- stdext::hash_set::insert
- stdext::hash_set::key_comp
- stdext::hash_set::lower_bound
- stdext::hash_set::max_size
- stdext::hash_set::rbegin
- stdext::hash_set::rend
- stdext::hash_set::size
- stdext::hash_set::swap
- stdext::hash_set::upper_bound
- stdext::hash_set::value_comp
ms.assetid: c765c06e-cbb6-48c2-93ca-d15468eb28d7
ms.openlocfilehash: becf038678f4abbe285e719e4d1cc1f3f12de982
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689539"
---
# <a name="hash_set-class"></a>hash_set – třída

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_set třída](../standard-library/unordered-set-class.md).

Třída kontejneru hash_set je rozšíření C++ standardní knihovny, které se používá pro úložiště a rychlé načítání dat z kolekce, ve které jsou hodnoty prvků, které jsou obsaženy, jedinečné a slouží jako klíčové hodnoty.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Key,
    class Traits=hash_compare<Key, less<Key>>,
    class Allocator=allocator<Key>>
class hash_set
```

### <a name="parameters"></a>Parametry

@No__t_1 *klíčů*
Typ dat prvku, který bude uložen v hash_set.

@No__t_1 *vlastností*
Typ, který obsahuje dva objekty funkce, jedno z porovnání třídy, které je binární predikát schopný porovnat dvě hodnoty elementů jako klíče řazení pro určení jejich relativního pořadí a funkci hash, která je unárním predikátem mapování hodnot klíčů prvků na nepodepsané celá čísla typu `size_t`. Tento argument je nepovinný a `hash_compare<Key, less<Key> >` je výchozí hodnota.

@No__t_1 *přidělování*
Typ, který představuje uložený objekt přidělování, který zapouzdřuje informace o přidělování hash_set's a navracení paměti. Tento argument je nepovinný a výchozí hodnota je `allocator<Key>`.

## <a name="remarks"></a>Poznámky

Hash_set je:

- Asociativní kontejner, což je kontejner proměnné velikosti, který podporuje efektivní načtení hodnoty prvku založené na přiřazené hodnotě klíče. Dále je to jednoduchý asociativní kontejner, protože jeho hodnoty prvku jsou jeho hodnoty klíče.

- Oboustranný, protože poskytuje obousměrný iterátor pro přístup k jeho prvkům.

- Hash, protože jeho prvky jsou seskupeny do kontejnerů na základě hodnoty funkce hash použité pro klíčové hodnoty prvků.

- Jedinečný v tom smyslu, že každý z jeho prvků musí mít jedinečný klíč. Vzhledem k tomu, že hash_set je také jednoduchý asociativní kontejner, jeho prvky jsou také jedinečné.

- Šablona třídy, protože funkce, které poskytuje, jsou obecné a nezávisle na konkrétním typu dat obsažených jako elementy nebo klíče. Datové typy použité pro prvky a klíče jsou místo toho zadány jako parametry v šabloně třídy společně s funkcí porovnání a alokátorem.

Hlavní výhodou použití algoritmu hash pro řazení je vyšší efektivita; úspěšné hashování provádí vložení, odstranění a vyhledá v konstantním průměrném čase v porovnání s časem, který je úměrný logaritmu počtu prvků v kontejneru pro řazení technik. Hodnotu prvku v sadě nelze změnit přímo. Místo toho musíte odstranit staré hodnoty a vložit prvky s novými hodnotami.

Volba typu kontejneru by měla obecně vycházet z typu vyhledávání a vkládání vyžadovaného aplikací. Asociativní kontejnery s algoritmem hash jsou optimalizované pro operace vyhledávání, vkládání a odebírání. Členské funkce, které explicitně podporují tyto operace, jsou efektivní při použití s dobře navrženou funkcí hash a jejich provádění v čase s průměrnou konstantou a nezávisle na počtu prvků v kontejneru. Dobře navržená funkce hash vytváří jednotnou distribuci hodnot hash a minimalizuje počet kolizí, kde je zřejmé, že se vyskytne při mapování jedinečných klíčových hodnot na stejnou hodnotu hash. V nejhorším případě s nejhorší možnou funkcí hash je počet operací úměrný počtu prvků v sekvenci (lineární čas).

Hash_set by měl být asociativní kontejner výběru, pokud podmínky přidružování hodnot k jejich klíčům jsou splněné aplikací. Prvky hash_set jsou jedinečné a slouží jako vlastní klíče řazení. Model pro tento typ struktury je uspořádaný seznam slov, v němž se slova mohou vyskytovat pouze jednou. Pokud bylo povoleno více výskytů slov, pak bude hash_multiset odpovídající strukturou kontejneru. Pokud jsou hodnoty nutné připojit k seznamu jedinečných klíčových slov, pak by hash_map byla vhodná struktura, která bude tato data obsahovat. Pokud místo toho klíče nejsou jedinečné, bude hash_multimap kontejnerem volby.

Hash_set objedná sekvenci, kterou řídí, voláním uložené hodnoty hash `Traits` objektu typu [value_compare](#value_compare). K tomuto uloženému objektu je možné přistupovat voláním členské funkce [key_comp](#key_comp). Takový objekt funkce se musí chovat stejně jako objekt třídy *hash_compare < Key, méně \<Key > >.* Konkrétně pro všechny hodnoty `key` typu klíč, hodnota vlastnosti volání (`key`) poskytuje distribuci hodnot typu size_t.

Obecně, tyto prvky musí být menší než srovnatelné pro toto pořadí, což znamená, že když jsou uvedeny dva prvky, může být stanoveno, zda jsou ekvivalentní (v tom smyslu, že ani jeden není menší než ten druhý), nebo že jeden je menší než druhý. Výsledkem je řazení mezi neekvivalentními prvky. Technicky je funkce porovnání binárním predikátem, který indukuje přísné slabé řazení, standardním matematickým způsobem. Binární predikát *f*( *x*, *y*) je objekt funkce, který má dva objekty argumentu x a y a návratovou hodnotu true nebo false. Řazení uložené na hash_set je přísné slabé seřazení, pokud je binární predikát Nereflexivní, antisymetrický a tranzitivní a je-li ekvivalence tranzitivní, kde jsou dva objekty *x* a *y* definovány jako ekvivalentní, když je nastaveno na hodnotu *f*( *x* , *y*) a *f*( *y*, *x*) jsou false. Pokud silnější podmínka rovnosti mezi klíči nahradí ekvivalenci, stane se pořadí celkovým (v tom smyslu, že všechny prvky jsou uspořádány ve vztahu k sobě navzájem) a odpovídající klíče budou od sebe nerozeznatelné.

Skutečné pořadí prvků v řízené sekvenci závisí na funkci hash, funkci řazení a aktuální velikosti zatřiďovací tabulky uložené v objektu kontejneru. Nelze určit aktuální velikost zatřiďovací tabulky, takže nemůžete obecné předpovědět pořadí prvků v řízené sekvenci. Vkládání prvků nezruší platnost žádných iterátorů a odstranění prvků zruší platnost pouze těch iterátorů, které výslovně odkazovaly na odstraněné prvky.

Iterátor poskytnutý třídou hash_set je obousměrný iterátor, ale funkce členských funkcí [INSERT](#insert) a [hash_set](#hash_set) mají verze, které přebírají jako parametry šablony slabší vstupní iterátor, jehož požadavky na funkčnost jsou větší. minimální než ta, která je zaručena třídou Obousměrných iterátorů. Různé koncepty iterátorů tvoří rodinu týkající se upřesnění jejich funkčnosti. Každý koncept iterátoru má vlastní sadu požadavků a algoritmy, které s nimi pracují, musí omezit jejich předpoklady na požadavky podle typu iterátoru. Lze předpokládat, že ke vstupnímu iterátoru lze přistoupit přes ukazatel pro odkazování na některý objekt a že může být zvýšen na další iterátor v pořadí. Toto je minimální sada funkcí, ale je dostatečná pro to, aby bylo možné mluvit smysluplně o rozsahu iterátorů [`first`, `last`) v kontextu funkcí členských tříd.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[hash_set](#hash_set)|Vytvoří `hash_set`, který je prázdný nebo který je kopií všech nebo částí jiných `hash_set`.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[allocator_type](#allocator_type)|Typ, který představuje třídu `allocator` pro objekt `hash_set`.|
|[const_iterator](#const_iterator)|Typ, který poskytuje obousměrný iterátor, který může číst `const` prvek v `hash_set`.|
|[const_pointer](#const_pointer)|Typ, který poskytuje ukazatel na prvek **const** v `hash_set`.|
|[const_reference](#const_reference)|Typ, který poskytuje odkaz na prvek **const** uložený v `hash_set` pro čtení a provádění operací **const** .|
|[const_reverse_iterator](#const_reverse_iterator)|Typ, který poskytuje obousměrný iterátor, který může číst libovolný prvek **const** v `hash_set`.|
|[difference_type](#difference_type)|Typ se znaménkem typu Integer, který lze použít k reprezentaci počtu prvků `hash_set` v rozsahu mezi prvky, na které odkazují iterátory.|
|[iterátor](#iterator)|Typ, který poskytuje obousměrný iterátor, který může číst nebo upravovat libovolný prvek v `hash_set`.|
|[key_compare](#key_compare)|Typ, který poskytuje objekt funkce, který může porovnat dva klíče řazení pro určení relativního pořadí dvou prvků v `hash_set`.|
|[key_type](#key_type)|Typ, který popisuje objekt uložený jako prvek `hash_set` v jeho kapacitě jako klíč řazení.|
|[ukazatele](#pointer)|Typ, který poskytuje ukazatel na prvek v `hash_set`.|
|[odkaz](#reference)|Typ, který poskytuje odkaz na prvek uložený v `hash_set`.|
|[reverse_iterator](#reverse_iterator)|Typ, který poskytuje obousměrný iterátor, který může číst nebo upravovat prvek v obráceném `hash_set`.|
|[size_type](#size_type)|Typ unsigned integer, který může představovat počet prvků v `hash_set`.|
|[value_compare](#value_compare)|Typ, který poskytuje dva objekty Functions, binární predikát porovnání třídy, který může porovnat dvě hodnoty prvku `hash_set` k určení jejich relativního pořadí a unární predikát, který prvky vyhodnotí.|
|[value_type](#value_type)|Typ, který popisuje objekt uložený jako prvek `hash_set` v jeho kapacitě jako hodnota.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[ifunctiondiscovery](#begin)|Vrátí iterátor, který adresuje první prvek v `hash_set`.|
|[cbegin](#cbegin)|Vrátí konstantní iterátor adresující první prvek v `hash_set`.|
|[cend](#cend)|Vrátí konstantní iterátor, který adresuje umístění následující po posledním prvku v `hash_set`.|
|[jejich](#clear)|Smaže všechny prvky `hash_set`.|
|[výpočtu](#count)|Vrátí počet prvků v `hash_set`, jejichž klíč odpovídá klíči určenému parametrem.|
|[crbegin –](#crbegin)|Vrátí konstantní iterátor adresující první prvek v obráceném `hash_set`.|
|[crend](#crend)|Vrátí konstantní iterátor, který adresuje umístění následující po posledním prvku v obráceném `hash_set`.|
|[emplace](#emplace)|Vloží prvek konstruovaný na místo do `hash_set`.|
|[emplace_hint](#emplace_hint)|Vloží prvek konstruovaný na místo do `hash_set` s pomocným parametrem umístění.|
|[obsahovat](#empty)|Testuje, zda je `hash_set` prázdné.|
|[účelu](#end)|Vrátí iterátor, který adresuje umístění následující po posledním prvku v `hash_set`.|
|[equal_range](#equal_range)|Vrátí dvojici iterátorů v uvedeném pořadí na první prvek v `hash_set` s klíčem, který je větší než zadaný klíč a na první prvek v `hash_set` s klíčem, který je roven nebo větší než klíč.|
|[ověřování](#erase)|Odebere prvek nebo rozsah prvků v `hash_set` ze zadané pozice nebo odstraní prvky, které odpovídají zadanému klíči.|
|[najít](#find)|Vrátí iterátor adresující umístění elementu v `hash_set`, který má klíč shodný se zadaným klíčem.|
|[get_allocator](#get_allocator)|Vrátí kopii objektu `allocator`, který se používá k vytvoření `hash_set`.|
|[zadat](#insert)|Vloží prvek nebo rozsah prvků do `hash_set`.|
|[key_comp](#key_comp)|Načte kopii objektu porovnání, která se používá k řazení klíčů v `hash_set`.|
|[lower_bound](#lower_bound)|Vrátí iterátor na první prvek v `hash_set` s klíčem, který je větší nebo roven zadanému klíči.|
|[max_size](#max_size)|Vrátí maximální délku `hash_set`.|
|[rbegin](#rbegin)|Vrátí iterátor adresující první prvek v obráceném `hash_set`.|
|[rend](#rend)|Vrátí iterátor, který adresuje umístění následující po posledním prvku v obráceném `hash_set`.|
|[hodnota](#size)|Vrátí počet prvků v `hash_set`.|
|[adresu](#swap)|Vyměňuje prvky dvou `hash_set`s.|
|[upper_bound](#upper_bound)|Vrátí iterátor na první prvek v `hash_set`, který má klíč, který je roven nebo větší než zadaný klíč.|
|[value_comp](#value_comp)|Načte kopii objektu zatřiďovacích vlastností, která se používá k hodnotě hash a seřazení hodnot klíčů elementu v `hash_set`.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[hash_set:: operator =](#op_eq)|Nahradí prvky `hash_set` kopií jiného `hash_set`.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<hash_set >

**Obor názvů:** stdext

## <a name="allocator_type"></a>hash_set::allocator_type

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_set třída](../standard-library/unordered-set-class.md).

Typ, který představuje třídu přidělování pro objekt hash_set.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::allocator_type allocator_type;
```

### <a name="remarks"></a>Poznámky

`allocator_type` je synonymum pro *přidělování*parametrů šablony.

Další informace o *přidělování*najdete v části poznámky tématu [třídy hash_set](../standard-library/hash-set-class.md) .

### <a name="example"></a>Příklad

Viz příklad pro [get_allocator](#get_allocator) pro příklad, který používá `allocator_type`.

## <a name="begin"></a>hash_set:: begin

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_set třída](../standard-library/unordered-set-class.md).

Vrátí iterátor, který adresuje první prvek v hash_set.

```cpp
const_iterator begin() const;

iterator begin();
```

### <a name="return-value"></a>Návratová hodnota

Obousměrný iterátor, který adresuje první prvek v hash_set nebo umístění, které je úspěšné pro prázdné hash_set.

### <a name="remarks"></a>Poznámky

Pokud je vrácená hodnota `begin` přiřazena k `const_iterator`, prvky v objektu hash_set nelze upravovat. Pokud je vrácená hodnota `begin` přiřazena k `iterator`, prvky v objektu hash_set lze upravit.

### <a name="example"></a>Příklad

```cpp
// hash_set_begin.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;
   hash_set <int>::iterator hs1_Iter;
   hash_set <int>::const_iterator hs1_cIter;

   hs1.insert( 1 );
   hs1.insert( 2 );
   hs1.insert( 3 );

   hs1_Iter = hs1.begin( );
   cout << "The first element of hs1 is " << *hs1_Iter << endl;

   hs1_Iter = hs1.begin( );
   hs1.erase( hs1_Iter );

   // The following 2 lines would err because the iterator is const
   // hs1_cIter = hs1.begin( );
   // hs1.erase( hs1_cIter );

   hs1_cIter = hs1.begin( );
   cout << "The first element of hs1 is now " << *hs1_cIter << endl;
}
```

```Output
The first element of hs1 is 1
The first element of hs1 is now 2
```

## <a name="cbegin"></a>hash_set:: cbegin

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_set třída](../standard-library/unordered-set-class.md).

Vrátí konstantní iterátor, který adresuje první prvek v hash_set.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>Návratová hodnota

Konstantní obousměrný iterátor, který adresuje první prvek v [hash_set](../standard-library/hash-set-class.md) nebo umístění, které je úspěšně prázdné `hash_set`.

### <a name="remarks"></a>Poznámky

S návratovou hodnotou `cbegin` nelze upravovat elementy v objektu `hash_set`.

### <a name="example"></a>Příklad

```cpp
// hash_set_cbegin.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;
   hash_set <int>::const_iterator hs1_cIter;

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

## <a name="cend"></a>hash_set:: cend

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_set třída](../standard-library/unordered-set-class.md).

Vrátí konstantní iterátor, který adresuje umístění následující po posledním prvku v hash_set.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>Návratová hodnota

Konstantní obousměrný iterátor, který adresuje umístění následující po posledním prvku v [hash_set](../standard-library/hash-set-class.md). Pokud je `hash_set` prázdné, `hash_set::cend == hash_set::begin`.

### <a name="remarks"></a>Poznámky

`cend` slouží k otestování, zda iterátor dosáhl konce jeho `hash_set`. Hodnota vrácená `cend` by neměla být zpětně odkazovaná.

### <a name="example"></a>Příklad

```cpp
// hash_set_cend.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;
   hash_set <int> :: const_iterator hs1_cIter;

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

## <a name="clear"></a>hash_set:: Clear

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_set třída](../standard-library/unordered-set-class.md).

Smaže všechny prvky hash_set.

```cpp
void clear();
```

### <a name="remarks"></a>Poznámky

### <a name="example"></a>Příklad

```cpp
// hash_set_clear.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;

   hs1.insert( 1 );
   hs1.insert( 2 );

   cout << "The size of the hash_set is initially " << hs1.size( )
        << "." << endl;

   hs1.clear( );
   cout << "The size of the hash_set after clearing is "
        << hs1.size( ) << "." << endl;
}
```

```Output
The size of the hash_set is initially 2.
The size of the hash_set after clearing is 0.
```

## <a name="const_iterator"></a>hash_set::const_iterator

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_set třída](../standard-library/unordered-set-class.md).

Typ, který poskytuje obousměrný iterátor, který může číst prvek **const** v hash_set.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_iterator const_iterator;
```

### <a name="remarks"></a>Poznámky

Typ `const_iterator` nelze použít pro úpravu hodnoty prvku.

### <a name="example"></a>Příklad

Viz příklad pro [začátek](#begin) příkladu, který používá `const_iterator`.

## <a name="const_pointer"></a>hash_set::const_pointer

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_set třída](../standard-library/unordered-set-class.md).

Typ, který poskytuje ukazatel na prvek **const** v hash_set.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_pointer const_pointer;
```

### <a name="remarks"></a>Poznámky

Typ `const_pointer` nelze použít pro úpravu hodnoty prvku.

Ve většině případů by měl být [const_iterator](#const_iterator) použit pro přístup k prvkům v objektu **const** hash_set.

## <a name="const_reference"></a>hash_set::const_reference

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_set třída](../standard-library/unordered-set-class.md).

Typ, který poskytuje odkaz na prvek **const** uložený v hash_set pro čtení a provádění operací **const** .

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_reference const_reference;
```

### <a name="remarks"></a>Poznámky

### <a name="example"></a>Příklad

```cpp
// hash_set_const_ref.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;

   hs1.insert( 10 );
   hs1.insert( 20 );

   // Declare and initialize a const_reference &Ref1
   // to the 1st element
   const int &Ref1 = *hs1.begin( );

   cout << "The first element in the hash_set is "
        << Ref1 << "." << endl;

   // The following line would cause an error because the
   // const_reference cannot be used to modify the hash_set
   // Ref1 = Ref1 + 5;
}
```

```Output
The first element in the hash_set is 10.
```

## <a name="const_reverse_iterator"></a>hash_set::const_reverse_iterator

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_set třída](../standard-library/unordered-set-class.md).

Typ, který poskytuje obousměrný iterátor, který může číst libovolný element **const** v hash_set.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_reverse_iterator const_reverse_iterator;
```

### <a name="remarks"></a>Poznámky

Typ `const_reverse_iterator` nemůže změnit hodnotu prvku a použít k iteraci přes hash_set v obráceném pořadí.

### <a name="example"></a>Příklad

Příklad, jak deklarovat a používat `const_reverse_iterator`, najdete v příkladu pro [rend](#rend) .

## <a name="count"></a>hash_set:: Count

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_set třída](../standard-library/unordered-set-class.md).

Vrátí počet prvků v hash_set, jejichž klíč odpovídá klíči určenému parametrem.

```cpp
size_type count(const Key& key) const;
```

### <a name="parameters"></a>Parametry

\ *klíčů*
Klíč prvků, které mají být porovnány s hash_set.

### <a name="return-value"></a>Návratová hodnota

1, pokud hash_set obsahuje element, jehož klíč řazení odpovídá klíči parametru.

0, pokud hash_set neobsahuje element se shodným klíčem.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí počet prvků v následujícím rozsahu:

\[ lower_bound (*klíč*), Upper_bound (*klíč*)).

### <a name="example"></a>Příklad

Následující příklad ukazuje použití členské funkce hash_set:: Count.

```cpp
// hash_set_count.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
    using namespace std;
    using namespace stdext;
    hash_set<int> hs1;
    hash_set<int>::size_type i;

    hs1.insert(1);
    hs1.insert(1);

    // Keys must be unique in hash_set, so duplicates are ignored.
    i = hs1.count(1);
    cout << "The number of elements in hs1 with a sort key of 1 is: "
         << i << "." << endl;

    i = hs1.count(2);
    cout << "The number of elements in hs1 with a sort key of 2 is: "
         << i << "." << endl;
}
```

```Output
The number of elements in hs1 with a sort key of 1 is: 1.
The number of elements in hs1 with a sort key of 2 is: 0.
```

## <a name="crbegin"></a>hash_set:: crbegin –

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_set třída](../standard-library/unordered-set-class.md).

Vrátí konstantní iterátor adresující první prvek v obráceném hash_setě.

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>Návratová hodnota

Konstantní reverzní obousměrný iterátor, který adresuje první prvek v obráceném [hash_set](../standard-library/hash-set-class.md) nebo řeší, co byl poslední prvek v neobráceném `hash_set`.

### <a name="remarks"></a>Poznámky

`crbegin` se používá s obráceným hash_set stejně jako [hash_set:: begin](#begin) se používá s hash_set.

S návratovou hodnotou `crbegin` nelze změnit objekt `hash_set`.

`crbegin` lze použít k iteraci `hash_set` zpět.

### <a name="example"></a>Příklad

```cpp
// hash_set_crbegin.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;
   hash_set <int>::const_reverse_iterator hs1_crIter;

   hs1.insert( 10 );
   hs1.insert( 20 );
   hs1.insert( 30 );

   hs1_crIter = hs1.crbegin( );
   cout << "The first element in the reversed hash_set is "
        << *hs1_crIter << "." << endl;
}
```

```Output
The first element in the reversed hash_set is 30.
```

## <a name="crend"></a>hash_set:: crend

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_set třída](../standard-library/unordered-set-class.md).

Vrátí konstantní iterátor, který adresuje umístění následující po posledním prvku v obráceném hash_setě.

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>Návratová hodnota

Const reverzní obousměrný iterátor, který adresuje umístění následující po posledním prvku v obráceném [hash_set](../standard-library/hash-set-class.md) (umístění, které předchází první prvek v neobráceném `hash_set`).

### <a name="remarks"></a>Poznámky

`crend` se používá s obráceným `hash_set` stejně jako [hash_set:: end](#end) se používá s `hash_set`.

S návratovou hodnotou `crend` nelze změnit objekt `hash_set`.

`crend` lze použít k otestování, zda reverzní iterátor dosáhl konce jeho `hash_set`.

### <a name="example"></a>Příklad

```cpp
// hash_set_crend.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;
   hash_set <int>::const_reverse_iterator hs1_crIter;

   hs1.insert( 10 );
   hs1.insert( 20 );
   hs1.insert( 30 );

   hs1_crIter = hs1.crend( );
   hs1_crIter--;
   cout << "The last element in the reversed hash_set is "
        << *hs1_crIter << "." << endl;
}
```

```Output
The last element in the reversed hash_set is 10.
```

## <a name="difference_type"></a>hash_set::d ifference_type

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_set třída](../standard-library/unordered-set-class.md).

Typ se znaménkem typu Integer, který lze použít k reprezentaci počtu prvků hash_set v rozsahu mezi prvky, na které odkazují iterátory.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::difference_type difference_type;
```

### <a name="remarks"></a>Poznámky

@No__t_0 je typ vrácený při odečítání nebo přírůstcích pomocí iterátorů kontejneru. @No__t_0 se obvykle používá k reprezentaci počtu prvků v rozsahu [`first`, `last`) mezi iterátory `first` a `last`, zahrnuje element, na který odkazuje `first`, a rozsah prvků až po , ale nezahrnuje prvek, na který ukazuje `last`.

Všimněte si, že i když `difference_type` je k dispozici pro všechny iterátory, které splňují požadavky vstupního iterátoru, které zahrnují třídu Obousměrných iterátorů podporovaných vratnými kontejnery, jako je například set, odečítání mezi iterátory je podporováno pouze pomocí iterátory s náhodným přístupem poskytované náhodným kontejnerem přístupu, jako je například Vector nebo deque.

### <a name="example"></a>Příklad

```cpp
// hash_set_diff_type.cpp
// compile with: /EHsc
#include <iostream>
#include <hash_set>
#include <algorithm>

int main( )
{
   using namespace std;
   using namespace stdext;

   hash_set <int> hs1;
   hash_set <int>::iterator hs1_Iter, hs1_bIter, hs1_eIter;

   hs1.insert( 20 );
   hs1.insert( 10 );
   hs1.insert( 20 );   // Won't insert as hash_set elements are unique

   hs1_bIter = hs1.begin( );
   hs1_eIter = hs1.end( );

   hash_set <int>::difference_type   df_typ5, df_typ10, df_typ20;

   df_typ5 = count( hs1_bIter, hs1_eIter, 5 );
   df_typ10 = count( hs1_bIter, hs1_eIter, 10 );
   df_typ20 = count( hs1_bIter, hs1_eIter, 20 );

   // The keys, and hence the elements, of a hash_set are unique,
   // so there is at most one of a given value
   cout << "The number '5' occurs " << df_typ5
        << " times in hash_set hs1.\n";
   cout << "The number '10' occurs " << df_typ10
        << " times in hash_set hs1.\n";
   cout << "The number '20' occurs " << df_typ20
        << " times in hash_set hs1.\n";

   // Count the number of elements in a hash_set
   hash_set <int>::difference_type  df_count = 0;
   hs1_Iter = hs1.begin( );
   while ( hs1_Iter != hs1_eIter)
   {
      df_count++;
      hs1_Iter++;
   }

   cout << "The number of elements in the hash_set hs1 is: "
        << df_count << "." << endl;
}
```

```Output
The number '5' occurs 0 times in hash_set hs1.
The number '10' occurs 1 times in hash_set hs1.
The number '20' occurs 1 times in hash_set hs1.
The number of elements in the hash_set hs1 is: 2.
```

## <a name="emplace"></a>hash_set:: emplace

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_set třída](../standard-library/unordered-set-class.md).

Vloží prvek konstruovaný na místo do hash_set.

```cpp
template <class ValTy>
pair <iterator, bool>
emplace(
    ValTy&& val);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|-|-|
|*počítává*|Hodnota prvku, který má být vložen do objektu [hash_set](../standard-library/hash-set-class.md) , pokud `hash_set` již tento prvek neobsahuje, nebo obecněji, což je objekt, jehož klíč je ekvivalentně seřazený.|

### <a name="return-value"></a>Návratová hodnota

Členská funkce `emplace` vrátí dvojici, jejíž **logická** komponenta vrátí **hodnotu true** , pokud byla vložena a **false** , pokud `hash_set` již obsahovala element, jehož klíč má ekvivalentní hodnotu v pořadí, a jehož iterátor součást vrátí adresu, kam byl vložen nový prvek nebo kde byl prvek již umístěn.

### <a name="remarks"></a>Poznámky

### <a name="example"></a>Příklad

```cpp
// hash_set_emplace.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>
#include <string>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set<string> hs3;
   string str1("a");

   hs3.emplace(move(str1));
   cout << "After the emplace insertion, hs3 contains "
      << *hs3.begin() << "." << endl;
}
```

```Output
After the emplace insertion, hs3 contains a.
```

## <a name="emplace_hint"></a>hash_set::emplace_hint

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_set třída](../standard-library/unordered-set-class.md).

Vloží prvek konstruovaný na místo do hash_set.

```cpp
template <class ValTy>
iterator emplace(
    const_iterator _Where,
    ValTy&& val);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|-|-|
|*počítává*|Hodnota prvku, který má být vložen do objektu [hash_set](../standard-library/hash-set-class.md) , pokud `hash_set` již tento prvek neobsahuje, nebo obecněji, což je objekt, jehož klíč je ekvivalentně seřazený.|
|*_Where*|Místo zahájení vyhledání správného bodu vložení. (Vložení se může vyskytnout v konstantním času v čase, namísto logaritmické doby, pokud kurzor hned následuje *_Where*.)|

### <a name="return-value"></a>Návratová hodnota

Členská funkce [hash_set:: emplace](#emplace) Vrátí iterátor, který odkazuje na pozici, kam byl nový element vložen do `hash_set`, nebo kde se nachází existující element s ekvivalentním řazením.

### <a name="remarks"></a>Poznámky

Vložení se může vyskytnout v konstantním času v čase, namísto logaritmické doby, pokud se bod vložení hned sleduje podle *_Where*.

### <a name="example"></a>Příklad

```cpp
// hash_set_emplace_hint.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>
#include <string>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set<string> hs3;
   string str1("a");

   hs3.insert(hs3.begin(), move(str1));
   cout << "After the emplace insertion, hs3 contains "
      << *hs3.begin() << "." << endl;
}
```

```Output
After the emplace insertion, hs3 contains a.
```

## <a name="empty"></a>hash_set:: Empty

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_set třída](../standard-library/unordered-set-class.md).

Testuje, zda je hash_set prázdné.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Návratová hodnota

**true** , pokud je hash_set prázdné; **false** , pokud je hash_set neprázdné.

### <a name="remarks"></a>Poznámky

### <a name="example"></a>Příklad

```cpp
// hash_set_empty.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1, hs2;
   hs1.insert ( 1 );

   if ( hs1.empty( ) )
      cout << "The hash_set hs1 is empty." << endl;
   else
      cout << "The hash_set hs1 is not empty." << endl;

   if ( hs2.empty( ) )
      cout << "The hash_set hs2 is empty." << endl;
   else
      cout << "The hash_set hs2 is not empty." << endl;
}
```

```Output
The hash_set hs1 is not empty.
The hash_set hs2 is empty.
```

## <a name="end"></a>hash_set:: end

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_set třída](../standard-library/unordered-set-class.md).

Vrátí iterátor, který adresuje umístění následující po posledním prvku v objektu hash_set.

```cpp
const_iterator end() const;

iterator end();
```

### <a name="return-value"></a>Návratová hodnota

Obousměrný iterátor, který adresuje umístění následující po posledním prvku v hash_set. Pokud je hash_set prázdné, potom hash_set:: end = = hash_set:: begin.

### <a name="remarks"></a>Poznámky

`end` slouží k otestování, zda iterátor dosáhl konce jeho hash_set. Hodnota vrácená `end` by neměla být zpětně odkazovaná.

### <a name="example"></a>Příklad

```cpp
// hash_set_end.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;
   hash_set <int> :: iterator hs1_Iter;
   hash_set <int> :: const_iterator hs1_cIter;

   hs1.insert( 1 );
   hs1.insert( 2 );
   hs1.insert( 3 );

   hs1_Iter = hs1.end( );
   hs1_Iter--;
   cout << "The last element of hs1 is " << *hs1_Iter << endl;

   hs1.erase( hs1_Iter );

   // The following 3 lines would err because the iterator is const:
   // hs1_cIter = hs1.end( );
   // hs1_cIter--;
   // hs1.erase( hs1_cIter );

   hs1_cIter = hs1.end( );
   hs1_cIter--;
   cout << "The last element of hs1 is now " << *hs1_cIter << endl;
}
```

```Output
The last element of hs1 is 3
The last element of hs1 is now 2
```

## <a name="equal_range"></a>hash_set::equal_range

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_set třída](../standard-library/unordered-set-class.md).

Vrátí dvojici iterátorů v uvedeném pořadí na první prvek sady hodnot hash s klíčem, který se rovná zadanému klíči a prvnímu prvku v sadě hodnot hash s klíčem, který je větší než klíč.

```cpp
pair <const_iterator, const_iterator> equal_range (const Key& key) const;

pair <iterator, iterator> equal_range (const Key& key);
```

### <a name="parameters"></a>Parametry

\ *klíčů*
Klíč argumentu, který se má porovnat s klíčem řazení prvku z prohledávané hash_sety.

### <a name="return-value"></a>Návratová hodnota

Pár iterátorů, kde první je [lower_bound](../standard-library/set-class.md#lower_bound) klíče a druhý je [Upper_bound](../standard-library/set-class.md#upper_bound) klíče.

Pro přístup k prvnímu iterátoru páru žádosti o přijetí změn vráceného členskou funkcí použijte `pr`. **nejprve**a pro zpětnou vazbu dolního iterátoru použijte \* (`pr`. **první**). Pro přístup k druhému iterátoru páru `pr` vráceném členskou funkcí použijte `pr`. za **druhé**a pro zpětnou vazbu k hornímu iterátoru použijte \* (`pr`. **sekundy**).

### <a name="remarks"></a>Poznámky

### <a name="example"></a>Příklad

```cpp
// hash_set_equal_range.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   typedef hash_set<int> IntHSet;
   IntHSet hs1;
   hash_set <int> :: const_iterator hs1_RcIter;

   hs1.insert( 10 );
   hs1.insert( 20 );
   hs1.insert( 30 );

   pair <IntHSet::const_iterator, IntHSet::const_iterator> p1, p2;
   p1 = hs1.equal_range( 20 );

   cout << "The upper bound of the element with "
        << "a key of 20 in the hash_set hs1 is: "
        << *(p1.second) << "." << endl;

   cout << "The lower bound of the element with "
        << "a key of 20 in the hash_set hs1 is: "
        << *(p1.first) << "." << endl;

   // Compare the upper_bound called directly
   hs1_RcIter = hs1.upper_bound( 20 );
   cout << "A direct call of upper_bound( 20 ) gives "
        << *hs1_RcIter << "," << endl
        << "matching the 2nd element of the pair"
        << " returned by equal_range( 20 )." << endl;

   p2 = hs1.equal_range( 40 );

   // If no match is found for the key,
   // both elements of the pair return end( )
   if ( ( p2.first == hs1.end( ) ) && ( p2.second == hs1.end( ) ) )
      cout << "The hash_set hs1 doesn't have an element "
           << "with a key greater than or equal to 40." << endl;
   else
      cout << "The element of hash_set hs1 with a key >= 40 is: "
           << *(p1.first) << "." << endl;
}
```

```Output
The upper bound of the element with a key of 20 in the hash_set hs1 is: 30.
The lower bound of the element with a key of 20 in the hash_set hs1 is: 20.
A direct call of upper_bound( 20 ) gives 30,
matching the 2nd element of the pair returned by equal_range( 20 ).
The hash_set hs1 doesn't have an element with a key greater than or equal to 40.
```

## <a name="erase"></a>hash_set:: Erase

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_set třída](../standard-library/unordered-set-class.md).

Odebere prvek nebo rozsah prvků v objektu hash_set ze zadané pozice nebo odstraní prvky, které odpovídají zadanému klíči.

```cpp
iterator erase(iterator _Where);

iterator erase(iterator first, iterator last);

size_type erase(const key_type& key);
```

### <a name="parameters"></a>Parametry

*_Where* \
Pozice prvku, který má být odebrán z hash_set.

*první* \
Pozice prvního prvku byla odebrána z hash_set.

*poslední* \
Pozice hned za posledním prvkem odebraným z hash_set.

\ *klíčů*
Klíč prvků, které mají být odebrány z hash_set.

### <a name="return-value"></a>Návratová hodnota

Pro první dvě členské funkce obousměrný iterátor, který určuje první prvek zbývající za odebranými prvky, nebo ukazatel na konec hash_set, pokud žádný takový prvek neexistuje. Pro třetí členskou funkci počet prvků, které byly odebrány z hash_set.

### <a name="remarks"></a>Poznámky

Členské funkce nikdy nevyvolají výjimku.

### <a name="example"></a>Příklad

Následující příklad ukazuje použití členské funkce hash_set:: Erase.

```cpp
// hash_set_erase.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main()
{
    using namespace std;
    using namespace stdext;
    hash_set<int> hs1, hs2, hs3;
    hash_set<int>::iterator pIter, Iter1, Iter2;
    int i;
    hash_set<int>::size_type n;

    for (i = 1; i < 5; i++)
    {
        hs1.insert (i);
        hs2.insert (i * i);
        hs3.insert (i - 1);
    }

    // The 1st member function removes an element at a given position
    Iter1 = ++hs1.begin();
    hs1.erase(Iter1);

    cout << "After the 2nd element is deleted, the hash_set hs1 is:";
    for (pIter = hs1.begin(); pIter != hs1.end(); pIter++)
        cout << " " << *pIter;
    cout << "." << endl;

    // The 2nd member function removes elements
    // in the range [ first,  last)
    Iter1 = ++hs2.begin();
    Iter2 = --hs2.end();
    hs2.erase(Iter1, Iter2);

    cout << "After the middle two elements are deleted, "
         << "the hash_set hs2 is:";
    for (pIter = hs2.begin(); pIter != hs2.end(); pIter++)
        cout << " " << *pIter;
    cout << "." << endl;

    // The 3rd member function removes elements with a given  key
    n = hs3.erase(2);

    cout << "After the element with a key of 2 is deleted, "
         << "the hash_set hs3 is:";
    for (pIter = hs3.begin(); pIter != hs3.end(); pIter++)
        cout << " " << *pIter;
    cout << "." << endl;

    // The 3rd member function returns the number of elements removed
    cout << "The number of elements removed from hs3 is: "
         << n << "." << endl;

    // The dereferenced iterator can also be used to specify a key
    Iter1 = ++hs3.begin();
    hs3.erase(Iter1);

    cout << "After another element (unique for hash_set) with a key "
         << endl;
    cout  << "equal to that of the 2nd element is deleted, "
          << "the hash_set hs3 is:";
    for (pIter = hs3.begin(); pIter != hs3.end(); pIter++)
        cout << " " << *pIter;
    cout << "." << endl;
}
```

```Output
After the 2nd element is deleted, the hash_set hs1 is: 1 3 4.
After the middle two elements are deleted, the hash_set hs2 is: 16 4.
After the element with a key of 2 is deleted, the hash_set hs3 is: 0 1 3.
The number of elements removed from hs3 is: 1.
After another element (unique for hash_set) with a key
equal to that of the 2nd element is deleted, the hash_set hs3 is: 0 3.
```

## <a name="find"></a>hash_set:: Find

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_set třída](../standard-library/unordered-set-class.md).

Vrátí iterátor adresující umístění elementu v hash_set, který má klíč odpovídající zadanému klíči.

```cpp
iterator find(const Key& key);

const_iterator find(const Key& key) const;
```

### <a name="parameters"></a>Parametry

\ *klíčů*
Klíč argumentu, který se má shodovat s klíčem řazení prvku z prohledávané hash_sety.

### <a name="return-value"></a>Návratová hodnota

@No__t_0 nebo `const_iterator`, které řeší umístění elementu, který odpovídá zadanému klíči, nebo který řeší umístění, které následuje po posledním prvku v hash_set, pokud není nalezena shoda pro klíč.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí iterátor, který adresuje element v hash_set, jehož klíč řazení je `equivalent` k klíči argumentu pod binárním predikátem, který vystaví řazení na základě vztahu srovnatelnosti menšího než.

Pokud je vrácená hodnota `find` přiřazena k `const_iterator`, objekt hash_set nelze změnit. Pokud je vrácená hodnota `find` přiřazena k `iterator`, lze objekt hash_set upravit.

### <a name="example"></a>Příklad

```cpp
// hash_set_find.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;
   hash_set <int> :: const_iterator hs1_AcIter, hs1_RcIter;

   hs1.insert( 10 );
   hs1.insert( 20 );
   hs1.insert( 30 );

   hs1_RcIter = hs1.find( 20 );
   cout << "The element of hash_set hs1 with a key of 20 is: "
        << *hs1_RcIter << "." << endl;

   hs1_RcIter = hs1.find( 40 );

   // If no match is found for the key, end( ) is returned
   if ( hs1_RcIter == hs1.end( ) )
      cout << "The hash_set hs1 doesn't have an element "
           << "with a key of 40." << endl;
   else
      cout << "The element of hash_set hs1 with a key of 40 is: "
           << *hs1_RcIter << "." << endl;

   // The element at a specific location in the hash_set can be found
   // by using a dereferenced iterator addressing the location
   hs1_AcIter = hs1.end( );
   hs1_AcIter--;
   hs1_RcIter = hs1.find( *hs1_AcIter );
   cout << "The element of hs1 with a key matching "
        << "that of the last element is: "
        << *hs1_RcIter << "." << endl;
}
```

```Output
The element of hash_set hs1 with a key of 20 is: 20.
The hash_set hs1 doesn't have an element with a key of 40.
The element of hs1 with a key matching that of the last element is: 30.
```

## <a name="get_allocator"></a>hash_set::get_allocator

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_set třída](../standard-library/unordered-set-class.md).

Vrátí kopii objektu přidělování, která se používá k vytvoření hash_set.

```cpp
Allocator get_allocator() const;
```

### <a name="return-value"></a>Návratová hodnota

Alokátor používaný hash_set ke správě paměti, což je *přidělování*parametrů šablony.

Další informace o *přidělování*najdete v části poznámky tématu [třídy hash_set](../standard-library/hash-set-class.md) .

### <a name="remarks"></a>Poznámky

Přidělování pro třídu hash_set určují, jak Třída spravuje úložiště. Výchozí přidělující třídy kontejnerů C++ standardní knihovny jsou dostačující pro většinu programovacích potřeb. Psaní a používání vlastního třídy přidělování je pokročilým C++ tématem.

### <a name="example"></a>Příklad

```cpp
// hash_set_get_allocator.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;

   // The following lines declare objects
   // that use the default allocator.
   hash_set <int, hash_compare <int, less<int> > > hs1;
   hash_set <int,  hash_compare <int, greater<int> > > hs2;
   hash_set <double, hash_compare <double,
      less<double> >, allocator<double> > hs3;

   hash_set <int, hash_compare <int,
      greater<int> > >::allocator_type hs2_Alloc;
   hash_set <double>::allocator_type hs3_Alloc;
   hs2_Alloc = hs2.get_allocator( );

   cout << "The number of integers that can be allocated"
        << endl << "before free memory is exhausted: "
        << hs1.max_size( ) << "." << endl;

   cout << "The number of doubles that can be allocated"
        << endl << "before free memory is exhausted: "
        << hs3.max_size( ) <<  "." << endl;

   // The following lines create a hash_set hs4
   // with the allocator of hash_set hs1.
   hash_set <int>::allocator_type hs4_Alloc;
   hash_set <int> hs4;
   hs4_Alloc = hs2.get_allocator( );

   // Two allocators are interchangeable if
   // storage allocated from each can be
   // deallocated by the other
   if( hs2_Alloc == hs4_Alloc )
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

## <a name="hash_set"></a>hash_set::hash_set

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_set třída](../standard-library/unordered-set-class.md).

Vytvoří `hash_set`, který je prázdný nebo který je kopií všech nebo částí jiných `hash_set`.

```cpp
hash_set();

explicit hash_set(
    const Traits& Comp);

hash_set(
    const Traits& Comp,
    const Allocator& Al);

hash_set(
    const hash_set<Key, Traits, Allocator>& Right);

hash_set(
    hash_set&& Right);

hash_set(
    initializer_list<Type> IList);

hash_set(
    initializer_list<Type> IList,
    const Compare& Comp);

hash_set(
    initializer_list<value_type> IList,
    const Compare& Comp,
    const Allocator& Al);

template <class InputIterator>
hash_set(
    InputIterator First,
    InputIterator Last);

template <class InputIterator>
hash_set(
    InputIterator First,
    InputIterator Last,
    const Traits& Comp);

template <class InputIterator>
hash_set(
    InputIterator First,
    InputIterator Last,
    const Traits& Comp,
    const Allocator& Al);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|-|-|
|*VŠ*|Třída přidělování úložiště, která se má použít pro tento objekt `hash_set`, který má výchozí hodnotu `Allocator`.|
|*Zajištění*|Funkce porovnání typu `const Traits` slouží k uspořádání prvků v `hash_set`, jejichž výchozí hodnota je `hash_compare`.|
|*Kliknutím*|@No__t_0, ze kterého má být vytvořená `hash_set` kopie.|
|*První*|Pozice prvního prvku v rozsahu prvků, které mají být zkopírovány.|
|*Posledního*|Pozice prvního prvku mimo rozsah prvků, které mají být zkopírovány.|

### <a name="remarks"></a>Poznámky

Všechny konstruktory ukládají typ objektu přidělování, který spravuje úložiště paměti pro `hash_set` a které mohou být později vráceny voláním [hash_set:: get_allocator](#get_allocator). Parametr allocator je často v deklaraci třídy vynechán a makra předběžného zpracování jsou použita k nahrazení alternativních alokátorů.

Všechny konstruktory inicializují své hash_sets.

Všechny konstruktory ukládají objekt funkce typu `Traits`, který se používá k navázání objednávky mezi klíči `hash_set` a které mohou být později vráceny voláním [hash_set:: key_comp](#key_comp). Další informace o `Traits` naleznete v tématu [Třída hash_set](../standard-library/hash-set-class.md) .

První konstruktor vytvoří prázdné počáteční `hash_set` druhá určuje typ funkce porovnání (`Comp`), která se použije při stanovení pořadí prvků, a třetí explicitně určuje typ přidělujícího objektu (`Al`), který se má použít. Klíčové slovo `explicit` potlačí některé druhy automatického převodu typu.

Čtvrtý a pátý konstruktor určuje kopii `hash_set` `Right`.

Poslední šestý, sedmý a osmý konstruktor používají pro elementy initializer_list.

Poslední konstruktory kopírují rozsah [`First`, `Last`) `hash_set` se zvýšením explicitního určení typu funkce porovnání vlastností třídy a přidělování.

Osmý konstruktor přesune `hash_set` `Right`.

Skutečné pořadí prvků v `hash_set` kontejneru závisí na funkci hash, funkci řazení a aktuální velikosti zatřiďovací tabulky a nelze obecně odhadnout, jak by mohla být s kontejnerem množiny, kde byla určena samostatně pro funkci řazení. .

## <a name="insert"></a>hash_set:: INSERT

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_set třída](../standard-library/unordered-set-class.md).

Vloží prvek nebo rozsah prvků do `hash_set`.

```cpp
pair<iterator, bool> insert(
    const value_type& Val);

iterator insert(
    iterator Where,
    const value_type& Val);

void insert(
    initializer_list<value_type> IList)
template <class InputIterator>
void insert(
    InputIterator First,
    InputIterator Last);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|-|-|
|*Počítává*|Hodnota prvku, který má být vložen do `hash_set`, pokud `hash_set` již daný prvek neobsahuje, nebo obecněji, element, jehož klíč je ekvivalentně seřazen.|
|*,*|Místo zahájení vyhledání správného bodu vložení. (Vložení se může vyskytnout v konstantním času v čase, namísto logaritmické doby, pokud se bod vložení hned `_Where`.)|
|*První*|Pozice prvního prvku, který má být zkopírován z `hash_set`.|
|*Posledního*|Pozice bezprostředně za posledním prvkem, který má být zkopírován z `hash_set`.|
|*IList*|Seznam initializer_list, ze kterého chcete kopírovat prvky.|

### <a name="return-value"></a>Návratová hodnota

První `insert` členská funkce vrátí dvojici, jejíž **logická** komponenta vrátí **hodnotu true** , pokud byla vložena a **false** , pokud `hash_set` již obsahovala element, jehož klíč měl ekvivalentní hodnotu v řazení a jehož iterátor součást vrátí adresu, kam byl vložen nový prvek nebo kde byl prvek již umístěn.

Chcete-li získat přístup k součásti iterátoru páru `pr` vráceného touto členskou funkcí, použijte `pr.first` a k jeho zpětnému odkazování použijte `*(pr.first)`. Chcete-li získat přístup ke komponentě **bool** páru `pr` vrácený touto členskou funkcí, použijte `pr.second` a k jejímu odkázání použijte `*(pr.second)`.

Druhá členská funkce `insert` Vrátí iterátor, který odkazuje na pozici, kam byl nový prvek vložen do `hash_set`.

### <a name="remarks"></a>Poznámky

Třetí členská funkce vloží prvky do initializer_list.

Třetí členská funkce vloží sekvenci hodnot prvků do `hash_set` odpovídající každému prvku, který je adresován v rozsahu [`First`, `Last`) zadaného `hash_set`.

## <a name="iterator"></a>hash_set:: iterátor

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_set třída](../standard-library/unordered-set-class.md).

Typ, který poskytuje obousměrný iterátor, který může číst nebo upravovat libovolný prvek v hash_set.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::iterator iterator;
```

### <a name="remarks"></a>Poznámky

Typ `iterator` lze použít pro úpravu hodnoty prvku.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [začátek](#begin) příkladu, jak deklarovat a použít `iterator`.

## <a name="key_comp"></a>hash_set::key_comp

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_set třída](../standard-library/unordered-set-class.md).

Načte kopii objektu zatřiďovacích vlastností, která se používá k hodnotě hash a seřazení hodnot klíčů elementů v hash_set.

```cpp
key_compare key_comp() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí objekt funkce, který hash_set používá k uspořádání prvků, což je *vlastnosti*parametru šablony.

Další informace o *vlastnostích* naleznete v tématu [třídy hash_set](../standard-library/hash-set-class.md) .

### <a name="remarks"></a>Poznámky

Uložený objekt definuje členskou funkci:

`bool operator( const Key& _xVal, const Key& _yVal );`

Vrátí **hodnotu true** , pokud `_xVal` předchází a není rovna `_yVal` v pořadí řazení.

Všimněte si, že obě [key_compare](#key_compare) a [value_compare](#value_compare) jsou synonyma pro *vlastnosti*parametrů šablony. Oba typy jsou k dispozici pro třídy hash_set a hash_multiset, kde jsou identické, pro zajištění kompatibility s třídami hash_map a hash_multimap, kde jsou odlišné.

### <a name="example"></a>Příklad

```cpp
// hash_set_key_comp.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;

   hash_set <int, hash_compare < int, less<int> > >hs1;
   hash_set<int, hash_compare < int, less<int> > >::key_compare kc1
          = hs1.key_comp( ) ;
   bool result1 = kc1( 2, 3 ) ;
   if( result1 == true )
   {
      cout << "kc1( 2,3 ) returns value of true, "
           << "where kc1 is the function object of hs1."
           << endl;
   }
   else
   {
      cout << "kc1( 2,3 ) returns value of false "
           << "where kc1 is the function object of hs1."
        << endl;
   }

   hash_set <int, hash_compare < int, greater<int> > > hs2;
   hash_set<int, hash_compare < int, greater<int> > >::key_compare
         kc2 = hs2.key_comp( ) ;
   bool result2 = kc2( 2, 3 ) ;
   if(result2 == true)
   {
      cout << "kc2( 2,3 ) returns value of true, "
           << "where kc2 is the function object of hs2."
           << endl;
   }
   else
   {
      cout << "kc2( 2,3 ) returns value of false, "
           << "where kc2 is the function object of hs2."
           << endl;
   }
}
```

## <a name="key_compare"></a>hash_set::key_compare

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_set třída](../standard-library/unordered-set-class.md).

Typ, který poskytuje objekt funkce, který může porovnat dva klíče řazení pro určení relativního pořadí dvou prvků v hash_set.

```cpp
typedef Traits key_compare;
```

### <a name="remarks"></a>Poznámky

`key_compare` je synonymum pro *vlastnosti*parametrů šablony.

Další informace o *vlastnostích* naleznete v tématu [třídy hash_set](../standard-library/hash-set-class.md) .

Všimněte si, že `key_compare` i [value_compare](#value_compare) jsou synonyma pro *vlastnosti*parametrů šablony. Oba typy jsou k dispozici pro třídy set a multiset, kde jsou identické, pro kompatibilitu s třídami map a multimap, kde jsou odlišné.

### <a name="example"></a>Příklad

Příklad, jak deklarovat a používat `key_compare`, naleznete v příkladu pro [key_comp](#key_comp) .

## <a name="key_type"></a>hash_set::key_type

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_set třída](../standard-library/unordered-set-class.md).

Typ, který popisuje objekt uložený jako prvek hash_set v jeho kapacitě jako klíč řazení.

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>Poznámky

`key_type` je synonymum pro *klíč*parametru šablony.

Další informace o *klíči*naleznete v části poznámky v tématu [Třída hash_set](../standard-library/hash-set-class.md) .

Všimněte si, že `key_type` i [value_type](#value_type) jsou synonyma pro *klíč*parametru šablony. Oba typy jsou k dispozici pro třídy hash_set a hash_multiset, kde jsou identické, pro zajištění kompatibility s třídami hash_map a hash_multimap, kde jsou odlišné.

### <a name="example"></a>Příklad

Příklad, jak deklarovat a používat `key_type`, naleznete v příkladu pro [value_type](#value_type) .

## <a name="lower_bound"></a>hash_set::lower_bound

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_set třída](../standard-library/unordered-set-class.md).

Vrátí iterátor na první prvek v hash_set s klíčem, který je větší nebo roven zadanému klíči.

```cpp
const_iterator lower_bound(const Key& key) const;

iterator lower_bound(const Key& key);
```

### <a name="parameters"></a>Parametry

\ *klíčů*
Klíč argumentu, který se má porovnat s klíčem řazení prvku z prohledávané hash_sety.

### <a name="return-value"></a>Návratová hodnota

@No__t_0 nebo `const_iterator`, které řeší umístění elementu v hash_set s klíčem, který je roven nebo větší než klíč argumentu nebo který řeší umístění, které následuje po posledním prvku v hash_set, pokud se pro klíč nenajde žádná shoda.

### <a name="remarks"></a>Poznámky

### <a name="example"></a>Příklad

```cpp
// hash_set_lower_bound.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;
   hash_set <int> :: const_iterator hs1_AcIter, hs1_RcIter;

   hs1.insert( 10 );
   hs1.insert( 20 );
   hs1.insert( 30 );

   hs1_RcIter = hs1.lower_bound( 20 );
   cout << "The element of hash_set hs1 with a key of 20 is: "
        << *hs1_RcIter << "." << endl;

   hs1_RcIter = hs1.lower_bound( 40 );

   // If no match is found for the key, end( ) is returned
   if ( hs1_RcIter == hs1.end( ) )
      cout << "The hash_set hs1 doesn't have an element "
           << "with a key of 40." << endl;
   else
      cout << "The element of hash_set hs1 with a key of 40 is: "
           << *hs1_RcIter << "." << endl;

   // An element at a specific location in the hash_set can be found
   // by using a dereferenced iterator that addresses the location
   hs1_AcIter = hs1.end( );
   hs1_AcIter--;
   hs1_RcIter = hs1.lower_bound( *hs1_AcIter );
   cout << "The element of hs1 with a key matching "
        << "that of the last element is: "
        << *hs1_RcIter << "." << endl;
}
```

```Output
The element of hash_set hs1 with a key of 20 is: 20.
The hash_set hs1 doesn't have an element with a key of 40.
The element of hs1 with a key matching that of the last element is: 30.
```

## <a name="max_size"></a>hash_set::max_size

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_set třída](../standard-library/unordered-set-class.md).

Vrátí maximální délku hash_set.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>Návratová hodnota

Maximální možná délka hash_set.

### <a name="remarks"></a>Poznámky

### <a name="example"></a>Příklad

```cpp
// hash_set_max_size.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;
   hash_set <int>::size_type i;

   i = hs1.max_size( );
   cout << "The maximum possible length "
        << "of the hash_set is " << i << "." << endl;
}
```

## <a name="op_eq"></a>hash_set:: operator =

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_set třída](../standard-library/unordered-set-class.md).

Nahradí prvky hash_set kopií jiného hash_set.

```cpp
hash_set& operator=(const hash_set& right);

hash_set& operator=(hash_set&& right);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|-|-|
|*Kliknutím*|[Hash_set](../standard-library/hash-set-class.md) se kopíruje do `hash_set`.|

### <a name="remarks"></a>Poznámky

Po vymazání všech existujících prvků v `hash_set` `operator=` buď zkopírování nebo přesunutí obsahu *přímo* do `hash_set`.

### <a name="example"></a>Příklad

```cpp
// hash_set_operator_as.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set<int> v1, v2, v3;
   hash_set<int>::iterator iter;

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

## <a name="pointer"></a>hash_set::p ointer

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_set třída](../standard-library/unordered-set-class.md).

Typ, který poskytuje ukazatel na prvek v hash_set.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::pointer pointer;
```

### <a name="remarks"></a>Poznámky

Typ `pointer` lze použít pro úpravu hodnoty prvku.

Ve většině případů by měl být použit [iterátor](#iterator) pro přístup k prvkům v objektu hash_set.

## <a name="rbegin"></a>hash_set:: rbegin

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_set třída](../standard-library/unordered-set-class.md).

Vrátí iterátor adresující první prvek v obráceném hash_setě.

```cpp
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```

### <a name="return-value"></a>Návratová hodnota

Reverzní obousměrný iterátor, který adresuje první prvek v obráceném hash_set nebo řeší, co byl posledním prvkem v neobráceném hash_set.

### <a name="remarks"></a>Poznámky

`rbegin` se používá s obráceným hash_set stejně jako [Begin](#begin) se používá s hash_set.

Pokud je vrácená hodnota `rbegin` přiřazena k `const_reverse_iterator`, objekt hash_set nelze změnit. Pokud je vrácená hodnota `rbegin` přiřazena k `reverse_iterator`, lze objekt hash_set upravit.

`rbegin` lze použít k iterování hash_set dozadu.

### <a name="example"></a>Příklad

```cpp
// hash_set_rbegin.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;
   hash_set <int>::iterator hs1_Iter;
   hash_set <int>::reverse_iterator hs1_rIter;

   hs1.insert( 10 );
   hs1.insert( 20 );
   hs1.insert( 30 );

   hs1_rIter = hs1.rbegin( );
   cout << "The first element in the reversed hash_set is "
        << *hs1_rIter << "." << endl;

   // begin can be used to start an iteration
   // through a hash_set in a forward order
   cout << "The hash_set is: ";
   for ( hs1_Iter = hs1.begin( ) ; hs1_Iter != hs1.end( );
         hs1_Iter++ )
      cout << *hs1_Iter << " ";
   cout << endl;

   // rbegin can be used to start an iteration
   // through a hash_set in a reverse order
   cout << "The reversed hash_set is: ";
   for ( hs1_rIter = hs1.rbegin( ) ; hs1_rIter != hs1.rend( );
         hs1_rIter++ )
      cout << *hs1_rIter << " ";
   cout << endl;

   // A hash_set element can be erased by dereferencing to its key
   hs1_rIter = hs1.rbegin( );
   hs1.erase ( *hs1_rIter );

   hs1_rIter = hs1.rbegin( );
   cout << "After the erasure, the first element "
        << "in the reversed hash_set is "<< *hs1_rIter << "."
        << endl;
}
```

```Output
The first element in the reversed hash_set is 30.
The hash_set is: 10 20 30
The reversed hash_set is: 30 20 10
After the erasure, the first element in the reversed hash_set is 20.
```

## <a name="reference"></a>hash_set:: Reference

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_set třída](../standard-library/unordered-set-class.md).

Typ, který poskytuje odkaz na prvek uložený v objektu hash_set.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::reference reference;
```

### <a name="remarks"></a>Poznámky

### <a name="example"></a>Příklad

```cpp
// hash_set_reference.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;

   hs1.insert( 10 );
   hs1.insert( 20 );

   // Declare and initialize a reference &Ref1 to the 1st element
   int &Ref1 = *hs1.begin( );

   cout << "The first element in the hash_set is "
        << Ref1 << "." << endl;

   // The value of the 1st element of the hash_set can be changed
   // by operating on its (non-const) reference
   Ref1 = Ref1 + 5;

   cout << "The first element in the hash_set is now "
        << *hs1.begin() << "." << endl;
}
```

```Output
The first element in the hash_set is 10.
The first element in the hash_set is now 15.
```

## <a name="rend"></a>hash_set:: rend

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_set třída](../standard-library/unordered-set-class.md).

Vrátí iterátor, který adresuje umístění následující po posledním prvku v obráceném hash_setě.

```cpp
const_reverse_iterator rend() const;

reverse_iterator rend();
```

### <a name="return-value"></a>Návratová hodnota

Zpětný obousměrný iterátor, který adresuje umístění následující po posledním prvku v obráceném hash_set (umístění, které předchází prvnímu prvku v neobráceném hash_set).

### <a name="remarks"></a>Poznámky

`rend` se používá s obráceným hash_set stejně jako [End](#end) se používá s hash_set.

Pokud je vrácená hodnota `rend` přiřazena k `const_reverse_iterator`, objekt hash_set nelze změnit. Pokud je vrácená hodnota `rend` přiřazena k `reverse_iterator`, lze objekt hash_set upravit. Hodnota vrácená `rend` by neměla být zpětně odkazovaná.

`rend` lze použít k otestování, zda reverzní iterátor dosáhl konce jeho hash_set.

### <a name="example"></a>Příklad

```cpp
// hash_set_rend.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;
   hash_set <int>::iterator hs1_Iter;
   hash_set <int>::reverse_iterator hs1_rIter;
   hash_set <int>::const_reverse_iterator hs1_crIter;

   hs1.insert( 10 );
   hs1.insert( 20 );
   hs1.insert( 30 );

   hs1_rIter = hs1.rend( );
   hs1_rIter--;
   cout << "The last element in the reversed hash_set is "
        << *hs1_rIter << "." << endl;

   // end can be used to terminate an iteration
   // through a hash_set in a forward order
   cout << "The hash_set is: ";
   for ( hs1_Iter = hs1.begin( ) ; hs1_Iter != hs1.end( );
         hs1_Iter++ )
      cout << *hs1_Iter << " ";
   cout << "." << endl;

   // rend can be used to terminate an iteration
   // through a hash_set in a reverse order
   cout << "The reversed hash_set is: ";
   for ( hs1_rIter = hs1.rbegin( ) ; hs1_rIter != hs1.rend( );
         hs1_rIter++ )
      cout << *hs1_rIter << " ";
   cout << "." << endl;

   hs1_rIter = hs1.rend( );
   hs1_rIter--;
   hs1.erase ( *hs1_rIter );

   hs1_rIter = hs1.rend( );
   hs1_rIter--;
   cout << "After the erasure, the last element in the "
        << "reversed hash_set is " << *hs1_rIter << "."
        << endl;
}
```

```Output
The last element in the reversed hash_set is 10.
The hash_set is: 10 20 30 .
The reversed hash_set is: 30 20 10 .
After the erasure, the last element in the reversed hash_set is 20.
```

## <a name="reverse_iterator"></a>hash_set::reverse_iterator

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_set třída](../standard-library/unordered-set-class.md).

Typ, který poskytuje obousměrný iterátor, který může číst nebo upravovat prvek v obráceném hash_setě.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::reverse_iterator reverse_iterator;
```

### <a name="remarks"></a>Poznámky

Typ `reverse_iterator` slouží k iterování hash_set v obráceném pořadí.

### <a name="example"></a>Příklad

Příklad, jak deklarovat a používat `reverse_iterator`, naleznete v příkladu pro [rbegin](#rbegin) .

## <a name="size"></a>hash_set:: size

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_set třída](../standard-library/unordered-set-class.md).

Vrátí počet prvků v hash_set.

```cpp
size_type size() const;
```

### <a name="return-value"></a>Návratová hodnota

Aktuální délka hash_set.

### <a name="remarks"></a>Poznámky

### <a name="example"></a>Příklad

```cpp
// hash_set_size.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;
   hash_set <int> :: size_type i;

   hs1.insert( 1 );
   i = hs1.size( );
   cout << "The hash_set length is " << i << "." << endl;

   hs1.insert( 2 );
   i = hs1.size( );
   cout << "The hash_set length is now " << i << "." << endl;
}
```

```Output
The hash_set length is 1.
The hash_set length is now 2.
```

## <a name="size_type"></a>hash_set::size_type

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_set třída](../standard-library/unordered-set-class.md).

Typ unsigned integer, který může představovat počet prvků v objektu hash_set.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::size_type size_type;
```

### <a name="remarks"></a>Poznámky

### <a name="example"></a>Příklad

Podívejte se na příklad pro [Velikost](#size) pro příklad, jak deklarovat a použít `size_type`

## <a name="swap"></a>hash_set:: swap

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_set třída](../standard-library/unordered-set-class.md).

Vyměňuje prvky dvou hash_sets.

```cpp
void swap(hash_set& right);
```

### <a name="parameters"></a>Parametry

*pravé* \
Argument hash_set, který poskytuje prvky, které mají být nahrazeny cílovým hash_set.

### <a name="remarks"></a>Poznámky

Členská funkce neověřuje žádné odkazy, ukazatele nebo iterátory, které určují elementy ve dvou hash_sets, jejichž prvky se vyměňují.

### <a name="example"></a>Příklad

```cpp
// hash_set_swap.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1, hs2, hs3;
   hash_set <int>::iterator hs1_Iter;

   hs1.insert( 10 );
   hs1.insert( 20 );
   hs1.insert( 30 );
   hs2.insert( 100 );
   hs2.insert( 200 );
   hs3.insert( 300 );

   cout << "The original hash_set hs1 is:";
   for ( hs1_Iter = hs1.begin( ); hs1_Iter != hs1.end( );
         hs1_Iter++ )
         cout << " " << *hs1_Iter;
   cout   << "." << endl;

   // This is the member function version of swap
   hs1.swap( hs2 );

   cout << "After swapping with hs2, list hs1 is:";
   for ( hs1_Iter = hs1.begin( ); hs1_Iter != hs1.end( );
         hs1_Iter++ )
         cout << " " << *hs1_Iter;
   cout  << "." << endl;

   // This is the specialized template version of swap
   swap( hs1, hs3 );

   cout << "After swapping with hs3, list hs1 is:";
   for ( hs1_Iter = hs1.begin( ); hs1_Iter != hs1.end( );
         hs1_Iter++ )
         cout << " " << *hs1_Iter;
   cout   << "." << endl;
}
```

```Output
The original hash_set hs1 is: 10 20 30.
After swapping with hs2, list hs1 is: 200 100.
After swapping with hs3, list hs1 is: 300.
```

## <a name="upper_bound"></a>hash_set::upper_bound

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_set třída](../standard-library/unordered-set-class.md).

Vrátí iterátor na první prvek v hash_set, který má klíč, který je větší než zadaný klíč.

```cpp
const_iterator upper_bound(const Key& key) const;

iterator upper_bound(const Key& key);
```

### <a name="parameters"></a>Parametry

\ *klíčů*
Klíč argumentu, který se má porovnat s klíčem řazení prvku z prohledávané hash_sety.

### <a name="return-value"></a>Návratová hodnota

@No__t_0 nebo `const_iterator`, které řeší umístění elementu v hash_set s klíčem, který je roven nebo větší než klíč argumentu, nebo který řeší umístění, které následuje po posledním prvku v hash_set, pokud se pro klíč nenajde žádná shoda.

### <a name="remarks"></a>Poznámky

### <a name="example"></a>Příklad

```cpp
// hash_set_upper_bound.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;
   hash_set <int> :: const_iterator hs1_AcIter, hs1_RcIter;

   hs1.insert( 10 );
   hs1.insert( 20 );
   hs1.insert( 30 );

   hs1_RcIter = hs1.upper_bound( 20 );
   cout << "The first element of hash_set hs1 with a key greater "
        << "than 20 is: " << *hs1_RcIter << "." << endl;

   hs1_RcIter = hs1.upper_bound( 30 );

   // If no match is found for the key, end( ) is returned
   if ( hs1_RcIter == hs1.end( ) )
      cout << "The hash_set hs1 doesn't have an element "
           << "with a key greater than 30." << endl;
   else
      cout << "The element of hash_set hs1 with a key > 40 is: "
           << *hs1_RcIter << "." << endl;

   // An element at a specific location in the hash_set can be found
   // by using a dereferenced iterator addressing the location
   hs1_AcIter = hs1.begin( );
   hs1_RcIter = hs1.upper_bound( *hs1_AcIter );
   cout << "The first element of hs1 with a key greater than "
        << endl << "that of the initial element of hs1 is: "
        << *hs1_RcIter << "." << endl;
}
```

```Output
The first element of hash_set hs1 with a key greater than 20 is: 30.
The hash_set hs1 doesn't have an element with a key greater than 30.
The first element of hs1 with a key greater than
that of the initial element of hs1 is: 20.
```

## <a name="value_comp"></a>hash_set::value_comp

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_set třída](../standard-library/unordered-set-class.md).

Načte kopii objektu porovnání, která se používá k seřazení hodnot prvků v hash_set.

```cpp
value_compare value_comp() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí objekt funkce, který hash_set používá k uspořádání prvků, což je *porovnání*parametru šablony.

Další informace o *porovnání*naleznete v části poznámky v tématu [Třída hash_set](../standard-library/hash-set-class.md) .

### <a name="remarks"></a>Poznámky

Uložený objekt definuje členskou funkci:

`bool operator( const Key& _xVal, const Key& _yVal );`

Vrátí **hodnotu true** , pokud `_xVal` předchází a není rovna `_yVal` v pořadí řazení.

Všimněte si, že obě [value_compare](../standard-library/set-class.md#value_compare) a [key_compare](../standard-library/set-class.md#key_compare) jsou synonyma pro parametr šablony *Compare*. Oba typy jsou k dispozici pro třídy hash_set a hash_multiset, kde jsou identické, pro zajištění kompatibility s třídami hash_map a hash_multimap, kde jsou odlišné.

### <a name="example"></a>Příklad

```cpp
// hash_set_value_comp.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;

   hash_set <int, hash_compare < int, less<int> > > hs1;
   hash_set <int, hash_compare < int, less<int> >  >::value_compare
      vc1 = hs1.value_comp( );
   bool result1 = vc1( 2, 3 );
   if( result1 == true )
   {
      cout << "vc1( 2,3 ) returns value of true, "
           << "where vc1 is the function object of hs1."
           << endl;
   }
   else
   {
      cout << "vc1( 2,3 ) returns value of false, "
           << "where vc1 is the function object of hs1."
           << endl;
   }

   hash_set <int, hash_compare < int, greater<int> > > hs2;
   hash_set<int, hash_compare < int, greater<int> > >::value_compare
      vc2 = hs2.value_comp( );
   bool result2 = vc2( 2, 3 );
   if( result2 == true )
   {
      cout << "vc2( 2,3 ) returns value of true, "
           << "where vc2 is the function object of hs2."
           << endl;
   }
   else
   {
      cout << "vc2( 2,3 ) returns value of false, "
           << "where vc2 is the function object of hs2."
           << endl;
   }
}
```

## <a name="value_compare"></a>hash_set::value_compare

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_set třída](../standard-library/unordered-set-class.md).

Typ, který poskytuje dva objekty Functions, binární predikát porovnání třídy, který může porovnat dvě hodnoty prvku hash_set a určit jejich relativní pořadí a unární predikát, který prvky vyhodnotí.

```cpp
typedef key_compare value_compare;
```

### <a name="remarks"></a>Poznámky

`value_compare` je synonymum pro *vlastnosti*parametrů šablony.

Další informace o *vlastnostích* naleznete v tématu [třídy hash_set](../standard-library/hash-set-class.md) .

Všimněte si, že [key_compare](#key_compare) i `value_compare` jsou synonyma pro *vlastnosti*parametrů šablony. Oba typy jsou k dispozici pro třídy hash_set a hash_multiset, kde jsou identické, pro zajištění kompatibility s třídami hash_map a hash_multimap, kde jsou odlišné.

### <a name="example"></a>Příklad

Příklad, jak deklarovat a používat `value_compare`, naleznete v příkladu pro [value_comp](#value_comp) .

## <a name="value_type"></a>hash_set::value_type

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [Unordered_set třída](../standard-library/unordered-set-class.md).

Typ, který popisuje objekt uložený jako prvek hash_set v jeho kapacitě jako hodnota.

```cpp
typedef Key value_type;
```

### <a name="example"></a>Příklad

```cpp
// hash_set_value_type.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;
   hash_set <int>::iterator hs1_Iter;

   hash_set <int> :: value_type hsvt_Int;   // Declare value_type
   hsvt_Int = 10;             // Initialize value_type

   hash_set <int> :: key_type hskt_Int;   // Declare key_type
   hskt_Int = 20;             // Initialize key_type

   hs1.insert( hsvt_Int );         // Insert value into hs1
   hs1.insert( hskt_Int );         // Insert key into hs1

   // A hash_set accepts key_types or value_types as elements
   cout << "The hash_set has elements:";
   for ( hs1_Iter = hs1.begin( ) ; hs1_Iter != hs1.end( ); hs1_Iter++)
      cout << " " << *hs1_Iter;
   cout << "." << endl;
}
```

```Output
The hash_set has elements: 10 20.
```

## <a name="see-also"></a>Viz také:

[Bezpečnost vlákna ve C++ standardní knihovně](../standard-library/thread-safety-in-the-cpp-standard-library.md) \
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)
