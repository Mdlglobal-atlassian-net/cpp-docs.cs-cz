---
title: multiset – třída
ms.date: 11/04/2016
f1_keywords:
- set/std::multiset
- set/std::multiset::allocator_type
- set/std::multiset::const_iterator
- set/std::multiset::const_pointer
- set/std::multiset::const_reference
- set/std::multiset::const_reverse_iterator
- set/std::multiset::difference_type
- set/std::multiset::iterator
- set/std::multiset::key_compare
- set/std::multiset::key_type
- set/std::multiset::pointer
- set/std::multiset::reference
- set/std::multiset::reverse_iterator
- set/std::multiset::size_type
- set/std::multiset::value_compare
- set/std::multiset::value_type
- set/std::multiset::begin
- set/std::multiset::cbegin
- set/std::multiset::cend
- set/std::multiset::clear
- set/std::multiset::count
- set/std::multiset::crbegin
- set/std::multiset::crend
- set/std::multiset::emplace
- set/std::multiset::emplace_hint
- set/std::multiset::empty
- set/std::multiset::end
- set/std::multiset::equal_range
- set/std::multiset::erase
- set/std::multiset::find
- set/std::multiset::get_allocator
- set/std::multiset::insert
- set/std::multiset::key_comp
- set/std::multiset::lower_bound
- set/std::multiset::max_size
- set/std::multiset::rbegin
- set/std::multiset::rend
- set/std::multiset::size
- set/std::multiset::swap
- set/std::multiset::upper_bound
- set/std::multiset::value_comp
helpviewer_keywords:
- std::multiset [C++]
- std::multiset [C++], allocator_type
- std::multiset [C++], const_iterator
- std::multiset [C++], const_pointer
- std::multiset [C++], const_reference
- std::multiset [C++], const_reverse_iterator
- std::multiset [C++], difference_type
- std::multiset [C++], iterator
- std::multiset [C++], key_compare
- std::multiset [C++], key_type
- std::multiset [C++], pointer
- std::multiset [C++], reference
- std::multiset [C++], reverse_iterator
- std::multiset [C++], size_type
- std::multiset [C++], value_compare
- std::multiset [C++], value_type
- std::multiset [C++], begin
- std::multiset [C++], cbegin
- std::multiset [C++], cend
- std::multiset [C++], clear
- std::multiset [C++], count
- std::multiset [C++], crbegin
- std::multiset [C++], crend
- std::multiset [C++], emplace
- std::multiset [C++], emplace_hint
- std::multiset [C++], empty
- std::multiset [C++], end
- std::multiset [C++], equal_range
- std::multiset [C++], erase
- std::multiset [C++], find
- std::multiset [C++], get_allocator
- std::multiset [C++], insert
- std::multiset [C++], key_comp
- std::multiset [C++], lower_bound
- std::multiset [C++], max_size
- std::multiset [C++], rbegin
- std::multiset [C++], rend
- std::multiset [C++], size
- std::multiset [C++], swap
- std::multiset [C++], upper_bound
- std::multiset [C++], value_comp
ms.assetid: 630e8c10-0ce9-4ad9-8d79-9e91a600713f
ms.openlocfilehash: 67cf79a935df71054dbc5c0ee2eb6ec98dd8b589
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367306"
---
# <a name="multiset-class"></a>multiset – třída

Vícesetová třída standardní knihovny jazyka C++ se používá pro ukládání a načítání dat z kolekce, ve které nemusí být hodnoty obsažených prvků jedinečné a ve kterých slouží jako klíčové hodnoty, podle kterých jsou data automaticky uspořádána. Hodnotu klíče prvku v multisadě nelze změnit přímo. Místo toho musíte odstranit staré hodnoty a vložit prvky s novými hodnotami.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Key, class Compare =less <Key>, class Allocator =allocator <Key>>
class multiset
```

### <a name="parameters"></a>Parametry

*Klíč*\
Typ dat prvku, který bude uložen do multisady.

*Porovnat*\
Typ poskytující objekt funkce, který může porovnat dvě hodnoty prvků pro určení jejich relativního pořadí v multisadě. Binární predikát **menší**\<klíč> je výchozí hodnota.

V jazyce C++14 můžete povolit heterogenní `std::less<>` vyhledávání `std::greater<>` zadáním nebo predikátu, který nemá žádné parametry typu. Další informace naleznete [v tématu Heterogenní vyhledávání v asociativních kontejnerech](../standard-library/stl-containers.md#sequence_containers)

*Přidělování*\
Typ představující uložený objekt alokátoru, který zapouzdřuje informace o přidělování a navrácení paměti zpět multisady. Výchozí hodnota je `allocator<Key>`.

## <a name="remarks"></a>Poznámky

Vícesetová třída standardní knihovny jazyka C++je:

- Asociativní kontejner, což je kontejner proměnné velikosti, který podporuje efektivní načtení hodnoty prvku založené na přiřazené hodnotě klíče.

- Oboustranný, protože poskytuje obousměrné iterátory pro přístup k jeho prvkům.

- Seřazený, protože jeho prvky jsou řazeny podle hodnot klíče v kontejneru podle zadané porovnávací funkce.

- Vícenásobný v tom smyslu, že jeho prvky nemusí mít jedinečné klíče, takže jedna hodnota klíče může mít k sobě přidružených mnoho hodnot prvků.

- Jednoduchý asociativní kontejner, protože jeho hodnoty prvku jsou jeho hodnoty klíče.

- Šablona třídy, protože funkce, které poskytuje, je obecná a tak nezávislá na konkrétním typu dat obsažených jako prvky. Datový typ, který má být použit, je místo toho zadán jako parametr v šabloně třídy společně s funkcí porovnání a alokátorem.

Iterátor poskytované multiset třídy je obousměrný iterátor, ale funkce členů třídy [vložit](#insert) a [multiset](#multiset) mají verze, které berou jako parametry šablony slabší vstupní iterátor, jehož požadavky na funkčnost jsou minimální než ty, které jsou zaručeny třídy obousměrné iterátory. Různé koncepty iterátorů tvoří rodinu týkající se upřesnění jejich funkčnosti. Každý koncept iterátoru má vlastní sadu požadavků a algoritmy, které s nimi pracují, musí omezit jejich předpoklady na požadavky podle typu iterátoru. Lze předpokládat, že ke vstupnímu iterátoru lze přistoupit přes ukazatel pro odkazování na některý objekt a že může být zvýšen na další iterátor v pořadí. Jedná se o minimální sadu funkcí, ale stačí, abyste mohli smysluplně hovořit o řadě iterátorů [ `First`, `Last`) v kontextu členských funkcí třídy.

Volba typu kontejneru by měla obecně vycházet z typu vyhledávání a vkládání vyžadovaného aplikací. Asociativní kontejnery jsou optimalizovány pro operace vyhledávání, vkládání a odstranění. Členské funkce, které explicitně podporují tyto operace, jsou efektivní a jsou prováděny v čase, který je průměrně úměrný logaritmu počtu prvků v kontejneru. Vkládání prvků nezruší platnost žádných iterátorů a odstranění prvků zruší platnost pouze těch iterátorů, které výslovně odkazovaly na odstraněné prvky.

Objekt multisady (multiset) by měl být asociativní kontejner dle výběru, kdy jsou podmínky přiřazení hodnot k jejich klíčům splněny aplikací. Prvků multisady může být více a slouží jako vlastní klíče řazení, takže klíče nejsou jedinečné. Model pro tento typ struktury je uspořádaný seznam slov, v němž se slova mohou vyskytovat více než jednou. Pokud by nebylo povoleno více výskytů jednoho slova, byl by objekt set odpovídající strukturou kontejneru. Pokud byly k seznamu jedinečných klíčových slov připojeny jedinečné definice jako hodnoty, objekt map by byl vhodnou strukturou, který by měla tato data obsahovat. Pokud by však definice nebyly jedinečné, byl by zvoleným kontejnerem multimap.

Vícesetová sestavu uskuteční pořadí sekvence, kterou řídí, voláním uloženého objektu funkce typu *Porovnat*. Tento uložený objekt je funkce porovnání, ke které lze přistupovat voláním členské funkce [key_comp](#key_comp). Obecně, tyto prvky musí být menší než srovnatelné pro toto pořadí, což znamená, že když jsou uvedeny dva prvky, může být stanoveno, zda jsou ekvivalentní (v tom smyslu, že ani jeden není menší než ten druhý), nebo že jeden je menší než druhý. To má za výsledek řazení mezi neekvivalentními prvky. Technicky je funkce porovnání binárním predikátem, který indukuje přísné slabé řazení, standardním matematickým způsobem. Binární predikát *f*( *x*, *y*) je objekt funkce, který má dva argumenty objekty *x* a *y* a vrácenou hodnotu **true** nebo **false**. Řazení uložené na sadu je přísné slabé řazení, pokud binární predikát je nereflexivní, antisymetrické a tranzitivní a pokud je ekvivalence přenosná, kde jsou dva objekty x a y definovány jako ekvivalentní, pokud jsou oba *f*( *x, y*) a *f*( *y, x*) false. Pokud silnější podmínka rovnosti mezi klíči nahradí ekvivalenci, stane se pořadí celkovým (v tom smyslu, že všechny prvky jsou uspořádány ve vztahu k sobě navzájem) a odpovídající klíče budou od sebe nerozeznatelné.

V jazyce C++14 můžete povolit heterogenní `std::less<>` vyhledávání `std::greater<>` zadáním nebo predikátu, který nemá žádné parametry typu. Další informace naleznete [v tématu Heterogenní vyhledávání v asociativních kontejnerech](../standard-library/stl-containers.md#sequence_containers)

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[vícesetový soubor](#multiset)|Konstrukce, `multiset` který je prázdný nebo který je kopií celénebo část zadaného `multiset`.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[allocator_type](#allocator_type)|Typedef pro `allocator` třídu `multiset` pro objekt.|
|[const_iterator](#const_iterator)|Typedef pro obousměrný iterátor, který může číst **const** prvek v `multiset`.|
|[const_pointer](#const_pointer)|Typedef pro ukazatel na **const** element `multiset`v .|
|[const_reference](#const_reference)|Typedef pro odkaz na **const** prvek `multiset` uložený v a pro čtení a provádění **const** operace.|
|[const_reverse_iterator](#const_reverse_iterator)|Typedef pro obousměrný iterátor, který může číst libovolný `multiset` **prvek const** v .|
|[difference_type](#difference_type)|Podepsané celé číslo typedef pro počet prvků `multiset` v rozsahu mezi prvky, na které se vztahuje iterátory.|
|[Iterace](#iterator)|Typedef pro obousměrný iterátor, který můžete číst nebo `multiset`upravovat libovolný prvek v .|
|[key_compare](#key_compare)|Typedef pro objekt funkce, který může porovnat dva klíče k `multiset`určení relativní pořadí dvou prvků v .|
|[key_type](#key_type)|Typedef pro objekt funkce, který může porovnat dva klíče řazení k `multiset`určení relativní pořadí dvou prvků v .|
|[ukazatel](#pointer)|Typedef pro ukazatel na prvek `multiset`v .|
|[Odkaz](#reference)|Typedef pro odkaz na prvek uložený `multiset`v .|
|[reverse_iterator](#reverse_iterator)|Typedef pro obousměrný iterátor, který může číst nebo upravovat `multiset`prvek v obráceném .|
|[size_type](#size_type)|Nepodepsaný podnosný typ, který může představovat počet prvků v . `multiset`|
|[value_compare](#value_compare)|Typedef pro objekt funkce, který může porovnat dva prvky jako `multiset`klíče řazení k určení jejich relativní pořadí v .|
|[value_type](#value_type)|Typedef, který popisuje objekt uložený jako `multiset` prvek jako v jeho kapacitě jako hodnotu.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[Začít](#begin)|Vrátí iterátor, který odkazuje na první `multiset`prvek v .|
|[cbegin](#cbegin)|Vrátí const iterator, který řeší první `multiset`prvek v rozhraní .|
|[cend](#cend)|Vrátí const iterátor, který řeší umístění, které následuje `multiset`poslední prvek v .|
|[Jasné](#clear)|Vymaže všechny `multiset`prvky .|
|[Počet](#count)|Vrátí počet prvků v `multiset` klíči, jejichž klíč odpovídá klíči určenému jako parametr.|
|[crbegin](#crbegin)|Vrátí konstantní iterátor adresující první prvek v obráceném objektu set.|
|[crend](#crend)|Vrátí konstantní iterátor adresující umístění následující po posledním prvku v obráceném objektu set.|
|[místo](#emplace)|Vloží prvek vytvořený na místě `multiset`do .|
|[emplace_hint](#emplace_hint)|Vloží prvek vytvořený na místě `multiset`do aplikace s nápovědou k umístění.|
|[empty](#empty)|Testuje, `multiset` pokud je prázdný.|
|[Konec](#end)|Vrátí iterátor, který odkazuje na umístění za `multiset`poslední prvek v .|
|[equal_range](#equal_range)|Vrátí pár iterátorů. První iterátor v páru odkazuje na první `multiset` prvek v klíč, který je větší než zadaný klíč. Druhý iterátor v páru odkazuje na první `multiset` prvek s klíčem, který je roven nebo větší než klíč.|
|[Vymazat](#erase)|Odebere prvek nebo rozsah prvků `multiset` v a ze zadané pozice nebo odebere prvky, které odpovídají zadanému klíči.|
|[find](#find)|Vrátí iterátor, který odkazuje na první umístění `multiset` prvku v a, který má klíč rovnající se zadanému klíči.|
|[get_allocator](#get_allocator)|Vrátí kopii `allocator` objektu, který se `multiset`používá k vytvoření .|
|[Vložit](#insert)|Vloží prvek nebo rozsah prvků do `multiset`.|
|[key_comp](#key_comp)|Poskytuje objekt funkce, který může porovnat dvě klávesy řazení `multiset`k určení relativního pořadí dvou prvků v rozhraní .|
|[lower_bound](#lower_bound)|Vrátí iterátor k prvnímu prvku `multiset` v a s klíčem, který je roven nebo větší než zadaný klíč.|
|[max_size](#max_size)|Vrátí maximální délku `multiset`.|
|[rbegin](#rbegin)|Vrátí iterátor, který odkazuje na první `multiset`prvek v obráceném .|
|[rend](#rend)|Vrátí iterátor, který odkazuje na umístění, které následuje `multiset`poslední prvek v obráceném .|
|[Velikost](#size)|Vrátí počet prvků v `multiset`rozhraní .|
|[Swap](#swap)|Vyměňuje prvky `multiset`dvou s.|
|[upper_bound](#upper_bound)|Vrátí iterátor na první prvek `multiset` v s klíčem, který je větší než zadaný klíč.|
|[value_comp](#value_comp)|Načte kopii objektu porovnání, který se používá `multiset`k pořadí hodnot prvků v .|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operátor =](#op_eq)|Nahradí prvky a `multiset` kopií jiného `multiset`.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<nastavit>

**Obor názvů:** std

## <a name="multisetallocator_type"></a><a name="allocator_type"></a>multiset::allocator_type

Typ, který představuje třídu alokátoru pro vícesetový objekt

```cpp
typedef Allocator allocator_type;
```

### <a name="remarks"></a>Poznámky

`allocator_type`je synonymem pro `Allocator`parametr šablony .

Další informace `Allocator`o tématu naleznete v části Poznámky v tématu [Vícesetové třídy.](../standard-library/multiset-class.md)

### <a name="example"></a>Příklad

Podívejte se na příklad [pro get_allocator](#get_allocator) příklad pomocí`allocator_type`

## <a name="multisetbegin"></a><a name="begin"></a>multiset::begin

Vrátí iterátor adresující první prvek ve vícesadí.

```cpp
const_iterator begin() const;

iterator begin();
```

### <a name="return-value"></a>Návratová hodnota

Obousměrný itečelní objekt adresující první prvek ve vícesetové sadě nebo umístění, které následuje prázdnou multisadu.

### <a name="example"></a>Příklad

```cpp
// multiset_begin.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   multiset <int> ms1;
   multiset <int>::iterator ms1_Iter;
   multiset <int>::const_iterator ms1_cIter;

   ms1.insert( 1 );
   ms1.insert( 2 );
   ms1.insert( 3 );

   ms1_Iter = ms1.begin( );
   cout << "The first element of ms1 is " << *ms1_Iter << endl;

   ms1_Iter = ms1.begin( );
   ms1.erase( ms1_Iter );

   // The following 2 lines would err as the iterator is const
   // ms1_cIter = ms1.begin( );
   // ms1.erase( ms1_cIter );

   ms1_cIter = ms1.begin( );
   cout << "The first element of ms1 is now " << *ms1_cIter << endl;
}
```

```Output
The first element of ms1 is 1
The first element of ms1 is now 2
```

## <a name="multisetcbegin"></a><a name="cbegin"></a>multiset::cbegin

Vrátí **const** iterator, který řeší první prvek v rozsahu.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>Návratová hodnota

**Konstovat** obousměrný přístup iterátor, který odkazuje na první prvek rozsahu nebo umístění těsně za koncem prázdné `cbegin() == cend()`oblasti (pro prázdný rozsah, ).

### <a name="remarks"></a>Poznámky

S vrácenou `cbegin`hodnotou , prvky v rozsahu nelze změnit.

Tuto člennou funkci můžete použít `begin()` místo členské funkce k `const_iterator`zajištění, že vrácená hodnota je . Obvykle se používá ve spojení s klíčovým slovem [automatického](../cpp/auto-cpp.md) odpočtu typu, jak je znázorněno v následujícím příkladu. V příkladu `Container` zvažte upravitelné (non-const) kontejner jakéhokoli druhu, `cbegin()`který podporuje **const** `begin()` a .

```cpp
auto i1 = Container.begin();
// i1 is Container<T>::iterator
auto i2 = Container.cbegin();

// i2 is Container<T>::const_iterator
```

## <a name="multisetcend"></a><a name="cend"></a>multiset::cend

Vrátí **const** iterator, který řeší umístění těsně za poslední prvek v rozsahu.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>Návratová hodnota

**Const** obousměrný přístup iterátor, který ukazuje těsně za koncem rozsahu.

### <a name="remarks"></a>Poznámky

`cend`se používá k testování, zda iterátor prošel koncem svého rozsahu.

Tuto člennou funkci můžete použít `end()` místo členské funkce k `const_iterator`zajištění, že vrácená hodnota je . Obvykle se používá ve spojení s klíčovým slovem [automatického](../cpp/auto-cpp.md) odpočtu typu, jak je znázorněno v následujícím příkladu. V příkladu `Container` zvažte upravitelné (non-const) kontejner jakéhokoli druhu, `cend()`který podporuje **const** `end()` a .

```cpp
auto i1 = Container.end();
// i1 is Container<T>::iterator
auto i2 = Container.cend();

// i2 is Container<T>::const_iterator
```

Hodnota vrácená `cend` by neměla být odkazována.

## <a name="multisetclear"></a><a name="clear"></a>multiset::vymazat

Vymaže všechny prvky multiset.

```cpp
void clear();
```

### <a name="example"></a>Příklad

```cpp
// multiset_clear.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   multiset <int> ms1;

   ms1.insert( 1 );
   ms1.insert( 2 );

   cout << "The size of the multiset is initially "
        << ms1.size( ) << "." << endl;

   ms1.clear( );
   cout << "The size of the multiset after clearing is "
        << ms1.size( ) << "." << endl;
}
```

```Output
The size of the multiset is initially 2.
The size of the multiset after clearing is 0.
```

## <a name="multisetconst_iterator"></a><a name="const_iterator"></a>multiset::const_iterator

Typ, který poskytuje obousměrný iterátor, který může číst **const** prvek ve víceset.

```cpp
typedef implementation-defined const_iterator;
```

### <a name="remarks"></a>Poznámky

Typ `const_iterator` nelze použít ke změně hodnoty prvku.

### <a name="example"></a>Příklad

Viz příklad pro [začátek](#begin) `const_iterator`pro příklad pomocí .

## <a name="multisetconst_pointer"></a><a name="const_pointer"></a>multiset::const_pointer

Typ, který poskytuje ukazatel na **prvek const** ve vícesetové sadě.

```cpp
typedef typename allocator_type::const_pointer const_pointer;
```

### <a name="remarks"></a>Poznámky

Typ `const_pointer` nelze použít ke změně hodnoty prvku.

Ve většině případů [iterátor](#iterator) by měl být použit pro přístup k prvkům v objektu více sad.

## <a name="multisetconst_reference"></a><a name="const_reference"></a>multiset::const_reference

Typ, který poskytuje odkaz na **const** prvek uložený ve vícesadépro čtení a provádění **const** operací.

```cpp
typedef typename allocator_type::const_reference const_reference;
```

### <a name="example"></a>Příklad

```cpp
// multiset_const_ref.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   multiset <int> ms1;

   ms1.insert( 10 );
   ms1.insert( 20 );

   // Declare and initialize a const_reference &Ref1
   // to the 1st element
   const int &Ref1 = *ms1.begin( );

   cout << "The first element in the multiset is "
        << Ref1 << "." << endl;

   // The following line would cause an error because the
   // const_reference cannot be used to modify the multiset
   // Ref1 = Ref1 + 5;
}
```

```Output
The first element in the multiset is 10.
```

## <a name="multisetconst_reverse_iterator"></a><a name="const_reverse_iterator"></a>multiset::const_reverse_iterator

Typ, který poskytuje obousměrný iterátor, který může číst libovolný **prvek const** ve vícesad.

```cpp
typedef std::reverse_iterator<const_iterator> const_reverse_iterator;
```

### <a name="remarks"></a>Poznámky

Typ `const_reverse_iterator` nemůže změnit hodnotu prvku a je používán k iterátu prostřednictvím vícesetových v opačném směru.

### <a name="example"></a>Příklad

Příklad pro [rend](#rend) naleznete v příkladu, jak `const_reverse_iterator`deklarovat a používat .

## <a name="multisetcount"></a><a name="count"></a>multiset::počet

Vrátí počet prvků ve vícesadě, jejichž klíč odpovídá klíči zadanému parametrem.

```cpp
size_type count(const Key& key) const;
```

### <a name="parameters"></a>Parametry

*Klíč*\
Klíč prvků, které mají být uzavřeno z multiset.

### <a name="return-value"></a>Návratová hodnota

Počet prvků ve vícesadě, jejichž klíč řazení odpovídá klíči parametru.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí počet prvků *x* v rozsahu

\[lower_bound(*klíč*), upper_bound(*klíč*)

### <a name="example"></a>Příklad

Následující příklad ukazuje použití multiset::count členské funkce.

```cpp
// multiset_count.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main()
{
    using namespace std;
    multiset<int> ms1;
    multiset<int>::size_type i;

    ms1.insert(1);
    ms1.insert(1);
    ms1.insert(2);

    // Elements do not need to be unique in multiset,
    // so duplicates are allowed and counted.
    i = ms1.count(1);
    cout << "The number of elements in ms1 with a sort key of 1 is: "
         << i << "." << endl;

    i = ms1.count(2);
    cout << "The number of elements in ms1 with a sort key of 2 is: "
         << i << "." << endl;

    i = ms1.count(3);
    cout << "The number of elements in ms1 with a sort key of 3 is: "
         << i << "." << endl;
}
```

```Output
The number of elements in ms1 with a sort key of 1 is: 2.
The number of elements in ms1 with a sort key of 2 is: 1.
The number of elements in ms1 with a sort key of 3 is: 0.
```

## <a name="multisetcrbegin"></a><a name="crbegin"></a>multiset::crbegin

Vrátí const iterator adresování první prvek v obrácené multiset.

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>Návratová hodnota

Const reverzní obousměrný iterátor adresování první prvek v obrácené multiset nebo adresování co byl poslední prvek v unreverse multiset.

### <a name="remarks"></a>Poznámky

`crbegin`se používá s obráceným multisetstejně jako begin se používá s multiset.

S vrácenou `crbegin`hodnotou aplikace nelze objekt vícesad změnit.

`crbegin`lze použít k iterátu přes multiset dozadu.

### <a name="example"></a>Příklad

```cpp
// multiset_crbegin.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   multiset <int> ms1;
   multiset <int>::const_reverse_iterator ms1_crIter;

   ms1.insert( 10 );
   ms1.insert( 20 );
   ms1.insert( 30 );

   ms1_crIter = ms1.crbegin( );
   cout << "The first element in the reversed multiset is "
        << *ms1_crIter << "." << endl;
}
```

```Output
The first element in the reversed multiset is 30.
```

## <a name="multisetcrend"></a><a name="crend"></a>multiset::crend

Vrátí const iterátor, který řeší umístění, které následuje poslední prvek v obrácené multisadě.

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>Návratová hodnota

Const reverzní obousměrný iterátor, který řeší umístění následující poslední prvek v obrácené multiset (umístění, které předcházelo první prvek v unreverse multiset).

### <a name="remarks"></a>Poznámky

`crend`se používá s obrácenou multisad stejně jako [konec](#end) se používá s multiset.

S vrácenou `crend`hodnotou aplikace nelze objekt vícesad změnit.

`crend`lze použít k testování, zda reverzní iterátor dosáhl konce svého multiset.

Hodnota vrácená `crend` by neměla být odkazována.

### <a name="example"></a>Příklad

```cpp
// multiset_crend.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main() {
   using namespace std;
   multiset <int> ms1;
   multiset <int>::const_reverse_iterator ms1_crIter;

   ms1.insert( 10 );
   ms1.insert( 20 );
   ms1.insert( 30 );

   ms1_crIter = ms1.crend( ) ;
   ms1_crIter--;
   cout << "The last element in the reversed multiset is "
        << *ms1_crIter << "." << endl;
}
```

## <a name="multisetdifference_type"></a><a name="difference_type"></a>multiset::difference_type

Podepsaný typ celé číslo, který lze použít k reprezentaci počtu prvků vícesad v rozsahu mezi prvky, na které se iterátory upozorují.

```cpp
typedef typename allocator_type::difference_type difference_type;
```

### <a name="remarks"></a>Poznámky

Je `difference_type` typ vrácena při odečtení nebo zvýšení prostřednictvím iterátory kontejneru. Obvykle `difference_type` se používá k reprezentaci počtu prvků `first` `last`v rozsahu [ , `first` ) `last`mezi iterátory `first` a , zahrnuje prvek, na který se vztahuje, a rozsah prvků až do prvku, na který je však `last`nezahrnuto.

Všimněte `difference_type` si, že i když je k dispozici pro všechny iterátory, které splňují požadavky vstupníitekor, který zahrnuje třídu obousměrné iterátory podporované reverzibilní kontejnery, jako je set, odčítání mezi iterátory je podporován pouze random-access iterátory poskytované náhodný přístup kontejneru, jako je vektor.

### <a name="example"></a>Příklad

```cpp
// multiset_diff_type.cpp
// compile with: /EHsc
#include <iostream>
#include <set>
#include <algorithm>

int main( )
{
   using namespace std;

   multiset <int> ms1;
   multiset <int>::iterator ms1_Iter, ms1_bIter, ms1_eIter;

   ms1.insert( 20 );
   ms1.insert( 10 );
   ms1.insert( 20 );

   ms1_bIter = ms1.begin( );
   ms1_eIter = ms1.end( );

   multiset <int>::difference_type   df_typ5, df_typ10, df_typ20;

   df_typ5 = count( ms1_bIter, ms1_eIter, 5 );
   df_typ10 = count( ms1_bIter, ms1_eIter, 10 );
   df_typ20 = count( ms1_bIter, ms1_eIter, 20 );

   // The keys, and hence the elements, of a multiset are not unique
   cout << "The number '5' occurs " << df_typ5
        << " times in multiset ms1.\n";
   cout << "The number '10' occurs " << df_typ10
        << " times in multiset ms1.\n";
   cout << "The number '20' occurs " << df_typ20
        << " times in multiset ms1.\n";

   // Count the number of elements in a multiset
   multiset <int>::difference_type  df_count = 0;
   ms1_Iter = ms1.begin( );
   while ( ms1_Iter != ms1_eIter)
   {
      df_count++;
      ms1_Iter++;
   }

   cout << "The number of elements in the multiset ms1 is: "
        << df_count << "." << endl;
}
```

```Output
The number '5' occurs 0 times in multiset ms1.
The number '10' occurs 1 times in multiset ms1.
The number '20' occurs 2 times in multiset ms1.
The number of elements in the multiset ms1 is: 3.
```

## <a name="multisetemplace"></a><a name="emplace"></a>multiset::emplace

Vloží prvek vytvořený na místě (nejsou prováděny žádné operace kopírování nebo přesunutí) s nápovědou k umístění.

```cpp
template <class... Args>
iterator emplace(Args&&... args);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|-|-|
|*Args*|Argumenty předány k vytvoření prvku, který má být vložen do multiset.|

### <a name="return-value"></a>Návratová hodnota

Iterátor nově vloženého prvku.

### <a name="remarks"></a>Poznámky

Žádné odkazy na prvky kontejneru jsou zrušena touto funkcí, ale může zneplatnit všechny iterátory do kontejneru.

Během umístění, pokud je vyvolána výjimka, stav kontejneru není změněn.

### <a name="example"></a>Příklad

```cpp
// multiset_emplace.cpp
// compile with: /EHsc
#include <set>
#include <string>
#include <iostream>

using namespace std;

template <typename S> void print(const S& s) {
    cout << s.size() << " elements: ";

    for (const auto& p : s) {
        cout << "(" << p << ") ";
    }

    cout << endl;
}

int main()
{
    multiset<string> s1;

    s1.emplace("Anna");
    s1.emplace("Bob");
    s1.emplace("Carmine");

    cout << "multiset modified, now contains ";
    print(s1);
    cout << endl;

    s1.emplace("Bob");

    cout << "multiset modified, now contains ";
    print(s1);
    cout << endl;
}
```

## <a name="multisetemplace_hint"></a><a name="emplace_hint"></a>multiset::emplace_hint

Vloží prvek vytvořený na místě (nejsou prováděny žádné operace kopírování nebo přesunutí) s nápovědou k umístění.

```cpp
template <class... Args>
iterator emplace_hint(
    const_iterator where,
    Args&&... args);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|-|-|
|*Args*|Argumenty předány k vytvoření prvku, který má být vložen do multiset.|
|*where*|Místo zahájení vyhledání správného bodu vložení. (Pokud tento bod bezprostředně předchází, *kde*, vložení může dojít v amortizované konstantní čas namísto logaritmického času.)|

### <a name="return-value"></a>Návratová hodnota

Iterátor nově vloženého prvku.

### <a name="remarks"></a>Poznámky

Žádné odkazy na prvky kontejneru jsou zrušena touto funkcí, ale může zneplatnit všechny iterátory do kontejneru.

Během umístění, pokud je vyvolána výjimka, stav kontejneru není změněn.

Příklad kódu naleznete v tématu [set::emplace_hint](../standard-library/set-class.md#emplace_hint).

## <a name="multisetempty"></a><a name="empty"></a>multiset::prázdný

Testuje, pokud je vícesetová sada prázdná.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Návratová hodnota

**true,** pokud je multiset prázdný; **false,** pokud multiset je neprázdný.

### <a name="example"></a>Příklad

```cpp
// multiset_empty.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   multiset <int> ms1, ms2;
   ms1.insert ( 1 );

   if ( ms1.empty( ) )
      cout << "The multiset ms1 is empty." << endl;
   else
      cout << "The multiset ms1 is not empty." << endl;

   if ( ms2.empty( ) )
      cout << "The multiset ms2 is empty." << endl;
   else
      cout << "The multiset ms2 is not empty." << endl;
}
```

```Output
The multiset ms1 is not empty.
The multiset ms2 is empty.
```

## <a name="multisetend"></a><a name="end"></a>multiset:end

Vrátí iterátor za koncem.

```cpp
const_iterator end() const;

iterator end();
```

### <a name="return-value"></a>Návratová hodnota

Iterátor z minulosti na konci. Pokud je multiset prázdný, pak `multiset::end() == multiset::begin()`.

### <a name="remarks"></a>Poznámky

**end** se používá k testování, zda iterátor prošel koncem jeho multiset.

Hodnota vrácená **na konci** by neměla být odkazována.

Příklad kódu naleznete v tématu [multiset::find](#find).

## <a name="multisetequal_range"></a><a name="equal_range"></a>multiset::equal_range

Vrátí dvojici iterátorů respektive první prvek ve vícesadé s klíčem, který je větší než zadaný klíč a na první prvek ve vícesadě s klíčem, který je roven nebo větší než klíč.

```cpp
pair <const_iterator, const_iterator> equal_range (const Key& key) const;

pair <iterator, iterator> equal_range (const Key& key);
```

### <a name="parameters"></a>Parametry

*Klíč*\
Klíč argumentu, který má být porovnán s klíčem řazení prvku z prohledávané multisady.

### <a name="return-value"></a>Návratová hodnota

Dvojice iterátorů tak, že první je [lower_bound](#lower_bound) klíče a druhý je [upper_bound](#upper_bound) klíče.

Chcete-li získat přístup k prvnímu iterátoru `pr` `pr`dvojice vrácené členovou funkcí, použijte . **a**dereferencovat nižší mez iterátoru, použijte \*( `pr`. **první**). Chcete-li získat přístup k druhému iterátoru `pr` `pr`dvojice vrácené členovou funkcí, použijte . **druhé**, a pro dereferenci horní mez iterátoru, použijte \*( `pr`. **za druhé**).

### <a name="example"></a>Příklad

```cpp
// multiset_equal_range.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   typedef multiset<int, less<int> > IntSet;
   IntSet ms1;
   multiset <int> :: const_iterator ms1_RcIter;

   ms1.insert( 10 );
   ms1.insert( 20 );
   ms1.insert( 30 );

   pair <IntSet::const_iterator, IntSet::const_iterator> p1, p2;
   p1 = ms1.equal_range( 20 );

   cout << "The upper bound of the element with "
        << "a key of 20 in the multiset ms1 is: "
        << *( p1.second ) << "." << endl;

   cout << "The lower bound of the element with "
        << "a key of 20 in the multiset ms1 is: "
        << *( p1.first ) << "." << endl;

   // Compare the upper_bound called directly
   ms1_RcIter = ms1.upper_bound( 20 );
   cout << "A direct call of upper_bound( 20 ) gives "
        << *ms1_RcIter << "," << endl
        << "matching the 2nd element of the pair"
        << " returned by equal_range( 20 )." << endl;

   p2 = ms1.equal_range( 40 );

   // If no match is found for the key,
   // both elements of the pair return end( )
   if ( ( p2.first == ms1.end( ) ) && ( p2.second == ms1.end( ) ) )
      cout << "The multiset ms1 doesn't have an element "
              << "with a key less than 40." << endl;
   else
      cout << "The element of multiset ms1 with a key >= 40 is: "
                << *( p1.first ) << "." << endl;
}
```

```Output
The upper bound of the element with a key of 20 in the multiset ms1 is: 30.
The lower bound of the element with a key of 20 in the multiset ms1 is: 20.
A direct call of upper_bound( 20 ) gives 30,
matching the 2nd element of the pair returned by equal_range( 20 ).
The multiset ms1 doesn't have an element with a key less than 40.
```

## <a name="multiseterase"></a><a name="erase"></a>multiset::vymazat

Odebere prvek nebo rozsah prvků ve vícesadách ze zadaných pozic nebo odebere prvky, které odpovídají zadanému klíči.

```cpp
iterator erase(
    const_iterator Where);

iterator erase(
    const_iterator First,
    const_iterator Last);

size_type erase(
    const key_type& Key);
```

### <a name="parameters"></a>Parametry

*Kde*\
Pozice prvku, který má být odebrán.

*První*\
Pozice prvního prvku, který má být odebrán.

*Poslední*\
Pozice bezprostředně za posledním prvkem, který má být odebrán.

*Klíč*\
Hodnota klíče prvků, které mají být odebrány.

### <a name="return-value"></a>Návratová hodnota

Pro první dvě členské funkce obousměrný iterátor, který označuje první prvek zbývající za všechny prvky odebrány nebo prvek, který je konec multiset, pokud žádný takový prvek neexistuje.

Pro třetí členfunkce vrátí počet prvků, které byly odebrány z vícesad.

### <a name="remarks"></a>Poznámky

Příklad kódu naleznete v tématu [set::erase](../standard-library/set-class.md#erase).

## <a name="multisetfind"></a><a name="find"></a>multiset::najít

Vrátí iterátor, který odkazuje na umístění prvku ve vícesetu, který má klíč ekvivalentní zadanému klíči.

```cpp
iterator find(const Key& key);

const_iterator find(const Key& key) const;
```

### <a name="parameters"></a>Parametry

*Klíč*\
Hodnota klíče, která má být porovnána s klíčem řazení prvku z prohledávané multisady.

### <a name="return-value"></a>Návratová hodnota

Iterátor, který odkazuje na umístění prvku se zadaným klíčem nebo umístění, které následuje `multiset::end()`poslední prvek ve vícesetové sadě ( ), pokud pro klíč není nalezena žádná shoda.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí iterátor, který odkazuje na prvek ve vícesadě, jehož klíč je ekvivalentní *klíč* argumentu pod binární predikát, který indukuje řazení na základě méně než vztah srovnatelnosti.

Pokud `find` je vrácená hodnota `const_iterator`přiřazena objektu , nelze objekt vícesadí změnit. Pokud `find` je vrácená hodnota `iterator`přiřazena objektu , lze objekt s více sadami změnit.

### <a name="example"></a>Příklad

```cpp
// compile with: /EHsc /W4 /MTd
#include <set>
#include <iostream>
#include <vector>
#include <string>

using namespace std;

template <typename T> void print_elem(const T& t) {
    cout << "(" << t << ") ";
}

template <typename T> void print_collection(const T& t) {
    cout << t.size() << " elements: ";

    for (const auto& p : t) {
        print_elem(p);
    }
    cout << endl;
}

template <typename C, class T> void findit(const C& c, T val) {
    cout << "Trying find() on value " << val << endl;
    auto result = c.find(val);
    if (result != c.end()) {
        cout << "Element found: "; print_elem(*result); cout << endl;
    } else {
        cout << "Element not found." << endl;
    }
}

int main()
{
    multiset<int> s1({ 40, 45 });
    cout << "The starting multiset s1 is: " << endl;
    print_collection(s1);

    vector<int> v;
    v.push_back(43);
    v.push_back(41);
    v.push_back(46);
    v.push_back(42);
    v.push_back(44);
    v.push_back(44); // attempt a duplicate

    cout << "Inserting the following vector data into s1: " << endl;
    print_collection(v);

    s1.insert(v.begin(), v.end());

    cout << "The modified multiset s1 is: " << endl;
    print_collection(s1);
    cout << endl;
    findit(s1, 45);
    findit(s1, 6);
}
```

## <a name="multisetget_allocator"></a><a name="get_allocator"></a>multiset::get_allocator

Vrátí kopii objektu alokátoru použitého k vytvoření multisetu.

```cpp
allocator_type get_allocator() const;
```

### <a name="return-value"></a>Návratová hodnota

Alokátor používaný multiset.

### <a name="remarks"></a>Poznámky

Alokátory pro třídu s více sadami určují, jak třída spravuje úložiště. Výchozí alokátory dodávané s třídami kontejneru standardní knihovny jazyka C++ jsou dostatečné pro většinu potřeb programování. Psaní a používání vlastní třídy přidělování je pokročilé téma jazyka C++.

### <a name="example"></a>Příklad

```cpp
// multiset_get_allocator.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   multiset <int>::allocator_type ms1_Alloc;
   multiset <int>::allocator_type ms2_Alloc;
   multiset <double>::allocator_type ms3_Alloc;
   multiset <int>::allocator_type ms4_Alloc;

   // The following lines declare objects
   // that use the default allocator.
   multiset <int> ms1;
   multiset <int, allocator<int> > ms2;
   multiset <double, allocator<double> > ms3;

   cout << "The number of integers that can be allocated"
        << endl << "before free memory is exhausted: "
        << ms2.max_size( ) << "." << endl;

   cout << "The number of doubles that can be allocated"
        << endl << "before free memory is exhausted: "
        << ms3.max_size( ) <<  "." << endl;

   // The following lines create a multiset ms4
   // with the allocator of multiset ms1
   ms1_Alloc = ms1.get_allocator( );
   multiset <int> ms4( less<int>( ), ms1_Alloc );
   ms4_Alloc = ms4.get_allocator( );

   // Two allocators are interchangeable if
   // storage allocated from each can be
   // deallocated with the other
   if( ms1_Alloc == ms4_Alloc )
   {
      cout << "Allocators are interchangeable."
           << endl;
   }
   else
   {
      cout << "Allocators are not interchangeable."
           << endl;
   }
}
```

## <a name="multisetinsert"></a><a name="insert"></a>multiset:vložení

Vloží prvek nebo rozsah prvků do vícesadé sady.

```cpp
// (1) single element
pair<iterator, bool> insert(
    const value_type& Val);

// (2) single element, perfect forwarded
template <class ValTy>
pair<iterator, bool>
insert(
    ValTy&& Val);

// (3) single element with hint
iterator insert(
    const_iterator Where,
    const value_type& Val);

// (4) single element, perfect forwarded, with hint
template <class ValTy>
iterator insert(
    const_iterator Where,
    ValTy&& Val);

// (5) range
template <class InputIterator>
void insert(
    InputIterator First,
    InputIterator Last);

// (6) initializer list
void insert(
    initializer_list<value_type>
IList);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|-|-|
|*Val*|Hodnota prvku, který má být vložen do multisetu.|
|*Kde*|Místo zahájení vyhledání správného bodu vložení. (Pokud tento bod bezprostředně předchází *Kde*, vložení může dojít v amortizované konstantní čas namísto logaritmického času.)|
|*Valty*|Parametr šablony, který určuje typ argumentu, který může multiset použít k vytvoření prvku [value_type](../standard-library/map-class.md#value_type)a předá *val* jako argument.|
|*První*|Pozice prvního prvku, který chcete zkopírovat.|
|*Poslední*|Pozice bezprostředně za posledním prvkem, který chcete zkopírovat.|
|*Vstupní iterátor*|Argument funkce šablony, který splňuje požadavky [vstupního iterátoru,](../standard-library/input-iterator-tag-struct.md) který odkazuje na prvky typu, který lze použít ke konstrukci [value_type](../standard-library/map-class.md#value_type) objektů.|
|*Ilist*|[Initializer_list,](../standard-library/initializer-list.md) ze kterého chcete zkopírovat prvky.|

### <a name="return-value"></a>Návratová hodnota

Jednoelementové funkce prvku insert, (1) a (2), vrátí iterátor do polohy, kde byl vložen nový prvek do multisetu.

Jednoelementové s nápovědou členské funkce,3) a (4), vrátí iterátor, který odkazuje na pozici, kde byl vložen nový prvek do multiset.

### <a name="remarks"></a>Poznámky

Žádné ukazatele nebo odkazy jsou zrušena touto funkcí, ale může zneplatnit všechny iterátory do kontejneru.

Během vkládání pouze jeden prvek, pokud je vyvolána výjimka, stav kontejneru není změněn. Pokud je při vkládání více prvků vyvolána výjimka, kontejner zůstane v neurčeném, ale platném stavu.

[value_type](../standard-library/map-class.md#value_type) kontejneru je typedef, který patří do kontejneru `multiset<V>::value_type` a `const V`pro sadu je typ .

Členská funkce rozsahu (5) vloží posloupnost hodnot prvků do vícesadé sady, která odpovídá každému `[First, Last)`prvku, kterému iterátor v rozsahu odpovídá ; proto `Last` není vložen. Členská funkce `end()` kontejneru odkazuje na pozici těsně za posledním prvkem v `s.insert(v.begin(), v.end());` kontejneru – `v` `s`například příkaz vloží všechny prvky do .

Inicializační seznam členské funkce (6) používá [initializer_list](../standard-library/initializer-list.md) ke kopírování prvků do multiset.

Pro vložení prvku vytvořeného na místě – to znamená, že nejsou prováděny žádné operace kopírování nebo přesouvání – viz [multiset::emplace](#emplace) a [multiset::emplace_hint](#emplace_hint).

### <a name="example"></a>Příklad

```cpp
// multiset_insert.cpp
// compile with: /EHsc
#include <set>
#include <iostream>
#include <string>
#include <vector>

using namespace std;

template <typename S> void print(const S& s) {
    cout << s.size() << " elements: ";

    for (const auto& p : s) {
        cout << "(" << p << ") ";
    }

    cout << endl;
}

int main()
{

    // insert single values
    multiset<int> s1;
    // call insert(const value_type&) version
    s1.insert({ 1, 10 });
    // call insert(ValTy&&) version
    s1.insert(20);

    cout << "The original multiset values of s1 are:" << endl;
    print(s1);

    // intentionally attempt a duplicate, single element
    s1.insert(1);
    cout << "The modified multiset values of s1 are:" << endl;
    print(s1);
    cout << endl;

    // single element, with hint
    s1.insert(s1.end(), 30);
    cout << "The modified multiset values of s1 are:" << endl;
    print(s1);
    cout << endl;

    // The templatized version inserting a jumbled range
    multiset<int> s2;
    vector<int> v;
    v.push_back(43);
    v.push_back(294);
    v.push_back(41);
    v.push_back(330);
    v.push_back(42);
    v.push_back(45);

    cout << "Inserting the following vector data into s2:" << endl;
    print(v);

    s2.insert(v.begin(), v.end());

    cout << "The modified multiset values of s2 are:" << endl;
    print(s2);
    cout << endl;

    // The templatized versions move-constructing elements
    multiset<string>  s3;
    string str1("blue"), str2("green");

    // single element
    s3.insert(move(str1));
    cout << "After the first move insertion, s3 contains:" << endl;
    print(s3);

    // single element with hint
    s3.insert(s3.end(), move(str2));
    cout << "After the second move insertion, s3 contains:" << endl;
    print(s3);
    cout << endl;

    multiset<int> s4;
    // Insert the elements from an initializer_list
    s4.insert({ 4, 44, 2, 22, 3, 33, 1, 11, 5, 55 });
    cout << "After initializer_list insertion, s4 contains:" << endl;
    print(s4);
    cout << endl;
}
```

## <a name="multisetiterator"></a><a name="iterator"></a>multiset::iterátor

Typ, který poskytuje konstantní [obousměrný iterátor,](../standard-library/bidirectional-iterator-tag-struct.md) který může číst libovolný prvek ve vícesadésadě.

```cpp
typedef implementation-defined iterator;
```

### <a name="example"></a>Příklad

Viz příklad pro [začátek](#begin) příklad, jak deklarovat a používat `iterator`.

## <a name="multisetkey_comp"></a><a name="key_comp"></a>multiset::key_comp

Načte kopii objektu porovnání použitého k objednání klíčů ve vícesadách.

```cpp
key_compare key_comp() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí objekt funkce, který vícesetpoužívá k objednání jeho `Compare`prvků, což je parametr šablony .

Další informace `Compare`o tématu naleznete v části Poznámky v tématu [Vícesetové třídy.](../standard-library/multiset-class.md)

### <a name="remarks"></a>Poznámky

Uložený objekt definuje členovou funkci:

**bool operátor** **(const Key&** *x*, **const Key&** *y);*

který vrátí hodnotu true, pokud *x* v pořadí řazení přísně předchází *y.*

Všimněte si, že [key_compare](#key_compare) i [value_compare](#value_compare) jsou synonyma pro parametr `Compare`šablony . Oba typy jsou k dispozici pro sady tříd a multiset, kde jsou identické, pro kompatibilitu s mapa tříd a multimap, kde jsou odlišné.

### <a name="example"></a>Příklad

```cpp
// multiset_key_comp.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;

   multiset <int, less<int> > ms1;
   multiset <int, less<int> >::key_compare kc1 = ms1.key_comp( ) ;
   bool result1 = kc1( 2, 3 ) ;
   if( result1 == true )
   {
      cout << "kc1( 2,3 ) returns value of true, "
           << "where kc1 is the function object of s1."
           << endl;
   }
   else
   {
      cout << "kc1( 2,3 ) returns value of false "
           << "where kc1 is the function object of ms1."
           << endl;
   }

   multiset <int, greater<int> > ms2;
   multiset <int, greater<int> >::key_compare kc2 = ms2.key_comp( ) ;
   bool result2 = kc2( 2, 3 ) ;
   if( result2 == true )
   {
      cout << "kc2( 2,3 ) returns value of true, "
           << "where kc2 is the function object of ms2."
           << endl;
   }
   else
   {
      cout << "kc2( 2,3 ) returns value of false, "
           << "where kc2 is the function object of ms2."
           << endl;
   }
}
```

```Output
kc1( 2,3 ) returns value of true, where kc1 is the function object of s1.
kc2( 2,3 ) returns value of false, where kc2 is the function object of ms2.
```

## <a name="multisetkey_compare"></a><a name="key_compare"></a>multiset::key_compare

Typ, který poskytuje objekt funkce, který může porovnat dvě klíče řazení k určení relativní pořadí dvou prvků ve vícesad.

```cpp
typedef Compare key_compare;
```

### <a name="remarks"></a>Poznámky

`key_compare`je synonymem pro `Compare`parametr šablony .

Další informace `Compare`o tématu naleznete v části Poznámky v tématu [Vícesetové třídy.](../standard-library/multiset-class.md)

### <a name="example"></a>Příklad

Příklad pro [key_comp](#key_comp) příklad, jak deklarovat a používat `key_compare`.

## <a name="multisetkey_type"></a><a name="key_type"></a>multiset::key_type

Typ, který poskytuje objekt funkce, který může porovnat klíče řazení k určení relativní pořadí dvou prvků ve vícesad.

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>Poznámky

`key_type`je synonymem pro `Key`parametr šablony .

Další informace `Key`o tématu naleznete v části Poznámky v tématu [Vícesetové třídy.](../standard-library/multiset-class.md)

### <a name="example"></a>Příklad

Příklad [value_type](#value_type) naleznete v příkladu, jak `key_type`deklarovat a používat .

## <a name="multisetlower_bound"></a><a name="lower_bound"></a>multiset::lower_bound

Vrátí iterátor prvnímu prvku ve vícesadě s klíčem, který je roven nebo větší než zadaný klíč.

```cpp
const_iterator lower_bound(const Key& key) const;

iterator lower_bound(const Key& key);
```

### <a name="parameters"></a>Parametry

*Klíč*\
Klíč argumentu, který má být porovnán s klíčem řazení prvku z prohledávané multisady.

### <a name="return-value"></a>Návratová hodnota

Nebo `iterator` `const_iterator` který řeší umístění prvku ve vícesadě, který s klíčem, který je roven nebo větší než klíč argumentu, nebo který řeší umístění, které následuje poslední prvek ve vícesadě, pokud pro klíč není nalezena žádná shoda.

### <a name="example"></a>Příklad

```cpp
// multiset_lower_bound.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   multiset <int> ms1;
   multiset <int> :: const_iterator ms1_AcIter, ms1_RcIter;

   ms1.insert( 10 );
   ms1.insert( 20 );
   ms1.insert( 30 );

   ms1_RcIter = ms1.lower_bound( 20 );
   cout << "The element of multiset ms1 with a key of 20 is: "
        << *ms1_RcIter << "." << endl;

   ms1_RcIter = ms1.lower_bound( 40 );

   // If no match is found for the key, end( ) is returned
   if ( ms1_RcIter == ms1.end( ) )
      cout << "The multiset ms1 doesn't have an element "
           << "with a key of 40." << endl;
   else
      cout << "The element of multiset ms1 with a key of 40 is: "
           << *ms1_RcIter << "." << endl;

   // The element at a specific location in the multiset can be
   // found using a dereferenced iterator addressing the location
   ms1_AcIter = ms1.end( );
   ms1_AcIter--;
   ms1_RcIter = ms1.lower_bound( *ms1_AcIter );
   cout << "The element of ms1 with a key matching "
        << "that of the last element is: "
        << *ms1_RcIter << "." << endl;
}
```

```Output
The element of multiset ms1 with a key of 20 is: 20.
The multiset ms1 doesn't have an element with a key of 40.
The element of ms1 with a key matching that of the last element is: 30.
```

## <a name="multisetmax_size"></a><a name="max_size"></a>multiset::max_size

Vrátí maximální délku multisetu.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>Návratová hodnota

Maximální možná délka multiset.

### <a name="example"></a>Příklad

```cpp
// multiset_max_size.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   multiset <int> ms1;
   multiset <int>::size_type i;

   i = ms1.max_size( );
   cout << "The maximum possible length "
        << "of the multiset is " << i << "." << endl;
}
```

## <a name="multisetmultiset"></a><a name="multiset"></a>multiset::vícesetová

Vytvoří multiset, který je prázdný nebo který je kopií celé nebo části některé jiné multiset.

```cpp
multiset();

explicit multiset (
    const Compare& Comp);

multiset (
    const Compare& Comp,
    const Allocator& Al);

multiset(
    const multiset& Right);

multiset(
    multiset&& Right);

multiset(
    initializer_list<Type> IList);

multiset(
    initializer_list<Type> IList,
    const Compare& Comp);

multiset(
    initializer_list<Type> IList,
    const Compare& Comp,
    const Allocator& Al);

template <class InputIterator>
multiset (
    InputIterator First,
    InputIterator Last);

template <class InputIterator>
multiset (
    InputIterator First,
    InputIterator Last,
    const Compare& Comp);

template <class InputIterator>
multiset (
    InputIterator First,
    InputIterator Last,
    const Compare& Comp,
    const Allocator& Al);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|-|-|
|*Al*|Třída alokátoru úložiště, která má být použita pro `Allocator`tento vícemnožinový objekt, který je ve výchozím nastavení .|
|*Comp*|Funkce porovnání typu `const Compare` použitého k seřizování prvků ve `Compare`vícesetové sadě, která je ve výchozím nastavení .|
|*Právo*|Multiset, který je vyrobeno multiset je kopie.|
|*První*|Umístění prvního prvku v rozsahu prvků, které mají být zkopírovány.|
|*Poslední*|Pozice první prvek mimo rozsah prvků, které mají být zkopírovány.|
|*Ilist*|Seznam initializer_list, ze kterého chcete kopírovat prvky.|

### <a name="remarks"></a>Poznámky

Všechny konstruktory uložit typ objektu alokátoru, který spravuje úložiště paměti pro multiset a které mohou být později vráceny voláním [get_allocator](#get_allocator). Parametr allocator je často v deklaraci třídy vynechán a makra předběžného zpracování jsou použita k nahrazení alternativních alokátorů.

Všechny konstruktory inicializovat jejich multiset.

Všechny konstruktory uložit objekt funkce typu Porovnat, který se používá k vytvoření pořadí mezi klíči multiset a které mohou být později vráceny voláním [key_comp](#key_comp).

První tři konstruktory určují prázdnou počáteční multisadu, druhou určující typ funkce porovnání (*Comp),* která má být použita při stanovení pořadí prvků, a třetí explicitně určující typ alokátoru (*Al*), který má být použit. Klíčové slovo **explicitní** potlačí určité druhy automatického převodu typu.

Čtvrtý konstruktor určuje kopii multiset *Right*.

Pátý konstruktor určuje kopii multiset přesunutím *Right*.

Šestý, sedmý a osmý konstruktory určit initializer_list, ze kterého chcete kopírovat prvky.

Další tři konstruktory zkopírují rozsah `[First, Last)` vícesetu s rostoucí explicitní při určování typu funkce porovnání a přidělování.

### <a name="example"></a>Příklad

```cpp
// multiset_ctor.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main()
{
    using namespace std;
    //multiset <int>::iterator ms1_Iter, ms2_Iter, ms3_Iter;
    multiset <int>::iterator ms4_Iter, ms5_Iter, ms6_Iter, ms7_Iter;

    // Create an empty multiset ms0 of key type integer
    multiset <int> ms0;

    // Create an empty multiset ms1 with the key comparison
    // function of less than, then insert 4 elements
    multiset <int, less<int> > ms1;
    ms1.insert(10);
    ms1.insert(20);
    ms1.insert(20);
    ms1.insert(40);

    // Create an empty multiset ms2 with the key comparison
    // function of greater than, then insert 2 elements
    multiset <int, less<int> > ms2;
    ms2.insert(10);
    ms2.insert(20);

    // Create a multiset ms3 with the
    // allocator of multiset ms1
    multiset <int>::allocator_type ms1_Alloc;
    ms1_Alloc = ms1.get_allocator();
    multiset <int> ms3(less<int>(), ms1_Alloc);
    ms3.insert(30);

    // Create a copy, multiset ms4, of multiset ms1
    multiset <int> ms4(ms1);

    // Create a multiset ms5 by copying the range ms1[ first,  last)
    multiset <int>::const_iterator ms1_bcIter, ms1_ecIter;
    ms1_bcIter = ms1.begin();
    ms1_ecIter = ms1.begin();
    ms1_ecIter++;
    ms1_ecIter++;
    multiset <int> ms5(ms1_bcIter, ms1_ecIter);

    // Create a multiset ms6 by copying the range ms4[ first,  last)
    // and with the allocator of multiset ms2
    multiset <int>::allocator_type ms2_Alloc;
    ms2_Alloc = ms2.get_allocator();
    multiset <int> ms6(ms4.begin(), ++ms4.begin(), less<int>(), ms2_Alloc);

    cout << "ms1 =";
    for (auto i : ms1)
        cout << " " << i;
    cout << endl;

    cout << "ms2 =";
    for (auto i : ms2)
        cout << " " << i;
   cout << endl;

   cout << "ms3 =";
   for (auto i : ms3)
       cout << " " << i;
    cout << endl;

    cout << "ms4 =";
    for (auto i : ms4)
        cout << " " << i;
    cout << endl;

    cout << "ms5 =";
    for (auto i : ms5)
        cout << " " << i;
    cout << endl;

    cout << "ms6 =";
    for (auto i : ms6)
        cout << " " << i;
    cout << endl;

    // Create a multiset by moving ms5
    multiset<int> ms7(move(ms5));
    cout << "ms7 =";
    for (auto i : ms7)
        cout << " " << i;
    cout << endl;

    // Create a multiset with an initializer_list
    multiset<int> ms8({1, 2, 3, 4});
    cout << "ms8=";
    for (auto i : ms8)
        cout << " " << i;
    cout << endl;
}
```

## <a name="multisetoperator"></a><a name="op_eq"></a>multiset::operátor=

Nahradí prvky tohoto `multiset` pomocí prvků `multiset`z jiného .

```cpp
multiset& operator=(const multiset& right);

multiset& operator=(multiset&& right);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|-|-|
|*Právo*|Ze `multiset` kterého jsou prvky zkopírovány nebo přesunuty.|

### <a name="remarks"></a>Poznámky

`operator=`zkopíruje nebo přesune *right* prvky `multiset`v pravo do tohoto , v závislosti na typu odkazu (lvalue nebo rvalue) použité. Prvky, které `multiset` `operator=` jsou v tomto před spuštění jsou zahozeny.

### <a name="example"></a>Příklad

```cpp
// multiset_operator_as.cpp
// compile with: /EHsc
#include <multiset>
#include <iostream>

int main( )
   {
   using namespace std;
   multiset<int> v1, v2, v3;
   multiset<int>::iterator iter;

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

## <a name="multisetpointer"></a><a name="pointer"></a>multiset::pointer

Typ, který poskytuje ukazatel na prvek ve vícesadí.

```cpp
typedef typename allocator_type::pointer pointer;
```

### <a name="remarks"></a>Poznámky

**Ukazatel** typu lze změnit hodnotu prvku.

Ve většině případů [iterátor](#iterator) by měl být použit pro přístup k prvkům v objektu více sad.

## <a name="multisetrbegin"></a><a name="rbegin"></a>multiset::začátek

Vrátí iterátor adresující první prvek v obrácené multisadě.

```cpp
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```

### <a name="return-value"></a>Návratová hodnota

Reverzní obousměrný itener adresování první prvek v obrácené multiset nebo adresování co byl poslední prvek v unreverse multiset.

### <a name="remarks"></a>Poznámky

`rbegin`se používá s obráceným multiset stejně jako rbegin se používá s multiset.

Pokud `rbegin` je vrácená hodnota `const_reverse_iterator`přiřazena aplikaci , nelze objekt s více sadami změnit. Pokud `rbegin` je vrácená hodnota `reverse_iterator`přiřazena k , lze změnit objekt s více sadami.

`rbegin`lze použít k iterátu přes multiset dozadu.

### <a name="example"></a>Příklad

```cpp
// multiset_rbegin.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   multiset <int> ms1;
   multiset <int>::iterator ms1_Iter;
   multiset <int>::reverse_iterator ms1_rIter;

   ms1.insert( 10 );
   ms1.insert( 20 );
   ms1.insert( 30 );

   ms1_rIter = ms1.rbegin( );
   cout << "The first element in the reversed multiset is "
        << *ms1_rIter << "." << endl;

   // begin can be used to start an iteration
   // through a multiset in a forward order
   cout << "The multiset is:";
   for ( ms1_Iter = ms1.begin( ) ; ms1_Iter != ms1.end( ); ms1_Iter++ )
      cout << " " << *ms1_Iter;
   cout << endl;

   // rbegin can be used to start an iteration
   // through a multiset in a reverse order
   cout << "The reversed multiset is:";
   for ( ms1_rIter = ms1.rbegin( ) ; ms1_rIter != ms1.rend( ); ms1_rIter++ )
      cout << " " << *ms1_rIter;
   cout << endl;

   // A multiset element can be erased by dereferencing to its key
   ms1_rIter = ms1.rbegin( );
   ms1.erase ( *ms1_rIter );

   ms1_rIter = ms1.rbegin( );
   cout << "After the erasure, the first element "
        << "in the reversed multiset is "<< *ms1_rIter << "."
        << endl;
}
```

```Output
The first element in the reversed multiset is 30.
The multiset is: 10 20 30
The reversed multiset is: 30 20 10
After the erasure, the first element in the reversed multiset is 20.
```

## <a name="multisetreference"></a><a name="reference"></a>multiset::odkaz

Typ, který poskytuje odkaz na prvek uložený ve vícesadí.

```cpp
typedef typename allocator_type::reference reference;
```

### <a name="example"></a>Příklad

```cpp
// multiset_ref.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   multiset <int> ms1;

   ms1.insert( 10 );
   ms1.insert( 20 );

   // Declare and initialize a reference &Ref1 to the 1st element
   const int &Ref1 = *ms1.begin( );

   cout << "The first element in the multiset is "
        << Ref1 << "." << endl;
}
```

```Output
The first element in the multiset is 10.
```

## <a name="multisetrend"></a><a name="rend"></a>multiset::rend

Vrátí iterátor, který řeší umístění, které následuje poslední prvek v obrácené multisadě.

```cpp
const_reverse_iterator rend() const;

reverse_iterator rend();
```

### <a name="return-value"></a>Návratová hodnota

Reverzní obousměrný itestrátor, který řeší umístění, které následuje poslední prvek v obrácené multisadě (umístění, které předcházelo prvnímu prvku v neobrácené multisadě).

### <a name="remarks"></a>Poznámky

`rend`se používá s obrácenou multisad stejně jako [konec](#end) se používá s multiset.

Pokud `rend` je vrácená hodnota `const_reverse_iterator`přiřazena aplikaci , nelze objekt s více sadami změnit. Pokud `rend` je vrácená hodnota `reverse_iterator`přiřazena k , lze změnit objekt s více sadami.

`rend`lze použít k testování, zda reverzní iterátor dosáhl konce svého multiset.

Hodnota vrácená `rend` by neměla být odkazována.

### <a name="example"></a>Příklad

```cpp
// multiset_rend.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main() {
   using namespace std;
   multiset <int> ms1;
   multiset <int>::iterator ms1_Iter;
   multiset <int>::reverse_iterator ms1_rIter;
   multiset <int>::const_reverse_iterator ms1_crIter;

   ms1.insert( 10 );
   ms1.insert( 20 );
   ms1.insert( 30 );

   ms1_rIter = ms1.rend( ) ;
   ms1_rIter--;
   cout << "The last element in the reversed multiset is "
        << *ms1_rIter << "." << endl;

   // end can be used to terminate an iteration
   // through a multiset in a forward order
   cout << "The multiset is: ";
   for ( ms1_Iter = ms1.begin( ) ; ms1_Iter != ms1.end( ); ms1_Iter++ )
      cout << *ms1_Iter << " ";
   cout << "." << endl;

   // rend can be used to terminate an iteration
   // through a multiset in a reverse order
   cout << "The reversed multiset is: ";
   for ( ms1_rIter = ms1.rbegin( ) ; ms1_rIter != ms1.rend( ); ms1_rIter++ )
      cout << *ms1_rIter << " ";
   cout << "." << endl;

   ms1_rIter = ms1.rend( );
   ms1_rIter--;
   ms1.erase ( *ms1_rIter );

   ms1_rIter = ms1.rend( );
   --ms1_rIter;
   cout << "After the erasure, the last element in the "
        << "reversed multiset is " << *ms1_rIter << "." << endl;
}
```

## <a name="multisetreverse_iterator"></a><a name="reverse_iterator"></a>multiset::reverse_iterator

Typ, který poskytuje obousměrný iterátor, který může číst nebo upravovat prvek v obrácené multiset.

```cpp
typedef std::reverse_iterator<iterator> reverse_iterator;
```

### <a name="remarks"></a>Poznámky

Typ `reverse_iterator` se používá k iterátu prostřednictvím multiset v opačném směru.

### <a name="example"></a>Příklad

Příklad pro [rbegin](#rbegin) pro příklad, jak `reverse_iterator`deklarovat a používat .

## <a name="multisetsize"></a><a name="size"></a>multiset::velikost

Vrátí počet prvků ve vícesadě.

```cpp
size_type size() const;
```

### <a name="return-value"></a>Návratová hodnota

Aktuální délka multiset.

### <a name="example"></a>Příklad

```cpp
// multiset_size.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   multiset <int> ms1;
   multiset <int> :: size_type i;

   ms1.insert( 1 );
   i = ms1.size( );
   cout << "The multiset length is " << i << "." << endl;

   ms1.insert( 2 );
   i = ms1.size( );
   cout << "The multiset length is now " << i << "." << endl;
}
```

```Output
The multiset length is 1.
The multiset length is now 2.
```

## <a name="multisetsize_type"></a><a name="size_type"></a>multiset::size_type

Nepodepsaný podnosný typ, který může představovat počet prvků ve vícesadách.

```cpp
typedef typename allocator_type::size_type size_type;
```

### <a name="example"></a>Příklad

Příklad [velikosti](#size) naleznete v příkladu, jak deklarovat a používat`size_type`

## <a name="multisetswap"></a><a name="swap"></a>multiset::prohození

Vyměňuje prvky dvou multisetů.

```cpp
void swap(
    multiset<Key, Compare, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*Právo*\
Vícesetargument poskytující prvky, které mají být vyměněny s cílovou multisad.

### <a name="remarks"></a>Poznámky

Členská funkce zruší platnost žádné odkazy, ukazatele nebo iterátory, které označují prvky ve dvou multisetech, jejichž prvky jsou vyměňovány.

### <a name="example"></a>Příklad

```cpp
// multiset_swap.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   multiset <int> ms1, ms2, ms3;
   multiset <int>::iterator ms1_Iter;

   ms1.insert( 10 );
   ms1.insert( 20 );
   ms1.insert( 30 );
   ms2.insert( 100 );
   ms2.insert( 200 );
   ms3.insert( 300 );

   cout << "The original multiset ms1 is:";
   for ( ms1_Iter = ms1.begin( ); ms1_Iter != ms1.end( ); ms1_Iter++ )
      cout << " " << *ms1_Iter;
   cout << "." << endl;

   // This is the member function version of swap
   ms1.swap( ms2 );

   cout << "After swapping with ms2, list ms1 is:";
   for ( ms1_Iter = ms1.begin( ); ms1_Iter != ms1.end( ); ms1_Iter++ )
      cout << " " << *ms1_Iter;
   cout << "." << endl;

   // This is the specialized template version of swap
   swap( ms1, ms3 );

   cout << "After swapping with ms3, list ms1 is:";
   for ( ms1_Iter = ms1.begin( ); ms1_Iter != ms1.end( ); ms1_Iter++ )
      cout << " " << *ms1_Iter;
   cout   << "." << endl;
}
```

```Output
The original multiset ms1 is: 10 20 30.
After swapping with ms2, list ms1 is: 100 200.
After swapping with ms3, list ms1 is: 300.
```

## <a name="multisetupper_bound"></a><a name="upper_bound"></a>multiset::upper_bound

Vrátí iterátor prvnímu prvku ve vícesadě s klíčem, který je větší než zadaný klíč.

```cpp
const_iterator upper_bound(const Key& key) const;

iterator upper_bound(const Key& key);
```

### <a name="parameters"></a>Parametry

*Klíč*\
Klíč argumentu, který má být porovnán s klíčem řazení prvku z prohledávané multisady.

### <a name="return-value"></a>Návratová hodnota

**Iterátor** nebo `const_iterator` který řeší umístění prvku ve vícesadé sadě s klíčem, který je větší než klíč argumentu nebo který řeší umístění, které následuje poslední prvek ve vícesadě, pokud pro klíč není nalezena žádná shoda.

### <a name="example"></a>Příklad

```cpp
// multiset_upper_bound.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   multiset <int> ms1;
   multiset <int> :: const_iterator ms1_AcIter, ms1_RcIter;

   ms1.insert( 10 );
   ms1.insert( 20 );
   ms1.insert( 30 );

   ms1_RcIter = ms1.upper_bound( 20 );
   cout << "The first element of multiset ms1 with a key greater "
           << "than 20 is: " << *ms1_RcIter << "." << endl;

   ms1_RcIter = ms1.upper_bound( 30 );

   // If no match is found for the key, end( ) is returned
   if ( ms1_RcIter == ms1.end( ) )
      cout << "The multiset ms1 doesn't have an element "
              << "with a key greater than 30." << endl;
   else
      cout << "The element of multiset ms1 with a key > 40 is: "
           << *ms1_RcIter << "." << endl;

   // The element at a specific location in the multiset can be
   // found using a dereferenced iterator addressing the location
   ms1_AcIter = ms1.begin( );
   ms1_RcIter = ms1.upper_bound( *ms1_AcIter );
   cout << "The first element of ms1 with a key greater than"
        << endl << "that of the initial element of ms1 is: "
        << *ms1_RcIter << "." << endl;
}
```

```Output
The first element of multiset ms1 with a key greater than 20 is: 30.
The multiset ms1 doesn't have an element with a key greater than 30.
The first element of ms1 with a key greater than
that of the initial element of ms1 is: 20.
```

## <a name="multisetvalue_comp"></a><a name="value_comp"></a>multiset::value_comp

Načte kopii objektu porovnání použitého k pořadí hodnot prvků ve vícesadí.

```cpp
value_compare value_comp() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí objekt funkce, který vícesetpoužívá k objednání jeho `Compare`prvků, což je parametr šablony .

Další informace `Compare`o tématu naleznete v části Poznámky v tématu [Vícesetové třídy.](../standard-library/multiset-class.md)

### <a name="remarks"></a>Poznámky

Uložený objekt definuje členovou funkci:

**bool operátor** **(const Key&** `_xVal`, **const Key&); ** `_yVal`

který vrátí `_xVal` hodnotu true, pokud `_yVal` předchází, a není rovna v pořadí řazení.

Všimněte si, že [key_compare](#key_compare) i [value_compare](#value_compare) jsou synonyma pro parametr `Compare`šablony . Oba typy jsou k dispozici pro sady tříd a multiset, kde jsou identické, pro kompatibilitu s mapa tříd a multimap, kde jsou odlišné.

### <a name="example"></a>Příklad

```cpp
// multiset_value_comp.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;

   multiset <int, less<int> > ms1;
   multiset <int, less<int> >::value_compare vc1 = ms1.value_comp( );
   bool result1 = vc1( 2, 3 );
   if( result1 == true )
   {
      cout << "vc1( 2,3 ) returns value of true, "
           << "where vc1 is the function object of ms1."
           << endl;
   }
   else
   {
      cout << "vc1( 2,3 ) returns value of false, "
           << "where vc1 is the function object of ms1."
           << endl;
   }

   set <int, greater<int> > ms2;
   set<int, greater<int> >::value_compare vc2 = ms2.value_comp( );
   bool result2 = vc2( 2, 3 );
   if( result2 == true )
   {
      cout << "vc2( 2,3 ) returns value of true, "
           << "where vc2 is the function object of ms2."
           << endl;
   }
   else
   {
      cout << "vc2( 2,3 ) returns value of false, "
           << "where vc2 is the function object of ms2."
           << endl;
   }
}
```

```Output
vc1( 2,3 ) returns value of true, where vc1 is the function object of ms1.
vc2( 2,3 ) returns value of false, where vc2 is the function object of ms2.
```

## <a name="multisetvalue_compare"></a><a name="value_compare"></a>multiset::value_compare

Typ, který poskytuje objekt funkce, který může porovnat dva klíče řazení k určení jejich relativní pořadí ve vícesad.

```cpp
typedef key_compare value_compare;
```

### <a name="remarks"></a>Poznámky

`value_compare`je synonymem pro `Compare`parametr šablony .

Všimněte si, že [oba key_compare](#key_compare) a `value_compare` jsou synonyma pro parametr `Compare`šablony . Oba typy jsou k dispozici pro sady tříd a multiset, kde jsou identické, pro kompatibilitu s mapa tříd a multimap, kde jsou odlišné.

Další informace `Compare`o tématu naleznete v části Poznámky v tématu [Vícesetové třídy.](../standard-library/multiset-class.md)

### <a name="example"></a>Příklad

Příklad pro [value_comp](#value_comp) příklad, jak deklarovat a používat `value_compare`.

## <a name="multisetvalue_type"></a><a name="value_type"></a>multiset::value_type

Typ, který popisuje objekt uložený jako prvek jako multiset v jeho kapacitě jako hodnotu.

```cpp
typedef Key value_type;
```

### <a name="remarks"></a>Poznámky

`value_type`je synonymem pro `Key`parametr šablony .

Všimněte si, že [oba key_type](#key_type) a `value_type` jsou synonyma pro parametr `Key`šablony . Oba typy jsou k dispozici pro sady tříd a multiset, kde jsou identické, pro kompatibilitu s mapa tříd a multimap, kde jsou odlišné.

Další informace `Key`naleznete v části Poznámky v tématu.

### <a name="example"></a>Příklad

```cpp
// multiset_value_type.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   multiset <int> ms1;
   multiset <int>::iterator ms1_Iter;

   multiset <int> :: value_type svt_Int;   // Declare value_type
   svt_Int = 10;             // Initialize value_type

   multiset <int> :: key_type skt_Int;   // Declare key_type
   skt_Int = 20;             // Initialize key_type

   ms1.insert( svt_Int );         // Insert value into s1
   ms1.insert( skt_Int );         // Insert key into s1

   // A multiset accepts key_types or value_types as elements
   cout << "The multiset has elements:";
   for ( ms1_Iter = ms1.begin( ) ; ms1_Iter != ms1.end( ); ms1_Iter++ )
      cout << " " << *ms1_Iter;
   cout << "." << endl;
}
```

```Output
The multiset has elements: 10 20.
```

## <a name="see-also"></a>Viz také

[Kontejnery](../cpp/containers-modern-cpp.md)\
[Bezpečnost vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Referenční příručka standardní knihovny jazyka C++](../standard-library/cpp-standard-library-reference.md)
