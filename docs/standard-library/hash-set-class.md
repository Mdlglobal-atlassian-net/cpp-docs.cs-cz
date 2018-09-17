---
title: hash_set – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 142b88cf58369f09be4e06ed47fef94b845dfe71
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45726021"
---
# <a name="hashset-class"></a>hash_set – třída

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set – třída](../standard-library/unordered-set-class.md).

Hash_set – třídy kontejnerů je rozšířením standardní knihovny C++ a slouží k ukládání a rychlé načítání dat z kolekce, ve kterém hodnoty elementů obsažených jsou jedinečné a slouží jako klíčové hodnoty.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Key,
    class Traits=hash_compare<Key, less<Key>>,
    class Allocator=allocator<Key>>
class hash_set
```

### <a name="parameters"></a>Parametry

*Key*<br/>
Typ dat prvku, který bude uložen do hash_set.

*Osobnostní rysy*<br/>
Typ, který obsahuje dva objekty funkce, jeden z třídy porovnání, který je binární predikát moci porovnat dvě hodnoty prvků jako klíče řazení pro určení jejich relativního pořadí a hashovací funkci, která je klíčové hodnoty unární predikát mapování elementů na nepodepsané celá čísla typu `size_t`. Tento argument je nepovinný a `hash_compare<Key, less<Key> >` je výchozí hodnota.

*Allocator –*<br/>
Typ představující uložený objekt alokátoru, který zapouzdřuje informace o přidělování a navracení zpět paměti hash_set –. Tento argument je nepovinný a výchozí hodnota je `allocator<Key>`.

## <a name="remarks"></a>Poznámky

Hash_set je:

- Asociativní kontejner, což je kontejner proměnné velikosti, který podporuje efektivní načtení hodnoty prvku založené na přiřazené hodnotě klíče. Dále je to jednoduchý asociativní kontejner, protože jeho hodnoty prvku jsou jeho hodnoty klíče.

- Oboustranný, protože poskytuje obousměrný iterátor pro přístup k jeho prvkům.

- Hodnoty hash, protože jeho prvky jsou seskupeny do intervalů podle hodnoty funkce hash u hodnoty klíče prvků.

- Jedinečný v tom smyslu, že každý z jeho prvků musí mít jedinečný klíč. Hash_set – je také jednoduchý asociativní kontejner, jeho prvky jsou také jedinečné.

- Třída šablony vzhledem k tomu, že funkce, které poskytuje je obecný a to nezávisle určitém typu dat obsažených jako prvky nebo klíče. Datové typy použité pro prvky a klíče jsou místo toho zadány jako parametry v šabloně třídy společně s funkcí porovnání a alokátorem.

Hlavní výhodou hashování přes řazení je vyšší efektivity; úspěšné algoritmu hash provádí vkládání, odstraňování a vyhledá v konstantní průměrnou dobu mezi dobou úměrný logaritmu počtu prvků v kontejneru pro řazení techniky. Hodnotu prvku v sadě nelze změnit přímo. Místo toho musíte odstranit staré hodnoty a vložit prvky s novými hodnotami.

Volba typu kontejneru by měla obecně vycházet z typu vyhledávání a vkládání vyžadovaného aplikací. Hodnoty hash asociativní kontejnery jsou optimalizovány pro operace vyhledávání, vkládání a odstranění. Členské funkce, které explicitně podporují tyto operace jsou efektivní, při použití s dobře navržené hashovací funkce, prováděny v čase, který je v průměru konstantní a není závislá na počtu prvků v kontejneru. Dobře navržené hashovací funkce generuje jednotné distribuce hodnot hash a minimalizuje počet kolizí, kde ke kolizi říká, že je dojít, když odlišné hodnoty klíče jsou mapovány na stejnou hodnotu hash. V nejhorším případě s nejhorší funkce hash je to možné je počet operací úměrný počtu prvků v sekvenci (lineární čas).

Hash_set by měl být asociativní kontejner dle výběru, když jsou podmínky přiřazení hodnot k jejich klíčům splněny aplikací. Elementy hash_set – musí být jedinečné a slouží jako vlastní klíče řazení. Model pro tento typ struktury je uspořádaný seznam slov, v němž se slova mohou vyskytovat pouze jednou. Pokud bylo povoleno více výskytů jednoho slova, hash_multiset by odpovídající strukturou kontejneru. Pokud hodnoty musí být připojeny k seznamu jedinečných klíčových slov, hash_map by vhodnou strukturou tato data obsahovat. Pokud místo toho klíče nejsou jedinečné, hash_multimap – by zvoleným kontejnerem.

Hash_set seřadí sekvence pomocí volání uloženého hash `Traits` objekt typu [value_compare –](#value_compare). Tento uložený objekt může získat přístup k voláním členské funkce [key_comp](#key_comp). Objekt funkce se musí chovat stejně jako objekt třídy *hash_compare – < klíč, méně\<klíč >>.* Konkrétně pro všechny hodnoty `key` typu klíče, volání vlastností (`key`) získá distribuci hodnot typu size_t.

Obecně, tyto prvky musí být menší než srovnatelné pro toto pořadí, což znamená, že když jsou uvedeny dva prvky, může být stanoveno, zda jsou ekvivalentní (v tom smyslu, že ani jeden není menší než ten druhý), nebo že jeden je menší než druhý. Výsledkem je řazení mezi neekvivalentních prvků. Technicky je funkce porovnání binárním predikátem, který indukuje přísné slabé řazení, standardním matematickým způsobem. Binární predikát *f*( *x*, *y*) je objekt funkce, který má dva objekty argumentu x a y a návratovou hodnotu true nebo false. Na hash_set je přísné slabé seřazení, pokud je binární predikát Nereflexivní, antisymetrický a tranzitivní a je-li ekvivalence tranzitivní, kde dva objekty *x* a *y* jsou definovány Chcete-li jako ekvivalentní, když oba *f*( *x*, *y*) a *f*( *y*, *x*) jsou false. Pokud silnější podmínka rovnosti mezi klíči nahradí ekvivalenci, stane se pořadí celkovým (v tom smyslu, že všechny prvky jsou uspořádány ve vztahu k sobě navzájem) a odpovídající klíče budou od sebe nerozeznatelné.

Skutečné pořadí prvků v řízené sekvenci závisí na hashovací funkci, funkci pořadí a aktuální velikost tabulky hash uloženou v objektu kontejneru. Nelze zjistit aktuální velikost tabulky hash, takže pořadí prvků v řízené sekvenci obecně nelze předvídat. Vkládání prvků nezruší platnost žádných iterátorů a odstranění prvků zruší platnost pouze těch iterátorů, které výslovně odkazovaly na odstraněné prvky.

Iterátor poskytovaný třídou hash_set je obousměrný iterátor, ale členské funkce třídy [vložit](#insert) a [hash_set](#hash_set) mají verze, které jako parametry šablony berou slabší vstupní iterátor, jehož požadavky na funkce jsou minimálnější než ty zaručeny třídou obousměrných iterátorů. Různé koncepty iterátorů tvoří rodinu týkající se upřesnění jejich funkčnosti. Každý koncept iterátoru má vlastní sadu požadavků a algoritmy, které s nimi pracují, musí omezit jejich předpoklady na požadavky podle typu iterátoru. Lze předpokládat, že ke vstupnímu iterátoru lze přistoupit přes ukazatel pro odkazování na některý objekt a že může být zvýšen na další iterátor v pořadí. Toto je minimální sada funkcí, ale je dostatečná pro srozumitelnou komunikaci o rozsahu u iterátorů [ `first`, `last`) v kontextu členské funkce třídy.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[hash_set](#hash_set)|Vytvoří `hash_set` , který je prázdný nebo, který je kopií celého nebo části některého jiného `hash_set`.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[allocator_type](#allocator_type)|Typ, který představuje `allocator` třídy pro `hash_set` objektu.|
|[const_iterator](#const_iterator)|Typ, který poskytuje obousměrný iterátor, který může číst `const` prvek `hash_set`.|
|[const_pointer](#const_pointer)|Typ, který poskytuje ukazatel na **const** prvek `hash_set`.|
|[const_reference](#const_reference)|Typ, který poskytuje odkaz na **const** element uložené v `hash_set` pro čtení a provádění **const** operace.|
|[const_reverse_iterator](#const_reverse_iterator)|Typ, který poskytuje obousměrný iterátor, který může přečíst jakýkoli **const** prvek `hash_set`.|
|[difference_type](#difference_type)|Celočíselný typ se znaménkem, který slouží k vyjádření počtu prvků `hash_set` v rozsahu mezi prvky, na které odkazují iterátory.|
|[iterátor](#iterator)|Typ, který poskytuje obousměrný iterátor, který může číst nebo upravovat libovolný prvek v `hash_set`.|
|[key_compare](#key_compare)|Typ poskytující objekt funkce, který může porovnat dva klíče řazení pro určení relativního pořadí dvou prvků v `hash_set`.|
|[key_type](#key_type)|Typ, který popisuje objekt uložený jako prvek sady `hash_set` v jeho kapacitě jako klíč řazení.|
|[Ukazatel](#pointer)|Typ, který poskytuje ukazatel na prvek v `hash_set`.|
|[Referenční dokumentace](#reference)|Typ, který poskytuje odkaz na prvek uložený v `hash_set`.|
|[reverse_iterator](#reverse_iterator)|Typ, který poskytuje obousměrný iterátor, který může číst nebo upravovat prvek v obráceném objektu `hash_set`.|
|[size_type](#size_type)|Typ celé číslo bez znaménka představující počet prvků v `hash_set`.|
|[value_compare](#value_compare)|Typ, který poskytuje dva objekty funkce, třídy porovnání, který může porovnat dvě hodnoty prvků ze binárním predikátem `hash_set` pro určení jejich relativního pořadí a unární predikát, který vytvoří hodnotu hash prvky.|
|[value_type](#value_type)|Typ, který popisuje objekt uložený jako prvek sady `hash_set` v jeho kapacitě jako hodnotu.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[začít](#begin)|Vrátí iterátor adresující první prvek `hash_set`.|
|[cbegin](#cbegin)|Vrátí konstantní iterátor adresující první prvek `hash_set`.|
|[cend](#cend)|Vrátí konstantní iterátor adresující umístění následující po posledním prvku v `hash_set`.|
|[Vymazat](#clear)|Vymaže všechny prvky `hash_set`.|
|[Počet](#count)|Vrátí počet prvků v `hash_set` jejichž klíč odpovídá klíči se zadaným parametrem.|
|[crbegin](#crbegin)|Vrátí konstantní iterátor adresující první prvek v obráceném objektu `hash_set`.|
|[crend –](#crend)|Vrátí konstantní iterátor adresující umístění následující po posledním prvku v obráceném objektu `hash_set`.|
|[emplace –](#emplace)|Vloží vytvořený prvek na místo do `hash_set`.|
|[emplace_hint –](#emplace_hint)|Vloží vytvořený prvek na místo do `hash_set`, s náznakem umístění.|
|[prázdný](#empty)|Testuje, zda `hash_set` je prázdný.|
|[ukončení](#end)|Vrátí iterátor adresující umístění následující po posledním prvku v `hash_set`.|
|[equal_range](#equal_range)|Vrátí pár iterátorů v uvedeném pořadí na první prvek v `hash_set` s klíčem, který je větší než zadaný klíč a na první prvek `hash_set` s klíčem, který je roven nebo větší než tento klíč.|
|[vymazání](#erase)|Odebere prvek nebo rozsah prvků `hash_set` od zadané pozice nebo odebere prvky, které odpovídají zadanému klíči.|
|[Najít](#find)|Vrátí iterátor adresující umístění prvku v `hash_set` , který má klíč odpovídající zadanému klíči.|
|[get_allocator](#get_allocator)|Vrátí kopii objektu `allocator` objekt použitý k vytvoření `hash_set`.|
|[Vložit](#insert)|Vloží prvek nebo rozsah prvků do `hash_set`.|
|[key_comp](#key_comp)|Získá kopii objektu porovnání použitého pro seřazení klíčů v `hash_set`.|
|[lower_bound –](#lower_bound)|Vrátí iterátor na první prvek v `hash_set` s klíčem, který je roven nebo větší než zadaný klíč.|
|[max_size](#max_size)|Vrátí maximální délku objektu `hash_set`.|
|[rbegin –](#rbegin)|Vrátí iterátor adresující první prvek v obráceném objektu `hash_set`.|
|[rend –](#rend)|Vrátí iterátor adresující umístění následující po posledním prvku v obráceném objektu `hash_set`.|
|[Velikost](#size)|Vrátí počet prvků v `hash_set`.|
|[Prohození](#swap)|Vymění prvky dvou `hash_set`s.|
|[upper_bound –](#upper_bound)|Vrátí iterátor na první prvek v `hash_set` s klíčem, který je roven nebo větší než zadaný klíč.|
|[value_comp](#value_comp)|Získá kopii objektu hash vlastností použita pro hodnoty hash a pořadí hodnot klíče v elementu `hash_set`.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[hash_set::Operator =](#op_eq)|Nahradí prvky objektu `hash_set` s kopií jiného `hash_set`.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<hash_set >

**Namespace:** stdext

## <a name="allocator_type"></a>  hash_set::allocator_type

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set – třída](../standard-library/unordered-set-class.md).

Typ, který představuje třídu alokátoru pro objekt hash_set.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::allocator_type allocator_type;
```

### <a name="remarks"></a>Poznámky

`allocator_type` je synonymum pro parametr šablony *alokátoru*.

Další informace o *alokátoru*, najdete v části poznámky [hash_set – třída](../standard-library/hash-set-class.md) tématu.

### <a name="example"></a>Příklad

Viz příklad pro [get_allocator](#get_allocator) příklad, který používá `allocator_type`.

## <a name="begin"></a>  hash_set::begin

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set – třída](../standard-library/unordered-set-class.md).

Vrátí iterátor adresující první prvek hash_set.

```cpp
const_iterator begin() const;

iterator begin();
```

### <a name="return-value"></a>Návratová hodnota

Obousměrný iterátor adresující první prvek v hash_set nebo adresující prázdný hash_set – umístění.

### <a name="remarks"></a>Poznámky

Pokud návratová hodnota `begin` je přiřazena `const_iterator`, prvků v objektu hash_set nelze upravit. Pokud návratová hodnota `begin` je přiřazena `iterator`, prvků v objektu hash_set – je možné upravit.

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

## <a name="cbegin"></a>  hash_set::cbegin

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set – třída](../standard-library/unordered-set-class.md).

Vrátí konstantní iterátor adresující první prvek hash_set.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>Návratová hodnota

Obousměrný iterátor const adresující první prvek v [hash_set](../standard-library/hash-set-class.md) nebo umístění následující po prázdná `hash_set`.

### <a name="remarks"></a>Poznámky

S návratovou hodnotou `cbegin`, prvky v `hash_set` objekt nelze změnit.

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

## <a name="cend"></a>  hash_set::cend

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set – třída](../standard-library/unordered-set-class.md).

Vrátí konstantní iterátor adresující umístění následující po posledním prvku v hash_set.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>Návratová hodnota

Obousměrný iterátor const adresující umístění následující po posledním prvku v [hash_set](../standard-library/hash-set-class.md). Pokud `hash_set` je prázdný, pak `hash_set::cend == hash_set::begin`.

### <a name="remarks"></a>Poznámky

`cend` slouží k otestování, zda iterátor dosáhl konce jeho `hash_set`. Hodnota vrácená `cend` by neměla být dereferencována.

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

## <a name="clear"></a>  hash_set::clear

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set – třída](../standard-library/unordered-set-class.md).

Vymaže všechny prvky hash_set.

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

## <a name="const_iterator"></a>  hash_set::const_iterator

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set – třída](../standard-library/unordered-set-class.md).

Typ, který poskytuje obousměrný iterátor, který může číst **const** prvek hash_set.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_iterator const_iterator;
```

### <a name="remarks"></a>Poznámky

Typ `const_iterator` nelze použít ke změně hodnoty prvku.

### <a name="example"></a>Příklad

Viz příklad pro [začít](#begin) příklad, který používá `const_iterator`.

## <a name="const_pointer"></a>  hash_set::const_pointer

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set – třída](../standard-library/unordered-set-class.md).

Typ, který poskytuje ukazatel **const** prvek hash_set –.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_pointer const_pointer;
```

### <a name="remarks"></a>Poznámky

Typ `const_pointer` nelze použít ke změně hodnoty prvku.

Ve většině případů [const_iterator](#const_iterator) by měla sloužit pro přístup k prvkům v **const** hash_set objektu.

## <a name="const_reference"></a>  hash_set::const_reference

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set – třída](../standard-library/unordered-set-class.md).

Typ, který poskytuje odkaz na **const** prvek uložený v hash_set – pro čtení a provádění **const** operace.

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

## <a name="const_reverse_iterator"></a>  hash_set::const_reverse_iterator

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set – třída](../standard-library/unordered-set-class.md).

Typ, který poskytuje obousměrný iterátor, který může přečíst jakýkoli **const** prvek hash_set.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_reverse_iterator const_reverse_iterator;
```

### <a name="remarks"></a>Poznámky

Typ `const_reverse_iterator` hodnotu prvku nelze změnit a použít k iteraci v rámci hash_set – v opačném pořadí.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [rend](#rend) příklad toho, jak deklarovat a použít `const_reverse_iterator`

## <a name="count"></a>  hash_set::Count

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set – třída](../standard-library/unordered-set-class.md).

Vrátí počet prvků v hash_set, jejichž klíč odpovídá klíči se zadaným parametrem.

```cpp
size_type count(const Key& key) const;
```

### <a name="parameters"></a>Parametry

*Klíč*<br/>
Klíč prvky lze porovnat z hash_set.

### <a name="return-value"></a>Návratová hodnota

1, pokud hash_set – obsahuje element, jehož klíč řazení odpovídá klíč parametru.

0, pokud hash_set neobsahuje prvek s odpovídajícím klíčem.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí počet prvků v následujícím rozsahu:

[ **lower_bound** (_ *klíč* ), **upper_bound** (\_ *klíč* )).

### <a name="example"></a>Příklad

Následující příklad ukazuje použití hash_set::count členskou funkci.

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

## <a name="crbegin"></a>  hash_set::crbegin

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set – třída](../standard-library/unordered-set-class.md).

Vrátí konstantní iterátor adresující první prvek v obráceném objektu hash_set.

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>Návratová hodnota

Konstantní reverzní obousměrný iterátor adresující první prvek v obráceném objektu [hash_set](../standard-library/hash-set-class.md) nebo co bylo posledním prvkem v neobráceném adresování `hash_set`.

### <a name="remarks"></a>Poznámky

`crbegin` se používá s obrácený hash_set – stejně jako [hash_set::begin](#begin) se používá s hash_set.

S návratovou hodnotou `crbegin`, `hash_set` objekt nelze změnit.

`crbegin` můžete použít k iteraci v rámci `hash_set` zpětně.

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

## <a name="crend"></a>  hash_set::crend

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set – třída](../standard-library/unordered-set-class.md).

Vrátí konstantní iterátor adresující umístění následující po posledním prvku v obráceném objektu hash_set.

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>Návratová hodnota

Konstantní reverzní obousměrný iterátor adresující umístění následující po posledním prvku v obráceném objektu [hash_set](../standard-library/hash-set-class.md) (umístění, ke které došlo před první prvek v neobráceném `hash_set`).

### <a name="remarks"></a>Poznámky

`crend` se používá s obráceném objektu `hash_set` stejně jako [hash_set::end](#end) se používá s `hash_set`.

S návratovou hodnotou `crend`, `hash_set` objekt nelze změnit.

`crend` můžete použít k testování na tom, zda zpětný iterátor dosáhl konce jeho `hash_set`.

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

## <a name="difference_type"></a>  hash_set::difference_type

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set – třída](../standard-library/unordered-set-class.md).

Celočíselný typ se znaménkem, který slouží k vyjádření počtu prvků hash_set – v rozsahu mezi prvky, na které odkazují iterátory.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::difference_type difference_type;
```

### <a name="remarks"></a>Poznámky

`difference_type` Typ dochází při přičítání nebo zvýšení prostřednictvím iterátorů kontejneru. `difference_type` Se obvykle používá k vyjádření počtu prvků v rozsahu [ `first`, `last`) mezi iterátory `first` a `last`, obsahuje element, na které odkazuje `first` a rozsah prvků do , ale bez zahrnutí elementu, na které odkazuje `last`.

Všimněte si, že i když `difference_type` je k dispozici pro všechny iterátory, které splňují požadavky na vstupní iterátor, který obsahuje třídou obousměrných iterátorů, které jsou podporovány reverzibilního kontejnery, jako je sada odčítání mezi iterátory pouze podporuje poskytuje náhodný přístup kontejneru, jako jsou vektorové nebo deque iterátory s náhodným přístupem.

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

## <a name="emplace"></a>  hash_set::emplace

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set – třída](../standard-library/unordered-set-class.md).

Vloží vytvořený prvek na místo do hash_set.

```cpp
template <class ValTy>
pair <iterator, bool>
emplace(
    ValTy&& val);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|-|-|
|*Val*|Hodnota element, který má být vložen do [hash_set](../standard-library/hash-set-class.md) není-li `hash_set` již obsahuje tento prvek nebo obecně platí, element, jehož klíč je ekvivalentně seřazen.|

### <a name="return-value"></a>Návratová hodnota

`emplace` Členská funkce vrátí pár jehož **bool** vrátí komponenty **true** Pokud vložení bylo zkontrolujte a **false** Pokud `hash_set` již obsahuje prvek, jehož klíč má ekvivalentní hodnotu v pořadí, a jehož komponenta iterátoru vrátí adresu, kde byl vložen nový element nebo element se kdy již nachází.

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

## <a name="emplace_hint"></a>  hash_set::emplace_hint

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set – třída](../standard-library/unordered-set-class.md).

Vloží vytvořený prvek na místo do hash_set.

```cpp
template <class ValTy>
iterator emplace(
    const_iterator _Where,
    ValTy&& val);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|-|-|
|*Val*|Hodnota element, který má být vložen do [hash_set](../standard-library/hash-set-class.md) není-li `hash_set` již obsahuje tento prvek nebo obecně platí, element, jehož klíč je ekvivalentně seřazen.|
|*_Where*|Místo zahájení vyhledání správného bodu vložení. (Vložení může dojít v amortizovaném konstantním času, namísto logaritmické času, pokud kurzor bezprostředně následuje po *_Where*.)|

### <a name="return-value"></a>Návratová hodnota

[Hash_set::emplace](#emplace) členská funkce vrátí iterátor, který odkazuje na místo, kde byl vložen nový prvek do `hash_set`, nebo kde se nachází existující prvek s odpovídající řazení.

### <a name="remarks"></a>Poznámky

Vložení může dojít v amortizovaném konstantním času, namísto logaritmické času, pokud kurzor bezprostředně následuje po *_Where*.

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

## <a name="empty"></a>  hash_set::Empty

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set – třída](../standard-library/unordered-set-class.md).

Testuje, zda je hash_set je prázdný.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud hash_set je prázdná. **false** Pokud hash_set je prázdný.

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

## <a name="end"></a>  hash_set::end

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set – třída](../standard-library/unordered-set-class.md).

Vrátí iterátor adresující umístění následující po posledním prvku v hash_set.

```cpp
const_iterator end() const;

iterator end();
```

### <a name="return-value"></a>Návratová hodnota

Obousměrný iterátor adresující umístění následující po posledním prvku v hash_set. Pokud hash_set – je prázdný, pak hash_set::end == hash_set::begin.

### <a name="remarks"></a>Poznámky

`end` slouží k otestování, zda iterátor dosáhl konce jeho hash_set. Hodnota vrácená `end` by neměla být dereferencována.

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

## <a name="equal_range"></a>  hash_set::equal_range

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set – třída](../standard-library/unordered-set-class.md).

Vrátí pár iterátorů v uvedeném pořadí na první prvek v hash set s klíčem, který odpovídá zadanému klíči a na první prvek v algoritmu hodnoty hash set s klíčem, který je větší než tento klíč.

```cpp
pair <const_iterator, const_iterator> equal_range (const Key& key) const;

pair <iterator, iterator> equal_range (const Key& key);
```

### <a name="parameters"></a>Parametry

*Klíč*<br/>
Klíč argumentu k porovnání s klíči řazení prvek z hash_set vyhledávaná.

### <a name="return-value"></a>Návratová hodnota

Pár iterátorů, kde je první [lower_bound](../standard-library/set-class.md#lower_bound) klíče a druhá je [upper_bound](../standard-library/set-class.md#upper_bound) klíče.

Pro přístup k první iterace žádost o přijetí změn dvojice vrácené členskou funkci, použijte `pr`. **první**a ke zrušení iterátoru dolní mez, použijte \*( `pr`. **nejprve**). Pro přístup k druhé iterátoru dvojice `pr` vrácený členskou funkci, použijte `pr`. **druhý**a ke zrušení iterátoru horní mez, použijte \*( `pr`. **za druhé**).

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

## <a name="erase"></a>  hash_set::Erase

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set – třída](../standard-library/unordered-set-class.md).

Odebere prvek nebo rozsah prvků v hash_set – od zadané pozice nebo odebere prvky, které odpovídají zadanému klíči.

```cpp
iterator erase(iterator _Where);

iterator erase(iterator first, iterator last);

size_type erase(const key_type& key);
```

### <a name="parameters"></a>Parametry

*_Where*<br/>
Pozice prvku, který chcete odebrat z hash_set.

*první*<br/>
Pozice prvního prvku odebrán hash_set.

*poslední*<br/>
Pozice bezprostředně za posledním prvkem odebrán hash_set.

*Klíč*<br/>
Klíč prvky, které mají být odebrány hash_set –.

### <a name="return-value"></a>Návratová hodnota

Pro první dvě členské funkce obousměrný iterátor, který označí první prvek zbývající za jakýmikoli odstraněnými prvky nebo ukazatel na konci hash_set – Pokud žádný takový prvek neexistuje. Pro třetí členská funkce, počet prvků, které byly odebrány z hash_set.

### <a name="remarks"></a>Poznámky

Členské funkce nikdy nevyvolají výjimku.

### <a name="example"></a>Příklad

Následující příklad ukazuje použití hash_set::erase členskou funkci.

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

## <a name="find"></a>  hash_set::Find

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set – třída](../standard-library/unordered-set-class.md).

Vrátí iterátor adresující umístění prvku v hash_set –, který má klíč odpovídající zadanému klíči.

```cpp
iterator find(const Key& key);

const_iterator find(const Key& key) const;
```

### <a name="parameters"></a>Parametry

*Klíč*<br/>
Klíč argumentu k porovnání s klíči řazení prvek z hash_set vyhledávaná.

### <a name="return-value"></a>Návratová hodnota

`iterator` Nebo `const_iterator` , který adresuje umístění prvku odpovídající zadanému klíči nebo, který adresuje umístění následující po posledním prvku v hash_set – Pokud pro klíč není nalezena žádná shoda.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí iterátor adresující prvek v hash_set, jehož klíč řazení je `equivalent` na argument klíče pod binární predikát, který indukuje má za výsledek řazení podle méně – než srovnání vztah.

Pokud návratová hodnota `find` přiřazen `const_iterator`, hash_set objekt nelze změnit. Pokud návratová hodnota `find` je přiřazena `iterator`, objekt hash_set lze upravit.

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

## <a name="get_allocator"></a>  hash_set::get_allocator

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set – třída](../standard-library/unordered-set-class.md).

Vrátí kopii přidělování objektu používanou k vytvoření hash_set.

```cpp
Allocator get_allocator() const;
```

### <a name="return-value"></a>Návratová hodnota

Allocator slouží ke správě paměti, což je parametr šablony hash_set *alokátoru*.

Další informace o *alokátoru*, najdete v části poznámky [hash_set – třída](../standard-library/hash-set-class.md) tématu.

### <a name="remarks"></a>Poznámky

Alokátory pro hash_set – Třída zadejte, jak spravuje třídu úložiště. Výchozí alokátorů součástí třídy kontejneru standardní knihovny C++ postačí pro většinu programovacích potřeb. Psaní a použití vlastní třídu alokátoru je rozšířená C++.

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

## <a name="hash_set"></a>  hash_set::hash_set

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set – třída](../standard-library/unordered-set-class.md).

Vytvoří `hash_set` , který je prázdný nebo, který je kopií celého nebo části některého jiného `hash_set`.

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
|*Al*|Třída úložiště alokátoru má být použit pro toto `hash_set` objekt, kde je použit výchozí `Allocator`.|
|*Kompozice*|Funkce porovnání typu `const Traits` slouží k seřazení prvků v `hash_set`, která má výchozí hodnotu `hash_compare`.|
|*doprava*|`hash_set` z nich vytvořeného `hash_set` je kopií.|
|*první*|Pozice prvního prvku v rozsahu prvků, které se mají zkopírovat.|
|*poslední*|Pozice prvního prvku mimo rozsah prvků, které se mají zkopírovat.|

### <a name="remarks"></a>Poznámky

Všechny konstruktory ukládají objekt alokátoru, který spravuje úložiště paměti pro typ `hash_set` a, který lze později vrátit voláním [hash_set::get_allocator](#get_allocator). Parametr allocator je často v deklaraci třídy vynechán a makra předběžného zpracování jsou použita k nahrazení alternativních alokátorů.

Všechny konstruktory inicializují své hash_sets.

Všechny konstruktory ukládají objekt funkce typu `Traits` , který slouží k vytvoření pořadí mezi klíči objektu `hash_set` a, který lze později vrátit voláním [hash_set::key_comp](#key_comp). Další informace o `Traits` najdete v článku [hash_set – třída](../standard-library/hash-set-class.md) tématu.

První konstruktor vytvoří prázdný počáteční `hash_set` druhý určuje typ funkce porovnání ( `Comp`) který se má použít při stanovení pořadí prvků a třetí explicitně určuje typ alokátoru ( `Al`) bude použít. Klíčové slovo `explicit` potlačí některé druhy automatického převodu typu.

Čtvrtý a pátý konstruktor určuje kopii `hash_set` `Right`.

Poslední šestý, sedmý a osmý konstruktor používá prvků objekt initializer_list.

Poslední konstruktory kopírují rozsah [ `First`, `Last`) z `hash_set` se zvyšující se explicitností v určování typu funkce porovnání třídy vlastností a alokátoru.

Osmý konstruktor přesune `hash_set` `Right`.

Skutečné pořadí prvků v `hash_set` kontejneru závisí na hashovací funkci, funkci pořadí a aktuální velikost-the-hash tabulku a nelze, předpovědět obecně platí, protože mohl až s kontejnerem sady, ve kterém bylo zjištěno podle pořadí samotné funkce.

## <a name="insert"></a>  hash_set::Insert

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set – třída](../standard-library/unordered-set-class.md).

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
|*Val*|Hodnota element, který má být vložen do `hash_set` není-li `hash_set` již obsahuje tento prvek nebo obecně platí, element, jehož klíč je ekvivalentně seřazen.|
|*kde*|Místo zahájení vyhledání správného bodu vložení. (Vložení může dojít v amortizovaném konstantním času, namísto logaritmické času, pokud kurzor bezprostředně následuje po `_Where`.)|
|*první*|Pozice prvního prvku, které se mají zkopírovat ze `hash_set`.|
|*poslední*|Pozice bezprostředně za posledním prvkem, které se mají zkopírovat ze `hash_set`.|
|*IList*|Seznam initializer_list, ze kterého chcete kopírovat prvky.|

### <a name="return-value"></a>Návratová hodnota

První `insert` členská funkce vrátí pár jehož **bool** vrátí komponenty **true** Pokud vložení bylo zkontrolujte a **false** Pokud `hash_set` již obsahuje prvek, jehož klíč má ekvivalentní hodnotu v pořadí, a jehož komponenta iterátoru vrátí adresu, kde byl vložen nový element nebo element se kdy již nachází.

Chcete-li přistupovat ke komponentě iterátoru dvojice `pr` vrácený tato členská funkce, použijte `pr.first` a chcete-li přistoupit přes ukazatel, použijte `*(pr.first)`. Pro přístup **bool** součásti páru `pr` vrácený tato členská funkce, použijte `pr.second`a můžete přistoupit přes ukazatel, pomocí `*(pr.second)`.

Druhá `insert` členská funkce vrátí iterátor, který odkazuje na místo, kde byl vložen nový prvek do `hash_set`.

### <a name="remarks"></a>Poznámky

Třetí členská funkce vloží prvků objekt initializer_list.

Třetí členská funkce vloží sekvenci hodnot prvků do `hash_set` odpovídá každému prvku určenému pomocí iterátoru v rozsahu [ `First`, `Last`) zadaného `hash_set`.

## <a name="iterator"></a>  hash_set::iterator

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set – třída](../standard-library/unordered-set-class.md).

Typ, který poskytuje obousměrný iterátor, který může číst nebo upravovat libovolný prvek v hash_set.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::iterator iterator;
```

### <a name="remarks"></a>Poznámky

Typ `iterator` lze použít ke změně hodnoty prvku.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [začít](#begin) příklad toho, jak deklarace a používání `iterator`.

## <a name="key_comp"></a>  hash_set::key_comp

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set – třída](../standard-library/unordered-set-class.md).

Získá kopii objektu hash vlastností použita pro hodnoty hash a pořadí hodnoty klíče prvku v hash_set –.

```cpp
key_compare key_comp() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí objekt funkce, která hash_set – používá k seřazení prvků, což je parametr šablony *osobnostní rysy*.

Další informace o *osobnostní rysy* najdete v článku [hash_set – třída](../standard-library/hash-set-class.md) tématu.

### <a name="remarks"></a>Poznámky

Uložený objekt definuje členskou funkci:

**BOOL – operátor**( **const Key &** _ *xVal*, **const Key &** \_ `yVal`);

který vrátí **true** Pokud `_xVal` předchází a není rovno `_yVal` v pořadí řazení.

Všimněte si, že oba [key_compare](#key_compare) a [value_compare –](#value_compare) jsou synonyma pro parametr šablony *osobnostní rysy*. Oba typy jsou k dispozici pro hash_set – a hash_multiset – třídy, ve kterém jsou identické, z důvodu kompatibility s třídami hash_map – a hash_multimap – kde se liší.

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

## <a name="key_compare"></a>  hash_set::key_compare

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set – třída](../standard-library/unordered-set-class.md).

Typ poskytující objekt funkce, který může porovnat dva klíče řazení pro určení relativního pořadí dvou prvků v hash_set.

```cpp
typedef Traits key_compare;
```

### <a name="remarks"></a>Poznámky

`key_compare` je synonymum pro parametr šablony *osobnostní rysy*.

Další informace o *osobnostní rysy* najdete v článku [hash_set – třída](../standard-library/hash-set-class.md) tématu.

Všimněte si, že oba `key_compare` a [value_compare –](#value_compare) jsou synonyma pro parametr šablony *osobnostní rysy*. Oba typy jsou k dispozici pro sadu a multiset – třídy, kde jsou identické, z důvodu kompatibility s mapy a multimap třídy, ve kterém se liší.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [key_comp](#key_comp) příklad toho, jak deklarace a používání `key_compare`.

## <a name="key_type"></a>  hash_set::key_type

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set – třída](../standard-library/unordered-set-class.md).

Typ, který popisuje objekt uložený jako prvek sady hash_set v jeho kapacitě jako klíč řazení.

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>Poznámky

`key_type` je synonymum pro parametr šablony *klíč*.

Další informace o *klíč*, najdete v části poznámky [hash_set – třída](../standard-library/hash-set-class.md) tématu.

Všimněte si, že oba `key_type` a [value_type](#value_type) jsou synonyma pro parametr šablony *klíč*. Oba typy jsou k dispozici pro hash_set – a hash_multiset – třídy, ve kterém jsou identické, z důvodu kompatibility s třídami hash_map – a hash_multimap – kde se liší.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [value_type](#value_type) příklad toho, jak deklarace a používání `key_type`.

## <a name="lower_bound"></a>  hash_set::lower_bound

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set – třída](../standard-library/unordered-set-class.md).

Vrátí iterátor na první prvek v hash_set s klíčem, který je roven nebo větší než zadaný klíč.

```cpp
const_iterator lower_bound(const Key& key) const;

iterator lower_bound(const Key& key);
```

### <a name="parameters"></a>Parametry

*Klíč*<br/>
Klíč argumentu k porovnání s klíči řazení prvek z hash_set vyhledávaná.

### <a name="return-value"></a>Návratová hodnota

`iterator` Nebo `const_iterator` adresy umístění prvku v hash_set, s klíčem, který je roven nebo větší než tento klíč argument nebo který adresuje umístění následující po posledním prvku v hash_set – pokud odpovídají je nalezen klíč.

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

## <a name="max_size"></a>  hash_set::max_size

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set – třída](../standard-library/unordered-set-class.md).

Vrátí maximální délku objektu hash_set.

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

## <a name="op_eq"></a>  hash_set::Operator =

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set – třída](../standard-library/unordered-set-class.md).

Nahradí prvky objektu hash_set kopií jiného hash_set.

```cpp
hash_set& operator=(const hash_set& right);

hash_set& operator=(hash_set&& right);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|-|-|
|*doprava*|[Hash_set](../standard-library/hash-set-class.md) kopírovaná do `hash_set`.|

### <a name="remarks"></a>Poznámky

Po odstranění jakýchkoli prvků v `hash_set`, `operator=` kopíruje nebo přesouvá obsah *správné* do `hash_set`.

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

## <a name="pointer"></a>  hash_set::Pointer

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set – třída](../standard-library/unordered-set-class.md).

Typ, který poskytuje ukazatel na prvek v hash_set.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::pointer pointer;
```

### <a name="remarks"></a>Poznámky

Typ `pointer` lze použít ke změně hodnoty prvku.

Ve většině případů [iterátoru](#iterator) by měla sloužit pro přístup k prvkům v objektu hash_set.

## <a name="rbegin"></a>  hash_set::rbegin

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set – třída](../standard-library/unordered-set-class.md).

Vrátí iterátor adresující první prvek v obráceném objektu hash_set.

```cpp
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```

### <a name="return-value"></a>Návratová hodnota

Reverzní obousměrný iterátor adresující první prvek v obráceném objektu hash_set nebo co bylo posledním prvkem v neobráceném hash_set adresování.

### <a name="remarks"></a>Poznámky

`rbegin` se používá s obrácený hash_set – stejně jako [začít](#begin) se používá s hash_set.

Pokud návratová hodnota `rbegin` je přiřazen `const_reverse_iterator`, pak hash_set objekt nelze změnit. Pokud návratová hodnota `rbegin` je přiřazena `reverse_iterator`, pak objekt hash_set lze upravit.

`rbegin` můžete použít k iteraci v rámci hash_set zpětně.

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
   // throught a hash_set in a forward order
   cout << "The hash_set is: ";
   for ( hs1_Iter = hs1.begin( ) ; hs1_Iter != hs1.end( );
         hs1_Iter++ )
      cout << *hs1_Iter << " ";
   cout << endl;

   // rbegin can be used to start an iteration
   // throught a hash_set in a reverse order
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

## <a name="reference"></a>  hash_set::Reference

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set – třída](../standard-library/unordered-set-class.md).

Typ, který poskytuje odkaz na prvek uložený v hash_set.

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

## <a name="rend"></a>  hash_set::rend

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set – třída](../standard-library/unordered-set-class.md).

Vrátí iterátor adresující umístění následující po posledním prvku v obráceném objektu hash_set.

```cpp
const_reverse_iterator rend() const;

reverse_iterator rend();
```

### <a name="return-value"></a>Návratová hodnota

Reverzní obousměrný iterátor adresující umístění následující po posledním prvku v obráceném objektu hash_set (umístění, ke které došlo před první prvek v neobráceném hash_set).

### <a name="remarks"></a>Poznámky

`rend` se používá s obrácený hash_set – stejně jako [end](#end) se používá s hash_set.

Pokud návratová hodnota `rend` je přiřazen `const_reverse_iterator`, pak hash_set objekt nelze změnit. Pokud návratová hodnota `rend` je přiřazena `reverse_iterator`, pak objekt hash_set lze upravit. Hodnota vrácená `rend` by neměla být dereferencována.

`rend` slouží k otestování pro Určuje, zda zpětný iterátor dosáhl konce jeho hash_set.

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
   // throught a hash_set in a forward order
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

## <a name="reverse_iterator"></a>  hash_set::reverse_iterator

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set – třída](../standard-library/unordered-set-class.md).

Typ, který poskytuje obousměrný iterátor, který může číst nebo upravovat prvek v obráceném objektu hash_set.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::reverse_iterator reverse_iterator;
```

### <a name="remarks"></a>Poznámky

Typ `reverse_iterator` se používá k iteraci v rámci hash_set – v opačném pořadí.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [rbegin –](#rbegin) příklad toho, jak deklarace a používání `reverse_iterator`.

## <a name="size"></a>  hash_set::size

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set – třída](../standard-library/unordered-set-class.md).

Vrátí počet prvků hash_set.

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

## <a name="size_type"></a>  hash_set::size_type

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set – třída](../standard-library/unordered-set-class.md).

Typ celé číslo bez znaménka představující počet prvků v hash_set.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::size_type size_type;
```

### <a name="remarks"></a>Poznámky

### <a name="example"></a>Příklad

Podívejte se na příklad pro [velikost](#size) příklad toho, jak deklarace a používání `size_type`

## <a name="swap"></a>  hash_set::swap

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set – třída](../standard-library/unordered-set-class.md).

Vymění prvky dvou hash_sets.

```cpp
void swap(hash_set& right);
```

### <a name="parameters"></a>Parametry

*doprava*<br/>
Hash_set – argument poskytující prvky pro záměnu s hash_set – cíl.

### <a name="remarks"></a>Poznámky

Žádné odkazy, ukazatele nebo iterátory, které určují prvky ve dvou hash_sets, jehož prvky jsou během výměny nezruší platnost členskou funkci.

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

## <a name="upper_bound"></a>  hash_set::upper_bound

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set – třída](../standard-library/unordered-set-class.md).

Vrátí iterátor na první prvek v hash_set –, který s klíčem, který je větší než zadaný klíč.

```cpp
const_iterator upper_bound(const Key& key) const;

iterator upper_bound(const Key& key);
```

### <a name="parameters"></a>Parametry

*Klíč*<br/>
Klíč argumentu k porovnání s klíči řazení prvek z hash_set vyhledávaná.

### <a name="return-value"></a>Návratová hodnota

`iterator` Nebo `const_iterator` adresy umístění prvku v hash_set, s klíčem, který je roven nebo větší než tento klíč argument nebo který adresuje umístění následující po posledním prvku v hash_set – pokud odpovídají je nalezen klíč.

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

## <a name="value_comp"></a>  hash_set::value_comp

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set – třída](../standard-library/unordered-set-class.md).

Získá kopii objektu porovnání použitého pro seřazení hodnot prvků hash_set –.

```cpp
value_compare value_comp() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí objekt funkce, která hash_set – používá k seřazení prvků, což je parametr šablony *porovnání*.

Další informace o *porovnání*, najdete v části poznámky [hash_set – třída](../standard-library/hash-set-class.md) tématu.

### <a name="remarks"></a>Poznámky

Uložený objekt definuje členskou funkci:

**BOOL – operátor**( **const Key &** _ *xVal*, **const Key &** \_ `yVal`);

který vrátí **true** Pokud `_xVal` předchází a není rovno `_yVal` v pořadí řazení.

Všimněte si, že oba [value_compare –](../standard-library/set-class.md#value_compare) a [key_compare](../standard-library/set-class.md#key_compare) jsou synonyma pro parametr šablony *porovnání*. Oba typy jsou k dispozici pro hash_set – a hash_multiset – třídy, ve kterém jsou identické, z důvodu kompatibility s třídami hash_map – a hash_multimap – kde se liší.

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

## <a name="value_compare"></a>  hash_set::value_compare

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set – třída](../standard-library/unordered-set-class.md).

Typ, který poskytuje dva objekty funkce binárním predikátem třída porovnání, který může porovnat dvě hodnoty prvků ze hash_set pro určení jejich relativního pořadí a unární predikát, který vytvoří hodnotu hash prvky.

```cpp
typedef key_compare value_compare;
```

### <a name="remarks"></a>Poznámky

`value_compare` je synonymum pro parametr šablony *osobnostní rysy*.

Další informace o *osobnostní rysy* najdete v článku [hash_set – třída](../standard-library/hash-set-class.md) tématu.

Všimněte si, že oba [key_compare](#key_compare) a `value_compare` jsou synonyma pro parametr šablony *osobnostní rysy*. Oba typy jsou k dispozici pro hash_set – a hash_multiset – třídy, ve kterém jsou identické, z důvodu kompatibility s třídami hash_map – a hash_multimap – kde se liší.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [value_comp –](#value_comp) příklad toho, jak deklarace a používání `value_compare`.

## <a name="value_type"></a>  hash_set::value_type

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_set – třída](../standard-library/unordered-set-class.md).

Typ, který popisuje objekt uložený jako prvek sady hash_set v jeho kapacitě jako hodnotu.

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

[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)<br/>
