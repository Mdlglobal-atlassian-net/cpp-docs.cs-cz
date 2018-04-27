---
title: map – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- map/std::map
- map/std::map::allocator_type
- map/std::map::const_iterator
- map/std::map::const_pointer
- map/std::map::const_reference
- map/std::map::const_reverse_iterator
- map/std::map::difference_type
- map/std::map::iterator
- map/std::map::key_compare
- map/std::map::key_type
- map/std::map::mapped_type
- map/std::map::pointer
- map/std::map::reference
- map/std::map::reverse_iterator
- map/std::map::size_type
- map/std::map::value_type
- map/std::map::at
- map/std::map::begin
- map/std::map::cbegin
- map/std::map::cend
- map/std::map::clear
- map/std::map::count
- map/std::map::crbegin
- map/std::map::crend
- map/std::map::emplace
- map/std::map::emplace_hint
- map/std::map::empty
- map/std::map::end
- map/std::map::equal_range
- map/std::map::erase
- map/std::map::find
- map/std::map::get_allocator
- map/std::map::insert
- map/std::map::key_comp
- map/std::map::lower_bound
- map/std::map::max_size
- map/std::map::rbegin
- map/std::map::rend
- map/std::map::size
- map/std::map::swap
- map/std::map::upper_bound
- map/std::map::value_comp
dev_langs:
- C++
helpviewer_keywords:
- std::map [C++]
- std::map [C++], allocator_type
- std::map [C++], const_iterator
- std::map [C++], const_pointer
- std::map [C++], const_reference
- std::map [C++], const_reverse_iterator
- std::map [C++], difference_type
- std::map [C++], iterator
- std::map [C++], key_compare
- std::map [C++], key_type
- std::map [C++], mapped_type
- std::map [C++], pointer
- std::map [C++], reference
- std::map [C++], reverse_iterator
- std::map [C++], size_type
- std::map [C++], value_type
- std::map [C++], at
- std::map [C++], begin
- std::map [C++], cbegin
- std::map [C++], cend
- std::map [C++], clear
- std::map [C++], count
- std::map [C++], crbegin
- std::map [C++], crend
- std::map [C++], emplace
- std::map [C++], emplace_hint
- std::map [C++], empty
- std::map [C++], end
- std::map [C++], equal_range
- std::map [C++], erase
- std::map [C++], find
- std::map [C++], get_allocator
- std::map [C++], insert
- std::map [C++], key_comp
- std::map [C++], lower_bound
- std::map [C++], max_size
- std::map [C++], rbegin
- std::map [C++], rend
- std::map [C++], size
- std::map [C++], swap
- std::map [C++], upper_bound
- std::map [C++], value_comp
ms.assetid: 7876f4c9-ebb4-4878-af1e-09364c43af0a
caps.latest.revision: 27
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 58c4353f36ceab0171b2cd928e8fa53a079f960b
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="map-class"></a>map – třída

Používá se pro ukládání a načítání dat z kolekce, ve které je každý prvek pár, který má datovou hodnotu a klíč řazení. Hodnota klíče je jedinečná a je použita k automatickému seřazení dat.

Hodnotu prvku v objektu map lze změnit přímo. Hodnota klíče je konstantní a nelze ji změnit. Namísto toho hodnoty klíčů přidružené ke starým prvkům musí být odstraněny a nové hodnoty klíče musí být vloženy pro nové prvky.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Key,
    class Type,
    class Traits = less<Key>,
    class Allocator=allocator<pair <const Key, Type>>>
class map;
```

### <a name="parameters"></a>Parametry

`Key` Typ klíče data k uložení do mapy.

`Type` Datový typ elementu k uložení do mapy.

`Traits` Typ, který poskytuje funkce objekt, který můžete porovnat dvě hodnoty element jako klíči řazení určit jejich relativní pořadí v mapě. Tento argument je volitelný a binární predikát `less<Key>` je výchozí hodnota.

V C ++ 14 můžete povolit heterogenní vyhledávání zadáním predikát <> std::less, který nemá žádné parametry typu. Další informace najdete v tématu [heterogenní vyhledávání v asociativní kontejnery](../standard-library/stl-containers.md#sequence_containers)

`Allocator` Typ, který představuje uložené allocator objekt, který zapouzdřuje podrobnosti o přidělení a zrušení přidělení paměti na mapě. Tento argument je volitelný a výchozí hodnota je `allocator<pair<const Key, Type> >`.

## <a name="remarks"></a>Poznámky

Standardní knihovna C++ mapy třída je:

- Kontejner s proměnnou velikostí, který efektivně načte hodnoty prvku na základě přidružených hodnot klíče.

- Oboustranný, protože poskytuje obousměrné iterátory pro přístup k jeho prvkům.

- Seřazená, protože její prvky jsou seřazeny podle hodnot klíče podle zadané funkce porovnání.

- Jedinečný. protože každý z jeho elementy musí mít jedinečný klíč.

- Kontejner asociativních párů, protože jeho prvky hodnoty dat se liší od hodnot klíčů.

- Třída šablony, protože funkce, které poskytuje jsou obecné a nezávislé na prvku nebo typu klíče. Datové typy použité pro prvky a klíče jsou zadány jako parametry v šabloně třídy společně s funkcí porovnání a alokátorem.

Iterator poskytuje třídu mapy je iterator obousměrného ale [vložit](#insert) a [mapy](#map) členské funkce třídy mají verze, které jako parametry šablony trvat slabší vstupní iterator, jejichž požadavky na funkce jsou méně než ty, které zaručit třídou iterátory obousměrné. Různé koncepty iterátorů se týkají upřesnění jejich funkčnosti. Každý koncept iterátoru má vlastní sadu požadavků a algoritmy, které s ním pracují musí být omezeny těmito požadavky. Ke vstupnímu iterátoru lze přistoupit přes ukazatel pro odkazování na některý objekt a může být zvýšena na další iterátor v sekvenci.

Doporučujeme založit volbu typu kontejneru podle druhu vyhledávání a vkládání, který je požadován aplikací. Asociativní kontejnery jsou optimalizovány pro operace vyhledávání, vkládání a odstranění. Členské funkce, které explicitně podporují tyto operace jsou provedeny v nejhorším čase, který je úměrný logaritmu počtu prvků v kontejneru. Vkládání prvků nezruší platnost žádných iterátorů a odstranění prvků zruší platnost pouze těch iterátorů, které výslovně odkazovaly na odstraněné prvky.

Doporučujeme objekt map vytvořit jako asociativní kontejner volby, pokud jsou v aplikaci splněny podmínky, které přiřazují hodnoty klíčům. Model tohoto typu struktury je uspořádaný seznam jednoznačně se vyskytujících klíčových slov, které mají přidružené hodnoty řetězce poskytující definice. Má-li slovo více než jednu správnou definici, takže tento klíč není jedinečný, potom by třída multimap měla být zvoleným kontejnerem. Pokud je uložen jen seznam slov, pak by třída set měla být vhodným kontejnerem. Pokud je povoleno více výskytů slova, měla by být použita třída multiset.

Mapy řadí elementy jimi řídí voláním funkce uložené objektu typu [key_compare –](#key_compare). Tento objekt uložené je porovnání funkce, které je přístupné pomocí volání [key_comp –](#key_comp) metoda. Obecně jsou dva dané prvky porovnány pro určení, zda je jeden menší než druhý nebo zda jsou stejné. Při porovnání všech prvků je vytvořena seřazená sekvence neekvivalentních prvků.

> [!NOTE]
> Funkce porovnání je binární predikát, který indukuje přísné slabé seřazení ve standardním matematickém smyslu. Binární predikátem f(x,y) je objekt funkce, která má dva objekty argument x a y a návratová hodnota `true` nebo `false`. Řazení vynucená pro sadu je striktní weak řazení Pokud binární predikát je Nereflexivní, antisymetrického a přenositelné a pokud ekvivalenční přenositelné, kde dva objekty x a y jsou definovány jako ekvivalentní při obě                     f (x, y) a f(y,x) `false`. Pokud silnější podmínka rovnosti mezi klíči nahradí ekvivalenci, stane se pořadí celkovým (v tom smyslu, že všechny prvky jsou uspořádány ve vztahu k sobě navzájem) a odpovídající klíče budou od sebe nerozeznatelné.
>
> V C ++ 14 můžete povolit heterogenní vyhledávání zadáním `std::less<>` nebo `std::greater<>` predikát, který nemá žádné parametry typu. Další informace najdete v tématu [heterogenní vyhledávání v asociativní kontejnery](../standard-library/stl-containers.md#sequence_containers)

## <a name="members"></a>Členové

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[mapy](#map)|Vytvoří seznam určité velikosti nebo elementy konkrétní hodnotu nebo s konkrétní `allocator` nebo jako kopii některé další mapy.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[allocator_type –](#allocator_type)|Typedef pro `allocator` tříd pro objekt map.|
|[const_iterator](#const_iterator)|Typedef pro obousměrnou iterator, který může číst `const` element v mapě.|
|[const_pointer](#const_pointer)|Typedef pro ukazatel na `const` element v mapování.|
|[const_reference](#const_reference)|Typedef pro odkaz na `const` element uložené v mapě pro čtení a provádění `const` operace.|
|[const_reverse_iterator](#const_reverse_iterator)|Typ, který poskytuje obousměrné iterator, který může číst všechny `const` element v mapě.|
|[difference_type](#difference_type)|Definice typu celého čísla se znaménkem pro počet prvků objektu map v rozsahu mezi prvky, na které odkazují iterátory.|
|[Iterator](#iterator)|Definice typu obousměrného iterátoru, který může číst nebo upravovat libovolný prvek v objektu map.|
|[key_compare](#key_compare)|Definice typu poskytující objekt funkce, který může porovnat dva klíče řazení pro určení relativního pořadí dvou prvků v objektu map.|
|[key_type](#key_type)|Definice typu klíče řazení uloženého v jednotlivých prvcích objektu map.|
|[mapped_type](#mapped_type)|Definice typu dat uložených v jednotlivých prvcích objektu map.|
|[Ukazatele](#pointer)|Typedef pro ukazatel na `const` element v mapování.|
|[Referenční dokumentace](#reference)|Definice typu odkazu na prvek uložený v objektu map.|
|[reverse_iterator](#reverse_iterator)|Definice typu obousměrného iterátoru, který může číst nebo upravovat prvek v obráceném objektu map.|
|[size_type](#size_type)|Celočíselná definice typu bez znaménka pro počet prvků v objektu map.|
|[value_type](#value_type)|Definice typu pro typ objektu, který je uložen jako prvek v objektu map.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[at](#at)|Vyhledá prvek se zadanou hodnotou klíče.|
|[Začátek](#begin)|Vrátí iterátor odkazující na první prvek v objektu map.|
|[cbegin –](#cbegin)|Vrátí konstantní iterátor odkazující na první prvek v objektu map.|
|[cend –](#cend)|Vrátí konstantní iterátor za koncem.|
|[Zrušte zaškrtnutí](#clear)|Odstraní všechny prvky objektu map.|
|[Počet](#count)|Vrátí počet prvků objektu map, jejichž klíč odpovídá klíči zadaného parametrem.|
|[crbegin](#crbegin)|Vrátí konstantní iterátor, který odkazuje na první prvek v obráceném objektu map.|
|[crend –](#crend)|Vrátí konstantní iterátor, který odkazuje na umístění za posledním prvkem v převráceném objektu map.|
|[emplace –](#emplace)|Vloží vytvořený prvek na místo do objektu map.|
|[emplace_hint –](#emplace_hint)|Vloží vytvořený prvek s náznakem umístění na místo do objektu map.|
|[prázdný](#empty)|Vrátí `true` Pokud mapu je prázdný.|
|[End](#end)|Vrátí iterátor za koncem.|
|[equal_range](#equal_range)|Vrátí pár iterátorů. První iterator v páru odkazuje na prvním elementem v `map` s klíčem, který je větší než je zadaný klíč. Druhý iterator v páru odkazuje na prvním elementem v `map` s klíčem, který je rovna nebo větší než klíč.|
|[vymazání](#erase)|Odebere prvek nebo rozsah prvků v objektu map od zadané pozice.|
|[Najít](#find)|Vrátí iterátor odkazující na umístění prvku v objektu map, který má klíč stejný jako zadaný klíč.|
|[get_allocator](#get_allocator)|Vrátí kopii `allocator` objekt, který se používá k vytvoření mapy.|
|[Vložení](#insert)|Vloží prvek nebo rozsah prvků na určenou pozici do objektu map.|
|[key_comp](#key_comp)|Vrátí kopii objektu porovnání, která je použit pro seřazení klíčů v objektu map.|
|[lower_bound –](#lower_bound)|Vrátí iterátor na první prvek objektu map s hodnotou klíče, který je roven nebo větší než zadaný klíč.|
|[max_size](#max_size)|Vrátí maximální délku objektu map.|
|[rbegin –](#rbegin)|Vrátí iterátor odkazující na první prvek v obráceném objektu map.|
|[rend –](#rend)|Vrátí iterátor, který odkazuje na umístění za posledním prvkem v převráceném objektu map.|
|[Velikost](#size)|Vrátí počet prvků v objektu map.|
|[Swap](#swap)|Zamění prvky dvou objektů map.|
|[upper_bound –](#upper_bound)|Vrátí iterátor na první prvek objektu map s hodnotou klíče, který je větší než zadaný klíč.|
|[value_comp](#value_comp)|Získá kopii objektu porovnání použitého pro seřazení hodnot prvků objektu map.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operátor&#91;&#93;](#op_at)|Vloží prvek do objektu map se zadanou hodnotou klíče.|
|[operátor =](#op_eq)|Nahradí prvky objektu map kopií jiného objektu map.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<mapy >

**Namespace:** – std

## <a name="allocator_type"></a>  map::allocator_type

Typ, který reprezentuje allocator – třída objektu mapy.

```cpp
typedef Allocator allocator_type;
```

### <a name="example"></a>Příklad

Podívejte se příklad [get_allocator –](#get_allocator) pro příklad, který používá `allocator_type`.

## <a name="at"></a>  map::AT

Vyhledá prvek se zadanou hodnotou klíče.

```cpp
Type& at(const Key& key);

const Type& at(const Key& key) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|-|-|
|Parametr|Popis|
|`key`|Hodnota klíče najít.|

### <a name="return-value"></a>Návratová hodnota

Odkaz na hodnotu dat nalezen prvek.

### <a name="remarks"></a>Poznámky

Pokud není nalezena hodnota klíče argument, pak funkce vyvolá objekt třídy [out_of_range – třída](../standard-library/out-of-range-class.md).

### <a name="example"></a>Příklad

```cpp
// map_at.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

typedef std::map<char, int> Mymap;
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

## <a name="begin"></a>  map::begin

Vrátí iterator adresování prvním elementem v mapě.

```cpp
const_iterator begin() const;

iterator begin();
```

### <a name="return-value"></a>Návratová hodnota

Obousměrné iterator, který adresování prvním elementem v mapě nebo umístění úspěšné prázdný mapy.

### <a name="example"></a>Příklad

```cpp
// map_begin.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int> m1;

   map <int, int> :: iterator m1_Iter;
   map <int, int> :: const_iterator m1_cIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 0, 0 ) );
   m1.insert ( Int_Pair ( 1, 1 ) );
   m1.insert ( Int_Pair ( 2, 4 ) );

   m1_cIter = m1.begin ( );
   cout << "The first element of m1 is " << m1_cIter -> first << endl;

   m1_Iter = m1.begin ( );
   m1.erase ( m1_Iter );

   // The following 2 lines would err because the iterator is const
   // m1_cIter = m1.begin ( );
   // m1.erase ( m1_cIter );

   m1_cIter = m1.begin( );
   cout << "The first element of m1 is now " << m1_cIter -> first << endl;
}
```

```Output
The first element of m1 is 0
The first element of m1 is now 1
```

## <a name="cbegin"></a>  map::cbegin

Vrátí `const` iterator, která řeší umístění bezprostředně za posledním prvkem v rozsahu.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>Návratová hodnota

A `const` obousměrného iterator adresování prvním elementem v rozsahu nebo umístění právě přesahuje za konec prázdného rozsahu (pro prázdného rozsahu, `cbegin() == cend()`).

### <a name="remarks"></a>Poznámky

S návratovou hodnotou `cbegin`, nemůže být upravena elementů v rozsahu.

Můžete použít tuto funkci člen místě `begin()` – členská funkce zaručit, že je návratovou hodnotu `const_iterator`. Obvykle se používá ve spojení s [automaticky](../cpp/auto-cpp.md) odvození – klíčové slovo, zadejte, jak je znázorněno v následujícím příkladu. V příkladu, vezměte v úvahu `Container` upravitelná (jinou hodnotu než `const`) kontejneru libovolného typu, který podporuje `begin()` a `cbegin()`.

```cpp
auto i1 = Container.begin();
// i1 is Container<T>::iterator
auto i2 = Container.cbegin();

// i2 is Container<T>::const_iterator
```

## <a name="cend"></a>  map::cend

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

## <a name="clear"></a>  map::clear

Odstraní všechny prvky objektu map.

```cpp
void clear();
```

### <a name="example"></a>Příklad

Následující příklad ukazuje použití map::clear – členská funkce.

```cpp
// map_clear.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main()
{
    using namespace std;
    map<int, int> m1;
    map<int, int>::size_type i;
    typedef pair<int, int> Int_Pair;

    m1.insert(Int_Pair(1, 1));
    m1.insert(Int_Pair(2, 4));

    i = m1.size();
    cout << "The size of the map is initially "
         << i << "." << endl;

    m1.clear();
    i = m1.size();
    cout << "The size of the map after clearing is "
         << i << "." << endl;
}
```

```Output
The size of the map is initially 2.
The size of the map after clearing is 0.
```

## <a name="const_iterator"></a>  map::const_iterator

Typ, který poskytuje obousměrné iterator, který může číst **const** element v mapě.

```cpp
typedef implementation-defined const_iterator;
```

### <a name="remarks"></a>Poznámky

Typ `const_iterator` nelze použít k úpravě hodnota elementu.

`const_iterator` Definované bodů mapy pro elementy, které jsou objekty [value_type](#value_type), která je typu `pair` \< **constKey**, **typ**> , jejichž první člen je klíčem k elementu a jehož sekundu člen je namapované datum uchovávat elementem.

K dereference `const_iterator` `cIter` odkazující na element mapy, použijte **->** operátor.

Chcete-li získat přístup k hodnotě klíče pro element, použijte `cIter`  ->  **první**, což je totéž jako (\* `cIter`). **první**.

Chcete-li získat přístup k hodnotě namapované datum pro element, použijte `cIter`  ->  **druhý**, což je totéž jako (\* `cIter`). **druhý**.

### <a name="example"></a>Příklad

Podívejte se příklad [začít](#begin) pro příklad, který používá `const_iterator`.

## <a name="const_pointer"></a>  map::const_pointer

Typ, který poskytuje odkazy **const** element v mapování.

```cpp
typedef typename allocator_type::const_pointer const_pointer;
```

### <a name="remarks"></a>Poznámky

Typ `const_pointer` nelze použít k úpravě hodnota elementu.

Ve většině případů [iterator](#iterator) se má použít pro přístup k elementům v objektu mapy.

## <a name="const_reference"></a>  map::const_reference

Typ, který obsahuje odkaz na **const** element uložené v mapě pro čtení a provádění **const** operace.

```cpp
typedef typename allocator_type::const_reference const_reference;
```

### <a name="example"></a>Příklad

```cpp
// map_const_ref.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int> m1;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );

   // Declare and initialize a const_reference &Ref1
   // to the key of the first element
   const int &Ref1 = ( m1.begin( ) -> first );

   // The following line would cause an error as the
   // non-const_reference cannot be used to access the key
   // int &Ref1 = ( m1.begin( ) -> first );

   cout << "The key of first element in the map is "
        << Ref1 << "." << endl;

   // Declare and initialize a reference &Ref2
   // to the data value of the first element
   int &Ref2 = ( m1.begin( ) -> second );

   cout << "The data value of first element in the map is "
        << Ref2 << "." << endl;
}
```

```Output
The key of first element in the map is 1.
The data value of first element in the map is 10.
```

## <a name="const_reverse_iterator"></a>  map::const_reverse_iterator

Typ, který poskytuje obousměrné iterator, který může číst všechny **const** element v mapě.

```cpp
typedef std::reverse_iterator<const_iterator> const_reverse_iterator;
```

### <a name="remarks"></a>Poznámky

Typ `const_reverse_iterator` nelze změnit hodnotu elementu a je použít k iteraci v rámci mapy pozpátku.

`const_reverse_iterator` Definované bodů mapy pro elementy, které jsou objekty [value_type](#value_type), která je typu `pair<const Key, Type>`, jehož první člen je klíčem k elementu a jehož sekundu člen je namapované datum uchovávat elementem.

K dereference `const_reverse_iterator crIter` odkazující na element mapy, použijte **->** operátor.

Chcete-li získat přístup k hodnotě klíče pro element, použijte `crIter`  ->  **první**, což je totéž jako (\* `crIter`). **první**.

Chcete-li získat přístup k hodnotě namapované datum pro element, použijte `crIter`  ->  **druhý**, což je totéž jako (\* `crIter`). **první**.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [rend](#rend) příklad toho, jak deklarace a používání `const_reverse_iterator`.

## <a name="count"></a>  map::Count

Vrátí počet prvků v mapě, jehož klíč odpovídá parametru zadaný klíč.

```cpp
size_type count(const Key& key) const;
```

### <a name="parameters"></a>Parametry

`key` Hodnota klíče elementů lze porovnat z mapování.

### <a name="return-value"></a>Návratová hodnota

1, pokud mapy obsahuje element, jehož klíč řazení shoduje s klíčem parametr; 0, pokud Mapa neobsahuje element s odpovídající klíč.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí počet prvků *x* v rozsahu

[ `lower_bound` (_ *Klíč* ), `upper_bound` (\_ *klíč* ))

což je 0 nebo 1 v případě map, který je jedinečný asociativní kontejner.

### <a name="example"></a>Příklad

Následující příklad ukazuje použití map::count – členská funkce.

```cpp
// map_count.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main()
{
    using namespace std;
    map<int, int> m1;
    map<int, int>::size_type i;
    typedef pair<int, int> Int_Pair;

    m1.insert(Int_Pair(1, 1));
    m1.insert(Int_Pair(2, 1));
    m1.insert(Int_Pair(1, 4));
    m1.insert(Int_Pair(2, 1));

    // Keys must be unique in map, so duplicates are ignored
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
The number of elements in m1 with a sort key of 1 is: 1.
The number of elements in m1 with a sort key of 2 is: 1.
The number of elements in m1 with a sort key of 3 is: 0.
```

## <a name="crbegin"></a>  map::crbegin

Vrátí const iterator adresování prvním elementem v invertovaných mapy.

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>Návratová hodnota

Const reverse obousměrného iterator adresování prvním elementem v odstínech [mapy](../standard-library/map-class.md) nebo řešení, co je posledním prvkem v unreversed `map`.

### <a name="remarks"></a>Poznámky

`crbegin` se používá s odstínech `map` stejně jako [začít](#begin) se používá s `map`.

S návratovou hodnotou `crbegin`, `map` objekt nelze změnit

`crbegin` lze použít k iteraci v rámci `map` zpětné.

### <a name="example"></a>Příklad

```cpp
// map_crbegin.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int> m1;

   map <int, int> :: const_reverse_iterator m1_crIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );

   m1_crIter = m1.crbegin( );
   cout << "The first element of the reversed map m1 is "
        << m1_crIter -> first << "." << endl;
}
```

```Output
The first element of the reversed map m1 is 3.
```

## <a name="crend"></a>  map::crend

Vrátí const iterator, která řeší umístění úspěšné posledním prvkem v invertovaných mapy.

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>Návratová hodnota

Const reverse iterator obousměrného, která řeší umístění úspěšné posledním prvkem v odstínech [mapy](../standard-library/map-class.md) (umístění, které měl před prvním elementem v unreversed `map`).

### <a name="remarks"></a>Poznámky

`crend` se používá s odstínech mapu stejně jako [end](#end) se používá s `map`.

S návratovou hodnotou `crend`, `map` objekt nelze změnit.

`crend` můžete použít k testování na tom, jestli má zpětné iterator dosáhla konce jeho `map`.

Hodnoty vrácené `crend` by neměl být vyhodnoceny odkazy.

### <a name="example"></a>Příklad

```cpp
// map_crend.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int> m1;

   map <int, int> :: const_reverse_iterator m1_crIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );

   m1_crIter = m1.crend( );
   m1_crIter--;
   cout << "The last element of the reversed map m1 is "
        << m1_crIter -> first << "." << endl;
}
```

```Output
The last element of the reversed map m1 is 1.
```

## <a name="difference_type"></a>  map::difference_type

Typ se znaménkem, který můžete použít k reprezentování počet elementů mapy v rozsahu mezi elementy, na kterou iterátory odkazuje.

```cpp
typedef allocator_type::difference_type difference_type;
```

### <a name="remarks"></a>Poznámky

`difference_type` Je typ vrácena, pokud odečtením nebo zvyšování prostřednictvím iterátory kontejneru. `difference_type` Se obvykle používá k reprezentování počet elementů v rozsahu *[první, poslední)* mezi iterátory `first` a `last`, obsahuje element, na kterou odkazuje `first` a rozsahu elementy až do, s výjimkou elementu na kterou odkazuje `last`.

Všimněte si, že i když `difference_type` je k dispozici pro všechny iterátory, které splňují požadavky vstupní iterator, který obsahuje třídu obousměrného iterátory nepodporuje reverzibilního kontejnery, jako je sada, odčítání mezi iterátory pouze iterátory náhodný přístup poskytuje náhodný přístup kontejner například vektoru podporována.

### <a name="example"></a>Příklad

```cpp
// map_diff_type.cpp
// compile with: /EHsc
#include <iostream>
#include <map>
#include <algorithm>

int main( )
{
   using namespace std;
   map <int, int> m1;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 3, 20 ) );
   m1.insert ( Int_Pair ( 2, 30 ) );

   map <int, int>::iterator m1_Iter, m1_bIter, m1_eIter;
   m1_bIter = m1.begin( );
   m1_eIter = m1.end( );

   // Count the number of elements in a map
   map <int, int>::difference_type  df_count = 1;
   m1_Iter = m1.begin( );
   while ( m1_Iter != m1_eIter)
   {
      df_count++;
      m1_Iter++;
   }

   cout << "The number of elements in the map m1 is: "
        << df_count << "." << endl;
}
```

```Output
The number of elements in the map m1 is: 4.
```

## <a name="emplace"></a>  map::emplace

Vloží element sestavený na místě (žádné kopírování nebo přesunutí operací) do mapy.

```cpp
template <class... Args>
pair<iterator, bool>
emplace(
    Args&&... args);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|-|-|
|Parametr|Popis|
|`args`|Argumenty předané vytvořit element, který má být vložen do mapy, pokud již obsahuje element, jehož hodnota je ekvivalentně řazení.|

### <a name="return-value"></a>Návratová hodnota

A [pár](../standard-library/pair-structure.md) jejichž `bool` součást je hodnota true, pokud došlo vložení a hodnotu false, pokud mapy už obsažený element odpovídající hodnotou v řazení. Komponenta iterátoru dvojice návratové hodnoty odkazuje na nově vložený prvek, pokud má komponenta `bool` hodnotu true, nebo na existující prvek, pokud má komponenta `bool` hodnotu false.

Pro přístup k komponenta iterator `pair` `pr`, použijte `pr.first`; chcete ji dereference, použijte `*pr.first`. Chcete-li přistupovat ke komponentě `bool`, použijte `pr.second`. Příklad naleznete v ukázce kódu dále v tomto článku.

### <a name="remarks"></a>Poznámky

Pomocí této funkce jsou zneplatněny žádné iterátory nebo odkazy.

Během. uložení Pokud je vyvolána výjimka, stavu kontejneru nezměnil.

[Value_type](#value_type) elementu je pár, aby bude použita hodnota elementu dvojici seřazené s první součást, která je rovna hodnotě klíče a druhá součást, která je rovna hodnotě dat prvku.

### <a name="example"></a>Příklad

```cpp
// map_emplace.cpp
// compile with: /EHsc
#include <map>
#include <string>
#include <iostream>

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
    map<int, string> m1;

    auto ret = m1.emplace(10, "ten");

    if (!ret.second){
        auto pr = *ret.first;
        cout << "Emplace failed, element with key 10 already exists."
            << endl << "  The existing element is (" << pr.first << ", " << pr.second << ")"
            << endl;
        cout << "map not modified" << endl;
    }
    else{
        cout << "map modified, now contains ";
        print(m1);
    }
    cout << endl;

    ret = m1.emplace(10, "one zero");

    if (!ret.second){
        auto pr = *ret.first;
        cout << "Emplace failed, element with key 10 already exists."
            << endl << "  The existing element is (" << pr.first << ", " << pr.second << ")"
            << endl;
    }
    else{
        cout << "map modified, now contains ";
        print(m1);
    }
    cout << endl;
}

```

## <a name="emplace_hint"></a>  map::emplace_hint

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
|Parametr|Popis|
|`args`|Argumenty předané vytvořit element, který má být vložen do mapy, pokud mapy již obsahuje daný element nebo obecně platí, pokud ji už obsahuje element, jehož klíč je ekvivalentně řazení.|
|`where`|Místo zahájení vyhledání správného bodu vložení. (Pokud tento bod okamžitě předchází `where`, vložení se může objevit v amortizovaný konstantní čas místo logaritmické času.)|

### <a name="return-value"></a>Návratová hodnota

Iterátor do nově vloženou elementu.

Pokud vložení se nezdařilo, protože element již existuje, vrátí iterovat do existujícího elementu jeho klíčem.

### <a name="remarks"></a>Poznámky

Pomocí této funkce jsou zneplatněny žádné iterátory nebo odkazy.

Během. uložení Pokud je vyvolána výjimka, stavu kontejneru nezměnil.

[Value_type](#value_type) elementu je pár, aby bude použita hodnota elementu dvojici seřazené s první součást, která je rovna hodnotě klíče a druhá součást, která je rovna hodnotě dat prvku.

### <a name="example"></a>Příklad

```cpp
// map_emplace.cpp
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
    map<string, string> m1;

    // Emplace some test data
    m1.emplace("Anna", "Accounting");
    m1.emplace("Bob", "Accounting");
    m1.emplace("Carmine", "Engineering");

    cout << "map starting data: ";
    print(m1);
    cout << endl;

    // Emplace with hint
    // m1.end() should be the "next" element after this emplacement
    m1.emplace_hint(m1.end(), "Doug", "Engineering");

    cout << "map modified, now contains ";
    print(m1);
    cout << endl;
}

```

## <a name="empty"></a>  map::Empty

Testy, pokud je prázdný mapování.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE,** Pokud mapy je prázdná. **false** Pokud mapy neprázdný.

### <a name="example"></a>Příklad

```cpp
// map_empty.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int> m1, m2;

   typedef pair <int, int> Int_Pair;
   m1.insert ( Int_Pair ( 1, 1 ) );

   if ( m1.empty( ) )
      cout << "The map m1 is empty." << endl;
   else
      cout << "The map m1 is not empty." << endl;

   if ( m2.empty( ) )
      cout << "The map m2 is empty." << endl;
   else
      cout << "The map m2 is not empty." << endl;
}
```

```Output
The map m1 is not empty.
The map m2 is empty.
```

## <a name="end"></a>  map::end

Vrátí iterátor za koncem.

```cpp
const_iterator end() const;


iterator end();
```

### <a name="return-value"></a>Návratová hodnota

Iterator minulosti the-end. Pokud mapy je prázdný, pak `map::end() == map::begin()`.

### <a name="remarks"></a>Poznámky

**end** slouží k otestování, jestli iterovat uplynutí konec jeho mapy.

Hodnoty vrácené **end** by neměl být vyhodnoceny odkazy.

Příklad kódu, najdete v části [map::find](#find).

## <a name="equal_range"></a>  map::equal_range

Vrátí pár iterátory, které představují [lower_bound –](#lower_bound) klíče a [upper_bound –](#upper_bound) klíče.

```cpp
pair <const_iterator, const_iterator> equal_range (const Key& key) const;

pair <iterator, iterator> equal_range (const Key& key);
```

### <a name="parameters"></a>Parametry

`key` Hodnota klíče argument být porovnána s klíč řazení elementu z prohledávaný mapy.

### <a name="return-value"></a>Návratová hodnota

Pro přístup k první iterator páru `pr` vrácené funkcí člen, použijte `pr`. **první**a pokud chcete dereference iterator dolní mez, použijte \*( `pr`. **nejprve**). Pro přístup k druhý iterator páru `pr` vrácené funkcí člen, použijte `pr`. **druhý**a pokud chcete dereference iterator horní mez, použijte \*( `pr`. **druhý**).

### <a name="example"></a>Příklad

```cpp
// map_equal_range.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   typedef map <int, int, less<int> > IntMap;
   IntMap m1;
   map <int, int> :: const_iterator m1_RcIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );

   pair <IntMap::const_iterator, IntMap::const_iterator> p1, p2;
   p1 = m1.equal_range( 2 );

   cout << "The lower bound of the element with "
        << "a key of 2 in the map m1 is: "
        << p1.first -> second << "." << endl;

   cout << "The upper bound of the element with "
        << "a key of 2 in the map m1 is: "
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
      cout << "The map m1 doesn't have an element "
           << "with a key less than 40." << endl;
   else
      cout << "The element of map m1 with a key >= 40 is: "
           << p2.first -> first << "." << endl;
}
```

```Output
The lower bound of the element with a key of 2 in the map m1 is: 20.
The upper bound of the element with a key of 2 in the map m1 is: 30.
A direct call of upper_bound( 2 ) gives 30,
 matching the 2nd element of the pair returned by equal_range( 2 ).
The map m1 doesn't have an element with a key less than 40.
```

## <a name="erase"></a>  map::Erase

Odebere element nebo rozsahu prvků v mapě ze zadaných pozic nebo odebere prvky, které odpovídají zadaným klíčem.

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

`Key` Hodnota klíče elementů odeberou.

### <a name="return-value"></a>Návratová hodnota

Pro první dva členské funkce obousměrné iterator, označí první prvek zbývající nad rámec žádné elementy, odebrat nebo element, který je konci mapy, pokud neexistuje žádný takový prvek.

Pro třetí – členská funkce vrátí počet prvků, které byly odebrány z mapování.

### <a name="example"></a>Příklad

```cpp
// map_erase.cpp
// compile with: /EHsc
#include <map>
#include <string>
#include <iostream>
#include <iterator> // next() and prev() helper functions
#include <utility>  // make_pair()

using namespace std;

using mymap = map<int, string>;

void printmap(const mymap& m) {
    for (const auto& elem : m) {
        cout << " [" << elem.first << ", " << elem.second << "]";
    }
    cout << endl << "size() == " << m.size() << endl << endl;
}

int main()
{
    mymap m1;

    // Fill in some data to test with, one at a time
    m1.insert(make_pair(1, "A"));
    m1.insert(make_pair(2, "B"));
    m1.insert(make_pair(3, "C"));
    m1.insert(make_pair(4, "D"));
    m1.insert(make_pair(5, "E"));

    cout << "Starting data of map m1 is:" << endl;
    printmap(m1);
    // The 1st member function removes an element at a given position
    m1.erase(next(m1.begin()));
    cout << "After the 2nd element is deleted, the map m1 is:" << endl;
    printmap(m1);

    // Fill in some data to test with, one at a time, using an intializer list
    mymap m2
    {
        { 10, "Bob" },
        { 11, "Rob" },
        { 12, "Robert" },
        { 13, "Bert" },
        { 14, "Bobby" }
    };

    cout << "Starting data of map m2 is:" << endl;
    printmap(m2);
    // The 2nd member function removes elements
    // in the range [First, Last)
    m2.erase(next(m2.begin()), prev(m2.end()));
    cout << "After the middle elements are deleted, the map m2 is:" << endl;
    printmap(m2);

    mymap m3;

    // Fill in some data to test with, one at a time, using emplace
    m3.emplace(1, "red");
    m3.emplace(2, "yellow");
    m3.emplace(3, "blue");
    m3.emplace(4, "green");
    m3.emplace(5, "orange");
    m3.emplace(6, "purple");
    m3.emplace(7, "pink");

    cout << "Starting data of map m3 is:" << endl;
    printmap(m3);
    // The 3rd member function removes elements with a given Key
    mymap::size_type count = m3.erase(2);
    // The 3rd member function also returns the number of elements removed
    cout << "The number of elements removed from m3 is: " << count << "." << endl;
    cout << "After the element with a key of 2 is deleted, the map m3 is:" << endl;
    printmap(m3);
}

```

## <a name="find"></a>  map::Find

Vrátí iterátor, který odkazuje na umístění elementu v mapu, která má klíč ekvivalentní k zadanému klíči.

```cpp
iterator find(const Key& key);


const_iterator find(const Key& key) const;
```

### <a name="parameters"></a>Parametry

`key` Hodnota klíče odpovídala klíč řazení elementu z mapy být vyhledán.

### <a name="return-value"></a>Návratová hodnota

Iterátor, který odkazuje na umístění element se zadaným klíčem nebo umístění úspěšné posledním prvkem v mapě ( `map::end()`) Pokud není nalezena žádná shoda pro klíč.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí iterátor, který odkazuje na element v mapě, jehož klíč řazení je ekvivalentní argument klíč v predikátu Binární indukuje řazení podle menší než srovnání vztah.

Pokud vrátí hodnotu, která **najít** je přiřazena k **const_iterator –**, mapy objekt nelze změnit. Pokud návratová hodnota **najít** je přiřazena k **iterator**, je možné upravit objekt map

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
    map<int, string> m1({ { 40, "Zr" }, { 45, "Rh" } });
    cout << "The starting map m1 is (key, value):" << endl;
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

    cout << "The modified map m1 is (key, value):" << endl;
    print_collection(m1);
    cout << endl;
    findit(m1, 45);
    findit(m1, 6);
}

```

## <a name="get_allocator"></a>  map::get_allocator

Vrátí kopii allocator objekt použitý k vytvoření mapy.

```cpp
allocator_type get_allocator() const;
```

### <a name="return-value"></a>Návratová hodnota

Allocator používané mapy.

### <a name="remarks"></a>Poznámky

Alokátorů pro třídu mapy zadejte, jak třída spravuje úložiště. Alokátorů výchozí součástí standardní knihovna C++ – třídy kontejnerů postačí pro většinu programovacích potřeb. Psaní a pomocí vlastní allocator – třída je rozšířená C++.

### <a name="example"></a>Příklad

```cpp
// map_get_allocator.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int>::allocator_type m1_Alloc;
   map <int, int>::allocator_type m2_Alloc;
   map <int, double>::allocator_type m3_Alloc;
   map <int, int>::allocator_type m4_Alloc;

   // The following lines declare objects
   // that use the default allocator.
   map <int, int> m1;
   map <int, int, allocator<int> > m2;
   map <int, double, allocator<double> > m3;

   m1_Alloc = m1.get_allocator( );
   m2_Alloc = m2.get_allocator( );
   m3_Alloc = m3.get_allocator( );

   cout << "The number of integers that can be allocated\n"
        << "before free memory is exhausted: "
        << m2.max_size( ) << ".\n" << endl;

   cout << "The number of doubles that can be allocated\n"
        << "before free memory is exhausted: "
        << m3.max_size( ) <<  ".\n" << endl;

   // The following line creates a map m4
   // with the allocator of map m1.
   map <int, int> m4( less<int>( ), m1_Alloc );

   m4_Alloc = m4.get_allocator( );

   // Two allocators are interchangeable if
   // storage allocated from each can be
   // deallocated with the other
   if( m1_Alloc == m4_Alloc )
   {
      cout << "The allocators are interchangeable." << endl;
   }
   else
   {
      cout << "The allocators are not interchangeable." << endl;
   }
}
```

## <a name="insert"></a>  map::Insert

Vloží elementu nebo rozsahu prvků do mapy.

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
|Parametr|Popis|
|`Val`|Hodnota elementu, který má být vložen do mapy, pokud již obsahuje element, jehož klíč je ekvivalentně řazení.|
|`Where`|Místo zahájení vyhledání správného bodu vložení. (Pokud tento bod okamžitě předchází `Where`, vložení se může objevit v amortizovaný konstantní čas místo logaritmické času.)|
|`ValTy`|Parametr šablony, která určuje typ argumentu, mapy můžete použít k vytvoření element [value_type](#value_type)a představuje výhodu předávání `Val` jako argument.|
|`First`|Pozice prvního prvku, který chcete zkopírovat.|
|`Last`|Pozice bezprostředně za posledním prvkem, který chcete zkopírovat.|
|`InputIterator`|Argument funkce šablony, který splňuje požadavky [vstupní iterator](../standard-library/input-iterator-tag-struct.md) který odkazuje na elementy typu, který slouží k vytvoření [value_type](#value_type) objekty.|
|`IList`|[Initializer_list](../standard-library/initializer-list.md) ze kterého chcete kopírovat prvky.|

### <a name="return-value"></a>Návratová hodnota

Vrátí jeden element členské funkce (1) a (2), [pár](../standard-library/pair-structure.md) jejichž `bool` součást je hodnota true, pokud došlo vložení a hodnotu false, pokud mapy už obsažený element, jehož klíč měl ekvivalentní hodnotu v pořadí. Komponenta iterátoru dvojice návratové hodnoty odkazuje na nově vložený prvek, pokud má komponenta `bool` hodnotu true, nebo na existující prvek, pokud má komponenta `bool` hodnotu false.

Jeden element s nápovědu členské funkce, (3) a (4) vrátí iterátor, který odkazuje na umístění, kde nového elementu byl vložen do mapy nebo, pokud již existuje element s klíčem ekvivalentní, do existujícího elementu.

### <a name="remarks"></a>Poznámky

Touto funkcí nejsou zneplatněny žádné iterátory, ukazatele ani odkazy.

Během vkládání pouze jeden prvek Pokud je vyvolána výjimka, stavu kontejneru nezměnil. Pokud je při vkládání více prvků vyvolána výjimka, kontejner zůstane v neurčeném, ale platném stavu.

Pro přístup k komponenta iterator `pair` `pr` je vrácený jedné položce členské funkce, použijte `pr.first`; chcete dereference iterator v rámci vrácený pár, použijte `*pr.first`, budete elementu. Chcete-li přistupovat ke komponentě `bool`, použijte `pr.second`. Příklad naleznete v ukázce kódu dále v tomto článku.

[Value_type](#value_type) kontejner je typedef, který patří do kontejneru a pro mapu, `map<K, V>::value_type` je `pair<const K, V>`. Hodnota prvku je seřazená dvojice, ve které je první komponenta rovna hodnotě klíče a druhá komponenta je rovna datové hodnotě prvku.

Členská funkce rozsahu (5) vloží pořadí hodnot element do mapu, která odpovídá každý prvek řešené pomocí iterace v rozsahu `[First, Last)`; proto `Last` získat nevloží. Členská funkce kontejneru `end()` se vztahuje k pozici hned za posledním prvkem v kontejneru, například příkaz `m.insert(v.begin(), v.end());` se pokusí vložit všechny prvky `v` do `m`. Vkládají se pouze prvky, které v rozsahu obsahují jedinečné hodnoty. Duplicitní hodnoty jsou ignorovány. Chcete-li sledovat, které prvky jsou odmítnuty, použijte jednoprvkovou verzi funkce `insert`.

Funkce člena inicializátoru seznamu (6) používá [initializer_list](../standard-library/initializer-list.md) kopírování prvků do mapy.

Pro vkládání elementu sestavený na místě – to znamená, se provádí žádné operace kopírování nebo přesunutí – najdete v části [map::emplace](#emplace) a [map::emplace_hint](#emplace_hint).

### <a name="example"></a>Příklad

```cpp
// map_insert.cpp
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
    map<int, int> m1;
    // call insert(const value_type&) version
    m1.insert({ 1, 10 });
    // call insert(ValTy&&) version
    m1.insert(make_pair(2, 20));

    cout << "The original key and mapped values of m1 are:" << endl;
    print(m1);

    // intentionally attempt a duplicate, single element
    auto ret = m1.insert(make_pair(1, 111));
    if (!ret.second){
        auto pr = *ret.first;
        cout << "Insert failed, element with key value 1 already exists."
            << endl << "  The existing element is (" << pr.first << ", " << pr.second << ")"
            << endl;
    }
    else{
        cout << "The modified key and mapped values of m1 are:" << endl;
        print(m1);
    }
    cout << endl;

    // single element, with hint
    m1.insert(m1.end(), make_pair(3, 30));
    cout << "The modified key and mapped values of m1 are:" << endl;
    print(m1);
    cout << endl;

    // The templatized version inserting a jumbled range
    map<int, int> m2;
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
    map<int, string>  m3;
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

    map<int, int> m4;
    // Insert the elements from an initializer_list
    m4.insert({ { 4, 44 }, { 2, 22 }, { 3, 33 }, { 1, 11 }, { 5, 55 } });
    cout << "After initializer_list insertion, m4 contains:" << endl;
    print(m4);
    cout << endl;
}

```

## <a name="iterator"></a>  map::iterator

Typ, který poskytuje obousměrné iterator, který může číst nebo upravovat libovolný element v mapování.

```cpp
typedef implementation-defined iterator;
```

### <a name="remarks"></a>Poznámky

**Iterator** definované bodů mapy pro elementy, které jsou objekty [value_type](#value_type), která je typu `pair` * \< * **constKey** , **Typ *** >*, jehož první člen je klíčem k elementu a jehož sekundu člen je namapované datum uchovávat elementem.

K dereference **iterator** `Iter` odkazující na element mapy, použijte **->** operátor.

Chcete-li získat přístup k hodnotě klíče pro element, použijte `Iter`  ->  **první**, což je totéž jako (\* `Iter`). **první**. Chcete-li získat přístup k hodnotě namapované datum pro element, použijte `Iter`  ->  **druhý**, což je totéž jako (\* `Iter`). **druhý**.

### <a name="example"></a>Příklad

Podívejte se příklad [začít](#begin) příklad toho, jak deklarace a používání **iterator**.

## <a name="key_comp"></a>  map::key_comp

Načte kopii porovnání objekt použitý k pořadí klíčů v mapování.

```cpp
key_compare key_comp() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí objekt funkce mapu používá pořadí jejích elementů.

### <a name="remarks"></a>Poznámky

Definuje objekt uložené – členská funkce

**BOOL – operátor**( **constKey &**`left`, **const klíč &**`right`);

která vrací **true** Pokud `left` předchází a není rovno `right` v pořadí řazení.

### <a name="example"></a>Příklad

```cpp
// map_key_comp.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;

   map <int, int, less<int> > m1;
   map <int, int, less<int> >::key_compare kc1 = m1.key_comp( ) ;
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

   map <int, int, greater<int> > m2;
   map <int, int, greater<int> >::key_compare kc2 = m2.key_comp( );
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

## <a name="key_compare"></a>  map::key_compare

Typ, který poskytuje funkce objekt, který můžete porovnat dva klíče řazení k určení relativních pořadí dva elementy v mapě.

```cpp
typedef Traits key_compare;
```

### <a name="remarks"></a>Poznámky

`key_compare` je synonymum pro parametr šablony `Traits`.

Další informace o `Traits` najdete v článku [map – třída](../standard-library/map-class.md) tématu.

### <a name="example"></a>Příklad

Podívejte se příklad [key_comp –](#key_comp) příklad toho, jak deklarace a používání `key_compare`.

## <a name="key_type"></a>  map::key_type

Typ, který popisuje klíč řazení uložené v každé elementu mapy.

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>Poznámky

`key_type` je synonymum pro parametr šablony `Key`.

Další informace o `Key`, najdete v části poznámky [map – třída](../standard-library/map-class.md) tématu.

### <a name="example"></a>Příklad

Podívejte se příklad [value_type](#value_type) příklad toho, jak deklarace a používání `key_type`.

## <a name="lower_bound"></a>  map::lower_bound

Vrátí iterovat prvním elementem v mapu s hodnotou klíče, která je rovna nebo větší než je zadaný klíč.

```cpp
iterator lower_bound(const Key& key);

const_iterator lower_bound(const Key& key) const;
```

### <a name="parameters"></a>Parametry

`key` Hodnota klíče argument být porovnána s klíč řazení elementu z prohledávaný mapy.

### <a name="return-value"></a>Návratová hodnota

**Iterator** nebo `const_iterator` adresy umístění elementu v mapě, že klíčem, která je rovna nebo větší než argument klíč nebo který adres umístění úspěšné posledním prvkem v mapě, pokud žádné odpovídají je najít pro klíč.

Pokud vrátí hodnotu, která `lower_bound` je přiřazena k `const_iterator`, mapy objekt nelze změnit. Pokud vrátí hodnotu, která `lower_bound` je přiřazena k **iterator**, je možné upravit objekt map.

### <a name="example"></a>Příklad

```cpp
// map_lower_bound.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int> m1;
   map <int, int> :: const_iterator m1_AcIter, m1_RcIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );

   m1_RcIter = m1.lower_bound( 2 );
   cout << "The first element of map m1 with a key of 2 is: "
        << m1_RcIter -> second << "." << endl;

   // If no match is found for this key, end( ) is returned
   m1_RcIter = m1. lower_bound ( 4 );

   if ( m1_RcIter == m1.end( ) )
      cout << "The map m1 doesn't have an element "
           << "with a key of 4." << endl;
   else
      cout << "The element of map m1 with a key of 4 is: "
           << m1_RcIter -> second << "." << endl;

   // The element at a specific location in the map can be found
   // using a dereferenced iterator addressing the location
   m1_AcIter = m1.end( );
   m1_AcIter--;
   m1_RcIter = m1. lower_bound ( m1_AcIter -> first );
   cout << "The element of m1 with a key matching "
        << "that of the last element is: "
        << m1_RcIter -> second << "." << endl;
}
```

```Output
The first element of map m1 with a key of 2 is: 20.
The map m1 doesn't have an element with a key of 4.
The element of m1 with a key matching that of the last element is: 30.
```

## <a name="map"></a>  map::map

Vytvoří mapu, která je prázdný nebo se kopírování všech nebo součástí některé další mapy.

```cpp
map();

explicit map(
    const Traits& Comp);

map(
    const Traits& Comp,
    const Allocator& Al);

map(
    const map& Right);

map(
    map&& Right);

map(
    initializer_list<value_type> IList);

map(
    initializer_list<value_type> IList,
    const Traits& Comp);

map(
    initializer_list<value_type> IList,
    const Traits& Comp,
    const Allocator& Allocator);

template <class InputIterator>
map(
 InputIterator First,
    InputIterator Last);

template <class InputIterator>
map(
 InputIterator First,
    InputIterator Last,
    const Traits& Comp);

template <class InputIterator>
map(
 InputIterator First,
    InputIterator Last,
    const Traits& Comp,
    const Allocator& Al);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|-|-|
|Parametr|Popis|
|`Al`|Allocator – třída úložiště má být použit pro tento objekt mapy, kde je použit výchozí `Allocator`.|
|`Comp`|Funkci porovnání typu `const Traits` sloužící k uspořádání elementy v mapě, který se standardně `hash_compare`.|
|`Right`|Objekt map, ze kterého je kopií vytvořen objekt set.|
|`First`|Pozice první prvek v rozsahu elementy, které se mají zkopírovat.|
|`Last`|Pozice první prvek mimo rozsah elementy, které se mají zkopírovat.|
|`IList`|Initializer_list, ze kterého budou elementy zkopírovány.|

### <a name="remarks"></a>Poznámky

Všechny konstruktory ukládání typu allocator objektu, který spravuje úložiště paměti pro mapu a který se může vracet později voláním [get_allocator –](#get_allocator). Parametr allocator je často v deklaraci třídy vynechán a makra předběžného zpracování jsou použita k nahrazení alternativních alokátorů.

Všechny konstruktory inicializovat jejich mapy.

Všechny konstruktory uložit objekt funkce typu vlastnosti, která se používá k navázání pořadí mezi klíči mapy a který se může vracet později voláním [key_comp –](#key_comp).

Zadejte první tři konstruktory prázdný počáteční mapy, druhý určující typ porovnání – funkce ( `Comp`) pro použití při vytváření pořadí elementy a třetí explicitním zadáním přidělujícího modulu zadejte ( `Al`) jako použít. Klíčové slovo `explicit` potlačí některé druhy automatického převodu typu.

Čtvrtý konstruktor určuje kopii mapy `Right`.

Páté konstruktor určuje kopii mapy přesunutím `Right`.

Šestinu, sedmý a osmou konstruktory použít initializer_list, ze kterého chcete zkopírovat členy.

Zkopírujte následující tři konstruktory rozsahu `[First, Last)` mapy se zvýšeným explicitness v určení typu funkci porovnání třídy `Traits` a přidělení.

### <a name="example"></a>Příklad

```cpp
// map_map.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main()
{
    using namespace std;
    typedef pair <int, int> Int_Pair;
    map <int, int>::iterator m1_Iter, m3_Iter, m4_Iter, m5_Iter, m6_Iter, m7_Iter;
    map <int, int, less<int> >::iterator m2_Iter;

    // Create an empty map m0 of key type integer
    map <int, int> m0;

    // Create an empty map m1 with the key comparison
    // function of less than, then insert 4 elements
    map <int, int, less<int> > m1;
    m1.insert(Int_Pair(1, 10));
    m1.insert(Int_Pair(2, 20));
    m1.insert(Int_Pair(3, 30));
    m1.insert(Int_Pair(4, 40));

    // Create an empty map m2 with the key comparison
    // function of geater than, then insert 2 elements
    map <int, int, less<int> > m2;
    m2.insert(Int_Pair(1, 10));
    m2.insert(Int_Pair(2, 20));

    // Create a map m3 with the
    // allocator of map m1
    map <int, int>::allocator_type m1_Alloc;
    m1_Alloc = m1.get_allocator();
    map <int, int> m3(less<int>(), m1_Alloc);
    m3.insert(Int_Pair(3, 30));

    // Create a copy, map m4, of map m1
    map <int, int> m4(m1);

    // Create a map m5 by copying the range m1[ first,  last)
    map <int, int>::const_iterator m1_bcIter, m1_ecIter;
    m1_bcIter = m1.begin();
    m1_ecIter = m1.begin();
    m1_ecIter++;
    m1_ecIter++;
    map <int, int> m5(m1_bcIter, m1_ecIter);

    // Create a map m6 by copying the range m4[ first,  last)
    // and with the allocator of map m2
    map <int, int>::allocator_type m2_Alloc;
    m2_Alloc = m2.get_allocator();
    map <int, int> m6(m4.begin(), ++m4.begin(), less<int>(), m2_Alloc);

    cout << "m1 =";
    for (auto i : m1)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    cout << "m2 =";
    for(auto i : m2)
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

    // Create a map m7 by moving m5
    cout << "m7 =";
    map<int, int> m7(move(m5));
    for (auto i : m7)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    // Create a map m8 by copying in an initializer_list
    map<int, int> m8{ { { 1, 1 }, { 2, 2 }, { 3, 3 }, { 4, 4 } } };
    cout << "m8: = ";
    for (auto i : m8)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    // Create a map m9 with an initializer_list and a comparator
    map<int, int> m9({ { 5, 5 }, { 6, 6 }, { 7, 7 }, { 8, 8 } }, less<int>());
    cout << "m9: = ";
    for (auto i : m9)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    // Create a map m10 with an initializer_list, a comparator, and an allocator
    map<int, int> m10({ { 9, 9 }, { 10, 10 }, { 11, 11 }, { 12, 12 } }, less<int>(), m9.get_allocator());
    cout << "m10: = ";
    for (auto i : m10)
        cout << i.first << " " << i.second << ", ";
    cout << endl;
}

```

## <a name="mapped_type"></a>  map::mapped_type

Typ, který představuje data uložená v mapování.

```cpp
typedef Type mapped_type;
```

### <a name="remarks"></a>Poznámky

Typ `mapped_type` je synonymum pro zadanou třídu `Type` parametr šablony.

Další informace o `Type` najdete v článku [map – třída](../standard-library/map-class.md) tématu.

### <a name="example"></a>Příklad

Podívejte se příklad [value_type](#value_type) příklad toho, jak deklarace a používání `mapped_type`.

## <a name="max_size"></a>  map::max_size

Vrátí maximální délku objektu map.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>Návratová hodnota

Maximální délka možné mapy.

### <a name="example"></a>Příklad

```cpp
// map_max_size.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int> m1;
   map <int, int> :: size_type i;

   i = m1.max_size( );
   cout << "The maximum possible length "
        << "of the map is " << i << "."
        << endl << "(Magnitude is machine specific.)";
}
```

## <a name="op_at"></a>  map::Operator]

Vloží prvek do objektu map se zadanou hodnotou klíče.

```cpp
Type& operator[](const Key& key);

Type& operator[](Key&& key);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|-|-|
|Parametr|Popis|
|`key`|Hodnota klíče elementu, který chcete vložit.|

### <a name="return-value"></a>Návratová hodnota

Odkaz na hodnotu dat vloženého prvku.

### <a name="remarks"></a>Poznámky

Pokud není nalezena hodnota klíče argumentu, je vložen spolu s výchozí hodnotou datového typu.

`operator[]` slouží k vložení elementy do mapy `m` pomocí `m[ key] = DataValue;` kde `DataValue` je hodnota `mapped_type` elementu s hodnotou klíče `key`.

Při použití `operator[]` Pokud chcete vložit elementy, vrácený odkaz neindikuje, zda je vložení Změna existující element nebo vytvořením nové. Členské funkce [najít](#find) a [vložit](#insert) slouží k určení, zda element se zadaným klíčem již nachází před vložení.

### <a name="example"></a>Příklad

```cpp
// map_op_insert.cpp
// compile with: /EHsc
#include <map>
#include <iostream>
#include <string>

int main( )
{
   using namespace std;
   typedef pair <const int, int> cInt2Int;
   map <int, int> m1;
   map <int, int> :: iterator pIter;

   // Insert a data value of 10 with a key of 1
   // into a map using the operator[] member function
   m1[ 1 ] = 10;

   // Compare other ways to insert objects into a map
   m1.insert ( map <int, int> :: value_type ( 2, 20 ) );
   m1.insert ( cInt2Int ( 3, 30 ) );

   cout  << "The keys of the mapped elements are:";
   for ( pIter = m1.begin( ) ; pIter != m1.end( ) ; pIter++ )
      cout << " " << pIter -> first;
   cout << "." << endl;

   cout  << "The values of the mapped elements are:";
   for ( pIter = m1.begin( ) ; pIter != m1.end( ) ; pIter++ )
      cout << " " << pIter -> second;
   cout << "." << endl;

   // If the key already exists, operator[]
   // changes the value of the datum in the element
   m1[ 2 ] = 40;

   // operator[] will also insert the value of the data
   // type's default constructor if the value is unspecified
   m1[5];

   cout  << "The keys of the mapped elements are now:";
   for ( pIter = m1.begin( ) ; pIter != m1.end( ) ; pIter++ )
      cout << " " << pIter -> first;
   cout << "." << endl;

   cout  << "The values of the mapped elements are now:";
   for ( pIter = m1.begin( ) ; pIter != m1.end( ) ; pIter++ )
      cout << " " << pIter -> second;
   cout << "." << endl;

// insert by moving key
    map<string, int> c2;
    string str("abc");
    cout << "c2[move(str)] == " << c2[move(str)] << endl;
    cout << "c2["abc"] == " << c2["abc"] << endl;

    return (0);
}
```

```Output
The keys of the mapped elements are: 1 2 3.
The values of the mapped elements are: 10 20 30.
The keys of the mapped elements are now: 1 2 3 5.
The values of the mapped elements are now: 10 40 30 0.
c2[move(str)] == 0
c2["abc"] == 1
```

## <a name="op_eq"></a>  map::Operator =

Nahradí prvky objektu map kopií jiného objektu map.

```cpp
map& operator=(const map& right);

map& operator=(map&& right);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|-|-|
|Parametr|Popis|
|`right`|[Mapy](../standard-library/map-class.md) se zkopírují `map`.|

### <a name="remarks"></a>Poznámky

Po vymazání v žádné stávající elementy `map`, `operator=` buď kopíruje nebo přesouvá obsah `right` do mapy.

### <a name="example"></a>Příklad

```cpp
// map_operator_as.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
   {
   using namespace std;
   map<int, int> v1, v2, v3;
   map<int, int>::iterator iter;

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

## <a name="pointer"></a>  map::Pointer

Typ, který poskytuje ukazatel na element mapy.

```cpp
typedef typename allocator_type::pointer pointer;
```

### <a name="remarks"></a>Poznámky

Typ **ukazatel** lze upravit hodnotu elementu.

Ve většině případů [iterator](#iterator) se má použít pro přístup k elementům v objektu mapy.

## <a name="rbegin"></a>  map::rbegin

Vrátí iterator adresování prvním elementem v invertovaných mapy.

```cpp
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```

### <a name="return-value"></a>Návratová hodnota

Iterator zpětné obousměrného adresování prvním elementem v invertovaných mapu nebo řešení, co je posledním prvkem v unreversed mapy.

### <a name="remarks"></a>Poznámky

`rbegin` se používá s odstínech mapu stejně jako [začít](#begin) se používá s mapou.

Pokud vrátí hodnotu, která `rbegin` je přiřazena k `const_reverse_iterator`, pak mapy objekt nelze změnit. Pokud vrátí hodnotu, která `rbegin` je přiřazena k `reverse_iterator`, pak je možné upravit objekt map.

`rbegin` můžete použít k iteraci v rámci mapy zpětné.

### <a name="example"></a>Příklad

```cpp
// map_rbegin.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int> m1;

   map <int, int> :: iterator m1_Iter;
   map <int, int> :: reverse_iterator m1_rIter;
   map <int, int> :: const_reverse_iterator m1_crIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );

   m1_rIter = m1.rbegin( );
   cout << "The first element of the reversed map m1 is "
        << m1_rIter -> first << "." << endl;

   // begin can be used to start an iteration
   // through a map in a forward order
   cout << "The map is: ";
   for ( m1_Iter = m1.begin( ) ; m1_Iter != m1.end( ); m1_Iter++)
      cout << m1_Iter -> first << " ";
      cout << "." << endl;

   // rbegin can be used to start an iteration
   // through a map in a reverse order
   cout << "The reversed map is: ";
   for ( m1_rIter = m1.rbegin( ) ; m1_rIter != m1.rend( ); m1_rIter++)
      cout << m1_rIter -> first << " ";
      cout << "." << endl;

   // A map element can be erased by dereferencing to its key
   m1_rIter = m1.rbegin( );
   m1.erase ( m1_rIter -> first );

   m1_rIter = m1.rbegin( );
   cout << "After the erasure, the first element "
        << "in the reversed map is "
        << m1_rIter -> first << "." << endl;
}
```

```Output
The first element of the reversed map m1 is 3.
The map is: 1 2 3 .
The reversed map is: 3 2 1 .
After the erasure, the first element in the reversed map is 2.
```

## <a name="reference"></a>  map::Reference

Typ, který obsahuje odkaz na element uložené v mapě.

```cpp
typedef typename allocator_type::reference reference;
```

### <a name="example"></a>Příklad

```cpp
// map_reference.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int> m1;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );

   // Declare and initialize a const_reference &Ref1
   // to the key of the first element
   const int &Ref1 = ( m1.begin( ) -> first );

   // The following line would cause an error because the
   // non-const_reference cannot be used to access the key
   // int &Ref1 = ( m1.begin( ) -> first );

   cout << "The key of first element in the map is "
        << Ref1 << "." << endl;

   // Declare and initialize a reference &Ref2
   // to the data value of the first element
   int &Ref2 = ( m1.begin( ) -> second );

   cout << "The data value of first element in the map is "
        << Ref2 << "." << endl;

   //The non-const_reference can be used to modify the
   //data value of the first element
   Ref2 = Ref2 + 5;
   cout << "The modified data value of first element is "
        << Ref2 << "." << endl;
}
```

```Output
The key of first element in the map is 1.
The data value of first element in the map is 10.
The modified data value of first element is 15.
```

## <a name="rend"></a>  map::rend

Vrátí iterátor, který řeší umístění úspěšné posledním prvkem v invertovaných mapy.

```cpp
const_reverse_iterator rend() const;

reverse_iterator rend();
```

### <a name="return-value"></a>Návratová hodnota

Iterator zpětné obousměrného, která řeší umístění úspěšné posledním prvkem v invertovaných mapu (umístění, které měl před prvním elementem v mapě unreversed).

### <a name="remarks"></a>Poznámky

`rend` se používá s odstínech mapu stejně jako [end](#end) se používá s mapou.

Pokud vrátí hodnotu, která `rend` je přiřazena k `const_reverse_iterator`, pak mapy objekt nelze změnit. Pokud vrátí hodnotu, která `rend` je přiřazena k `reverse_iterator`, pak je možné upravit objekt map.

`rend` slouží k testování, aby se jestli zpětné iterator dosáhne konce své mapy.

Hodnoty vrácené `rend` by neměl být vyhodnoceny odkazy.

### <a name="example"></a>Příklad

```cpp
// map_rend.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int> m1;

   map <int, int> :: iterator m1_Iter;
   map <int, int> :: reverse_iterator m1_rIter;
   map <int, int> :: const_reverse_iterator m1_crIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );

   m1_rIter = m1.rend( );
   m1_rIter--;
   cout << "The last element of the reversed map m1 is "
        << m1_rIter -> first << "." << endl;

   // begin can be used to start an iteration
   // through a map in a forward order
   cout << "The map is: ";
   for ( m1_Iter = m1.begin( ) ; m1_Iter != m1.end( ); m1_Iter++)
      cout << m1_Iter -> first << " ";
      cout << "." << endl;

   // rbegin can be used to start an iteration
   // through a map in a reverse order
   cout << "The reversed map is: ";
   for ( m1_rIter = m1.rbegin( ) ; m1_rIter != m1.rend( ); m1_rIter++)
      cout << m1_rIter -> first << " ";
      cout << "." << endl;

   // A map element can be erased by dereferencing to its key
   m1_rIter = --m1.rend( );
   m1.erase ( m1_rIter -> first );

   m1_rIter = m1.rend( );
   m1_rIter--;
   cout << "After the erasure, the last element "
        << "in the reversed map is "
        << m1_rIter -> first << "." << endl;
}
```

```Output
The last element of the reversed map m1 is 1.
The map is: 1 2 3 .
The reversed map is: 3 2 1 .
After the erasure, the last element in the reversed map is 2.
```

## <a name="reverse_iterator"></a>  map::reverse_iterator

Typ, který poskytuje obousměrné iterator, které můžou číst nebo upravte element v invertovaných mapy.

```cpp
typedef std::reverse_iterator<iterator> reverse_iterator;
```

### <a name="remarks"></a>Poznámky

Typ `reverse_iterator` nelze změnit hodnotu elementu a je použít k iteraci v rámci mapy pozpátku.

`reverse_iterator` Definované bodů mapy pro elementy, které jsou objekty [value_type](#value_type), která je typu `pair` * \< * **constKey**, * *Typ *** >*, jehož první člen je klíčem k elementu a jehož sekundu člen je namapované datum uchovávat elementem.

K dereference `reverse_iterator` `rIter` odkazující na element mapy, použijte **->** operátor.

Chcete-li získat přístup k hodnotě klíče pro element, použijte `rIter`  ->  **první**, což je totéž jako (\* `rIter`). **první**. Chcete-li získat přístup k hodnotě namapované datum pro element, použijte `rIter`  ->  **druhý**, což je totéž jako (\* `rIter`). **první**.

### <a name="example"></a>Příklad

Podívejte se příklad [rbegin –](#rbegin) příklad toho, jak deklarace a používání `reverse_iterator`.

## <a name="size"></a>  map::size

Vrátí počet prvků v objektu map.

```cpp
size_type size() const;
```

### <a name="return-value"></a>Návratová hodnota

Aktuální délka mapy.

### <a name="example"></a>Příklad

Následující příklad ukazuje použití map::size – členská funkce.

```cpp
// map_size.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main()
{
    using namespace std;
    map<int, int> m1, m2;
    map<int, int>::size_type i;
    typedef pair<int, int> Int_Pair;

    m1.insert(Int_Pair(1, 1));
    i = m1.size();
    cout << "The map length is " << i << "." << endl;

    m1.insert(Int_Pair(2, 4));
    i = m1.size();
    cout << "The map length is now " << i << "." << endl;
}
```

```Output
The map length is 1.
The map length is now 2.
```

## <a name="size_type"></a>  map::size_type

Typ celé číslo bez znaménka, která představuje počet elementů v mapování.

```cpp
typedef typename allocator_type::size_type size_type;
```

### <a name="example"></a>Příklad

Podívejte se na příklad pro [velikost](#size) příklad toho, jak deklarace a používání `size_type`.

## <a name="swap"></a>  map::swap

Zamění prvky dvou objektů map.

```cpp
void swap(
    map<Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

`right` Argument mapy poskytování elementy pro si místo se cíl mapy.

### <a name="remarks"></a>Poznámky

Členská funkce by způsobila neplatnost žádné odkazy, ukazatele nebo iterátory, které určit elementů ve dvou mapy, jehož elementy jsou během výměny.

### <a name="example"></a>Příklad

```cpp
// map_swap.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int> m1, m2, m3;
   map <int, int>::iterator m1_Iter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );
   m2.insert ( Int_Pair ( 10, 100 ) );
   m2.insert ( Int_Pair ( 20, 200 ) );
   m3.insert ( Int_Pair ( 30, 300 ) );

   cout << "The original map m1 is:";
   for ( m1_Iter = m1.begin( ); m1_Iter != m1.end( ); m1_Iter++ )
      cout << " " << m1_Iter -> second;
   cout   << "." << endl;

   // This is the member function version of swap
   //m2 is said to be the argument map; m1 the target map
   m1.swap( m2 );

   cout << "After swapping with m2, map m1 is:";
   for ( m1_Iter = m1.begin( ); m1_Iter != m1.end( ); m1_Iter++ )
      cout << " " << m1_Iter -> second;
   cout  << "." << endl;

   // This is the specialized template version of swap
   swap( m1, m3 );

   cout << "After swapping with m3, map m1 is:";
   for ( m1_Iter = m1.begin( ); m1_Iter != m1.end( ); m1_Iter++ )
      cout << " " << m1_Iter -> second;
   cout   << "." << endl;
}
```

```Output
The original map m1 is: 10 20 30.
After swapping with m2, map m1 is: 100 200.
After swapping with m3, map m1 is: 300.
```

## <a name="upper_bound"></a>  map::upper_bound

Vrátí iterovat prvním elementem v mapu, aby pomocí klíče s hodnotou, která je větší než je zadaný klíč.

```cpp
iterator upper_bound(const Key& key);

const_iterator upper_bound(const Key& key) const;
```

### <a name="parameters"></a>Parametry

`key` Hodnota klíče argument který se má porovnat s hodnotou klíče řazení elementu z mapy být vyhledán.

### <a name="return-value"></a>Návratová hodnota

**Iterator** nebo `const_iterator` adresy umístění elementu v mapě, že klíčem, který je větší než klíč argument, nebo, který se týká umístění úspěšné posledním prvkem v mapě, pokud žádné odpovídají je nalezen klíče.

Pokud návratová hodnota je přiřazen k `const_iterator`, mapy objekt nelze změnit. Pokud návratová hodnota je přiřazen k **iterator**, je možné upravit objekt map.

### <a name="example"></a>Příklad

```cpp
// map_upper_bound.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int> m1;
   map <int, int> :: const_iterator m1_AcIter, m1_RcIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );

   m1_RcIter = m1.upper_bound( 2 );
   cout << "The first element of map m1 with a key "
        << "greater than 2 is: "
        << m1_RcIter -> second << "." << endl;

   // If no match is found for the key, end is returned
   m1_RcIter = m1. upper_bound ( 4 );

   if ( m1_RcIter == m1.end( ) )
      cout << "The map m1 doesn't have an element "
           << "with a key greater than 4." << endl;
   else
      cout << "The element of map m1 with a key > 4 is: "
           << m1_RcIter -> second << "." << endl;

   // The element at a specific location in the map can be found
   // using a dereferenced iterator addressing the location
   m1_AcIter = m1.begin( );
   m1_RcIter = m1. upper_bound ( m1_AcIter -> first );
   cout << "The 1st element of m1 with a key greater than\n"
        << "that of the initial element of m1 is: "
        << m1_RcIter -> second << "." << endl;
}
```

```Output
The first element of map m1 with a key greater than 2 is: 30.
The map m1 doesn't have an element with a key greater than 4.
The 1st element of m1 with a key greater than
that of the initial element of m1 is: 20.
```

## <a name="value_comp"></a>  map::value_comp

Členská funkce vrátí objekt funkce, který určuje pořadí prvků v mapování tak, že porovnáte jejich hodnoty klíče.

```cpp
value_compare value_comp() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí objekt funkce porovnání mapu používá pořadí jejích elementů.

### <a name="remarks"></a>Poznámky

Pro mapu *m*, pokud dva elementy *e*1 ( *tisíc*1, *d*1) a *e*2 ( *tisíc*2, `d`2) jsou objekty typu `value_type`, kde *tisíc*1 a *tisíc*2 jsou jejich klíče typu `key_type` a `d`1 a `d`jsou 2 jejich data typu `mapped_type`, pak *m.*`value_comp`( *e*1, *e*2) je ekvivalentní *m.* `key_comp` *(KB*1, *tisíc*2). Definuje objekt uložené – členská funkce

**BOOL – operátor**( **value_type &**`left`, **value_type &**`right`);

která vrací **true** Pokud klíčovou hodnotu `left` předchází a není roven hodnotě klíče `right` v pořadí řazení.

### <a name="example"></a>Příklad

```cpp
// map_value_comp.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;

   map <int, int, less<int> > m1;
   map <int, int, less<int> >::value_compare vc1 = m1.value_comp( );
   pair< map<int,int>::iterator, bool > pr1, pr2;

   pr1= m1.insert ( map <int, int> :: value_type ( 1, 10 ) );
   pr2= m1.insert ( map <int, int> :: value_type ( 2, 5 ) );

   if( vc1( *pr1.first, *pr2.first ) == true )
   {
      cout << "The element ( 1,10 ) precedes the element ( 2,5 )."
           << endl;
   }
   else
   {
      cout << "The element ( 1,10 ) does not precede the element ( 2,5 )."
           << endl;
   }

   if(vc1( *pr2.first, *pr1.first ) == true )
   {
      cout << "The element ( 2,5 ) precedes the element ( 1,10 )."
           << endl;
   }
   else
   {
      cout << "The element ( 2,5 ) does not precede the element ( 1,10 )."
           << endl;
   }
}
```

```Output
The element ( 1,10 ) precedes the element ( 2,5 ).
The element ( 2,5 ) does not precede the element ( 1,10 ).
```

## <a name="value_type"></a>  map::value_type

Typ objektu uložené jako element v mapování.

```cpp
typedef pair<const Key, Type> value_type;
```

### <a name="example"></a>Příklad

```cpp
// map_value_type.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   typedef pair <const int, int> cInt2Int;
   map <int, int> m1;
   map <int, int> :: key_type key1;
   map <int, int> :: mapped_type mapped1;
   map <int, int> :: value_type value1;
   map <int, int> :: iterator pIter;

   // value_type can be used to pass the correct type
   // explicitly to avoid implicit type conversion
   m1.insert ( map <int, int> :: value_type ( 1, 10 ) );

   // Compare other ways to insert objects into a map
   m1.insert ( cInt2Int ( 2, 20 ) );
   m1[ 3 ] = 30;

   // Initializing key1 and mapped1
   key1 = ( m1.begin( ) -> first );
   mapped1 = ( m1.begin( ) -> second );

   cout << "The key of first element in the map is "
        << key1 << "." << endl;

   cout << "The data value of first element in the map is "
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

## <a name="see-also"></a>Viz také

[\<Mapa > členy](http://msdn.microsoft.com/en-us/7e8f0bc2-6034-40f6-9d14-76d4cef86308)<br/>
[Kontejnery](../cpp/containers-modern-cpp.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)<br/>
