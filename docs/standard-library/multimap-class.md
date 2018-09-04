---
title: multimap – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- map/std::multimap
- map/std::multimap::allocator_type
- map/std::multimap::const_iterator
- map/std::multimap::const_pointer
- map/std::multimap::const_reference
- map/std::multimap::const_reverse_iterator
- map/std::multimap::difference_type
- map/std::multimap::iterator
- map/std::multimap::key_compare
- map/std::multimap::key_type
- map/std::multimap::mapped_type
- map/std::multimap::pointer
- map/std::multimap::reference
- map/std::multimap::reverse_iterator
- map/std::multimap::size_type
- map/std::multimap::value_type
- map/std::multimap::begin
- map/std::multimap::cbegin
- map/std::multimap::cend
- map/std::multimap::clear
- map/std::multimap::count
- map/std::multimap::crbegin
- map/std::multimap::crend
- map/std::multimap::emplace
- map/std::multimap::emplace_hint
- map/std::multimap::empty
- map/std::multimap::end
- map/std::multimap::equal_range
- map/std::multimap::erase
- map/std::multimap::find
- map/std::multimap::get_allocator
- map/std::multimap::insert
- map/std::multimap::key_comp
- map/std::multimap::lower_bound
- map/std::multimap::max_size
- map/std::multimap::rbegin
- map/std::multimap::rend
- map/std::multimap::size
- map/std::multimap::swap
- map/std::multimap::upper_bound
- map/std::multimap::value_comp
dev_langs:
- C++
helpviewer_keywords:
- std::multimap [C++]
- std::multimap [C++], allocator_type
- std::multimap [C++], const_iterator
- std::multimap [C++], const_pointer
- std::multimap [C++], const_reference
- std::multimap [C++], const_reverse_iterator
- std::multimap [C++], difference_type
- std::multimap [C++], iterator
- std::multimap [C++], key_compare
- std::multimap [C++], key_type
- std::multimap [C++], mapped_type
- std::multimap [C++], pointer
- std::multimap [C++], reference
- std::multimap [C++], reverse_iterator
- std::multimap [C++], size_type
- std::multimap [C++], value_type
- std::multimap [C++], begin
- std::multimap [C++], cbegin
- std::multimap [C++], cend
- std::multimap [C++], clear
- std::multimap [C++], count
- std::multimap [C++], crbegin
- std::multimap [C++], crend
- std::multimap [C++], emplace
- std::multimap [C++], emplace_hint
- std::multimap [C++], empty
- std::multimap [C++], end
- std::multimap [C++], equal_range
- std::multimap [C++], erase
- std::multimap [C++], find
- std::multimap [C++], get_allocator
- std::multimap [C++], insert
- std::multimap [C++], key_comp
- std::multimap [C++], lower_bound
- std::multimap [C++], max_size
- std::multimap [C++], rbegin
- std::multimap [C++], rend
- std::multimap [C++], size
- std::multimap [C++], swap
- std::multimap [C++], upper_bound
- std::multimap [C++], value_comp
ms.assetid: 8796ae05-37c4-475a-9e61-75fde9d4a463
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: de4fa70eb4be67eb9ec29fbd24b7b1476681f7bd
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43678561"
---
# <a name="multimap-class"></a>multimap – třída

Multimap – třída standardní knihovny C++ se používá pro ukládání a načítání dat z kolekce, ve kterém je každý prvek pár, který má datovou hodnotu a klíč řazení. Hodnota klíče nemusí být jedinečná a je použita k automatickému seřazení dat. Hodnotu prvku v objektu multimap, ale ne jeho přidruženou hodnotu klíče, lze změnit přímo. Namísto toho hodnoty klíčů přidružené ke starým prvkům musí být odstraněny a vloženy nové hodnoty klíče související s novými prvky.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Key,
    class Type,
    class Traits=less <Key>,
    class Allocator=allocator <pair  <const Key, Type>>>
class multimap;
```

### <a name="parameters"></a>Parametry

*Key*<br/>
 Datový typ klíče, který se uloží v objektu multimap.

*Typ*<br/>
 Typ dat prvku, který bude uložen do objektu multimap.

*Osobnostní rysy*<br/>
 Typ poskytující objekt funkce, který může porovnat dvě hodnoty prvků pro určení jejich relativního pořadí v objektu multimap. Binární predikát `less<Key>` je výchozí hodnota.

V C ++ 14 můžete povolit heterogenní vyhledávání tak, že zadáte `std::less<>` nebo `std::greater<>` predikát, který nemá žádné parametry typu. Další informace najdete v tématu [heterogenní vyhledávání v asociativních kontejnerech](../standard-library/stl-containers.md#heterogeneous-lookup-in-associative-containers-c14)

*Allocator –*<br/>
 Typ představující uložený objekt alokátoru, který zapouzdřuje informace o přidělování a navrácení paměti zpět objektu map. Tento argument je nepovinný a výchozí hodnota je `allocator<pair <const Key, Type> >`.

## <a name="remarks"></a>Poznámky

Standardní knihovny C++, který je multimap – třída

- Asociativní kontejner, což je kontejner proměnné velikosti, který podporuje efektivní načtení hodnoty prvku založené na přiřazené hodnotě klíče.

- Oboustranný, protože poskytuje obousměrné iterátory pro přístup k jeho prvkům.

- Seřazený, protože jeho prvky jsou řazeny podle hodnot klíče v kontejneru podle zadané porovnávací funkce.

- Vícenásobný, protože je prvky nemusí mít jedinečné klíče, takže jedna hodnota klíče může mít k sobě přidružených mnoho datových hodnot prvků.

- Kontejner asociativních párů, protože jeho prvky hodnoty dat se liší od hodnot klíčů.

- Třída šablony, protože poskytuje obecné funkce a to nezávisle na určitém typu dat obsažených jako prvky nebo klíče. Datové typy použité pro prvky a klíče jsou místo toho zadány jako parametry v šabloně třídy společně s funkcí porovnání a alokátorem.

Iterátor poskytovaný třídou map je obousměrný iterátor, ale členské funkce třídy [vložit](#insert) a [multimap](#multimap) mají verze, které jako parametry šablony berou slabší vstupní iterátor, jehož požadavky na funkce jsou minimálnější než ty zaručeny třídou obousměrných iterátorů. Různé koncepty iterátorů tvoří rodinu týkající se upřesnění jejich funkčnosti. Každý koncept iterátoru má vlastní sadu požadavků a algoritmy, které s nimi pracují, musí omezit jejich předpoklady na požadavky podle typu iterátoru. Lze předpokládat, že ke vstupnímu iterátoru lze přistoupit přes ukazatel pro odkazování na některý objekt a že může být zvýšen na další iterátor v pořadí. Toto je minimální sada funkcí, ale je dostatečná pro srozumitelnou komunikaci o rozsahu u iterátorů `[First, Last)` v rámci členských funkcí třídy.

Volba typu kontejneru by měla obecně vycházet z typu vyhledávání a vkládání vyžadovaného aplikací. Asociativní kontejnery jsou optimalizovány pro operace vyhledávání, vkládání a odstranění. Členské funkce, které explicitně podporují tyto operace, jsou efektivní a jsou prováděny v čase, který je průměrně úměrný logaritmu počtu prvků v kontejneru. Vkládání prvků nezruší platnost žádných iterátorů a odstranění prvků zruší platnost pouze těch iterátorů, které výslovně odkazovaly na odstraněné prvky.

Objekt multimap by měl být asociativní kontejner dle výběru, kdy jsou podmínky přiřazení hodnot k jejich klíčům splněny aplikací. Model pro tento typ struktury je uspořádaný seznam klíčových slov s přidruženými řetězcovými hodnotami poskytujícími (řekněme) definice, kde slova nebyla vždy jednoznačně definována. Pokud místo toho klíčová slova byla jedinečně definovaná tak, aby byly klíče jedinečné, bude objekt map správným kontejnerem výběru. Naopak pokud je pouze uložen seznam slov, bude objekt set tím správným kontejnerem. Pokud bylo povoleno více výskytů jednoho slova, je objekt multiset odpovídající strukturou kontejneru.

Třída multimap seřadí sekvence pomocí volání uloženého objektu funkce typu [key_compare](#key_compare). Tento uložený objekt je funkce porovnání, která může získat přístup k voláním členské funkce [key_comp](#key_comp). Obecně, tyto prvky musí být menší než srovnatelné pro toto pořadí, což znamená, že když jsou uvedeny dva prvky, může být stanoveno, zda jsou ekvivalentní (v tom smyslu, že ani jeden není menší než ten druhý), nebo že jeden je menší než druhý. To má za výsledek řazení mezi neekvivalentními prvky. Technicky je funkce porovnání binárním predikátem, který indukuje přísné slabé řazení, standardním matematickým způsobem. Binární predikát `f(x,y)` je objekt funkce, který má dva objekty argumentu `x` a `y` a návratovou hodnotu true nebo false. Na sadě je přísné slabé seřazení, pokud je binární predikát Nereflexivní, antisymetrický a tranzitivní a je-li ekvivalence tranzitivní, kde dva objekty `x` a `y` jsou definovány jako ekvivalentní, když oba `f(x,y)`a `f(y,x)` jsou false. Pokud silnější podmínka rovnosti mezi klíči nahradí ekvivalenci, stane se pořadí celkovým (v tom smyslu, že všechny prvky jsou uspořádány ve vztahu k sobě navzájem) a odpovídající klíče budou od sebe nerozeznatelné.

V C ++ 14 můžete povolit heterogenní vyhledávání tak, že zadáte `std::less<>` nebo `std::greater<>` predikát, který nemá žádné parametry typu. Další informace najdete v tématu [heterogenní vyhledávání v asociativních kontejnerech](../standard-library/stl-containers.md#sequence_containers)

## <a name="members"></a>Členové

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[multimap](#multimap)|Vytvoří `multimap` , který je prázdný nebo, který je kopií celého nebo části některého jiného `multimap`.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[allocator_type](#allocator_type)|Typ, který představuje `allocator` třídy pro `multimap` objektu.|
|[const_iterator](#const_iterator)|Typ, který poskytuje obousměrný iterátor, který může číst **const** prvek `multimap`.|
|[const_pointer](#const_pointer)|Typ, který poskytuje ukazatel na **const** prvek `multimap`.|
|[const_reference](#const_reference)|Typ, který poskytuje odkaz na **const** element uložené v `multimap` pro čtení a provádění **const** operace.|
|[const_reverse_iterator](#const_reverse_iterator)|Typ, který poskytuje obousměrný iterátor, který může přečíst jakýkoli **const** prvek `multimap`.|
|[difference_type](#difference_type)|Celočíselný typ se znaménkem, který slouží k vyjádření počtu prvků `multimap` v rozsahu mezi prvky, na které odkazují iterátory.|
|[iterátor](#iterator)|Typ, který obsahuje rozdíl mezi dvěma iterátory, které odkazují na prvky v rámci stejného `multimap`.|
|[key_compare](#key_compare)|Typ poskytující objekt funkce, který může porovnat dva klíče řazení pro určení relativního pořadí dvou prvků v `multimap`.|
|[key_type](#key_type)|Typ, který popisuje řazení objektu klíče, který představuje každý prvek objektu `multimap`.|
|[mapped_type](#mapped_type)|Typ, který představuje typ dat uložených v `multimap`.|
|[Ukazatel](#pointer)|Typ, který poskytuje ukazatel na **const** prvek `multimap`.|
|[Referenční dokumentace](#reference)|Typ, který poskytuje odkaz na prvek uložený v `multimap`.|
|[reverse_iterator](#reverse_iterator)|Typ, který poskytuje obousměrný iterátor, který může číst nebo upravovat prvek v obráceném objektu `multimap`.|
|[size_type](#size_type)|Který poskytuje ukazatel na typ unsigned integer **const** prvek `multimap`.|
|[value_type](#value_type)|Typ poskytující objekt funkce, který může porovnat dva prvky jako klíče řazení pro určení jejich relativního pořadí v `multimap`.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[začít](#begin)|Vrátí iterátor adresující první prvek `multimap`.|
|[cbegin](#cbegin)|Vrátí konstantní iterátor adresující první prvek `multimap`.|
|[cend](#cend)|Vrátí konstantní iterátor adresující umístění následující po posledním prvku v `multimap`.|
|[Vymazat](#clear)|Vymaže všechny prvky `multimap`.|
|[Počet](#count)|Vrátí počet prvků v `multimap` jejichž klíč odpovídá klíči se zadaným parametrem.|
|[crbegin](#crbegin)|Vrátí konstantní iterátor adresující první prvek v obráceném objektu `multimap`.|
|[crend –](#crend)|Vrátí konstantní iterátor adresující umístění následující po posledním prvku v obráceném objektu `multimap`.|
|[emplace –](#emplace)|Vloží vytvořený prvek na místo do `multimap`.|
|[emplace_hint –](#emplace_hint)|Vloží vytvořený prvek na místo do `multimap`, s náznakem umístění|
|[prázdný](#empty)|Testuje, zda `multimap` je prázdný.|
|[ukončení](#end)|Vrátí iterátor adresující umístění následující po posledním prvku v `multimap`.|
|[equal_range](#equal_range)|Vyhledá rozsahu prvků, kde klíče prvku odpovídají zadané hodnotě.|
|[vymazání](#erase)|Odebere prvek nebo rozsah prvků `multimap` od zadané pozice nebo odebere prvky, které odpovídají zadanému klíči.|
|[Najít](#find)|Vrátí iterátor adresující první umístění prvku v `multimap` , který má klíč odpovídající zadanému klíči.|
|[get_allocator](#get_allocator)|Vrátí kopii objektu `allocator` objekt použitý k vytvoření `multimap`.|
|[Vložit](#insert)|Vloží prvek nebo rozsah prvků do `multimap`.|
|[key_comp](#key_comp)|Získá kopii objektu porovnání použitého pro seřazení klíčů v `multimap`.|
|[lower_bound –](#lower_bound)|Vrátí iterátor na první prvek v `multimap` s klíčem, který je roven nebo větší než zadaný klíč.|
|[max_size](#max_size)|Vrátí maximální délku objektu `multimap`.|
|[rbegin –](#rbegin)|Vrátí iterátor adresující první prvek v obráceném objektu `multimap`.|
|[rend –](#rend)|Vrátí iterátor adresující umístění následující po posledním prvku v obráceném objektu `multimap`.|
|[Velikost](#size)|Vrátí počet prvků v `multimap`.|
|[Prohození](#swap)|Vymění prvky dvou `multimap`s.|
|[upper_bound –](#upper_bound)|Vrátí iterátor na první prvek v `multimap` s klíčem, který je větší než zadaný klíč.|
|[value_comp](#value_comp)|Členská funkce vrátí objekt funkce, která určuje pořadí prvků v `multimap` porovnáním jejich hodnoty klíče.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operátor =](#op_eq)|Nahradí prvky objektu `multimap` s kopií jiného `multimap`.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<mapy >

**Namespace:** std

( **Klíč**, **hodnotu**) páry se ukládají v objektech multimap jako objekty typu `pair`. Třída pair vyžaduje hlavičku \<nástroje >, která je automaticky zahrnut objektem \<map >.

## <a name="allocator_type"></a>  multimap::allocator_type

Typ, který představuje třídu alokátoru pro objekt multimap.

```cpp
typedef Allocator allocator_type;
```

### <a name="example"></a>Příklad

Podívejte se na příklad pro [get_allocator](#get_allocator) příklad použití `allocator_type`.

## <a name="begin"></a>  multimap::begin

Vrátí iterátor adresující první prvek v objektu multimap.

```cpp
const_iterator begin() const;

iterator begin();
```

### <a name="return-value"></a>Návratová hodnota

Obousměrný iterátor adresující první prvek v objektu multimap nebo umístění následující po prázdný objektu multimap.

### <a name="example"></a>Příklad

```cpp
// multimap_begin.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1;

   multimap <int, int> :: iterator m1_Iter;
   multimap <int, int> :: const_iterator m1_cIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 0, 0 ) );
   m1.insert ( Int_Pair ( 1, 1 ) );
   m1.insert ( Int_Pair ( 2, 4 ) );

   m1_cIter = m1.begin ( );
   cout << "The first element of m1 is " << m1_cIter -> first << endl;

   m1_Iter = m1.begin ( );
   m1.erase ( m1_Iter );

   // The following 2 lines would err as the iterator is const
   // m1_cIter = m1.begin ( );
   // m1.erase ( m1_cIter );

   m1_cIter = m1.begin( );
   cout << "First element of m1 is now " << m1_cIter -> first << endl;
}
```

```Output
The first element of m1 is 0
First element of m1 is now 1
```

## <a name="cbegin"></a>  multimap::cbegin

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

## <a name="cend"></a>  multimap::cend

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

## <a name="clear"></a>  multimap::clear

Odstraní všechny prvky objektu multimap.

```cpp
void clear();
```

### <a name="example"></a>Příklad

Následující příklad ukazuje použití multimap::clear členskou funkci.

```cpp
// multimap_clear.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap<int, int> m1;
   multimap<int, int>::size_type i;
   typedef pair<int, int> Int_Pair;

   m1.insert(Int_Pair(1, 1));
   m1.insert(Int_Pair(2, 4));

   i = m1.size();
   cout << "The size of the multimap is initially "
        << i << "." << endl;

   m1.clear();
   i = m1.size();
   cout << "The size of the multimap after clearing is "
        << i << "." << endl;
}
```

```Output
The size of the multimap is initially 2.
The size of the multimap after clearing is 0.
```

## <a name="const_iterator"></a>  multimap::const_iterator

Typ, který poskytuje obousměrný iterátor, který může číst **const** prvek v objektu multimap.

```cpp
typedef implementation-defined const_iterator;
```

### <a name="remarks"></a>Poznámky

Typ `const_iterator` nelze použít ke změně hodnoty prvku.

`const_iterator` Určené multimap – odkazuje na objekty [value_type](#value_type), které jsou typu `pair<const Key, Type>`. Hodnota klíče je k dispozici prostřednictvím první pár členů, hodnota elementu pro mapovanou je k dispozici druhý člen, které odpovídá páru licencí.

Ke zrušení `const_iterator` *cIter* odkazující na prvek v objektu multimap, použijte **->** operátor.

Chcete-li přistupovat k hodnotě klíče pro element, použijte `cIter->first`, což je totéž jako `(*cIter).first`. Chcete-li získat přístup k hodnotě z namapované datum pro element, použijte `cIter->second`, což je totéž jako `(*cIter).second`.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [začít](#begin) příklad použití `const_iterator`.

## <a name="const_pointer"></a>  multimap::const_pointer

Typ, který poskytuje ukazatel **const** prvek v objektu multimap.

```cpp
typedef typename allocator_type::const_pointer const_pointer;
```

### <a name="remarks"></a>Poznámky

Typ `const_pointer` nelze použít ke změně hodnoty prvku.

Ve většině případů [iterátoru](#iterator) by měla sloužit pro přístup k prvkům v objektu multimap.

## <a name="const_reference"></a>  multimap::const_reference

Typ, který poskytuje odkaz na **const** prvek uložený v objektu multimap pro čtení a provádění **const** operace.

```cpp
typedef typename allocator_type::const_reference const_reference;
```

### <a name="example"></a>Příklad

```cpp
// multimap_const_ref.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );

   // Declare and initialize a const_reference &Ref1
   // to the key of the first element
   const int &Ref1 = ( m1.begin( ) -> first );

   // The following line would cause an error because the
   // non-const_reference cannot be used to access the key
   // int &Ref1 = ( m1.begin( ) -> first );

   cout << "The key of the first element in the multimap is "
        << Ref1 << "." << endl;

   // Declare and initialize a reference &Ref2
   // to the data value of the first element
   int &Ref2 = ( m1.begin( ) -> second );

   cout << "The data value of the first element in the multimap is "
        << Ref2 << "." << endl;
}
```

```Output
The key of the first element in the multimap is 1.
The data value of the first element in the multimap is 10.
```

## <a name="const_reverse_iterator"></a>  multimap::const_reverse_iterator

Typ, který poskytuje obousměrný iterátor, který může přečíst jakýkoli **const** prvek v objektu multimap.

```cpp
typedef std::reverse_iterator<const_iterator> const_reverse_iterator;
```

### <a name="remarks"></a>Poznámky

Typ `const_reverse_iterator` hodnotu prvku nelze změnit a použít k iteraci v rámci objektu multimap, v opačném pořadí.

`const_reverse_iterator` Určené multimap – odkazuje na objekty [value_type](#value_type), které jsou typu `pair<const Key, Type>`. Hodnota klíče je k dispozici prostřednictvím první pár členů, hodnota elementu pro mapovanou je k dispozici druhý člen, které odpovídá páru licencí.

Ke zrušení `const_reverse_iterator` *crIter* odkazující na prvek v objektu multimap, použijte **->** operátor.

Chcete-li přistupovat k hodnotě klíče pro element, použijte `crIter->first`, což je totéž jako `(*crIter).first`. Chcete-li získat přístup k hodnotě z namapované datum pro element, použijte `crIter->second`, což je totéž jako `(*crIter).first`.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [rend](#rend) příklad toho, jak deklarace a používání `const_reverse_iterator`.

## <a name="count"></a>  multimap::Count

Vrátí počet prvků v objektu multimap klíči odpovídá klíči se zadaným parametrem.

```cpp
size_type count(const Key& key) const;
```

### <a name="parameters"></a>Parametry

*Klíč*<br/>
 Klíč prvky, které mají být odpovídat z objektu multimap.

### <a name="return-value"></a>Návratová hodnota

Počet prvků, jejichž klíče řazení odpovídat klíč parametru; 0, pokud objektu multimap neobsahuje prvek s odpovídajícím klíčem.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí počet prvků v rozsahu

[ `lower_bound` (_ *Klíč* ), `upper_bound` (\_ *klíč* ))

které mají hodnotu klíče *klíč*.

### <a name="example"></a>Příklad

Následující příklad ukazuje použití multimap::count členskou funkci.

```cpp
// multimap_count.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
    using namespace std;
    multimap<int, int> m1;
    multimap<int, int>::size_type i;
    typedef pair<int, int> Int_Pair;

    m1.insert(Int_Pair(1, 1));
    m1.insert(Int_Pair(2, 1));
    m1.insert(Int_Pair(1, 4));
    m1.insert(Int_Pair(2, 1));

    // Elements do not need to have unique keys in multimap,
    // so duplicates are allowed and counted
    i = m1.count(1);
    cout << "The number of elements in m1 with a sort key of 1 is: "
         << i << "." << endl;

    i = m1.count(2);
    cout << "The number of elements in m1 with a sort key of 2 is: "
         << i << "." << endl;

    i = m1.count(3);
    cout << "The number of elements in m1 with a sort key of 3 is: "
         << i << "." << endl;
}
```

```Output
The number of elements in m1 with a sort key of 1 is: 2.
The number of elements in m1 with a sort key of 2 is: 2.
The number of elements in m1 with a sort key of 3 is: 0.
```

## <a name="crbegin"></a>  multimap::crbegin

Vrátí konstantní iterátor adresující první prvek v obráceném objektu multimap.

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>Návratová hodnota

Konstantní reverzní obousměrný iterátor adresující první prvek v obráceném objektu [multimap](../standard-library/multimap-class.md) nebo co bylo posledním prvkem v neobráceném adresování `multimap`.

### <a name="remarks"></a>Poznámky

`crbegin` se používá s obráceném objektu `multimap` stejně jako [začít](#begin) se používá s `multimap`.

S návratovou hodnotou `crbegin`, `multimap` objekt nelze změnit.

`crbegin` můžete použít k iteraci v rámci `multimap` zpětně.

### <a name="example"></a>Příklad

```cpp
// multimap_crbegin.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1;

   multimap <int, int> :: const_reverse_iterator m1_crIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );

   m1_crIter = m1.crbegin( );
   cout << "The first element of the reversed multimap m1 is "
        << m1_crIter -> first << "." << endl;
}
```

```Output
The first element of the reversed multimap m1 is 3.
```

## <a name="crend"></a>  multimap::crend

Vrátí konstantní iterátor adresující umístění následující po posledním prvku v obráceném objektu multimap.

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>Návratová hodnota

Konstantní reverzní obousměrný iterátor adresující umístění následující po posledním prvku v obráceném objektu [multimap](../standard-library/multimap-class.md) (umístění, ke které došlo před první prvek v neobráceném `multimap`).

### <a name="remarks"></a>Poznámky

`crend` se používá s obráceném objektu `multimap` stejně jako [multimap::end](#end) se používá s `multimap`.

S návratovou hodnotou `crend`, `multimap` objekt nelze změnit.

`crend` můžete použít k testování na tom, zda zpětný iterátor dosáhl konce jeho `multimap`.

Hodnota vrácená `crend` by neměla být dereferencována.

### <a name="example"></a>Příklad

```cpp
// multimap_crend.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1;

   multimap <int, int> :: const_reverse_iterator m1_crIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );

   m1_crIter = m1.crend( );
   m1_crIter--;
   cout << "The last element of the reversed multimap m1 is "
        << m1_crIter -> first << "." << endl;
}
```

```Output
The last element of the reversed multimap m1 is 1.
```

## <a name="difference_type"></a>  multimap::difference_type

Celočíselný typ se znaménkem, který slouží k vyjádření počtu prvků objektu multimap v rozsahu mezi prvky, na které odkazují iterátory.

```cpp
typedef typename allocator_type::difference_type difference_type;
```

### <a name="remarks"></a>Poznámky

`difference_type` Typ dochází při přičítání nebo zvýšení prostřednictvím iterátorů kontejneru. `difference_type` Se obvykle používá k vyjádření počtu prvků v rozsahu [*první*, *poslední*) mezi iterátory `first` a `last`, obsahuje prvek, na který podle `first` a rozsahu prvků až, ale bez zahrnutí elementu odkazované `last`.

Všimněte si, že i když `difference_type` je k dispozici pro všechny iterátory, které splňují požadavky na vstupní iterátor, který obsahuje třídou obousměrných iterátorů, které jsou podporovány reverzibilního kontejnery, jako je sada odčítání mezi iterátory pouze podporuje iterátory s náhodným přístupem k dispozici kontejnerem náhodného přístupu, jako je například vektoru.

### <a name="example"></a>Příklad

```cpp
// multimap_diff_type.cpp
// compile with: /EHsc
#include <iostream>
#include <map>
#include <algorithm>

int main( )
{
   using namespace std;
   multimap <int, int> m1;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 3, 20 ) );

   // The following will insert as multimap keys are not unique
   m1.insert ( Int_Pair ( 2, 30 ) );

   multimap <int, int>::iterator m1_Iter, m1_bIter, m1_eIter;
   m1_bIter = m1.begin( );
   m1_eIter = m1.end( );

   // Count the number of elements in a multimap
   multimap <int, int>::difference_type  df_count = 0;
   m1_Iter = m1.begin( );
   while ( m1_Iter != m1_eIter )
   {
      df_count++;
      m1_Iter++;
   }

   cout << "The number of elements in the multimap m1 is: "
        << df_count << "." << endl;
}
```

```Output
The number of elements in the multimap m1 is: 4.
```

## <a name="emplace"></a>  multimap::emplace

Vloží vytvořený prvek na místo (jsou prováděny žádné operace kopírování nebo přesunutí).

```cpp
template <class... Args>
iterator emplace(Args&&... args);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|-|-|
|*argumenty*|Argumenty předané vytvořit element, který má být vložen do objektu multimap.|

### <a name="return-value"></a>Návratová hodnota

Iterátor na nově vložený prvek.

### <a name="remarks"></a>Poznámky

Touto funkcí nejsou zneplatněny žádné odkazy na prvky kontejneru, ale to může zneplatnit všechny iterátory do kontejneru.

Pokud při vkládání je vyvolána výjimka, kontejner zůstane beze změny a je znovu vyvolána výjimka.

[Value_type](../standard-library/map-class.md#value_type) elementu je pár, tak, aby hodnota elementu bude seřazená dvojice s první komponenta rovna hodnotě klíče a druhá komponenta rovna hodnotě dat tohoto prvku.

### <a name="example"></a>Příklad

```cpp
// multimap_emplace.cpp
// compile with: /EHsc
#include <map>
#include <string>
#include <iostream>

using namespace std;

template <typename M> void print(const M& m) {
    cout << m.size() << " elements: " << endl;

    for (const auto& p : m) {
        cout << "(" << p.first <<  "," << p.second << ") ";
    }

    cout << endl;
}

int main()
{
    multimap<string, string> m1;

    m1.emplace("Anna", "Accounting");
    m1.emplace("Bob", "Accounting");
    m1.emplace("Carmine", "Engineering");

    cout << "multimap modified, now contains ";
    print(m1);
    cout << endl;

    m1.emplace("Bob", "Engineering");

    cout << "multimap modified, now contains ";
    print(m1);
    cout << endl;
}

```

## <a name="emplace_hint"></a>  multimap::emplace_hint

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
|*argumenty*|Argumenty předané vytvořit element, který má být vložen do objektu multimap.|
|*kde*|Místo zahájení vyhledání správného bodu vložení. (Pokud bezprostředně předchází tento bod *kde*, vložení, může dojít v amortizovaném konstantním času místo logaritmické čas.)|

### <a name="return-value"></a>Návratová hodnota

Iterátor na nově vložený prvek.

### <a name="remarks"></a>Poznámky

Touto funkcí nejsou zneplatněny žádné odkazy na prvky kontejneru, ale to může zneplatnit všechny iterátory do kontejneru.

Při uložení Pokud je vyvolána výjimka, stav kontejneru se nezmění.

[Value_type](../standard-library/map-class.md#value_type) elementu je pár, tak, aby hodnota elementu bude seřazená dvojice s první komponenta rovna hodnotě klíče a druhá komponenta rovna hodnotě dat tohoto prvku.

Příklad kódu naleznete v tématu [map::emplace_hint](../standard-library/map-class.md#emplace_hint).

## <a name="empty"></a>  multimap::Empty

Testuje, zda multimap je prázdný.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud objektu multimap je prázdná. **false** Pokud objektu multimap je prázdný.

### <a name="example"></a>Příklad

```cpp
// multimap_empty.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1, m2;

   typedef pair <int, int> Int_Pair;
   m1.insert ( Int_Pair ( 1, 1 ) );

   if ( m1.empty( ) )
      cout << "The multimap m1 is empty." << endl;
   else
      cout << "The multimap m1 is not empty." << endl;

   if ( m2.empty( ) )
      cout << "The multimap m2 is empty." << endl;
   else
      cout << "The multimap m2 is not empty." << endl;
}
```

```Output
The multimap m1 is not empty.
The multimap m2 is empty.
```

## <a name="end"></a>  multimap::end

Vrátí iterátor za koncem.

```cpp
const_iterator end() const;


iterator end();
```

### <a name="return-value"></a>Návratová hodnota

Minulosti koncem iterátor. Pokud objektu multimap je prázdný, pak `multimap::end() == multimap::begin()`.

### <a name="remarks"></a>Poznámky

**end** slouží k otestování, zda iterátor prošel konec jeho objektu multimap.

Hodnota vrácená **end** by neměla být dereferencována.

Příklad kódu naleznete v tématu [multimap::find](#find).

## <a name="equal_range"></a>  multimap::equal_range

Vyhledá rozsahu prvků, kde klíče prvku odpovídají zadané hodnotě.

```cpp
pair <const_iterator, const_iterator> equal_range (const Key& key) const;

pair <iterator, iterator> equal_range (const Key& key);
```

### <a name="parameters"></a>Parametry

*Klíč*<br/>
 Klíč argumentu k porovnání s klíči řazení prvek z objektu multimap vyhledaly.

### <a name="return-value"></a>Návratová hodnota

Pár iterátorů tak, že je první [lower_bound](#lower_bound) klíče a druhá je [upper_bound](#upper_bound) klíče.

Pro přístup k první iterace dvojice `pr` vrácený členskou funkci, použijte `pr`. **první** a pokouší dereferencovat iterátoru dolní mez, použijte \*( `pr`. **nejprve**). Pro přístup k druhé iterátoru dvojice `pr` vrácený členskou funkci, použijte `pr`. **druhý** a pokouší dereferencovat iterátoru horní mez, použijte \*( `pr`. **za druhé**).

### <a name="example"></a>Příklad

```cpp
// multimap_equal_range.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   typedef multimap <int, int, less<int> > IntMMap;
   IntMMap m1;
   multimap <int, int> :: const_iterator m1_RcIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );

   pair <IntMMap::const_iterator, IntMMap::const_iterator> p1, p2;
   p1 = m1.equal_range( 2 );

   cout << "The lower bound of the element with "
        << "a key of 2 in the multimap m1 is: "
        << p1.first -> second << "." << endl;

   cout << "The upper bound of the element with "
        << "a key of 2 in the multimap m1 is: "
        << p1.second -> second << "." << endl;

   // Compare the upper_bound called directly
   m1_RcIter = m1.upper_bound( 2 );

   cout << "A direct call of upper_bound( 2 ) gives "
        << m1_RcIter -> second << "," << endl
        << " matching the 2nd element of the pair"
        << " returned by equal_range( 2 )." << endl;

   p2 = m1.equal_range( 4 );

   // If no match is found for the key,
   // both elements of the pair return end( )
   if ( ( p2.first == m1.end( ) ) && ( p2.second == m1.end( ) ) )
      cout << "The multimap m1 doesn't have an element "
           << "with a key less than 4." << endl;
   else
      cout << "The element of multimap m1 with a key >= 40 is: "
           << p1.first -> first << "." << endl;
}
```

```Output
The lower bound of the element with a key of 2 in the multimap m1 is: 20.
The upper bound of the element with a key of 2 in the multimap m1 is: 30.
A direct call of upper_bound( 2 ) gives 30,
 matching the 2nd element of the pair returned by equal_range( 2 ).
The multimap m1 doesn't have an element with a key less than 4.
```

## <a name="erase"></a>  multimap::Erase

Odebere prvek nebo rozsah prvků v objektu multimap od zadané pozice nebo odebere prvky, které odpovídají zadanému klíči.

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
 Klíč prvky, které mají být odebrány.

### <a name="return-value"></a>Návratová hodnota

Pro první dvě členské funkce obousměrný iterátor, který označí první prvek zbývající za jakýmikoli odstraněnými prvky, nebo element, který je koncem objektu na mapě, pokud žádný takový prvek neexistuje.

Třetí členská funkce vrátí počet prvků, které byly odebrány z objektu multimap.

### <a name="remarks"></a>Poznámky

Příklad kódu naleznete v tématu [map::erase](../standard-library/map-class.md#erase).

## <a name="find"></a>  multimap::Find

Vrátí iterátor odkazující na první umístění prvku v objektu multimap, který má klíč odpovídající zadanému klíči.

```cpp
iterator find(const Key& key);


const_iterator find(const Key& key) const;
```

### <a name="parameters"></a>Parametry

*Klíč*<br/>
 Hodnota klíče k porovnání s klíči řazení prvek z objektu multimap vyhledaly.

### <a name="return-value"></a>Návratová hodnota

Iterátor, který odkazuje na umístění element se zadaným klíčem nebo umístění následující po posledním prvku v objektu multimap (`multimap::end()`) Pokud není nalezena žádná shoda pro klíč.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí iterátor odkazující na prvek v objektu multimap jehož klíč řazení je ekvivalentní argumentu klíče pod binární predikát, který indukuje má za výsledek řazení podle méně než srovnání vztah.

Pokud návratová hodnota `find` je přiřazena `const_iterator`, nelze upravit objekt multimap. Pokud návratová hodnota `find` je přiřazena `iterator`, objektem multimap je možné upravit.

### <a name="example"></a>Příklad

```cpp
// compile with: /EHsc /W4 /MTd
#include <map>
#include <iostream>
#include <vector>
#include <string>
#include <utility>  // make_pair()

using namespace std;

template <typename A, typename B> void print_elem(const pair<A, B>& p) {
    cout << "(" << p.first << ", " << p.second << ") ";
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
    multimap<int, string> m1({ { 40, "Zr" }, { 45, "Rh" } });
    cout << "The starting multimap m1 is (key, value):" << endl;
    print_collection(m1);

    vector<pair<int, string>> v;
    v.push_back(make_pair(43, "Tc"));
    v.push_back(make_pair(41, "Nb"));
    v.push_back(make_pair(46, "Pd"));
    v.push_back(make_pair(42, "Mo"));
    v.push_back(make_pair(44, "Ru"));
    v.push_back(make_pair(44, "Ru")); // attempt a duplicate

    cout << "Inserting the following vector data into m1:" << endl;
    print_collection(v);

    m1.insert(v.begin(), v.end());

    cout << "The modified multimap m1 is (key, value):" << endl;
    print_collection(m1);
    cout << endl;
    findit(m1, 45);
    findit(m1, 6);
}

```

## <a name="get_allocator"></a>  multimap::get_allocator

Vrátí kopii přidělování objektu používanou k vytvoření objektu multimap.

```cpp
allocator_type get_allocator() const;
```

### <a name="return-value"></a>Návratová hodnota

Alokátor použitý v objektu multimap.

### <a name="remarks"></a>Poznámky

Alokátory pro multimap – Třída zadejte, jak spravuje třídu úložiště. Výchozí alokátorů součástí třídy kontejneru standardní knihovny C++ postačí pro většinu programovacích potřeb. Psaní a použití vlastní třídu alokátoru je rozšířená C++.

### <a name="example"></a>Příklad

```cpp
// multimap_get_allocator.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int>::allocator_type m1_Alloc;
   multimap <int, int>::allocator_type m2_Alloc;
   multimap <int, double>::allocator_type m3_Alloc;
   multimap <int, int>::allocator_type m4_Alloc;

   // The following lines declare objects
   // that use the default allocator.
   multimap <int, int> m1;
   multimap <int, int, allocator<int> > m2;
   multimap <int, double, allocator<double> > m3;

   m1_Alloc = m1.get_allocator( );
   m2_Alloc = m2.get_allocator( );
   m3_Alloc = m3.get_allocator( );

   cout << "The number of integers that can be allocated"
        << endl << "before free memory is exhausted: "
        << m2.max_size( ) << ".\n" << endl;

   cout << "The number of doubles that can be allocated"
        << endl << "before free memory is exhausted: "
        << m3.max_size( ) <<  ".\n" << endl;

   // The following line creates a multimap m4
   // with the allocator of multimap m1.
   map <int, int> m4( less<int>( ), m1_Alloc );

   m4_Alloc = m4.get_allocator( );

   // Two allocators are interchangeable if
   // storage allocated from each can be
   // deallocated via the other
   if( m1_Alloc == m4_Alloc )
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

## <a name="insert"></a>  multimap::Insert

Vloží prvek nebo rozsah prvků do multimap.

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
|*Val*|Hodnota element, který má být vložen do objektu multimap.|
|*kde*|Místo zahájení vyhledání správného bodu vložení. (Pokud bezprostředně předchází tento bod *kde*, vložení, může dojít v amortizovaném konstantním času místo logaritmické čas.)|
|*ValTy*|Parametr šablony určující typ argumentu, na mapě můžete použít k vytvoření prvku [value_type](../standard-library/map-class.md#value_type)a dokonalému předání *Val* jako argument.|
|*první*|Pozice prvního prvku, který chcete zkopírovat.|
|*poslední*|Pozice bezprostředně za posledním prvkem, který chcete zkopírovat.|
|*InputIterator*|Argument funkce šablony, který splňuje požadavky [vstupní iterátor](../standard-library/input-iterator-tag-struct.md) , která odkazuje na prvky typu, který lze použít k sestavení kompletních [value_type](../standard-library/map-class.md#value_type) objekty.|
|*IList*|[Initializer_list](../standard-library/initializer-list.md) ze kterého chcete kopírovat prvky.|

### <a name="return-value"></a>Návratová hodnota

Jeden element vložení členských funkcí (1) a (2) vrátí iterátor na místo, kde byl vložen nový prvek do objektu multimap.

Jeden element s nápovědu členské funkce, (3) a (4) vrátí iterátor, který odkazuje na místo, kde byl vložen nový prvek do objektu multimap.

### <a name="remarks"></a>Poznámky

Touto funkcí nejsou zneplatněny žádné ukazatele nebo odkazy, ale to může zneplatnit všechny iterátory do kontejneru.

Při vložení pouze jednoho prvku Pokud je vyvolána výjimka, stav kontejneru se nezmění. Pokud je při vkládání více prvků vyvolána výjimka, kontejner zůstane v neurčeném, ale platném stavu.

[Value_type](../standard-library/map-class.md#value_type) kontejneru je definice typu, který patří do tohoto kontejneru a pro mapu, `multimap<K, V>::value_type` je `pair<const K, V>`. Hodnota prvku je seřazená dvojice, ve které je první komponenta rovna hodnotě klíče a druhá komponenta je rovna datové hodnotě prvku.

Rozsah členské funkce (5) vloží sekvenci hodnot prvků do objektu multimap, který odpovídá každému prvku určenému pomocí iterátoru v rozsahu `[First, Last)`; proto *poslední* nebude vložen. Členská funkce kontejneru `end()` vztahuje k pozici hned za posledním prvkem v kontejneru, například příkaz `m.insert(v.begin(), v.end());` vloží všechny prvky `v` do `m`.

Funkce člena seznamu inicializátorů (6) používá [initializer_list](../standard-library/initializer-list.md) pro kopírování prvků do objektu map.

Pro vložení prvku vytvořeného na místě – to znamená, jsou prováděny žádné operace kopírování nebo přesunutí – naleznete v tématu [multimap::emplace](#emplace) a [multimap::emplace_hint](#emplace_hint).

### <a name="example"></a>Příklad

```cpp
// multimap_insert.cpp
// compile with: /EHsc
#include <map>
#include <iostream>
#include <string>
#include <vector>
#include <utility>  // make_pair()

using namespace std;

template <typename M> void print(const M& m) {
    cout << m.size() << " elements: ";

    for (const auto& p : m) {
        cout << "(" << p.first << ", " << p.second << ") ";
    }

    cout << endl;
}

int main()
{

    // insert single values
    multimap<int, int> m1;
    // call insert(const value_type&) version
    m1.insert({ 1, 10 });
    // call insert(ValTy&&) version
    m1.insert(make_pair(2, 20));

    cout << "The original key and mapped values of m1 are:" << endl;
    print(m1);

    // intentionally attempt a duplicate, single element
    m1.insert(make_pair(1, 111));

    cout << "The modified key and mapped values of m1 are:" << endl;
    print(m1);

    // single element, with hint
    m1.insert(m1.end(), make_pair(3, 30));
    cout << "The modified key and mapped values of m1 are:" << endl;
    print(m1);
    cout << endl;

    // The templatized version inserting a jumbled range
    multimap<int, int> m2;
    vector<pair<int, int>> v;
    v.push_back(make_pair(43, 294));
    v.push_back(make_pair(41, 262));
    v.push_back(make_pair(45, 330));
    v.push_back(make_pair(42, 277));
    v.push_back(make_pair(44, 311));

    cout << "Inserting the following vector data into m2:" << endl;
    print(v);

    m2.insert(v.begin(), v.end());

    cout << "The modified key and mapped values of m2 are:" << endl;
    print(m2);
    cout << endl;

    // The templatized versions move-constructing elements
    multimap<int, string>  m3;
    pair<int, string> ip1(475, "blue"), ip2(510, "green");

    // single element
    m3.insert(move(ip1));
    cout << "After the first move insertion, m3 contains:" << endl;
    print(m3);

    // single element with hint
    m3.insert(m3.end(), move(ip2));
    cout << "After the second move insertion, m3 contains:" << endl;
    print(m3);
    cout << endl;

    multimap<int, int> m4;
    // Insert the elements from an initializer_list
    m4.insert({ { 4, 44 }, { 2, 22 }, { 3, 33 }, { 1, 11 }, { 5, 55 } });
    cout << "After initializer_list insertion, m4 contains:" << endl;
    print(m4);
    cout << endl;
}

```

## <a name="iterator"></a>  multimap::iterator

Typ, který poskytuje obousměrný iterátor, který může číst nebo upravovat libovolný prvek v objektu multimap.

```cpp
typedef implementation-defined iterator;
```

### <a name="remarks"></a>Poznámky

`iterator` Určené multimap – odkazuje na objekty [value_type](#value_type), které jsou typu `pair<const Key, Type>`. Hodnota klíče je k dispozici prostřednictvím první pár členů, hodnota elementu pro mapovanou je k dispozici druhý člen, které odpovídá páru licencí.

Ke zrušení `iterator` *Iter* odkazující na prvek v objektu multimap, použijte **->** operátor.

Chcete-li přistupovat k hodnotě klíče pro element, použijte `Iter->first`, což je totéž jako `(*Iter).first`. Chcete-li získat přístup k hodnotě z namapované datum pro element, použijte `Iter->second`, což je totéž jako `(*Iter).second`.

Typ `iterator` lze použít ke změně hodnoty prvku.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [začít](#begin) příklad toho, jak deklarace a používání `iterator`.

## <a name="key_comp"></a>  multimap::key_comp

Načte kopii objektu porovnání, použita pro seřazení klíčů v objektu multimap.

```cpp
key_compare key_comp() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí objekt funkce, která používá multimap řazení jeho prvků.

### <a name="remarks"></a>Poznámky

Uložený objekt definuje členskou funkci

`bool operator( const Key& x, const Key& y);`

který vrátí hodnotu true, pokud *x* výhradně předchází *y* v pořadí řazení.

### <a name="example"></a>Příklad

```cpp
// multimap_key_comp.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;

   multimap <int, int, less<int> > m1;
   multimap <int, int, less<int> >::key_compare kc1 = m1.key_comp( ) ;
   bool result1 = kc1( 2, 3 ) ;
   if( result1 == true )
   {
      cout << "kc1( 2,3 ) returns value of true, "
           << "where kc1 is the function object of m1."
           << endl;
   }
   else
   {
      cout << "kc1( 2,3 ) returns value of false "
           << "where kc1 is the function object of m1."
           << endl;
   }

   multimap <int, int, greater<int> > m2;
   multimap <int, int, greater<int> >::key_compare kc2 = m2.key_comp( );
   bool result2 = kc2( 2, 3 ) ;
   if( result2 == true )
   {
      cout << "kc2( 2,3 ) returns value of true, "
           << "where kc2 is the function object of m2."
           << endl;
   }
   else
   {
      cout << "kc2( 2,3 ) returns value of false, "
           << "where kc2 is the function object of m2."
           << endl;
   }
}
```

```Output
kc1( 2,3 ) returns value of true, where kc1 is the function object of m1.
kc2( 2,3 ) returns value of false, where kc2 is the function object of m2.
```

## <a name="key_compare"></a>  multimap::key_compare

Typ poskytující objekt funkce, který může porovnat dva klíče řazení pro určení relativního pořadí dvou prvků v objektu multimap.

```cpp
typedef Traits key_compare;
```

### <a name="remarks"></a>Poznámky

`key_compare` je synonymum pro parametr šablony `Traits`.

Další informace o `Traits` najdete v článku [multimap – třída](../standard-library/multimap-class.md) tématu.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [key_comp](#key_comp) příklad toho, jak deklarace a používání `key_compare`.

## <a name="key_type"></a>  multimap::key_type

Typ, který popisuje řazení objektu klíče, který představuje každý prvek objektu multimap.

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>Poznámky

`key_type` je synonymum pro parametr šablony `Key`.

Další informace o `Key`, najdete v části poznámky [multimap – třída](../standard-library/multimap-class.md) tématu.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [value_type](#value_type) příklad toho, jak deklarace a používání `key_type`.

## <a name="lower_bound"></a>  multimap::lower_bound

Vrátí iterátor na první prvek v objektu multimap, který s klíčem, který je roven nebo větší než zadaný klíč.

```cpp
iterator lower_bound(const Key& key);

const_iterator lower_bound(const Key& key) const;
```

### <a name="parameters"></a>Parametry

*Klíč*<br/>
 Klíč argumentu k porovnání s klíči řazení prvek z objektu multimap vyhledaly.

### <a name="return-value"></a>Návratová hodnota

Iterátor nebo `const_iterator` adresy umístění prvku v objektu multimap, s klíčem, který je roven nebo větší než tento klíč argument nebo který adresuje umístění následující po posledním prvku v objektu multimap, pokud žádné odpovídají je nalezen klíč.

Pokud návratová hodnota `lower_bound` je přiřazena `const_iterator`, nelze upravit objekt multimap. Pokud návratová hodnota `lower_bound` je přiřazena **iterátoru**, objektem multimap je možné upravit.

### <a name="example"></a>Příklad

```cpp
// multimap_lower_bound.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1;
   multimap <int, int> :: const_iterator m1_AcIter, m1_RcIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );

   m1_RcIter = m1.lower_bound( 2 );
   cout << "The element of multimap m1 with a key of 2 is: "
        << m1_RcIter -> second << "." << endl;

   m1_RcIter = m1.lower_bound( 3 );
   cout << "The first element of multimap m1 with a key of 3 is: "
        << m1_RcIter -> second << "." << endl;

   // If no match is found for the key, end( ) is returned
   m1_RcIter = m1.lower_bound( 4 );

   if ( m1_RcIter == m1.end( ) )
      cout << "The multimap m1 doesn't have an element "
              << "with a key of 4." << endl;
   else
      cout << "The element of multimap m1 with a key of 4 is: "
                << m1_RcIter -> second << "." << endl;

   // The element at a specific location in the multimap can be
   // found using a dereferenced iterator addressing the location
   m1_AcIter = m1.end( );
   m1_AcIter--;
   m1_RcIter = m1.lower_bound( m1_AcIter -> first );
   cout << "The first element of m1 with a key matching\n"
        << "that of the last element is: "
        << m1_RcIter -> second << "." << endl;

   // Note that the first element with a key equal to
   // the key of the last element is not the last element
   if ( m1_RcIter == --m1.end( ) )
      cout << "This is the last element of multimap m1."
           << endl;
   else
      cout << "This is not the last element of multimap m1."
           << endl;
}
```

```Output
The element of multimap m1 with a key of 2 is: 20.
The first element of multimap m1 with a key of 3 is: 20.
The multimap m1 doesn't have an element with a key of 4.
The first element of m1 with a key matching
that of the last element is: 20.
This is not the last element of multimap m1.
```

## <a name="mapped_type"></a>  multimap::mapped_type

Typ, který představuje datový typ uložený v objektu multimap.

```cpp
typedef Type mapped_type;
```

### <a name="remarks"></a>Poznámky

`mapped_type` je synonymum pro parametr šablony `Type`.

Další informace o `Type` najdete v článku [multimap – třída](../standard-library/multimap-class.md) tématu.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [value_type](#value_type) příklad toho, jak deklarace a používání `key_type`.

## <a name="max_size"></a>  multimap::max_size

Vrátí maximální délku objektu multimap.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>Návratová hodnota

Maximální možná délka objektu multimap.

### <a name="example"></a>Příklad

```cpp
// multimap_max_size.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1;
   multimap <int, int> :: size_type i;

   i = m1.max_size( );
   cout << "The maximum possible length "
        << "of the multimap is " << i << "." << endl;
}
```

## <a name="multimap"></a>  multimap::multimap

Zkonstruuje objekt multimap, který je prázdný nebo který je kopií celého objektu multimap nebo části některého jiného objektu multimap.

```cpp
multimap();

explicit multimap(
    const Traits& Comp);

multimap(
    const Traits& Comp,
    const Allocator& Al);

map(
    const multimap& Right);

multimap(
    multimap&& Right);

multimap(
    initializer_list<value_type> IList);

multimap(
    initializer_list<value_type> IList,
    const Compare& Comp);

multimap(
    initializer_list<value_type> IList,
    const Compare& Comp,
    const Allocator& Al);

template <class InputIterator>
multimap(
 InputIterator First,
    InputIterator Last);

template <class InputIterator>
multimap(
 InputIterator First,
    InputIterator Last,
    const Traits& Comp);

template <class InputIterator>
multimap(
 InputIterator First,
    InputIterator Last,
    const Traits& Comp,
    const Allocator& Al);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|-|-|
|*Al*|Třída úložiště alokátoru pro použití s tímto objektem multimap, kterou je standardně třída Allocator.|
|*Kompozice*|Funkce porovnání typu `constTraits` používají k seřazení prvků v objektu map, kde je použit výchozí `Traits`.|
|*doprava*|Objekt map, ze kterého je kopií vytvořen objekt set.|
|*první*|Pozice prvního prvku v rozsahu prvků, které se mají zkopírovat.|
|*poslední*|Pozice prvního prvku mimo rozsah prvků, které se mají zkopírovat.|
|*IList*|Seznam initializer_list, ze kterého chcete kopírovat prvky.|

### <a name="remarks"></a>Poznámky

Všechny konstruktory ukládají typ objektu allocator, který spravuje úložiště paměti objektu multimap a který lze později vrátit voláním [get_allocator](#get_allocator). Parametr allocator je často v deklaraci třídy vynechán a makra předběžného zpracování jsou použita k nahrazení alternativních alokátorů.

Všechny konstruktory inicializují své objekty multimap.

Všechny konstruktory ukládají objekt funkce typu `Traits` , který slouží k vytvoření pořadí mezi klíči objektu multimap a který lze později vrátit voláním [key_comp](#key_comp).

První tři konstruktory určují prázdný počáteční objekt multimap, druhý určuje typ funkce porovnání (*kompozici*) který se má použít při stanovení pořadí prvků a třetí explicitně určuje typ alokátoru (*Al*) který se má použít. Klíčové slovo **explicitní** potlačí některé druhy automatického převodu typu.

Čtvrtý konstruktor určuje kopii objektu multimap *vpravo*.

Pátý konstruktor určuje kopii objektu multimap přesunutím *vpravo*.

Šestý, sedmý a osmý konstruktor kopírují členy objektu initializer_list.

Následující tři konstruktory kopírují rozsah `[First, Last)` objektu map se zvyšující se explicitností v určování typu funkce porovnání třídy `Traits` a alokátorem.

### <a name="example"></a>Příklad

```cpp
// multimap_ctor.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main()
{
    using namespace std;
    typedef pair <int, int> Int_Pair;

    // Create an empty multimap m0 of key type integer
    multimap <int, int> m0;

    // Create an empty multimap m1 with the key comparison
    // function of less than, then insert 4 elements
    multimap <int, int, less<int> > m1;
    m1.insert(Int_Pair(1, 10));
    m1.insert(Int_Pair(2, 20));
    m1.insert(Int_Pair(3, 30));
    m1.insert(Int_Pair(4, 40));

    // Create an empty multimap m2 with the key comparison
    // function of geater than, then insert 2 elements
    multimap <int, int, less<int> > m2;
    m2.insert(Int_Pair(1, 10));
    m2.insert(Int_Pair(2, 20));

    // Create a multimap m3 with the
    // allocator of multimap m1
    multimap <int, int>::allocator_type m1_Alloc;
    m1_Alloc = m1.get_allocator();
    multimap <int, int> m3(less<int>(), m1_Alloc);
    m3.insert(Int_Pair(3, 30));

    // Create a copy, multimap m4, of multimap m1
    multimap <int, int> m4(m1);

    // Create a multimap m5 by copying the range m1[ first,  last)
    multimap <int, int>::const_iterator m1_bcIter, m1_ecIter;
    m1_bcIter = m1.begin();
    m1_ecIter = m1.begin();
    m1_ecIter++;
    m1_ecIter++;
    multimap <int, int> m5(m1_bcIter, m1_ecIter);

    // Create a multimap m6 by copying the range m4[ first,  last)
    // and with the allocator of multimap m2
    multimap <int, int>::allocator_type m2_Alloc;
    m2_Alloc = m2.get_allocator();
    multimap <int, int> m6(m4.begin(), ++m4.begin(), less<int>(), m2_Alloc);

    cout << "m1 =";
    for (auto i : m1)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    cout << "m2 =";
    for (auto i : m2)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    cout << "m3 =";
    for (auto i : m3)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    cout << "m4 =";
    for (auto i : m4)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    cout << "m5 =";
    for (auto i : m5)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    cout << "m6 =";
    for (auto i : m6)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    // Create a multimap m8 by copying in an initializer_list
    multimap<int, int> m8{ { { 1, 1 }, { 2, 2 }, { 3, 3 }, { 4, 4 } } };
    cout << "m8: = ";
    for (auto i : m8)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    // Create a multimap m9 with an initializer_list and a comparator
    multimap<int, int> m9({ { 5, 5 }, { 6, 6 }, { 7, 7 }, { 8, 8 } }, less<int>());
    cout << "m9: = ";
    for (auto i : m9)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    // Create a multimap m10 with an initializer_list, a comparator, and an allocator
    multimap<int, int> m10({ { 9, 9 }, { 10, 10 }, { 11, 11 }, { 12, 12 } }, less<int>(), m9.get_allocator());
    cout << "m10: = ";
    for (auto i : m10)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

}

```

## <a name="op_eq"></a>  multimap::Operator =

Nahradí prvky objektu multimap kopií jiného objektu multimap.

```cpp
multimap& operator=(const multimap& right);

multimap& operator=(multimap&& right);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|-|-|
|*doprava*|[Multimap](../standard-library/multimap-class.md) kopírovaná do `multimap`.|

### <a name="remarks"></a>Poznámky

Po odstranění jakýchkoli prvků v `multimap`, `operator=` kopíruje nebo přesouvá obsah *správné* do `multimap`.

### <a name="example"></a>Příklad

```cpp
// multimap_operator_as.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
   {
   using namespace std;
   multimap<int, int> v1, v2, v3;
   multimap<int, int>::iterator iter;

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

## <a name="pointer"></a>  multimap::Pointer

Typ, který poskytuje ukazatel na prvek v objektu multimap.

```cpp
typedef typename allocator_type::pointer pointer;
```

### <a name="remarks"></a>Poznámky

Typ `pointer` lze použít ke změně hodnoty prvku.

Ve většině případů [iterátoru](#iterator) by měla sloužit pro přístup k prvkům v objektu multimap.

## <a name="rbegin"></a>  multimap::rbegin

Vrátí iterátor adresující první prvek v obráceném objektu multimap.

```cpp
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```

### <a name="return-value"></a>Návratová hodnota

Reverzní obousměrný iterátor adresující první prvek v obráceném objektu multimap nebo adresování, co bylo posledním prvkem v neobráceném objektu multimap.

### <a name="remarks"></a>Poznámky

`rbegin` se používá s obráceném objektu multimap stejně jako [začít](#begin) se používá s multimap.

Pokud návratová hodnota `rbegin` je přiřazena `const_reverse_iterator`, pak nelze upravit objekt multimap. Pokud návratová hodnota `rbegin` je přiřazena `reverse_iterator`, pak je možné upravit objektem multimap.

`rbegin` můžete použít k iteraci v rámci multimap zpětně.

### <a name="example"></a>Příklad

```cpp
// multimap_rbegin.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1;

   multimap <int, int> :: iterator m1_Iter;
   multimap <int, int> :: reverse_iterator m1_rIter;
   multimap <int, int> :: const_reverse_iterator m1_crIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );

   m1_rIter = m1.rbegin( );
   cout << "The first element of the reversed multimap m1 is "
        << m1_rIter -> first << "." << endl;

   // begin can be used to start an iteration
   // throught a multimap in a forward order
   cout << "The multimap is: ";
   for ( m1_Iter = m1.begin( ) ; m1_Iter != m1.end( ); m1_Iter++)
      cout << m1_Iter -> first << " ";
      cout << "." << endl;

   // rbegin can be used to start an iteration
   // throught a multimap in a reverse order
   cout << "The reversed multimap is: ";
   for ( m1_rIter = m1.rbegin( ) ; m1_rIter != m1.rend( ); m1_rIter++)
      cout << m1_rIter -> first << " ";
      cout << "." << endl;

   // A multimap element can be erased by dereferencing its key
   m1_rIter = m1.rbegin( );
   m1.erase ( m1_rIter -> first );

   m1_rIter = m1.rbegin( );
   cout << "After the erasure, the first element "
        << "in the reversed multimap is "
        << m1_rIter -> first << "." << endl;
}
```

```Output
The first element of the reversed multimap m1 is 3.
The multimap is: 1 2 3 .
The reversed multimap is: 3 2 1 .
After the erasure, the first element in the reversed multimap is 2.
```

## <a name="reference"></a>  multimap::Reference

Typ, který poskytuje odkaz na prvek uložený v objektu multimap.

```cpp
typedef typename allocator_type::reference reference;
```

### <a name="example"></a>Příklad

```cpp
// multimap_ref.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );

   // Declare and initialize a const_reference &Ref1
   // to the key of the first element
   const int &Ref1 = ( m1.begin( ) -> first );

   // The following line would cause an error because the
   // non-const_reference cannot be used to access the key
   // int &Ref1 = ( m1.begin( ) -> first );

   cout << "The key of first element in the multimap is "
        << Ref1 << "." << endl;

   // Declare and initialize a reference &Ref2
   // to the data value of the first element
   int &Ref2 = ( m1.begin( ) -> second );

   cout << "The data value of first element in the multimap is "
        << Ref2 << "." << endl;

   // The non-const_reference can be used to modify the
   // data value of the first element
   Ref2 = Ref2 + 5;
   cout << "The modified data value of first element is "
        << Ref2 << "." << endl;
}
```

```Output
The key of first element in the multimap is 1.
The data value of first element in the multimap is 10.
The modified data value of first element is 15.
```

## <a name="rend"></a>  multimap::rend

Vrátí iterátor adresující umístění následující po posledním prvku v obráceném objektu multimap.

```cpp
const_reverse_iterator rend() const;

reverse_iterator rend();
```

### <a name="return-value"></a>Návratová hodnota

Reverzní obousměrný iterátor adresující umístění následující po posledním prvku v obráceném objektu multimap (umístění, ke které došlo před první prvek v neobráceném multimap).

### <a name="remarks"></a>Poznámky

`rend` se používá s obráceném objektu multimap stejně jako [end](../standard-library/map-class.md#end) se používá s multimap.

Pokud návratová hodnota `rend` je přiřazena `const_reverse_iterator`, pak nelze upravit objekt multimap. Pokud návratová hodnota `rend` je přiřazena `reverse_iterator`, pak je možné upravit objektem multimap.

`rend` slouží k otestování pro Určuje, zda zpětný iterátor dosáhl konce jeho objektu multimap.

Hodnota vrácená `rend` by neměla být dereferencována.

### <a name="example"></a>Příklad

```cpp
// multimap_rend.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1;

   multimap <int, int> :: iterator m1_Iter;
   multimap <int, int> :: reverse_iterator m1_rIter;
   multimap <int, int> :: const_reverse_iterator m1_crIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );

   m1_rIter = m1.rend( );
   m1_rIter--;
   cout << "The last element of the reversed multimap m1 is "
        << m1_rIter -> first << "." << endl;

   // begin can be used to start an iteration
   // throught a multimap in a forward order
   cout << "The multimap is: ";
   for ( m1_Iter = m1.begin( ) ; m1_Iter != m1.end( ); m1_Iter++)
      cout << m1_Iter -> first << " ";
      cout << "." << endl;

   // rbegin can be used to start an iteration
   // throught a multimap in a reverse order
   cout << "The reversed multimap is: ";
   for ( m1_rIter = m1.rbegin( ) ; m1_rIter != m1.rend( ); m1_rIter++)
      cout << m1_rIter -> first << " ";
      cout << "." << endl;

   // A multimap element can be erased by dereferencing to its key
   m1_rIter = --m1.rend( );
   m1.erase ( m1_rIter -> first );

   m1_rIter = m1.rend( );
   m1_rIter--;
   cout << "After the erasure, the last element "
        << "in the reversed multimap is "
        << m1_rIter -> first << "." << endl;
}
```

```Output
The last element of the reversed multimap m1 is 1.
The multimap is: 1 2 3 .
The reversed multimap is: 3 2 1 .
After the erasure, the last element in the reversed multimap is 2.
```

## <a name="reverse_iterator"></a>  multimap::reverse_iterator

Typ, který poskytuje obousměrný iterátor, který může číst nebo upravovat prvek v obráceném objektu multimap.

```cpp
typedef std::reverse_iterator<iterator> reverse_iterator;
```

### <a name="remarks"></a>Poznámky

Typ `reverse_iterator` se používá k iteraci v rámci objektu multimap, v opačném pořadí.

`reverse_iterator` Určené multimap – odkazuje na objekty [value_type](#value_type), které jsou typu `pair<const Key, Type>`. Hodnota klíče je k dispozici prostřednictvím první pár členů, hodnota elementu pro mapovanou je k dispozici druhý člen, které odpovídá páru licencí.

Ke zrušení `reverse_iterator` *rIter* odkazující na prvek v objektu multimap, použijte **->** operátor.

Chcete-li přistupovat k hodnotě klíče pro element, použijte `rIter->first`, což je totéž jako `(*rIter).first`. Chcete-li získat přístup k hodnotě z namapované datum pro element, použijte `rIter->second`, což je totéž jako `(*rIter).second`.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [rbegin –](#rbegin) příklad toho, jak deklarace a používání `reverse_iterator`.

## <a name="size"></a>  multimap::size

Vrátí počet prvků v objektu multimap.

```cpp
size_type size() const;
```

### <a name="return-value"></a>Návratová hodnota

Aktuální délka objektu multimap.

### <a name="example"></a>Příklad

Následující příklad ukazuje použití multimap::size členskou funkci.

```cpp
// multimap_size.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main()
{
    using namespace std;
    multimap<int, int> m1, m2;
    multimap<int, int>::size_type i;
    typedef pair<int, int> Int_Pair;

    m1.insert(Int_Pair(1, 1));
    i = m1.size();
    cout << "The multimap length is " << i << "." << endl;

    m1.insert(Int_Pair(2, 4));
    i = m1.size();
    cout << "The multimap length is now " << i << "." << endl;
}
```

```Output
The multimap length is 1.
The multimap length is now 2.
```

## <a name="size_type"></a>  multimap::size_type

Typ unsigned integer, která vrátí počet prvků v objektu multimap.

```cpp
typedef typename allocator_type::size_type size_type;
```

### <a name="example"></a>Příklad

Podívejte se na příklad pro [velikost](#size) příklad toho, jak deklarace a používání `size_type`

## <a name="swap"></a>  multimap::swap

Vymění prvky dvou multimaps.

```cpp
void swap(
    multimap<Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*doprava*<br/>
 Multimap poskytující prvky pro záměnu nebo objektu multimap, jehož prvky mají být zaměněny objektu multimap `left`.

### <a name="remarks"></a>Poznámky

Žádné odkazy, ukazatele nebo iterátory, které určují prvky ve dvou multimaps, jehož prvky jsou během výměny nezruší platnost členskou funkci.

### <a name="example"></a>Příklad

```cpp
// multimap_swap.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1, m2, m3;
   multimap <int, int>::iterator m1_Iter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );
   m2.insert ( Int_Pair ( 10, 100 ) );
   m2.insert ( Int_Pair ( 20, 200 ) );
   m3.insert ( Int_Pair ( 30, 300 ) );

   cout << "The original multimap m1 is:";
   for ( m1_Iter = m1.begin( ); m1_Iter != m1.end( ); m1_Iter++ )
      cout << " " << m1_Iter -> second;
   cout   << "." << endl;

   // This is the member function version of swap
   m1.swap( m2 );

   cout << "After swapping with m2, multimap m1 is:";
   for ( m1_Iter = m1.begin( ); m1_Iter != m1.end( ); m1_Iter++ )
      cout << " " << m1_Iter -> second;
   cout  << "." << endl;

   // This is the specialized template version of swap
   swap( m1, m3 );

   cout << "After swapping with m3, multimap m1 is:";
   for ( m1_Iter = m1.begin( ); m1_Iter != m1.end( ); m1_Iter++ )
      cout << " " << m1_Iter -> second;
   cout   << "." << endl;
}
```

```Output
The original multimap m1 is: 10 20 30.
After swapping with m2, multimap m1 is: 100 200.
After swapping with m3, multimap m1 is: 300.
```

## <a name="upper_bound"></a>  multimap::upper_bound

Vrátí iterátor na první prvek v objektu multimap, který s klíčem, který je větší než zadaný klíč.

```cpp
iterator upper_bound(const Key& key);

const_iterator upper_bound(const Key& key) const;
```

### <a name="parameters"></a>Parametry

*Klíč*<br/>
 Klíč argumentu k porovnání s klíči řazení prvek z objektu multimap vyhledaly.

### <a name="return-value"></a>Návratová hodnota

Iterátor nebo `const_iterator` adresy umístění prvku v objektu multimap, s klíčem, který je větší než tento klíč argument nebo který adresuje umístění následující po posledním prvku v objektu multimap, pokud žádné odpovídají je nalezen klíč.

Pokud vrácená hodnota je přiřazena k `const_iterator`, nelze upravit objekt multimap. Pokud vrácená hodnota je přiřazena k `iterator`, je možné upravit objektem multimap.

### <a name="example"></a>Příklad

```cpp
// multimap_upper_bound.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1;
   multimap <int, int> :: const_iterator m1_AcIter, m1_RcIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );
   m1.insert ( Int_Pair ( 3, 40 ) );

   m1_RcIter = m1.upper_bound( 1 );
   cout << "The 1st element of multimap m1 with "
        << "a key greater than 1 is: "
        << m1_RcIter -> second << "." << endl;

   m1_RcIter = m1.upper_bound( 2 );
   cout << "The first element of multimap m1 with a key "
        << " greater than 2 is: "
        << m1_RcIter -> second << "." << endl;

   // If no match is found for the key, end( ) is returned
   m1_RcIter = m1.lower_bound( 4 );

   if ( m1_RcIter == m1.end( ) )
      cout << "The multimap m1 doesn't have an element "
           << "with a key of 4." << endl;
   else
      cout << "The element of multimap m1 with a key of 4 is: "
           << m1_RcIter -> second << "." << endl;

   // The element at a specific location in the multimap can be
   // found using a derefenced iterator addressing the location
   m1_AcIter = m1.begin( );
   m1_RcIter = m1.upper_bound( m1_AcIter -> first );
   cout << "The first element of m1 with a key greater than\n"
        << "that of the initial element of m1 is: "
        << m1_RcIter -> second << "." << endl;
}
```

```Output
The 1st element of multimap m1 with a key greater than 1 is: 20.
The first element of multimap m1 with a key  greater than 2 is: 30.
The multimap m1 doesn't have an element with a key of 4.
The first element of m1 with a key greater than
that of the initial element of m1 is: 20.
```

## <a name="value_comp"></a>  multimap::value_comp

Členská funkce vrátí objekt funkce, která určuje pořadí prvků v objektu multimap porovnáním jejich hodnoty klíče.

```cpp
value_compare value_comp() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí objekt funkce porovnání, která používá multimap řazení jeho prvků.

### <a name="remarks"></a>Poznámky

Pro multimap *m*, pokud dva prvky *e*1 ( *k*1, *d*1) a *e*2 ( *k*2, `d`2) jsou objekty typu `value_type`, kde *k*1 a *k*2 jsou jejich klíče typu `key_type` a `d`1 a `d`2 jsou jejich data typu `mapped_type`, pak *m.*`value_comp`( *e*1, *e*2) je ekvivalentní *m.* `key_comp` ( *k*1, *k*2).

### <a name="example"></a>Příklad

```cpp
// multimap_value_comp.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;

   multimap <int, int, less<int> > m1;
   multimap <int, int, less<int> >::value_compare vc1 = m1.value_comp( );
   multimap<int,int>::iterator Iter1, Iter2;

   Iter1= m1.insert ( multimap <int, int> :: value_type ( 1, 10 ) );
   Iter2= m1.insert ( multimap <int, int> :: value_type ( 2, 5 ) );

   if( vc1( *Iter1, *Iter2 ) == true )
   {
      cout << "The element ( 1,10 ) precedes the element ( 2,5 )."
           << endl;
   }
   else
   {
      cout << "The element ( 1,10 ) does "
           << "not precede the element ( 2,5 )."
           << endl;
   }

   if( vc1( *Iter2, *Iter1 ) == true )
   {
      cout << "The element ( 2,5 ) precedes the element ( 1,10 )."
           << endl;
   }
   else
   {
      cout << "The element ( 2,5 ) does "
           << "not precede the element ( 1,10 )."
           << endl;
   }
}
```

```Output
The element ( 1,10 ) precedes the element ( 2,5 ).
The element ( 2,5 ) does not precede the element ( 1,10 ).
```

## <a name="value_type"></a>  multimap::value_type

Typ, který představuje typ objektu uložený jako prvek v objektu map.

```cpp
typedef pair<const Key, Type> value_type;
```

### <a name="example"></a>Příklad

```cpp
// multimap_value_type.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   typedef pair <const int, int> cInt2Int;
   multimap <int, int> m1;
   multimap <int, int> :: key_type key1;
   multimap <int, int> :: mapped_type mapped1;
   multimap <int, int> :: value_type value1;
   multimap <int, int> :: iterator pIter;

   // value_type can be used to pass the correct type
   // explicitely to avoid implicit type conversion
   m1.insert ( multimap <int, int> :: value_type ( 1, 10 ) );

   // Compare another way to insert objects into a hash_multimap
   m1.insert ( cInt2Int ( 2, 20 ) );

   // Initializing key1 and mapped1
   key1 = ( m1.begin( ) -> first );
   mapped1 = ( m1.begin( ) -> second );

   cout << "The key of first element in the multimap is "
        << key1 << "." << endl;

   cout << "The data value of first element in the multimap is "
        << mapped1 << "." << endl;

   // The following line would cause an error because
   // the value_type is not assignable
   // value1 = cInt2Int ( 4, 40 );

   cout  << "The keys of the mapped elements are:";
   for ( pIter = m1.begin( ) ; pIter != m1.end( ) ; pIter++ )
      cout << " " << pIter -> first;
   cout << "." << endl;

   cout  << "The values of the mapped elements are:";
   for ( pIter = m1.begin( ) ; pIter != m1.end( ) ; pIter++ )
      cout << " " << pIter -> second;
   cout << "." << endl;
}
```

```Output
The key of first element in the multimap is 1.
The data value of first element in the multimap is 10.
The keys of the mapped elements are: 1 2.
The values of the mapped elements are: 10 20.
```

## <a name="see-also"></a>Viz také:

[Kontejnery](../cpp/containers-modern-cpp.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)<br/>
