---
title: set – třída
ms.date: 11/04/2016
f1_keywords:
- set/std::set
- set/std::set::allocator_type
- set/std::set::const_iterator
- set/std::set::const_pointer
- set/std::set::const_reference
- set/std::set::const_reverse_iterator
- set/std::set::difference_type
- set/std::set::iterator
- set/std::set::key_compare
- set/std::set::key_type
- set/std::set::pointer
- set/std::set::reference
- set/std::set::reverse_iterator
- set/std::set::size_type
- set/std::set::value_compare
- set/std::set::value_type
- set/std::set::begin
- set/std::set::cbegin
- set/std::set::cend
- set/std::set::clear
- set/std::set::count
- set/std::set::crbegin
- set/std::set::crend
- set/std::set::emplace
- set/std::set::emplace_hint
- set/std::set::empty
- set/std::set::end
- set/std::set::equal_range
- set/std::set::erase
- set/std::set::find
- set/std::set::get_allocator
- set/std::set::insert
- set/std::set::key_comp
- set/std::set::lower_bound
- set/std::set::max_size
- set/std::set::rbegin
- set/std::set::rend
- set/std::set::size
- set/std::set::swap
- set/std::set::upper_bound
- set/std::set::value_comp
helpviewer_keywords:
- std::set [C++]
- std::set [C++], allocator_type
- std::set [C++], const_iterator
- std::set [C++], const_pointer
- std::set [C++], const_reference
- std::set [C++], const_reverse_iterator
- std::set [C++], difference_type
- std::set [C++], iterator
- std::set [C++], key_compare
- std::set [C++], key_type
- std::set [C++], pointer
- std::set [C++], reference
- std::set [C++], reverse_iterator
- std::set [C++], size_type
- std::set [C++], value_compare
- std::set [C++], value_type
- std::set [C++], begin
- std::set [C++], cbegin
- std::set [C++], cend
- std::set [C++], clear
- std::set [C++], count
- std::set [C++], crbegin
- std::set [C++], crend
- std::set [C++], emplace
- std::set [C++], emplace_hint
- std::set [C++], empty
- std::set [C++], end
- std::set [C++], equal_range
- std::set [C++], erase
- std::set [C++], find
- std::set [C++], get_allocator
- std::set [C++], insert
- std::set [C++], key_comp
- std::set [C++], lower_bound
- std::set [C++], max_size
- std::set [C++], rbegin
- std::set [C++], rend
- std::set [C++], size
- std::set [C++], swap
- std::set [C++], upper_bound
- std::set [C++], value_comp
ms.assetid: 8991f9aa-5509-4440-adc1-371512d32018
ms.openlocfilehash: f1718b1cd362e54f63388b46025804ccc0396851
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79419565"
---
# <a name="set-class"></a>set – třída

Sada C++ třídy kontejnerů standardní knihovny se používá pro ukládání a načítání dat z kolekce, ve které jsou hodnoty prvků, které jsou obsaženy, jedinečné a slouží jako klíčové hodnoty, podle kterých jsou data automaticky řazena. Hodnotu prvku v sadě nelze změnit přímo. Místo toho musíte odstranit staré hodnoty a vložit prvky s novými hodnotami.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Key,
    class Traits=less<Key>,
    class Allocator=allocator<Key>>
class set
```

### <a name="parameters"></a>Parametry

\ *klíčů*
Typ dat prvku, který bude uložen do sady.

\ *vlastností*
Typ poskytující objekt funkce, který může porovnat dvě hodnoty prvků pro určení jejich relativního pořadí v sadě. Tento argument je nepovinný a binární predikát je **míň** *\<Key >* je výchozí hodnota.

V jazyce C++ 14 můžete povolit heterogenní vyhledávání zadáním predikátu `std::less<>` nebo `std::greater<>`, který nemá žádné parametry typu. Další informace najdete v tématu [heterogenní vyhledávání v asociativních kontejnerech](../standard-library/stl-containers.md#sequence_containers) .

\ *přidělování*
Typ představující uložený objekt alokátoru, který zapouzdřuje informace o přidělování a navrácení paměti zpět sady. Tento argument je nepovinný a výchozí hodnota je `allocator<Key>`.

## <a name="remarks"></a>Poznámky

Sada C++ standardních knihoven je:

- Asociativní kontejner, což je kontejner proměnné velikosti, který podporuje efektivní načtení hodnoty prvku založené na přiřazené hodnotě klíče. Dále je to jednoduchý asociativní kontejner, protože jeho hodnoty prvku jsou jeho hodnoty klíče.

- Oboustranný, protože poskytuje obousměrný iterátor pro přístup k jeho prvkům.

- Seřazený, protože jeho prvky jsou řazeny podle hodnot klíče v kontejneru podle zadané porovnávací funkce.

- Jedinečný v tom smyslu, že každý z jeho prvků musí mít jedinečný klíč. Vzhledem k tomu, že je sada také jednoduchý asociativní kontejner, jeho prvky jsou také jedinečné.

Sada je také popsána jako šablona třídy, protože funkce, které poskytuje, jsou obecné a nezávislé na konkrétním typu dat obsažených jako prvky. Datový typ, který má být použit, je místo toho zadán jako parametr v šabloně třídy společně s funkcí porovnání a alokátorem.

Volba typu kontejneru by měla obecně vycházet z typu vyhledávání a vkládání vyžadovaného aplikací. Asociativní kontejnery jsou optimalizovány pro operace vyhledávání, vkládání a odstranění. Členské funkce, které explicitně podporují tyto operace, jsou efektivní a jsou prováděny v čase, který je průměrně úměrný logaritmu počtu prvků v kontejneru. Vkládání prvků nezruší platnost žádných iterátorů a odstranění prvků zruší platnost pouze těch iterátorů, které výslovně odkazovaly na odstraněné prvky.

Objekt sady (set) by měl být asociativní kontejner dle výběru, kdy jsou podmínky přiřazení hodnot k jejich klíčům splněny aplikací. Prvky sady jsou jedinečné a slouží jako vlastní klíče řazení. Model pro tento typ struktury je uspořádaný seznam slov, v němž se slova mohou vyskytovat pouze jednou. Pokud bylo povoleno více výskytů jednoho slova, je objekt multiset odpovídající strukturou kontejneru. Pokud hodnoty musí být připojeny k seznamu jedinečných klíčových slov, objekt map by byl vhodnou strukturou, který by měla tato data obsahovat. Pokud však klíče nejsou jedinečné, byl by zvoleným kontejnerem multimap.

Sada seřadí sekvenci, kterou ovládá, voláním uloženého objektu funkce typu [key_compare](#key_compare). Tento uložený objekt je funkce porovnání, která může být k dispozici, voláním členské funkce [key_comp](#key_comp). Obecně, tyto prvky musí být menší než srovnatelné pro toto pořadí, což znamená, že když jsou uvedeny dva prvky, může být stanoveno, zda jsou ekvivalentní (v tom smyslu, že ani jeden není menší než ten druhý), nebo že jeden je menší než druhý. To má za výsledek řazení mezi neekvivalentními prvky. Technicky je funkce porovnání binárním predikátem, který indukuje přísné slabé řazení, standardním matematickým způsobem. Binární predikát *f*( *x, y*) je objekt funkce, který má dva objekty argumentu *x* a *y* a návratovou hodnotu **true** nebo **false**. Řazení uložené na objektu set je přísné slabé řazení, pokud je binární predikát Nereflexivní, antisymetrický a tranzitivní a je-li ekvivalence tranzitivní, kde jsou dva objekty *x* a *y* definovány jako ekvivalentní, pokud jsou hodnoty v *f*( *x, y*) i *f*( *y, x*) nepravdivé. Pokud silnější podmínka rovnosti mezi klíči nahradí ekvivalenci, stane se pořadí celkovým (v tom smyslu, že všechny prvky jsou uspořádány ve vztahu k sobě navzájem) a odpovídající klíče budou od sebe nerozeznatelné.

V jazyce C++ 14 můžete povolit heterogenní vyhledávání zadáním predikátu `std::less<>` nebo `std::greater<>`, který nemá žádné parametry typu. Další informace najdete v tématu [heterogenní vyhledávání v asociativních kontejnerech](../standard-library/stl-containers.md#sequence_containers) .

Iterátor poskytnutý třídou set je obousměrný iterátor, ale funkce členských funkcí [INSERT](#insert) a [set](#set) mají verze, které přebírají jako parametry šablony slabší vstupní iterátor, jehož požadavky na funkce jsou více minimální než ty, které jsou zaručeny třídou Obousměrných iterátorů. Různé koncepty iterátorů tvoří rodinu týkající se upřesnění jejich funkčnosti. Každý koncept iterátoru má vlastní sadu požadavků a algoritmy, které s nimi pracují, musí omezit jejich předpoklady na požadavky podle typu iterátoru. Lze předpokládat, že ke vstupnímu iterátoru lze přistoupit přes ukazatel pro odkazování na některý objekt a že může být zvýšen na další iterátor v pořadí. Toto je minimální sada funkcí, ale je dostatečná pro to, aby bylo možné mluvit smysluplně o rozsahu iterátorů [`First`, `Last`) v kontextu členských funkcí třídy.

### <a name="constructors"></a>Konstruktory

|||
|-|-|
|[set](#set)|Zkonstruuje objekt set, který je prázdný nebo který je kopií celého nebo části některého jiného objektu set.|

### <a name="typedefs"></a>Typedefs

|||
|-|-|
|[allocator_type](#allocator_type)|Typ, který představuje třídu `allocator` pro objekt set.|
|[const_iterator](#const_iterator)|Typ, který poskytuje obousměrný iterátor, který může číst prvek **const** v sadě.|
|[const_pointer](#const_pointer)|Typ, který poskytuje ukazatel na prvek **const** v sadě.|
|[const_reference](#const_reference)|Typ, který poskytuje odkaz na prvek **const** uložený v sadě pro čtení a provádění operací **const** .|
|[const_reverse_iterator](#const_reverse_iterator)|Typ, který poskytuje obousměrný iterátor, který může číst libovolný element **const** v sadě.|
|[difference_type](#difference_type)|Celočíselný typ se znaménkem, který slouží k vyjádření počtu prvků objektu set v rozsahu mezi prvky, na které odkazují iterátory.|
|[iterátor](#iterator)|Typ, který poskytuje obousměrný iterátor, který může číst nebo upravovat libovolný prvek v objektu set.|
|[key_compare](#key_compare)|Typ, který poskytuje objekt funkce, který může porovnat dva klíče řazení pro určení relativního pořadí dvou prvků v objektu set.|
|[key_type](#key_type)|Typ popisuje objekt uložený jako prvek sady (objekt set) v jeho kapacitě jako klíč řazení.|
|[ukazatele](#pointer)|Typ, který poskytuje ukazatel na prvek v objektu set.|
|[odkaz](#reference)|Typ, který poskytuje odkaz na prvek uložený v objektu set.|
|[reverse_iterator](#reverse_iterator)|Typ, který poskytuje obousměrný iterátor, který může číst nebo upravovat prvek v obráceném objektu set.|
|[size_type](#size_type)|Celočíselný typ bez znaménka představující počet prvků v objektu set.|
|[value_compare](#value_compare)|Typ poskytující objekt funkce, který může porovnat dva prvků pro určení jejich relativního pořadí v sadě.|
|[value_type](#value_type)|Typ popisuje objekt uložený jako prvek sady (objekt set) v jeho kapacitě jako hodnotu.|

### <a name="functions"></a>Funkce

|||
|-|-|
|[ifunctiondiscovery](#begin)|Vrátí iterátor adresující první prvek v sadě.|
|[cbegin](#cbegin)|Vrátí iterátor const adresující první prvek v sadě.|
|[cend](#cend)|Vrátí konstantní iterátor adresující umístění následující po posledním prvku v objektu set.|
|[jejich](#clear)|Odstraní všechny prvky objektu set.|
|[count](#count)|Vrátí počet prvků objektu set, jejichž klíč odpovídá klíči se zadaným parametrem.|
|[crbegin –](#rbegin)|Vrátí konstantní iterátor adresující první prvek v obráceném objektu set.|
|[crend](#rend)|Vrátí konstantní iterátor adresující umístění následující po posledním prvku v obráceném objektu set.|
|[emplace](#emplace)|Vloží vytvořený prvek na místo do objektu set.|
|[emplace_hint](#emplace_hint)|Vloží vytvořený prvek s náznakem umístění na místo do objektu set.|
|[obsahovat](#empty)|Testuje, zda je objekt set prázdný.|
|[účelu](#end)|Vrátí iterátor adresující umístění následující po posledním prvku v objektu set.|
|[equal_range](#equal_range)|Vrátí pár iterátorů, respektive, na první prvek objektu set s klíčem, který je větší než zadaný klíč a na první prvek objektu set s klíčem, který je roven nebo větší než tento klíč.|
|[ověřování](#erase)|Odebere prvek nebo rozsah prvků v objektu set od zadané pozice nebo odebere prvky, které odpovídají zadanému klíči.|
|[find](#find)|Vrátí iterátor adresující umístění prvku v objektu set, který má klíč odpovídající zadanému klíči.|
|[get_allocator](#get_allocator)|Vrátí kopii objektu `allocator`, který se používá k vytvoření sady.|
|[zadat](#insert)|Vloží prvek nebo rozsah prvků do objektu set.|
|[key_comp](#key_comp)|Načte kopii objektu porovnání, která je použita pro seřazení klíčů v objektu set.|
|[lower_bound](#lower_bound)|Vrátí iterátor na první prvek objektu set s klíčem, který je roven nebo větší než zadaný klíč.|
|[max_size](#max_size)|Vrátí maximální délku objektu set.|
|[rbegin](#rbegin)|Vrátí iterátor adresující první prvek v obráceném objektu set.|
|[rend](#rend)|Vrátí iterátor adresující umístění následující po posledním prvku v obráceném objektu set.|
|[hodnota](#size)|Vrátí počet prvků v objektu set.|
|[adresu](#swap)|Vymění prvky dvou sad.|
|[upper_bound](#upper_bound)|Vrátí iterátor na první prvek objektu set s klíčem, který je větší než zadaný klíč.|
|[value_comp](#value_comp)|Získá kopii objektu porovnání použitého pro seřazení hodnot prvků objektu set.|

### <a name="operators"></a>Operátory

|||
|-|-|
|[operátor =](#op_eq)|Nahradí prvky objektu set kopií jiného objektu set.|

## <a name="allocator_type"></a>allocator_type

Typ, který představuje třídu přidělování pro objekt set.

```cpp
typedef Allocator allocator_type;
```

### <a name="remarks"></a>Poznámky

`allocator_type` je synonymum pro [přidělování](../standard-library/set-class.md)parametrů šablony.

Vrátí objekt funkce, který multiset používá k uspořádání prvků, což je parametr šablony `Allocator`.

Další informace o `Allocator`naleznete v části poznámky v tématu [sada třídy](../standard-library/set-class.md) .

### <a name="example"></a>Příklad

Příklad, který používá `allocator_type`, najdete v příkladu pro [get_allocator](#get_allocator) .

## <a name="begin"></a>ifunctiondiscovery

Vrátí iterátor adresující první prvek v sadě.

```cpp
const_iterator begin() const;

iterator begin();
```

### <a name="return-value"></a>Návratová hodnota

Obousměrný iterátor, který adresuje první prvek v sadě nebo umístění, které je pro prázdnou sadu úspěšné.

### <a name="remarks"></a>Poznámky

Pokud je vrácená hodnota `begin` přiřazena k `const_iterator`, prvky v objektu set nelze upravovat. Pokud je vrácená hodnota `begin` přiřazena k `iterator`, prvky v objektu set lze upravit.

### <a name="example"></a>Příklad

```cpp
// set_begin.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1;
   set <int>::iterator s1_Iter;
   set <int>::const_iterator s1_cIter;

   s1.insert( 1 );
   s1.insert( 2 );
   s1.insert( 3 );

   s1_Iter = s1.begin( );
   cout << "The first element of s1 is " << *s1_Iter << endl;

   s1_Iter = s1.begin( );
   s1.erase( s1_Iter );

   // The following 2 lines would err because the iterator is const
   // s1_cIter = s1.begin( );
   // s1.erase( s1_cIter );

   s1_cIter = s1.begin( );
   cout << "The first element of s1 is now " << *s1_cIter << endl;
}
```

```Output
The first element of s1 is 1
The first element of s1 is now 2
```

## <a name="cbegin"></a>cbegin

Vrátí **konstantní** iterátor, který adresuje první prvek v rozsahu.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>Návratová hodnota

Iterátor s obousměrným přístupem **const** , který odkazuje na první prvek rozsahu nebo umístění hned za konec prázdného rozsahu (pro prázdný rozsah `cbegin() == cend()`).

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

Odstraní všechny prvky objektu set.

```cpp
void clear();
```

### <a name="example"></a>Příklad

```cpp
// set_clear.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1;

   s1.insert( 1 );
   s1.insert( 2 );

   cout << "The size of the set is initially " << s1.size( )
        << "." << endl;

   s1.clear( );
   cout << "The size of the set after clearing is "
        << s1.size( ) << "." << endl;
}
```

```Output
The size of the set is initially 2.
The size of the set after clearing is 0.
```

## <a name="const_iterator"></a>const_iterator

Typ, který poskytuje obousměrný iterátor, který může číst prvek **const** v sadě.

```cpp
typedef implementation-defined const_iterator;
```

### <a name="remarks"></a>Poznámky

Typ `const_iterator` nelze použít pro úpravu hodnoty prvku.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [začátek](#begin) příkladu, který používá `const_iterator`.

## <a name="const_pointer"></a>const_pointer

Typ, který poskytuje ukazatel na prvek **const** v sadě.

```cpp
typedef typename allocator_type::const_pointer const_pointer;
```

### <a name="remarks"></a>Poznámky

Typ `const_pointer` nelze použít pro úpravu hodnoty prvku.

Ve většině případů by [const_iterator](#const_iterator) měla použít pro přístup k prvkům v objektu sady const.

## <a name="const_reference"></a>const_reference

Typ, který poskytuje odkaz na prvek **const** uložený v sadě pro čtení a provádění operací **const** .

```cpp
typedef typename allocator_type::const_reference const_reference;
```

### <a name="example"></a>Příklad

```cpp
// set_const_ref.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1;

   s1.insert( 10 );
   s1.insert( 20 );

   // Declare and initialize a const_reference &Ref1
   // to the 1st element
   const int &Ref1 = *s1.begin( );

   cout << "The first element in the set is "
        << Ref1 << "." << endl;

   // The following line would cause an error because the
   // const_reference cannot be used to modify the set
   // Ref1 = Ref1 + 5;
}
```

```Output
The first element in the set is 10.
```

## <a name="const_reverse_iterator"></a>const_reverse_iterator

Typ, který poskytuje obousměrný iterátor, který může číst libovolný element **const** v sadě.

```cpp
typedef std::reverse_iterator<const_iterator> const_reverse_iterator;
```

### <a name="remarks"></a>Poznámky

Typ `const_reverse_iterator` nemůže změnit hodnotu prvku a používá se k iterování skrze sadu obráceně.

### <a name="example"></a>Příklad

Příklad, jak deklarovat a použít `const_reverse_iterator`, naleznete v příkladu pro [rend](#rend) .

## <a name="count"></a>výpočtu

Vrátí počet prvků objektu set, jejichž klíč odpovídá klíči se zadaným parametrem.

```cpp
size_type count(const Key& key) const;
```

### <a name="parameters"></a>Parametry

\ *klíčů*
Klíč prvků, které mají být porovnány se sadou.

### <a name="return-value"></a>Návratová hodnota

1, pokud sada obsahuje element, jehož klíč řazení odpovídá klíči parametru. 0, pokud sada neobsahuje element se shodným klíčem.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí počet prvků v následujícím rozsahu:

\[ lower_bound (*klíč*), Upper_bound (*klíč*)).

### <a name="example"></a>Příklad

Následující příklad ukazuje použití členské funkce Set:: Count.

```cpp
// set_count.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main()
{
    using namespace std;
    set<int> s1;
    set<int>::size_type i;

    s1.insert(1);
    s1.insert(1);

    // Keys must be unique in set, so duplicates are ignored
    i = s1.count(1);
    cout << "The number of elements in s1 with a sort key of 1 is: "
         << i << "." << endl;

    i = s1.count(2);
    cout << "The number of elements in s1 with a sort key of 2 is: "
         << i << "." << endl;
}
```

```Output
The number of elements in s1 with a sort key of 1 is: 1.
The number of elements in s1 with a sort key of 2 is: 0.
```

## <a name="crbegin"></a>crbegin –

Vrátí konstantní iterátor adresující první prvek v obráceném objektu set.

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>Návratová hodnota

Konstantní reverzní obousměrný iterátor, který adresuje první prvek v obráceném množině nebo řeší, co byl posledním prvkem v neobrácené sadě.

### <a name="remarks"></a>Poznámky

`crbegin` se používá s obrácenou sadou, která je použita stejně jako [Begin](#begin) , se používá se sadou.

S návratovou hodnotou `crbegin`nelze změnit objekt set.

### <a name="example"></a>Příklad

```cpp
// set_crbegin.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1;
   set <int>::const_reverse_iterator s1_crIter;

   s1.insert( 10 );
   s1.insert( 20 );
   s1.insert( 30 );

   s1_crIter = s1.crbegin( );
   cout << "The first element in the reversed set is "
        << *s1_crIter << "." << endl;
}
```

```Output
The first element in the reversed set is 30.
```

## <a name="crend"></a>crend

Vrátí konstantní iterátor adresující umístění následující po posledním prvku v obráceném objektu set.

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>Návratová hodnota

Const reverzní obousměrný iterátor, který adresuje umístění následující po posledním prvku v obráceném seznamu (umístění, které předchází prvnímu prvku v neobrácené sadě).

### <a name="remarks"></a>Poznámky

`crend` se používá s obrácenou sadou, která je použita stejně jako [End](#end) , se používá se sadou.

S návratovou hodnotou `crend`nelze změnit objekt set. Hodnota vrácená `crend` by neměla být zpětně odkazovaná.

`crend` lze použít k otestování, zda zpětný iterátor dosáhl konce jeho sady.

### <a name="example"></a>Příklad

```cpp
// set_crend.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main() {
   using namespace std;
   set <int> s1;
   set <int>::const_reverse_iterator s1_crIter;

   s1.insert( 10 );
   s1.insert( 20 );
   s1.insert( 30 );

   s1_crIter = s1.crend( );
   s1_crIter--;
   cout << "The last element in the reversed set is "
        << *s1_crIter << "." << endl;
}
```

## <a name="difference_type"></a>difference_type

Celočíselný typ se znaménkem, který slouží k vyjádření počtu prvků objektu set v rozsahu mezi prvky, na které odkazují iterátory.

```cpp
typedef typename allocator_type::difference_type difference_type;
```

### <a name="remarks"></a>Poznámky

`difference_type` je typ vrácený při odečítání nebo přírůstcích pomocí iterátorů kontejneru. `difference_type` se obvykle používá k reprezentaci počtu prvků v rozsahu *[First, Last)* mezi iterátory `first` a `last`, zahrnuje element, na který odkazuje `first`, a rozsah prvků až do, ale ne včetně prvku, na který odkazuje `last`.

Všimněte si, že i když je `difference_type` k dispozici pro všechny iterátory, které splňují požadavky vstupního iterátoru, který zahrnuje třídu Obousměrných iterátorů podporovaných vratnými kontejnery, jako je například set, odečítání mezi iterátory je podporováno pouze iterátory s náhodným přístupem, které jsou poskytovány kontejnerem s náhodným přístupem, jako je například Vector.

### <a name="example"></a>Příklad

```cpp
// set_diff_type.cpp
// compile with: /EHsc
#include <iostream>
#include <set>
#include <algorithm>

int main( )
{
   using namespace std;

   set <int> s1;
   set <int>::iterator s1_Iter, s1_bIter, s1_eIter;

   s1.insert( 20 );
   s1.insert( 10 );
   s1.insert( 20 );   // won't insert as set elements are unique

   s1_bIter = s1.begin( );
   s1_eIter = s1.end( );

   set <int>::difference_type   df_typ5, df_typ10, df_typ20;

   df_typ5 = count( s1_bIter, s1_eIter, 5 );
   df_typ10 = count( s1_bIter, s1_eIter, 10 );
   df_typ20 = count( s1_bIter, s1_eIter, 20 );

   // the keys, and hence the elements of a set are unique,
   // so there is at most one of a given value
   cout << "The number '5' occurs " << df_typ5
        << " times in set s1.\n";
   cout << "The number '10' occurs " << df_typ10
        << " times in set s1.\n";
   cout << "The number '20' occurs " << df_typ20
        << " times in set s1.\n";

   // count the number of elements in a set
   set <int>::difference_type  df_count = 0;
   s1_Iter = s1.begin( );
   while ( s1_Iter != s1_eIter)
   {
      df_count++;
      s1_Iter++;
   }

   cout << "The number of elements in the set s1 is: "
        << df_count << "." << endl;
}
```

```Output
The number '5' occurs 0 times in set s1.
The number '10' occurs 1 times in set s1.
The number '20' occurs 1 times in set s1.
The number of elements in the set s1 is: 2.
```

## <a name="emplace"></a>emplace

Vloží prvek sestavený na místě (nejsou provedeny žádné operace kopírování nebo přesunutí).

```cpp
template <class... Args>
pair<iterator, bool>
emplace(
    Args&&... args);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|-|-|
|*argumentů*|Argumenty předané k vytvoření elementu, který má být vložen do sady, pokud již neobsahují element, jehož hodnota je ekvivalentně seřazena.|

### <a name="return-value"></a>Návratová hodnota

[Dvojice](../standard-library/pair-structure.md) , jejíž logická komponenta vrátí hodnotu true, pokud bylo provedeno vložení, a hodnotu false, pokud mapa již obsahovala prvek, jehož hodnota měla v řazení odpovídající hodnotu. Komponenta iterátoru dvojice návratová hodnota vrátí adresu, kam byl vložen nový prvek (Pokud je logická komponenta true) nebo kde již byl element umístěn (Pokud je logická komponenta false).

### <a name="remarks"></a>Poznámky

Tato funkce neověřuje žádné iterátory ani odkazy.

V případě, že je vyvolána výjimka, stav kontejneru není změněn.

### <a name="example"></a>Příklad

```cpp
// set_emplace.cpp
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
    set<string> s1;

    auto ret = s1.emplace("ten");

    if (!ret.second){
        cout << "Emplace failed, element with value \"ten\" already exists."
            << endl << "  The existing element is (" << *ret.first << ")"
            << endl;
        cout << "set not modified" << endl;
    }
    else{
        cout << "set modified, now contains ";
        print(s1);
    }
    cout << endl;

    ret = s1.emplace("ten");

    if (!ret.second){
        cout << "Emplace failed, element with value \"ten\" already exists."
            << endl << "  The existing element is (" << *ret.first << ")"
            << endl;
    }
    else{
        cout << "set modified, now contains ";
        print(s1);
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
Argumenty předané k vytvoření elementu, který má být vložen do sady, pokud již sada neobsahuje tento prvek nebo všeobecně obecně, pokud již neobsahuje prvek, jehož hodnota je ekvivalentně seřazena.

*kde*\
Místo zahájení vyhledání správného bodu vložení. (Pokud tento bod bezprostředně předchází *místu, k*vložení může dojít v konstantním času v čase namísto logaritmické doby.)

### <a name="return-value"></a>Návratová hodnota

Iterátor nově vloženého prvku.

Pokud se vložení nezdařilo, protože prvek již existuje, vrátí iterátor existujícímu prvku.

### <a name="remarks"></a>Poznámky

Tato funkce neověřuje žádné iterátory ani odkazy.

V případě, že je vyvolána výjimka, stav kontejneru není změněn.

### <a name="example"></a>Příklad

```cpp
// set_emplace.cpp
// compile with: /EHsc
#include <set>
#include <string>
#include <iostream>

using namespace std;

template <typename S> void print(const S& s) {
    cout << s.size() << " elements: " << endl;

    for (const auto& p : s) {
        cout << "(" << p <<  ") ";
    }

    cout << endl;
}

int main()
{
    set<string> s1;

    // Emplace some test data
    s1.emplace("Anna");
    s1.emplace("Bob");
    s1.emplace("Carmine");

    cout << "set starting data: ";
    print(s1);
    cout << endl;

    // Emplace with hint
    // s1.end() should be the "next" element after this emplacement
    s1.emplace_hint(s1.end(), "Doug");

    cout << "set modified, now contains ";
    print(s1);
    cout << endl;
}
```

## <a name="empty"></a>obsahovat

Testuje, zda je objekt set prázdný.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Návratová hodnota

**true** , pokud je sada prázdná; **false** , pokud je sada neprázdná.

### <a name="example"></a>Příklad

```cpp
// set_empty.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1, s2;
   s1.insert ( 1 );

   if ( s1.empty( ) )
      cout << "The set s1 is empty." << endl;
   else
      cout << "The set s1 is not empty." << endl;

   if ( s2.empty( ) )
      cout << "The set s2 is empty." << endl;
   else
      cout << "The set s2 is not empty." << endl;
}
```

```Output
The set s1 is not empty.
The set s2 is empty.
```

## <a name="end"></a>účelu

Vrátí iterátor za koncem.

```cpp
const_iterator end() const;

iterator end();
```

### <a name="return-value"></a>Návratová hodnota

Iterace po konci. Pokud je sada prázdná a pak `set::end() == set::begin()`.

### <a name="remarks"></a>Poznámky

**End** slouží k otestování, zda iterátor prošl na konci jeho sady.

Hodnota vrácená funkcí **End** nesmí být zpětně odkazovaná.

Příklad kódu naleznete v tématu [set:: Find](#find).

## <a name="equal_range"></a>equal_range

Vrátí dvojici iterátorů v uvedeném pořadí na první prvek v sadě s klíčem, který je větší nebo roven zadanému klíči a prvnímu prvku v sadě s klíčem, který je větší než klíč.

```cpp
pair <const_iterator, const_iterator> equal_range (const Key& key) const;

pair <iterator, iterator> equal_range (const Key& key);
```

### <a name="parameters"></a>Parametry

\ *klíčů*
Klíč argumentu, který má být porovnán s klíčem řazení prvku z prohledávané sady.

### <a name="return-value"></a>Návratová hodnota

Pár iterátorů, kde první je [lower_bound](#lower_bound) klíče a druhý je [Upper_bound](#upper_bound) klíče.

Chcete-li získat přístup k prvnímu iterátoru páru `pr` vráceném členskou funkcí, použijte `pr`. **nejprve**a pro zpětnou vazbu dolního iterátoru použijte \*(`pr`. **první**). Pro přístup k druhému iterátoru páru `pr` vráceném členskou funkcí použijte `pr`. za **druhé**a pro zpětnou vazbu k hornímu iterátoru použijte \*(`pr`. **sekundy**).

### <a name="example"></a>Příklad

```cpp
// set_equal_range.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   typedef set<int, less< int > > IntSet;
   IntSet s1;
   set <int, less< int > > :: const_iterator s1_RcIter;

   s1.insert( 10 );
   s1.insert( 20 );
   s1.insert( 30 );

   pair <IntSet::const_iterator, IntSet::const_iterator> p1, p2;
   p1 = s1.equal_range( 20 );

   cout << "The upper bound of the element with "
        << "a key of 20 in the set s1 is: "
        << *(p1.second) << "." << endl;

   cout << "The lower bound of the element with "
        << "a key of 20 in the set s1 is: "
        << *(p1.first) << "." << endl;

   // Compare the upper_bound called directly
   s1_RcIter = s1.upper_bound( 20 );
   cout << "A direct call of upper_bound( 20 ) gives "
        << *s1_RcIter << "," << endl
        << "matching the 2nd element of the pair"
        << " returned by equal_range( 20 )." << endl;

   p2 = s1.equal_range( 40 );

   // If no match is found for the key,
   // both elements of the pair return end( )
   if ( ( p2.first == s1.end( ) ) && ( p2.second == s1.end( ) ) )
      cout << "The set s1 doesn't have an element "
           << "with a key less than 40." << endl;
   else
      cout << "The element of set s1 with a key >= 40 is: "
           << *(p1.first) << "." << endl;
}
```

```Output
The upper bound of the element with a key of 20 in the set s1 is: 30.
The lower bound of the element with a key of 20 in the set s1 is: 20.
A direct call of upper_bound( 20 ) gives 30,
matching the 2nd element of the pair returned by equal_range( 20 ).
The set s1 doesn't have an element with a key less than 40.
```

## <a name="erase"></a>ověřování

Odebere prvek nebo rozsah prvků v objektu set od zadané pozice nebo odebere prvky, které odpovídají zadanému klíči.

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

Pro první dvě členské funkce obousměrný iterátor, který označí první prvek zbývající za jakýmikoli odstraněnými prvky, nebo prvek, který je koncem objektu set, pokud žádný takový prvek neexistuje.

Třetí členská funkce vrátí počet prvků, které byly odebrány z objektu set.

### <a name="example"></a>Příklad

```cpp
// set_erase.cpp
// compile with: /EHsc
#include <set>
#include <string>
#include <iostream>
#include <iterator> // next() and prev() helper functions

using namespace std;

using myset = set<string>;

void printset(const myset& s) {
    for (const auto& iter : s) {
        cout << " [" << iter << "]";
    }
    cout << endl << "size() == " << s.size() << endl << endl;
}

int main()
{
    myset s1;

    // Fill in some data to test with, one at a time
    s1.insert("Bob");
    s1.insert("Robert");
    s1.insert("Bert");
    s1.insert("Rob");
    s1.insert("Bobby");

    cout << "Starting data of set s1 is:" << endl;
    printset(s1);
    // The 1st member function removes an element at a given position
    s1.erase(next(s1.begin()));
    cout << "After the 2nd element is deleted, the set s1 is:" << endl;
    printset(s1);

    // Fill in some data to test with, one at a time, using an initializer list
    myset s2{ "meow", "hiss", "purr", "growl", "yowl" };

    cout << "Starting data of set s2 is:" << endl;
    printset(s2);
    // The 2nd member function removes elements
    // in the range [First, Last)
    s2.erase(next(s2.begin()), prev(s2.end()));
    cout << "After the middle elements are deleted, the set s2 is:" << endl;
    printset(s2);

    myset s3;

    // Fill in some data to test with, one at a time, using emplace
    s3.emplace("C");
    s3.emplace("C#");
    s3.emplace("D");
    s3.emplace("D#");
    s3.emplace("E");
    s3.emplace("E#");
    s3.emplace("F");
    s3.emplace("F#");
    s3.emplace("G");
    s3.emplace("G#");
    s3.emplace("A");
    s3.emplace("A#");
    s3.emplace("B");

    cout << "Starting data of set s3 is:" << endl;
    printset(s3);
    // The 3rd member function removes elements with a given Key
    myset::size_type count = s3.erase("E#");
    // The 3rd member function also returns the number of elements removed
    cout << "The number of elements removed from s3 is: " << count << "." << endl;
    cout << "After the element with a key of \"E#\" is deleted, the set s3 is:" << endl;
    printset(s3);
}
```

## <a name="find"></a>najít

Vrátí iterátor, který odkazuje na umístění prvku v objektu set, který má klíč shodný se zadaným klíčem.

```cpp
iterator find(const Key& key);

const_iterator find(const Key& key) const;
```

### <a name="parameters"></a>Parametry

\ *klíčů*
Hodnota klíče, která má být porovnána klíčem řazení prvku z prohledávané sady.

### <a name="return-value"></a>Návratová hodnota

Iterátor, který odkazuje na umístění elementu se zadaným klíčem, nebo umístění, které následuje po posledním prvku v sadě (`set::end()`), pokud se pro klíč nenajde žádná shoda.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí iterátor, který odkazuje na prvek v sadě, jejíž klíč je ekvivalentní *klíči* argumentu v binárním predikátu, který vystaví řazení na základě vztahu k porovnatelnosti méně než.

Pokud je vrácená hodnota `find` přiřazena k `const_iterator`, objekt set nelze upravit. Pokud je vrácená hodnota `find` přiřazená k `iterator`, objekt sady se dá upravit.

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
    set<int> s1({ 40, 45 });
    cout << "The starting set s1 is: " << endl;
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

    cout << "The modified set s1 is: " << endl;
    print_collection(s1);
    cout << endl;
    findit(s1, 45);
    findit(s1, 6);
}
```

## <a name="get_allocator"></a>get_allocator

Vrátí kopii objektu přidělování, která se používá k vytvoření sady.

```cpp
allocator_type get_allocator() const;
```

### <a name="return-value"></a>Návratová hodnota

Alokátor používaný sadou pro správu paměti, což je parametr šablony `Allocator`.

Další informace o `Allocator`naleznete v části poznámky v tématu [sada třídy](../standard-library/set-class.md) .

### <a name="remarks"></a>Poznámky

Přidělování pro třídu set určují, jak Třída spravuje úložiště. Výchozí přidělující třídy kontejnerů C++ standardní knihovny jsou dostačující pro většinu programovacích potřeb. Psaní a používání vlastního třídy přidělování je pokročilým C++ tématem.

### <a name="example"></a>Příklad

```cpp
// set_get_allocator.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int>::allocator_type s1_Alloc;
   set <int>::allocator_type s2_Alloc;
   set <double>::allocator_type s3_Alloc;
   set <int>::allocator_type s4_Alloc;

   // The following lines declare objects
   // that use the default allocator.
   set <int> s1;
   set <int, allocator<int> > s2;
   set <double, allocator<double> > s3;

   s1_Alloc = s1.get_allocator( );
   s2_Alloc = s2.get_allocator( );
   s3_Alloc = s3.get_allocator( );

   cout << "The number of integers that can be allocated"
        << endl << "before free memory is exhausted: "
        << s2.max_size( ) << "." << endl;

   cout << "\nThe number of doubles that can be allocated"
        << endl << "before free memory is exhausted: "
        << s3.max_size( ) <<  "." << endl;

   // The following line creates a set s4
   // with the allocator of multiset s1.
   set <int> s4( less<int>( ), s1_Alloc );

   s4_Alloc = s4.get_allocator( );

   // Two allocators are interchangeable if
   // storage allocated from each can be
   // deallocated by the other
   if( s1_Alloc == s4_Alloc )
   {
      cout << "\nThe allocators are interchangeable."
           << endl;
   }
   else
   {
      cout << "\nThe allocators are not interchangeable."
           << endl;
   }
}
```

## <a name="insert"></a>zadat

Vloží prvek nebo rozsah prvků do objektu set.

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
Hodnota prvku, který má být vložen do sady, pokud již neobsahuje prvek, jehož hodnota je ekvivalentní.

*Kde*\
Místo zahájení vyhledání správného bodu vložení. (Pokud tento bod bezprostředně předchází *místu, k*vložení může dojít v konstantním času v čase namísto logaritmické doby.)

*ValTy*\
Parametr šablony, který určuje typ argumentu, který může sada použít k vytvoření prvku [value_type](../standard-library/map-class.md#value_type)a Perfect-Forwards *Val* jako argument.

*První*\
Pozice prvního prvku, který chcete zkopírovat.

*Poslední*\
Pozice bezprostředně za posledním prvkem, který chcete zkopírovat.

*InputIterator*\
Argument funkce šablony, který splňuje požadavky [vstupního iterátoru](../standard-library/input-iterator-tag-struct.md) , který odkazuje na prvky typu, které lze použít k vytvoření [value_type](../standard-library/map-class.md#value_type) objektů.

\ *IList*
[Initializer_list](../standard-library/initializer-list.md) , ze kterých se mají kopírovat prvky

### <a name="return-value"></a>Návratová hodnota

Členské funkce s jedním prvkem, (1) a (2), vrátí [dvojici](../standard-library/pair-structure.md) , jejíž **logická** komponenta má hodnotu true, pokud bylo provedeno vložení, a hodnotu false, pokud již sada obsahuje element s ekvivalentní hodnotou v řazení. Komponenta iterátoru dvojice vrácených hodnot odkazuje na nově vložený element, pokud je **logická** komponenta true nebo na existující prvek, pokud je komponenta **bool** false.

Členské funkce s jedním prvkem, (3) a (4), vrátí iterátor, který odkazuje na pozici, kam byl nový element vložen do sady, nebo pokud element s ekvivalentním klíčem již existuje, pro existující prvek.

### <a name="remarks"></a>Poznámky

Touto funkcí nejsou zneplatněny žádné iterátory, ukazatele ani odkazy.

Při vložení pouze jednoho prvku, pokud je vyvolána výjimka, není změněn stav kontejneru. Pokud je při vkládání více prvků vyvolána výjimka, kontejner zůstane v neurčeném, ale platném stavu.

Chcete-li získat přístup k součásti iterátoru `pair` `pr`, který je vrácen členskými funkcemi s jedním prvkem, použijte `pr.first`; Chcete-li překázat na iterátor v rámci vráceného páru, použijte `*pr.first`, což vám poskytne element. Pro přístup ke komponentě **bool** použijte `pr.second`. Příklad naleznete v ukázce kódu dále v tomto článku.

[Value_type](../standard-library/map-class.md#value_type) kontejneru je definice typu, která patří do kontejneru, a v případě sady `set<V>::value_type` je typ `const V`.

Člen rozsahu (5) vloží sekvenci hodnot prvků do sady, která odpovídá každému prvku řešenému iterátorem v rozsahu `[First, Last)`; Proto se `Last` nevloží. Členská funkce kontejneru `end()` se vztahuje k pozici hned za posledním prvkem v kontejneru, například příkaz `s.insert(v.begin(), v.end());` se pokusí vložit všechny prvky `v` do `s`. Vkládají se pouze prvky, které v rozsahu obsahují jedinečné hodnoty. Duplicitní hodnoty jsou ignorovány. Chcete-li sledovat, které prvky jsou odmítnuty, použijte jednoprvkovou verzi funkce `insert`.

Členská funkce seznamu inicializátorů (6) používá [initializer_list](../standard-library/initializer-list.md) ke zkopírování prvků do sady.

Pro vložení elementu vytvořeného na místě – to znamená, že nejsou provedeny žádné operace kopírování nebo přesunu – viz [set:: emplace](#emplace) a [set:: emplace_hint](#emplace_hint).

### <a name="example"></a>Příklad

```cpp
// set_insert.cpp
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
    set<int> s1;
    // call insert(const value_type&) version
    s1.insert({ 1, 10 });
    // call insert(ValTy&&) version
    s1.insert(20);

    cout << "The original set values of s1 are:" << endl;
    print(s1);

    // intentionally attempt a duplicate, single element
    auto ret = s1.insert(1);
    if (!ret.second){
        auto elem = *ret.first;
        cout << "Insert failed, element with value 1 already exists."
            << endl << "  The existing element is (" << elem << ")"
            << endl;
    }
    else{
        cout << "The modified set values of s1 are:" << endl;
        print(s1);
    }
    cout << endl;

    // single element, with hint
    s1.insert(s1.end(), 30);
    cout << "The modified set values of s1 are:" << endl;
    print(s1);
    cout << endl;

    // The templatized version inserting a jumbled range
    set<int> s2;
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

    cout << "The modified set values of s2 are:" << endl;
    print(s2);
    cout << endl;

    // The templatized versions move-constructing elements
    set<string>  s3;
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

    set<int> s4;
    // Insert the elements from an initializer_list
    s4.insert({ 4, 44, 2, 22, 3, 33, 1, 11, 5, 55 });
    cout << "After initializer_list insertion, s4 contains:" << endl;
    print(s4);
    cout << endl;
}
```

## <a name="iterator"></a>iterátor

Typ, který poskytuje konstantní [obousměrný iterátor](../standard-library/bidirectional-iterator-tag-struct.md) , který může číst libovolný prvek v sadě.

```cpp
typedef implementation-defined iterator;
```

### <a name="example"></a>Příklad

Podívejte se na příklad pro [začátek](#begin) příkladu, jak deklarovat a použít `iterator`.

## <a name="key_comp"></a>key_comp

Načte kopii objektu porovnání, která je použita pro seřazení klíčů v objektu set.

```cpp
key_compare key_comp() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí objekt funkce, který sada používá pro seřazení jeho prvků, což je parametr šablony `Traits`.

Další informace o `Traits` naleznete v tématu [sada třídy](../standard-library/set-class.md) .

### <a name="remarks"></a>Poznámky

Uložený objekt definuje členskou funkci:

**bool – operátor ()** (**const Key &** `_xVal`, **const Key &** `_yVal`);

Vrátí **hodnotu true** , pokud `_xVal` předchází a není rovna `_yVal` v pořadí řazení.

Všimněte si, že [key_compare](#key_compare) i [value_compare](#value_compare) jsou synonyma pro parametr šablony `Traits`. Oba typy jsou k dispozici pro třídy set a multiset, kde jsou identické, pro kompatibilitu s třídami map a multimap, kde jsou odlišné.

### <a name="example"></a>Příklad

```cpp
// set_key_comp.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;

   set <int, less<int> > s1;
   set<int, less<int> >::key_compare kc1 = s1.key_comp( ) ;
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
           << "where kc1 is the function object of s1."
           << endl;
   }

   set <int, greater<int> > s2;
   set<int, greater<int> >::key_compare kc2 = s2.key_comp( ) ;
   bool result2 = kc2( 2, 3 ) ;
   if(result2 == true)
   {
      cout << "kc2( 2,3 ) returns value of true, "
           << "where kc2 is the function object of s2."
           << endl;
   }
   else
   {
      cout << "kc2( 2,3 ) returns value of false, "
           << "where kc2 is the function object of s2."
           << endl;
   }
}
```

```Output
kc1( 2,3 ) returns value of true, where kc1 is the function object of s1.
kc2( 2,3 ) returns value of false, where kc2 is the function object of s2.
```

## <a name="key_compare"></a>key_compare

Typ, který poskytuje objekt funkce, který může porovnat dva klíče řazení pro určení relativního pořadí dvou prvků v objektu set.

```cpp
typedef Traits key_compare;
```

### <a name="remarks"></a>Poznámky

`key_compare` je synonymum pro parametr šablony `Traits`.

Další informace o `Traits` naleznete v tématu [sada třídy](../standard-library/set-class.md) .

Všimněte si, že `key_compare` i [value_compare](#value_compare) jsou synonyma pro parametr šablony `Traits`. Oba typy jsou k dispozici pro třídy set a multiset, kde jsou identické, pro kompatibilitu s třídami map a multimap, kde jsou odlišné.

### <a name="example"></a>Příklad

Příklad, jak deklarovat a používat `key_compare`, naleznete v příkladu pro [key_comp](#key_comp) .

## <a name="key_type"></a>key_type

Typ, který popisuje objekt uložený jako prvek sady v jeho kapacitě jako klíč řazení.

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>Poznámky

`key_type` je synonymum pro parametr šablony `Key`.

Další informace o `Key`naleznete v části poznámky v tématu [sada třídy](../standard-library/set-class.md) .

Všimněte si, že `key_type` i [value_type](#value_type) jsou synonyma pro parametr šablony `Key`. Oba typy jsou k dispozici pro třídy set a multiset, kde jsou identické, pro kompatibilitu s třídami map a multimap, kde jsou odlišné.

### <a name="example"></a>Příklad

Příklad, jak deklarovat a používat `key_type`, naleznete v příkladu pro [value_type](#value_type) .

## <a name="lower_bound"></a>lower_bound

Vrátí iterátor na první prvek objektu set s klíčem, který je roven nebo větší než zadaný klíč.

```cpp
const_iterator lower_bound(const Key& key) const;

iterator lower_bound(const Key& key);
```

### <a name="parameters"></a>Parametry

\ *klíčů*
Klíč argumentu, který má být porovnán s klíčem řazení prvku z prohledávané sady.

### <a name="return-value"></a>Návratová hodnota

Iterátor nebo `const_iterator`, které řeší umístění elementu v sadě, které mají klíč, který je roven nebo větší než klíč argumentu nebo který řeší umístění, které následuje po posledním prvku v objektu set, pokud se pro klíč nenajde žádná shoda.

### <a name="example"></a>Příklad

```cpp
// set_lower_bound.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1;
   set <int> :: const_iterator s1_AcIter, s1_RcIter;

   s1.insert( 10 );
   s1.insert( 20 );
   s1.insert( 30 );

   s1_RcIter = s1.lower_bound( 20 );
   cout << "The element of set s1 with a key of 20 is: "
        << *s1_RcIter << "." << endl;

   s1_RcIter = s1.lower_bound( 40 );

   // If no match is found for the key, end( ) is returned
   if ( s1_RcIter == s1.end( ) )
      cout << "The set s1 doesn't have an element "
           << "with a key of 40." << endl;
   else
      cout << "The element of set s1 with a key of 40 is: "
           << *s1_RcIter << "." << endl;

   // The element at a specific location in the set can be found
   // by using a dereferenced iterator that addresses the location
   s1_AcIter = s1.end( );
   s1_AcIter--;
   s1_RcIter = s1.lower_bound( *s1_AcIter );
   cout << "The element of s1 with a key matching "
        << "that of the last element is: "
        << *s1_RcIter << "." << endl;
}
```

```Output
The element of set s1 with a key of 20 is: 20.
The set s1 doesn't have an element with a key of 40.
The element of s1 with a key matching that of the last element is: 30.
```

## <a name="max_size"></a>max_size

Vrátí maximální délku objektu set.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>Návratová hodnota

Maximální možná délka sady.

### <a name="example"></a>Příklad

```cpp
// set_max_size.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1;
   set <int>::size_type i;

   i = s1.max_size( );
   cout << "The maximum possible length "
        << "of the set is " << i << "." << endl;
}
```

## <a name="op_eq"></a>operátor =

Nahradí prvky tohoto `set` pomocí prvků z jiného `set`.

```cpp
set& operator=(const set& right);

set& operator=(set&& right);
```

### <a name="parameters"></a>Parametry

*pravé*\
`set` poskytují nové prvky, které mají být přiřazeny k této `set`.

### <a name="remarks"></a>Poznámky

První verze `operator=` používá [odkaz lvalue](../cpp/lvalue-reference-declarator-amp.md) pro *pravou*, ke zkopírování prvků z *pravého* k tomuto `set`.

Druhá verze používá [odkaz rvalue](../cpp/rvalue-reference-declarator-amp-amp.md) vpravo. Přesune prvky z *pravého* na tento `set`.

Všechny prvky v tomto `set` před provedením funkce operátoru jsou zahozeny.

### <a name="example"></a>Příklad

```cpp
// set_operator_as.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
   {
   using namespace std;
   set<int> v1, v2, v3;
   set<int>::iterator iter;

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

## <a name="pointer"></a>ukazatele

Typ, který poskytuje ukazatel na prvek v objektu set.

```cpp
typedef typename allocator_type::pointer pointer;
```

### <a name="remarks"></a>Poznámky

**Ukazatel** typu lze použít pro úpravu hodnoty prvku.

Ve většině případů by měl být použit [iterátor](#iterator) pro přístup k prvkům v objektu set.

## <a name="rbegin"></a>rbegin

Vrátí iterátor adresující první prvek v obráceném objektu set.

```cpp
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```

### <a name="return-value"></a>Návratová hodnota

Reverzní obousměrný iterátor, který adresuje první prvek v obráceném množině nebo řeší, co byl posledním prvkem v neobrácené sadě.

### <a name="remarks"></a>Poznámky

`rbegin` se používá s obrácenou sadou, která je použita stejně jako [Begin](#begin) , se používá se sadou.

Pokud je vrácená hodnota `rbegin` přiřazena k `const_reverse_iterator`, objekt set nelze upravit. Pokud je vrácená hodnota `rbegin` přiřazena k `reverse_iterator`, lze objekt set upravit.

`rbegin` lze použít k iterování v rámci sady zpět.

### <a name="example"></a>Příklad

```cpp
// set_rbegin.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1;
   set <int>::iterator s1_Iter;
   set <int>::reverse_iterator s1_rIter;

   s1.insert( 10 );
   s1.insert( 20 );
   s1.insert( 30 );

   s1_rIter = s1.rbegin( );
   cout << "The first element in the reversed set is "
        << *s1_rIter << "." << endl;

   // begin can be used to start an iteration
   // through a set in a forward order
   cout << "The set is:";
   for ( s1_Iter = s1.begin( ) ; s1_Iter != s1.end( ); s1_Iter++ )
      cout << " " << *s1_Iter;
   cout << endl;

   // rbegin can be used to start an iteration
   // through a set in a reverse order
   cout << "The reversed set is:";
   for ( s1_rIter = s1.rbegin( ) ; s1_rIter != s1.rend( ); s1_rIter++ )
      cout << " " << *s1_rIter;
   cout << endl;

   // A set element can be erased by dereferencing to its key
   s1_rIter = s1.rbegin( );
   s1.erase ( *s1_rIter );

   s1_rIter = s1.rbegin( );
   cout << "After the erasure, the first element "
        << "in the reversed set is "<< *s1_rIter << "." << endl;
}
```

```Output
The first element in the reversed set is 30.
The set is: 10 20 30
The reversed set is: 30 20 10
After the erasure, the first element in the reversed set is 20.
```

## <a name="reference"></a>odkaz

Typ, který poskytuje odkaz na prvek uložený v objektu set.

```cpp
typedef typename allocator_type::reference reference;
```

### <a name="example"></a>Příklad

```cpp
// set_reference.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1;

   s1.insert( 10 );
   s1.insert( 20 );

   // Declare and initialize a reference &Ref1 to the 1st element
   const int &Ref1 = *s1.begin( );

   cout << "The first element in the set is "
        << Ref1 << "." << endl;
}
```

```Output
The first element in the set is 10.
```

## <a name="rend"></a>rend

Vrátí iterátor adresující umístění následující po posledním prvku v obráceném objektu set.

```cpp
const_reverse_iterator rend() const;

reverse_iterator rend();
```

### <a name="return-value"></a>Návratová hodnota

Zpětný obousměrný iterátor, který adresuje umístění následující po posledním prvku v obráceném seznamu (umístění, které předchází prvnímu prvku v neobrácené sadě).

### <a name="remarks"></a>Poznámky

`rend` se používá s obrácenou sadou, která je použita stejně jako [End](#end) , se používá se sadou.

Pokud je vrácená hodnota `rend` přiřazena k `const_reverse_iterator`, objekt set nelze upravit. Pokud je vrácená hodnota `rend` přiřazena k `reverse_iterator`, lze objekt set upravit. Hodnota vrácená `rend` by neměla být zpětně odkazovaná.

`rend` lze použít k otestování, zda zpětný iterátor dosáhl konce jeho sady.

### <a name="example"></a>Příklad

```cpp
// set_rend.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main() {
   using namespace std;
   set <int> s1;
   set <int>::iterator s1_Iter;
   set <int>::reverse_iterator s1_rIter;
   set <int>::const_reverse_iterator s1_crIter;

   s1.insert( 10 );
   s1.insert( 20 );
   s1.insert( 30 );

   s1_rIter = s1.rend( );
   s1_rIter--;
   cout << "The last element in the reversed set is "
        << *s1_rIter << "." << endl;

   // end can be used to terminate an iteration
   // through a set in a forward order
   cout << "The set is: ";
   for ( s1_Iter = s1.begin( ) ; s1_Iter != s1.end( ); s1_Iter++ )
      cout << *s1_Iter << " ";
   cout << "." << endl;

   // rend can be used to terminate an iteration
   // through a set in a reverse order
   cout << "The reversed set is: ";
   for ( s1_rIter = s1.rbegin( ) ; s1_rIter != s1.rend( ); s1_rIter++ )
      cout << *s1_rIter << " ";
   cout << "." << endl;

   s1_rIter = s1.rend( );
   s1_rIter--;
   s1.erase ( *s1_rIter );

   s1_rIter = s1.rend( );
   --s1_rIter;
   cout << "After the erasure, the last element in the "
        << "reversed set is " << *s1_rIter << "." << endl;
}
```

## <a name="reverse_iterator"></a>reverse_iterator

Typ, který poskytuje obousměrný iterátor, který může číst nebo upravovat prvek v obráceném objektu set.

```cpp
typedef std::reverse_iterator<iterator> reverse_iterator;
```

### <a name="remarks"></a>Poznámky

Typ `reverse_iterator` slouží k iterování skrze sadu v obráceném pořadí.

### <a name="example"></a>Příklad

Příklad, jak deklarovat a používat `reverse_iterator`, naleznete v příkladu pro [rbegin](#rbegin) .

## <a name="set"></a>stanovenými

Zkonstruuje objekt set, který je prázdný nebo který je kopií celého nebo části některého jiného objektu set.

```cpp
set();

explicit set(
    const Traits& Comp);

set(
    const Traits& Comp,
    const Allocator& Al);

set(
    const set& Right);

set(
    set&& Right);

set(
    initializer_list<Type> IList);

set(
    initializer_list<Type> IList,
    const Compare& Comp);

set(
    initializer_list<Type> IList,
    const Compare& Comp,
    const Allocator& Al);

template <class InputIterator>
set(
    InputIterator First,
    InputIterator Last);

template <class InputIterator>
set(
    InputIterator First,
    InputIterator Last,
    const Traits& Comp);

template <class InputIterator>
set(
    InputIterator First,
    InputIterator Last,
    const Traits& Comp,
    const Allocator& Al);
```

### <a name="parameters"></a>Parametry

*Al*\
Třída přidělování úložiště, která se má použít pro tento objekt sady, ve kterém se výchozí hodnota `Allocator`.

\ *comp*
Funkce porovnání typu `const Traits` slouží k uspořádání prvků v sadě, které mají výchozí hodnotu `Compare`.

*Rght*\
Sada, kterou má vytvořená sada mít kopii.

*První*\
Pozice prvního prvku v rozsahu prvků, které mají být zkopírovány.

*Poslední*\
Pozice prvního prvku mimo rozsah prvků, které mají být zkopírovány.

\ *IList*
Seznam initializer_list, ze kterého chcete kopírovat prvky.

### <a name="remarks"></a>Poznámky

Všechny konstruktory ukládají typ objektu přidělování, který spravuje úložiště paměti pro sadu a které lze později vrátit voláním [get_allocator](#get_allocator). Parametr allocator je často v deklaraci třídy vynechán a makra předběžného zpracování jsou použita k nahrazení alternativních alokátorů.

Všechny konstruktory inicializují své sady.

Všechny konstruktory ukládají objekt funkce typu `Traits`, který se používá k navázání objednávky mezi klíči sady a které mohou být později vráceny voláním [key_comp](#key_comp).

První tři konstruktory určují prázdnou počáteční sadu, druhý určující typ funkce porovnání (`comp`), která se má použít při vytváření pořadí prvků a třetí, explicitně určující typ přidělujícího objektu (`al`), který se má použít. Klíčové slovo **Explicit** potlačí určité druhy automatických převodů typu.

Čtvrtý konstruktor určuje kopii sady `right`.

Následující tři konstruktory používají initializer_list k určení prvků.

Následující tři konstruktory kopírují rozsah [`first`, `last`) sady se zvýšením explicitního určení typu funkce porovnání třídy `Traits` a **přidělování**.

Osmý konstruktor určuje kopii sady pomocí přesunutí `right`.

### <a name="example"></a>Příklad

```cpp
// set_set.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main()
{
    using namespace std;

    // Create an empty set s0 of key type integer
    set <int> s0;

    // Create an empty set s1 with the key comparison
    // function of less than, then insert 4 elements
    set <int, less<int> > s1;
    s1.insert(10);
    s1.insert(20);
    s1.insert(30);
    s1.insert(40);

    // Create an empty set s2 with the key comparison
    // function of less than, then insert 2 elements
    set <int, less<int> > s2;
    s2.insert(10);
    s2.insert(20);

    // Create a set s3 with the
    // allocator of set s1
    set <int>::allocator_type s1_Alloc;
    s1_Alloc = s1.get_allocator();
    set <int> s3(less<int>(), s1_Alloc);
    s3.insert(30);

    // Create a copy, set s4, of set s1
    set <int> s4(s1);

    // Create a set s5 by copying the range s1[ first,  last)
    set <int>::const_iterator s1_bcIter, s1_ecIter;
    s1_bcIter = s1.begin();
    s1_ecIter = s1.begin();
    s1_ecIter++;
    s1_ecIter++;
    set <int> s5(s1_bcIter, s1_ecIter);

    // Create a set s6 by copying the range s4[ first,  last)
    // and with the allocator of set s2
    set <int>::allocator_type s2_Alloc;
    s2_Alloc = s2.get_allocator();
    set <int> s6(s4.begin(), ++s4.begin(), less<int>(), s2_Alloc);

    cout << "s1 =";
    for (auto i : s1)
        cout << " " << i;
    cout << endl;

    cout << "s2 = " << *s2.begin() << " " << *++s2.begin() << endl;

    cout << "s3 =";
    for (auto i : s3)
        cout << " " << i;
    cout << endl;

    cout << "s4 =";
    for (auto i : s4)
        cout << " " << i;
    cout << endl;

    cout << "s5 =";
    for (auto i : s5)
        cout << " " << i;
    cout << endl;

    cout << "s6 =";
    for (auto i : s6)
        cout << " " << i;
    cout << endl;

    // Create a set by moving s5
    set<int> s7(move(s5));
    cout << "s7 =";
    for (auto i : s7)
        cout << " " << i;
    cout << endl;

    // Create a set with an initializer_list
    cout << "s8 =";
    set<int> s8{ { 1, 2, 3, 4 } };
    for (auto i : s8)
        cout << " " << i;
    cout << endl;

    cout << "s9 =";
    set<int> s9{ { 5, 6, 7, 8 }, less<int>() };
    for (auto i : s9)
        cout << " " << i;
    cout << endl;

    cout << "s10 =";
    set<int> s10{ { 10, 20, 30, 40 }, less<int>(), s9.get_allocator() };
    for (auto i : s10)
        cout << " " << i;
    cout << endl;
}
```

```Output
s1 = 10 20 30 40s2 = 10 20s3 = 30s4 = 10 20 30 40s5 = 10 20s6 = 10s7 = 10 20s8 = 1 2 3 4s9 = 5 6 7 8s10 = 10 20 30 40
```

## <a name="size"></a>hodnota

Vrátí počet prvků v objektu set.

```cpp
size_type size() const;
```

### <a name="return-value"></a>Návratová hodnota

Aktuální délka sady.

### <a name="example"></a>Příklad

```cpp
// set_size.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1;
   set <int> :: size_type i;

   s1.insert( 1 );
   i = s1.size( );
   cout << "The set length is " << i << "." << endl;

   s1.insert( 2 );
   i = s1.size( );
   cout << "The set length is now " << i << "." << endl;
}
```

```Output
The set length is 1.
The set length is now 2.
```

## <a name="size_type"></a>size_type

Celočíselný typ bez znaménka představující počet prvků v objektu set.

```cpp
typedef typename allocator_type::size_type size_type;
```

### <a name="example"></a>Příklad

Podívejte se na příklad pro [Velikost](#size) pro příklad, jak deklarovat a použít `size_type`

## <a name="swap"></a>adresu

Vymění prvky dvou sad.

```cpp
void swap(
    set<Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*pravé*\
Argument sada, která poskytuje prvky pro záměnu s cílovou sadou.

### <a name="remarks"></a>Poznámky

Členská funkce neověřuje žádné odkazy, ukazatele nebo iterátory, které určují elementy ve dvou sadách, jejichž prvky jsou vyměňovány.

### <a name="example"></a>Příklad

```cpp
// set_swap.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1, s2, s3;
   set <int>::iterator s1_Iter;

   s1.insert( 10 );
   s1.insert( 20 );
   s1.insert( 30 );
   s2.insert( 100 );
   s2.insert( 200 );
   s3.insert( 300 );

   cout << "The original set s1 is:";
   for ( s1_Iter = s1.begin( ); s1_Iter != s1.end( ); s1_Iter++ )
      cout << " " << *s1_Iter;
   cout   << "." << endl;

   // This is the member function version of swap
   s1.swap( s2 );

   cout << "After swapping with s2, list s1 is:";
   for ( s1_Iter = s1.begin( ); s1_Iter != s1.end( ); s1_Iter++ )
      cout << " " << *s1_Iter;
   cout  << "." << endl;

   // This is the specialized template version of swap
   swap( s1, s3 );

   cout << "After swapping with s3, list s1 is:";
   for ( s1_Iter = s1.begin( ); s1_Iter != s1.end( ); s1_Iter++ )
      cout << " " << *s1_Iter;
   cout   << "." << endl;
}
```

```Output
The original set s1 is: 10 20 30.
After swapping with s2, list s1 is: 100 200.
After swapping with s3, list s1 is: 300.
```

## <a name="upper_bound"></a>upper_bound

Vrátí iterátor na první prvek v objektu set s klíčem, který je větší než zadaný klíč.

```cpp
const_iterator upper_bound(const Key& key) const;

iterator upper_bound(const Key& key);
```

### <a name="parameters"></a>Parametry

\ *klíčů*
Klíč argumentu, který má být porovnán s klíčem řazení prvku z prohledávané sady.

### <a name="return-value"></a>Návratová hodnota

`iterator` nebo `const_iterator`, které řeší umístění elementu v sadě s klíčem, který je větší než klíč argumentu, nebo který řeší umístění, které následuje po posledním prvku v objektu set, pokud se pro klíč nenajde žádná shoda.

### <a name="example"></a>Příklad

```cpp
// set_upper_bound.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1;
   set <int> :: const_iterator s1_AcIter, s1_RcIter;

   s1.insert( 10 );
   s1.insert( 20 );
   s1.insert( 30 );

   s1_RcIter = s1.upper_bound( 20 );
   cout << "The first element of set s1 with a key greater "
        << "than 20 is: " << *s1_RcIter << "." << endl;

   s1_RcIter = s1.upper_bound( 30 );

   // If no match is found for the key, end( ) is returned
   if ( s1_RcIter == s1.end( ) )
      cout << "The set s1 doesn't have an element "
           << "with a key greater than 30." << endl;
   else
      cout << "The element of set s1 with a key > 40 is: "
           << *s1_RcIter << "." << endl;

   // The element at a specific location in the set can be found
   // by using a dereferenced iterator addressing the location
   s1_AcIter = s1.begin( );
   s1_RcIter = s1.upper_bound( *s1_AcIter );
   cout << "The first element of s1 with a key greater than"
        << endl << "that of the initial element of s1 is: "
        << *s1_RcIter << "." << endl;
}
```

```Output
The first element of set s1 with a key greater than 20 is: 30.
The set s1 doesn't have an element with a key greater than 30.
The first element of s1 with a key greater than
that of the initial element of s1 is: 20.
```

## <a name="value_comp"></a>value_comp

Získá kopii objektu porovnání použitého pro seřazení hodnot prvků objektu set.

```cpp
value_compare value_comp() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí objekt funkce, který sada používá pro seřazení jeho prvků, což je parametr šablony `Traits`.

Další informace o `Traits` naleznete v tématu [sada třídy](../standard-library/set-class.md) .

### <a name="remarks"></a>Poznámky

Uložený objekt definuje členskou funkci:

**bool – operátor**(**const Key &** `_xVal`, **const Key &** `_yVal`);

Vrátí **hodnotu true** , pokud `_xVal` předchází a není rovna `_yVal` v pořadí řazení.

Všimněte si, že [value_compare](#value_compare) i [key_compare](#key_compare) jsou synonyma pro parametr šablony `Traits`. Oba typy jsou k dispozici pro třídy set a multiset, kde jsou identické, pro kompatibilitu s třídami map a multimap, kde jsou odlišné.

### <a name="example"></a>Příklad

```cpp
// set_value_comp.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;

   set <int, less<int> > s1;
   set <int, less<int> >::value_compare vc1 = s1.value_comp( );
   bool result1 = vc1( 2, 3 );
   if( result1 == true )
   {
      cout << "vc1( 2,3 ) returns value of true, "
           << "where vc1 is the function object of s1."
           << endl;
   }
   else
   {
      cout << "vc1( 2,3 ) returns value of false, "
           << "where vc1 is the function object of s1."
           << endl;
   }

   set <int, greater<int> > s2;
   set<int, greater<int> >::value_compare vc2 = s2.value_comp( );
   bool result2 = vc2( 2, 3 );
   if( result2 == true )
   {
      cout << "vc2( 2,3 ) returns value of true, "
           << "where vc2 is the function object of s2."
           << endl;
   }
   else
   {
      cout << "vc2( 2,3 ) returns value of false, "
           << "where vc2 is the function object of s2."
           << endl;
   }
}
```

```Output
vc1( 2,3 ) returns value of true, where vc1 is the function object of s1.
vc2( 2,3 ) returns value of false, where vc2 is the function object of s2.
```

## <a name="value_compare"></a>value_compare

Typ, který poskytuje objekt funkce, který může porovnat dvě hodnoty prvků pro určení jejich relativního pořadí v sadě.

```cpp
typedef key_compare value_compare;
```

### <a name="remarks"></a>Poznámky

`value_compare` je synonymum pro parametr šablony `Traits`.

Další informace o `Traits` naleznete v tématu [sada třídy](../standard-library/set-class.md) .

Všimněte si, že [key_compare](#key_compare) i `value_compare` jsou synonyma pro parametr šablony `Traits`. Oba typy jsou k dispozici pro třídy set a multiset, kde jsou identické, pro kompatibilitu s třídami map a multimap, kde jsou odlišné.

### <a name="example"></a>Příklad

Příklad, jak deklarovat a používat `value_compare`, naleznete v příkladu pro [value_comp](#value_comp) .

## <a name="value_type"></a>value_type

Typ, který popisuje objekt uložený jako prvek sady v jeho kapacitě jako hodnota.

```cpp
typedef Key value_type;
```

### <a name="remarks"></a>Poznámky

`value_type` je synonymum pro parametr šablony `Key`.

Další informace o `Key`naleznete v části poznámky v tématu [sada třídy](../standard-library/set-class.md) .

Všimněte si, že [key_type](#key_type) i `value_type` jsou synonyma pro parametr šablony `Key`. Oba typy jsou k dispozici pro třídy set a multiset, kde jsou identické, pro kompatibilitu s třídami map a multimap, kde jsou odlišné.

### <a name="example"></a>Příklad

```cpp
// set_value_type.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1;
   set <int>::iterator s1_Iter;

   set <int>::value_type svt_Int;   // Declare value_type
   svt_Int = 10;            // Initialize value_type

   set <int> :: key_type skt_Int;   // Declare key_type
   skt_Int = 20;             // Initialize key_type

   s1.insert( svt_Int );         // Insert value into s1
   s1.insert( skt_Int );         // Insert key into s1

   // A set accepts key_types or value_types as elements
   cout << "The set has elements:";
   for ( s1_Iter = s1.begin( ) ; s1_Iter != s1.end( ); s1_Iter++)
      cout << " " << *s1_Iter;
   cout << "." << endl;
}
```

```Output
The set has elements: 10 20.
```
