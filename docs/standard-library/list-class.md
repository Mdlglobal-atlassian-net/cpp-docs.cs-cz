---
title: list – třída
ms.date: 11/04/2016
f1_keywords:
- list/std::list
- list/std::list::allocator_type
- list/std::list::const_iterator
- list/std::list::const_pointer
- list/std::list::const_reference
- list/std::list::const_reverse_iterator
- list/std::list::difference_type
- list/std::list::iterator
- list/std::list::pointer
- list/std::list::reference
- list/std::list::reverse_iterator
- list/std::list::size_type
- list/std::list::value_type
- list/std::list::assign
- list/std::list::back
- list/std::list::begin
- list/std::list::cbegin
- list/std::list::cend
- list/std::list::clear
- list/std::list::crbegin
- list/std::list::crend
- list/std::list::emplace
- list/std::list::emplace_back
- list/std::list::emplace_front
- list/std::list::empty
- list/std::list::end
- list/std::list::erase
- list/std::list::front
- list/std::list::get_allocator
- list/std::list::insert
- list/std::list::max_size
- list/std::list::merge
- list/std::list::pop_back
- list/std::list::pop_front
- list/std::list::push_back
- list/std::list::push_front
- list/std::list::rbegin
- list/std::list::remove
- list/std::list::remove_if
- list/std::list::rend
- list/std::list::resize
- list/std::list::reverse
- list/std::list::size
- list/std::list::sort
- list/std::list::splice
- list/std::list::swap
- list/std::list::unique
helpviewer_keywords:
- std::list [C++]
- std::list [C++], allocator_type
- std::list [C++], const_iterator
- std::list [C++], const_pointer
- std::list [C++], const_reference
- std::list [C++], const_reverse_iterator
- std::list [C++], difference_type
- std::list [C++], iterator
- std::list [C++], pointer
- std::list [C++], reference
- std::list [C++], reverse_iterator
- std::list [C++], size_type
- std::list [C++], value_type
- std::list [C++], assign
- std::list [C++], back
- std::list [C++], begin
- std::list [C++], cbegin
- std::list [C++], cend
- std::list [C++], clear
- std::list [C++], crbegin
- std::list [C++], crend
- std::list [C++], emplace
- std::list [C++], emplace_back
- std::list [C++], emplace_front
- std::list [C++], empty
- std::list [C++], end
- std::list [C++], erase
- std::list [C++], front
- std::list [C++], get_allocator
- std::list [C++], insert
- std::list [C++], max_size
- std::list [C++], merge
- std::list [C++], pop_back
- std::list [C++], pop_front
- std::list [C++], push_back
- std::list [C++], push_front
- std::list [C++], rbegin
- std::list [C++], remove
- std::list [C++], remove_if
- std::list [C++], rend
- std::list [C++], resize
- std::list [C++], reverse
- std::list [C++], size
- std::list [C++], sort
- std::list [C++], splice
- std::list [C++], swap
- std::list [C++], unique
ms.assetid: d3707f4a-10fd-444f-b856-f9ca2077c1cd
ms.openlocfilehash: d990efb7d4c363b8d8e38f42f9edac7eea0a3882
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62413213"
---
# <a name="list-class"></a>list – třída

Třídy seznamu standardní knihovny C++ je třída šablony kontejnery sekvence, které zachovávají prvky ve lineární uspořádání a umožní efektivní vložení a odstranění v libovolném umístění v rámci pořadí. Sekvence se ukládá jako obousměrný propojený seznam prvků, každá obsahuje člen typu *typ*.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Type, class Allocator= allocator<Type>>
class list
```

### <a name="parameters"></a>Parametry

*Typ*<br/>
Typ dat prvku, který bude uložen do seznamu.

*Allocator –*<br/>
Typ představující uložený objekt alokátoru, který zapouzdřuje informace o přidělování a navracení zpět paměti v seznamu. Tento argument je nepovinný a výchozí hodnota je **alokátoru**\<*typ*>.

## <a name="remarks"></a>Poznámky

Volba typu kontejneru by měla obecně vycházet z typu vyhledávání a vkládání vyžadovaného aplikací. Vektory by měl být upřednostňované kontejner pro správu sekvenci, když je náhodný přístup k libovolnému prvku v na úrovni premium a vložení nebo odstranění prvků jsou pouze požadované na konci sekvence. Výkon kontejneru deque – třída je vynikající, když je potřeba náhodný přístup a vložení a odstranění na začátku a konci sekvence došli na úrovni premium.

Členské funkce seznam [sloučení](#merge), [reverzní](#reverse), [jedinečný](#unique), [odebrat](#remove), a [remove_if –](#remove_if) byly optimalizované pro operace s objekty seznam a nabídka výkonné alternativou k jejich obecné protějšky.

Seznam realokace nastane, pokud členskou funkci musíte vložit nebo mazání prvků seznamu. V takových případech pouze u iterátorů nebo odkazy, které odkazují na vymaže částí řízené sekvence se zneplatní.

Zahrnout hlavičku standardní knihovny C++ standard \<seznamu > k definování [kontejneru](../standard-library/stl-containers.md) seznam šablon třídy a několik podpůrných šablon.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[list](#list)|Sestaví seznam určité velikosti nebo s prvky určité hodnoty nebo s konkrétní `allocator` nebo jako kopii jiného seznamu.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[allocator_type](#allocator_type)|Typ, který představuje `allocator` třídy pro objekt seznamu.|
|[const_iterator](#const_iterator)|Typ, který poskytuje obousměrný iterátor, který může číst **const** prvek v seznamu.|
|[const_pointer](#const_pointer)|Typ, který poskytuje ukazatel **const** prvek v seznamu.|
|[const_reference](#const_reference)|Typ, který poskytuje odkaz na **const** prvek uložený v seznamu pro čtení a provádění **const** operace.|
|[const_reverse_iterator](#const_reverse_iterator)|Typ, který poskytuje obousměrný iterátor, který může přečíst jakýkoli **const** prvek v seznamu.|
|[difference_type](#difference_type)|Typ, který obsahuje rozdíl mezi dvěma iterátory, které odkazují na prvky v rámci stejného seznamu.|
|[iterator](#iterator)|Typ, který poskytuje obousměrný iterátor, který může číst nebo upravovat libovolný prvek v seznamu.|
|[pointer](#pointer)|Typ, který poskytuje ukazatel na prvek v seznamu.|
|[Referenční dokumentace](#reference)|Typ, který poskytuje odkaz na **const** prvek uložený v seznamu pro čtení a provádění **const** operace.|
|[reverse_iterator](#reverse_iterator)|Typ, který poskytuje obousměrný iterátor, který může číst nebo upravovat prvek v obráceném seznamu.|
|[size_type](#size_type)|Typ, který vrátí počet prvků v seznamu.|
|[value_type](#value_type)|Typ, který představuje datový typ uložený v seznamu.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[assign](#assign)|Odstraní prvky ze seznamu a zkopíruje novou sadu prvků do cílového seznamu.|
|[Zpět](#back)|Vrátí odkaz na poslední prvek seznamu.|
|[začít](#begin)|Vrátí iterátor adresující první prvek v seznamu.|
|[cbegin](#cbegin)|Vrátí konstantní iterátor adresující první prvek v seznamu.|
|[cend](#cend)|Vrátí konstantní iterátor adresující umístění následující po posledním prvku v seznamu.|
|[clear](#clear)|Vymaže všechny prvky seznamu.|
|[crbegin](#crbegin)|Vrátí konstantní iterátor adresující první prvek v obráceném seznamu.|
|[crend](#crend)|Vrátí konstantní iterátor adresující umístění následující po posledním prvku v obráceném seznamu.|
|[emplace](#emplace)|Vloží vytvořený prvek na místo do seznamu na zadané pozici.|
|[emplace_back](#emplace_back)|Přidá prvek vytvořený v místě na konec seznamu.|
|[emplace_front](#emplace_front)|Přidá prvek vytvořený v místě na začátek seznamu.|
|[prázdný](#empty)|Testuje, zda je seznam prázdný.|
|[ukončení](#end)|Vrátí iterátor adresující umístění následující po posledním prvku v seznamu.|
|[vymazání](#erase)|Odebere prvek nebo rozsah prvků v seznamu od zadané pozice.|
|[Přední](#front)|Vrátí odkaz na první prvek v seznamu.|
|[get_allocator](#get_allocator)|Vrátí kopii objektu `allocator` objekt použitý k vytvoření seznamu.|
|[Vložit](#insert)|Vloží prvek nebo prvky, nebo rozsah prvků do seznamu na zadané pozici.|
|[max_size](#max_size)|Vrátí maximální délku seznamu.|
|[sloučení](#merge)|Odebere prvky ze seznamu argumentů, vloží do cílového seznamu a řadí nové, kombinované sadu elementů ve vzestupném pořadí nebo v jiných určeném pořadí.|
|[pop_back](#pop_back)|Odstraní prvek na konec seznamu.|
|[pop_front](#pop_front)|Odstraní prvek na začátku seznamu.|
|[push_back](#push_back)|Přidá prvek na konec seznamu.|
|[push_front](#push_front)|Přidá prvek na začátku seznamu.|
|[rbegin](#rbegin)|Vrátí iterátor adresující první prvek v obráceném seznamu.|
|[remove](#remove)|Odstraní prvky v seznamu, které odpovídají zadané hodnotě.|
|[remove_if](#remove_if)|Odstraní prvky ze seznamu, pro kterou zadaný predikát uspokojen.|
|[rend –](#rend)|Vrátí iterátor adresující umístění následující po posledním prvku v obráceném seznamu.|
|[resize](#resize)|Určuje novou velikost seznamu.|
|[reverzní](#reverse)|Obrátí pořadí, ve kterém se prvky objevují v seznamu.|
|[Velikost](#size)|Vrátí počet prvků v seznamu.|
|[Řazení](#sort)|Uspořádá prvky seznamu vzestupně nebo s ohledem na některé jiné pořadí vztah.|
|[splice](#splice)|Odstraní prvky ze seznamu argumentů a vloží je do cílového seznamu.|
|[swap](#swap)|Vymění prvky dvou seznamů.|
|[unique](#unique)|Odebere sousedících duplicitních prvků nebo sousedící prvky, které splňují některé binárním predikátem ze seznamu.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[list::Operator =](#op_eq)|Nahradí prvky seznamu kopii jiného seznamu.|

## <a name="requirements"></a>Požadavky

**Hlavička**: \<seznamu >

## <a name="allocator_type"></a>  list::allocator_type

Typ, který představuje třídu alokátoru pro objekt seznamu.

```cpp
typedef Allocator allocator_type;
```

### <a name="remarks"></a>Poznámky

`allocator_type` je synonymum pro parametr šablony *alokátoru*.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [get_allocator](#get_allocator).

## <a name="assign"></a>  list::Assign

Odstraní prvky ze seznamu a zkopíruje novou sadu prvků do cílového seznamu.

```cpp
void assign(
    size_type Count,
    const Type& Val);

void assign
    initializer_list<Type> IList);

template <class InputIterator>
void assign(
    InputIterator First,
    InputIterator Last);
```

### <a name="parameters"></a>Parametry

*první*<br/>
Pozice prvního prvku v rozsahu prvků, které se mají zkopírovat ze seznamu argumentů.

*poslední*<br/>
Pozice prvního prvku za rozsahem prvků, které se mají zkopírovat ze seznamu argumentů.

*Počet*<br/>
Počet kopií prvku vloženého do seznamu.

*Val*<br/>
Hodnota prvku vloženého do seznamu.

*IList*<br/>
Objekt initializer_list obsahující prvky, které mají být vloženy.

### <a name="remarks"></a>Poznámky

Po odstranění jakýchkoli prvků v cílovém seznamu přiřaďte buď vložení zadaného rozsahu prvků z původního seznamu nebo z některého jiného seznamu do cílového seznamu, nebo vložení kopií nového prvku zadané hodnoty do cílového seznamu.

### <a name="example"></a>Příklad

```cpp
// list_assign.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main()
{
    using namespace std;
    list<int> c1, c2;
    list<int>::const_iterator cIter;

    c1.push_back(10);
    c1.push_back(20);
    c1.push_back(30);
    c2.push_back(40);
    c2.push_back(50);
    c2.push_back(60);

    cout << "c1 =";
    for (auto c : c1)
        cout << " " << c;
    cout << endl;

    c1.assign(++c2.begin(), c2.end());
    cout << "c1 =";
    for (auto c : c1)
        cout << " " << c;
    cout << endl;

    c1.assign(7, 4);
    cout << "c1 =";
    for (auto c : c1)
        cout << " " << c;
    cout << endl;

    c1.assign({ 10, 20, 30, 40 });
    cout << "c1 =";
    for (auto c : c1)
        cout << " " << c;
    cout << endl;
}
```

```Output
c1 = 10 20 30c1 = 50 60c1 = 4 4 4 4 4 4 4c1 = 10 20 30 40
```

## <a name="back"></a>  list::back

Vrátí odkaz na poslední prvek seznamu.

```cpp
reference back();

const_reference back() const;
```

### <a name="return-value"></a>Návratová hodnota

Poslední prvek v seznamu. Pokud je seznam prázdný, návratová hodnota není definována.

### <a name="remarks"></a>Poznámky

Pokud návratová hodnota `back` je přiřazen `const_reference`, objekt seznamu nelze upravit. Pokud návratová hodnota `back` je přiřazen `reference`, objekt seznamu lze upravit.

Při kompilaci pomocí [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) definováno jako 1 nebo 2, dojde k chybě při pokusu o přístup k prvku v prázdném seznamu.  Zobrazit [Checked Iterators](../standard-library/checked-iterators.md) Další informace.

### <a name="example"></a>Příklad

```cpp
// list_back.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;

   c1.push_back( 10 );
   c1.push_back( 11 );

   int& i = c1.back( );
   const int& ii = c1.front( );

   cout << "The last integer of c1 is " << i << endl;
   i--;
   cout << "The next-to-last integer of c1 is " << ii << endl;
}
```

```Output
The last integer of c1 is 11
The next-to-last integer of c1 is 10
```

## <a name="begin"></a>  list::begin

Vrátí iterátor adresující první prvek v seznamu.

```cpp
const_iterator begin() const;

iterator begin();
```

### <a name="return-value"></a>Návratová hodnota

Obousměrný iterátor adresující první prvek v seznamu nebo na umístění následující po prázdný seznam.

### <a name="remarks"></a>Poznámky

Pokud návratová hodnota `begin` je přiřazen `const_iterator`, prvků v objektu seznamu nelze upravit. Pokud návratová hodnota `begin` je přiřazena `iterator`, prvků v objektu seznamu lze upravit.

### <a name="example"></a>Příklad

```cpp
// list_begin.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;
   list <int>::iterator c1_Iter;
   list <int>::const_iterator c1_cIter;

   c1.push_back( 1 );
   c1.push_back( 2 );

   c1_Iter = c1.begin( );
   cout << "The first element of c1 is " << *c1_Iter << endl;

*c1_Iter = 20;
   c1_Iter = c1.begin( );
   cout << "The first element of c1 is now " << *c1_Iter << endl;

   // The following line would be an error because iterator is const
   // *c1_cIter = 200;
}
```

```Output
The first element of c1 is 1
The first element of c1 is now 20
```

## <a name="cbegin"></a>  list::cbegin

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

## <a name="cend"></a>  list::cend

Vrátí `const` iterátor adresující umístění hned za posledním prvkem v rozsahu.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>Návratová hodnota

A `const` iterátor s obousměrným přístupem, který ukazuje přesně za konec rozsahu.

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

## <a name="clear"></a>  list::clear

Vymaže všechny prvky seznamu.

```cpp
void clear();
```

### <a name="example"></a>Příklad

```cpp
// list_clear.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main() {
   using namespace std;
   list <int> c1;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );

   cout << "The size of the list is initially " << c1.size( ) << endl;
   c1.clear( );
   cout << "The size of list after clearing is " << c1.size( ) << endl;
}
```

```Output
The size of the list is initially 3
The size of list after clearing is 0
```

## <a name="const_iterator"></a>  list::const_iterator

Typ, který poskytuje obousměrný iterátor, který může číst **const** prvek v seznamu.

```cpp
typedef implementation-defined const_iterator;
```

### <a name="remarks"></a>Poznámky

Typ `const_iterator` nelze použít ke změně hodnoty prvku.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [zpět](#back).

## <a name="const_pointer"></a>  list::const_pointer

Poskytuje ukazatel **const** prvek v seznamu.

```cpp
typedef typename Allocator::const_pointer const_pointer;
```

### <a name="remarks"></a>Poznámky

Typ `const_pointer` nelze použít ke změně hodnoty prvku.

Ve většině případů [iterátoru](#iterator) by měla sloužit pro přístup k prvkům v seznamu objektů.

## <a name="const_reference"></a>  list::const_reference

Typ, který poskytuje odkaz na **const** prvek uložený v seznamu pro čtení a provádění **const** operace.

```cpp
typedef typename Allocator::const_reference const_reference;
```

### <a name="remarks"></a>Poznámky

Typ `const_reference` nelze použít ke změně hodnoty prvku.

### <a name="example"></a>Příklad

```cpp
// list_const_ref.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;

   c1.push_back( 10 );
   c1.push_back( 20 );

   const list <int> c2 = c1;
   const int &i = c2.front( );
   const int &j = c2.back( );
   cout << "The first element is " << i << endl;
   cout << "The second element is " << j << endl;

   // The following line would cause an error because c2 is const
   // c2.push_back( 30 );
}
```

```Output
The first element is 10
The second element is 20
```

## <a name="const_reverse_iterator"></a>  list::const_reverse_iterator

Typ, který poskytuje obousměrný iterátor, který může přečíst jakýkoli **const** prvek v seznamu.

```cpp
typedef std::reverse_iterator<const_iterator> const_reverse_iterator;
```

### <a name="remarks"></a>Poznámky

Typ `const_reverse_iterator` hodnotu prvku nelze změnit a slouží k iteraci v rámci seznamu pozpátku.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [rbegin –](#rbegin).

## <a name="crbegin"></a>  list::crbegin

Vrátí konstantní iterátor adresující první prvek v obráceném seznamu.

```cpp
const_reverse_iterator rbegin() const;
```

### <a name="return-value"></a>Návratová hodnota

Konstantní reverzní obousměrný iterátor adresující první prvek v obráceném seznamu (nebo adresující, co bylo posledním prvkem v neobráceném `list`).

### <a name="remarks"></a>Poznámky

`crbegin` se používá s obráceným seznamem stejně jako [list::begin](#begin) se používá s `list`.

S návratovou hodnotou `crbegin`, objekt seznamu nelze upravit. [list::rbegin](#rbegin) lze použít k iteraci seznamem zpět.

### <a name="example"></a>Příklad

```cpp
// list_crbegin.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;
   list <int>::const_reverse_iterator c1_crIter;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );
   c1_crIter = c1.crbegin( );
   cout << "The last element in the list is " << *c1_crIter << "." << endl;
}
```

```Output
The last element in the list is 30.
```

## <a name="crend"></a>  list::crend

Vrátí konstantní iterátor adresující umístění následující po posledním prvku v obráceném seznamu.

```cpp
const_reverse_iterator rend() const;
```

### <a name="return-value"></a>Návratová hodnota

Konstantní reverzní obousměrný iterátor adresující umístění následující po posledním prvku v obráceném objektu [seznamu](../standard-library/list-class.md) (umístění, ke které došlo před první prvek v neobráceném `list`).

### <a name="remarks"></a>Poznámky

`crend` se používá s obráceným seznamem stejně jako [list::end](#end) se používá s `list`.

S návratovou hodnotou `crend`, `list` objekt nelze změnit.

`crend` můžete použít k testování na tom, zda zpětný iterátor dosáhl konce jeho `list`.

Hodnota vrácená `crend` by neměla být dereferencována.

### <a name="example"></a>Příklad

```cpp
// list_crend.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;
   list <int>::const_reverse_iterator c1_crIter;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );

   c1_crIter = c1.crend( );
   c1_crIter --;  // Decrementing a reverse iterator moves it forward in
                 // the list (to point to the first element here)
   cout << "The first element in the list is: " << *c1_crIter << endl;
}
```

```Output
The first element in the list is: 10
```

## <a name="difference_type"></a>  list::difference_type

Celočíselný typ se znaménkem, který slouží k vyjádření počtu prvků v seznamu v rozsahu mezi prvky, na které odkazují iterátory.

```cpp
typedef typename Allocator::difference_type difference_type;
```

### <a name="remarks"></a>Poznámky

`difference_type` Typ dochází při přičítání nebo zvýšení prostřednictvím iterátorů kontejneru. `difference_type` Se obvykle používá k vyjádření počtu prvků v rozsahu [ `first`, `last`) mezi iterátory `first` a `last`, obsahuje element, na které odkazuje `first` a rozsah prvků do , ale bez zahrnutí elementu, na které odkazuje `last`.

Všimněte si, že i když `difference_type` je k dispozici pro všechny iterátory, které splňují požadavky na vstupní iterátor, který obsahuje třídou obousměrných iterátorů, které jsou podporované reverzibilního kontejnery jako sadu, odčítání mezi iterátory pouze podporuje iterátory s náhodným přístupem poskytované kontejner náhodného přístupu, jako například [vector – třída](../standard-library/vector-class.md).

### <a name="example"></a>Příklad

```cpp
// list_diff_type.cpp
// compile with: /EHsc
#include <iostream>
#include <list>
#include <algorithm>

int main( )
{
   using namespace std;

   list <int> c1;
   list <int>::iterator   c1_Iter, c2_Iter;

   c1.push_back( 30 );
   c1.push_back( 20 );
   c1.push_back( 30 );
   c1.push_back( 10 );
   c1.push_back( 30 );
   c1.push_back( 20 );

   c1_Iter = c1.begin( );
   c2_Iter = c1.end( );

    list <int>::difference_type df_typ1, df_typ2, df_typ3;

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

## <a name="emplace"></a>  list::emplace

Vloží vytvořený prvek na místo do seznamu na zadané pozici.

```cpp
void emplace(iterator Where, Type&& val);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|-|-|
|*kde*|Pozice v cílovém [seznamu](../standard-library/list-class.md) vloženy první prvek.|
|*Val*|Prvek přidán na konec objektu `list`.|

### <a name="remarks"></a>Poznámky

Pokud je vyvolána výjimka, `list` je beze změny doleva a je znovu vyvolána výjimka.

### <a name="example"></a>Příklad

```cpp
// list_emplace.cpp
// compile with: /EHsc
#include <list>
#include <iostream>
#include <string>

int main( )
{
   using namespace std;
   list <string> c2;
   string str("a");

   c2.emplace(c2.begin(), move( str ) );
   cout << "Moved first element: " << c2.back( ) << endl;
}
```

```Output
Moved first element: a
```

## <a name="emplace_back"></a>  list::emplace_back

Přidá prvek vytvořený v místě na konec seznamu.

```cpp
void emplace_back(Type&& val);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|-|-|
|*Val*|Prvek přidán na konec objektu [seznamu](../standard-library/list-class.md).|

### <a name="remarks"></a>Poznámky

Pokud je vyvolána výjimka, `list` je beze změny doleva a je znovu vyvolána výjimka.

### <a name="example"></a>Příklad

```cpp
// list_emplace_back.cpp
// compile with: /EHsc
#include <list>
#include <iostream>
#include <string>

int main( )
{
   using namespace std;
   list <string> c2;
   string str("a");

   c2.emplace_back( move( str ) );
   cout << "Moved first element: " << c2.back( ) << endl;
}
```

```Output
Moved first element: a
```

## <a name="emplace_front"></a>  list::emplace_front

Přidá prvek vytvořený v místě na začátek seznamu.

```cpp
void emplace_front(Type&& val);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|-|-|
|*Val*|Element přidá na začátek [seznamu](../standard-library/list-class.md).|

### <a name="remarks"></a>Poznámky

Pokud je vyvolána výjimka, `list` je beze změny doleva a je znovu vyvolána výjimka.

### <a name="example"></a>Příklad

```cpp
// list_emplace_front.cpp
// compile with: /EHsc
#include <list>
#include <iostream>
#include <string>

int main( )
{
   using namespace std;
   list <string> c2;
   string str("a");

   c2.emplace_front( move( str ) );
   cout << "Moved first element: " << c2.front( ) << endl;
}
```

```Output
Moved first element: a
```

## <a name="empty"></a>  list::Empty

Testuje, zda je seznam prázdný.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud je seznam prázdný; **false** Pokud seznam není prázdný.

### <a name="example"></a>Příklad

```cpp
// list_empty.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;

   c1.push_back( 10 );
   if ( c1.empty( ) )
      cout << "The list is empty." << endl;
   else
      cout << "The list is not empty." << endl;
}
```

```Output
The list is not empty.
```

## <a name="end"></a>  list::end

Vrátí iterátor adresující umístění následující po posledním prvku v seznamu.

```cpp
const_iterator end() const;
iterator end();
```

### <a name="return-value"></a>Návratová hodnota

Obousměrný iterátor adresující umístění následující po posledním prvku v seznamu. Pokud je seznam prázdný, pak `list::end == list::begin`.

### <a name="remarks"></a>Poznámky

`end` slouží k otestování, zda iterátor dosáhl konce seznamu.

### <a name="example"></a>Příklad

```cpp
// list_end.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;
   list <int>::iterator c1_Iter;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );

   c1_Iter = c1.end( );
   c1_Iter--;
   cout << "The last integer of c1 is " << *c1_Iter << endl;

   c1_Iter--;
*c1_Iter = 400;
   cout << "The new next-to-last integer of c1 is "
        << *c1_Iter << endl;

   // If a const iterator had been declared instead with the line:
   // list <int>::const_iterator c1_Iter;
   // an error would have resulted when inserting the 400

   cout << "The list is now:";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
}
```

```Output
The last integer of c1 is 30
The new next-to-last integer of c1 is 400
The list is now: 10 400 30
```

## <a name="erase"></a>  list::Erase

Odebere prvek nebo rozsah prvků v seznamu od zadané pozice.

```cpp
iterator erase(iterator Where);
iterator erase(iterator first, iterator last);
```

### <a name="parameters"></a>Parametry

*kde*<br/>
Pozice prvku, který chcete odebrat ze seznamu.

*první*<br/>
Pozice prvního prvku odebrán ze seznamu.

*last*<br/>
Pozice bezprostředně za posledním prvkem odebrán ze seznamu.

### <a name="return-value"></a>Návratová hodnota

Obousměrný iterátor, který určuje první prvek zbývající za jakýmikoli odstraněnými prvky, nebo ukazatel na konec seznamu, pokud žádný takový prvek neexistuje.

### <a name="remarks"></a>Poznámky

Dojde k žádné přerozdělení, takže iterátory a odkazy zneplatní pouze pro mazání prvků.

`erase` nikdy nevyvolá výjimku.

### <a name="example"></a>Příklad

```cpp
// list_erase.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;
   list <int>::iterator Iter;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );
   c1.push_back( 40 );
   c1.push_back( 50 );
   cout << "The initial list is:";
   for ( Iter = c1.begin( ); Iter != c1.end( ); Iter++ )
      cout << " " << *Iter;
   cout << endl;

   c1.erase( c1.begin( ) );
   cout << "After erasing the first element, the list becomes:";
   for ( Iter = c1.begin( ); Iter != c1.end( ); Iter++ )
      cout << " " << *Iter;
   cout << endl;
   Iter = c1.begin( );
   Iter++;
   c1.erase( Iter, c1.end( ) );
   cout << "After erasing all elements but the first, the list becomes: ";
   for (Iter = c1.begin( ); Iter != c1.end( ); Iter++ )
      cout << " " << *Iter;
   cout << endl;
}
```

```Output
The initial list is: 10 20 30 40 50
After erasing the first element, the list becomes: 20 30 40 50
After erasing all elements but the first, the list becomes:  20
```

## <a name="front"></a>  list::front

Vrátí odkaz na první prvek v seznamu.

```cpp
reference front();
const_reference front() const;
```

### <a name="return-value"></a>Návratová hodnota

Pokud je seznam prázdný, vrácení není definován.

### <a name="remarks"></a>Poznámky

Pokud návratová hodnota `front` je přiřazen `const_reference`, objekt seznamu nelze upravit. Pokud návratová hodnota `front` je přiřazen `reference`, objekt seznamu lze upravit.

Při kompilaci pomocí [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) definováno jako 1 nebo 2, dojde k chybě při pokusu o přístup k prvku v prázdném seznamu.  Zobrazit [Checked Iterators](../standard-library/checked-iterators.md) Další informace.

### <a name="example"></a>Příklad

```cpp
// list_front.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main() {
   using namespace std;
   list <int> c1;

   c1.push_back( 10 );

   int& i = c1.front();
   const int& ii = c1.front();

   cout << "The first integer of c1 is " << i << endl;
   i++;
   cout << "The first integer of c1 is " << ii << endl;
}
```

```Output
The first integer of c1 is 10
The first integer of c1 is 11
```

## <a name="get_allocator"></a>  list::get_allocator

Vrátí kopii přidělování objektu používanou k vytvoření seznamu.

```cpp
Allocator get_allocator() const;
```

### <a name="return-value"></a>Návratová hodnota

Alokátor použitý v seznamu.

### <a name="remarks"></a>Poznámky

Alokátory pro třídu seznamu určete, jak třída spravuje úložiště. Výchozí alokátorů součástí třídy kontejneru standardní knihovny C++ postačí pro většinu programovacích potřeb. Psaní a použití vlastní třídu alokátoru je rozšířená C++.

### <a name="example"></a>Příklad

```cpp
// list_get_allocator.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   // The following lines declare objects
   // that use the default allocator.
   list <int> c1;
   list <int, allocator<int> > c2 = list <int, allocator<int> >( allocator<int>( ) );

   // c3 will use the same allocator class as c1
   list <int> c3( c1.get_allocator( ) );

   list<int>::allocator_type xlst = c1.get_allocator( );
   // You can now call functions on the allocator class used by c1
}
```

## <a name="insert"></a>  list::Insert

Vloží prvek nebo prvky, nebo rozsah prvků do seznamu na zadané pozici.

```cpp
iterator insert(iterator Where, const Type& Val);
iterator insert(iterator Where, Type&& Val);

void insert(iterator Where, size_type Count, const Type& Val);
iterator insert(iterator Where, initializer_list<Type> IList);

template <class InputIterator>
void insert(iterator Where, InputIterator First, InputIterator Last);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|-|-|
|*kde*|Pozice v cílovém seznamu vloženy první prvek.|
|*Val*|Hodnota prvku vloženého do seznamu.|
|*Počet*|Počet prvků vloženého do seznamu.|
|*první*|Pozice prvního prvku v rozsahu prvků v seznamu argumentů, které se mají zkopírovat.|
|*poslední*|Pozice prvního prvku mimo rozsah prvků v seznamu argumentů, které se mají zkopírovat.|

### <a name="return-value"></a>Návratová hodnota

Vložit první dvě funkce vrátí iterátor, který odkazuje na místo, kde se nový prvek vložila do seznamu.

### <a name="example"></a>Příklad

```cpp
// list_class_insert.cpp
// compile with: /EHsc
#include <list>
#include <iostream>
#include <string>

int main()
{
    using namespace std;
    list <int> c1, c2;
    list <int>::iterator Iter;

    c1.push_back(10);
    c1.push_back(20);
    c1.push_back(30);
    c2.push_back(40);
    c2.push_back(50);
    c2.push_back(60);

    cout << "c1 =";
    for (auto c : c1)
        cout << " " << c;
    cout << endl;

    Iter = c1.begin();
    Iter++;
    c1.insert(Iter, 100);
    cout << "c1 =";
    for (auto c : c1)
        cout << " " << c;
    cout << endl;

    Iter = c1.begin();
    Iter++;
    Iter++;
    c1.insert(Iter, 2, 200);

    cout << "c1 =";
    for(auto c : c1)
        cout << " " << c;
    cout << endl;

    c1.insert(++c1.begin(), c2.begin(), --c2.end());

    cout << "c1 =";
    for (auto c : c1)
        cout << " " << c;
    cout << endl;

    // initialize a list of strings by moving
    list < string > c3;
    string str("a");

    c3.insert(c3.begin(), move(str));
    cout << "Moved first element: " << c3.front() << endl;

    // Assign with an initializer_list
    list <int> c4{ {1, 2, 3, 4} };
    c4.insert(c4.begin(), { 5, 6, 7, 8 });

    cout << "c4 =";
    for (auto c : c4)
        cout << " " << c;
    cout << endl;
}
```

## <a name="iterator"></a>  list::iterator

Typ, který poskytuje obousměrný iterátor, který může číst nebo upravovat libovolný prvek v seznamu.

```cpp
typedef implementation-defined iterator;
```

### <a name="remarks"></a>Poznámky

Typ `iterator` lze použít ke změně hodnoty prvku.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [začít](#begin).

## <a name="list"></a>  list::list

Sestaví seznam určité velikosti nebo s prvky určité hodnoty nebo se zvláštní alokátory nebo jako kopii celé nebo části některého jiného seznamu.

```cpp
list();
explicit list(const Allocator& Al);
explicit list(size_type Count);
list(size_type Count, const Type& Val);
list(size_type Count, const Type& Val, const Allocator& Al);

list(const list& Right);
list(list&& Right);
list(initializer_list<Type> IList, const Allocator& Al);

template <class InputIterator>
list(InputIterator First, InputIterator Last);

template <class InputIterator>
list(InputIterator First, InputIterator Last, const Allocator& Al);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|-|-|
|*Al*|Třída alokátoru, která se má použít s tímto objektem.|
|*Počet*|Počet prvků v sestaveném seznamu.|
|*Val*|Hodnota prvků v seznamu.|
|*doprava*|Seznam, jehož vyrobený seznam je kopií.|
|*první*|Pozice prvního prvku v rozsahu prvků, které se mají zkopírovat.|
|*poslední*|Pozice prvního prvku mimo rozsah prvků, které se mají zkopírovat.|
|*IList*|Objekt initializer_list obsahující prvky, které mají být zkopírovány.|

### <a name="remarks"></a>Poznámky

Všechny konstruktory ukládají objekt alokátoru (*Al*) a inicializují seznam.

[get_allocator](#get_allocator) vrátí kopii přidělování objektu používanou k vytvoření seznamu.

První dva konstruktory určují prázdný počáteční seznam, druhý určuje typ přidělování (*Al*) který se má použít.

Třetí konstruktor určuje opakování zadaného počtu (*počet*) prvků výchozí hodnoty pro třídu `Type`.

Čtvrtý a pátý konstruktor určuje opakování (*počet*) prvků hodnoty *Val*.

Šestý konstruktor určuje kopii seznamu *vpravo*.

Sedmý konstruktor přesune seznam *vpravo*.

Osmý konstruktor používá k určení prvků objekt initializer_list.

Následující dva konstruktory kopírují rozsah `[First, Last)` seznamu.

Žádné konstruktory neprovádí žádná prozatímní přerozdělení.

### <a name="example"></a>Příklad

```cpp
// list_class_list.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main()
{
    using namespace std;
    // Create an empty list c0
    list <int> c0;

    // Create a list c1 with 3 elements of default value 0
    list <int> c1(3);

    // Create a list c2 with 5 elements of value 2
    list <int> c2(5, 2);

    // Create a list c3 with 3 elements of value 1 and with the
    // allocator of list c2
    list <int> c3(3, 1, c2.get_allocator());

    // Create a copy, list c4, of list c2
    list <int> c4(c2);

    // Create a list c5 by copying the range c4[ first,  last)
    list <int>::iterator c4_Iter = c4.begin();
    c4_Iter++;
    c4_Iter++;
    list <int> c5(c4.begin(), c4_Iter);

    // Create a list c6 by copying the range c4[ first,  last) and with
    // the allocator of list c2
    c4_Iter = c4.begin();
    c4_Iter++;
    c4_Iter++;
    c4_Iter++;
    list <int> c6(c4.begin(), c4_Iter, c2.get_allocator());

    cout << "c1 =";
    for (auto c : c1)
        cout << " " << c;
    cout << endl;

    cout << "c2 =";
    for (auto c : c2)
        cout << " " << c;
    cout << endl;

    cout << "c3 =";
    for (auto c : c3)
        cout << " " << c;
    cout << endl;

    cout << "c4 =";
    for (auto c : c4)
        cout << " " << c;
    cout << endl;

    cout << "c5 =";
    for (auto c : c5)
        cout << " " << c;
    cout << endl;

    cout << "c6 =";
    for (auto c : c6)
        cout << " " << c;
    cout << endl;

    // Move list c6 to list c7
    list <int> c7(move(c6));
    cout << "c7 =";
    for (auto c : c7)
        cout << " " << c;
    cout << endl;

    // Construct with initializer_list
    list<int> c8({ 1, 2, 3, 4 });
    cout << "c8 =";
    for (auto c : c8)
        cout << " " << c;
    cout << endl;
}
```

```Output
c1 = 0 0 0c2 = 2 2 2 2 2c3 = 1 1 1c4 = 2 2 2 2 2c5 = 2 2c6 = 2 2 2c7 = 2 2 2c8 = 1 2 3 4
```

## <a name="max_size"></a>  list::max_size

Vrátí maximální délku seznamu.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>Návratová hodnota

Maximální možná délka seznamu.

### <a name="example"></a>Příklad

```cpp
// list_max_size.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;
   list <int>::size_type i;

   i = c1.max_size( );
   cout << "Maximum possible length of the list is " << i << "." << endl;
}
```

## <a name="merge"></a>  list::merge

Odebere prvky ze seznamu argumentů, vloží do cílového seznamu a řadí nové, kombinované sadu elementů ve vzestupném pořadí nebo v jiných určeném pořadí.

```cpp
void merge(list<Type, Allocator>& right);

template <class Traits>
void merge(list<Type, Allocator>& right, Traits comp);
```

### <a name="parameters"></a>Parametry

*doprava*<br/>
Seznam argumentů ke sloučení se do cílového seznamu.

*comp*<br/>
Operátor porovnání slouží k seřazení prvků do cílového seznamu.

### <a name="remarks"></a>Poznámky

Seznam argumentů *správné* je sloučen s cílového seznamu.

Seznamy argumentů a cíl musejí být seřazeny pomocí stejného porovnání vztahu, podle kterého má být seřazeny výsledné pořadí. Výchozí pořadí pro první členská funkce je vzestupném pořadí. Druhá členská funkce ukládá operace porovnání zadané uživatelem *kompozice* třídy `Traits`.

### <a name="example"></a>Příklad

```cpp
// list_merge.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1, c2, c3;
   list <int>::iterator c1_Iter, c2_Iter, c3_Iter;

   c1.push_back( 3 );
   c1.push_back( 6 );
   c2.push_back( 2 );
   c2.push_back( 4 );
   c3.push_back( 5 );
   c3.push_back( 1 );

   cout << "c1 =";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;

   cout << "c2 =";
   for ( c2_Iter = c2.begin( ); c2_Iter != c2.end( ); c2_Iter++ )
      cout << " " << *c2_Iter;
   cout << endl;

   c2.merge( c1 );  // Merge c1 into c2 in (default) ascending order
   c2.sort( greater<int>( ) );
   cout << "After merging c1 with c2 and sorting with >: c2 =";
   for ( c2_Iter = c2.begin( ); c2_Iter != c2.end( ); c2_Iter++ )
      cout << " " << *c2_Iter;
   cout << endl;

   cout << "c3 =";
   for ( c3_Iter = c3.begin( ); c3_Iter != c3.end( ); c3_Iter++ )
      cout << " " << *c3_Iter;
   cout << endl;

   c2.merge( c3, greater<int>( ) );
   cout << "After merging c3 with c2 according to the '>' comparison relation: c2 =";
   for ( c2_Iter = c2.begin( ); c2_Iter != c2.end( ); c2_Iter++ )
      cout << " " << *c2_Iter;
   cout << endl;
}
```

```Output
c1 = 3 6
c2 = 2 4
After merging c1 with c2 and sorting with >: c2 = 6 4 3 2
c3 = 5 1
After merging c3 with c2 according to the '>' comparison relation: c2 = 6 5 4 3 2 1
```

## <a name="op_eq"></a>  list::Operator =

Nahradí prvky seznamu kopii jiného seznamu.

```cpp
list& operator=(const list& right);
list& operator=(list&& right);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|-|-|
|*doprava*|[Seznamu](../standard-library/list-class.md) kopírovaná do `list`.|

### <a name="remarks"></a>Poznámky

Po odstranění jakýchkoli prvků v `list`, operátor, který kopíruje nebo přesouvá obsah *správné* do `list`.

### <a name="example"></a>Příklad

```cpp
// list_operator_as.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list<int> v1, v2, v3;
   list<int>::iterator iter;

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
   v2 = forward< list<int> >(v1);
   cout << "v2 = ";
   for (iter = v2.begin(); iter != v2.end(); iter++)
      cout << *iter << " ";
   cout << endl;
}
```

## <a name="pointer"></a>  list::Pointer

Poskytuje ukazatel na prvek v seznamu.

```cpp
typedef typename Allocator::pointer pointer;
```

### <a name="remarks"></a>Poznámky

Typ `pointer` lze použít ke změně hodnoty prvku.

Ve většině případů [iterátoru](#iterator) by měla sloužit pro přístup k prvkům v seznamu objektů.

## <a name="pop_back"></a>  list::pop_back

Odstraní prvek na konec seznamu.

```cpp
void pop_back();
```

### <a name="remarks"></a>Poznámky

Poslední prvek nesmí být prázdný. `pop_back` nikdy nevyvolá výjimku.

### <a name="example"></a>Příklad

```cpp
// list_pop_back.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;

   c1.push_back( 1 );
   c1.push_back( 2 );
   cout << "The first element is: " << c1.front( ) << endl;
   cout << "The last element is: " << c1.back( ) << endl;

   c1.pop_back( );
   cout << "After deleting the element at the end of the list, "
           "the last element is: " << c1.back( ) << endl;
}
```

```Output
The first element is: 1
The last element is: 2
After deleting the element at the end of the list, the last element is: 1
```

## <a name="pop_front"></a>  list::pop_front

Odstraní prvek na začátku seznamu.

```cpp
void pop_front();
```

### <a name="remarks"></a>Poznámky

První prvek nesmí být prázdný. `pop_front` nikdy nevyvolá výjimku.

### <a name="example"></a>Příklad

```cpp
// list_pop_front.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;

   c1.push_back( 1 );
   c1.push_back( 2 );
   cout << "The first element is: " << c1.front( ) << endl;
   cout << "The second element is: " << c1.back( ) << endl;

   c1.pop_front( );
   cout << "After deleting the element at the beginning of the list, "
         "the first element is: " << c1.front( ) << endl;
}
```

```Output
The first element is: 1
The second element is: 2
After deleting the element at the beginning of the list, the first element is: 2
```

## <a name="push_back"></a>  list::push_back

Přidá prvek na konec seznamu.

```cpp
void push_back(void push_back(Type&& val);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|-|-|
|*Val*|Prvek přidán na konec seznamu.|

### <a name="remarks"></a>Poznámky

Pokud je vyvolána výjimka, seznam zůstane beze změny a je znovu vyvolána výjimka.

### <a name="example"></a>Příklad

```cpp
// list_push_back.cpp
// compile with: /EHsc
#include <list>
#include <iostream>
#include <string>

int main( )
{
   using namespace std;
   list <int> c1;

   c1.push_back( 1 );
   if ( c1.size( ) != 0 )
      cout << "Last element: " << c1.back( ) << endl;

   c1.push_back( 2 );
   if ( c1.size( ) != 0 )
      cout << "New last element: " << c1.back( ) << endl;

// move initialize a list of strings
   list <string> c2;
   string str("a");

   c2.push_back( move( str ) );
   cout << "Moved first element: " << c2.back( ) << endl;
}
```

```Output
Last element: 1
New last element: 2
Moved first element: a
```

## <a name="push_front"></a>  list::push_front

Přidá prvek na začátku seznamu.

```cpp
void push_front(const Type& val);
void push_front(Type&& val);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|-|-|
|*Val*|Element přidá na začátek seznamu.|

### <a name="remarks"></a>Poznámky

Pokud je vyvolána výjimka, seznam zůstane beze změny a je znovu vyvolána výjimka.

### <a name="example"></a>Příklad

```cpp
// list_push_front.cpp
// compile with: /EHsc
#include <list>
#include <iostream>
#include <string>

int main( )
{
   using namespace std;
   list <int> c1;

   c1.push_front( 1 );
   if ( c1.size( ) != 0 )
      cout << "First element: " << c1.front( ) << endl;

   c1.push_front( 2 );
   if ( c1.size( ) != 0 )
      cout << "New first element: " << c1.front( ) << endl;

// move initialize a list of strings
   list <string> c2;
   string str("a");

   c2.push_front( move( str ) );
   cout << "Moved first element: " << c2.front( ) << endl;
}
```

```Output
First element: 1
New first element: 2
Moved first element: a
```

## <a name="rbegin"></a>  list::rbegin

Vrátí iterátor adresující první prvek v obráceném seznamu.

```cpp
const_reverse_iterator rbegin() const;
reverse_iterator rbegin();
```

### <a name="return-value"></a>Návratová hodnota

Reverzní obousměrný iterátor adresující první prvek v obráceném seznamu (nebo adresování, co bylo posledním prvkem v neobráceném seznamu).

### <a name="remarks"></a>Poznámky

`rbegin` se používá s obráceným seznamem stejně jako [začít](#begin) se používá se seznamem.

Pokud návratová hodnota `rbegin` je přiřazen `const_reverse_iterator`, objekt seznamu nelze upravit. Pokud návratová hodnota `rbegin` je přiřazen `reverse_iterator`, objekt seznamu lze upravit.

`rbegin` můžete použít k iteraci seznamem zpět.

### <a name="example"></a>Příklad

```cpp
// list_rbegin.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;
   list <int>::iterator c1_Iter;
   list <int>::reverse_iterator c1_rIter;

   // If the following line replaced the line above, *c1_rIter = 40;
   // (below) would be an error
   //list <int>::const_reverse_iterator c1_rIter;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );
   c1_rIter = c1.rbegin( );
   cout << "The last element in the list is " << *c1_rIter << "." << endl;

   cout << "The list is:";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;

   // rbegin can be used to start an iteration through a list in
   // reverse order
   cout << "The reversed list is:";
   for ( c1_rIter = c1.rbegin( ); c1_rIter != c1.rend( ); c1_rIter++ )
      cout << " " << *c1_rIter;
   cout << endl;

   c1_rIter = c1.rbegin( );
*c1_rIter = 40;
   cout << "The last element in the list is now " << *c1_rIter << "." << endl;
}
```

```Output
The last element in the list is 30.
The list is: 10 20 30
The reversed list is: 30 20 10
The last element in the list is now 40.
```

## <a name="reference"></a>  list::Reference

Typ, který poskytuje odkaz na prvek uložený v seznamu.

```cpp
typedef typename Allocator::reference reference;
```

### <a name="example"></a>Příklad

```cpp
// list_ref.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;

   c1.push_back( 10 );
   c1.push_back( 20 );

   int &i = c1.front( );
   int &j = c1.back( );
   cout << "The first element is " << i << endl;
   cout << "The second element is " << j << endl;
}
```

```Output
The first element is 10
The second element is 20
```

## <a name="remove"></a>  list::Remove

Odstraní prvky v seznamu, které odpovídají zadané hodnotě.

```cpp
void remove(const Type& val);
```

### <a name="parameters"></a>Parametry

*Val*<br/>
Hodnota, která pokud je uložena prvkem, způsobí odebrání tohoto prvku ze seznamu.

### <a name="remarks"></a>Poznámky

Pořadí zbývajících prvků není ovlivněno.

### <a name="example"></a>Příklad

```cpp
// list_remove.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;
   list <int>::iterator c1_Iter, c2_Iter;

   c1.push_back( 5 );
   c1.push_back( 100 );
   c1.push_back( 5 );
   c1.push_back( 200 );
   c1.push_back( 5 );
   c1.push_back( 300 );

   cout << "The initial list is c1 =";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;

   list <int> c2 = c1;
   c2.remove( 5 );
   cout << "After removing elements with value 5, the list becomes c2 =";
   for ( c2_Iter = c2.begin( ); c2_Iter != c2.end( ); c2_Iter++ )
      cout << " " << *c2_Iter;
   cout << endl;
}
```

```Output
The initial list is c1 = 5 100 5 200 5 300
After removing elements with value 5, the list becomes c2 = 100 200 300
```

## <a name="remove_if"></a>  list::remove_if

Odstraní prvky ze seznamu, pro kterou zadaný predikát uspokojen.

```cpp
template <class Predicate>
void remove_if(Predicate pred)
```

### <a name="parameters"></a>Parametry

*Před*<br/>
Unární predikát, který pokud uspokojen prvkem, má za následek odstranění tohoto prvku ze seznamu.

### <a name="example"></a>Příklad

```cpp
// list_remove_if.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

template <class T> class is_odd : public std::unary_function<T, bool>
{
public:
   bool operator( ) ( T& val )
   {
   return ( val % 2 ) == 1;
   }
};

int main( )
{
   using namespace std;
   list <int> c1;
   list <int>::iterator c1_Iter, c2_Iter;

   c1.push_back( 3 );
   c1.push_back( 4 );
   c1.push_back( 5 );
   c1.push_back( 6 );
   c1.push_back( 7 );
   c1.push_back( 8 );

   cout << "The initial list is c1 =";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;

   list <int> c2 = c1;
   c2.remove_if( is_odd<int>( ) );

   cout << "After removing the odd elements, "
        << "the list becomes c2 =";
   for ( c2_Iter = c2.begin( ); c2_Iter != c2.end( ); c2_Iter++ )
      cout << " " << *c2_Iter;
   cout << endl;
}
```

```Output
The initial list is c1 = 3 4 5 6 7 8
After removing the odd elements, the list becomes c2 = 4 6 8
```

## <a name="rend"></a>  list::rend

Vrátí iterátor adresující umístění následující po posledním prvku v obráceném seznamu.

```cpp
const_reverse_iterator rend() const;
reverse_iterator rend();
```

### <a name="return-value"></a>Návratová hodnota

Reverzní obousměrný iterátor adresující umístění následující po posledním prvku v obráceném seznamu (umístění, ke které došlo před první prvek v neobráceném seznamu).

### <a name="remarks"></a>Poznámky

`rend` se používá s obráceným seznamem stejně jako [end](#end) se používá se seznamem.

Pokud návratová hodnota `rend` je přiřazen `const_reverse_iterator`, objekt seznamu nelze upravit. Pokud návratová hodnota `rend` je přiřazen `reverse_iterator`, objekt seznamu lze upravit.

`rend` slouží k otestování pro Určuje, zda zpětný iterátor dosáhl konce seznamu.

Hodnota vrácená `rend` by neměla být dereferencována.

### <a name="example"></a>Příklad

```cpp
// list_rend.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;
   list <int>::iterator c1_Iter;
   list <int>::reverse_iterator c1_rIter;

   // If the following line had replaced the line above, an error would
   // have resulted in the line modifying an element (commented below)
   // because the iterator would have been const
   // list <int>::const_reverse_iterator c1_rIter;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );

   c1_rIter = c1.rend( );
   c1_rIter --;  // Decrementing a reverse iterator moves it forward in
                 // the list (to point to the first element here)
   cout << "The first element in the list is: " << *c1_rIter << endl;

   cout << "The list is:";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;

   // rend can be used to test if an iteration is through all of the
   // elements of a reversed list
   cout << "The reversed list is:";
   for ( c1_rIter = c1.rbegin( ); c1_rIter != c1.rend( ); c1_rIter++ )
      cout << " " << *c1_rIter;
   cout << endl;

   c1_rIter = c1.rend( );
   c1_rIter--;  // Decrementing the reverse iterator moves it backward
                // in the reversed list (to the last element here)

*c1_rIter = 40;  // This modification of the last element would have
                    // caused an error if a const_reverse iterator had
                    // been declared (as noted above)

   cout << "The modified reversed list is:";
   for ( c1_rIter = c1.rbegin( ); c1_rIter != c1.rend( ); c1_rIter++ )
      cout << " " << *c1_rIter;
   cout << endl;
}
```

```Output
The first element in the list is: 10
The list is: 10 20 30
The reversed list is: 30 20 10
The modified reversed list is: 30 20 40
```

## <a name="resize"></a>  list::Resize

Určuje novou velikost seznamu.

```cpp
void resize(size_type _Newsize);
void resize(size_type _Newsize, Type val);
```

### <a name="parameters"></a>Parametry

*_Newsize*<br/>
Nová velikost seznamu.

*Val*<br/>
Hodnota nových prvků, které mají být přidány do seznamu, pokud je nová velikost větší, původní velikost. Pokud je hodnota vynechána, nové prvky jsou přiřazeny výchozí hodnotě pro třídu.

### <a name="remarks"></a>Poznámky

Pokud velikost seznamu menší než požadovaná velikost *_Newsize*, prvky jsou přidány do seznamu, dokud nedosáhne požadované velikosti.

Pokud velikost seznamu je větší než požadovaná velikost, prvky nejblíže konci seznamu jsou odstraněny, dokud seznam nedosáhne velikosti *_Newsize*.

Pokud je k dispozici velikost seznamu je stejná jako požadovaná velikost, nedojde k žádné akci.

[velikost](#size) odráží aktuální velikost seznamu.

### <a name="example"></a>Příklad

```cpp
// list_resize.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );

   c1.resize( 4,40 );
   cout << "The size of c1 is " << c1.size( ) << endl;
   cout << "The value of the last element is " << c1.back( ) << endl;

   c1.resize( 5 );
   cout << "The size of c1 is now " << c1.size( ) << endl;
   cout << "The value of the last element is now " << c1.back( ) << endl;

   c1.resize( 2 );
   cout << "The reduced size of c1 is: " << c1.size( ) << endl;
   cout << "The value of the last element is now " << c1.back( ) << endl;
}
```

```Output
The size of c1 is 4
The value of the last element is 40
The size of c1 is now 5
The value of the last element is now 0
The reduced size of c1 is: 2
The value of the last element is now 20
```

## <a name="reverse"></a>  list::Reverse

Obrátí pořadí, ve kterém se prvky objevují v seznamu.

```cpp
void reverse();
```

### <a name="example"></a>Příklad

```cpp
// list_reverse.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;
   list <int>::iterator c1_Iter;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );

   cout << "c1 =";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;

   c1.reverse( );
   cout << "Reversed c1 =";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;
}
```

```Output
c1 = 10 20 30
Reversed c1 = 30 20 10
```

## <a name="reverse_iterator"></a>  list::reverse_iterator

Typ, který poskytuje obousměrný iterátor, který může číst nebo upravovat prvek v obráceném seznamu.

```cpp
typedef std::reverse_iterator<iterator> reverse_iterator;
```

### <a name="remarks"></a>Poznámky

Typ `reverse_iterator` se používá k iteraci v rámci seznamu pozpátku.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [rbegin –](#rbegin).

## <a name="size"></a>  list::size

Vrátí počet prvků v seznamu.

```cpp
size_type size() const;
```

### <a name="return-value"></a>Návratová hodnota

Aktuální délka seznamu.

### <a name="example"></a>Příklad

```cpp
// list_size.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;
   list <int>::size_type i;

   c1.push_back( 5 );
   i = c1.size( );
   cout << "List length is " << i << "." << endl;

   c1.push_back( 7 );
   i = c1.size( );
   cout << "List length is now " << i << "." << endl;
}
```

```Output
List length is 1.
List length is now 2.
```

## <a name="size_type"></a>  list::size_type

Typ, který vrátí počet prvků v seznamu.

```cpp
typedef typename Allocator::size_type size_type;
```

### <a name="example"></a>Příklad

Podívejte se na příklad pro [velikost](#size).

## <a name="sort"></a>  list::sort

Uspořádá prvky seznamu vzestupně nebo s ohledem na některé jiné řazení zadané uživatelem.

```cpp
void sort();

template <class Traits>
void sort(Traits comp);
```

### <a name="parameters"></a>Parametry

*comp*<br/>
Operátor porovnání slouží k seřazení po sobě jdoucí prvky.

### <a name="remarks"></a>Poznámky

První členská funkce umístí prvky ve vzestupném pořadí ve výchozím nastavení.

Členská funkce šablony řadí prvky podle operace porovnání zadané uživatelem *kompozice* třídy `Traits`.

### <a name="example"></a>Příklad

```cpp
// list_sort.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;
   list <int>::iterator c1_Iter;

   c1.push_back( 20 );
   c1.push_back( 10 );
   c1.push_back( 30 );

   cout << "Before sorting: c1 =";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;

   c1.sort( );
   cout << "After sorting c1 =";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;

   c1.sort( greater<int>( ) );
   cout << "After sorting with 'greater than' operation, c1 =";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;
}
```

```Output
Before sorting: c1 = 20 10 30
After sorting c1 = 10 20 30
After sorting with 'greater than' operation, c1 = 30 20 10
```

## <a name="splice"></a>  list::splice

Odstraní prvky ze seznamu zdrojů a vloží je do cílového seznamu.

```cpp
// insert the entire source list
void splice(const_iterator Where, list<Type, Allocator>& Source);
void splice(const_iterator Where, list<Type, Allocator>&& Source);

// insert one element of the source list
void splice(const_iterator Where, list<Type, Allocator>& Source, const_iterator Iter);
void splice(const_iterator Where, list<Type, Allocator>&& Source, const_iterator Iter);

// insert a range of elements from the source list
void splice(const_iterator Where, list<Type, Allocator>& Source, const_iterator First, const_iterator Last);
void splice(const_iterator Where, list<Type, Allocator>&& Source, const_iterator First, const_iterator Last);
```

### <a name="parameters"></a>Parametry

*kde*<br/>
Pozice v seznamu cíl před, které se má vložit.

*Zdroj*<br/>
Zdroj seznamu, který má být vložen do cílového seznamu.

*ITER*<br/>
Element, který má být vložen ze zdrojového seznamu.

*první*<br/>
První prvek v rozsahu, který chcete vložit ze zdrojového seznamu.

*poslední*<br/>
První pozici za posledním prvkem v rozsahu, který chcete vložit ze zdrojového seznamu.

### <a name="remarks"></a>Poznámky

První pár členských funkcí vloží všechny prvky v seznamu zdrojů do cílového seznamu před pozici, na které odkazuje *kde* a odebere všechny prvky ze zdrojového seznamu. (`&Source` nesmí být stejný jako `this`.)

Druhý pár členských funkcí vloží prvek, na které odkazuje *Iter* před pozice v seznamu cíl odkazuje *kde* a odebere *Iter* z Seznam zdrojů. (Pokud `Where == Iter || Where == ++Iter`, nedošlo k žádné změně.)

Třetí pár členských funkcí vloží rozsahu určeném [ `First`, `Last`) předtím, než na prvek v seznamu cíl odkazuje *kde* a odebere tuto řadu prvků ze zdrojového seznamu. (Pokud `&Source == this`, rozsahu `[First, Last)` nesmí obsahovat prvek, na které odkazuje *kde*.)

Pokud ranged spojení se vloží `N` elementy, a `&Source != this`, objekt třídy [iterátoru](../standard-library/forward-list-class.md#iterator) se zvýší `N` časy.

Ve všech případech iterátory, ukazatele nebo odkazy, které odkazují na prvky spojeného jsou dál platné a jsou přeneseny do cílového kontejneru.

### <a name="example"></a>Příklad

```cpp
// list_splice.cpp
// compile with: /EHsc /W4
#include <list>
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
    list<int> c1{10,11};
    list<int> c2{20,21,22};
    list<int> c3{30,31};
    list<int> c4{40,41,42,43};

    list<int>::iterator where_iter;
    list<int>::iterator first_iter;
    list<int>::iterator last_iter;

    cout << "Beginning state of lists:" << endl;
    cout << "c1 = ";
    print(c1);
    cout << "c2 = ";
    print(c2);
    cout << "c3 = ";
    print(c3);
    cout << "c4 = ";
    print(c4);

    where_iter = c2.begin();
    ++where_iter; // start at second element
    c2.splice(where_iter, c1);
    cout << "After splicing c1 into c2:" << endl;
    cout << "c1 = ";
    print(c1);
    cout << "c2 = ";
    print(c2);

    first_iter = c3.begin();
    c2.splice(where_iter, c3, first_iter);
    cout << "After splicing the first element of c3 into c2:" << endl;
    cout << "c3 = ";
    print(c3);
    cout << "c2 = ";
    print(c2);

    first_iter = c4.begin();
    last_iter = c4.end();
    // set up to get the middle elements
    ++first_iter;
    --last_iter;
    c2.splice(where_iter, c4, first_iter, last_iter);
    cout << "After splicing a range of c4 into c2:" << endl;
    cout << "c4 = ";
    print(c4);
    cout << "c2 = ";
    print(c2);
}
```

```Output
Beginning state of lists:c1 = 2 elements: (10) (11)c2 = 3 elements: (20) (21) (22)c3 = 2 elements: (30) (31)c4 = 4 elements: (40) (41) (42) (43)After splicing c1 into c2:c1 = 0 elements:c2 = 5 elements: (20) (10) (11) (21) (22)After splicing the first element of c3 into c2:c3 = 1 elements: (31)c2 = 6 elements: (20) (10) (11) (30) (21) (22)After splicing a range of c4 into c2:c4 = 2 elements: (40) (43)c2 = 8 elements: (20) (10) (11) (30) (41) (42) (21) (22)
```

## <a name="swap"></a>  list::swap

Vymění prvky dvou seznamů.

```cpp
void swap(list<Type, Allocator>& right);
friend void swap(list<Type, Allocator>& left, list<Type, Allocator>& right)
```

### <a name="parameters"></a>Parametry

*doprava*<br/>
Seznam poskytující prvky pro záměnu nebo seznam, jehož prvky mají vyměnit s těmi na seznamu *levé*.

*doleva*<br/>
Seznam, jehož prvky mají vyměnit s těmi na seznamu *správné*.

### <a name="example"></a>Příklad

```cpp
// list_swap.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1, c2, c3;
   list <int>::iterator c1_Iter;

   c1.push_back( 1 );
   c1.push_back( 2 );
   c1.push_back( 3 );
   c2.push_back( 10 );
   c2.push_back( 20 );
   c3.push_back( 100 );

   cout << "The original list c1 is:";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;

   c1.swap( c2 );

   cout << "After swapping with c2, list c1 is:";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;

   swap( c1,c3 );

   cout << "After swapping with c3, list c1 is:";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;
}
```

```Output
The original list c1 is: 1 2 3
After swapping with c2, list c1 is: 10 20
After swapping with c3, list c1 is: 100
```

## <a name="unique"></a>  list::Unique

Odebere sousedících duplicitních prvků nebo sousedící prvky, které splňují některé binárním predikátem ze seznamu.

```cpp
void unique();

template <class BinaryPredicate>
void unique(BinaryPredicate pred);
```

### <a name="parameters"></a>Parametry

*Před*<br/>
Binární predikát, který používá k porovnání po sobě jdoucí prvky.

### <a name="remarks"></a>Poznámky

Tato funkce se předpokládá, že je seznam seřazen, tak, aby všechny elementy s duplicitními sousedí. Duplicitní položky, které spolu nesousedí, se neodstraní.

První členská funkce odebere každý element, který při porovnání rovna jeho předchozí prvek.

Druhá členská funkce odebere každý element, který splňuje funkce predikátu *před* ve srovnání s jeho předchozí prvek. Můžete použít některý z binární funkce objekty deklarované v \<funkční > záhlaví pro argument *před* nebo můžete vytvořit svoje vlastní.

### <a name="example"></a>Příklad

```cpp
// list_unique.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;
   list <int>::iterator c1_Iter, c2_Iter,c3_Iter;
   not_equal_to<int> mypred;

   c1.push_back( -10 );
   c1.push_back( 10 );
   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 20 );
   c1.push_back( -10 );

   cout << "The initial list is c1 =";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;

   list <int> c2 = c1;
   c2.unique( );
   cout << "After removing successive duplicate elements, c2 =";
   for ( c2_Iter = c2.begin( ); c2_Iter != c2.end( ); c2_Iter++ )
      cout << " " << *c2_Iter;
   cout << endl;

   list <int> c3 = c2;
   c3.unique( mypred );
   cout << "After removing successive unequal elements, c3 =";
   for ( c3_Iter = c3.begin( ); c3_Iter != c3.end( ); c3_Iter++ )
      cout << " " << *c3_Iter;
   cout << endl;
}
```

```Output
The initial list is c1 = -10 10 10 20 20 -10
After removing successive duplicate elements, c2 = -10 10 20 -10
After removing successive unequal elements, c3 = -10 -10
```

## <a name="value_type"></a>  list::value_type

Typ, který představuje datový typ uložený v seznamu.

```cpp
typedef typename Allocator::value_type value_type;
```

### <a name="remarks"></a>Poznámky

`value_type` je synonymum pro parametr šablony *typ*.

### <a name="example"></a>Příklad

```cpp
// list_value_type.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list<int>::value_type AnInt;
   AnInt = 44;
   cout << AnInt << endl;
}
```

```Output
44
```

## <a name="see-also"></a>Viz také:

[\<list>](../standard-library/list.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)<br/>
