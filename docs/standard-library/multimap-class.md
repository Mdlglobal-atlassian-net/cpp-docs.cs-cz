---
title: multimap – třída | Microsoft Docs
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
ms.openlocfilehash: 863d0c84d772de389affc8167e3a0f69b0e0fabe
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="multimap-class"></a>multimap – třída

Standardní knihovna C++ multimap – třída se používá pro ukládání a načítání dat z kolekce, ve kterém je každý prvek pár, který má hodnotu data a klíč řazení. Hodnota klíče nemusí být jedinečná a je použita k automatickému seřazení dat. Hodnotu prvku v objektu multimap, ale ne jeho přidruženou hodnotu klíče, lze změnit přímo. Namísto toho hodnoty klíčů přidružené ke starým prvkům musí být odstraněny a vloženy nové hodnoty klíče související s novými prvky.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Key,
    class Type,
    class Traits=less <Key>,
    class Allocator=allocator <pair  <const Key, Type>>>
class multimap;
```

### <a name="parameters"></a>Parametry

`Key` Typ klíče dat k uložení do multimap.

`Type` Datový typ elementu k uložení do multimap.

`Traits` Typ, který poskytuje funkce objekt, který můžete porovnat dvě hodnoty element jako klíči řazení určit jejich relativní pořadí v multimap. Binární predikát `less<Key>` je výchozí hodnota.

V C ++ 14 můžete povolit heterogenní vyhledávání zadáním `std::less<>` nebo `std::greater<>` predikát, který nemá žádné parametry typu. Další informace najdete v tématu [heterogenní vyhledávání v asociativní kontejnery](../standard-library/stl-containers.md#sequence_containers)

`Allocator` Typ, který představuje uložené allocator objekt, který zapouzdřuje podrobnosti o přidělení a zrušení přidělení paměti na mapě. Tento argument je volitelný a výchozí hodnota je `allocator<pair <const Key, Type> >`.

## <a name="remarks"></a>Poznámky

Je standardní knihovna C++ multimap – třída

- Asociativní kontejner, což je kontejner proměnné velikosti, který podporuje efektivní načtení hodnoty prvku založené na přiřazené hodnotě klíče.

- Oboustranný, protože poskytuje obousměrné iterátory pro přístup k jeho prvkům.

- Seřazený, protože jeho prvky jsou řazeny podle hodnot klíče v kontejneru podle zadané porovnávací funkce.

- Vícenásobný, protože je prvky nemusí mít jedinečné klíče, takže jedna hodnota klíče může mít k sobě přidružených mnoho datových hodnot prvků.

- Kontejner asociativních párů, protože jeho prvky hodnoty dat se liší od hodnot klíčů.

- Třída šablony, protože poskytuje obecné funkce a to nezávisle na určitém typu dat obsažených jako prvky nebo klíče. Datové typy použité pro prvky a klíče jsou místo toho zadány jako parametry v šabloně třídy společně s funkcí porovnání a alokátorem.

Iterator poskytuje třídu mapy je obousměrný iterator, ale členské funkce tříd [vložit](#insert) a [multimap](#multimap) mají verze, které jako parametry šablony trvat slabší vstupní iterator, jejichž požadavky na funkce jsou minimální více než ty, které zaručit třídou iterátory obousměrné. Různé koncepty iterátorů tvoří rodinu týkající se upřesnění jejich funkčnosti. Každý koncept iterátoru má vlastní sadu požadavků a algoritmy, které s nimi pracují, musí omezit jejich předpoklady na požadavky podle typu iterátoru. Lze předpokládat, že ke vstupnímu iterátoru lze přistoupit přes ukazatel pro odkazování na některý objekt a že může být zvýšen na další iterátor v pořadí. Toto je minimální sadu funkcí, které, ale stačí mohli srozumitelně mluvit o rozsah iterátory `[First, Last)` v kontextu třídy členské funkce.

Volba typu kontejneru by měla obecně vycházet z typu vyhledávání a vkládání vyžadovaného aplikací. Asociativní kontejnery jsou optimalizovány pro operace vyhledávání, vkládání a odstranění. Členské funkce, které explicitně podporují tyto operace, jsou efektivní a jsou prováděny v čase, který je průměrně úměrný logaritmu počtu prvků v kontejneru. Vkládání prvků nezruší platnost žádných iterátorů a odstranění prvků zruší platnost pouze těch iterátorů, které výslovně odkazovaly na odstraněné prvky.

Objekt multimap by měl být asociativní kontejner dle výběru, kdy jsou podmínky přiřazení hodnot k jejich klíčům splněny aplikací. Model pro tento typ struktury je uspořádaný seznam klíčových slov s přidruženými řetězcovými hodnotami poskytujícími (řekněme) definice, kde slova nebyla vždy jednoznačně definována. Pokud místo toho klíčová slova byla jedinečně definovaná tak, aby byly klíče jedinečné, bude objekt map správným kontejnerem výběru. Naopak pokud je pouze uložen seznam slov, bude objekt set tím správným kontejnerem. Pokud bylo povoleno více výskytů jednoho slova, je objekt multiset odpovídající strukturou kontejneru.

Multimap řadí pořadí jimi řídí voláním funkce uložené objektu typu [key_compare –](#key_compare). Tento objekt uložené je porovnání funkce, která může získat přístup k voláním členské funkce [key_comp –](#key_comp). Obecně, tyto prvky musí být menší než srovnatelné pro toto pořadí, což znamená, že když jsou uvedeny dva prvky, může být stanoveno, zda jsou ekvivalentní (v tom smyslu, že ani jeden není menší než ten druhý), nebo že jeden je menší než druhý. To má za výsledek řazení mezi neekvivalentními prvky. Technicky je funkce porovnání binárním predikátem, který indukuje přísné slabé řazení, standardním matematickým způsobem. Predikát binární `f(x,y)` je objekt funkce, která má dva objekty argument `x` a `y` a návratovou hodnotu PRAVDA nebo NEPRAVDA. Řazení vynucená pro sadu je striktní weak řazení Pokud binární predikát je Nereflexivní, antisymetrického a přenositelné a pokud ekvivalenční přenositelné, kde dva objekty `x` a `y` jsou definovány jako ekvivalentní při obou `f(x,y)`a `f(y,x)` jsou false. Pokud silnější podmínka rovnosti mezi klíči nahradí ekvivalenci, stane se pořadí celkovým (v tom smyslu, že všechny prvky jsou uspořádány ve vztahu k sobě navzájem) a odpovídající klíče budou od sebe nerozeznatelné.

V C ++ 14 můžete povolit heterogenní vyhledávání zadáním `std::less<>` nebo `std::greater<>` predikát, který nemá žádné parametry typu. Další informace najdete v tématu [heterogenní vyhledávání v asociativní kontejnery](../standard-library/stl-containers.md#sequence_containers)

## <a name="members"></a>Členové

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[multimap](#multimap)|Vytvoří `multimap` který je prázdný nebo který je kopie všech nebo některých jiných součástí `multimap`.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[allocator_type –](#allocator_type)|Typ, který reprezentuje `allocator` třídy pro `multimap` objektu.|
|[const_iterator](#const_iterator)|Typ, který poskytuje obousměrné iterator, který může číst `const` element v `multimap`.|
|[const_pointer](#const_pointer)|Typ, který poskytuje odkazy `const` element v `multimap`.|
|[const_reference](#const_reference)|Typ, který obsahuje odkaz na `const` element uložené v `multimap` pro čtení a provádění `const` operace.|
|[const_reverse_iterator](#const_reverse_iterator)|Typ, který poskytuje obousměrné iterator, který může číst všechny `const` element v `multimap`.|
|[difference_type](#difference_type)|Typ se znaménkem, který můžete použít k reprezentování počet prvků `multimap` v rozsahu mezi elementy, na kterou iterátory odkazuje.|
|[Iterator](#iterator)|Typ, který poskytuje rozdíl mezi dvěma iterátory, které odkazují na elementy v téže `multimap`.|
|[key_compare](#key_compare)|Typ, který poskytuje funkce objekt, který můžete porovnat dva klíče řazení k určení relativních pořadí dva elementy v `multimap`.|
|[key_type](#key_type)|Typ, který popisuje řazení klíče objektu, která se považuje za každý element `multimap`.|
|[mapped_type](#mapped_type)|Typ, který představuje typ data uložená v `multimap`.|
|[Ukazatele](#pointer)|Typ, který poskytuje odkazy `const` element v `multimap`.|
|[Referenční dokumentace](#reference)|Typ, který obsahuje odkaz na element uložené v `multimap`.|
|[reverse_iterator](#reverse_iterator)|Typ, který poskytuje obousměrné iterator, které můžou číst nebo upravte element v odstínech `multimap`.|
|[size_type](#size_type)|Typ celé číslo bez znaménka, který poskytuje odkazy `const` element v `multimap`.|
|[value_type](#value_type)|Typ, který poskytuje funkce objekt, který můžete porovnat dva elementy jako klíči řazení určit jejich relativní pořadí v `multimap`.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[Začátek](#begin)|Vrátí iterovat adresování prvním elementem v `multimap`.|
|[cbegin –](#cbegin)|Vrátí const iterator adresování prvním elementem v `multimap`.|
|[cend –](#cend)|Vrátí const iterator, která řeší úspěšné posledním prvkem v umístění `multimap`.|
|[Zrušte zaškrtnutí](#clear)|Vymaže všechny elementy `multimap`.|
|[Počet](#count)|Vrátí počet prvků v `multimap` jejichž klíč odpovídá parametru zadaný klíč.|
|[crbegin](#crbegin)|Vrátí const iterator adresování prvním elementem v odstínech `multimap`.|
|[crend –](#crend)|Vrátí const iterator, která řeší umístění úspěšné posledním prvkem v odstínech `multimap`.|
|[emplace –](#emplace)|Vloží element v místě do zkonstruovat `multimap`.|
|[emplace_hint –](#emplace_hint)|Vloží element v místě do zkonstruovat `multimap`, s pomocným parametrem umístění|
|[prázdný](#empty)|Pokud testy `multimap` je prázdný.|
|[End](#end)|Vrátí iterátor, který řeší úspěšné posledním prvkem v umístění `multimap`.|
|[equal_range](#equal_range)|Vyhledá rozsahu prvků, kde klíče prvku odpovídají zadané hodnotě.|
|[vymazání](#erase)|Odebere element nebo rozsah elementů v `multimap` ze zadaných pozic nebo odebere elementy, které odpovídají zadaným klíčem.|
|[Najít](#find)|Vrátí iterovat adresování elementu v první oblasti `multimap` který má klíč ekvivalentní k zadanému klíči.|
|[get_allocator](#get_allocator)|Vrátí kopii `allocator` objekt použitý k vytvoření `multimap`.|
|[Vložení](#insert)|Vloží elementu nebo rozsahu prvků do `multimap`.|
|[key_comp](#key_comp)|Načte kopii porovnání objekt použitý k pořadí klíčů v `multimap`.|
|[lower_bound –](#lower_bound)|Vrátí iterovat prvním elementem v `multimap` , s klíčem, který je rovna nebo větší než je zadaný klíč.|
|[max_size](#max_size)|Vrátí maximální délka `multimap`.|
|[rbegin –](#rbegin)|Vrátí iterovat adresování prvním elementem v odstínech `multimap`.|
|[rend –](#rend)|Vrátí iterátor, který řeší umístění úspěšné posledním prvkem v odstínech `multimap`.|
|[Velikost](#size)|Vrátí počet prvků v `multimap`.|
|[Swap](#swap)|Výměny dva elementy `multimap`s.|
|[upper_bound –](#upper_bound)|Vrátí iterovat prvním elementem v `multimap` , s klíčem, který je větší než je zadaný klíč.|
|[value_comp](#value_comp)|Členská funkce vrátí objekt funkce, který určuje pořadí prvků v `multimap` tak, že porovnáte jejich hodnoty klíče.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operátor =](#op_eq)|Nahradí elementy `multimap` kopii jiného `multimap`.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<mapy >

**Namespace:** – std

( **Klíč**, **hodnotu**) páry jsou uložené v multimap jako objekty typu `pair`. Pair – třída vyžaduje hlavičku \<nástroj >, které je součástí automaticky podle \<mapy >.

## <a name="allocator_type"></a>  multimap::allocator_type

Typ, který reprezentuje allocator – třída multimap objektu.

```cpp
typedef Allocator allocator_type;
```

### <a name="example"></a>Příklad

Podívejte se na příklad pro [get_allocator –](#get_allocator) pro příklad použití `allocator_type`.

## <a name="begin"></a>  multimap::begin

Vrátí iterator adresování prvním elementem v multimap.

```cpp
const_iterator begin() const;

iterator begin();
```

### <a name="return-value"></a>Návratová hodnota

Adresování prvním elementem v multimap nebo umístění úspěšné prázdný multimap iterator obousměrné.

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

Vrátí `const` iterator, která řeší prvním elementem v rozsahu.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>Návratová hodnota

A `const` iterator obousměrného přístup, který odkazuje na první prvek rozsahu nebo umístění právě přesahuje za konec prázdného rozsahu (pro prázdného rozsahu, `cbegin() == cend()`).

### <a name="remarks"></a>Poznámky

S návratovou hodnotou `cbegin`, nemůže být upravena elementů v rozsahu.

Můžete použít tuto funkci člen místě `begin()` – členská funkce zaručit, že je návratovou hodnotu `const_iterator`. Obvykle se používá ve spojení s [automaticky](../cpp/auto-cpp.md) odvození – klíčové slovo, zadejte, jak je znázorněno v následujícím příkladu. V příkladu, vezměte v úvahu `Container` upravitelná (jinou hodnotu než `const`) kontejneru libovolného typu, který podporuje `begin()` a `cbegin()`.

```cpp
auto i1 = Container.begin();
// i1 is Container<T>::iterator
auto i2 = Container.cbegin();

// i2 is Container<T>::const_iterator
```

## <a name="cend"></a>  multimap::cend

Vrátí `const` iterator, která řeší umístění bezprostředně za posledním prvkem v rozsahu.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>Návratová hodnota

A `const` iterator obousměrného přístup, který odkazuje právě přesahuje za konec rozsahu.

### <a name="remarks"></a>Poznámky

`cend` slouží k ověření, zda iterovat uplynutí konec její rozsah.

Můžete použít tuto funkci člen místě `end()` – členská funkce zaručit, že je návratovou hodnotu `const_iterator`. Obvykle se používá ve spojení s [automaticky](../cpp/auto-cpp.md) odvození – klíčové slovo, zadejte, jak je znázorněno v následujícím příkladu. V příkladu, vezměte v úvahu `Container` upravitelná (jinou hodnotu než `const`) kontejneru libovolného typu, který podporuje `end()` a `cend()`.

```cpp
auto i1 = Container.end();
// i1 is Container<T>::iterator
auto i2 = Container.cend();

// i2 is Container<T>::const_iterator
```

Hodnoty vrácené `cend` by neměl být vyhodnoceny odkazy.

## <a name="clear"></a>  multimap::clear

Vymaže všechny elementy multimap.

```cpp
void clear();
```

### <a name="example"></a>Příklad

Následující příklad ukazuje použití multimap::clear – členská funkce.

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

Typ, který poskytuje obousměrné iterator, který může číst **const** element v multimap.

```cpp
typedef implementation-defined const_iterator;
```

### <a name="remarks"></a>Poznámky

Typ `const_iterator` nelze použít k úpravě hodnota elementu.

`const_iterator` Definovaný multimap body objektů [value_type](#value_type), které jsou typu `pair` * \< * **const klíč**, **Typ *** >*. Hodnota klíče je k dispozici prostřednictvím první člen pár a hodnota namapované elementu je k dispozici prostřednictvím druhý člen, které odpovídá páru.

K dereference `const_iterator` `cIter` odkazující na element v multimap, použijte **->** operátor.

Chcete-li získat přístup k hodnotě klíče pro element, použijte `cIter`  ->  **první**, což je totéž jako (\* `cIter`). **první**. Chcete-li získat přístup k hodnotě namapované datum pro element, použijte `cIter`  ->  **druhý**, což je totéž jako (\* `cIter`). **druhý**.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [začít](#begin) pro příklad použití `const_iterator`.

## <a name="const_pointer"></a>  multimap::const_pointer

Typ, který poskytuje odkazy **const** element v multimap.

```cpp
typedef typename allocator_type::const_pointer const_pointer;
```

### <a name="remarks"></a>Poznámky

Typ `const_pointer` nelze použít k úpravě hodnota elementu.

Ve většině případů [iterator](#iterator) se má použít pro přístup k elementům v multimap objektu.

## <a name="const_reference"></a>  multimap::const_reference

Typ, který obsahuje odkaz na **const** element uložené v multimap pro čtení a provádění **const** operace.

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

Typ, který poskytuje obousměrné iterator, který může číst všechny **const** element v multimap.

```cpp
typedef std::reverse_iterator<const_iterator> const_reverse_iterator;
```

### <a name="remarks"></a>Poznámky

Typ `const_reverse_iterator` nelze změnit hodnotu elementu a je použít k iteraci v rámci multimap pozpátku.

`const_reverse_iterator` Definovaný multimap body objektů [value_type](#value_type), které jsou typu `pair` * \< * **const klíč**, **Typ *** >*. Hodnota klíče je k dispozici prostřednictvím první člen pár a hodnota namapované elementu je k dispozici prostřednictvím druhý člen, které odpovídá páru.

K dereference `const_reverse_iterator` `crIter` odkazující na element v multimap, použijte **->** operátor.

Chcete-li získat přístup k hodnotě klíče pro element, použijte `crIter`  ->  **první**, což je totéž jako (\* `crIter`). **první**. Chcete-li získat přístup k hodnotě namapované datum pro element, použijte `crIter`  ->  **druhý**, což je totéž jako (\* `crIter`). **první**.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [rend](#rend) příklad toho, jak deklarace a používání `const_reverse_iterator`.

## <a name="count"></a>  multimap::Count

Vrátí počet prvků v multimap, jejichž klíče shodují parametr zadaný klíč.

```cpp
size_type count(const Key& key) const;
```

### <a name="parameters"></a>Parametry

`key` Klíč elementy lze porovnat z multimap.

### <a name="return-value"></a>Návratová hodnota

Počet elementů, jejichž řazení klíče shodují klíč parametru; 0, pokud multimap neobsahuje element s odpovídající klíč.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí počet prvků v rozsahu

[ `lower_bound` (_ *Klíč* ), `upper_bound` (\_ *klíč* ))

které mají hodnotu klíče `key`.

### <a name="example"></a>Příklad

Následující příklad ukazuje použití multimap::count – členská funkce.

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

Vrátí const iterator adresování prvním elementem v invertovaných multimap.

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>Návratová hodnota

Const reverse obousměrného iterator adresování prvním elementem v odstínech [multimap](../standard-library/multimap-class.md) nebo řešení, co je posledním prvkem v unreversed `multimap`.

### <a name="remarks"></a>Poznámky

`crbegin` se používá s odstínech `multimap` stejně jako [začít](#begin) se používá s `multimap`.

S návratovou hodnotou `crbegin`, `multimap` objekt nelze změnit.

`crbegin` lze použít k iteraci v rámci `multimap` zpětné.

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

Vrátí const iterator, která řeší úspěšné posledním prvkem v invertovaných multimap umístění.

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>Návratová hodnota

Const reverse iterator obousměrného, která řeší umístění úspěšné posledním prvkem v odstínech [multimap](../standard-library/multimap-class.md) (umístění, které měl před prvním elementem v unreversed `multimap`).

### <a name="remarks"></a>Poznámky

`crend` se používá s odstínech `multimap` stejně jako [multimap::end](#end) se používá s `multimap`.

S návratovou hodnotou `crend`, `multimap` objekt nelze změnit.

`crend` můžete použít k testování na tom, jestli má zpětné iterator dosáhla konce jeho `multimap`.

Hodnoty vrácené `crend` by neměl být vyhodnoceny odkazy.

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

Typ se znaménkem, který můžete použít k reprezentování počet elementů multimap v rozsahu mezi elementy, na kterou iterátory odkazuje.

```cpp
typedef typename allocator_type::difference_type difference_type;
```

### <a name="remarks"></a>Poznámky

`difference_type` Je typ vrácena, pokud odečtením nebo zvyšování prostřednictvím iterátory kontejneru. `difference_type` Se obvykle používá k reprezentování počet elementů v rozsahu [*první*, *poslední*) mezi iterátory `first` a `last`, obsahuje element, který ukazuje podle `first` a rozsah elementy až do, ale bez zahrnutí elementu na kterou odkazuje `last`.

Všimněte si, že i když `difference_type` je k dispozici pro všechny iterátory, které splňují požadavky vstupní iterator, který obsahuje třídu obousměrného iterátory nepodporuje reverzibilního kontejnery, jako je sada, odčítání mezi iterátory pouze iterátory náhodný přístup poskytuje náhodný přístup kontejner například vektoru podporována.

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

Vloží element sestavený na místě (žádné kopírování nebo přesunutí operací).

```cpp
template <class... Args>
iterator emplace(Args&&... args);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|-|-|
|`args`|Argumenty předané vytvořit element, který má být vložen do multimap.|

### <a name="return-value"></a>Návratová hodnota

Iterátor do nově vloženou elementu.

### <a name="remarks"></a>Poznámky

Pomocí této funkce jsou zneplatněny žádné odkazy na elementy kontejnerů, ale může ho zneplatnit všechny iterátory do kontejneru.

Pokud je vyvolána výjimka při vložení, je ponechán kontejneru v nezměněném stavu a je znovu vyvolány výjimku.

[Value_type](../standard-library/map-class.md#value_type) elementu je pár, aby bude použita hodnota elementu dvojici seřazené s první součást, která je rovna hodnotě klíče a druhá součást, která je rovna hodnotě dat prvku.

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

Vloží element sestavený na místě (žádné kopírování nebo přesunutí operací), s pomocným parametrem umístění.

```cpp
template <class... Args>
iterator emplace_hint(
    const_iterator where,
    Args&&... args);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|-|-|
|`args`|Argumenty předané vytvořit element, který má být vložen do multimap.|
|`where`|Místo zahájení vyhledání správného bodu vložení. (Pokud tento bod okamžitě předchází `where`, vložení se může objevit v amortizovaný konstantní čas místo logaritmické času.)|

### <a name="return-value"></a>Návratová hodnota

Iterátor do nově vloženou elementu.

### <a name="remarks"></a>Poznámky

Pomocí této funkce jsou zneplatněny žádné odkazy na elementy kontejnerů, ale může ho zneplatnit všechny iterátory do kontejneru.

Během. uložení Pokud je vyvolána výjimka, stavu kontejneru nezměnil.

[Value_type](../standard-library/map-class.md#value_type) elementu je pár, aby bude použita hodnota elementu dvojici seřazené s první součást, která je rovna hodnotě klíče a druhá součást, která je rovna hodnotě dat prvku.

Příklad kódu, najdete v části [map::emplace_hint](../standard-library/map-class.md#emplace_hint).

## <a name="empty"></a>  multimap::Empty

Testy, pokud multimap je prázdný.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE,** Pokud multimap je prázdná. **false** Pokud je multimap neprázdný.

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

Iterator minulosti the-end. Pokud multimap je prázdný, pak `multimap::end() == multimap::begin()`.

### <a name="remarks"></a>Poznámky

**end** slouží k otestování, jestli iterovat uplynutí konec jeho multimap.

Hodnoty vrácené **end** by neměl být vyhodnoceny odkazy.

Příklad kódu, najdete v části [multimap::find](#find).

## <a name="equal_range"></a>  multimap::equal_range

Vyhledá rozsahu prvků, kde klíče prvku odpovídají zadané hodnotě.

```cpp
pair <const_iterator, const_iterator> equal_range (const Key& key) const;

pair <iterator, iterator> equal_range (const Key& key);
```

### <a name="parameters"></a>Parametry

`key` Argument klíč, který se má porovnat s klíč řazení elementu z multimap prohledávaný.

### <a name="return-value"></a>Návratová hodnota

Pár iterátory tak, aby první je [lower_bound –](#lower_bound) klíč a druhý je [upper_bound –](#upper_bound) klíče.

Pro přístup k první iterator páru `pr` vrácené funkcí člen, použijte `pr`. **první** a pokud chcete dereference iterator dolní mez, použijte \*( `pr`. **nejprve**). Pro přístup k druhý iterator páru `pr` vrácené funkcí člen, použijte `pr`. **druhý** a pokud chcete dereference iterator horní mez, použijte \*( `pr`. **druhý**).

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

Odebere element nebo rozsahu prvků v multimap ze zadaných pozic nebo odebere prvky, které odpovídají zadaným klíčem.

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

`Where` Pozice elementu, který chcete odebrat.

`First` Pozice prvního elementu, který chcete odebrat.

`Last` Pozice bezprostředně za posledním elementem odeberou.

`Key` Klíč prvky, které mají být odebrány.

### <a name="return-value"></a>Návratová hodnota

Pro první dva členské funkce obousměrné iterator, označí první prvek zbývající nad rámec žádné elementy, odebrat nebo element, který je konci mapy, pokud neexistuje žádný takový prvek.

Pro třetí – členská funkce vrátí počet prvků, které byly odebrány z multimap.

### <a name="remarks"></a>Poznámky

Příklad kódu, najdete v části [map::erase](../standard-library/map-class.md#erase).

## <a name="find"></a>  multimap::Find

Vrátí iterátor, který odkazuje na první umístění elementu v multimap, s klíčem ekvivalentní k zadanému klíči.

```cpp
iterator find(const Key& key);


const_iterator find(const Key& key) const;
```

### <a name="parameters"></a>Parametry

`key` Hodnota klíče odpovídala klíč řazení elementu z multimap být vyhledán.

### <a name="return-value"></a>Návratová hodnota

Iterátor, který odkazuje na umístění element se zadaným klíčem nebo umístění úspěšné posledním prvkem v multimap ( `multimap::end()`) Pokud není nalezena žádná shoda pro klíč.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí iterátor, který odkazuje na element v multimap jehož klíč řazení je ekvivalentní argument klíč v predikátu Binární indukuje řazení podle menší než srovnání vztah.

Pokud vrátí hodnotu, která **najít** je přiřazena k **const_iterator –**, multimap objekt nelze změnit. Pokud návratová hodnota **najít** je přiřazen **iterator**, multimap objekt můžete upravit.

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

Vrátí kopii allocator objekt použitý k vytvoření multimap.

```cpp
allocator_type get_allocator() const;
```

### <a name="return-value"></a>Návratová hodnota

Allocator používané multimap.

### <a name="remarks"></a>Poznámky

Alokátorů pro multimap – Třída zadejte, jak třída spravuje úložiště. Alokátorů výchozí součástí standardní knihovna C++ – třídy kontejnerů postačí pro většinu programovacích potřeb. Psaní a pomocí vlastní allocator – třída je rozšířená C++.

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

Vloží do multimap elementu nebo rozsahu prvků.

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
|`Val`|Hodnota elementu, který má být vložen do multimap.|
|`Where`|Místo zahájení vyhledání správného bodu vložení. (Pokud tento bod okamžitě předchází `Where`, vložení se může objevit v amortizovaný konstantní čas místo logaritmické času.)|
|`ValTy`|Parametr šablony, která určuje typ argumentu, mapy můžete použít k vytvoření element [value_type](../standard-library/map-class.md#value_type)a představuje výhodu předávání `Val` jako argument.|
|`First`|Pozice prvního prvku, který chcete zkopírovat.|
|`Last`|Pozice bezprostředně za posledním prvkem, který chcete zkopírovat.|
|`InputIterator`|Argument funkce šablony, který splňuje požadavky [vstupní iterator](../standard-library/input-iterator-tag-struct.md) který odkazuje na elementy typu, který slouží k vytvoření [value_type](../standard-library/map-class.md#value_type) objekty.|
|`IList`|[Initializer_list](../standard-library/initializer-list.md) ze kterého chcete kopírovat prvky.|

### <a name="return-value"></a>Návratová hodnota

Příkaz insert jeden element členské funkce (1) a (2), vrátí iterovat na pozici, kde byl nového elementu vložit do multimap.

Jeden element s nápovědu členské funkce, (3) a (4) vrátí iterátor, který odkazuje na pozici, kde byl nového elementu vložit do multimap.

### <a name="remarks"></a>Poznámky

Pomocí této funkce jsou zneplatněny žádné ukazatele nebo odkazy, ale zneplatnění všechny iterátory do kontejneru.

Během vkládání pouze jeden prvek Pokud je vyvolána výjimka, stavu kontejneru nezměnil. Pokud je při vkládání více prvků vyvolána výjimka, kontejner zůstane v neurčeném, ale platném stavu.

[Value_type](../standard-library/map-class.md#value_type) kontejner je typedef, který patří do kontejneru a pro mapu, `multimap<K, V>::value_type` je `pair<const K, V>`. Hodnota prvku je seřazená dvojice, ve které je první komponenta rovna hodnotě klíče a druhá komponenta je rovna datové hodnotě prvku.

Členská funkce rozsahu (5) vloží do multimap, která odpovídá každý prvek řešené pomocí iterace v rozsahu pořadí hodnot element `[First, Last)`; proto `Last` získat nevloží. Členské funkce kontejneru `end()` odkazuje na pozici bezprostředně za posledním prvkem v kontejneru – například příkaz `m.insert(v.begin(), v.end());` vloží všechny elementy `v` do `m`.

Funkce člena inicializátoru seznamu (6) používá [initializer_list](../standard-library/initializer-list.md) kopírování prvků do mapy.

Pro vkládání elementu sestavený na místě – to znamená, se provádí žádné operace kopírování nebo přesunutí – najdete v části [multimap::emplace](#emplace) a [multimap::emplace_hint](#emplace_hint).

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

Typ, který poskytuje obousměrné iterator, který může číst nebo upravovat libovolný element v multimap.

```cpp
typedef implementation-defined iterator;
```

### <a name="remarks"></a>Poznámky

**Iterator** definovaný multimap body objektů [value_type](#value_type), které jsou typu `pair` * \< * **const klíč**, **Typ *** >*. Hodnota klíče je k dispozici prostřednictvím první člen pár a hodnota namapované elementu je k dispozici prostřednictvím druhý člen, které odpovídá páru.

K dereference **iterator** `Iter` odkazující na element v multimap, použijte **->** operátor.

Chcete-li získat přístup k hodnotě klíče pro element, použijte `Iter`  ->  **první**, což je totéž jako (\* `Iter`). **první**. Chcete-li získat přístup k hodnotě namapované datum pro element, použijte `Iter`  ->  **druhý**, což je totéž jako (\* `Iter`). **druhý**.

Typ **iterator** lze upravit hodnotu elementu.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [začít](#begin) příklad toho, jak deklarace a používání **iterator**.

## <a name="key_comp"></a>  multimap::key_comp

Načte kopii porovnání objekt použitý k pořadí klíčů v multimap.

```cpp
key_compare key_comp() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí objekt funkce multimap používá pořadí jejích elementů.

### <a name="remarks"></a>Poznámky

Definuje objekt uložené – členská funkce

**BOOL – operátor**( **const klíč &** *x*, **const klíč &** *y*);

která vrátí hodnotu true, pokud *x* výhradně předchází *y* v pořadí řazení.

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

Typ, který poskytuje funkce objekt, který můžete porovnat dva klíče řazení k určení relativních pořadí dva elementy v multimap.

```cpp
typedef Traits key_compare;
```

### <a name="remarks"></a>Poznámky

**key_compare –** je synonymum pro parametr šablony `Traits`.

Další informace o `Traits` najdete v článku [multimap – třída](../standard-library/multimap-class.md) tématu.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [key_comp –](#key_comp) příklad toho, jak deklarace a používání `key_compare`.

## <a name="key_type"></a>  multimap::key_type

Typ, který popisuje řazení klíče objektu, která se považuje za každý prvek multimap.

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>Poznámky

**key_type –** je synonymum pro parametr šablony `Key`.

Další informace o `Key`, najdete v části poznámky [multimap – třída](../standard-library/multimap-class.md) tématu.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [value_type](#value_type) příklad toho, jak deklarace a používání `key_type`.

## <a name="lower_bound"></a>  multimap::lower_bound

Vrátí iterovat prvním elementem v multimap, s klíčem, který je rovna nebo větší než je zadaný klíč.

```cpp
iterator lower_bound(const Key& key);

const_iterator lower_bound(const Key& key) const;
```

### <a name="parameters"></a>Parametry

`key` Argument klíč, který se má porovnat s klíč řazení elementu z multimap prohledávaný.

### <a name="return-value"></a>Návratová hodnota

Iterátor nebo `const_iterator` adresy umístění elementu v multimap, že klíčem, která je rovna nebo větší než argument klíč nebo který adres umístění úspěšné posledním prvkem v multimap, pokud žádné odpovídají je nalezen klíče.

Pokud vrátí hodnotu, která `lower_bound` je přiřazena k `const_iterator`, multimap objekt nelze změnit. Pokud návratová hodnota `lower_bound` je přiřazen **iterator**, multimap objekt můžete upravit.

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

Typ, který představuje typ data uložená v multimap.

```cpp
typedef Type mapped_type;
```

### <a name="remarks"></a>Poznámky

`mapped_type` je synonymum pro parametr šablony `Type`.

Další informace o `Type` najdete v článku [multimap – třída](../standard-library/multimap-class.md) tématu.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [value_type](#value_type) příklad toho, jak deklarace a používání `key_type`.

## <a name="max_size"></a>  multimap::max_size

Vrátí maximální délka multimap.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>Návratová hodnota

Maximální možné délku multimap.

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
|`Al`|Třída úložiště alokátoru pro použití s tímto objektem multimap, kterou je standardně třída Allocator.|
|`Comp`|Funkci porovnání typu **constTraits** sloužící k uspořádání elementy v mapě, který se standardně **vlastnosti**.|
|`Right`|Objekt map, ze kterého je kopií vytvořen objekt set.|
|`First`|Pozice první prvek v rozsahu elementy, které se mají zkopírovat.|
|`Last`|Pozice první prvek mimo rozsah elementy, které se mají zkopírovat.|
|`IList`|Seznam initializer_list, ze kterého chcete kopírovat prvky.|

### <a name="remarks"></a>Poznámky

Všechny konstruktory ukládání typu allocator objektu, který spravuje úložiště paměti pro multimap a který se může vracet později voláním [get_allocator –](#get_allocator). Parametr allocator je často v deklaraci třídy vynechán a makra předběžného zpracování jsou použita k nahrazení alternativních alokátorů.

Všechny konstruktory inicializují své objekty multimap.

Všechny konstruktory uložit objekt funkce typu `Traits` který se používá k navázání pořadí mezi klíči multimap a který se může vracet později voláním [key_comp –](#key_comp).

Zadejte první tři konstruktory prázdný počáteční multimap, druhý určující typ porovnání – funkce ( `Comp`) pro použití při vytváření pořadí elementy a třetí explicitním zadáním přidělujícího modulu zadejte ( `Al`) na použít. Klíčové slovo `explicit` potlačí některé druhy automatického převodu typu.

Čtvrtý konstruktor určuje kopii parametru `Right` objektu multimap.

Pátý konstruktor určuje kopii objektu multimap přesunutím parametru `Right`.

Šestý, sedmý a osmý konstruktor kopírují členy objektu initializer_list.

Zkopírujte následující tři konstruktory rozsahu `[First, Last)` mapy se zvýšeným explicitness v určení typu funkci porovnání třídy **vlastnosti** a přidělení.

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

Nahradí elementy multimap kopii jiného multimap.

```cpp
multimap& operator=(const multimap& right);

multimap& operator=(multimap&& right);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|-|-|
|`right`|[Multimap](../standard-library/multimap-class.md) se zkopírují `multimap`.|

### <a name="remarks"></a>Poznámky

Po vymazání v žádné stávající elementy `multimap`, `operator=` buď kopíruje nebo přesouvá obsah `right` do `multimap`.

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

Typ, který poskytuje ukazatel na element multimap.

```cpp
typedef typename allocator_type::pointer pointer;
```

### <a name="remarks"></a>Poznámky

Typ **ukazatel** lze upravit hodnotu elementu.

Ve většině případů [iterator](#iterator) se má použít pro přístup k elementům v multimap objektu.

## <a name="rbegin"></a>  multimap::rbegin

Vrátí iterator adresování prvním elementem v invertovaných multimap.

```cpp
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```

### <a name="return-value"></a>Návratová hodnota

Iterator zpětné obousměrného adresování prvním elementem v invertovaných multimap nebo řešení, co je posledním prvkem v unreversed multimap.

### <a name="remarks"></a>Poznámky

`rbegin` se používá s odstínech multimap stejně jako [začít](#begin) se používá s multimap.

Pokud vrátí hodnotu, která `rbegin` je přiřazena k `const_reverse_iterator`, pak multimap objekt nelze změnit. Pokud vrátí hodnotu, která `rbegin` je přiřazena k `reverse_iterator`, pak je možné upravit multimap objekt.

`rbegin` můžete použít k iteraci v rámci multimap zpětné.

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

Typ, který obsahuje odkaz na element uložené v multimap.

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

Vrátí iterátor, který řeší úspěšné posledním prvkem v invertovaných multimap umístění.

```cpp
const_reverse_iterator rend() const;

reverse_iterator rend();
```

### <a name="return-value"></a>Návratová hodnota

Iterator zpětné obousměrného, která řeší umístění úspěšné posledním prvkem v invertovaných multimap (umístění, které měl před prvním elementem v unreversed multimap).

### <a name="remarks"></a>Poznámky

`rend` se používá s odstínech multimap stejně jako [end](../standard-library/map-class.md#end) se používá s multimap.

Pokud vrátí hodnotu, která `rend` je přiřazena k `const_reverse_iterator`, pak multimap objekt nelze změnit. Pokud vrátí hodnotu, která `rend` je přiřazena k `reverse_iterator`, pak je možné upravit multimap objekt.

`rend` dá se použít k testování na tom, jestli zpětné iterator dosáhne konce své multimap.

Hodnoty vrácené `rend` by neměl být vyhodnoceny odkazy.

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

Typ, který poskytuje obousměrné iterator, které můžou číst nebo upravit element v invertovaných multimap.

```cpp
typedef std::reverse_iterator<iterator> reverse_iterator;
```

### <a name="remarks"></a>Poznámky

Typ `reverse_iterator` je použít k iteraci v rámci multimap pozpátku.

`reverse_iterator` Definovaný multimap body objektů [value_type](#value_type), které jsou typu `pair` * \< * **const klíč**, **Typ *** >*. Hodnota klíče je k dispozici prostřednictvím první člen pár a hodnota namapované elementu je k dispozici prostřednictvím druhý člen, které odpovídá páru.

K dereference `reverse_iterator` `rIter` odkazující na element v multimap, použijte -> – operátor.

Chcete-li získat přístup k hodnotě klíče pro element, použijte `rIter`  ->  **první**, což je totéž jako (\* `rIter`). **první**. Chcete-li získat přístup k hodnotě namapované datum pro element, použijte `rIter`  ->  **druhý**, což je totéž jako (\* `rIter`). **první**.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [rbegin –](#rbegin) příklad toho, jak deklarace a používání `reverse_iterator`.

## <a name="size"></a>  multimap::size

Vrátí počet prvků multimap.

```cpp
size_type size() const;
```

### <a name="return-value"></a>Návratová hodnota

Aktuální délka multimap.

### <a name="example"></a>Příklad

Následující příklad ukazuje použití multimap::size – členská funkce.

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

Spočítá počet elementů v multimap typ celé číslo bez znaménka.

```cpp
typedef typename allocator_type::size_type size_type;
```

### <a name="example"></a>Příklad

Podívejte se na příklad pro [velikost](#size) příklad toho, jak deklarace a používání `size_type`

## <a name="swap"></a>  multimap::swap

Elementy dvě multimaps výměny.

```cpp
void swap(
    multimap<Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

`right` Multimap poskytuje prvky, které mají být prohodily nebo multimap, jehož elementy jsou k výměně s těmi multimap `left`.

### <a name="remarks"></a>Poznámky

Členská funkce by způsobila neplatnost žádné odkazy, ukazatele nebo iterátory, které určíte elementy ve dvou multimaps, jehož elementy jsou během výměny.

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

Vrátí iterovat prvním elementem v multimap, s klíčem, který je větší než je zadaný klíč.

```cpp
iterator upper_bound(const Key& key);

const_iterator upper_bound(const Key& key) const;
```

### <a name="parameters"></a>Parametry

`key` Argument klíč, který se má porovnat s klíč řazení elementu z multimap prohledávaný.

### <a name="return-value"></a>Návratová hodnota

Iterátor nebo `const_iterator` adresy umístění elementu v multimap, že klíčem, který je větší než klíč argument, nebo, který se týká umístění úspěšné posledním prvkem v multimap, pokud žádné odpovídají je nalezen klíče.

Pokud je přiřazen návratovou hodnotu `const_iterator`, multimap objekt nelze změnit. Pokud návratová hodnota je přiřazen k **iterator**, multimap objekt je možné upravit.

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

Členská funkce vrátí objekt funkce, který určuje pořadí prvků v multimap tak, že porovnáte jejich hodnoty klíče.

```cpp
value_compare value_comp() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí objekt funkce porovnání multimap používá pořadí jejích elementů.

### <a name="remarks"></a>Poznámky

Pro multimap *m*, pokud dva elementy *e*1 ( *tisíc*1, *d*1) a *e*2 ( *tisíc*2, `d`2) jsou objekty typu `value_type`, kde *tisíc*1 a *tisíc*2 jsou jejich klíče typu `key_type` a `d`1 a `d`2 jsou jejich data typu `mapped_type`, pak *m.*`value_comp`( *e*1, *e*2) je ekvivalentní *m.* `key_comp` ( *tisíc*1, *tisíc*2).

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

Typ, který představuje typ objektu uložené jako element v mapování.

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

## <a name="see-also"></a>Viz také

[\<Mapa > členy](http://msdn.microsoft.com/en-us/7e8f0bc2-6034-40f6-9d14-76d4cef86308)<br/>
[Kontejnery](../cpp/containers-modern-cpp.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)<br/>
