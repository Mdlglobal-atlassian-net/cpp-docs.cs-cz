---
title: multimap – třída
ms.date: 10/18/2018
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
ms.openlocfilehash: 2f6ae50a825d6eff2eb64c84b209fa81c4b7949f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363859"
---
# <a name="multimap-class"></a>multimap – třída

C++ Standardní knihovna multimap třídy se používá pro ukládání a načítání dat z kolekce, ve kterém každý prvek je pár, který má hodnotu dat a klíč řazení. Hodnota klíče nemusí být jedinečná a je použita k automatickému seřazení dat. Hodnotu prvku v objektu multimap, ale ne jeho přidruženou hodnotu klíče, lze změnit přímo. Namísto toho hodnoty klíčů přidružené ke starým prvkům musí být odstraněny a vloženy nové hodnoty klíče související s novými prvky.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Key,
    class Type,
    class Traits=less <Key>,
    class Allocator=allocator <pair  <const Key, Type>>>
class multimap;
```

### <a name="parameters"></a>Parametry

*Klíč*\
Datový typ klíče, který se uloží v objektu multimap.

*Typ*\
Typ dat prvku, který bude uložen do objektu multimap.

*Vlastnosti*\
Typ poskytující objekt funkce, který může porovnat dvě hodnoty prvků pro určení jejich relativního pořadí v objektu multimap. Binární predikát `less<Key>` je výchozí hodnota.

V jazyce C++14 můžete povolit heterogenní `std::less<>` vyhledávání `std::greater<>` zadáním nebo predikátu, který nemá žádné parametry typu. Další informace naleznete [v tématu Heterogenní vyhledávání v asociativních kontejnerech](../standard-library/stl-containers.md#heterogeneous-lookup-in-associative-containers-c14)

*Přidělování*\
Typ představující uložený objekt alokátoru, který zapouzdřuje informace o přidělování a navrácení paměti zpět objektu map. Tento argument je volitelný a `allocator<pair <const Key, Type> >`výchozí hodnota je .

## <a name="remarks"></a>Poznámky

Třída multimap standardní knihovny C++ je

- Asociativní kontejner, což je kontejner proměnné velikosti, který podporuje efektivní načtení hodnoty prvku založené na přiřazené hodnotě klíče.

- Oboustranný, protože poskytuje obousměrné iterátory pro přístup k jeho prvkům.

- Seřazený, protože jeho prvky jsou řazeny podle hodnot klíče v kontejneru podle zadané porovnávací funkce.

- Vícenásobný, protože je prvky nemusí mít jedinečné klíče, takže jedna hodnota klíče může mít k sobě přidružených mnoho datových hodnot prvků.

- Kontejner asociativních párů, protože jeho prvky hodnoty dat se liší od hodnot klíčů.

- Šablona třídy, protože funkce, které poskytuje, je obecná a tak nezávislá na konkrétním typu dat obsažených jako prvky nebo klíče. Datové typy použité pro prvky a klíče jsou místo toho zadány jako parametry v šabloně třídy společně s funkcí porovnání a alokátorem.

Iterátor poskytované mapové třídy je obousměrný iterátor, ale funkce členů třídy [insert](#insert) a [multimap](#multimap) mají verze, které berou jako parametry šablony slabší vstupní iterátor, jehož požadavky na funkčnost jsou minimální než požadavky zaručené třídou obousměrných iterátorů. Různé koncepty iterátorů tvoří rodinu týkající se upřesnění jejich funkčnosti. Každý koncept iterátoru má vlastní sadu požadavků a algoritmy, které s nimi pracují, musí omezit jejich předpoklady na požadavky podle typu iterátoru. Lze předpokládat, že ke vstupnímu iterátoru lze přistoupit přes ukazatel pro odkazování na některý objekt a že může být zvýšen na další iterátor v pořadí. Toto je minimální sada funkcí, ale stačí, abyste mohli smysluplně hovořit o rozsahu `[First, Last)` iterátorů v kontextu členských funkcí třídy.

Volba typu kontejneru by měla obecně vycházet z typu vyhledávání a vkládání vyžadovaného aplikací. Asociativní kontejnery jsou optimalizovány pro operace vyhledávání, vkládání a odstranění. Členské funkce, které explicitně podporují tyto operace, jsou efektivní a jsou prováděny v čase, který je průměrně úměrný logaritmu počtu prvků v kontejneru. Vkládání prvků nezruší platnost žádných iterátorů a odstranění prvků zruší platnost pouze těch iterátorů, které výslovně odkazovaly na odstraněné prvky.

Objekt multimap by měl být asociativní kontejner dle výběru, kdy jsou podmínky přiřazení hodnot k jejich klíčům splněny aplikací. Model pro tento typ struktury je uspořádaný seznam klíčových slov s přidruženými řetězcovými hodnotami poskytujícími (řekněme) definice, kde slova nebyla vždy jednoznačně definována. Pokud místo toho klíčová slova byla jedinečně definovaná tak, aby byly klíče jedinečné, bude objekt map správným kontejnerem výběru. Naopak pokud je pouze uložen seznam slov, bude objekt set tím správným kontejnerem. Pokud bylo povoleno více výskytů jednoho slova, je objekt multiset odpovídající strukturou kontejneru.

Multimap seřídí sekvenci, kterou řídí voláním uloženého objektu funkce typu [key_compare](#key_compare). Tento uložený objekt je funkce porovnání, ke které lze přistupovat voláním členské funkce [key_comp](#key_comp). Obecně, tyto prvky musí být menší než srovnatelné pro toto pořadí, což znamená, že když jsou uvedeny dva prvky, může být stanoveno, zda jsou ekvivalentní (v tom smyslu, že ani jeden není menší než ten druhý), nebo že jeden je menší než druhý. To má za výsledek řazení mezi neekvivalentními prvky. Technicky je funkce porovnání binárním predikátem, který indukuje přísné slabé řazení, standardním matematickým způsobem. Binární predikát `f(x,y)` je objekt funkce, který `x` `y` má dva objekty argumentů a vrácenou hodnotu true nebo false. Řazení uložené na sadu je přísné slabé řazení, pokud binární predikát je nereflexivní, antisymetrické a tranzitivní a `x` `y` pokud ekvivalence `f(x,y)` `f(y,x)` je tranzitivní, kde dva objekty a jsou definovány jako rovnocenné, pokud jsou oba a jsou false. Pokud silnější podmínka rovnosti mezi klíči nahradí ekvivalenci, stane se pořadí celkovým (v tom smyslu, že všechny prvky jsou uspořádány ve vztahu k sobě navzájem) a odpovídající klíče budou od sebe nerozeznatelné.

V jazyce C++14 můžete povolit heterogenní `std::less<>` vyhledávání `std::greater<>` zadáním nebo predikátu, který nemá žádné parametry typu. Další informace naleznete [v tématu Heterogenní vyhledávání v asociativních kontejnerech](../standard-library/stl-containers.md#sequence_containers)

## <a name="members"></a>Členové

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[multimap](#multimap)|Konstrukce, `multimap` který je prázdný nebo který je kopií celé `multimap`nebo části některé jiné .|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[allocator_type](#allocator_type)|Typ, který `allocator` představuje třídu `multimap` pro objekt.|
|[const_iterator](#const_iterator)|Typ, který poskytuje obousměrný iterátor, který může číst `multimap` **const** prvek v .|
|[const_pointer](#const_pointer)|Typ, který poskytuje ukazatel na **const** element v `multimap`.|
|[const_reference](#const_reference)|Typ, který poskytuje odkaz na **const** `multimap` prvek uložený v a pro čtení a provádění **const** operací.|
|[const_reverse_iterator](#const_reverse_iterator)|Typ, který poskytuje obousměrný iterátor, který může číst `multimap`libovolný **prvek const** v .|
|[difference_type](#difference_type)|Podepsaný typ celé číslo, který lze použít k reprezentaci počtu prvků `multimap` a v rozsahu mezi prvky, na které iterátory poukázaly.|
|[Iterace](#iterator)|Typ, který poskytuje rozdíl mezi dvěma iterátory, `multimap`které odkazují na prvky v rámci stejné .|
|[key_compare](#key_compare)|Typ, který poskytuje objekt funkce, který může porovnat dva klíče řazení `multimap`k určení relativní pořadí dvou prvků v .|
|[key_type](#key_type)|Typ, který popisuje objekt klíče řazení, který `multimap`představuje každý prvek .|
|[mapped_type](#mapped_type)|Typ, který představuje datový typ `multimap`uložený v aplikaci .|
|[ukazatel](#pointer)|Typ, který poskytuje ukazatel na **const** element v `multimap`.|
|[Odkaz](#reference)|Typ, který poskytuje odkaz na prvek `multimap`uložený v .|
|[reverse_iterator](#reverse_iterator)|Typ, který poskytuje obousměrný iterátor, který může číst nebo `multimap`upravovat prvek v obráceném .|
|[size_type](#size_type)|Nepodepsaný celé číslo typ, který poskytuje ukazatel na `multimap`prvek **const** v .|
|[value_type](#value_type)|Typ, který poskytuje objekt funkce, který může porovnat dva prvky `multimap`jako klíče řazení k určení jejich relativní pořadí v .|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[Začít](#begin)|Vrátí iterátor adresující první prvek `multimap`v rozhraní .|
|[cbegin](#cbegin)|Vrátí const iterator adresující první `multimap`prvek v rozhraní .|
|[cend](#cend)|Vrátí const iterátor, který řeší umístění, které následuje `multimap`poslední prvek v .|
|[Jasné](#clear)|Vymaže všechny `multimap`prvky .|
|[Počet](#count)|Vrátí počet prvků v `multimap` klíči, jejichž klíč odpovídá klíči zadanému parametrem.|
|[crbegin](#crbegin)|Vrátí const iterator adresování první `multimap`prvek v obrácené .|
|[crend](#crend)|Vrátí const iterator, který řeší umístění, které následuje `multimap`poslední prvek v obráceném .|
|[místo](#emplace)|Vloží prvek vytvořený na místě `multimap`do .|
|[emplace_hint](#emplace_hint)|Vloží prvek vytvořený na místě `multimap`do aplikace a s nápovědou k umístění.|
|[empty](#empty)|Testuje, `multimap` pokud je prázdný.|
|[Konec](#end)|Vrátí iterátor, který řeší umístění, které následuje `multimap`poslední prvek v rozhraní .|
|[equal_range](#equal_range)|Vyhledá rozsahu prvků, kde klíče prvku odpovídají zadané hodnotě.|
|[Vymazat](#erase)|Odebere prvek nebo rozsah prvků `multimap` v a ze zadané pozice nebo odebere prvky, které odpovídají zadanému klíči.|
|[find](#find)|Vrátí iterátor adresování první umístění prvku `multimap` v, který má klíč ekvivalentní zadaný klíč.|
|[get_allocator](#get_allocator)|Vrátí kopii `allocator` objektu použitého `multimap`k vytvoření .|
|[Vložit](#insert)|Vloží prvek nebo rozsah prvků do `multimap`.|
|[key_comp](#key_comp)|Načte kopii objektu porovnání použitého `multimap`k objednání klíčů v .|
|[lower_bound](#lower_bound)|Vrátí iterátor prvnímu prvku v `multimap` a, který s klíčem, který je roven nebo větší než zadaný klíč.|
|[max_size](#max_size)|Vrátí maximální délku `multimap`.|
|[rbegin](#rbegin)|Vrátí iterátor adresující první prvek `multimap`v obráceném .|
|[rend](#rend)|Vrátí iterátor, který řeší umístění, které následuje poslední `multimap`prvek v obráceném .|
|[Velikost](#size)|Vrátí počet prvků v `multimap`rozhraní .|
|[Swap](#swap)|Vyměňuje prvky `multimap`dvou s.|
|[upper_bound](#upper_bound)|Vrátí iterátor prvnímu prvku v `multimap` prvku, který má klíč větší než zadaný klíč.|
|[value_comp](#value_comp)|Členská funkce vrátí objekt funkce, který určuje `multimap` pořadí prvků v a porovnáním jejich hodnoty klíče.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operátor =](#op_eq)|Nahradí prvky a `multimap` kopií jiného `multimap`.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<mapa>

**Obor názvů:** std

Dvojice ( **klíč**, **hodnota**) jsou uloženy v `pair`multimapě jako objekty typu . Dvojice třída vyžaduje \<záhlaví utility>, který \<je automaticky zahrnuta do mapy>.

## <a name="multimapallocator_type"></a><a name="allocator_type"></a>multimap::allocator_type

Typ, který představuje třídu alokátoru pro objekt multimap.

```cpp
typedef Allocator allocator_type;
```

### <a name="example"></a>Příklad

Viz příklad pro [get_allocator](#get_allocator) příklad `allocator_type`pomocí .

## <a name="multimapbegin"></a><a name="begin"></a>multimap::begin

Vrátí iterátor adresující první prvek v multimap.

```cpp
const_iterator begin() const;

iterator begin();
```

### <a name="return-value"></a>Návratová hodnota

Obousměrný itestrátor adresující první prvek v multimapě nebo umístění, které následuje prázdnou multimapu.

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

## <a name="multimapcbegin"></a><a name="cbegin"></a>multimap::cbegin

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

## <a name="multimapcend"></a><a name="cend"></a>multimap::cend

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

## <a name="multimapclear"></a><a name="clear"></a>multimap::vymazat

Vymaže všechny prvky multimapy.

```cpp
void clear();
```

### <a name="example"></a>Příklad

Následující příklad ukazuje použití multimap::clear členské funkce.

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

## <a name="multimapconst_iterator"></a><a name="const_iterator"></a>multimap::const_iterator

Typ, který poskytuje obousměrný iterátor, který může číst **const** prvek v multimap.

```cpp
typedef implementation-defined const_iterator;
```

### <a name="remarks"></a>Poznámky

Typ `const_iterator` nelze použít ke změně hodnoty prvku.

Definované `const_iterator` multimapovými body na objekty [value_type](#value_type) `pair<const Key, Type>`, které jsou typu . Hodnota klíče je k dispozici prostřednictvím první dvojice členů a hodnota mapovaného prvku je k dispozici prostřednictvím druhého člena dvojice.

Chcete-li `const_iterator` odkazovat *cIter* ukazující na prvek v **->** multimap, použijte operátor.

Chcete-li získat přístup k hodnotě `cIter->first`klíče pro `(*cIter).first`prvek, použijte , což je ekvivalentní . Chcete-li získat přístup k hodnotě mapované základny pro prvek, použijte `cIter->second`, což je ekvivalentní `(*cIter).second`.

### <a name="example"></a>Příklad

Viz příklad pro [začátek](#begin) `const_iterator`pro příklad pomocí .

## <a name="multimapconst_pointer"></a><a name="const_pointer"></a>multimap::const_pointer

Typ, který poskytuje ukazatel na **const** element v multimap.

```cpp
typedef typename allocator_type::const_pointer const_pointer;
```

### <a name="remarks"></a>Poznámky

Typ `const_pointer` nelze použít ke změně hodnoty prvku.

Ve většině případů [iterátor](#iterator) by měl být použit pro přístup k prvkům v multimap objektu.

## <a name="multimapconst_reference"></a><a name="const_reference"></a>multimap::const_reference

Typ, který poskytuje odkaz na **prvek const** uložený v multimap pro čtení a provádění operací **const.**

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

## <a name="multimapconst_reverse_iterator"></a><a name="const_reverse_iterator"></a>multimap::const_reverse_iterator

Typ, který poskytuje obousměrný iterátor, který může číst libovolný **prvek const** v multimap.

```cpp
typedef std::reverse_iterator<const_iterator> const_reverse_iterator;
```

### <a name="remarks"></a>Poznámky

Typ `const_reverse_iterator` nemůže změnit hodnotu prvku a používá se k iterátu prostřednictvím multimap v opačném směru.

Definované `const_reverse_iterator` multimapovými body na objekty [value_type](#value_type) `pair<const Key, Type>`, které jsou typu . Hodnota klíče je k dispozici prostřednictvím první dvojice členů a hodnota mapovaného prvku je k dispozici prostřednictvím druhého člena dvojice.

Chcete-li `const_reverse_iterator` odkazovat *na crIter* ukazující na prvek **->** v multimap, použijte operátor.

Chcete-li získat přístup k hodnotě `crIter->first`klíče pro `(*crIter).first`prvek, použijte , což je ekvivalentní . Chcete-li získat přístup k hodnotě mapované základny pro prvek, použijte `crIter->second`, což je ekvivalentní `(*crIter).first`.

### <a name="example"></a>Příklad

Příklad pro [rend](#rend) naleznete v příkladu, `const_reverse_iterator`jak deklarovat a používat .

## <a name="multimapcount"></a><a name="count"></a>multimap::počet

Vrátí počet prvků v multimap, jejichž klíče odpovídají klíči zadanému parametrem.

```cpp
size_type count(const Key& key) const;
```

### <a name="parameters"></a>Parametry

*Klíč*\
Klíč prvků, které mají být uzavřeno z multimap.

### <a name="return-value"></a>Návratová hodnota

Počet prvků, jejichž klíče řazení odpovídají klíči parametru; 0, pokud multimap neobsahuje prvek s odpovídající klíč.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí počet prvků v rozsahu

\[lower_bound(*klíč*), upper_bound(*klíč*)

které mají *klíč*hodnoty klíče .

### <a name="example"></a>Příklad

Následující příklad ukazuje použití multimap::count členské funkce.

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

## <a name="multimapcrbegin"></a><a name="crbegin"></a>multimap::crbegin

Vrátí const iterator adresování první prvek v obrácené multimap.

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>Návratová hodnota

Const reverzní obousměrný iterátor adresování první prvek v obrácené [multimap](../standard-library/multimap-class.md) nebo adresování, `multimap`co bylo poslední prvek v unreverse .

### <a name="remarks"></a>Poznámky

`crbegin`se používá s `multimap` obráceným stejně `multimap`jako [begin](#begin) se používá s .

S vrácenou `crbegin`hodnotou `multimap` aplikace nelze objekt změnit.

`crbegin`lze použít k iterovat přes `multimap` dozadu.

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

## <a name="multimapcrend"></a><a name="crend"></a>multimap::crend

Vrátí const iterátor, který řeší umístění, které následuje poslední prvek v obráceném multimap.

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>Návratová hodnota

Const reverzní obousměrný iterátor, který řeší umístění následující poslední prvek v obrácené [multimap](../standard-library/multimap-class.md) (umístění, které předcházelo první prvek v unreverse). `multimap`

### <a name="remarks"></a>Poznámky

`crend`se používá s `multimap` obráceným stejně jako [multimap::end](#end) se používá s `multimap`.

S vrácenou `crend`hodnotou `multimap` aplikace nelze objekt změnit.

`crend`lze použít k testování, zda reverzní iterátor dosáhl `multimap`konce svého .

Hodnota vrácená `crend` by neměla být odkazována.

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

## <a name="multimapdifference_type"></a><a name="difference_type"></a>multimap::difference_type

Podepsaný typ celé číslo, který lze použít k reprezentaci počtu prvků multimap v rozsahu mezi prvky, na které se iterátory mapují.

```cpp
typedef typename allocator_type::difference_type difference_type;
```

### <a name="remarks"></a>Poznámky

Je `difference_type` typ vrácena při odečtení nebo zvýšení prostřednictvím iterátory kontejneru. Obvykle `difference_type` se používá k reprezentaci počtu prvků v rozsahu [*první*, `first` *poslední*) mezi iterátory a `last`, zahrnuje prvek, na který `first` se `last`vztahuje, a rozsah prvků až do prvku, na který je však nezahrnuto.

Všimněte `difference_type` si, že i když je k dispozici pro všechny iterátory, které splňují požadavky vstupní iterátor, který zahrnuje třídu obousměrné iterátory podporované reverzibilní kontejnery, jako je například set, odčítání mezi iterátory je podporován pouze náhodný přístup iterátory poskytované kontejneru s náhodným přístupem, jako je vektor.

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

## <a name="multimapemplace"></a><a name="emplace"></a>multimap::emplace

Vloží prvek vytvořený na místě (nejsou prováděny žádné operace kopírování nebo přesouvání).

```cpp
template <class... Args>
iterator emplace(Args&&... args);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|-|-|
|*Args*|Argumenty předány k vytvoření prvku, který má být vložen do multimap.|

### <a name="return-value"></a>Návratová hodnota

Iterátor nově vloženého prvku.

### <a name="remarks"></a>Poznámky

Žádné odkazy na prvky kontejneru jsou zrušena touto funkcí, ale může zneplatnit všechny iterátory do kontejneru.

Pokud je vyvolána výjimka během vložení, kontejner zůstane beze změny a výjimka je znovu vyvolána.

Value_type [value_type](../standard-library/map-class.md#value_type) prvku je pár, takže hodnota prvku bude uspořádaný pár s první komponentou rovnající se hodnotě klíče a druhou komponentou rovnající se hodnotě dat prvku.

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

## <a name="multimapemplace_hint"></a><a name="emplace_hint"></a>multimap::emplace_hint

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
|*Args*|Argumenty předány k vytvoření prvku, který má být vložen do multimap.|
|*where*|Místo zahájení vyhledání správného bodu vložení. (Pokud tento bod bezprostředně předchází, *kde*, vložení může dojít v amortizované konstantní čas namísto logaritmického času.)|

### <a name="return-value"></a>Návratová hodnota

Iterátor nově vloženého prvku.

### <a name="remarks"></a>Poznámky

Žádné odkazy na prvky kontejneru jsou zrušena touto funkcí, ale může zneplatnit všechny iterátory do kontejneru.

Během umístění, pokud je vyvolána výjimka, stav kontejneru není změněn.

Value_type [value_type](../standard-library/map-class.md#value_type) prvku je pár, takže hodnota prvku bude uspořádaný pár s první komponentou rovnající se hodnotě klíče a druhou komponentou rovnající se hodnotě dat prvku.

Příklad kódu naleznete v tématu [map::emplace_hint](../standard-library/map-class.md#emplace_hint).

## <a name="multimapempty"></a><a name="empty"></a>multimap::prázdný

Testuje, pokud je multimap prázdný.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Návratová hodnota

**true,** pokud je multimap prázdný; **false,** pokud multimap je neprázdný.

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

## <a name="multimapend"></a><a name="end"></a>multimap:konec

Vrátí iterátor za koncem.

```cpp
const_iterator end() const;

iterator end();
```

### <a name="return-value"></a>Návratová hodnota

Iterátor z minulosti na konci. Pokud je multimap prázdný, pak `multimap::end() == multimap::begin()`.

### <a name="remarks"></a>Poznámky

**end** se používá k testování, zda iterátor prošel koncem jeho multimap.

Hodnota vrácená **na konci** by neměla být odkazována.

Příklad kódu najdete v [tématu multimap::find](#find).

## <a name="multimapequal_range"></a><a name="equal_range"></a>multimap::equal_range

Vyhledá rozsahu prvků, kde klíče prvku odpovídají zadané hodnotě.

```cpp
pair <const_iterator, const_iterator> equal_range (const Key& key) const;

pair <iterator, iterator> equal_range (const Key& key);
```

### <a name="parameters"></a>Parametry

*Klíč*\
Klíč argumentu, který má být porovnán s klíčem řazení prvku z prohledávaného multimap.

### <a name="return-value"></a>Návratová hodnota

Dvojice iterátorů tak, že první je [lower_bound](#lower_bound) klíče a druhý je [upper_bound](#upper_bound) klíče.

Chcete-li získat přístup k prvnímu iterátoru `pr` `pr`dvojice vrácené členovou funkcí, použijte . **nejprve** a dereference dolní mez iterátoru, použití \*( `pr`. **první**). Chcete-li získat přístup k druhému iterátoru `pr` `pr`dvojice vrácené členovou funkcí, použijte . **a** pro dereferenci horní mez iterátoru, použití \*( `pr`. **za druhé**).

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
        << "matching the 2nd element of the pair "
        << "returned by equal_range( 2 )." << endl;

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

## <a name="multimaperase"></a><a name="erase"></a>multimap::vymazat

Odebere prvek nebo rozsah prvků v multimap ze zadaných pozic nebo odebere prvky, které odpovídají zadanému klíči.

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
Klíč prvků, které mají být odstraněny.

### <a name="return-value"></a>Návratová hodnota

Pro první dvě členské funkce obousměrný iterátor, který označuje první prvek zbývající za všechny prvky odebrány nebo prvek, který je konec mapy, pokud žádný takový prvek neexistuje.

Pro třetí členfunkce vrátí počet prvků, které byly odebrány z multimap.

### <a name="remarks"></a>Poznámky

Příklad kódu naleznete v tématu [map::erase](../standard-library/map-class.md#erase).

## <a name="multimapfind"></a><a name="find"></a>multimap::najít

Vrátí iterátor, který odkazuje na první umístění prvku v multimap, který má klíč ekvivalentní zadaný klíč.

```cpp
iterator find(const Key& key);

const_iterator find(const Key& key) const;
```

### <a name="parameters"></a>Parametry

*Klíč*\
Hodnota klíče, která má být porovnána s klíčem řazení prvku z prohledávaného multimap.

### <a name="return-value"></a>Návratová hodnota

Iterátor, který odkazuje na umístění prvku se zadaným klíčem nebo umístění, které následuje`multimap::end()`poslední prvek v multimap ( ), pokud není nalezena žádná shoda pro klíč.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí iterátor, který odkazuje na prvek v multimap, jehož klíč řazení je ekvivalentní klíč argument u binárnípredikát, který indukuje řazení na základě méně než vztah srovnatelnosti.

Pokud `find` je vrácená hodnota `const_iterator`přiřazena objektu , nelze objekt s více mapami změnit. Pokud `find` je vrácená hodnota `iterator`přiřazena objektu , lze změnit objekt s více mapami.

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

## <a name="multimapget_allocator"></a><a name="get_allocator"></a>multimap::get_allocator

Vrátí kopii objektu přidělování použitého k vytvoření multimapy.

```cpp
allocator_type get_allocator() const;
```

### <a name="return-value"></a>Návratová hodnota

Alokátor používaný multimap.

### <a name="remarks"></a>Poznámky

Alokátory pro třídu multimap určují, jak třída spravuje úložiště. Výchozí alokátory dodávané s třídami kontejneru standardní knihovny jazyka C++ jsou dostatečné pro většinu potřeb programování. Psaní a používání vlastní třídy přidělování je pokročilé téma jazyka C++.

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

## <a name="multimapinsert"></a><a name="insert"></a>multimap:vložení

Vloží prvek nebo rozsah prvků do multimapy.

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
|*Val*|Hodnota prvku, který má být vložen do multimap.|
|*Kde*|Místo zahájení vyhledání správného bodu vložení. (Pokud tento bod bezprostředně předchází *Kde*, vložení může dojít v amortizované konstantní čas namísto logaritmického času.)|
|*Valty*|Parametr šablony, který určuje typ argumentu, který může mapa použít k vytvoření prvku [value_type](../standard-library/map-class.md#value_type)a dokonalého předávání *Val* jako argumentu.|
|*První*|Pozice prvního prvku, který chcete zkopírovat.|
|*Poslední*|Pozice bezprostředně za posledním prvkem, který chcete zkopírovat.|
|*Vstupní iterátor*|Argument funkce šablony, který splňuje požadavky [vstupního iterátoru,](../standard-library/input-iterator-tag-struct.md) který odkazuje na prvky typu, který lze použít ke konstrukci [value_type](../standard-library/map-class.md#value_type) objektů.|
|*Ilist*|[Initializer_list,](../standard-library/initializer-list.md) ze kterého chcete zkopírovat prvky.|

### <a name="return-value"></a>Návratová hodnota

Jednoelementové funkce vložit člen, (1) a (2), vrátí iterátor na pozici, kde byl vložen nový prvek do multimap.

Jednoelementové s nápovědou členské funkce,3) a (4), vrátí iterátor, který odkazuje na pozici, kde byl vložen nový prvek do multimap.

### <a name="remarks"></a>Poznámky

Žádné ukazatele nebo odkazy jsou zrušena touto funkcí, ale může zneplatnit všechny iterátory do kontejneru.

Během vkládání pouze jeden prvek, pokud je vyvolána výjimka, stav kontejneru není změněn. Pokud je při vkládání více prvků vyvolána výjimka, kontejner zůstane v neurčeném, ale platném stavu.

[Value_type](../standard-library/map-class.md#value_type) kontejneru je typedef, který patří do kontejneru `multimap<K, V>::value_type` `pair<const K, V>`a pro mapu, je . Hodnota prvku je seřazená dvojice, ve které je první komponenta rovna hodnotě klíče a druhá komponenta je rovna datové hodnotě prvku.

Členská funkce rozsahu (5) vloží posloupnost hodnot prvků do multimapy, která odpovídá každému prvku, `[First, Last)`kterému iterátor v rozsahu odpovídá ; proto *Last* nezíská vložen. Členská funkce `end()` kontejneru odkazuje na pozici těsně za posledním prvkem v `m.insert(v.begin(), v.end());` kontejneru – `v` `m`například příkaz vloží všechny prvky do .

Inicializační seznam členské funkce (6) používá [initializer_list](../standard-library/initializer-list.md) ke kopírování prvků do mapy.

Pro vložení prvku vytvořeného na místě – to znamená, že nejsou prováděny žádné operace kopírování nebo přesouvání – viz [multimap::emplace](#emplace) a [multimap::emplace_hint](#emplace_hint).

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

## <a name="multimapiterator"></a><a name="iterator"></a>multimap::iterátor

Typ, který poskytuje obousměrný iterátor, který může číst nebo upravovat libovolný prvek v multimap.

```cpp
typedef implementation-defined iterator;
```

### <a name="remarks"></a>Poznámky

Definované `iterator` multimapovými body na objekty [value_type](#value_type) `pair<const Key, Type>`, které jsou typu . Hodnota klíče je k dispozici prostřednictvím první dvojice členů a hodnota mapovaného prvku je k dispozici prostřednictvím druhého člena dvojice.

Chcete-li `iterator` odkazovat *iter* ukazující na prvek v **->** multimap, použijte operátor.

Chcete-li získat přístup k hodnotě `Iter->first`klíče pro `(*Iter).first`prvek, použijte , což je ekvivalentní . Chcete-li získat přístup k hodnotě mapované základny pro prvek, použijte `Iter->second`, což je ekvivalentní `(*Iter).second`.

Typ `iterator` lze změnit hodnotu prvku.

### <a name="example"></a>Příklad

Příklad [začátku](#begin) naleznete v příkladu, jak `iterator`deklarovat a používat .

## <a name="multimapkey_comp"></a><a name="key_comp"></a>multimap::key_comp

Načte kopii objektu porovnání použitého k objednání klíčů v multimapě.

```cpp
key_compare key_comp() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí objekt funkce, který multimap používá k objednání jeho prvků.

### <a name="remarks"></a>Poznámky

Uložený objekt definuje členovou funkci

`bool operator( const Key& x, const Key& y);`

který vrátí hodnotu true, pokud *x* v pořadí řazení přísně předchází *y.*

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

## <a name="multimapkey_compare"></a><a name="key_compare"></a>multimap::key_compare

Typ, který poskytuje objekt funkce, který může porovnat dvě klíče řazení k určení relativní pořadí dvou prvků v multimap.

```cpp
typedef Traits key_compare;
```

### <a name="remarks"></a>Poznámky

`key_compare`je synonymem pro `Traits`parametr šablony .

Další informace `Traits` o tématu [třídy multimap.](../standard-library/multimap-class.md)

### <a name="example"></a>Příklad

Příklad pro [key_comp](#key_comp) příklad, jak deklarovat a používat `key_compare`.

## <a name="multimapkey_type"></a><a name="key_type"></a>multimap::key_type

Typ, který popisuje objekt klíče řazení, který představuje každý prvek multimap.

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>Poznámky

`key_type`je synonymem pro `Key`parametr šablony .

Další informace `Key`o tématu naleznete v části Poznámky v tématu [třídy s více mapami.](../standard-library/multimap-class.md)

### <a name="example"></a>Příklad

Příklad [value_type](#value_type) naleznete v příkladu, jak `key_type`deklarovat a používat .

## <a name="multimaplower_bound"></a><a name="lower_bound"></a>multimap::lower_bound

Vrátí iterátor prvnímu prvku v multimap, který s klíčem, který je roven nebo větší než zadaný klíč.

```cpp
iterator lower_bound(const Key& key);

const_iterator lower_bound(const Key& key) const;
```

### <a name="parameters"></a>Parametry

*Klíč*\
Klíč argumentu, který má být porovnán s klíčem řazení prvku z prohledávaného multimap.

### <a name="return-value"></a>Návratová hodnota

Iterátor nebo `const_iterator` který řeší umístění prvku v multimap, který s klíčem, který je roven nebo větší než klíč argumentu nebo který řeší umístění, které následuje poslední prvek v multimap, pokud není nalezena žádná shoda pro klíč.

Pokud `lower_bound` je vrácená hodnota `const_iterator`přiřazena objektu , nelze objekt s více mapami změnit. Pokud `lower_bound` je vrácená hodnota přiřazena **iterátoru**, lze objekt multimap změnit.

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

## <a name="multimapmapped_type"></a><a name="mapped_type"></a>multimap::mapped_type

Typ, který představuje datový typ uložený v multimap.

```cpp
typedef Type mapped_type;
```

### <a name="remarks"></a>Poznámky

`mapped_type`je synonymem pro `Type`parametr šablony .

Další informace `Type` o tématu [třídy multimap.](../standard-library/multimap-class.md)

### <a name="example"></a>Příklad

Příklad [value_type](#value_type) naleznete v příkladu, jak `key_type`deklarovat a používat .

## <a name="multimapmax_size"></a><a name="max_size"></a>multimap::max_size

Vrátí maximální délku multimapy.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>Návratová hodnota

Maximální možná délka multimap.

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

## <a name="multimapmultimap"></a><a name="multimap"></a>multimap::multimapa

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
|*Comp*|Funkce porovnání typu `constTraits` použitého k seřizování prvků `Traits`v mapě, která je ve výchozím nastavení .|
|*Právo*|Objekt map, ze kterého je kopií vytvořen objekt set.|
|*První*|Umístění prvního prvku v rozsahu prvků, které mají být zkopírovány.|
|*Poslední*|Pozice první prvek mimo rozsah prvků, které mají být zkopírovány.|
|*Ilist*|Seznam initializer_list, ze kterého chcete kopírovat prvky.|

### <a name="remarks"></a>Poznámky

Všechny konstruktory uložit typ objektu alokátoru, který spravuje úložiště paměti pro multimap a které mohou být později vráceny voláním [get_allocator](#get_allocator). Parametr allocator je často v deklaraci třídy vynechán a makra předběžného zpracování jsou použita k nahrazení alternativních alokátorů.

Všechny konstruktory inicializují své objekty multimap.

Všechny konstruktory uložit objekt `Traits` funkce typu, který se používá k vytvoření pořadí mezi klávesami multimap a které mohou být později vráceny voláním [key_comp](#key_comp).

První tři konstruktory určují prázdnou počáteční multimapu, druhou určující typ funkce porovnání (*Comp),* která má být použita při stanovení pořadí prvků, a třetí explicitně specifikuje typ alokátoru (*Al*), který má být použit. Klíčové slovo **explicitní** potlačuje určité druhy automatického převodu typu.

Čtvrtý konstruktor určuje kopii multimap *Right*.

Pátý konstruktor určuje kopii multimap přesunutím *Right*.

Šestý, sedmý a osmý konstruktor kopírují členy objektu initializer_list.

Další tři konstruktory zkopírují rozsah `[First, Last)` mapy s rostoucí explicitní při určování typu `Traits` funkce porovnání třídy a alokátoru.

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
    // function of greater than, then insert 2 elements
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

## <a name="multimapoperator"></a><a name="op_eq"></a>multimap::operátor=

Nahradí prvky multimapy kopií jiné hospo-

```cpp
multimap& operator=(const multimap& right);

multimap& operator=(multimap&& right);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|-|-|
|*Právo*|[Multimap](../standard-library/multimap-class.md) kopírované do `multimap`.|

### <a name="remarks"></a>Poznámky

Po vymazání všech existujících `multimap` `operator=` prvků v aplikaci zkopíruje `multimap`nebo přesune obsah *vpravo* do .

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

## <a name="multimappointer"></a><a name="pointer"></a>multimap::pointer

Typ, který poskytuje ukazatel na prvek v multimap.

```cpp
typedef typename allocator_type::pointer pointer;
```

### <a name="remarks"></a>Poznámky

Typ `pointer` lze změnit hodnotu prvku.

Ve většině případů [iterátor](#iterator) by měl být použit pro přístup k prvkům v multimap objektu.

## <a name="multimaprbegin"></a><a name="rbegin"></a>multimap::begin

Vrátí iterátor adresující první prvek v obráceném multimap.

```cpp
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```

### <a name="return-value"></a>Návratová hodnota

Reverzní obousměrný iterátor adresování první prvek v obrácené multimap nebo adresování co byl poslední prvek v unreverse multimap.

### <a name="remarks"></a>Poznámky

`rbegin`se používá s obrácenou multimap [stejně](#begin) jako begin se používá s multimap.

Pokud `rbegin` je vrácená hodnota `const_reverse_iterator`přiřazena aplikaci , nelze objekt s více mapami změnit. Pokud `rbegin` je vrácená hodnota `reverse_iterator`přiřazena objektu , lze objekt s více mapami změnit.

`rbegin`lze itetovat prostřednictvím multimap dozadu.

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
   // through a multimap in a forward order
   cout << "The multimap is: ";
   for ( m1_Iter = m1.begin( ) ; m1_Iter != m1.end( ); m1_Iter++)
      cout << m1_Iter -> first << " ";
      cout << "." << endl;

   // rbegin can be used to start an iteration
   // through a multimap in a reverse order
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

## <a name="multimapreference"></a><a name="reference"></a>multimap::odkaz

Typ, který poskytuje odkaz na prvek uložený v multimap.

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

## <a name="multimaprend"></a><a name="rend"></a>multimap::rend

Vrátí iterátor, který řeší umístění, které následuje poslední prvek v obráceném multimap.

```cpp
const_reverse_iterator rend() const;

reverse_iterator rend();
```

### <a name="return-value"></a>Návratová hodnota

Reverzní obousměrný iterátor, který řeší umístění, které následuje poslední prvek v obráceném multimap (umístění, které předcházelo prvnímu prvku v neobrácené multimap).

### <a name="remarks"></a>Poznámky

`rend`se používá s obrácenou multimap stejně jako [konec](../standard-library/map-class.md#end) se používá s multimap.

Pokud `rend` je vrácená hodnota `const_reverse_iterator`přiřazena aplikaci , nelze objekt s více mapami změnit. Pokud `rend` je vrácená hodnota `reverse_iterator`přiřazena objektu , lze objekt s více mapami změnit.

`rend`lze použít k testování, zda zpětný iterátor dosáhl konce jeho multimap.

Hodnota vrácená `rend` by neměla být odkazována.

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
   // through a multimap in a forward order
   cout << "The multimap is: ";
   for ( m1_Iter = m1.begin( ) ; m1_Iter != m1.end( ); m1_Iter++)
      cout << m1_Iter -> first << " ";
      cout << "." << endl;

   // rbegin can be used to start an iteration
   // through a multimap in a reverse order
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

## <a name="multimapreverse_iterator"></a><a name="reverse_iterator"></a>multimap::reverse_iterator

Typ, který poskytuje obousměrný iterátor, který může číst nebo upravovat prvek v obrácené množiny.

```cpp
typedef std::reverse_iterator<iterator> reverse_iterator;
```

### <a name="remarks"></a>Poznámky

Typ `reverse_iterator` se používá k iterátu prostřednictvím multimap v opačném směru.

Definované `reverse_iterator` multimapovými body na objekty [value_type](#value_type) `pair<const Key, Type>`, které jsou typu . Hodnota klíče je k dispozici prostřednictvím první dvojice členů a hodnota mapovaného prvku je k dispozici prostřednictvím druhého člena dvojice.

Chcete-li `reverse_iterator` odkazovat *rIter* ukazující na prvek v **->** multimap, použijte operátor.

Chcete-li získat přístup k hodnotě `rIter->first`klíče pro `(*rIter).first`prvek, použijte , což je ekvivalentní . Chcete-li získat přístup k hodnotě mapované základny pro prvek, použijte `rIter->second`, což je ekvivalentní `(*rIter).second`.

### <a name="example"></a>Příklad

Příklad pro [rbegin](#rbegin) naleznete v příkladu, `reverse_iterator`jak deklarovat a používat .

## <a name="multimapsize"></a><a name="size"></a>multimap::velikost

Vrátí počet prvků v multimap.

```cpp
size_type size() const;
```

### <a name="return-value"></a>Návratová hodnota

Aktuální délka multimap.

### <a name="example"></a>Příklad

Následující příklad ukazuje použití multimap::size členské funkce.

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

## <a name="multimapsize_type"></a><a name="size_type"></a>multimap::size_type

Nepodepsaný čtyřčíselný typ, který počítá počet prvků v multimap.

```cpp
typedef typename allocator_type::size_type size_type;
```

### <a name="example"></a>Příklad

Příklad [velikosti](#size) naleznete v příkladu, jak deklarovat a používat`size_type`

## <a name="multimapswap"></a><a name="swap"></a>multimap::prohození

Vyměňuje prvky dvou multimap.

```cpp
void swap(
    multimap<Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*Právo*\
Multimap poskytující prvky, které mají být vyměněny, nebo multimap, jehož `left`prvky mají být vyměněny s prvky multimap .

### <a name="remarks"></a>Poznámky

Členská funkce zruší platnost žádné odkazy, ukazatele nebo iterátory, které označují prvky ve dvou multimapách, jejichž prvky jsou vyměňovány.

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

## <a name="multimapupper_bound"></a><a name="upper_bound"></a>multimap::upper_bound

Vrátí iterátor prvnímu prvku v multimap, který s klíčem, který je větší než zadaný klíč.

```cpp
iterator upper_bound(const Key& key);

const_iterator upper_bound(const Key& key) const;
```

### <a name="parameters"></a>Parametry

*Klíč*\
Klíč argumentu, který má být porovnán s klíčem řazení prvku z prohledávaného multimap.

### <a name="return-value"></a>Návratová hodnota

Iterátor nebo `const_iterator` který řeší umístění prvku v multimap, který s klíčem, který je větší než klíč argumentu nebo který řeší umístění, které následuje poslední prvek v multimap, pokud není nalezena žádná shoda pro klíč.

Pokud je vrácená hodnota `const_iterator`přiřazena objektu , nelze objekt s více mapami změnit. Pokud je vrácená hodnota `iterator`přiřazena objektu , lze objekt s více mapami změnit.

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
   // found using a dereferenced iterator addressing the location
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

## <a name="multimapvalue_comp"></a><a name="value_comp"></a>multimap::value_comp

Členská funkce vrátí objekt funkce, který určuje pořadí prvků v multimap porovnáním jejich hodnot klíče.

```cpp
value_compare value_comp() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí objekt funkce porovnání, který multimap používá k objednání jeho prvků.

### <a name="remarks"></a>Poznámky

Pro multimap *m*, pokud dva prvky *e1*(*k1*, *d1*) a `value_type` *e2*(*k2*, *d2*) jsou objekty typu , kde *k1* a *k2* `key_type` jsou jejich klíče typu a *d1* a *d2* jsou jejich data typu `mapped_type`, pak `m.value_comp(e1, e2)` je ekvivalentní . `m.key_comp(k1, k2)`

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

## <a name="multimapvalue_type"></a><a name="value_type"></a>multimap::value_type

Typ, který představuje typ objektu uloženého jako prvek v mapě.

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
   // explicitly to avoid implicit type conversion
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

[Kontejnery](../cpp/containers-modern-cpp.md)\
[Bezpečnost vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Referenční příručka standardní knihovny jazyka C++](../standard-library/cpp-standard-library-reference.md)
