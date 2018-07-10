---
title: Vector – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- vector/std::vector::allocator_type
- vector/std::vector::const_iterator
- vector/std::vector::const_pointer
- vector/std::vector::const_reference
- vector/std::vector::const_reverse_iterator
- vector/std::vector::difference_type
- vector/std::vector::iterator
- vector/std::vector::pointer
- vector/std::vector::reference
- vector/std::vector::reverse_iterator
- vector/std::vector::size_type
- vector/std::vector::value_type
- vector/std::vector::assign
- vector/std::vector::at
- vector/std::vector::back
- vector/std::vector::begin
- vector/std::vector::capacity
- vector/std::vector::cbegin
- vector/std::vector::cend
- vector/std::vector::crbegin
- vector/std::vector::crend
- vector/std::vector::clear
- vector/std::vector::data
- vector/std::vector::emplace
- vector/std::vector::emplace_back
- vector/std::vector::empty
- vector/std::vector::end
- vector/std::vector::erase
- vector/std::vector::front
- vector/std::vector::get_allocator
- vector/std::vector::insert
- vector/std::vector::max_size
- vector/std::vector::pop_back
- vector/std::vector::push_back
- vector/std::vector::rbegin
- vector/std::vector::rend
- vector/std::vector::reserve
- vector/std::vector::resize
- vector/std::vector::shrink_to_fit
- vector/std::vector::size
- vector/std::vector::swap
dev_langs:
- C++
helpviewer_keywords:
- std::vector [C++], allocator_type
- std::vector [C++], const_iterator
- std::vector [C++], const_pointer
- std::vector [C++], const_reference
- std::vector [C++], const_reverse_iterator
- std::vector [C++], difference_type
- std::vector [C++], iterator
- std::vector [C++], pointer
- std::vector [C++], reference
- std::vector [C++], reverse_iterator
- std::vector [C++], size_type
- std::vector [C++], value_type
- std::vector [C++], assign
- std::vector [C++], at
- std::vector [C++], back
- std::vector [C++], begin
- std::vector [C++], capacity
- std::vector [C++], cbegin
- std::vector [C++], cend
- std::vector [C++], crbegin
- std::vector [C++], crend
- std::vector [C++], clear
- std::vector [C++], data
- std::vector [C++], emplace
- std::vector [C++], emplace_back
- std::vector [C++], empty
- std::vector [C++], end
- std::vector [C++], erase
- std::vector [C++], front
- std::vector [C++], get_allocator
- std::vector [C++], insert
- std::vector [C++], max_size
- std::vector [C++], pop_back
- std::vector [C++], push_back
- std::vector [C++], rbegin
- std::vector [C++], rend
- std::vector [C++], reserve
- std::vector [C++], resize
- std::vector [C++], shrink_to_fit
- std::vector [C++], size
- std::vector [C++], swap
ms.assetid: a3e0a8f8-7565-4fe0-93e4-e4d74ae1b70d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6ea70adff4f162c432fea96c25e37ecca917d96d
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33862939"
---
# <a name="vector-class"></a>vector – třída

Vector – třída standardní knihovna C++ je třída šablony pořadí kontejnerů, které umožňuje uspořádat prvky daného typu v lineární uspořádání a povolit vysoká rychlost náhodného přístup k libovolného elementu. Měly by být upřednostňované kontejneru pro pořadí, když výkonu náhodný přístup premium.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Type, class Allocator = allocator<Type>>
class vector
```

### <a name="parameters"></a>Parametry

*Typ* element datový typ se neukládají v vektoru

`Allocator` Typ, který představuje uložené allocator objekt, který zapouzdřuje informace o vektoru přidělení a zrušení přidělení paměti. Tento argument je volitelný a výchozí hodnota je **allocator ***\<typ >.*

## <a name="remarks"></a>Poznámky

Vektory povolí vložení konstantní čas a odstranění na konci pořadí. Vložením či odstraněním elementy uprostřed vektor vyžaduje lineární času. Výkon [deque – třída](../standard-library/deque-class.md) kontejner je nadřízená s ohledem na vložení a odstranění na začátku a konci sekvenci. [List – třída](../standard-library/list-class.md) kontejner je nadřízená s ohledem na vložení a odstranění v libovolném umístění v rámci posloupnosti.

Opakované přidělení vektoru nastane, když členské funkce musíte zvýšit pořadí obsažené v objektu vector mimo své aktuální kapacity úložiště. Další vložení a vymazání může změnit různé adresy úložiště v sekvenci. Ve všech takových případech, iterátory nebo odkazy, které odkazují na změněné části pořadí zneplatní. Pokud žádné opakované přidělení se stane, zůstávají platná pouze iterátory a odkazy na před bodem vkládání a odstraňování.

[Vektoru\<bool > třída](../standard-library/vector-bool-class.md) je úplná specializace šablony třídy vektoru u elementů typu bool s přidělení pro základní typ používané specializace.

[Vektoru\<bool > referenční třídy](../standard-library/vector-bool-class.md#reference_class) je vnořené třídy, jejichž objekty jsou schopný poskytnout odkazy na elementy (jeden bits) v rámci vektor\<bool > objektu.

## <a name="members"></a>Členové

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[vektor](#vector)|Vytvoří vektoru určité velikosti nebo elementy konkrétní hodnotu nebo s konkrétní `allocator` nebo jako kopii některé jiné vektoru.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[allocator_type –](#allocator_type)|Typ, který reprezentuje `allocator` tříd pro objekt vektoru.|
|[const_iterator](#const_iterator)|Typ, který poskytuje iterator náhodný přístup, který může číst `const` element v vektor.|
|[const_pointer](#const_pointer)|Typ, který poskytuje odkazy `const` element v vektor.|
|[const_reference](#const_reference)|Typ, který obsahuje odkaz na `const` element uložené v vektor pro čtení a provádění `const` operace.|
|[const_reverse_iterator](#const_reverse_iterator)|Typ, který poskytuje iterator náhodný přístup, který může číst všechny `const` element v vektoru.|
|[difference_type](#difference_type)|Typ, který poskytuje rozdíl mezi adresy dva elementy v objektu vector.|
|[Iterator](#iterator)|Typ, který poskytuje iterator náhodný přístup, který může číst nebo upravovat libovolný element v vektor.|
|[Ukazatele](#pointer)|Typ, který poskytuje ukazatel na prvek v vektor.|
|[Referenční dokumentace](#reference)|Typ, který obsahuje odkaz na element uložené v vektor.|
|[reverse_iterator](#reverse_iterator)|Typ, který poskytuje iterator náhodný přístup, který může číst nebo upravovat libovolný element v invertovaných vektoru.|
|[size_type](#size_type)|Typ, který udává počet elementů v vektor.|
|[value_type](#value_type)|Typ, který představuje typ data uložená v vektor.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[přiřazení](#assign)|Vymaže vektor a zkopíruje zadaných elementů prázdný vektoru.|
|[at](#at)|Vrátí odkaz na element v zadaném umístění v vektoru.|
|[zpět](#back)|Vrátí odkaz na posledním elementem vektoru.|
|[Začátek](#begin)|Vrátí první prvek v vektoru iterator náhodný přístup.|
|[Kapacita](#capacity)|Vrátí počet prvků, které by mohly obsahovat vektoru bez přidělení další úložiště.|
|[cbegin –](#cbegin)|Vrátí první prvek v vektoru const iterator náhodným přístupem.|
|[cend –](#cend)|Vrátí const iterator náhodným přístupem této body právě přesahuje za konec vektoru.|
|[crbegin](#crbegin)|Vrátí const iterator prvním elementem v invertovaných vektoru.|
|[crend –](#crend)|Vrátí const iterator na konec odstínech vektoru.|
|[Zrušte zaškrtnutí](#clear)|Vymaže elementy vektoru.|
|[data](#data)|Vrací ukazatel na prvním elementem v vektoru.|
|[emplace –](#emplace)|Vloží element sestavený na místě do vektoru na zadané pozici.|
|[emplace_back –](#emplace_back)|Přidá element v místě na konec vektoru zkonstruovat.|
|[prázdný](#empty)|Testy, pokud kontejneru vektoru je prázdný.|
|[End](#end)|Vrátí iterator náhodný přístup, který odkazuje na konec vektoru.|
|[vymazání](#erase)|Odebere element nebo rozsah elementů u funkce vector ze zadaných pozic.|
|[Přední](#front)|Vrátí odkaz na prvním elementem v vektor.|
|[get_allocator](#get_allocator)|Vrátí objekt tak, aby `allocator` třídy používané vektor.|
|[Vložení](#insert)|Vloží elementu nebo počet elementů do vektoru na zadané pozici.|
|[max_size](#max_size)|Vrátí maximální délku vektoru.|
|[pop_back –](#pop_back)|Odstraní prvek na konec vektoru.|
|[push_back –](#push_back)|Přidáte element do konce vektoru.|
|[rbegin –](#rbegin)|Vrátí iterovat prvním elementem v invertovaných vektoru.|
|[rend –](#rend)|Vrátí iterator na konec odstínech vektoru.|
|[Rezervovat](#reserve)|Si vyhrazuje minimální délku úložiště pro objekt vektoru.|
|[Změna velikosti](#resize)|Určuje novou velikost vektor.|
|[shrink_to_fit](#shrink_to_fit)|Zahození přebytečnou kapacitou.|
|[Velikost](#size)|Vrátí počet prvků v vektoru.|
|[Swap](#swap)|Výměny elementy dvěma způsoby.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operátor&#91;&#93;](#op_at)|Vrátí odkaz na prvek vektoru na určené pozici.|
|[operátor =](#op_eq)|Nahradí elementy vektoru kopii jiným způsobem.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<vektoru >

**Namespace:** – std

## <a name="allocator_type"></a>  Vector::allocator_type

Typ, který reprezentuje allocator – třída objektu vektoru.

```cpp
typedef Allocator allocator_type;
```

### <a name="remarks"></a>Poznámky

`allocator_type` je synonymum pro parametr šablony **přidělení.**

### <a name="example"></a>Příklad

Podívejte se na příklad pro [get_allocator –](#get_allocator) pro příklad, který používá `allocator_type`.

## <a name="assign"></a>  Vector::Assign

Vymaže vektor a zkopíruje zadaných elementů prázdný vektoru.

```cpp
void assign(size_type Count, const Type& Val);
void assign(initializer_list<Type> IList);

template <class InputIterator>
void assign(InputIterator First, InputIterator Last);
```

### <a name="parameters"></a>Parametry

`First` Pozice první prvek v rozsahu elementy, které se mají zkopírovat.

`Last` Pozice první prvek mimo rozsah elementy, které se mají zkopírovat.

`Count` Počet kopií elementu vkládání do vektoru.

`Val` Hodnota elementu vkládání do vektoru.

`IList` Initializer_list obsahující elementy pro vložení.

### <a name="remarks"></a>Poznámky

Po vymazání existující elementy v objektu vector přiřadit buď vloží zadaný rozsah elementů z původní vektoru do vektoru nebo vložení kopie nového elementu zadané hodnoty do vektor.

### <a name="example"></a>Příklad

```cpp
/ vector_assign.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main()
{
    using namespace std;
    vector<int> v1, v2, v3;

    v1.push_back(10);
    v1.push_back(20);
    v1.push_back(30);
    v1.push_back(40);
    v1.push_back(50);

    cout << "v1 = ";
    for (auto& v : v1){
        cout << v << " ";
    }
    cout << endl;

    v2.assign(v1.begin(), v1.end());
    cout << "v2 = ";
    for (auto& v : v2){
        cout << v << " ";
    }
    cout << endl;

    v3.assign(7, 4);
    cout << "v3 = ";
    for (auto& v : v3){
        cout << v << " ";
    }
    cout << endl;

    v3.assign({ 5, 6, 7 });
    for (auto& v : v3){
        cout << v << " ";
    }
    cout << endl;
}

```

## <a name="at"></a>  Vector::AT

Vrátí odkaz na element v zadaném umístění v vektoru.

```cpp
reference at(size_type _Pos);

const_reference at(size_type _Pos) const;
```

### <a name="parameters"></a>Parametry

`_Pos` Dolní index nebo pozice počet elementu, který chcete odkazovat v vektoru.

### <a name="return-value"></a>Návratová hodnota

Odkaz na element dolního indexu v argumentu. Pokud `_Off` je větší než velikost vektoru, **v** vyvolá výjimku.

### <a name="remarks"></a>Poznámky

Pokud vrátí hodnotu, která **v** je přiřazena k `const_reference`, vector objekt nelze změnit. Pokud návratová hodnota **v** je přiřazena k **odkaz**, je možné upravit objekt vektoru.

### <a name="example"></a>Příklad

```cpp
// vector_at.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;

   v1.push_back( 10 );
   v1.push_back( 20 );

   const int &i = v1.at( 0 );
   int &j = v1.at( 1 );
   cout << "The first element is " << i << endl;
   cout << "The second element is " << j << endl;
}
```

```Output
The first element is 10
The second element is 20
```

## <a name="back"></a>  Vector::back

Vrátí odkaz na posledním elementem vektoru.

```cpp
reference back();

const_reference back() const;
```

### <a name="return-value"></a>Návratová hodnota

Posledním elementem vektoru. Pokud vektoru je prázdná, není definován návratovou hodnotu.

### <a name="remarks"></a>Poznámky

Pokud vrátí hodnotu, která **zpět** je přiřazena k `const_reference`, vector objekt nelze změnit. Pokud návratová hodnota **zpět** je přiřazena k **odkaz**, je možné upravit objekt vektoru.

Při kompilaci pomocí [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) definován jako 1 nebo 2, Chyba za běhu dochází, při pokusu o přístup k elementu v prázdný vektoru.  V tématu [zaškrtnutí iterátory](../standard-library/checked-iterators.md) Další informace.

### <a name="example"></a>Příklad

```cpp
// vector_back.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main() {
   using namespace std;
   vector <int> v1;

   v1.push_back( 10 );
   v1.push_back( 11 );

   int& i = v1.back( );
   const int& ii = v1.front( );

   cout << "The last integer of v1 is " << i << endl;
   i--;
   cout << "The next-to-last integer of v1 is "<< ii << endl;
}
```

## <a name="begin"></a>  Vector::begin

Vrátí první prvek v vektoru iterator náhodný přístup.

```cpp
const_iterator begin() const;


iterator begin();
```

### <a name="return-value"></a>Návratová hodnota

Iterator náhodným přístupem adresování prvním elementem v `vector` nebo do umístění, které nahradí prázdnou `vector`. Vždy byste měli porovnat hodnoty vrácené s [vector::end](#end) zajistit je platná.

### <a name="remarks"></a>Poznámky

Pokud vrátí hodnotu, která `begin` je přiřazena k [vector::const_iterator](#const_iterator), `vector` objekt nelze změnit. Pokud návratová hodnota `begin` je přiřazen [vector::iterator](#iterator), `vector` objekt můžete upravit.

### <a name="example"></a>Příklad

```cpp
// vector_begin.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main()
{
    using namespace std;
    vector<int> c1;
    vector<int>::iterator c1_Iter;
    vector<int>::const_iterator c1_cIter;

    c1.push_back(1);
    c1.push_back(2);

    cout << "The vector c1 contains elements:";
    c1_Iter = c1.begin();
    for (; c1_Iter != c1.end(); c1_Iter++)
    {
        cout << " " << *c1_Iter;
    }
    cout << endl;

    cout << "The vector c1 now contains elements:";
    c1_Iter = c1.begin();
 *c1_Iter = 20;
    for (; c1_Iter != c1.end(); c1_Iter++)
    {
        cout << " " << *c1_Iter;
    }
    cout << endl;

    // The following line would be an error because iterator is const
    // *c1_cIter = 200;
}
```

```Output
The vector c1 contains elements: 1 2
The vector c1 now contains elements: 20 2
```

## <a name="capacity"></a>  Vector::Capacity

Vrátí počet prvků, které by mohly obsahovat vektoru bez přidělení další úložiště.

```cpp
size_type capacity() const;
```

### <a name="return-value"></a>Návratová hodnota

Aktuální délka úložiště přidělené vektoru.

### <a name="remarks"></a>Poznámky

Členská funkce [změnit velikost](#resize) efektivnější, pokud je přidělen dostatek paměti pro jeho umístění. Pomocí funkce člen [rezervovat](#reserve) k určení množství paměti přidělené.

### <a name="example"></a>Příklad

```cpp
// vector_capacity.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;

   v1.push_back( 1 );
   cout << "The length of storage allocated is "
        << v1.capacity( ) << "." << endl;

   v1.push_back( 2 );
   cout << "The length of storage allocated is now "
        << v1.capacity( ) << "." << endl;
}
```

```Output
The length of storage allocated is 1.
The length of storage allocated is now 2.
```

## <a name="cbegin"></a>  Vector::cbegin

Vrátí `const` iterator, která řeší prvním elementem v rozsahu.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>Návratová hodnota

A `const` iterator náhodný přístup, který odkazuje na první prvek rozsahu nebo umístění právě přesahuje za konec prázdného rozsahu (pro prázdného rozsahu, `cbegin() == cend()`).

### <a name="remarks"></a>Poznámky

S návratovou hodnotou `cbegin`, nemůže být upravena elementů v rozsahu.

Můžete použít tuto funkci člen místě `begin()` – členská funkce zaručit, že je návratovou hodnotu `const_iterator`. Obvykle se používá ve spojení s [automaticky](../cpp/auto-cpp.md) odvození – klíčové slovo, zadejte, jak je znázorněno v následujícím příkladu. V příkladu, vezměte v úvahu `Container` upravitelná (jinou hodnotu než `const`) kontejneru libovolného typu, který podporuje `begin()` a `cbegin()`.

```cpp
auto i1 = Container.begin();
// i1 is Container<T>::iterator
auto i2 = Container.cbegin();

// i2 is Container<T>::const_iterator
```

## <a name="cend"></a>  Vector::cend

Vrátí `const` iterator, která řeší umístění bezprostředně za posledním prvkem v rozsahu.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>Návratová hodnota

A `const` iterator náhodný přístup, který odkazuje právě přesahuje za konec rozsahu.

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

## <a name="clear"></a>  Vector::clear

Vymaže elementy vektoru.

```cpp
void clear();
```

### <a name="example"></a>Příklad

```cpp
// vector_clear.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;

   v1.push_back( 10 );
   v1.push_back( 20 );
   v1.push_back( 30 );

   cout << "The size of v1 is " << v1.size( ) << endl;
   v1.clear( );
   cout << "The size of v1 after clearing is " << v1.size( ) << endl;
}
```

```Output
The size of v1 is 3
The size of v1 after clearing is 0
```

## <a name="const_iterator"></a>  Vector::const_iterator

Typ, který poskytuje iterator náhodný přístup, který může číst **const** element v vektor.

```cpp
typedef implementation-defined const_iterator;
```

### <a name="remarks"></a>Poznámky

Typ `const_iterator` nelze použít k úpravě hodnota elementu.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [zpět](#back) pro příklad, který používá `const_iterator`.

## <a name="const_pointer"></a>  Vector::const_pointer

Typ, který poskytuje odkazy **const** element v vektor.

```cpp
typedef typename Allocator::const_pointer const_pointer;
```

### <a name="remarks"></a>Poznámky

Typ `const_pointer` nelze použít k úpravě hodnota elementu.

[Iterator](#iterator) se běžně používá pro přístup vektoru elementu.

## <a name="const_reference"></a>  Vector::const_reference

Typ, který obsahuje odkaz na **const** element uložené v vektor pro čtení a provádění **const** operace.

```cpp
typedef typename Allocator::const_reference const_reference;
```

### <a name="remarks"></a>Poznámky

Typ `const_reference` nelze použít k úpravě hodnota elementu.

### <a name="example"></a>Příklad

```cpp
// vector_const_ref.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;

   v1.push_back( 10 );
   v1.push_back( 20 );

   const vector <int> v2 = v1;
   const int &i = v2.front( );
   const int &j = v2.back( );
   cout << "The first element is " << i << endl;
   cout << "The second element is " << j << endl;

   // The following line would cause an error as v2 is const
   // v2.push_back( 30 );
}
```

```Output
The first element is 10
The second element is 20
```

## <a name="const_reverse_iterator"></a>  Vector::const_reverse_iterator

Typ, který poskytuje iterator náhodný přístup, který může číst všechny **const** element v vektoru.

```cpp
typedef std::reverse_iterator<const_iterator> const_reverse_iterator;
```

### <a name="remarks"></a>Poznámky

Typ `const_reverse_iterator` nelze změnit hodnotu elementu a slouží k iteraci v rámci vektoru pozpátku.

### <a name="example"></a>Příklad

V tématu [rbegin –](#rbegin) příklad toho, jak deklarace a pomocí iterace.

## <a name="crbegin"></a>  Vector::crbegin

Vrátí const iterator prvním elementem v invertovaných vektoru.

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>Návratová hodnota

Const reverse náhodný přístup iterator adresování prvním elementem v odstínech [vektoru](../standard-library/vector-class.md) nebo řešení, co je posledním prvkem v unreversed `vector`.

### <a name="remarks"></a>Poznámky

S návratovou hodnotou `crbegin`, `vector` objekt nelze změnit.

### <a name="example"></a>Příklad

```cpp
// vector_crbegin.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   vector <int>::iterator v1_Iter;
   vector <int>::const_reverse_iterator v1_rIter;

   v1.push_back( 1 );
   v1.push_back( 2 );

   v1_Iter = v1.begin( );
   cout << "The first element of vector is "
        << *v1_Iter << "." << endl;

   v1_rIter = v1.crbegin( );
   cout << "The first element of the reversed vector is "
        << *v1_rIter << "." << endl;
}
```

```Output
The first element of vector is 1.
The first element of the reversed vector is 2.
```

## <a name="crend"></a>  Vector::crend

Vrátí const iterator, která řeší umístění úspěšné posledním prvkem v invertovaných vektoru.

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>Návratová hodnota

Const reverse iterator náhodný přístup, která řeší umístění úspěšné posledním prvkem v odstínech [vektoru](../standard-library/vector-class.md) (umístění, které měl před prvním elementem v unreversed `vector`).

### <a name="remarks"></a>Poznámky

`crend` se používá s odstínech `vector` stejně jako [vector::cend](#cend) se používá s `vector`.

S návratovou hodnotou `crend` (vhodně odečte), `vector` objekt nelze změnit.

`crend` můžete použít k testování na tom, jestli má zpětné iterator dosáhla konce jeho `vector`.

Hodnoty vrácené `crend` by neměl být vyhodnoceny odkazy.

### <a name="example"></a>Příklad

```cpp
// vector_crend.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   vector <int>::const_reverse_iterator v1_rIter;

   v1.push_back( 1 );
   v1.push_back( 2 );

   for ( v1_rIter = v1.rbegin( ) ; v1_rIter != v1.rend( ) ; v1_rIter++ )
      cout << *v1_rIter << endl;
}
```

```Output
2
1
```

## <a name="data"></a>  Vector::data

Vrací ukazatel na prvním elementem v vektoru.

```cpp
const_pointer data() const;


pointer data();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na prvním elementem v [vektoru](../standard-library/vector-class.md) nebo do umístění, které nahradí prázdnou `vector`.

### <a name="example"></a>Příklad

```cpp
// vector_data.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main()
{
    using namespace std;
    vector<int> c1;
    vector<int>::pointer c1 ptr;
    vector<int>::const_pointer c1_cPtr;

    c1.push_back(1);
    c1.push_back(2);

    cout << "The vector c1 contains elements:";
    c1_cPtr = c1.data();
    for (size_t n = c1.size(); 0 < n; --n, c1_cPtr++)
    {
        cout << " " << *c1_cPtr;
    }
    cout << endl;

    cout << "The vector c1 now contains elements:";
    c1 ptr = c1.data();
 *c1 ptr = 20;
    for (size_t n = c1.size(); 0 < n; --n, c1 ptr++)
    {
        cout << " " << *c1 ptr;
    }
    cout << endl;
}
```

```Output
The vector c1 contains elements: 1 2
The vector c1 now contains elements: 20 2
```

## <a name="difference_type"></a>  Vector::difference_type

Typ, který poskytuje rozdíl mezi dvěma iterátory, které odkazují na elementů v rámci stejné vektoru.

```cpp
typedef typename Allocator::difference_type difference_type;
```

### <a name="remarks"></a>Poznámky

A `difference_type` lze také popsat jako počet elementů mezi dvěma ukazatele, protože ukazatel na element obsahuje adresy.

[Iterator](#iterator) se běžně používá pro přístup vektoru elementu.

### <a name="example"></a>Příklad

```cpp
// vector_diff_type.cpp
// compile with: /EHsc
#include <iostream>
#include <vector>
#include <algorithm>

int main( )
{
   using namespace std;

   vector <int> c1;
   vector <int>::iterator c1_Iter, c2_Iter;

   c1.push_back( 30 );
   c1.push_back( 20 );
   c1.push_back( 30 );
   c1.push_back( 10 );
   c1.push_back( 30 );
   c1.push_back( 20 );

   c1_Iter = c1.begin( );
   c2_Iter = c1.end( );

   vector <int>::difference_type   df_typ1, df_typ2, df_typ3;

   df_typ1 = count( c1_Iter, c2_Iter, 10 );
   df_typ2 = count( c1_Iter, c2_Iter, 20 );
   df_typ3 = count( c1_Iter, c2_Iter, 30 );
   cout << "The number '10' is in c1 collection " << df_typ1 << " times.\n";
   cout << "The number '20' is in c1 collection " << df_typ2 << " times.\n";
   cout << "The number '30' is in c1 collection " << df_typ3 << " times.\n";
}
```

```Output
The number '10' is in c1 collection 1 times.
The number '20' is in c1 collection 2 times.
The number '30' is in c1 collection 3 times.
```

## <a name="emplace"></a>  Vector::emplace

Vloží element sestavený na místě do vektoru na zadané pozici.

```cpp
iterator emplace(
    const_iterator _Where,
    Type&& val);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|-|-|
|`_Where`|Pozice v [vektoru](../standard-library/vector-class.md) vloženy první prvek.|
|`val`|Hodnota elementu vkládání do `vector`.|

### <a name="return-value"></a>Návratová hodnota

Funkce vrátí hodnotu iterátor, který odkazuje na pozici, kde byl nový element vložený do `vector`.

### <a name="remarks"></a>Poznámky

Všechny operace vložení může být nákladné naleznete v tématu [vector – třída](../standard-library/vector-class.md) diskuzi o `vector` výkonu.

### <a name="example"></a>Příklad

```cpp
// vector_emplace.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   vector <int>::iterator Iter;

   v1.push_back( 10 );
   v1.push_back( 20 );
   v1.push_back( 30 );

   cout << "v1 =" ;
   for ( Iter = v1.begin( ) ; Iter != v1.end( ) ; Iter++ )
      cout << " " << *Iter;
   cout << endl;

// initialize a vector of vectors by moving v1
   vector < vector <int> > vv1;

   vv1.emplace( vv1.begin(), move( v1 ) );
   if ( vv1.size( ) != 0 && vv1[0].size( ) != 0 )
      {
      cout << "vv1[0] =";
      for (Iter = vv1[0].begin( ); Iter != vv1[0].end( ); Iter++ )
         cout << " " << *Iter;
      cout << endl;
      }
}
```

```Output
v1 = 10 20 30
vv1[0] = 10 20 30
```

## <a name="emplace_back"></a>  Vector::emplace_back

Přidá element v místě na konec vektoru zkonstruovat.

```cpp
template <class... Types>
void emplace_back(Types&&... _Args);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|`_Args`|Argumenty konstruktoru. Funkce odvodí které přetížení konstruktor k vyvolání podle zadaných argumentů.|

### <a name="example"></a>Příklad

```cpp
#include <vector>
struct obj
{
   obj(int, double) {}
};

int main()
{
   std::vector<obj> v;
   v.emplace_back(1, 3.14); // obj in created in place in the vector
}

```

## <a name="empty"></a>  Vector::Empty

Testy, pokud vektoru je prázdný.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE,** Pokud vektoru je prázdná. **false** Pokud vektoru není prázdná.

### <a name="example"></a>Příklad

```cpp
// vector_empty.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;

   v1.push_back( 10 );

   if ( v1.empty( ) )
      cout << "The vector is empty." << endl;
   else
      cout << "The vector is not empty." << endl;
}
```

```Output
The vector is not empty.
```

## <a name="end"></a>  Vector::end

Vrátí iterátor za koncem.

```cpp
iterator end();

const_iterator end() const;
```

### <a name="return-value"></a>Návratová hodnota

Iterator minulosti the-end pro vektoru. Pokud je prázdný, vektoru `vector::end() == vector::begin()`.

### <a name="remarks"></a>Poznámky

Pokud návratová hodnota **end** je přiřazený k proměnné typu `const_iterator`, vector objekt nelze změnit. Pokud návratová hodnota **end** je přiřazený k proměnné typu **iterator**, je možné upravit objekt vektoru.

### <a name="example"></a>Příklad

```cpp
// vector_end.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>
int main( )
{
   using namespace std;
   vector <int> v1;
   vector <int>::iterator v1_Iter;

   v1.push_back( 1 );
   v1.push_back( 2 );

   for ( v1_Iter = v1.begin( ) ; v1_Iter != v1.end( ) ; v1_Iter++ )
      cout << *v1_Iter << endl;
}
```

```Output
1
2
```

## <a name="erase"></a>  Vector::Erase

Odebere element nebo rozsah elementů u funkce vector ze zadaných pozic.

```cpp
iterator erase(
    const_iterator _Where);

iterator erase(
    const_iterator first,
    const_iterator last);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|-|-|
|`_Where`|Pozice elementu, který chcete odebrat z vektoru.|
|`first`|Pozice první prvek odebrat z vektoru.|
|`last`|Pozice bezprostředně za posledním elementem odebrat z vektoru.|

### <a name="return-value"></a>Návratová hodnota

Iterátor, který označuje zbývající nad rámec všechny elementy odebrán první prvek, nebo odkazy na konec vektoru, pokud neexistuje žádný takový prvek.

### <a name="example"></a>Příklad

```cpp
// vector_erase.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   vector <int>::iterator Iter;

   v1.push_back( 10 );
   v1.push_back( 20 );
   v1.push_back( 30 );
   v1.push_back( 40 );
   v1.push_back( 50 );

   cout << "v1 =" ;
   for ( Iter = v1.begin( ) ; Iter != v1.end( ) ; Iter++ )
      cout << " " << *Iter;
   cout << endl;

   v1.erase( v1.begin( ) );
   cout << "v1 =";
   for ( Iter = v1.begin( ) ; Iter != v1.end( ) ; Iter++ )
      cout << " " << *Iter;
   cout << endl;

   v1.erase( v1.begin( ) + 1, v1.begin( ) + 3 );
   cout << "v1 =";
   for ( Iter = v1.begin( ) ; Iter != v1.end( ) ; Iter++ )
      cout << " " << *Iter;
   cout << endl;
}
```

```Output
v1 = 10 20 30 40 50
v1 = 20 30 40 50
v1 = 20 50
```

## <a name="front"></a>  Vector::front

Vrátí odkaz na prvním elementem v vektor.

```cpp
reference front();

const_reference front() const;
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na prvním elementem v objektu vektoru. Pokud vektoru je prázdná, návratový není definován.

### <a name="remarks"></a>Poznámky

Pokud vrátí hodnotu, která `front` je přiřazena k `const_reference`, vector objekt nelze změnit. Pokud návratová hodnota `front` je přiřazena k **odkaz**, je možné upravit objekt vektoru.

Při kompilaci pomocí [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) definován jako 1 nebo 2, Chyba za běhu dochází, při pokusu o přístup k elementu v prázdný vektoru.  V tématu [zaškrtnutí iterátory](../standard-library/checked-iterators.md) Další informace.

### <a name="example"></a>Příklad

```cpp
// vector_front.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;

   v1.push_back( 10 );
   v1.push_back( 11 );

   int& i = v1.front( );
   const int& ii = v1.front( );

   cout << "The first integer of v1 is "<< i << endl;
   // by incrementing i, we move the the front reference to the second element
   i++;
   cout << "Now, the first integer of v1 is "<< i << endl;
}
```

## <a name="get_allocator"></a>  Vector::get_allocator

Vrátí kopii allocator objekt použitý k vytvoření vektoru.

```cpp
Allocator get_allocator() const;
```

### <a name="return-value"></a>Návratová hodnota

Allocator používané vektoru.

### <a name="remarks"></a>Poznámky

Alokátorů pro třídu vector zadejte, jak třída spravuje úložiště. Alokátorů výchozí součástí standardní knihovna C++ – třídy kontejnerů postačí pro většinu programovacích potřeb. Psaní a pomocí vlastní allocator – třída je rozšířená C++.

### <a name="example"></a>Příklad

```cpp
// vector_get_allocator.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   // The following lines declare objects that use the default allocator.
   vector<int> v1;
   vector<int, allocator<int> > v2 = vector<int, allocator<int> >(allocator<int>( )) ;

   // v3 will use the same allocator class as v1
   vector <int> v3( v1.get_allocator( ) );

   vector<int>::allocator_type xvec = v3.get_allocator( );
   // You can now call functions on the allocator class used by vec
}
```

## <a name="insert"></a>  Vector::Insert

Vloží elementu nebo počet elementů nebo rozsah elementů do vektoru na zadané pozici.

```cpp
iterator insert(
    const_iterator _Where,
    const Type& val);

iterator insert(
    const_iterator _Where,
    Type&& val);

void insert(
    const_iterator _Where,
    size_type count,
    const Type& val);

template <class InputIterator>
void insert(
    const_iterator _Where,
    InputIterator first,
    InputIterator last);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|-|-|
|`_Where`|Pozice v vektoru, kde je první prvek vložit.|
|`val`|Hodnota elementu vkládání do vektoru.|
|`count`|Počet elementů vkládání do vektoru.|
|`first`|Pozice první prvek v rozsahu elementy, které se mají zkopírovat.|
|`last`|Pozice první prvek mimo rozsah elementy, které se mají zkopírovat.|

### <a name="return-value"></a>Návratová hodnota

První dvě `insert` funkce vrátí iterátor, který odkazuje na pozici, kde byla nového elementu vložit do vektoru.

### <a name="remarks"></a>Poznámky

Podmínkou `first` a `last` nesmí být iterátory do vektoru, nebo chování není definován. Všechny operace vložení může být nákladné naleznete v tématu [vector – třída](../standard-library/vector-class.md) diskuzi o `vector` výkonu.

### <a name="example"></a>Příklad

```cpp
// vector_insert.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   vector <int>::iterator Iter;

   v1.push_back( 10 );
   v1.push_back( 20 );
   v1.push_back( 30 );

   cout << "v1 =" ;
   for ( Iter = v1.begin( ) ; Iter != v1.end( ) ; Iter++ )
      cout << " " << *Iter;
   cout << endl;

   v1.insert( v1.begin( ) + 1, 40 );
   cout << "v1 =";
   for ( Iter = v1.begin( ) ; Iter != v1.end( ) ; Iter++ )
      cout << " " << *Iter;
   cout << endl;
   v1.insert( v1.begin( ) + 2, 4, 50 );

   cout << "v1 =";
   for ( Iter = v1.begin( ) ; Iter != v1.end( ) ; Iter++ )
      cout << " " << *Iter;
   cout << endl;

   v1.insert( v1.begin( )+1, v1.begin( )+2, v1.begin( )+4 );
   cout << "v1 =";
   for (Iter = v1.begin( ); Iter != v1.end( ); Iter++ )
      cout << " " << *Iter;
   cout << endl;

// initialize a vector of vectors by moving v1
   vector < vector <int> > vv1;

   vv1.insert( vv1.begin(), move( v1 ) );
   if ( vv1.size( ) != 0 && vv1[0].size( ) != 0 )
      {
      vector < vector <int> >::iterator Iter;
      cout << "vv1[0] =";
      for (Iter = vv1[0].begin( ); Iter != vv1[0].end( ); Iter++ )
         cout << " " << *Iter;
      cout << endl;
      }
}
```

```Output
v1 = 10 20 30
v1 = 10 40 20 30
v1 = 10 40 50 50 50 50 20 30
v1 = 10 50 50 40 50 50 50 50 20 30
vv1[0] = 10 50 50 40 50 50 50 50 20 30
```

## <a name="iterator"></a>  Vector::iterator

Typ, který poskytuje iterator náhodný přístup, který může číst nebo upravovat libovolný element v vektor.

```cpp
typedef implementation-defined iterator;
```

### <a name="remarks"></a>Poznámky

Typ **iterator** lze upravit hodnotu elementu.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [začít](#begin).

## <a name="max_size"></a>  Vector::max_size

Vrátí maximální délku vektoru.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>Návratová hodnota

Maximální délka možné vektoru.

### <a name="example"></a>Příklad

```cpp
// vector_max_size.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   vector <int>::size_type i;

   i = v1.max_size( );
   cout << "The maximum possible length of the vector is " << i << "." << endl;
}
```

## <a name="op_at"></a>  Vector::Operator]

Vrátí odkaz na prvek vektoru na určené pozici.

```cpp
reference operator[](size_type Pos);

const_reference operator[](size_type Pos) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|-|-|
|`Pos`|Pozice prvku vektoru.|

### <a name="return-value"></a>Návratová hodnota

Pokud je zadaná pozice větší nebo rovna velikosti kontejneru, výsledek je nedefinován.

### <a name="remarks"></a>Poznámky

Pokud vrátí hodnotu, která `operator[]` je přiřazena k `const_reference`, vector objekt nelze změnit. Pokud vrátí hodnotu, která `operator[]` je přiřazen na odkaz, můžete upravit objekt vektoru.

Při kompilaci pomocí [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) definován jako 1 nebo 2, Chyba za běhu dochází, pokud budete chtít přístup k elementu mimo hranice vektoru.  V tématu [zaškrtnutí iterátory](../standard-library/checked-iterators.md) Další informace.

### <a name="example"></a>Příklad

```cpp
// vector_op_ref.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;

   v1.push_back( 10 );
   v1.push_back( 20 );

   int& i = v1[1];
   cout << "The second integer of v1 is " << i << endl;
}
```

## <a name="op_eq"></a>  Vector::Operator =

Nahradí elementy vektoru kopii jiným způsobem.

```cpp
vector& operator=(const vector& right);

vector& operator=(vector&& right);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|-|-|
|`right`|[Vektoru](../standard-library/vector-class.md) se zkopírují `vector`.|

### <a name="remarks"></a>Poznámky

Po vymazání v žádné stávající elementy `vector`, `operator=` buď kopíruje nebo přesouvá obsah `right` do `vector`.

### <a name="example"></a>Příklad

```cpp
// vector_operator_as.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector<int> v1, v2, v3;
   vector<int>::iterator iter;

   v1.push_back(10);
   v1.push_back(20);
   v1.push_back(30);
   v1.push_back(40);
   v1.push_back(50);

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

## <a name="pointer"></a>  Vector::Pointer

Typ, který poskytuje ukazatel na prvek v vektor.

```cpp
typedef typename Allocator::pointer pointer;
```

### <a name="remarks"></a>Poznámky

Typ **ukazatel** lze upravit hodnotu elementu.

### <a name="example"></a>Příklad

```cpp
// vector_pointer.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector<int> v;
   v.push_back( 11 );
   v.push_back( 22 );

   vector<int>::pointer ptr = &v[0];
   cout << *ptr << endl;
   ptr++;
   cout << *ptr << endl;
 *ptr = 44;
   cout << *ptr << endl;
}
```

```Output
11
22
44
```

## <a name="pop_back"></a>  Vector::pop_back

Odstraní prvek na konec vektoru.

```cpp
void pop_back();
```

### <a name="remarks"></a>Poznámky

Příklad kódu, najdete v části [vector:: push_back()](#push_back).

## <a name="push_back"></a>  Vector::push_back

Přidá prvek na konec vektoru.

```cpp
void push_back(const T& Val);


void push_back(T&& Val);
```

### <a name="parameters"></a>Parametry

`Val` Hodnota pro přiřazení k elementu přidány na konec vektoru.

### <a name="example"></a>Příklad

```cpp
// compile with: /EHsc /W4
#include <vector>
#include <iostream>

using namespace std;

template <typename T> void print_elem(const T& t) {
    cout << "(" << t << ") ";
}

template <typename T> void print_collection(const T& t) {
    cout << "  " << t.size() << " elements: ";

    for (const auto& p : t) {
        print_elem(p);
    }
    cout << endl;
}

int main()
{
    vector<int> v;
    for (int i = 0; i < 10; ++i) {
        v.push_back(10 + i);
    }

    cout << "vector data: " << endl;
    print_collection(v);

    // pop_back() until it's empty, printing the last element as we go
    while (v.begin() != v.end()) {
        cout << "v.back(): "; print_elem(v.back()); cout << endl;
        v.pop_back();
    }
}
```

## <a name="rbegin"></a>  Vector::rbegin

Vrátí iterovat prvním elementem v invertovaných vektoru.

```cpp
reverse_iterator rbegin();
const_reverse_iterator rbegin() const;
```

### <a name="return-value"></a>Návratová hodnota

Zpětné iterator náhodný přístup adresování prvním elementem v invertovaných vektoru nebo řešení, co je posledním prvkem v unreversed vektoru.

### <a name="remarks"></a>Poznámky

Pokud vrátí hodnotu, která `rbegin` je přiřazena k `const_reverse_iterator`, vector objekt nelze změnit. Pokud vrátí hodnotu, která `rbegin` je přiřazena k `reverse_iterator`, vector objekt můžete upravit.

### <a name="example"></a>Příklad

```cpp
// vector_rbegin.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   vector <int>::iterator v1_Iter;
   vector <int>::reverse_iterator v1_rIter;

   v1.push_back( 1 );
   v1.push_back( 2 );

   v1_Iter = v1.begin( );
   cout << "The first element of vector is "
        << *v1_Iter << "." << endl;

   v1_rIter = v1.rbegin( );
   cout << "The first element of the reversed vector is "
        << *v1_rIter << "." << endl;
}
```

```Output
The first element of vector is 1.
The first element of the reversed vector is 2.
```

## <a name="reference"></a>  Vector::Reference

Typ, který obsahuje odkaz na element uložené v vektor.

```cpp
typedef typename Allocator::reference reference;
```

### <a name="example"></a>Příklad

Najdete v části [v](#at) příklad použití **odkaz** ve třídě vektoru.

## <a name="rend"></a>  Vector::rend

Vrátí iterátor, který řeší umístění úspěšné posledním prvkem v invertovaných vektoru.

```cpp
const_reverse_iterator rend() const;
reverse_iterator rend();
```

### <a name="return-value"></a>Návratová hodnota

Zpětné iterator náhodný přístup, která řeší umístění úspěšné posledním prvkem v invertovaných vektoru (umístění, které měl před prvním elementem v unreversed vektoru).

### <a name="remarks"></a>Poznámky

`rend` se používá s odstínech vektoru stejně jako [end](#end) se používá s vektor.

Pokud vrátí hodnotu, která `rend` je přiřazena k `const_reverse_iterator`, pak vektoru objekt nelze změnit. Pokud vrátí hodnotu, která `rend` je přiřazena k `reverse_iterator`, pak je možné upravit objekt vektoru.

`rend` slouží k testování, aby se jestli zpětné iterator dosáhne konce své vektoru.

Hodnoty vrácené `rend` by neměl být vyhodnoceny odkazy.

### <a name="example"></a>Příklad

```cpp
// vector_rend.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   vector <int>::reverse_iterator v1_rIter;

   v1.push_back( 1 );
   v1.push_back( 2 );

   for ( v1_rIter = v1.rbegin( ) ; v1_rIter != v1.rend( ) ; v1_rIter++ )
      cout << *v1_rIter << endl;
}
```

```Output
2
1
```

## <a name="reserve"></a>  Vector::Reserve

Si vyhrazuje minimální délku úložiště pro objekt vector přidělení místa v případě potřeby.

```cpp
void reserve(size_type count);
```

### <a name="parameters"></a>Parametry

`count` Minimální délka úložiště, která bude přidělena pro vektoru.

### <a name="example"></a>Příklad

```cpp
// vector_reserve.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   //vector <int>::iterator Iter;

   v1.push_back( 1 );
   cout << "Current capacity of v1 = "
      << v1.capacity( ) << endl;
   v1.reserve( 20 );
   cout << "Current capacity of v1 = "
      << v1.capacity( ) << endl;
}
```

```Output
Current capacity of v1 = 1
Current capacity of v1 = 20
```

## <a name="resize"></a>  Vector::Resize

Určuje novou velikost vektor.

```cpp
void resize(size_type Newsize);
void resize(size_type Newsize, Type Val);
```

### <a name="parameters"></a>Parametry

`Newsize` Novou velikost vektoru.

`Val` Inicializace hodnotu nové elementy přidané do vektoru, pokud nová velikost je větší, původní velikost. Pokud hodnota je vynechán, použijte nové objekty jejich výchozí konstruktor.

### <a name="remarks"></a>Poznámky

Pokud kontejneru velikost je menší než požadovaná velikost `Newsize`, prvky jsou přidány do vektoru, dokud nedosáhne požadované velikosti. Pokud velikost kontejneru je větší než požadovaná velikost, jsou nejbližší na konec objektu kontejneru elementů odstranit, dokud kontejneru dosáhne velikosti `Newsize`. Pokud je přítomen velikost kontejneru stejná jako požadovaná velikost, nebyla provedena žádná akce.

[velikost](#size) odráží aktuální velikosti vektoru.

### <a name="example"></a>Příklad

```cpp
// vectorsizing.cpp
// compile with: /EHsc /W4
// Illustrates vector::reserve, vector::max_size,
// vector::resize, vector::resize, and vector::capacity.
//
// Functions:
//
//    vector::max_size - Returns maximum number of elements vector could
//                       hold.
//
//    vector::capacity - Returns number of elements for which memory has
//                       been allocated.
//
//    vector::size - Returns number of elements in the vector.
//
//    vector::resize - Reallocates memory for vector, preserves its
//                     contents if new size is larger than existing size.
//
//    vector::reserve - Allocates elements for vector to ensure a minimum
//                      size, preserving its contents if the new size is
//                      larger than existing size.
//
//    vector::push_back - Appends (inserts) an element to the end of a
//                        vector, allocating memory for it if necessary.
//
//////////////////////////////////////////////////////////////////////

// The debugger cannot handle symbols more than 255 characters long.
// The C++ Standard Library often creates symbols longer than that.
// The warning can be disabled:
//#pragma warning(disable:4786)

#include <iostream>
#include <vector>
#include <string>

using namespace std;

template <typename C> void print(const string& s, const C& c) {
    cout << s;

    for (const auto& e : c) {
        cout << e << " ";
    }
    cout << endl;
}

void printvstats(const vector<int>& v) {
    cout << "   the vector's size is: " << v.size() << endl;
    cout << "   the vector's capacity is: " << v.capacity() << endl;
    cout << "   the vector's maximum size is: " << v.max_size() << endl;
}

int main()
{
    // declare a vector that begins with 0 elements.
    vector<int> v;

    // Show statistics about vector.
    cout << endl << "After declaring an empty vector:" << endl;
    printvstats(v);
    print("   the vector's contents: ", v);

    // Add one element to the end of the vector.
    v.push_back(-1);
    cout << endl << "After adding an element:" << endl;
    printvstats(v);
    print("   the vector's contents: ", v);

    for (int i = 1; i < 10; ++i) {
        v.push_back(i);
    }
    cout << endl << "After adding 10 elements:" << endl;
    printvstats(v);
    print("   the vector's contents: ", v);

    v.resize(6);
    cout << endl << "After resizing to 6 elements without an initialization value:" << endl;
    printvstats(v);
    print("   the vector's contents: ", v);

    v.resize(9, 999);
    cout << endl << "After resizing to 9 elements with an initialization value of 999:" << endl;
    printvstats(v);
    print("   the vector's contents: ", v);

    v.resize(12);
    cout << endl << "After resizing to 12 elements without an initialization value:" << endl;
    printvstats(v);
    print("   the vector's contents: ", v);

    // Ensure there's room for at least 1000 elements.
    v.reserve(1000);
    cout << endl << "After vector::reserve(1000):" << endl;
    printvstats(v);

    // Ensure there's room for at least 2000 elements.
    v.resize(2000);
    cout << endl << "After vector::resize(2000):" << endl;
    printvstats(v);
}
```

## <a name="reverse_iterator"></a>  Vector::reverse_iterator

Typ, který poskytuje iterator náhodný přístup, který může číst nebo upravovat libovolný element v invertovaných vektoru.

```cpp
typedef std::reverse_iterator<iterator> reverse_iterator;
```

### <a name="remarks"></a>Poznámky

Typ `reverse_iterator` se používá k iteraci v rámci vektoru pozpátku.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [rbegin –](#rbegin).

## <a name="shrink_to_fit"></a>  Vector::shrink_to_fit

Zahození přebytečnou kapacitou.

```cpp
void shrink_to_fit();
```

### <a name="example"></a>Příklad

```cpp
// vector_shrink_to_fit.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   //vector <int>::iterator Iter;

   v1.push_back( 1 );
   cout << "Current capacity of v1 = "
      << v1.capacity( ) << endl;
   v1.reserve( 20 );
   cout << "Current capacity of v1 = "
      << v1.capacity( ) << endl;
   v1.shrink_to_fit();
   cout << "Current capacity of v1 = "
      << v1.capacity( ) << endl;
}
```

```Output
Current capacity of v1 = 1
Current capacity of v1 = 20
Current capacity of v1 = 1
```

## <a name="size"></a>  Vector::size

Vrátí počet prvků v vektoru.

```cpp
size_type size() const;
```

### <a name="return-value"></a>Návratová hodnota

Aktuální délka vektoru.

### <a name="example"></a>Příklad

```cpp
// vector_size.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   vector <int>::size_type i;

   v1.push_back( 1 );
   i = v1.size( );
   cout << "Vector length is " << i << "." << endl;

   v1.push_back( 2 );
   i = v1.size( );
   cout << "Vector length is now " << i << "." << endl;
}
```

```Output
Vector length is 1.
Vector length is now 2.
```

## <a name="size_type"></a>  Vector::size_type

Typ, který udává počet elementů v vektor.

```cpp
typedef typename Allocator::size_type size_type;
```

### <a name="example"></a>Příklad

Podívejte se na příklad pro [kapacity](#capacity).

## <a name="swap"></a>  Vector::swap

Výměny elementy dvěma způsoby.

```cpp
void swap(
    vector<Type, Allocator>& right);

friend void swap(
    vector<Type, Allocator>& left,
    vector<Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

`right` Vektor poskytování elementy pro si místo nebo vektoru, jehož elementy jsou k výměně s těmi, která vektoru `left`.

`left` Vektor, jehož elementy jsou k výměně s těmi, která vektoru `right`.

### <a name="example"></a>Příklad

```cpp
// vector_swap.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1, v2;

   v1.push_back( 1 );
   v1.push_back( 2 );
   v1.push_back( 3 );

   v2.push_back( 10 );
   v2.push_back( 20 );

   cout << "The number of elements in v1 = " << v1.size( ) << endl;
   cout << "The number of elements in v2 = " << v2.size( ) << endl;
   cout << endl;

   v1.swap( v2 );

   cout << "The number of elements in v1 = " << v1.size( ) << endl;
   cout << "The number of elements in v2 = " << v2.size( ) << endl;
}
```

```Output
The number of elements in v1 = 3
The number of elements in v2 = 2

The number of elements in v1 = 2
The number of elements in v2 = 3
```

## <a name="value_type"></a>  Vector::value_type

Typ, který představuje typ data uložená v vektor.

```cpp
typedef typename Allocator::value_type value_type;
```

### <a name="remarks"></a>Poznámky

`value_type` je synonymum pro parametr šablony **typu**.

### <a name="example"></a>Příklad

```cpp
// vector_value_type.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector<int>::value_type AnInt;
   AnInt = 44;
   cout << AnInt << endl;
}
```

```Output
44
```

## <a name="vector"></a>  Vector::Vector

Sestaví vektor určité velikosti, s elementy s konkrétní hodnotou, s konkrétním alokátorem nebo jako kopii celého existujícího vektoru nebo jeho části.

```cpp
vector();
explicit vector(const Allocator& Al);
explicit vector(size_type Count);
vector(size_type Count, const Type& Val);
vector(size_type Count, const Type& Val, const Allocator& Al);

vector(const vector& Right);
vector(vector&& Right);
vector(initializer_list<Type> IList, const _Allocator& Al);

template <class InputIterator>
vector(InputIterator First, InputIterator Last);
template <class InputIterator>
vector(InputIterator First, InputIterator Last, const Allocator& Al);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|-|-|
|`Al`|Třída alokátoru, která se má použít s tímto objektem. [get_allocator –](#get_allocator) vrátí allocator – třída objektu.|
|`Count`|Počet prvků ve vytvořeném vektoru.|
|`Val`|Hodnota prvků v sestaveném vektoru.|
|`Right`|Vektor, jehož bude vytvořený vektor kopií.|
|`First`|Pozice první prvek v rozsahu elementy, které se mají zkopírovat.|
|`Last`|Pozice první prvek mimo rozsah elementy, které se mají zkopírovat.|
|`IList`|Objekt initializer_list obsahující prvky ke zkopírování.|

### <a name="remarks"></a>Poznámky

Všechny konstruktory uložit objekt allocator ( `Al`) a inicializace vektoru.

První dva konstruktory určují prázdný počáteční vektor. Druhý explicitně určuje typ allocator ( `Al`) má být použit.

Třetí konstruktor určuje opakování určeného čísla ( `Count`) elementů výchozí hodnota pro třídu `Type`.

Konstruktory čtvrté a páté zadejte opakování ( `Count`) elementy hodnoty `Val`.

Šestý konstruktor určuje kopii vektoru `Right`.

Sedmý konstruktor přesune vektor `Right`.

Osmý konstruktor používá k určení prvků objekt initializer_list.

Konstruktory deváté a desetinu zkopírujte rozsahu [ `First`, `Last`) vektoru.

### <a name="example"></a>Příklad

```cpp
// vector_ctor.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main()
{
    using namespace std;
    vector <int>::iterator v1_Iter, v2_Iter, v3_Iter, v4_Iter, v5_Iter, v6_Iter;

    // Create an empty vector v0
    vector <int> v0;

    // Create a vector v1 with 3 elements of default value 0
    vector <int> v1(3);

    // Create a vector v2 with 5 elements of value 2
    vector <int> v2(5, 2);

    // Create a vector v3 with 3 elements of value 1 and with the allocator
    // of vector v2
    vector <int> v3(3, 1, v2.get_allocator());

    // Create a copy, vector v4, of vector v2
    vector <int> v4(v2);

    // Create a new temporary vector for demonstrating copying ranges
    vector <int> v5(5);
    for (auto i : v5) {
        v5[i] = i;
    }

    // Create a vector v6 by copying the range v5[ first,  last)
    vector <int> v6(v5.begin() + 1, v5.begin() + 3);

    cout << "v1 =";
    for (auto& v : v1){
        cout << " " << v;
    }
    cout << endl;

    cout << "v2 =";
    for (auto& v : v2){
        cout << " " << v;
    }
    cout << endl;

    cout << "v3 =";
    for (auto& v : v3){
        cout << " " << v;
    }
    cout << endl;
    cout << "v4 =";
    for (auto& v : v4){
        cout << " " << v;
    }
    cout << endl;

    cout << "v5 =";
    for (auto& v : v5){
        cout << " " << v;
    }
    cout << endl;

    cout << "v6 =";
    for (auto& v : v6){
        cout << " " << v;
    }
    cout << endl;

    // Move vector v2 to vector v7
    vector <int> v7(move(v2));
    vector <int>::iterator v7_Iter;

    cout << "v7 =";
    for (auto& v : v7){
        cout << " " << v;
    }
    cout << endl;

    vector<int> v8{ { 1, 2, 3, 4 } };
    for (auto& v : v8){
        cout << " " << v ;
    }
    cout << endl;
}

```

```Output
v1 = 0 0 0v2 = 2 2 2 2 2v3 = 1 1 1v4 = 2 2 2 2 2v5 = 0 1 2 3 4v6 = 1 2v7 = 2 2 2 2 21 2 3 4
```

## <a name="see-also"></a>Viz také

[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)<br/>
