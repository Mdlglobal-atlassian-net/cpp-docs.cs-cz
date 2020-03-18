---
title: map – třída
ms.date: 10/18/2018
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
ms.openlocfilehash: d25d8837c549b425416632ee07e23bb57fbd17ae
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79419985"
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

\ *klíčů*
Datový typ klíče, který se uloží v objektu map.

*Zadejte*\
Typ dat prvku, který bude uložen v objektu map.

\ *vlastností*
Typ poskytující objekt funkce, který může porovnat dvě hodnoty prvků pro určení jejich relativního pořadí v objektu map. Tento argument je nepovinný a binární predikát `less<Key>` výchozí hodnotu.

V jazyce C++ 14 můžete povolit heterogenní vyhledávání zadáním predikátu std:: less < >, který nemá žádné parametry typu. Další informace najdete v tématu [heterogenní vyhledávání v asociativních kontejnerech](../standard-library/stl-containers.md#sequence_containers) .

\ *přidělování*
Typ představující uložený objekt alokátoru, který zapouzdřuje informace o přidělování a navrácení paměti zpět objektu map. Tento argument je nepovinný a výchozí hodnota je `allocator<pair<const Key, Type> >`.

## <a name="remarks"></a>Poznámky

Třída C++ mapy standardní knihovny je:

- Kontejner s proměnnou velikostí, který efektivně načte hodnoty prvku na základě přidružených hodnot klíče.

- Oboustranný, protože poskytuje obousměrné iterátory pro přístup k jeho prvkům.

- Seřazená, protože její prvky jsou seřazeny podle hodnot klíče podle zadané funkce porovnání.

- Tabulka. vzhledem k tomu, že každý z jeho prvků musí mít jedinečný klíč.

- Kontejner asociativních párů, protože jeho prvky hodnoty dat se liší od hodnot klíčů.

- Šablona třídy, protože funkce, které poskytuje, jsou obecné a nezávislé na elementu nebo typu klíče. Datové typy použité pro prvky a klíče jsou zadány jako parametry v šabloně třídy společně s funkcí porovnání a alokátorem.

Iterátor poskytnutý třídou map je obousměrný iterátor, ale členské funkce třídy [INSERT](#insert) a [map](#map) mají verze, které přebírají jako parametry šablony slabší vstupní iterátor, jehož požadavky na funkce jsou menší než ty, které jsou zaručené třídou Obousměrných iterátorů. Různé koncepty iterátorů se týkají upřesnění jejich funkčnosti. Každý koncept iterátoru má vlastní sadu požadavků a algoritmy, které s ním pracují musí být omezeny těmito požadavky. Ke vstupnímu iterátoru lze přistoupit přes ukazatel pro odkazování na některý objekt a může být zvýšena na další iterátor v sekvenci.

Doporučujeme založit volbu typu kontejneru podle druhu vyhledávání a vkládání, který je požadován aplikací. Asociativní kontejnery jsou optimalizovány pro operace vyhledávání, vkládání a odstranění. Členské funkce, které explicitně podporují tyto operace jsou provedeny v nejhorším čase, který je úměrný logaritmu počtu prvků v kontejneru. Vkládání prvků nezruší platnost žádných iterátorů a odstranění prvků zruší platnost pouze těch iterátorů, které výslovně odkazovaly na odstraněné prvky.

Doporučujeme objekt map vytvořit jako asociativní kontejner volby, pokud jsou v aplikaci splněny podmínky, které přiřazují hodnoty klíčům. Model tohoto typu struktury je uspořádaný seznam jednoznačně se vyskytujících klíčových slov, které mají přidružené hodnoty řetězce poskytující definice. Má-li slovo více než jednu správnou definici, takže tento klíč není jedinečný, potom by třída multimap měla být zvoleným kontejnerem. Pokud je uložen jen seznam slov, pak by třída set měla být vhodným kontejnerem. Pokud je povoleno více výskytů slova, měla by být použita třída multiset.

Mapa řadí prvky, které ovládací prvek ovládá, voláním uloženého objektu funkce typu [key_compare](#key_compare). Tento uložený objekt je funkce porovnání, ke které je přistup volán voláním metody [key_comp](#key_comp) . Obecně jsou dva dané prvky porovnány pro určení, zda je jeden menší než druhý nebo zda jsou stejné. Při porovnání všech prvků je vytvořena seřazená sekvence neekvivalentních prvků.

> [!NOTE]
> Funkce porovnání je binární predikát, který indukuje přísné slabé seřazení ve standardním matematickém smyslu. Binární predikát f (x, y) je objekt funkce, který má dva objekty argumentu x a y a návratovou hodnotu **true** nebo **false**. Řazení určené pro sadu je přísné slabé řazení, pokud je binární predikát Nereflexivní, antisymetrický a tranzitivní a je-li ekvivalence tranzitivní, kde jsou dva objekty x a y definovány jako ekvivalentní, je-li hodnota f (x, y) i f (y, x) **false**. Pokud silnější podmínka rovnosti mezi klíči nahradí ekvivalenci, stane se pořadí celkovým (v tom smyslu, že všechny prvky jsou uspořádány ve vztahu k sobě navzájem) a odpovídající klíče budou od sebe nerozeznatelné.
>
> V jazyce C++ 14 můžete povolit heterogenní vyhledávání zadáním predikátu `std::less<>` nebo `std::greater<>`, který nemá žádné parametry typu. Další informace najdete v tématu [heterogenní vyhledávání v asociativních kontejnerech](../standard-library/stl-containers.md#sequence_containers) .

## <a name="members"></a>Členové

### <a name="constructors"></a>Konstruktory

|||
|-|-|
|[mapy](#map)|Sestaví seznam konkrétní velikosti nebo s prvky konkrétní hodnoty nebo pomocí konkrétního `allocator` nebo jako kopii nějaké jiné mapy.|

### <a name="typedefs"></a>Typedefs

|||
|-|-|
|[allocator_type](#allocator_type)|Typedef pro třídu `allocator` pro objekt map.|
|[const_iterator](#const_iterator)|Definice typu obousměrného iterátoru, který může číst prvek **const** v mapě.|
|[const_pointer](#const_pointer)|Typedef pro ukazatel na prvek **const** v mapě.|
|[const_reference](#const_reference)|Definice typu odkazu na prvek **const** uložený v mapě pro čtení a provádění operací **const** .|
|[const_reverse_iterator](#const_reverse_iterator)|Typ, který poskytuje obousměrný iterátor, který může číst libovolný element **const** v mapě.|
|[difference_type](#difference_type)|Definice typu celého čísla se znaménkem pro počet prvků objektu map v rozsahu mezi prvky, na které odkazují iterátory.|
|[iterátor](#iterator)|Definice typu obousměrného iterátoru, který může číst nebo upravovat libovolný prvek v objektu map.|
|[key_compare](#key_compare)|Definice typu poskytující objekt funkce, který může porovnat dva klíče řazení pro určení relativního pořadí dvou prvků v objektu map.|
|[key_type](#key_type)|Definice typu klíče řazení uloženého v jednotlivých prvcích objektu map.|
|[mapped_type](#mapped_type)|Definice typu dat uložených v jednotlivých prvcích objektu map.|
|[ukazatele](#pointer)|Typedef pro ukazatel na prvek **const** v mapě.|
|[odkaz](#reference)|Definice typu odkazu na prvek uložený v objektu map.|
|[reverse_iterator](#reverse_iterator)|Definice typu obousměrného iterátoru, který může číst nebo upravovat prvek v obráceném objektu map.|
|[size_type](#size_type)|Celočíselná definice typu bez znaménka pro počet prvků v objektu map.|
|[value_type](#value_type)|Definice typu pro typ objektu, který je uložen jako prvek v objektu map.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[Počínaje](#at)|Vyhledá prvek se zadanou hodnotou klíče.|
|[ifunctiondiscovery](#begin)|Vrátí iterátor odkazující na první prvek v objektu map.|
|[cbegin](#cbegin)|Vrátí konstantní iterátor odkazující na první prvek v objektu map.|
|[cend](#cend)|Vrátí konstantní iterátor za koncem.|
|[jejich](#clear)|Odstraní všechny prvky objektu map.|
|[count](#count)|Vrátí počet prvků objektu map, jejichž klíč odpovídá klíči zadaného parametrem.|
|[crbegin –](#crbegin)|Vrátí konstantní iterátor, který odkazuje na první prvek v obráceném objektu map.|
|[crend](#crend)|Vrátí konstantní iterátor, který odkazuje na umístění za posledním prvkem v převráceném objektu map.|
|[emplace](#emplace)|Vloží vytvořený prvek na místo do objektu map.|
|[emplace_hint](#emplace_hint)|Vloží vytvořený prvek s náznakem umístění na místo do objektu map.|
|[obsahovat](#empty)|Vrátí **hodnotu true** , pokud je mapa prázdná.|
|[účelu](#end)|Vrátí iterátor za koncem.|
|[equal_range](#equal_range)|Vrátí pár iterátorů. První iterátor ve dvojici odkazuje na první prvek v `map` s klíčem, který je větší než zadaný klíč. Druhý iterátor v páru odkazuje na první prvek v `map` s klíčem, který je roven nebo větší než klíč.|
|[ověřování](#erase)|Odebere prvek nebo rozsah prvků v objektu map od zadané pozice.|
|[find](#find)|Vrátí iterátor odkazující na umístění prvku v objektu map, který má klíč stejný jako zadaný klíč.|
|[get_allocator](#get_allocator)|Vrátí kopii objektu `allocator`, který se používá k vytvoření mapy.|
|[zadat](#insert)|Vloží prvek nebo rozsah prvků na určenou pozici do objektu map.|
|[key_comp](#key_comp)|Vrátí kopii objektu porovnání, která je použit pro seřazení klíčů v objektu map.|
|[lower_bound](#lower_bound)|Vrátí iterátor na první prvek objektu map s hodnotou klíče, který je roven nebo větší než zadaný klíč.|
|[max_size](#max_size)|Vrátí maximální délku objektu map.|
|[rbegin](#rbegin)|Vrátí iterátor odkazující na první prvek v obráceném objektu map.|
|[rend](#rend)|Vrátí iterátor, který odkazuje na umístění za posledním prvkem v převráceném objektu map.|
|[hodnota](#size)|Vrátí počet prvků v objektu map.|
|[adresu](#swap)|Zamění prvky dvou objektů map.|
|[upper_bound](#upper_bound)|Vrátí iterátor na první prvek objektu map s hodnotou klíče, který je větší než zadaný klíč.|
|[value_comp](#value_comp)|Získá kopii objektu porovnání použitého pro seřazení hodnot prvků objektu map.|

### <a name="operators"></a>Operátory

|||
|-|-|
|[podnikatel&#91;&#93;](#op_at)|Vloží prvek do objektu map se zadanou hodnotou klíče.|
|[operátor =](#op_eq)|Nahradí prvky objektu map kopií jiného objektu map.|

## <a name="allocator_type"></a>allocator_type

Typ, který představuje třídu přidělování pro objekt map.

```cpp
typedef Allocator allocator_type;
```

### <a name="example"></a>Příklad

Příklad, který používá `allocator_type`, naleznete v tématu příklad pro [get_allocator](#get_allocator) .

## <a name="at"></a>Počínaje

Vyhledá prvek se zadanou hodnotou klíče.

```cpp
Type& at(const Key& key);

const Type& at(const Key& key) const;
```

### <a name="parameters"></a>Parametry

klíč * \
Hodnota klíče, která se má najít

### <a name="return-value"></a>Návratová hodnota

Odkaz na hodnotu dat nalezeného prvku.

### <a name="remarks"></a>Poznámky

Pokud hodnota klíče argumentu nebyla nalezena, funkce vyvolá objekt třídy [Out_of_range třídy](../standard-library/out-of-range-class.md).

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

## <a name="begin"></a>ifunctiondiscovery

Vrátí iterátor adresující první prvek v mapě.

```cpp
const_iterator begin() const;

iterator begin();
```

### <a name="return-value"></a>Návratová hodnota

Obousměrný iterátor, který adresuje první prvek v mapě nebo umístění, které je pro prázdné mapování úspěšné.

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

## <a name="cbegin"></a>cbegin

Vrátí **konstantní** iterátor, který adresuje umístění hned za poslední prvek v rozsahu.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>Návratová hodnota

**Konstantní** obousměrný iterátor, který adresuje první prvek v rozsahu nebo umístění hned za konec prázdného rozsahu (pro prázdný rozsah `cbegin() == cend()`).

### <a name="remarks"></a>Poznámky

S návratovou hodnotou `cbegin`nelze upravovat elementy v rozsahu.

Tuto členskou funkci lze použít místo `begin()` členské funkce pro zajištění, že návratová hodnota je `const_iterator`. Obvykle se používá ve spojení s klíčovým slovem srážky typu [auto](../cpp/auto-cpp.md) , jak je znázorněno v následujícím příkladu. V příkladu zvažte `Container` jako upravitelný kontejner ( **nekonstantní**) libovolného druhu, který podporuje `begin()` a `cbegin()`.

```cpp
auto i1 = Container.begin();
// i1 is Container<T>::iterator
auto i2 = Container.cbegin();

// i2 is Container<T>::const_iterator
```

## <a name="cend"></a>cend

Vrátí **konstantní** iterátor, který adresuje umístění hned za poslední prvek v rozsahu.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>Návratová hodnota

Iterátor s obousměrným přístupem **const** , který odkazuje hned za konec rozsahu.

### <a name="remarks"></a>Poznámky

`cend` slouží k otestování, zda iterátor prošl na konci rozsahu.

Tuto členskou funkci lze použít místo `end()` členské funkce pro zajištění, že návratová hodnota je `const_iterator`. Obvykle se používá ve spojení s klíčovým slovem srážky typu [auto](../cpp/auto-cpp.md) , jak je znázorněno v následujícím příkladu. V příkladu zvažte `Container` jako upravitelný kontejner ( **nekonstantní**) libovolného druhu, který podporuje `end()` a `cend()`.

```cpp
auto i1 = Container.end();
// i1 is Container<T>::iterator
auto i2 = Container.cend();

// i2 is Container<T>::const_iterator
```

Hodnota vrácená `cend` by neměla být zpětně odkazovaná.

## <a name="clear"></a>jejich

Odstraní všechny prvky objektu map.

```cpp
void clear();
```

### <a name="example"></a>Příklad

Následující příklad ukazuje použití funkce map:: Clear členské funkce.

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

## <a name="const_iterator"></a>const_iterator

Typ, který poskytuje obousměrný iterátor, který může číst prvek **const** v mapě.

```cpp
typedef implementation-defined const_iterator;
```

### <a name="remarks"></a>Poznámky

Typ `const_iterator` nelze použít pro úpravu hodnoty prvku.

`const_iterator` definován pomocí map body k prvkům, které jsou objekty [value_type](#value_type), který je typu `pair`\< **constKey**, **typ**>, jehož prvním členem je klíč k elementu a jehož druhý člen je mapované datum uchovávané prvkem.

Chcete-li přesměrovat `const_iterator` `cIter` ukazovat na prvek v mapě, použijte operátor `->`.

Chcete-li získat přístup k hodnotě klíče pro element, použijte **nejprve**`cIter` -> , který je ekvivalentní (\* `cIter`). **nejprve**.

Pro přístup k hodnotě mapovaného pole pro prvek použijte `cIter` -> **Second**, který je ekvivalentní (\* `cIter`). **sekunda**.

### <a name="example"></a>Příklad

Viz příklad pro [začátek](#begin) příkladu, který používá `const_iterator`.

## <a name="const_pointer"></a>const_pointer

Typ, který poskytuje ukazatel na prvek **const** v mapě.

```cpp
typedef typename allocator_type::const_pointer const_pointer;
```

### <a name="remarks"></a>Poznámky

Typ `const_pointer` nelze použít pro úpravu hodnoty prvku.

Ve většině případů by měl být použit [iterátor](#iterator) pro přístup k prvkům v objektu map.

## <a name="const_reference"></a>const_reference

Typ, který poskytuje odkaz na prvek **const** uložený v mapě pro čtení a provádění operací **const** .

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

## <a name="const_reverse_iterator"></a>const_reverse_iterator

Typ, který poskytuje obousměrný iterátor, který může číst libovolný element **const** v mapě.

```cpp
typedef std::reverse_iterator<const_iterator> const_reverse_iterator;
```

### <a name="remarks"></a>Poznámky

Typ `const_reverse_iterator` nemůže změnit hodnotu prvku a použít k iteraci přes mapu v opačném případě.

`const_reverse_iterator` definován pomocí map body k prvkům, které jsou objekty [value_type](#value_type), který je typu `pair<const Key, Type>`, jehož prvním členem je klíč k elementu a druhý člen je mapovaným datumem drženým prvkem.

Chcete-li přesměrovat `const_reverse_iterator crIter` odkazující na prvek v mapě, použijte operátor `->`.

Chcete-li získat přístup k hodnotě klíče pro element, použijte **nejprve**`crIter` -> , který je ekvivalentní (\* `crIter`). **nejprve**.

Pro přístup k hodnotě mapovaného pole pro prvek použijte `crIter` -> **Second**, který je ekvivalentní (\* `crIter`). **nejprve**.

### <a name="example"></a>Příklad

Příklad, jak deklarovat a používat `const_reverse_iterator`, naleznete v příkladu pro [rend](#rend) .

## <a name="count"></a>výpočtu

Vrátí počet prvků v mapě, jejichž klíč odpovídá klíči určenému parametrem.

```cpp
size_type count(const Key& key) const;
```

### <a name="parameters"></a>Parametry

\ *klíčů*
Hodnota klíče prvků, které mají být porovnány s mapou.

### <a name="return-value"></a>Návratová hodnota

1, pokud mapa obsahuje element, jehož klíč řazení odpovídá klíči parametru; 0, pokud mapa neobsahuje element se shodným klíčem.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí počet prvků *x* v rozsahu.

\[ lower_bound (*klíč*), Upper_bound (*klíč*))

což je 0 nebo 1 v případě mapy, což je jedinečný asociativní kontejner.

### <a name="example"></a>Příklad

Následující příklad ukazuje použití členské funkce map:: Count.

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

## <a name="crbegin"></a>crbegin –

Vrátí konstantní iterátor adresující první prvek v obráceném mapě.

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>Návratová hodnota

Konstantní reverzní obousměrný iterátor, který adresuje první prvek v obrácené [mapě](../standard-library/map-class.md) nebo řeší, co byl posledním prvkem v neobráceném `map`.

### <a name="remarks"></a>Poznámky

`crbegin` se používá s obráceným `map` stejně jako [Begin](#begin) se používá s `map`.

S návratovou hodnotou `crbegin`nelze změnit objekt `map`

`crbegin` lze použít k iteraci `map` zpět.

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

## <a name="crend"></a>crend

Vrátí konstantní iterátor, který adresuje umístění následující po posledním prvku v obráceném mapování.

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>Návratová hodnota

Konstantní reverzní obousměrný iterátor, který adresuje umístění následující po posledním prvku v obrácené [mapě](../standard-library/map-class.md) (umístění, které předchází první prvek v neobráceném `map`).

### <a name="remarks"></a>Poznámky

`crend` se používá s obrácenou mapou jako [End](#end) se používá s `map`.

S návratovou hodnotou `crend`nelze změnit objekt `map`.

`crend` lze použít k otestování, zda reverzní iterátor dosáhl konce jeho `map`.

Hodnota vrácená `crend` by neměla být zpětně odkazovaná.

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

## <a name="difference_type"></a>difference_type

Typ se znaménkem typu Integer, který lze použít k reprezentaci počtu prvků mapy v rozsahu mezi prvky, na které odkazují iterátory.

```cpp
typedef allocator_type::difference_type difference_type;
```

### <a name="remarks"></a>Poznámky

`difference_type` je typ vrácený při odečítání nebo přírůstcích pomocí iterátorů kontejneru. `difference_type` se obvykle používá k reprezentaci počtu prvků v rozsahu *[First, Last)* mezi iterátory `first` a `last`, zahrnuje element, na který odkazuje `first`, a rozsah prvků až do, ale ne včetně prvku, na který odkazuje `last`.

Všimněte si, že i když je `difference_type` k dispozici pro všechny iterátory, které splňují požadavky vstupního iterátoru, které zahrnují třídu Obousměrných iterátorů podporovaných vratnými kontejnery, jako je například set, odečítání mezi iterátory je podporováno pouze iterátory náhodného přístupu, které jsou poskytovány náhodným kontejnerem přístupu, jako je například Vector.

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

## <a name="emplace"></a>emplace

Vloží prvek sestavený na místě (nejsou provedeny žádné operace kopírování nebo přesunutí) do mapy.

```cpp
template <class... Args>
pair<iterator, bool>
emplace(
    Args&&... args);
```

### <a name="parameters"></a>Parametry

\ *argumentů*
Argumenty předané k vytvoření prvku, který má být vložen do mapy, pokud již neobsahuje prvek, jehož hodnota je ekvivalentní objednaná.

### <a name="return-value"></a>Návratová hodnota

[Dvojice](../standard-library/pair-structure.md) , jejíž **logická** komponenta má hodnotu true, pokud bylo provedeno vložení, a hodnotu false, pokud mapa již obsahovala prvek ekvivalentní hodnoty v řazení. Komponenta iterátoru dvojice vrácených hodnot odkazuje na nově vložený element, pokud je **logická** komponenta true nebo na existující prvek, pokud je komponenta **bool** false.

Chcete-li získat přístup k součásti iterátoru `pair` `pr`, použijte `pr.first`; Pokud ho chcete odkázat, použijte `*pr.first`. Pro přístup ke komponentě **bool** použijte `pr.second`. Příklad naleznete v ukázce kódu dále v tomto článku.

### <a name="remarks"></a>Poznámky

Tato funkce neověřuje žádné iterátory ani odkazy.

V případě, že je vyvolána výjimka, stav kontejneru není změněn.

[Value_type](#value_type) prvku je dvojice, takže hodnota elementu bude seřazená dvojice s první komponentou rovnající se hodnotě klíče a druhá komponenta se rovná hodnotě dat elementu.

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

## <a name="emplace_hint"></a>emplace_hint

Vloží prvek sestavený na místě (nejsou provedeny žádné operace kopírování nebo přesunutí) s pomocným parametrem umístění.

```cpp
template <class... Args>
iterator emplace_hint(
    const_iterator where,
    Args&&... args);
```

### <a name="parameters"></a>Parametry

\ *argumentů*
Argumenty předané k vytvoření prvku, který má být vložen do mapy, pokud již mapa tento prvek neobsahuje, nebo obecněji, pokud již neobsahuje prvek, jehož klíč je ekvivalentní objednání.

*kde*\
Místo zahájení vyhledání správného bodu vložení. (Pokud tento bod bezprostředně předchází *místu, k*vložení může dojít v konstantním času v čase namísto logaritmické doby.)

### <a name="return-value"></a>Návratová hodnota

Iterátor nově vloženého prvku.

Pokud se vložení nezdařilo, protože prvek již existuje, vrátí iterátor existujícímu prvku s jeho klíčem.

### <a name="remarks"></a>Poznámky

Tato funkce neověřuje žádné iterátory ani odkazy.

V případě, že je vyvolána výjimka, stav kontejneru není změněn.

[Value_type](#value_type) prvku je dvojice, takže hodnota elementu bude seřazená dvojice s první komponentou rovnající se hodnotě klíče a druhá komponenta se rovná hodnotě dat elementu.

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

## <a name="empty"></a>obsahovat

Testuje, zda je mapa prázdná.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Návratová hodnota

**true** , pokud je mapa prázdná; **false** , pokud je mapa neprázdná.

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

## <a name="end"></a>účelu

Vrátí iterátor za koncem.

```cpp
const_iterator end() const;

iterator end();
```

### <a name="return-value"></a>Návratová hodnota

Iterace po konci. Pokud je mapa prázdná, pak `map::end() == map::begin()`.

### <a name="remarks"></a>Poznámky

`end` slouží k otestování, zda iterátor prošl koncem jeho mapy.

Hodnota vrácená `end` by neměla být zpětně odkazovaná.

Příklad kódu naleznete v tématu [map:: Find](#find).

## <a name="equal_range"></a>equal_range

Vrátí dvojici iterátorů, které reprezentují [lower_bound](#lower_bound) klíče a [Upper_bound](#upper_bound) klíče.

```cpp
pair <const_iterator, const_iterator> equal_range (const Key& key) const;

pair <iterator, iterator> equal_range (const Key& key);
```

### <a name="parameters"></a>Parametry

\ *klíčů*
Hodnota klíče argumentu, která má být porovnána s klíčem řazení prvku z prohledávané mapy.

### <a name="return-value"></a>Návratová hodnota

Chcete-li získat přístup k prvnímu iterátoru páru `pr` vráceném členskou funkcí, použijte `pr`. **nejprve**a pro zpětnou vazbu dolního iterátoru použijte \*(`pr`. **první**). Pro přístup k druhému iterátoru páru `pr` vráceném členskou funkcí použijte `pr`. za **druhé**a pro zpětnou vazbu k hornímu iterátoru použijte \*(`pr`. **sekundy**).

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
        << "matching the 2nd element of the pair"
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

## <a name="erase"></a>ověřování

Odebere prvek nebo rozsah prvků v mapě ze zadané pozice nebo odstraní prvky, které odpovídají zadanému klíči.

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

\ *klíčů*
Hodnota klíče prvků, které mají být odebrány.

### <a name="return-value"></a>Návratová hodnota

Pro první dvě členské funkce obousměrný iterátor, který určuje první prvek zbývající za odebranými prvky, nebo element, který je konci mapy, pokud žádný takový prvek neexistuje.

Třetí členská funkce vrátí počet prvků, které byly odebrány z mapy.

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

    // Fill in some data to test with, one at a time, using an initializer list
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

## <a name="find"></a>najít

Vrátí iterátor, který odkazuje na umístění elementu v mapě, který má klíč odpovídající zadanému klíči.

```cpp
iterator find(const Key& key);

const_iterator find(const Key& key) const;
```

### <a name="parameters"></a>Parametry

\ *klíčů*
Hodnota klíče, která má být porovnána klíčem řazení prvku z prohledávané mapy.

### <a name="return-value"></a>Návratová hodnota

Iterátor, který odkazuje na umístění elementu se zadaným klíčem, nebo umístění, které následuje po posledním prvku v mapě (`map::end()`), pokud se pro klíč nenajde žádná shoda.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí iterátor, který odkazuje na prvek v mapě, jejíž klíč řazení je ekvivalentní klíči argumentu v binárním predikátu, který vystaví řazení na základě vztahu k srovnatelnosti.

Pokud je vrácená hodnota `find` přiřazena k `const_iterator`, objekt mapy nelze změnit. Pokud je vrácená hodnota `find` přiřazena k `iterator`, objekt mapy lze upravit

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

## <a name="get_allocator"></a>get_allocator

Vrátí kopii objektu přidělování, která se používá k vytvoření mapy.

```cpp
allocator_type get_allocator() const;
```

### <a name="return-value"></a>Návratová hodnota

Alokátor použitý mapou.

### <a name="remarks"></a>Poznámky

Přidělování pro třídu map určují, jak Třída spravuje úložiště. Výchozí přidělující třídy kontejnerů C++ standardní knihovny jsou dostačující pro většinu programovacích potřeb. Psaní a používání vlastního třídy přidělování je pokročilým C++ tématem.

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

## <a name="insert"></a>zadat

Vloží prvek nebo rozsah prvků do mapy.

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

\ *Val*
Hodnota prvku, který má být vložen do mapy, pokud již neobsahuje prvek, jehož klíč je ekvivalentní objednané.

*Kde*\
Místo zahájení vyhledání správného bodu vložení. (Pokud tento bod bezprostředně předchází *místu, k*vložení může dojít v konstantním času v čase namísto logaritmické doby.)

*ValTy*\
Parametr šablony, který určuje typ argumentu, který může mapa použít k vytvoření prvku [value_type](#value_type)a Perfect-Forwards *Val* jako argument.

*První*\
Pozice prvního prvku, který chcete zkopírovat.

*Poslední*\
Pozice bezprostředně za posledním prvkem, který chcete zkopírovat.

*InputIterator*\
Argument funkce šablony, který splňuje požadavky [vstupního iterátoru](../standard-library/input-iterator-tag-struct.md) , který odkazuje na prvky typu, které lze použít k vytvoření [value_type](#value_type) objektů.

\ *IList*
[Initializer_list](../standard-library/initializer-list.md) , ze kterých se mají kopírovat prvky

### <a name="return-value"></a>Návratová hodnota

Členské funkce s jedním prvkem, (1) a (2), vrátí [dvojici](../standard-library/pair-structure.md) , jejíž **logická** komponenta má hodnotu true, pokud bylo provedeno vložení, a hodnotu false, pokud mapa již obsahovala element, jehož klíč měl ekvivalentní hodnotu v řazení. Komponenta iterátoru dvojice vrácených hodnot odkazuje na nově vložený element, pokud je **logická** komponenta true nebo na existující prvek, pokud je komponenta **bool** false.

Členské funkce s jedním prvkem, (3) a (4), vrátí iterátor, který odkazuje na pozici, kam byl nový prvek vložen do mapy, nebo pokud element s ekvivalentním klíčem již existuje, pro existující prvek.

### <a name="remarks"></a>Poznámky

Touto funkcí nejsou zneplatněny žádné iterátory, ukazatele ani odkazy.

Při vložení pouze jednoho prvku, pokud je vyvolána výjimka, není změněn stav kontejneru. Pokud je při vkládání více prvků vyvolána výjimka, kontejner zůstane v neurčeném, ale platném stavu.

Chcete-li získat přístup k součásti iterátoru `pair` `pr`, který je vrácen členskými funkcemi s jedním prvkem, použijte `pr.first`; Chcete-li překázat na iterátor v rámci vráceného páru, použijte `*pr.first`, což vám poskytne element. Pro přístup ke komponentě **bool** použijte `pr.second`. Příklad naleznete v ukázce kódu dále v tomto článku.

[Value_type](#value_type) kontejneru je definice typu, která patří do kontejneru a pro mapu `map<K, V>::value_type` je `pair<const K, V>`. Hodnota prvku je seřazená dvojice, ve které je první komponenta rovna hodnotě klíče a druhá komponenta je rovna datové hodnotě prvku.

Členská funkce range (5) vloží sekvenci hodnot prvků do mapy, která odpovídá každému prvku, který je adresován iterátorem v rozsahu `[First, Last)`; Proto se `Last` nevloží. Členská funkce kontejneru `end()` se vztahuje k pozici hned za posledním prvkem v kontejneru, například příkaz `m.insert(v.begin(), v.end());` se pokusí vložit všechny prvky `v` do `m`. Vkládají se pouze prvky, které v rozsahu obsahují jedinečné hodnoty. Duplicitní hodnoty jsou ignorovány. Chcete-li sledovat, které prvky jsou odmítnuty, použijte jednoprvkovou verzi funkce `insert`.

Členská funkce seznamu inicializátorů (6) používá [initializer_list](../standard-library/initializer-list.md) ke zkopírování prvků do mapy.

Pro vložení elementu vytvořeného na místě – to znamená, že nejsou provedeny žádné operace kopírování nebo přesunutí – viz [map:: emplace](#emplace) a [map:: emplace_hint](#emplace_hint).

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

## <a name="iterator"></a>iterátor

Typ, který poskytuje obousměrný iterátor, který může číst nebo upravovat libovolný prvek v mapě.

```cpp
typedef implementation-defined iterator;
```

### <a name="remarks"></a>Poznámky

Iterátor definovaný v mapě odkazuje na elementy, které jsou objekty [value_type](#value_type), který je typu `pair<const Key, Type>`, jehož prvním členem je klíč k elementu a jehož druhým členem je mapované datum uchovávané prvkem.

Chcete-li odkázat iterátor *ITER* ukazující na prvek v mapě, použijte operátor `->`.

Chcete-li získat přístup k hodnotě klíče pro element, použijte `Iter->first`, který je ekvivalentní `(*Iter).first`. Pro přístup k hodnotě mapovaného pole Datum elementu použijte `Iter->second`, který je ekvivalentní `(*Iter).second`.

### <a name="example"></a>Příklad

Viz příklad pro [začátek](#begin) pro příklad, jak deklarovat a používat `iterator`.

## <a name="key_comp"></a>key_comp

Načte kopii objektu porovnání, která se používá k řazení klíčů v mapě.

```cpp
key_compare key_comp() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí objekt funkce, který mapa používá pro seřazení jeho prvků.

### <a name="remarks"></a>Poznámky

Uložený objekt definuje členskou funkci.

`bool operator(const Key& left, const Key& right);`

Vrátí **hodnotu true** , pokud `left` předchází a není rovna `right` v pořadí řazení.

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

## <a name="key_compare"></a>key_compare

Typ, který poskytuje objekt funkce, který může porovnat dva klíče řazení pro určení relativního pořadí dvou prvků v mapě.

```cpp
typedef Traits key_compare;
```

### <a name="remarks"></a>Poznámky

`key_compare` je synonymum pro *vlastnosti*parametrů šablony.

Další informace o *vlastnostích* naleznete v tématu [Třída mapy](../standard-library/map-class.md) .

### <a name="example"></a>Příklad

Příklad, jak deklarovat a používat `key_compare`, naleznete v tématu příklad pro [key_comp](#key_comp) .

## <a name="key_type"></a>key_type

Typ, který popisuje klíč řazení uložený v každém elementu mapy.

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>Poznámky

`key_type` je synonymum pro *klíč*parametru šablony.

Další informace o *klíči*naleznete v části poznámky v tématu [Třída mapy](../standard-library/map-class.md) .

### <a name="example"></a>Příklad

Příklad, jak deklarovat a používat `key_type`, naleznete v tématu příklad pro [value_type](#value_type) .

## <a name="lower_bound"></a>lower_bound

Vrátí iterátor na první prvek v objektu map s hodnotou klíče, která je větší nebo rovna hodnotě zadaného klíče.

```cpp
iterator lower_bound(const Key& key);

const_iterator lower_bound(const Key& key) const;
```

### <a name="parameters"></a>Parametry

\ *klíčů*
Hodnota klíče argumentu, která má být porovnána s klíčem řazení prvku z prohledávané mapy.

### <a name="return-value"></a>Návratová hodnota

`iterator` nebo `const_iterator`, které řeší umístění elementu v mapě, který má klíč, který je roven nebo větší než klíč argumentu nebo který řeší umístění, které následuje po posledním prvku na mapě, pokud není nalezena shoda pro klíč.

Pokud je vrácená hodnota `lower_bound` přiřazena k `const_iterator`, objekt mapy nelze změnit. Pokud je vrácená hodnota `lower_bound` přiřazena k `iterator`, lze objekt map upravit.

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

## <a name="map"></a>mapy

Vytvoří mapu, která je prázdná nebo je kopií celé nebo části nějaké jiné mapy.

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

*Al*\
Třída přidělování úložiště, která se má použít pro tento objekt mapy, ve kterém se výchozí hodnota `Allocator`.

\ *comp*
Funkce porovnání typu `const Traits` slouží k uspořádání prvků na mapě, která má výchozí hodnotu `hash_compare`.

*Pravé*\
Objekt map, ze kterého je kopií vytvořen objekt set.

*První*\
Pozice prvního prvku v rozsahu prvků, které mají být zkopírovány.

*Poslední*\
Pozice prvního prvku mimo rozsah prvků, které mají být zkopírovány.

\ *IList*
Initializer_list, ze kterých se mají kopírovat prvky

### <a name="remarks"></a>Poznámky

Všechny konstruktory ukládají typ objektu přidělování, který spravuje úložiště paměti pro mapu a které lze později vrátit voláním [get_allocator](#get_allocator). Parametr allocator je často v deklaraci třídy vynechán a makra předběžného zpracování jsou použita k nahrazení alternativních alokátorů.

Všechny konstruktory inicializují svou mapu.

Všechny konstruktory ukládají objekt funkce typu, který se používá k navázání objednávky mezi klíči mapy a které mohou být později vráceny voláním [key_comp](#key_comp).

První tři konstruktory určují prázdnou počáteční mapu, druhá určuje typ funkce porovnání (*comp*), která se použije při vytváření pořadí prvků, a třetí explicitní určení typu přidělujícího objektu (*Al*), který se má použít. Klíčové slovo **výslovně** potlačí určité druhy automatických převodů typu.

Čtvrtý konstruktor určuje kopii *přímo*v mapě.

Pátý konstruktor určuje kopii mapy přesunutím *doprava*.

Šesté, sedmé a osmá konstruktory používají initializer_list, ze kterých se zkopírují členové.

Následující tři konstruktory kopírují rozsah `[First, Last)` mapy a zvyšují tak explicitní určení typu funkce porovnání třídy `Traits` a přidělování.

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
    // function of greater than, then insert 2 elements
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

## <a name="mapped_type"></a>mapped_type

Typ, který představuje data uložená v mapě.

```cpp
typedef Type mapped_type;
```

### <a name="remarks"></a>Poznámky

Typ `mapped_type` je synonymum pro parametr šablony *typu* třídy.

Další informace o *typu* naleznete v tématu [Třída mapy](../standard-library/map-class.md) .

### <a name="example"></a>Příklad

Příklad, jak deklarovat a používat `mapped_type`, naleznete v tématu příklad pro [value_type](#value_type) .

## <a name="max_size"></a>max_size

Vrátí maximální délku objektu map.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>Návratová hodnota

Maximální možná délka mapy.

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

## <a name="op_at"></a>operator [] – operátor

Vloží prvek do objektu map se zadanou hodnotou klíče.

```cpp
Type& operator[](const Key& key);

Type& operator[](Key&& key);
```

### <a name="parameters"></a>Parametry

\ *klíčů*
Hodnota klíče prvku, který má být vložen.

### <a name="return-value"></a>Návratová hodnota

Odkaz na hodnotu dat vloženého prvku.

### <a name="remarks"></a>Poznámky

Pokud není nalezena hodnota klíče argumentu, je vložen spolu s výchozí hodnotou datového typu.

`operator[]` lze použít k vložení prvků do mapy `m` pomocí `m[key] = DataValue;`, kde `DataValue` je hodnota `mapped_type` elementu s klíčovou hodnotou *klíče*.

Při použití `operator[]` pro vložení prvků, vrácený odkaz neurčuje, zda vložení mění již existující prvek nebo vytváří nový. Členské funkce [find](#find) a [INSERT](#insert) lze použít k určení, zda je prvek se zadaným klíčem již přítomen před vložením.

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

## <a name="op_eq"></a>operátor =

Nahradí prvky objektu map kopií jiného objektu map.

```cpp
map& operator=(const map& right);
map& operator=(map&& right);
```

### <a name="parameters"></a>Parametry

*pravé*\
[Mapa](../standard-library/map-class.md) , která se kopíruje do `map`.

### <a name="remarks"></a>Poznámky

Po vymazání všech existujících prvků v `map``operator=` buď zkopírování nebo přesunutí obsahu *přímo* do mapy.

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

## <a name="pointer"></a>ukazatele

Typ, který poskytuje ukazatel na prvek v mapě.

```cpp
typedef typename allocator_type::pointer pointer;
```

### <a name="remarks"></a>Poznámky

Typ `pointer` lze použít pro úpravu hodnoty prvku.

Ve většině případů by měl být použit [iterátor](#iterator) pro přístup k prvkům v objektu map.

## <a name="rbegin"></a>rbegin

Vrátí iterátor adresující první prvek v obráceném objektu map.

```cpp
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```

### <a name="return-value"></a>Návratová hodnota

Reverzní obousměrný iterátor, který adresuje první prvek v obrácené mapě nebo řeší, co byl posledním prvkem v neobráceném mapě.

### <a name="remarks"></a>Poznámky

`rbegin` se používá s obrácenou mapou jako [začínající](#begin) , která se používá s mapou.

Pokud je vrácená hodnota `rbegin` přiřazena k `const_reverse_iterator`, objekt mapy nelze změnit. Pokud je vrácená hodnota `rbegin` přiřazena k `reverse_iterator`, lze objekt map upravit.

`rbegin` lze použít k iteraci v mapě zpět.

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

## <a name="reference"></a>odkaz

Typ, který poskytuje odkaz na prvek uložený v mapě.

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

## <a name="rend"></a>rend

Vrátí iterátor, který adresuje umístění následující po posledním prvku v obráceném objektu map.

```cpp
const_reverse_iterator rend() const;

reverse_iterator rend();
```

### <a name="return-value"></a>Návratová hodnota

Zpětný obousměrný iterátor, který adresuje umístění následující po posledním prvku v obráceném mapování (umístění, které předchází první prvek v neobráceném mapování).

### <a name="remarks"></a>Poznámky

`rend` se používá s obrácenou mapou jako [End](#end) se používá s mapou.

Pokud je vrácená hodnota `rend` přiřazena k `const_reverse_iterator`, objekt mapy nelze změnit. Pokud je vrácená hodnota `rend` přiřazena k `reverse_iterator`, lze objekt map upravit.

`rend` lze použít k otestování, zda zpětný iterátor dosáhl konce jeho mapy.

Hodnota vrácená `rend` by neměla být zpětně odkazovaná.

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

## <a name="reverse_iterator"></a>reverse_iterator

Typ, který poskytuje obousměrný iterátor, který může číst nebo upravovat prvek v obráceném mapě.

```cpp
typedef std::reverse_iterator<iterator> reverse_iterator;
```

### <a name="remarks"></a>Poznámky

Typ `reverse_iterator` nemůže změnit hodnotu prvku a použít k iteraci přes mapu v opačném případě.

`reverse_iterator` definován pomocí map body k prvkům, které jsou objekty [value_type](#value_type), který je typu `pair<const Key, Type>`, jehož prvním členem je klíč k elementu a druhý člen je mapovaným datumem drženým prvkem.

Chcete-li odkázat na `reverse_iterator` *rIter* ukazující na prvek v mapě, použijte operátor `->`.

Chcete-li získat přístup k hodnotě klíče pro element, použijte **nejprve**`rIter` -> , který je ekvivalentní (\* `rIter`). **nejprve**. Pro přístup k hodnotě mapovaného pole pro prvek použijte `rIter` -> **Second**, který je ekvivalentní (\* `rIter`). **nejprve**.

### <a name="example"></a>Příklad

Příklad, jak deklarovat a používat `reverse_iterator`, naleznete v tématu příklad pro [rbegin](#rbegin) .

## <a name="size"></a>hodnota

Vrátí počet prvků v objektu map.

```cpp
size_type size() const;
```

### <a name="return-value"></a>Návratová hodnota

Aktuální délka mapy

### <a name="example"></a>Příklad

Následující příklad ukazuje použití členské funkce map:: size.

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

## <a name="size_type"></a>size_type

Typ unsigned integer, který může představovat počet prvků v mapě.

```cpp
typedef typename allocator_type::size_type size_type;
```

### <a name="example"></a>Příklad

Podívejte se na příklad pro [Velikost](#size) pro příklad, jak deklarovat a použít `size_type`.

## <a name="swap"></a>adresu

Zamění prvky dvou objektů map.

```cpp
void swap(
    map<Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*pravé*\
Mapa argumentů poskytující prvky, které mají být nahrazeny cílovou mapou.

### <a name="remarks"></a>Poznámky

Členská funkce neověřuje žádné odkazy, ukazatele nebo iterátory, které určují elementy ve dvou mapách, jejichž prvky se vyměňují.

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

## <a name="upper_bound"></a>upper_bound

Vrátí iterátor na první prvek v mapě, který má klíč s hodnotou, která je větší než zadaný klíč.

```cpp
iterator upper_bound(const Key& key);

const_iterator upper_bound(const Key& key) const;
```

### <a name="parameters"></a>Parametry

\ *klíčů*
Hodnota klíče argumentu, která má být porovnána s hodnotou klíče řazení prvku z prohledávané mapy.

### <a name="return-value"></a>Návratová hodnota

`iterator` nebo `const_iterator`, které řeší umístění elementu v mapě s klíčem, který je větší než klíč argumentu, nebo který řeší umístění, které následuje po posledním prvku na mapě, pokud není nalezena shoda pro klíč.

Pokud je vrácená hodnota přiřazena k `const_iterator`, objekt mapy nelze změnit. Pokud je vrácená hodnota přiřazena k `iterator`, objekt mapy lze změnit.

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

## <a name="value_comp"></a>value_comp

Členská funkce vrátí objekt funkce, který určuje pořadí prvků v mapě porovnáním jejich hodnot klíče.

```cpp
value_compare value_comp() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí objekt funkce porovnání, který mapa používá pro seřazení jeho prvků.

### <a name="remarks"></a>Poznámky

Pro mapu *m*, pokud jsou dva prvky *E1*(*K1*, *D1*) a *E2*(*K2*, *D2*) objekty typu `value_type`, kde *K1* a *K1* jsou jejich klíče typu `key_type` a *D1* a *D2* jsou jejich data typu `mapped_type`, `m.value_comp(e1, e2)` je ekvivalentem `m.key_comp(k1, k2)`. Uložený objekt definuje členskou funkci.

`bool operator( value_type& left, value_type& right);`

Vrátí hodnotu **true** , pokud hodnota klíče `left` předchází a není rovna hodnotě klíče `right` v pořadí řazení.

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

## <a name="value_type"></a>value_type

Typ objektu uložený jako prvek v mapě.

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

[Containers](../cpp/containers-modern-cpp.md)\
[Bezpečnost vlákna ve C++ standardní knihovně](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)
