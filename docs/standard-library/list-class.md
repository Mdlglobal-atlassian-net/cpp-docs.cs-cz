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
ms.openlocfilehash: 7e30583a185a46e5e0f0544ac2b00848dc989f26
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377329"
---
# <a name="list-class"></a>list – třída

Třída seznamu standardní knihovny jazyka C++ je šablona třídy sekvenčních kontejnerů, které udržují své prvky v lineárním uspořádání a umožňují efektivní vkládání a odstraňování na libovolném místě v sekvenci. Sekvence je uložena jako obousměrný propojený seznam prvků, z nichž každý obsahuje člen nějakého typu *Type*.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Type, class Allocator= allocator<Type>>
class list
```

### <a name="parameters"></a>Parametry

*Typ*\
Datový typ prvku, který má být uložen v seznamu.

*Přidělování*\
Typ, který představuje uložený objekt přidělování, který zapouzdřuje podrobnosti o přidělení seznamu a přidělení paměti. Tento argument je volitelný a výchozí hodnotou je **alokátor**\<*Typ*>.

## <a name="remarks"></a>Poznámky

Volba typu kontejneru by měla obecně vycházet z typu vyhledávání a vkládání vyžadovaného aplikací. Vektory by měly být upřednostňovaným kontejnerem pro správu sekvence, když je náhodný přístup k libovolnému prvku na prémii a vložení nebo odstranění prvků jsou vyžadovány pouze na konci sekvence. Výkon kontejneru deque třídy je vynikající, když je potřeba náhodný přístup a vložení a odstranění na začátku i na konci sekvence jsou na prémii.

Členské funkce seznamu [slučují](#merge), [zvrátí](#reverse), [jedinečný](#unique), [odebrat](#remove)a [remove_if](#remove_if) byly optimalizovány pro provoz na objektech seznamu a nabízejí vysoce výkonnou alternativu k jejich obecným protějškům.

K přerozdělení seznamu dochází, když členská funkce musí vložit nebo vymazat prvky seznamu. Ve všech takových případech se stanou neplatnými pouze iterátory nebo odkazy, které odkazují na vymývané části řízené sekvence.

Zahrňte standardní seznam \<hlaviček standardní knihovny C++> k definování seznamu šablon [třídy kontejneru](../standard-library/stl-containers.md) a několika podpůrných šablon.

## <a name="members"></a>Členové

### <a name="constructors"></a>Konstruktory

|||
|-|-|
|[list](#list)|Vytvoří seznam určité velikosti nebo s prvky určité hodnoty `allocator` nebo s konkrétní nebo jako kopie některého jiného seznamu.|

### <a name="typedefs"></a>Typedefs

|||
|-|-|
|[allocator_type](#allocator_type)|Typ, který `allocator` představuje třídu pro objekt seznamu.|
|[const_iterator](#const_iterator)|Typ, který poskytuje obousměrný iterátor, který může číst **const** prvek v seznamu.|
|[const_pointer](#const_pointer)|Typ, který poskytuje ukazatel na **prvek const** v seznamu.|
|[const_reference](#const_reference)|Typ, který poskytuje odkaz na **prvek const** uložený v seznamu pro čtení a provádění operací **const.**|
|[const_reverse_iterator](#const_reverse_iterator)|Typ, který poskytuje obousměrný iterátor, který může číst libovolný **prvek const** v seznamu.|
|[difference_type](#difference_type)|Typ, který poskytuje rozdíl mezi dvěma iterátory, které odkazují na prvky ve stejném seznamu.|
|[Iterace](#iterator)|Typ, který poskytuje obousměrný iterátor, který může číst nebo upravovat libovolný prvek v seznamu.|
|[ukazatel](#pointer)|Typ, který poskytuje ukazatel na prvek v seznamu.|
|[Odkaz](#reference)|Typ, který poskytuje odkaz na **prvek const** uložený v seznamu pro čtení a provádění operací **const.**|
|[reverse_iterator](#reverse_iterator)|Typ, který poskytuje obousměrný iterátor, který může číst nebo upravovat prvek v obráceném seznamu.|
|[size_type](#size_type)|Typ, který počítá počet prvků v seznamu.|
|[value_type](#value_type)|Typ, který představuje datový typ uložený v seznamu.|

### <a name="functions"></a>Functions

|||
|-|-|
|[Přiřadit](#assign)|Vymaže prvky ze seznamu a zkopíruje novou sadu prvků do cílového seznamu.|
|[Zpět](#back)|Vrátí odkaz na poslední prvek seznamu.|
|[Začít](#begin)|Vrátí iterátor adresující první prvek v seznamu.|
|[cbegin](#cbegin)|Vrátí const iterator adresující první prvek v seznamu.|
|[cend](#cend)|Vrátí const iterator, který řeší umístění, které následuje poslední prvek v seznamu.|
|[Jasné](#clear)|Vymaže všechny prvky seznamu.|
|[crbegin](#crbegin)|Vrátí const iterator adresující první prvek v obráceném seznamu.|
|[crend](#crend)|Vrátí const iterator, který řeší umístění, které následuje poslední prvek v obráceném seznamu.|
|[místo](#emplace)|Vloží prvek vytvořený na místě do seznamu na zadané pozici.|
|[emplace_back](#emplace_back)|Přidá prvek vytvořený na místě na konec seznamu.|
|[emplace_front](#emplace_front)|Přidá prvek vytvořený na místě na začátek seznamu.|
|[empty](#empty)|Testuje, pokud je seznam prázdný.|
|[Konec](#end)|Vrátí iterátor, který řeší umístění, které následuje poslední prvek v seznamu.|
|[Vymazat](#erase)|Odebere prvek nebo rozsah prvků v seznamu ze zadaných pozic.|
|[Přední](#front)|Vrátí odkaz na první prvek v seznamu.|
|[get_allocator](#get_allocator)|Vrátí kopii `allocator` objektu použitého k vytvoření seznamu.|
|[Vložit](#insert)|Vloží prvek nebo počet prvků nebo rozsah prvků do seznamu na zadané pozici.|
|[max_size](#max_size)|Vrátí maximální délku seznamu.|
|[Sloučit](#merge)|Odebere prvky ze seznamu argumentů, vloží je do cílového seznamu a sestaví novou kombinovanou sadu prvků ve vzestupném pořadí nebo v jiném zadaném pořadí.|
|[pop_back](#pop_back)|Odstraní prvek na konci seznamu.|
|[pop_front](#pop_front)|Odstraní prvek na začátku seznamu.|
|[push_back](#push_back)|Přidá prvek na konec seznamu.|
|[push_front](#push_front)|Přidá prvek na začátek seznamu.|
|[rbegin](#rbegin)|Vrátí iterátor adresující první prvek v obráceném seznamu.|
|[remove](#remove)|Vymaže prvky v seznamu, které odpovídají zadané hodnotě.|
|[remove_if](#remove_if)|Vymaže prvky ze seznamu, pro které je splněn zadaný predikát.|
|[rend](#rend)|Vrátí iterátor, který řeší umístění, které následuje poslední prvek v obráceném seznamu.|
|[Změnit velikost](#resize)|Určuje novou velikost seznamu.|
|[Reverzní](#reverse)|Obrátí pořadí, ve kterém se prvky vyskytují v seznamu.|
|[Velikost](#size)|Vrátí počet prvků v seznamu.|
|[Řazení](#sort)|Uspořádá prvky seznamu ve vzestupném pořadí nebo s ohledem na jiný vztah pořadí.|
|[Spojovat](#splice)|Odebere prvky ze seznamu argumentů a vloží je do cílového seznamu.|
|[Swap](#swap)|Vyměňuje prvky dvou seznamů.|
|[Jedinečný](#unique)|Odebere sousední duplicitní prvky nebo sousední prvky, které splňují některé jiné binární predikát ze seznamu.|

### <a name="operators"></a>Operátory

|||
|-|-|
|[operátor =](#op_eq)|Nahradí prvky seznamu kopií jiného seznamu.|

## <a name="requirements"></a>Požadavky

**Záhlaví** \<:> seznamu

## <a name="allocator_type"></a><a name="allocator_type"></a>allocator_type

Typ, který představuje třídu alokátoru pro objekt seznamu.

```cpp
typedef Allocator allocator_type;
```

### <a name="remarks"></a>Poznámky

`allocator_type`je synonymem pro parametr šablony *Alokátor*.

### <a name="example"></a>Příklad

Viz příklad pro [get_allocator](#get_allocator).

## <a name="assign"></a><a name="assign"></a>Přiřadit

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

*První*\
Pozice prvního prvku v rozsahu prvků, které se mají zkopírovat ze seznamu argumentů.

*Poslední*\
Pozice prvního prvku za rozsahem prvků, které se mají zkopírovat ze seznamu argumentů.

*Počet*\
Počet kopií prvku vloženého do seznamu.

*Val*\
Hodnota prvku vloženého do seznamu.

*Ilist*\
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

## <a name="back"></a><a name="back"></a>Zpět

Vrátí odkaz na poslední prvek seznamu.

```cpp
reference back();

const_reference back() const;
```

### <a name="return-value"></a>Návratová hodnota

Poslední prvek seznamu. Pokud je seznam prázdný, vrácená hodnota není definována.

### <a name="remarks"></a>Poznámky

Pokud `back` je vrácená hodnota `const_reference`přiřazena aplikaci , nelze objekt seznamu změnit. Pokud `back` je vrácená hodnota `reference`přiřazena objektu , lze objekt seznamu změnit.

Při kompilaci pomocí [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) definované jako 1 nebo 2, dojde k chybě za běhu, pokud se pokusíte o přístup k prvku v prázdném seznamu.  Další informace naleznete v [tématu Checked Iterators](../standard-library/checked-iterators.md) for more information.

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

## <a name="begin"></a><a name="begin"></a>Začít

Vrátí iterátor adresující první prvek v seznamu.

```cpp
const_iterator begin() const;

iterator begin();
```

### <a name="return-value"></a>Návratová hodnota

Obousměrný itečelní objekt adresující první prvek v seznamu nebo umístění, které následuje prázdný seznam.

### <a name="remarks"></a>Poznámky

Pokud `begin` je vrácená hodnota `const_iterator`přiřazena aplikaci , nelze prvky v objektu seznamu změnit. Pokud `begin` je vrácená hodnota `iterator`přiřazena k aplikaci , lze změnit prvky v objektu seznamu.

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

## <a name="cbegin"></a><a name="cbegin"></a>cbegin

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

## <a name="cend"></a><a name="cend"></a>cend

Vrátí `const` iterátor, který řeší umístění těsně za poslední prvek v rozsahu.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>Návratová hodnota

Obousměrný `const` iterátor, který ukazuje těsně za koncem rozsahu.

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

## <a name="clear"></a><a name="clear"></a>Jasné

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

## <a name="const_iterator"></a><a name="const_iterator"></a>const_iterator

Typ, který poskytuje obousměrný iterátor, který může číst **const** prvek v seznamu.

```cpp
typedef implementation-defined const_iterator;
```

### <a name="remarks"></a>Poznámky

Typ `const_iterator` nelze použít ke změně hodnoty prvku.

### <a name="example"></a>Příklad

Viz příklad pro [zpět](#back).

## <a name="const_pointer"></a><a name="const_pointer"></a>const_pointer

Poskytuje ukazatel na **prvek const** v seznamu.

```cpp
typedef typename Allocator::const_pointer const_pointer;
```

### <a name="remarks"></a>Poznámky

Typ `const_pointer` nelze použít ke změně hodnoty prvku.

Ve většině případů [iterátor](#iterator) by měl být použit pro přístup k prvkům v seznamu objektu.

## <a name="const_reference"></a><a name="const_reference"></a>const_reference

Typ, který poskytuje odkaz na **prvek const** uložený v seznamu pro čtení a provádění operací **const.**

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

## <a name="const_reverse_iterator"></a><a name="const_reverse_iterator"></a>const_reverse_iterator

Typ, který poskytuje obousměrný iterátor, který může číst libovolný **prvek const** v seznamu.

```cpp
typedef std::reverse_iterator<const_iterator> const_reverse_iterator;
```

### <a name="remarks"></a>Poznámky

Typ `const_reverse_iterator` nemůže změnit hodnotu prvku a používá se k iterátu prostřednictvím seznamu v opačném pořadí.

### <a name="example"></a>Příklad

Viz příklad pro [rbegin](#rbegin).

## <a name="crbegin"></a><a name="crbegin"></a>crbegin

Vrátí const iterator adresující první prvek v obráceném seznamu.

```cpp
const_reverse_iterator rbegin() const;
```

### <a name="return-value"></a>Návratová hodnota

Const reverzní obousměrný iterátor adresování první prvek v obráceném seznamu (nebo řešení `list`toho, co bylo poslední prvek v unreverse ).

### <a name="remarks"></a>Poznámky

`crbegin`se používá s obráceným seznamem stejně `list`jako [list::begin](#begin) se používá s .

S návratovou `crbegin`hodnotou aplikace nelze objekt seznamu změnit. [list::rbegin](#rbegin) lze použít k iterátu prostřednictvím seznamu pozpátku.

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

## <a name="crend"></a><a name="crend"></a>crend

Vrátí const iterator, který řeší umístění, které následuje poslední prvek v obráceném seznamu.

```cpp
const_reverse_iterator rend() const;
```

### <a name="return-value"></a>Návratová hodnota

Const reverzní obousměrný iterátor, který řeší umístění následující poslední prvek v obráceném [seznamu](../standard-library/list-class.md) (umístění, které `list`předcházelo první prvek v unreverse).

### <a name="remarks"></a>Poznámky

`crend`se používá s obráceným seznamem stejně jako `list` [list::end](#end) se používá s .

S vrácenou `crend`hodnotou `list` aplikace nelze objekt změnit.

`crend`lze použít k testování, zda reverzní iterátor dosáhl `list`konce svého .

Hodnota vrácená `crend` by neměla být odkazována.

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

## <a name="difference_type"></a><a name="difference_type"></a>difference_type

Podepsaný typ celé číslo, který lze použít k reprezentaci počtu prvků seznamu v rozsahu mezi prvky, na které se iterátory upozorují.

```cpp
typedef typename Allocator::difference_type difference_type;
```

### <a name="remarks"></a>Poznámky

Je `difference_type` typ vrácena při odečtení nebo zvýšení prostřednictvím iterátory kontejneru. Obvykle `difference_type` se používá k reprezentaci počtu prvků `first` `last`v rozsahu [ , `first` ) `last`mezi iterátory `first` a , zahrnuje prvek, na který se vztahuje, a rozsah prvků až do prvku, na který je však `last`nezahrnuto.

Všimněte `difference_type` si, že i když je k dispozici pro všechny iterátory, které splňují požadavky vstupníitekor, který zahrnuje třídu obousměrné iterátory podporované reverzibilní kontejnery, jako je set, odčítání mezi iterátory je podporován pouze random-access iterátory poskytované kontejneru s náhodným přístupem, jako je [například vector Class](../standard-library/vector-class.md).

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

## <a name="emplace"></a><a name="emplace"></a>místo

Vloží prvek vytvořený na místě do seznamu na zadané pozici.

```cpp
void emplace(iterator Where, Type&& val);
```

### <a name="parameters"></a>Parametry

*Kde*\
Pozice v cílovém [seznamu,](../standard-library/list-class.md) kam je vložen první prvek.

*Val*\
Prvek přidán na konec `list`.

### <a name="remarks"></a>Poznámky

Pokud je vyvolána výjimka, `list` je ponechána beze změny a výjimka je znovu vyvolána.

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

## <a name="emplace_back"></a><a name="emplace_back"></a>emplace_back

Přidá prvek vytvořený na místě na konec seznamu.

```cpp
void emplace_back(Type&& val);
```

### <a name="parameters"></a>Parametry

*Val*\
Prvek byl přidán na konec [seznamu](../standard-library/list-class.md).

### <a name="remarks"></a>Poznámky

Pokud je vyvolána výjimka, `list` je ponechána beze změny a výjimka je znovu vyvolána.

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

## <a name="emplace_front"></a><a name="emplace_front"></a>emplace_front

Přidá prvek vytvořený na místě na začátek seznamu.

```cpp
void emplace_front(Type&& val);
```

### <a name="parameters"></a>Parametry

*Val*\
Prvek byl přidán na začátek [seznamu](../standard-library/list-class.md).

### <a name="remarks"></a>Poznámky

Pokud je vyvolána výjimka, `list` je ponechána beze změny a výjimka je znovu vyvolána.

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

## <a name="empty"></a><a name="empty"></a>Prázdné

Testuje, pokud je seznam prázdný.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Návratová hodnota

**true,** pokud je seznam prázdný; **false,** pokud seznam není prázdný.

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

## <a name="end"></a><a name="end"></a>Konec

Vrátí iterátor, který řeší umístění, které následuje poslední prvek v seznamu.

```cpp
const_iterator end() const;
iterator end();
```

### <a name="return-value"></a>Návratová hodnota

Obousměrný iterátor, který řeší umístění, které následuje poslední prvek v seznamu. Pokud je seznam prázdný, pak `list::end == list::begin`.

### <a name="remarks"></a>Poznámky

`end`se používá k testování, zda iterátor dosáhl konce svého seznamu.

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

## <a name="erase"></a><a name="erase"></a>Vymazat

Odebere prvek nebo rozsah prvků v seznamu ze zadaných pozic.

```cpp
iterator erase(iterator Where);
iterator erase(iterator first, iterator last);
```

### <a name="parameters"></a>Parametry

*Kde*\
Umístění prvku, který má být odebrán ze seznamu.

*První*\
Umístění prvního prvku odebránze seznamu.

*Poslední*\
Umístěte těsně za poslední prvek odebrán ze seznamu.

### <a name="return-value"></a>Návratová hodnota

Obousměrný iterátor, který označuje první prvek zbývající za všechny prvky odebrány nebo ukazatel na konec seznamu, pokud žádný takový prvek neexistuje.

### <a name="remarks"></a>Poznámky

Nedojde k žádné přerozdělení, takže iterátory a odkazy se stanou neplatnými pouze pro vymažené prvky.

`erase`nikdy vyvolá výjimku.

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

## <a name="front"></a><a name="front"></a>Přední

Vrátí odkaz na první prvek v seznamu.

```cpp
reference front();
const_reference front() const;
```

### <a name="return-value"></a>Návratová hodnota

Pokud je seznam prázdný, návrat není definován.

### <a name="remarks"></a>Poznámky

Pokud `front` je vrácená hodnota `const_reference`přiřazena aplikaci , nelze objekt seznamu změnit. Pokud `front` je vrácená hodnota `reference`přiřazena objektu , lze objekt seznamu změnit.

Při kompilaci pomocí [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) definované jako 1 nebo 2, dojde k chybě za běhu, pokud se pokusíte o přístup k prvku v prázdném seznamu.  Další informace naleznete v [tématu Checked Iterators](../standard-library/checked-iterators.md) for more information.

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

## <a name="get_allocator"></a><a name="get_allocator"></a>get_allocator

Vrátí kopii objektu přidělování použitého k vytvoření seznamu.

```cpp
Allocator get_allocator() const;
```

### <a name="return-value"></a>Návratová hodnota

Alokátor používaný v seznamu.

### <a name="remarks"></a>Poznámky

Alokátory pro třídu seznamu určují, jak třída spravuje úložiště. Výchozí alokátory dodávané s třídami kontejneru standardní knihovny jazyka C++ jsou dostatečné pro většinu potřeb programování. Psaní a používání vlastní třídy přidělování je pokročilé téma jazyka C++.

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

## <a name="insert"></a><a name="insert"></a>Vložit

Vloží prvek nebo počet prvků nebo rozsah prvků do seznamu na zadané pozici.

```cpp
iterator insert(iterator Where, const Type& Val);
iterator insert(iterator Where, Type&& Val);

void insert(iterator Where, size_type Count, const Type& Val);
iterator insert(iterator Where, initializer_list<Type> IList);

template <class InputIterator>
void insert(iterator Where, InputIterator First, InputIterator Last);
```

### <a name="parameters"></a>Parametry

*Kde*\
Pozice v cílovém seznamu, kam je vložen první prvek.

*Val*\
Hodnota prvku vloženého do seznamu.

*Počet*\
Počet prvků, které jsou vloženy do seznamu.

*První*\
Pozice prvního prvku v rozsahu prvků v seznamu argumentů, které mají být zkopírovány.

*Poslední*\
Pozice první prvek mimo rozsah prvků v seznamu argumentů, které mají být zkopírovány.

### <a name="return-value"></a>Návratová hodnota

První dvě funkce vložení vrátí iterátor, který odkazuje na pozici, kde byl vložen nový prvek do seznamu.

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

## <a name="iterator"></a><a name="iterator"></a>Iterace

Typ, který poskytuje obousměrný iterátor, který může číst nebo upravovat libovolný prvek v seznamu.

```cpp
typedef implementation-defined iterator;
```

### <a name="remarks"></a>Poznámky

Typ `iterator` lze změnit hodnotu prvku.

### <a name="example"></a>Příklad

Viz příklad pro [začátek](#begin).

## <a name="list"></a><a name="list"></a>Seznamu

Vytvoří seznam určité velikosti nebo s prvky určité hodnoty nebo s konkrétním přidělováním nebo jako kopie celého nebo části některého jiného seznamu.

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

*Al*\
Třída alokátoru, která se má použít s tímto objektem.

*Počet*\
Počet prvků v seznamu vyrobeno.

*Val*\
Hodnota prvků v seznamu.

*Právo*\
Seznam, který má být kopií sestaveného seznamu.

*První*\
Umístění prvního prvku v rozsahu prvků, které mají být zkopírovány.

*Poslední*\
Pozice první prvek mimo rozsah prvků, které mají být zkopírovány.

*Ilist*\
Initializer_list, který obsahuje prvky, které mají být zkopírovány.

### <a name="remarks"></a>Poznámky

Všechny konstruktory uložit objekt přidělování (*Al*) a inicializovat seznam.

[get_allocator](#get_allocator) vrátí kopii objektu alokátoru použitého k vytvoření seznamu.

První dva konstruktory určují prázdný počáteční seznam, druhý určující typ alokátoru (*Al*), který má být použit.

Třetí konstruktor určuje opakování zadaného čísla (*Count*) prvků výchozí `Type`hodnoty pro třídu .

Čtvrtý a pátý konstruktory určují opakování (*Count*) prvků hodnoty *Val*.

Šestý konstruktor určuje kopii seznamu *Right*.

Sedmý konstruktor přesune seznam *Vpravo*.

Osmý konstruktor používá k určení prvků objekt initializer_list.

Další dva konstruktory zkopírují rozsah `[First, Last)` seznamu.

Žádný z konstruktorů provádět žádné dočasné přerozdělení.

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

## <a name="max_size"></a><a name="max_size"></a>max_size

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

## <a name="merge"></a><a name="merge"></a>Sloučit

Odebere prvky ze seznamu argumentů, vloží je do cílového seznamu a sestaví novou kombinovanou sadu prvků ve vzestupném pořadí nebo v jiném zadaném pořadí.

```cpp
void merge(list<Type, Allocator>& right);

template <class Traits>
void merge(list<Type, Allocator>& right, Traits comp);
```

### <a name="parameters"></a>Parametry

*Právo*\
Seznam argumentů, který má být sloučen s cílovým seznamem.

*Comp*\
Operátor porovnání slouží k objednání prvků cílového seznamu.

### <a name="remarks"></a>Poznámky

Právo na seznam *argumentů* je sloučeno s cílovým seznamem.

Argument a cílové seznamy musí být seřazeny se stejným vztahem porovnání, podle kterého má být seřazena výsledná sekvence. Výchozí pořadí pro první členská funkce je vzestupné pořadí. Druhá členská funkce ukládá uživatelem *comp* zadaná `Traits`porovnání operace comp třídy .

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

## <a name="operator"></a><a name="op_eq"></a>operátor =

Nahradí prvky seznamu kopií jiného seznamu.

```cpp
list& operator=(const list& right);
list& operator=(list&& right);
```

### <a name="parameters"></a>Parametry

*Právo*\
[Seznam](../standard-library/list-class.md) kopírovaný do `list`.

### <a name="remarks"></a>Poznámky

Po vymazání všech existujících `list`prvků v aplikaci operátor buď zkopíruje nebo přesune obsah *vpravo* do `list`.

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

## <a name="pointer"></a><a name="pointer"></a>Ukazatel

Poskytuje ukazatel na prvek v seznamu.

```cpp
typedef typename Allocator::pointer pointer;
```

### <a name="remarks"></a>Poznámky

Typ `pointer` lze změnit hodnotu prvku.

Ve většině případů [iterátor](#iterator) by měl být použit pro přístup k prvkům v seznamu objektu.

## <a name="pop_back"></a><a name="pop_back"></a>pop_back

Odstraní prvek na konci seznamu.

```cpp
void pop_back();
```

### <a name="remarks"></a>Poznámky

Poslední prvek nesmí být prázdný. `pop_back`nikdy vyvolá výjimku.

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

## <a name="pop_front"></a><a name="pop_front"></a>pop_front

Odstraní prvek na začátku seznamu.

```cpp
void pop_front();
```

### <a name="remarks"></a>Poznámky

První prvek nesmí být prázdný. `pop_front`nikdy vyvolá výjimku.

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

## <a name="push_back"></a><a name="push_back"></a>push_back

Přidá prvek na konec seznamu.

```cpp
void push_back(const Type& val);
void push_back(Type&& val);
```

### <a name="parameters"></a>Parametry

*Val*\
Prvek přidán na konec seznamu.

### <a name="remarks"></a>Poznámky

Pokud je vyvolána výjimka, seznam zůstane beze změny a výjimka je znovu vyvolána.

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

## <a name="push_front"></a><a name="push_front"></a>push_front

Přidá prvek na začátek seznamu.

```cpp
void push_front(const Type& val);
void push_front(Type&& val);
```

### <a name="parameters"></a>Parametry

*Val*\
Prvek byl přidán na začátek seznamu.

### <a name="remarks"></a>Poznámky

Pokud je vyvolána výjimka, seznam zůstane beze změny a výjimka je znovu vyvolána.

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

## <a name="rbegin"></a><a name="rbegin"></a>rbegin

Vrátí iterátor, který řeší první prvek v obráceném seznamu.

```cpp
const_reverse_iterator rbegin() const;
reverse_iterator rbegin();
```

### <a name="return-value"></a>Návratová hodnota

Reverzní obousměrný iterátor adresování první prvek v obráceném seznamu (nebo adresování co byl poslední prvek v seznamu unreverse).

### <a name="remarks"></a>Poznámky

`rbegin`se používá s obráceným seznamem stejně jako [begin](#begin) se používá se seznamem.

Pokud `rbegin` je vrácená hodnota `const_reverse_iterator`přiřazena aplikaci , nelze objekt seznamu změnit. Pokud `rbegin` je vrácená hodnota `reverse_iterator`přiřazena objektu , lze objekt seznamu změnit.

`rbegin`lze itetovat prostřednictvím seznamu pozpátku.

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

## <a name="reference"></a><a name="reference"></a>Odkaz

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

## <a name="remove"></a><a name="remove"></a>Odebrat

Vymaže prvky v seznamu, které odpovídají zadané hodnotě.

```cpp
void remove(const Type& val);
```

### <a name="parameters"></a>Parametry

*Val*\
Hodnota, která, pokud je držena elementem, bude mít za následek odebrání tohoto prvku ze seznamu.

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

## <a name="remove_if"></a><a name="remove_if"></a>remove_if

Vymaže prvky ze seznamu, pro který je splněn zadaný predikát.

```cpp
template <class Predicate>
void remove_if(Predicate pred)
```

### <a name="parameters"></a>Parametry

*pred*\
Unární predikát, který, je-li splněn prvek, vede k výmazu tohoto prvku ze seznamu.

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

## <a name="rend"></a><a name="rend"></a>rend

Vrátí iterátor, který řeší umístění, které následuje za posledním prvkem v obráceném seznamu.

```cpp
const_reverse_iterator rend() const;
reverse_iterator rend();
```

### <a name="return-value"></a>Návratová hodnota

Reverzní obousměrný iterátor, který řeší umístění, které následuje poslední prvek v obráceném seznamu (umístění, které předcházelo prvnímu prvku v seznamu bez protisměru).

### <a name="remarks"></a>Poznámky

`rend`se používá s obráceným seznamem stejně jako [konec](#end) se používá se seznamem.

Pokud `rend` je vrácená hodnota `const_reverse_iterator`přiřazena aplikaci , nelze objekt seznamu změnit. Pokud `rend` je vrácená hodnota `reverse_iterator`přiřazena objektu , lze objekt seznamu změnit.

`rend`lze použít k testování, zda zpětný iterátor dosáhl konce svého seznamu.

Hodnota vrácená `rend` by neměla být odkazována.

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

## <a name="resize"></a><a name="resize"></a>Změnit velikost

Určuje novou velikost seznamu.

```cpp
void resize(size_type _Newsize);
void resize(size_type _Newsize, Type val);
```

### <a name="parameters"></a>Parametry

*_Newsize*\
Nová velikost seznamu.

*Val*\
Hodnota nových prvků, které mají být přidány do seznamu, pokud je nová velikost větší než původní velikost. Pokud je hodnota vynechána, jsou novým prvkům přiřazena výchozí hodnota pro třídu.

### <a name="remarks"></a>Poznámky

Pokud je velikost seznamu menší než požadovaná velikost, *_Newsize*, prvky jsou přidány do seznamu, dokud nedosáhne požadované velikosti.

Pokud je velikost seznamu větší než požadovaná velikost, prvky, které jsou nejblíže konci seznamu, jsou odstraněny, dokud seznam nedosáhne velikosti *_Newsize*.

Pokud je současná velikost seznamu stejná jako požadovaná velikost, nebude provedena žádná akce.

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

## <a name="reverse"></a><a name="reverse"></a>Reverzní

Obrátí pořadí, ve kterém se prvky vyskytují v seznamu.

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

## <a name="reverse_iterator"></a><a name="reverse_iterator"></a>reverse_iterator

Typ, který poskytuje obousměrný iterátor, který může číst nebo upravovat prvek v obráceném seznamu.

```cpp
typedef std::reverse_iterator<iterator> reverse_iterator;
```

### <a name="remarks"></a>Poznámky

Typ `reverse_iterator` se používá k iterátu prostřednictvím seznamu v opačném směru.

### <a name="example"></a>Příklad

Viz příklad pro [rbegin](#rbegin).

## <a name="size"></a><a name="size"></a>Velikost

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

## <a name="size_type"></a><a name="size_type"></a>size_type

Typ, který počítá počet prvků v seznamu.

```cpp
typedef typename Allocator::size_type size_type;
```

### <a name="example"></a>Příklad

Viz příklad [velikosti](#size).

## <a name="sort"></a><a name="sort"></a>Řazení

Uspořádá prvky seznamu ve vzestupném pořadí nebo s ohledem na některé jiné uživatelem zadané pořadí.

```cpp
void sort();

template <class Traits>
    void sort(Traits comp);
```

### <a name="parameters"></a>Parametry

*Comp*\
Operátor porovnání slouží k objednání po sobě jdoucích prvků.

### <a name="remarks"></a>Poznámky

První členská funkce umístí prvky ve vzestupném pořadí ve výchozím nastavení.

Funkce členské šablony objednává prvky podle uživatelem zadaného porovnání operace *comp* třídy `Traits`.

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

## <a name="splice"></a><a name="splice"></a>Spojovat

Odebere prvky ze zdrojového seznamu a vloží je do cílového seznamu.

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

*Kde*\
Pozice v cílovém seznamu, před kterou chcete vložit.

*Zdroj*\
Zdrojový seznam, který má být vložen do cílového seznamu.

*Iter*\
Prvek, který má být vložen ze zdrojového seznamu.

*První*\
První prvek v oblasti, která má být vložena ze zdrojového seznamu.

*Poslední*\
První pozice za poslední prvek v oblasti, které mají být vloženy ze zdrojového seznamu.

### <a name="remarks"></a>Poznámky

První dvojice členských funkcí vloží všechny prvky ve zdrojovém seznamu do cílového seznamu před pozici, na kterou odkazuje *Kde* a odebere všechny prvky ze zdrojového seznamu. (`&Source` se `this`nesmí rovnat .)

Druhá dvojice členských funkcí vloží prvek, na který *iter* odkazuje, před pozici v cílovém seznamu, na kterou odkazuje *Where,* a odebere *iter* ze zdrojového seznamu. (Pokud `Where == Iter || Where == ++Iter`nedojde k žádné změně.)

Třetí dvojice členských funkcí vloží rozsah určený `First` `Last`[ , ) před prvek v cílovém seznamu, na který odkazuje *Kde,* a odebere tento rozsah prvků ze zdrojového seznamu. (Pokud `&Source == this`rozsah `[First, Last)` nesmí obsahovat prvek, na který odkazuje *Where*.)

Pokud splice s rozsahem `N` vloží `&Source != this`prvky a , objekt třídy [iterátoru](../standard-library/forward-list-class.md#iterator) je inkrementní `N` časy.

Ve všech případech iterátory, ukazatele nebo odkazy, které odkazují na spliced prvky zůstávají platné a jsou převedeny do cílového kontejneru.

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

## <a name="swap"></a><a name="swap"></a>Swap

Vyměňuje prvky dvou seznamů.

```cpp
void swap(list<Type, Allocator>& right);
friend void swap(list<Type, Allocator>& left, list<Type, Allocator>& right)
```

### <a name="parameters"></a>Parametry

*Právo*\
Seznam poskytující prvky, které mají být vyměněny, nebo seznam, jehož prvky mají být vyměněny za prvky *zbývajícího*seznamu .

*Vlevo*\
Seznam, jehož prvky mají být vyměněny s prvky v *pravém*seznamu .

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

## <a name="unique"></a><a name="unique"></a>Jedinečný

Odebere sousední duplicitní prvky nebo sousední prvky, které splňují některé jiné binární predikát ze seznamu.

```cpp
void unique();

template <class BinaryPredicate>
void unique(BinaryPredicate pred);
```

### <a name="parameters"></a>Parametry

*pred*\
Binární predikát použitý k porovnání po sobě jdoucích prvků.

### <a name="remarks"></a>Poznámky

Tato funkce předpokládá, že seznam je seřazen tak, aby všechny duplicitní prvky sousedí. Duplikáty, které nejsou vedle sebe, nebudou odstraněny.

První členská funkce odebere každý prvek, který porovnává rovná jeho předchozí prvek.

Druhá členská funkce odebere každý prvek, který splňuje predikát funkce *pred* ve srovnání s jeho předchozí prvek. Můžete použít libovolný z binárních objektů \<funkce deklarovaných ve funkční> záhlaví pro *argument pred* nebo můžete vytvořit vlastní.

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

## <a name="value_type"></a><a name="value_type"></a>value_type

Typ, který představuje datový typ uložený v seznamu.

```cpp
typedef typename Allocator::value_type value_type;
```

### <a name="remarks"></a>Poznámky

`value_type`je synonymem pro parametr šablony *Type*.

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
