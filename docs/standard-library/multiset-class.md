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
ms.openlocfilehash: 3b059db877d24f5e4414745ba6c2f9ee4f6591e7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62205083"
---
# <a name="multiset-class"></a>multiset – třída

Standardní knihovny C++ multiset – třída se používá pro ukládání a načítání dat z kolekce, ve kterém hodnoty elementů obsažených nemusí být jedinečný a ve které slouží jako klíčové hodnoty, podle kterých jsou data automaticky uspořádávána. Hodnotu klíče prvku v multisadě nelze změnit přímo. Místo toho musíte odstranit staré hodnoty a vložit prvky s novými hodnotami.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Key, class Compare =less <Key>, class Allocator =allocator <Key>>
class multiset
```

### <a name="parameters"></a>Parametry

*Key*<br/>
Typ dat prvku, který bude uložen do multisady.

*Compare*<br/>
Typ poskytující objekt funkce, který může porovnat dvě hodnoty prvků pro určení jejich relativního pořadí v multisadě. Binární predikát **méně**\<Key > je výchozí hodnota.

V C ++ 14 můžete povolit heterogenní vyhledávání tak, že zadáte `std::less<>` nebo `std::greater<>` predikát, který nemá žádné parametry typu. Další informace najdete v tématu [heterogenní vyhledávání v asociativních kontejnerech](../standard-library/stl-containers.md#sequence_containers)

*Allocator –*<br/>
Typ představující uložený objekt alokátoru, který zapouzdřuje informace o přidělování a navrácení paměti zpět multisady. Výchozí hodnota je `allocator<Key>`.

## <a name="remarks"></a>Poznámky

Standardní knihovny C++, které je multiset – třída:

- Asociativní kontejner, což je kontejner proměnné velikosti, který podporuje efektivní načtení hodnoty prvku založené na přiřazené hodnotě klíče.

- Oboustranný, protože poskytuje obousměrné iterátory pro přístup k jeho prvkům.

- Seřazený, protože jeho prvky jsou řazeny podle hodnot klíče v kontejneru podle zadané porovnávací funkce.

- Vícenásobný v tom smyslu, že jeho prvky nemusí mít jedinečné klíče, takže jedna hodnota klíče může mít k sobě přidružených mnoho hodnot prvků.

- Jednoduchý asociativní kontejner, protože jeho hodnoty prvku jsou jeho hodnoty klíče.

- Třída šablony, protože poskytuje obecné funkce a to nezávisle na určitém typu dat obsažených jako prvky. Datový typ, který má být použit, je místo toho zadán jako parametr v šabloně třídy společně s funkcí porovnání a alokátorem.

Iterátor poskytovaný třídou multiset je obousměrný iterátor, ale členské funkce třídy [vložit](#insert) a [multiset](#multiset) mají verze, které jako parametry šablony berou slabší vstupní iterátor, jehož požadavky na funkce jsou minimálnější než ty zaručeny třídou obousměrných iterátorů. Různé koncepty iterátorů tvoří rodinu týkající se upřesnění jejich funkčnosti. Každý koncept iterátoru má vlastní sadu požadavků a algoritmy, které s nimi pracují, musí omezit jejich předpoklady na požadavky podle typu iterátoru. Lze předpokládat, že ke vstupnímu iterátoru lze přistoupit přes ukazatel pro odkazování na některý objekt a že může být zvýšen na další iterátor v pořadí. Toto je minimální sada funkcí, ale je dostatečná pro srozumitelnou komunikaci o rozsahu u iterátorů [ `First`, `Last`) v rámci členských funkcí třídy.

Volba typu kontejneru by měla obecně vycházet z typu vyhledávání a vkládání vyžadovaného aplikací. Asociativní kontejnery jsou optimalizovány pro operace vyhledávání, vkládání a odstranění. Členské funkce, které explicitně podporují tyto operace, jsou efektivní a jsou prováděny v čase, který je průměrně úměrný logaritmu počtu prvků v kontejneru. Vkládání prvků nezruší platnost žádných iterátorů a odstranění prvků zruší platnost pouze těch iterátorů, které výslovně odkazovaly na odstraněné prvky.

Objekt multisady (multiset) by měl být asociativní kontejner dle výběru, kdy jsou podmínky přiřazení hodnot k jejich klíčům splněny aplikací. Prvků multisady může být více a slouží jako vlastní klíče řazení, takže klíče nejsou jedinečné. Model pro tento typ struktury je uspořádaný seznam slov, v němž se slova mohou vyskytovat více než jednou. Pokud by nebylo povoleno více výskytů jednoho slova, byl by objekt set odpovídající strukturou kontejneru. Pokud byly k seznamu jedinečných klíčových slov připojeny jedinečné definice jako hodnoty, objekt map by byl vhodnou strukturou, který by měla tato data obsahovat. Pokud by však definice nebyly jedinečné, byl by zvoleným kontejnerem multimap.

Třída multiset seřadí sekvence pomocí volání uloženého objektu funkce typu *porovnání*. Tento uložený objekt je funkce porovnání, která může získat přístup k voláním členské funkce [key_comp](#key_comp). Obecně, tyto prvky musí být menší než srovnatelné pro toto pořadí, což znamená, že když jsou uvedeny dva prvky, může být stanoveno, zda jsou ekvivalentní (v tom smyslu, že ani jeden není menší než ten druhý), nebo že jeden je menší než druhý. To má za výsledek řazení mezi neekvivalentními prvky. Technicky je funkce porovnání binárním predikátem, který indukuje přísné slabé řazení, standardním matematickým způsobem. Binární predikát *f*( *x*, *y*) je objekt funkce, který má dva objekty argumentu *x* a *y* a vrácená hodnota **true** nebo **false**. Na sadě je přísné slabé seřazení, pokud je binární predikát Nereflexivní, antisymetrický a tranzitivní a je-li ekvivalence tranzitivní, kde dva objekty x a y definovány jako ekvivalentní, když oba *f*( *x, y*) a *f*( *y, x*) jsou false. Pokud silnější podmínka rovnosti mezi klíči nahradí ekvivalenci, stane se pořadí celkovým (v tom smyslu, že všechny prvky jsou uspořádány ve vztahu k sobě navzájem) a odpovídající klíče budou od sebe nerozeznatelné.

V C ++ 14 můžete povolit heterogenní vyhledávání tak, že zadáte `std::less<>` nebo `std::greater<>` predikát, který nemá žádné parametry typu. Další informace najdete v tématu [heterogenní vyhledávání v asociativních kontejnerech](../standard-library/stl-containers.md#sequence_containers)

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[multiset](#multiset)|Vytvoří `multiset` , který je prázdný nebo, který je kopií celého nebo části zadaného `multiset`.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[allocator_type](#allocator_type)|Definice typu `allocator` třídy pro `multiset` objektu.|
|[const_iterator](#const_iterator)|Definice typu pro obousměrný iterátor, který může číst **const** prvek `multiset`.|
|[const_pointer](#const_pointer)|Typedef pro ukazatel **const** element v `multiset`.|
|[const_reference](#const_reference)|Definice typu odkazu na **const** element uložené v `multiset` pro čtení a provádění **const** operace.|
|[const_reverse_iterator](#const_reverse_iterator)|Definice typu pro obousměrný iterátor, který může číst jakýkoli **const** prvek `multiset`.|
|[difference_type](#difference_type)|Definice typu celé číslo se znaménkem pro počet prvků objektu `multiset` v rozsahu mezi prvky, na které odkazují iterátory.|
|[iterator](#iterator)|Definice typu pro obousměrný iterátor, který může číst nebo upravovat libovolný prvek v `multiset`.|
|[key_compare](#key_compare)|Definice typu poskytující objekt funkce, který může porovnat dva klíče pro určení relativního pořadí dvou prvků v `multiset`.|
|[key_type](#key_type)|Definice typu poskytující objekt funkce, který může porovnat dva klíče řazení pro určení relativního pořadí dvou prvků v `multiset`.|
|[pointer](#pointer)|Typedef pro ukazatel na prvek v `multiset`.|
|[Referenční dokumentace](#reference)|Definice typu odkazu na prvek uložený v `multiset`.|
|[reverse_iterator](#reverse_iterator)|Definice typu pro obousměrný iterátor, který může číst nebo upravovat prvek v obráceném objektu `multiset`.|
|[size_type](#size_type)|Typ celé číslo bez znaménka představující počet prvků v `multiset`.|
|[value_compare](#value_compare)|Definice typu poskytující objekt funkce, který může porovnat dva prvky jako klíče řazení pro určení jejich relativního pořadí v `multiset`.|
|[value_type](#value_type)|Definice typu popisuje objekt uložený jako prvek sady jako `multiset` v jeho kapacitě jako hodnotu.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[začít](#begin)|Vrátí iterátor odkazující na první prvek `multiset`.|
|[cbegin](#cbegin)|Vrátí konstantní iterátor adresující první prvek `multiset`.|
|[cend](#cend)|Vrátí konstantní iterátor adresující umístění následující po posledním prvku v `multiset`.|
|[clear](#clear)|Vymaže všechny prvky `multiset`.|
|[Počet](#count)|Vrátí počet prvků v `multiset` jejichž klíč odpovídá klíči zadanému jako parametr.|
|[crbegin](#crbegin)|Vrátí konstantní iterátor adresující první prvek v obráceném objektu set.|
|[crend](#crend)|Vrátí konstantní iterátor adresující umístění následující po posledním prvku v obráceném objektu set.|
|[emplace](#emplace)|Vloží vytvořený prvek na místo do `multiset`.|
|[emplace_hint](#emplace_hint)|Vloží vytvořený prvek na místo do `multiset`, s náznakem umístění.|
|[prázdný](#empty)|Testuje, zda `multiset` je prázdný.|
|[ukončení](#end)|Vrátí iterátor odkazující na umístění za posledním prvkem v `multiset`.|
|[equal_range](#equal_range)|Vrátí pár iterátorů. První iterátor v páru odkazuje na první prvek v `multiset` s klíčem, který je větší než zadaný klíč. Druhý iterátor v páru odkazuje na první prvek `multiset` s klíčem, který je roven nebo větší než tento klíč.|
|[vymazání](#erase)|Odebere prvek nebo rozsah prvků `multiset` od zadané pozice nebo odebere prvky, které odpovídají zadanému klíči.|
|[Najít](#find)|Vrátí iterátor odkazující na první umístění prvku v `multiset` , který má klíč stejný jako zadaný klíč.|
|[get_allocator](#get_allocator)|Vrátí kopii objektu `allocator` objekt, který se používá ke konstrukci `multiset`.|
|[Vložit](#insert)|Vloží prvek nebo rozsah prvků do `multiset`.|
|[key_comp](#key_comp)|Poskytuje objekt funkce, který může porovnat dva klíče řazení pro určení relativního pořadí dvou prvků v `multiset`.|
|[lower_bound –](#lower_bound)|Vrátí iterátor na první prvek v `multiset` s klíčem, který je roven nebo větší než zadaný klíč.|
|[max_size](#max_size)|Vrátí maximální délku objektu `multiset`.|
|[rbegin](#rbegin)|Vrátí iterátor odkazující na první prvek v obráceném objektu `multiset`.|
|[rend –](#rend)|Vrátí iterátor odkazující na umístění následující po posledním prvku v obráceném objektu `multiset`.|
|[Velikost](#size)|Vrátí počet prvků v `multiset`.|
|[swap](#swap)|Vymění prvky dvou `multiset`s.|
|[upper_bound](#upper_bound)|Vrátí iterátor na první prvek v `multiset` s klíčem, který je větší než zadaný klíč.|
|[value_comp](#value_comp)|Načte kopii objektu porovnání použitého pro seřazení hodnot prvků `multiset`.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operátor =](#op_eq)|Nahradí prvky objektu `multiset` s kopií jiného `multiset`.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<nastavit >

**Namespace:** std

## <a name="allocator_type"></a>  multiset::allocator_type

Typ, který představuje třídu alokátoru pro objekt multiset –

```cpp
typedef Allocator allocator_type;
```

### <a name="remarks"></a>Poznámky

`allocator_type` je synonymum pro parametr šablony `Allocator`.

Další informace o `Allocator`, najdete v části poznámky [multiset – třída](../standard-library/multiset-class.md) tématu.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [get_allocator](#get_allocator) příklad použití `allocator_type`

## <a name="begin"></a>  multiset::begin

Vrátí iterátor adresující první prvek v multisadě.

```cpp
const_iterator begin() const;

iterator begin();
```

### <a name="return-value"></a>Návratová hodnota

Obousměrný iterátor adresující první prvek v multisadě nebo umístění následující po prázdnou multimnožinu.

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

## <a name="cbegin"></a>  multiset::cbegin

Vrátí **const** iterátor adresující první prvek v rozsahu.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>Návratová hodnota

A **const** iterátor s obousměrným přístupem, který ukazuje na první prvek rozsahu nebo na umístění hned za koncem prázdného rozsahu (pro prázdný rozsah `cbegin() == cend()`).

### <a name="remarks"></a>Poznámky

S návratovou hodnotou `cbegin`, nejde upravit prvky v rozsahu.

Můžete použít tuto členskou funkci místo `begin()` členskou funkci pro zajištění, že návratová hodnota je `const_iterator`. Obvykle se používá ve spojení s [automaticky](../cpp/auto-cpp.md) zadejte klíčovým slovem odvození, jak je znázorněno v následujícím příkladu. V tomto příkladu zvažte `Container` jako upravitelný (jinou hodnotu než **const**) kontejner jakéhokoli druhu, který podporuje `begin()` a `cbegin()`.

```cpp
auto i1 = Container.begin();
// i1 is Container<T>::iterator
auto i2 = Container.cbegin();

// i2 is Container<T>::const_iterator
```

## <a name="cend"></a>  multiset::cend

Vrátí **const** iterátor adresující umístění hned za posledním prvkem v rozsahu.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>Návratová hodnota

A **const** iterátor s obousměrným přístupem, který ukazuje přesně za konec rozsahu.

### <a name="remarks"></a>Poznámky

`cend` slouží k otestování, zda iterátor prošel konec rozsahu.

Můžete použít tuto členskou funkci místo `end()` členskou funkci pro zajištění, že návratová hodnota je `const_iterator`. Obvykle se používá ve spojení s [automaticky](../cpp/auto-cpp.md) zadejte klíčovým slovem odvození, jak je znázorněno v následujícím příkladu. V tomto příkladu zvažte `Container` jako upravitelný (jinou hodnotu než **const**) kontejner jakéhokoli druhu, který podporuje `end()` a `cend()`.

```cpp
auto i1 = Container.end();
// i1 is Container<T>::iterator
auto i2 = Container.cend();

// i2 is Container<T>::const_iterator
```

Hodnota vrácená `cend` by neměla být dereferencována.

## <a name="clear"></a>  multiset::clear

Vymaže všechny prvky použita třída multiset.

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

## <a name="const_iterator"></a>  multiset::const_iterator

Typ, který poskytuje obousměrný iterátor, který může číst **const** prvku v multisadě.

```cpp
typedef implementation-defined const_iterator;
```

### <a name="remarks"></a>Poznámky

Typ `const_iterator` nelze použít ke změně hodnoty prvku.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [začít](#begin) příklad použití `const_iterator`.

## <a name="const_pointer"></a>  multiset::const_pointer

Typ, který poskytuje ukazatel **const** prvku v multisadě.

```cpp
typedef typename allocator_type::const_pointer const_pointer;
```

### <a name="remarks"></a>Poznámky

Typ `const_pointer` nelze použít ke změně hodnoty prvku.

Ve většině případů [iterátoru](#iterator) by měla sloužit pro přístup k prvkům v multiset – objektu.

## <a name="const_reference"></a>  multiset::const_reference

Typ, který poskytuje odkaz na **const** prvek uložený v multisadě pro čtení a provádění **const** operace.

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

## <a name="const_reverse_iterator"></a>  multiset::const_reverse_iterator

Typ, který poskytuje obousměrný iterátor, který může přečíst jakýkoli **const** prvku v multisadě.

```cpp
typedef std::reverse_iterator<const_iterator> const_reverse_iterator;
```

### <a name="remarks"></a>Poznámky

Typ `const_reverse_iterator` hodnotu prvku nelze změnit a použít k iteraci v rámci multiset v opačném pořadí.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [rend](#rend) příklad toho, jak deklarovat a použít `const_reverse_iterator`.

## <a name="count"></a>  multiset::Count

Vrátí počet prvků v multisadě, jejichž klíč odpovídá klíči se zadaným parametrem.

```cpp
size_type count(const Key& key) const;
```

### <a name="parameters"></a>Parametry

*key*<br/>
Klíč prvky lze porovnat z multisady.

### <a name="return-value"></a>Návratová hodnota

Počet prvků v multisadě, jejichž řazení klíč odpovídá klíči parametru.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí počet prvků, které *x* v rozsahu

\[ lower_bound (*klíč*), upper_bound (*klíč*))

### <a name="example"></a>Příklad

Následující příklad ukazuje použití multiset::count členskou funkci.

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

## <a name="crbegin"></a>  multiset::crbegin

Vrátí konstantní iterátor adresující první prvek v obráceném objektu multiset.

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>Návratová hodnota

Konstantní reverzní obousměrný iterátor adresující první prvek v obráceném objektu multiset nebo adresování, co bylo posledním prvkem v neobráceném multiset.

### <a name="remarks"></a>Poznámky

`crbegin` se používá s obrácený multiset stejně jako začít se používá s použita třída multiset.

S návratovou hodnotou `crbegin`, multiset – objekt nelze změnit.

`crbegin` můžete použít k iteraci v rámci použita třída multiset zpětně.

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

## <a name="crend"></a>  multiset::crend

Vrátí konstantní iterátor adresující umístění následující po posledním prvku v obráceném objektu multiset.

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>Návratová hodnota

Konstantní reverzní obousměrný iterátor adresující umístění následující po posledním prvku v obráceném objektu multiset (umístění, ke které došlo před první prvek v neobráceném multiset).

### <a name="remarks"></a>Poznámky

`crend` se používá s obrácený multiset stejně jako [end](#end) se používá s použita třída multiset.

S návratovou hodnotou `crend`, multiset – objekt nelze změnit.

`crend` slouží k otestování pro Určuje, zda zpětný iterátor dosáhl konce jeho multimnožina.

Hodnota vrácená `crend` by neměla být dereferencována.

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

## <a name="difference_type"></a>  multiset::difference_type

Celočíselný typ se znaménkem, který slouží k vyjádření počtu prvků multisady v rozsahu mezi prvky, na které odkazují iterátory.

```cpp
typedef typename allocator_type::difference_type difference_type;
```

### <a name="remarks"></a>Poznámky

`difference_type` Typ dochází při přičítání nebo zvýšení prostřednictvím iterátorů kontejneru. `difference_type` Se obvykle používá k vyjádření počtu prvků v rozsahu [ `first`, `last`) mezi iterátory `first` a `last`, obsahuje element, na které odkazuje `first` a rozsah prvků do , ale bez zahrnutí elementu, na které odkazuje `last`.

Všimněte si, že i když `difference_type` je k dispozici pro všechny iterátory, které splňují požadavky na vstupní iterátor, který obsahuje třídou obousměrných iterátorů, které jsou podporované reverzibilního kontejnery jako sadu, odčítání mezi iterátory pouze podporuje poskytuje náhodný přístup kontejneru jako vektor iterátory s náhodným přístupem.

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

## <a name="emplace"></a>  multiset::emplace

Vloží vytvořený prvek na místo (jsou prováděny žádné operace kopírování nebo přesunutí), s náznakem umístění.

```cpp
template <class... Args>
iterator emplace(Args&&... args);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|-|-|
|*argumenty*|Argumenty předané vytvořit element, který má být vložen do multisady.|

### <a name="return-value"></a>Návratová hodnota

Iterátor na nově vložený prvek.

### <a name="remarks"></a>Poznámky

Touto funkcí nejsou zneplatněny žádné odkazy na prvky kontejneru, ale to může zneplatnit všechny iterátory do kontejneru.

Při uložení Pokud je vyvolána výjimka, stav kontejneru se nezmění.

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

## <a name="emplace_hint"></a>  multiset::emplace_hint

Vloží vytvořený prvek na místo (jsou prováděny žádné operace kopírování nebo přesunutí), s náznakem umístění.

```cpp
template <class... Args>
iterator emplace_hint(
    const_iterator where,
    Args&&... args);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|-|-|
|*argumenty*|Argumenty předané vytvořit element, který má být vložen do multisady.|
|*kde*|Místo zahájení vyhledání správného bodu vložení. (Pokud bezprostředně předchází tento bod *kde*, vložení, může dojít v amortizovaném konstantním času místo logaritmické čas.)|

### <a name="return-value"></a>Návratová hodnota

Iterátor na nově vložený prvek.

### <a name="remarks"></a>Poznámky

Touto funkcí nejsou zneplatněny žádné odkazy na prvky kontejneru, ale to může zneplatnit všechny iterátory do kontejneru.

Při uložení Pokud je vyvolána výjimka, stav kontejneru se nezmění.

Příklad kódu naleznete v tématu [set::emplace_hint](../standard-library/set-class.md#emplace_hint).

## <a name="empty"></a>  multiset::Empty

Testuje, zda je objekt multiset je prázdný.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud třída multiset je prázdná. **false** Pokud třída multiset je prázdný.

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

## <a name="end"></a>  multiset::end

Vrátí iterátor za koncem.

```cpp
const_iterator end() const;

iterator end();
```

### <a name="return-value"></a>Návratová hodnota

Minulosti koncem iterátor. Pokud třída multiset je prázdný, pak `multiset::end() == multiset::begin()`.

### <a name="remarks"></a>Poznámky

**end** slouží k otestování, zda iterátor prošel konec jeho multiset.

Hodnota vrácená **end** by neměla být dereferencována.

Příklad kódu naleznete v tématu [multiset::find](#find).

## <a name="equal_range"></a>  multiset::equal_range

Vrátí pár iterátorů v uvedeném pořadí na první prvek v multisadě s klíčem, který je větší než zadaný klíč a na první prvek v multisadě s klíčem, který je roven nebo větší než tento klíč.

```cpp
pair <const_iterator, const_iterator> equal_range (const Key& key) const;

pair <iterator, iterator> equal_range (const Key& key);
```

### <a name="parameters"></a>Parametry

*key*<br/>
Klíč argumentu k porovnání s klíči řazení prvek z multiset vyhledaly.

### <a name="return-value"></a>Návratová hodnota

Pár iterátorů tak, že je první [lower_bound](#lower_bound) klíče a druhá je [upper_bound](#upper_bound) klíče.

Pro přístup k první iterace dvojice `pr` vrácený členskou funkci, použijte `pr`. **první**a ke zrušení iterátoru dolní mez, použijte \*( `pr`. **nejprve**). Pro přístup k druhé iterátoru dvojice `pr` vrácený členskou funkci, použijte `pr`. **druhý**a ke zrušení iterátoru horní mez, použijte \*( `pr`. **za druhé**).

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

## <a name="erase"></a>  multiset::Erase

Odebere prvek nebo rozsah prvků v multisadě od zadané pozice nebo odebere prvky, které odpovídají zadanému klíči.

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

*kde*<br/>
Pozice prvku, který má být odebrán.

*první*<br/>
Pozice prvního prvku, který má být odebrán.

*poslední*<br/>
Pozice bezprostředně za posledním prvkem, který má být odebrán.

*Key*<br/>
Hodnota klíče prvků, které mají být odebrány.

### <a name="return-value"></a>Návratová hodnota

Pro první dvě členské funkce obousměrný iterátor, který označí první prvek zbývající za jakýmikoli odstraněnými prvky, nebo element, který je koncem objektu multisady, pokud žádný takový prvek neexistuje.

Třetí členská funkce vrátí počet prvků, které byly odebrány z třída multiset.

### <a name="remarks"></a>Poznámky

Příklad kódu naleznete v tématu [set::erase](../standard-library/set-class.md#erase).

## <a name="find"></a>  multiset::Find

Vrátí iterátor odkazující na umístění prvku v multisadě, který má klíč odpovídající zadanému klíči.

```cpp
iterator find(const Key& key);

const_iterator find(const Key& key) const;
```

### <a name="parameters"></a>Parametry

*key*<br/>
Hodnota klíče k porovnání s klíči řazení prvek z multiset vyhledaly.

### <a name="return-value"></a>Návratová hodnota

Iterátor, který odkazuje na umístění element se zadaným klíčem nebo umístění následující po posledním prvku v multisadě ( `multiset::end()`) Pokud není nalezena žádná shoda pro klíč.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí iterátor odkazující na prvek v multisadě jejichž klíč odpovídá argumentu *klíč* pod binární predikát, který indukuje má za výsledek řazení podle méně než srovnání vztah.

Pokud návratová hodnota `find` přiřazen `const_iterator`, multiset – objekt nelze změnit. Pokud návratová hodnota `find` je přiřazena `iterator`, je možné upravit objekt multiset –

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

## <a name="get_allocator"></a>  multiset::get_allocator

Vrátí kopii přidělování objektu používanou k vytvoření multisady.

```cpp
allocator_type get_allocator() const;
```

### <a name="return-value"></a>Návratová hodnota

Alokátor použitý v multisadě.

### <a name="remarks"></a>Poznámky

Alokátory pro multiset – Třída zadejte, jak spravuje třídu úložiště. Výchozí alokátorů součástí třídy kontejneru standardní knihovny C++ postačí pro většinu programovacích potřeb. Psaní a použití vlastní třídu alokátoru je rozšířená C++.

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

## <a name="insert"></a>  multiset::Insert

Vloží prvek nebo rozsah prvků do multisady.

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
|*Val*|Hodnota element, který má být vložen do multisady.|
|*kde*|Místo zahájení vyhledání správného bodu vložení. (Pokud bezprostředně předchází tento bod *kde*, vložení, může dojít v amortizovaném konstantním času místo logaritmické čas.)|
|*ValTy*|Parametr šablony určující typ argumentu, třída multiset můžete použít k vytvoření prvku [value_type](../standard-library/map-class.md#value_type)a dokonalému předání *Val* jako argument.|
|*první*|Pozice prvního prvku, který chcete zkopírovat.|
|*poslední*|Pozice bezprostředně za posledním prvkem, který chcete zkopírovat.|
|*InputIterator*|Argument funkce šablony, který splňuje požadavky [vstupní iterátor](../standard-library/input-iterator-tag-struct.md) , která odkazuje na prvky typu, který lze použít k sestavení kompletních [value_type](../standard-library/map-class.md#value_type) objekty.|
|*IList*|[Initializer_list](../standard-library/initializer-list.md) ze kterého chcete kopírovat prvky.|

### <a name="return-value"></a>Návratová hodnota

Jeden element vložení členských funkcí (1) a (2) vrátí iterátor na místo, kde byl vložen nový prvek do multisady.

Jeden element s nápovědu členské funkce, (3) a (4) vrátí iterátor, který odkazuje na místo, kde byl vložen nový prvek do multisady.

### <a name="remarks"></a>Poznámky

Touto funkcí nejsou zneplatněny žádné ukazatele nebo odkazy, ale to může zneplatnit všechny iterátory do kontejneru.

Při vložení pouze jednoho prvku Pokud je vyvolána výjimka, stav kontejneru se nezmění. Pokud je při vkládání více prvků vyvolána výjimka, kontejner zůstane v neurčeném, ale platném stavu.

[Value_type](../standard-library/map-class.md#value_type) kontejneru je definice typu, který patří do tohoto kontejneru a sady pro `multiset<V>::value_type` je typ `const V`.

Rozsah členské funkce (5) vloží sekvenci hodnot prvků do multisady, která odpovídá každému prvku určenému pomocí iterátoru v rozsahu `[First, Last)`; proto `Last` nebude vložen. Členská funkce kontejneru `end()` vztahuje k pozici hned za posledním prvkem v kontejneru, například příkaz `s.insert(v.begin(), v.end());` vloží všechny prvky `v` do `s`.

Funkce člena seznamu inicializátorů (6) používá [initializer_list](../standard-library/initializer-list.md) pro kopírování prvků do multisady.

Pro vložení prvku vytvořeného na místě – to znamená, jsou prováděny žádné operace kopírování nebo přesunutí – naleznete v tématu [multiset::emplace](#emplace) a [multiset::emplace_hint](#emplace_hint).

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

## <a name="iterator"></a>  multiset::iterator

Typ, který poskytuje konstantní [obousměrný iterátor, který](../standard-library/bidirectional-iterator-tag-struct.md) , který může číst libovolný prvek v multisadě.

```cpp
typedef implementation-defined iterator;
```

### <a name="example"></a>Příklad

Podívejte se na příklad pro [začít](#begin) příklad toho, jak deklarace a používání `iterator`.

## <a name="key_comp"></a>  multiset::key_comp

Načte kopii objektu porovnání, použita pro seřazení klíčů v multisadě.

```cpp
key_compare key_comp() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí objekt funkce, která používá použita třída multiset k seřazení prvků, což je parametr šablony `Compare`.

Další informace o `Compare`, najdete v části poznámky [multiset – třída](../standard-library/multiset-class.md) tématu.

### <a name="remarks"></a>Poznámky

Uložený objekt definuje členskou funkci:

**BOOL – operátor**( **const Key &** *x*, **const Key &** *y*);

který vrátí hodnotu true, pokud *x* výhradně předchází *y* v pořadí řazení.

Všimněte si, že oba [key_compare](#key_compare) a [value_compare –](#value_compare) jsou synonyma pro parametr šablony `Compare`. Oba typy jsou k dispozici pro sadu tříd a multiset, kde jsou identické, z důvodu kompatibility se mapování tříd a multimap, kde se liší.

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

## <a name="key_compare"></a>  multiset::key_compare

Typ poskytující objekt funkce, který může porovnat dva klíče řazení pro určení relativního pořadí dvou prvků v multisadě.

```cpp
typedef Compare key_compare;
```

### <a name="remarks"></a>Poznámky

`key_compare` je synonymum pro parametr šablony `Compare`.

Další informace o `Compare`, najdete v části poznámky [multiset – třída](../standard-library/multiset-class.md) tématu.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [key_comp](#key_comp) příklad toho, jak deklarace a používání `key_compare`.

## <a name="key_type"></a>  multiset::key_type

Typ poskytující objekt funkce, který může porovnat klíče řazení pro určení relativního pořadí dvou prvků v multisadě.

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>Poznámky

`key_type` je synonymum pro parametr šablony `Key`.

Další informace o `Key`, najdete v části poznámky [multiset – třída](../standard-library/multiset-class.md) tématu.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [value_type](#value_type) příklad toho, jak deklarace a používání `key_type`.

## <a name="lower_bound"></a>  multiset::lower_bound

Vrátí iterátor na první prvek v multisadě s klíčem, který je roven nebo větší než zadaný klíč.

```cpp
const_iterator lower_bound(const Key& key) const;

iterator lower_bound(const Key& key);
```

### <a name="parameters"></a>Parametry

*key*<br/>
Klíč argumentu k porovnání s klíči řazení prvek z multiset vyhledaly.

### <a name="return-value"></a>Návratová hodnota

`iterator` Nebo `const_iterator` adresy umístění prvku v multisadě, s klíčem, který je roven nebo větší než tento klíč argument nebo který adresuje umístění následující po posledním prvku v multisadě, pokud ne odpovídají je nalezen klíč.

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

## <a name="max_size"></a>  multiset::max_size

Vrátí maximální délku multisady.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>Návratová hodnota

Maximální možná délka multisady.

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

## <a name="multiset"></a>  multiset::multiset

Vytvoří objekt multiset, který je prázdný nebo který je kopií celého nebo části některé multiset.

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
|*Al*|Třída úložiště alokátoru má být použit pro tento objekt multiset – výchozí nastavení je `Allocator`.|
|*Kompozice*|Funkce porovnání typu `const Compare` používají k seřazení prvků v multisadě, kde je použit výchozí `Compare`.|
|*doprava*|Multiset je vytvořený multiset kopií.|
|*první*|Pozice prvního prvku v rozsahu prvků, které se mají zkopírovat.|
|*poslední*|Pozice prvního prvku mimo rozsah prvků, které se mají zkopírovat.|
|*IList*|Seznam initializer_list, ze kterého chcete kopírovat prvky.|

### <a name="remarks"></a>Poznámky

Všechny konstruktory ukládají typ objektu allocator, který spravuje úložiště paměti třída multiset a, který lze později vrátit voláním [get_allocator](#get_allocator). Parametr allocator je často v deklaraci třídy vynechán a makra předběžného zpracování jsou použita k nahrazení alternativních alokátorů.

Všechny konstruktory inicializují své multiset.

Všechny konstruktory úložiště zadejte objekt funkce porovnání, která se používá k vytvoření pořadí mezi klíči objektu třída multiset a, který lze později vrátit voláním [key_comp](#key_comp).

První tři konstruktory určují prázdný počáteční multiset, druhý určuje typ funkce porovnání (*kompozici*) který se má použít při stanovení pořadí prvků a třetí explicitně určuje typ alokátoru (*Al*) který se má použít. Klíčové slovo **explicitní** potlačí některé druhy automatického převodu typu.

Čtvrtý konstruktor určuje kopii třída multiset *vpravo*.

Pátý konstruktor určuje kopii třída multiset přesunutím *vpravo*.

Šestý, sedmý a osmý konstruktory určují objekt initializer_list, ze kterého chcete kopírovat prvky.

Následující tři konstruktory kopírují rozsah `[First, Last)` multisady se zvyšující se explicitností v určování typu funkce porovnání a alokátorem.

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

## <a name="op_eq"></a>  multiset::Operator =

Nahradí prvky objektu to `multiset` konkrétně pomocí elementů z jiného `multiset`.

```cpp
multiset& operator=(const multiset& right);

multiset& operator=(multiset&& right);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|-|-|
|*doprava*|`multiset` z prvky, které jsou zkopírovaný ani přesunutý.|

### <a name="remarks"></a>Poznámky

`operator=` kopíruje nebo přesouvá prvky *správné* do tohoto `multiset`, v závislosti na typu odkazu (lvalue nebo rvalue) používá. Prvky, které jsou v tomto `multiset` před `operator=` spustí se zahodí.

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

## <a name="pointer"></a>  multiset::Pointer

Typ, který poskytuje ukazatel na prvek v multisadě.

```cpp
typedef typename allocator_type::pointer pointer;
```

### <a name="remarks"></a>Poznámky

Typ **ukazatel** lze použít ke změně hodnoty prvku.

Ve většině případů [iterátoru](#iterator) by měla sloužit pro přístup k prvkům v multiset – objektu.

## <a name="rbegin"></a>  multiset::rbegin

Vrátí iterátor adresující první prvek v obráceném objektu multiset.

```cpp
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```

### <a name="return-value"></a>Návratová hodnota

Reverzní obousměrný iterátor adresující první prvek v obráceném objektu multiset nebo adresování, co bylo posledním prvkem v neobráceném multiset.

### <a name="remarks"></a>Poznámky

`rbegin` se používá s obrácený multiset, stejně jako rbegin – se používá s použita třída multiset.

Pokud návratová hodnota `rbegin` přiřazen `const_reverse_iterator`, pak multiset – objekt nelze změnit. Pokud návratová hodnota `rbegin` je přiřazena `reverse_iterator`, pak multiset – objekt lze upravit.

`rbegin` můžete použít k iteraci v rámci použita třída multiset zpětně.

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

## <a name="reference"></a>  multiset::Reference

Typ, který poskytuje odkaz na prvek uložený v multisadě.

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

## <a name="rend"></a>  multiset::rend

Vrátí iterátor adresující umístění následující po posledním prvku v obráceném objektu multiset.

```cpp
const_reverse_iterator rend() const;

reverse_iterator rend();
```

### <a name="return-value"></a>Návratová hodnota

Reverzní obousměrný iterátor adresující umístění následující po posledním prvku v obráceném objektu multiset (umístění, ke které došlo před první prvek v neobráceném multiset).

### <a name="remarks"></a>Poznámky

`rend` se používá s obrácený multiset stejně jako [end](#end) se používá s použita třída multiset.

Pokud návratová hodnota `rend` přiřazen `const_reverse_iterator`, pak multiset – objekt nelze změnit. Pokud návratová hodnota `rend` je přiřazena `reverse_iterator`, pak multiset – objekt lze upravit.

`rend` slouží k otestování pro Určuje, zda zpětný iterátor dosáhl konce jeho multimnožina.

Hodnota vrácená `rend` by neměla být dereferencována.

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

## <a name="reverse_iterator"></a>  multiset::reverse_iterator

Typ, který poskytuje obousměrný iterátor, který může číst nebo upravovat prvek v obráceném objektu multiset.

```cpp
typedef std::reverse_iterator<iterator> reverse_iterator;
```

### <a name="remarks"></a>Poznámky

Typ `reverse_iterator` se používá k iteraci v rámci multiset v opačném pořadí.

### <a name="example"></a>Příklad

Viz příklad pro [rbegin –](#rbegin) příklad toho, jak deklarace a používání `reverse_iterator`.

## <a name="size"></a>  multiset::size

Vrátí počet prvků v multisadě.

```cpp
size_type size() const;
```

### <a name="return-value"></a>Návratová hodnota

Aktuální délka multisady.

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

## <a name="size_type"></a>  multiset::size_type

Typ celé číslo bez znaménka představující počet prvků v multisadě.

```cpp
typedef typename allocator_type::size_type size_type;
```

### <a name="example"></a>Příklad

Viz příklad pro [velikost](#size) příklad toho, jak deklarace a používání `size_type`

## <a name="swap"></a>  multiset::swap

Vymění prvky dvou multisets.

```cpp
void swap(
    multiset<Key, Compare, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*doprava*<br/>
Třída multiset argument poskytující prvky pro záměnu s multiset cíl.

### <a name="remarks"></a>Poznámky

Žádné odkazy, ukazatele nebo iterátory, které určují prvky ve dvou multisets, jehož prvky jsou během výměny nezruší platnost členskou funkci.

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

## <a name="upper_bound"></a>  multiset::upper_bound

Vrátí iterátor na první prvek v multisadě s klíčem, který je větší než zadaný klíč.

```cpp
const_iterator upper_bound(const Key& key) const;

iterator upper_bound(const Key& key);
```

### <a name="parameters"></a>Parametry

*key*<br/>
Klíč argumentu k porovnání s klíči řazení prvek z multiset vyhledaly.

### <a name="return-value"></a>Návratová hodnota

**Iterátoru** nebo `const_iterator` , který adresuje umístění prvku v multisadě s klíčem, který je větší než tento klíč argument nebo který adresuje umístění následující po posledním prvku v multisadě, pokud není nalezena žádná shoda pro klíč.

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

## <a name="value_comp"></a>  multiset::value_comp

Získá kopii objektu porovnání použitého pro seřazení hodnot prvků v multisadě.

```cpp
value_compare value_comp() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí objekt funkce, která používá použita třída multiset k seřazení prvků, což je parametr šablony `Compare`.

Další informace o `Compare`, najdete v části poznámky [multiset – třída](../standard-library/multiset-class.md) tématu.

### <a name="remarks"></a>Poznámky

Uložený objekt definuje členskou funkci:

**BOOL – operátor**( **const Key &**`_xVal`, **const Key &**`_yVal`);

který vrátí hodnotu true, pokud `_xVal` předchází a není rovno `_yVal` v pořadí řazení.

Všimněte si, že oba [key_compare](#key_compare) a [value_compare –](#value_compare) jsou synonyma pro parametr šablony `Compare`. Oba typy jsou k dispozici pro sadu tříd a multiset, kde jsou identické, z důvodu kompatibility se mapování tříd a multimap, kde se liší.

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

## <a name="value_compare"></a>  multiset::value_compare

Typ poskytující objekt funkce, který může porovnat dva klíče řazení pro určení jejich relativního pořadí v multisadě.

```cpp
typedef key_compare value_compare;
```

### <a name="remarks"></a>Poznámky

`value_compare` je synonymum pro parametr šablony `Compare`.

Všimněte si, že oba [key_compare](#key_compare) a `value_compare` jsou synonyma pro parametr šablony `Compare`. Oba typy jsou k dispozici pro sadu tříd a multiset, kde jsou identické, z důvodu kompatibility se mapování tříd a multimap, kde se liší.

Další informace o `Compare`, najdete v části poznámky [multiset – třída](../standard-library/multiset-class.md) tématu.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [value_comp –](#value_comp) příklad toho, jak deklarace a používání `value_compare`.

## <a name="value_type"></a>  multiset::value_type

Typ, který popisuje objekt uložený jako prvek sady jako multiset v jeho kapacitě jako hodnotu.

```cpp
typedef Key value_type;
```

### <a name="remarks"></a>Poznámky

`value_type` je synonymum pro parametr šablony `Key`.

Všimněte si, že oba [key_type](#key_type) a `value_type` jsou synonyma pro parametr šablony `Key`. Oba typy jsou k dispozici pro sadu tříd a multiset, kde jsou identické, z důvodu kompatibility se mapování tříd a multimap, kde se liší.

Další informace o `Key`, naleznete v části poznámky v tématu.

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

## <a name="see-also"></a>Viz také:

[Kontejnery](../cpp/containers-modern-cpp.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)<br/>
