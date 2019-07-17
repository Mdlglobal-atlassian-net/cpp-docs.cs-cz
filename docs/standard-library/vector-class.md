---
title: vector – třída
ms.date: 11/04/2016
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
ms.openlocfilehash: 4ec2873055593d8081f7da6d60221494117ca39d
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/16/2019
ms.locfileid: "68241049"
---
# <a name="vector-class"></a>vector – třída

Třída vector standardní knihovny jazyka C++ je třída šablony kontejnery sekvence, které uspořádat prvky daného typu v lineární uspořádání a umožňují rychlý náhodný přístup k libovolnému prvku. Když v na úrovni premium je výkon náhodného přístupu, měly by být upřednostňované kontejnerem pro sekvence.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Type, class Allocator = allocator<Type>>
class vector
```

### <a name="parameters"></a>Parametry

*Typ*\
Typ dat prvku mají být uloženy ve vektoru

*Allocator –* \
Typ představující uložený objekt alokátoru, který zapouzdřuje informace o přidělování a navracení zpět paměti vektoru. Tento argument je nepovinný a výchozí hodnota je `allocator<Type>`.

## <a name="remarks"></a>Poznámky

Vektory povolit konstantním času vložení a odstranění na konci sekvence. Vložení nebo odstranění prvků uprostřed vektor vyžaduje lineárním čase. Výkon [třídou deque](../standard-library/deque-class.md) kontejneru je vynikající s ohledem na vložení a odstranění na začátku a konci sekvence. [List – třída](../standard-library/list-class.md) kontejneru je vynikající s ohledem na vložení a odstranění v libovolném umístění v rámci posloupnosti.

Vektor realokace nastane, pokud členskou funkci, musíte zvýšit pořadí obsažené v objektu vektoru nad rámec jeho aktuální kapacita úložiště. Další vložení a vymazání mohou změnit různé adresy úložiště v rámci sekvence. Ve všech těchto případech, iterátory nebo odkazy, které odkazují na změněné části pořadí se zneplatní. Pokud žádné realokace dojde, jsou dál platné pouze iterátory a odkazy na před bodu vložení nebo odstranění.

[Vektoru\<bool > třída](../standard-library/vector-bool-class.md) je úplné specializací šablony vektoru třídu pro prvky typu bool s Alokátor pro základní typ používán specializací.

[Vektoru\<bool > referenční třídu](../standard-library/vector-bool-class.md#reference_class) je vnořené třídy, jejíž objekty mohou poskytnout odkazy na prvky (jeden bit) v rámci vektor\<bool > objektu.

## <a name="members"></a>Členové

### <a name="constructors"></a>Konstruktory

|||
|-|-|
|[vektor](#vector)|Sestaví vektor určité velikosti nebo s prvky určité hodnoty nebo s konkrétní `allocator` nebo jako kopii vektoru.|

### <a name="typedefs"></a>Typedefs

|||
|-|-|
|[allocator_type](#allocator_type)|Typ, který představuje `allocator` třídy pro objekt vektoru.|
|[const_iterator](#const_iterator)|Typ, který poskytuje iterátor náhodného přístupu, který může přečíst **const** prvek vektoru.|
|[const_pointer](#const_pointer)|Typ, který poskytuje ukazatel **const** prvek vektoru.|
|[const_reference](#const_reference)|Typ, který poskytuje odkaz na **const** prvek uložený v vektor pro čtení a provádění **const** operace.|
|[const_reverse_iterator](#const_reverse_iterator)|Typ, který poskytuje iterátor náhodného přístupu, který může přečíst jakýkoli **const** element ve vektoru.|
|[difference_type](#difference_type)|Typ, který obsahuje rozdíl mezi adresami dvou prvků ve vektoru.|
|[iterator](#iterator)|Typ, který poskytuje iterátor náhodného přístupu, který může číst nebo upravovat libovolný prvek vektoru.|
|[pointer](#pointer)|Typ, který poskytuje ukazatel na prvek ve vektoru.|
|[Referenční dokumentace](#reference)|Typ, který poskytuje odkaz na prvek uložený ve vektoru.|
|[reverse_iterator](#reverse_iterator)|Typ, který poskytuje iterátor náhodného přístupu, který může číst nebo upravovat libovolný prvek v obráceném objektu vektoru.|
|[size_type](#size_type)|Typ, který vrátí počet prvků ve vektoru.|
|[value_type](#value_type)|Typ, který představuje datový typ uložený ve vektoru.|

### <a name="functions"></a>Funkce

|||
|-|-|
|[assign](#assign)|Vymaže vektoru a zkopíruje zadané elementy prázdný vektor.|
|[at](#at)|Vrátí odkaz na prvek v zadaném umístění ve vektoru.|
|[Zpět](#back)|Vrátí odkaz na poslední prvek vektoru.|
|[začít](#begin)|Vrátí iterátor s náhodným přístupem na první prvek ve vektoru.|
|[Kapacita](#capacity)|Vrátí počet prvků, které by mohly obsahovat vektoru bez přidělení úložiště.|
|[cbegin](#cbegin)|Vrátí konstantní iterátor náhodného přístupu na první prvek ve vektoru.|
|[cend](#cend)|Vrátí konstantní iterátor náhodného přístupu, na kterou odkazuje přesně za konec vektoru.|
|[crbegin](#crbegin)|Vrátí konstantní iterátor na první prvek v obráceném objektu vektoru.|
|[crend –](#crend)|Vrátí konstantní iterátor za účelem obráceném objektu vektoru.|
|[Vymazat](#clear)|Odstraní prvky vektoru.|
|[data](#data)|Vrací ukazatel na první prvek ve vektoru.|
|[emplace –](#emplace)|Vloží vytvořený prvek na místo do vektoru na určené pozici.|
|[emplace_back](#emplace_back)|Přidá prvek vytvořený v místě na konec vektoru.|
|[prázdný](#empty)|Testuje, zda kontejner vektoru je prázdný.|
|[ukončení](#end)|Vrátí iterátor náhodného přístupu, který odkazuje na konec vektoru.|
|[vymazání](#erase)|Odebere prvek nebo rozsah prvků ve vektoru od zadané pozice.|
|[Přední](#front)|Vrátí odkaz na první prvek ve vektoru.|
|[get_allocator](#get_allocator)|Vrátí objekt `allocator` Třída použitá ve vektoru.|
|[Vložit](#insert)|Vloží prvek nebo počet elementů do vektoru na určené pozici.|
|[max_size](#max_size)|Vrátí maximální délku vektoru.|
|[pop_back –](#pop_back)|Odstraní prvek na konec vektoru.|
|[push_back](#push_back)|Přidáte element do konec vektoru.|
|[rbegin](#rbegin)|Vrátí iterátor na první prvek v obráceném objektu vektoru.|
|[rend –](#rend)|Vrátí iterátor na konci obráceném objektu vektoru.|
|[reserve](#reserve)|Rezervuje o minimální délce úložiště pro objekt vektoru.|
|[Změna velikosti](#resize)|Určuje novou velikost vektoru.|
|[shrink_to_fit](#shrink_to_fit)|Odstraní nadbytečnou kapacitu.|
|[Velikost](#size)|Vrátí počet prvků ve vektoru.|
|[swap](#swap)|Vymění prvky dvou vektorů.|

### <a name="operators"></a>Operátory

|||
|-|-|
|[– operátor&#91;&#93;](#op_at)|Vrátí odkaz na prvek vektoru na určené pozici.|
|[operátor =](#op_eq)|Nahradí prvky objektu vektoru kopií jiného vektoru.|

## <a name="allocator_type"></a> allocator_type

Typ, který představuje třídu alokátoru pro objekt vektoru.

```cpp
typedef Allocator allocator_type;
```

### <a name="remarks"></a>Poznámky

`allocator_type` je synonymum pro parametr šablony `Allocator`.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [get_allocator](#get_allocator) příklad, který používá `allocator_type`.

## <a name="assign"></a> přiřazení

Vymaže vektoru a zkopíruje zadané elementy prázdný vektor.

```cpp
void assign(size_type Count, const Type& Val);
void assign(initializer_list<Type> IList);

template <class InputIterator>
void assign(InputIterator First, InputIterator Last);
```

### <a name="parameters"></a>Parametry

*první*\
Pozice prvního prvku v rozsahu prvků, které se mají zkopírovat.

*poslední*\
Pozice prvního prvku mimo rozsah prvků, které se mají zkopírovat.

*Počet*\
Počet kopií prvku vloženého do vektoru.

*Val*\
Hodnota prvku vloženého do vektoru.

*IList*\
Objekt initializer_list obsahující prvky, které mají vložit.

### <a name="remarks"></a>Poznámky

Po odstranění jakýchkoli prvků ve vektoru, přiřaďte buď vložení zadaného rozsahu prvků z původního vektoru do vektoru nebo vložení kopií nového prvku zadané hodnoty do vektoru.

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

## <a name="at"></a> v

Vrátí odkaz na prvek v zadaném umístění ve vektoru.

```cpp
reference at(size_type _Pos);

const_reference at(size_type _Pos) const;
```

### <a name="parameters"></a>Parametry

*_Pos*\
Číslo dolní index nebo pozice prvku, který chcete odkazovat ve vektoru.

### <a name="return-value"></a>Návratová hodnota

Odkaz na prvek indexované v argumentu. Pokud `_Off` je větší než velikost vektoru, `at` vyvolá výjimku.

### <a name="remarks"></a>Poznámky

Pokud návratová hodnota `at` je přiřazen `const_reference`, objekt vektoru nelze upravit. Pokud návratová hodnota `at` je přiřazen `reference`, objekt vektoru lze upravit.

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

## <a name="back"></a> Zpět

Vrátí odkaz na poslední prvek vektoru.

```cpp
reference back();

const_reference back() const;
```

### <a name="return-value"></a>Návratová hodnota

Poslední element objektu vektoru. Pokud vektoru je prázdný, návratová hodnota není definována.

### <a name="remarks"></a>Poznámky

Pokud návratová hodnota `back` je přiřazen `const_reference`, objekt vektoru nelze upravit. Pokud návratová hodnota `back` je přiřazen `reference`, objekt vektoru lze upravit.

Při kompilaci pomocí [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) definováno jako 1 nebo 2, Chyba za běhu dochází, pokud se pokusíte o přístup k prvku v prázdný vektor.  Zobrazit [Checked Iterators](../standard-library/checked-iterators.md) Další informace.

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

## <a name="begin"></a> začít

Vrátí iterátor s náhodným přístupem na první prvek ve vektoru.

```cpp
const_iterator begin() const;

iterator begin();
```

### <a name="return-value"></a>Návratová hodnota

Iterátor pro náhodný přístup adresující první prvek v `vector` nebo na umístění následující po prázdná `vector`. Byste měli vždy porovnat hodnoty vrácené s [vector::end](#end) zajistit, že je platný.

### <a name="remarks"></a>Poznámky

Pokud návratová hodnota `begin` je přiřazen [vector::const_iterator](#const_iterator), `vector` objekt nelze změnit. Pokud návratová hodnota `begin` je přiřazena [vector::iterator](#iterator), `vector` objekt lze upravit.

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

## <a name="capacity"></a> Kapacita

Vrátí počet prvků, které by mohly obsahovat vektoru bez přidělení úložiště.

```cpp
size_type capacity() const;
```

### <a name="return-value"></a>Návratová hodnota

Aktuální délka úložiště přidělené pro vektor.

### <a name="remarks"></a>Poznámky

Členská funkce [změnit velikost](#resize) efektivnější, pokud je dostatečná paměť přidělena tak, aby vyhovovaly ho. Pomocí členské funkce [rezervovat](#reserve) k určení množství paměti přidělené.

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

## <a name="cbegin"></a> cbegin

Vrátí **const** iterátor adresující první prvek v rozsahu.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>Návratová hodnota

A **const** iterátor s náhodným přístupem, který ukazuje na první prvek rozsahu nebo na umístění hned za koncem prázdného rozsahu (pro prázdný rozsah `cbegin() == cend()`).

### <a name="remarks"></a>Poznámky

S návratovou hodnotou `cbegin`, nejde upravit prvky v rozsahu.

Můžete použít tuto členskou funkci místo `begin()` členskou funkci pro zajištění, že návratová hodnota je `const_iterator`. Obvykle se používá ve spojení s [automaticky](../cpp/auto-cpp.md) zadejte klíčovým slovem odvození, jak je znázorněno v následujícím příkladu. V tomto příkladu zvažte `Container` jako upravitelný (jinou hodnotu než **const**) kontejner jakéhokoli druhu, který podporuje `begin()` a `cbegin()`.

```cpp
auto i1 = Container.begin();
// i1 is Container<T>::iterator
auto i2 = Container.cbegin();

// i2 is Container<T>::const_iterator
```

## <a name="cend"></a> cend

Vrátí **const** iterátor adresující umístění hned za posledním prvkem v rozsahu.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>Návratová hodnota

A **const** iterátor s náhodným přístupem, který ukazuje přesně za konec rozsahu.

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

## <a name="clear"></a> Vymazat

Odstraní prvky vektoru.

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

## <a name="const_iterator"></a> const_iterator

Typ, který poskytuje iterátor náhodného přístupu, který může přečíst **const** prvek vektoru.

```cpp
typedef implementation-defined const_iterator;
```

### <a name="remarks"></a>Poznámky

Typ `const_iterator` nelze použít ke změně hodnoty prvku.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [zpět](#back) příklad, který používá `const_iterator`.

## <a name="const_pointer"></a> const_pointer

Typ, který poskytuje ukazatel **const** prvek vektoru.

```cpp
typedef typename Allocator::const_pointer const_pointer;
```

### <a name="remarks"></a>Poznámky

Typ `const_pointer` nelze použít ke změně hodnoty prvku.

[Iterátoru](#iterator) se běžněji používá pro přístup k prvku vektoru.

## <a name="const_reference"></a> const_reference

Typ, který poskytuje odkaz na **const** prvek uložený v vektor pro čtení a provádění **const** operace.

```cpp
typedef typename Allocator::const_reference const_reference;
```

### <a name="remarks"></a>Poznámky

Typ `const_reference` nelze použít ke změně hodnoty prvku.

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

## <a name="const_reverse_iterator"></a> const_reverse_iterator

Typ, který poskytuje iterátor náhodného přístupu, který může přečíst jakýkoli **const** element ve vektoru.

```cpp
typedef std::reverse_iterator<const_iterator> const_reverse_iterator;
```

### <a name="remarks"></a>Poznámky

Typ `const_reverse_iterator` hodnotu prvku nelze změnit a slouží k iteraci v rámci vektoru, v opačném pořadí.

### <a name="example"></a>Příklad

Zobrazit [rbegin –](#rbegin) příklad toho, jak deklarovat a používat iterátor.

## <a name="crbegin"></a> crbegin –

Vrátí konstantní iterátor na první prvek v obráceném objektu vektoru.

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>Návratová hodnota

Reverse konstantní iterátor adresující první prvek v obráceném objektu s náhodným přístupem [vektoru](../standard-library/vector-class.md) nebo co bylo posledním prvkem v neobráceném adresování `vector`.

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

## <a name="crend"></a> crend –

Vrátí konstantní iterátor adresující umístění následující po posledním prvku v obráceném objektu vektoru.

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>Návratová hodnota

Reverse konstantní iterátor s náhodným přístupem, který adresuje umístění následující po posledním prvku v obráceném objektu [vektoru](../standard-library/vector-class.md) (umístění, ke které došlo před první prvek v neobráceném `vector`).

### <a name="remarks"></a>Poznámky

`crend` se používá s obráceném objektu `vector` stejně jako [vector::cend](#cend) se používá s `vector`.

S návratovou hodnotou `crend` (vhodně snížen), `vector` objekt nelze změnit.

`crend` můžete použít k testování na tom, zda zpětný iterátor dosáhl konce jeho `vector`.

Hodnota vrácená `crend` by neměla být dereferencována.

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

## <a name="data"></a> Data

Vrací ukazatel na první prvek ve vektoru.

```cpp
const_pointer data() const;

pointer data();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na první prvek v [vektoru](../standard-library/vector-class.md) nebo na umístění následující po prázdná `vector`.

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

## <a name="difference_type"></a> difference_type

Typ, který obsahuje rozdíl mezi dvěma iterátory, které odkazují na prvky v rámci stejné vektoru.

```cpp
typedef typename Allocator::difference_type difference_type;
```

### <a name="remarks"></a>Poznámky

A `difference_type` lze popsat také jako počet prvků mezi dvěma ukazateli, protože ukazatel na prvek obsahuje její adresu.

[Iterátoru](#iterator) se běžněji používá pro přístup k prvku vektoru.

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

## <a name="emplace"></a> emplace –

Vloží vytvořený prvek na místo do vektoru na určené pozici.

```cpp
iterator emplace(
    const_iterator _Where,
    Type&& val);
```

### <a name="parameters"></a>Parametry

*_Where*\
Pozice v [vektoru](../standard-library/vector-class.md) vloženy první prvek.

*Val*\
Hodnota prvku vloženého do `vector`.

### <a name="return-value"></a>Návratová hodnota

Vrátí iterátor, který odkazuje na místo, kde byl vložen nový prvek do funkce `vector`.

### <a name="remarks"></a>Poznámky

Všechny operace vložení může být nákladné, naleznete v tématu [vector – třída](../standard-library/vector-class.md) diskuzi o `vector` výkonu.

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

## <a name="emplace_back"></a> emplace_back

Přidá prvek vytvořený v místě na konec vektoru.

```cpp
template <class... Types>
void emplace_back(Types&&... _Args);
```

### <a name="parameters"></a>Parametry

*_Args*\
Argumenty konstruktoru. Funkce odvodí, které přetížení konstruktoru, který má být vyvolán podle zadaných argumentů.

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

## <a name="empty"></a> prázdný

Testuje, zda je prázdný vektor.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud vektoru je prázdná. **false** Pokud vektoru není prázdný.

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

## <a name="end"></a> ukončení

Vrátí iterátor za koncem.

```cpp
iterator end();

const_iterator end() const;
```

### <a name="return-value"></a>Návratová hodnota

Minulosti koncem iterátoru vektoru. Pokud je prázdný, vektoru `vector::end() == vector::begin()`.

### <a name="remarks"></a>Poznámky

Pokud návratová hodnota `end` je přiřazen proměnné typu `const_iterator`, objekt vektoru nelze upravit. Pokud návratová hodnota `end` je přiřazen proměnné typu `iterator`, objekt vektoru lze upravit.

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

## <a name="erase"></a> vymazání

Odebere prvek nebo rozsah prvků ve vektoru od zadané pozice.

```cpp
iterator erase(
    const_iterator _Where);

iterator erase(
    const_iterator first,
    const_iterator last);
```

### <a name="parameters"></a>Parametry

*_Where*\
Pozice prvku, který chcete odebrat z vektoru.

*první*\
Pozice prvního prvku odebrán vektoru.

*poslední*\
Pozice bezprostředně za posledním prvkem odebrán vektoru.

### <a name="return-value"></a>Návratová hodnota

Iterátor, který určuje první prvek zbývající za jakýmikoli odstraněnými prvky, nebo ukazatel na konec vektoru, pokud žádný takový prvek neexistuje.

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

## <a name="front"></a> Přední

Vrátí odkaz na první prvek ve vektoru.

```cpp
reference front();

const_reference front() const;
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na první prvek v objektu vektoru. Pokud je prázdný vektor, vrácení není definováno.

### <a name="remarks"></a>Poznámky

Pokud návratová hodnota `front` je přiřazen `const_reference`, objekt vektoru nelze upravit. Pokud návratová hodnota `front` je přiřazen **odkaz**, objekt vektoru lze upravit.

Při kompilaci pomocí [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) definováno jako 1 nebo 2, Chyba za běhu dochází, pokud se pokusíte o přístup k prvku v prázdný vektor.  Zobrazit [Checked Iterators](../standard-library/checked-iterators.md) Další informace.

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
   // by incrementing i, we move the front reference to the second element
   i++;
   cout << "Now, the first integer of v1 is "<< i << endl;
}
```

## <a name="get_allocator"></a> get_allocator

Vrátí kopii přidělování objektu používanou k vytvoření vektoru.

```cpp
Allocator get_allocator() const;
```

### <a name="return-value"></a>Návratová hodnota

Alokátor použitý ve vektoru.

### <a name="remarks"></a>Poznámky

Alokátory pro třídu vector zadejte, jak spravuje třídu úložiště. Výchozí alokátorů součástí třídy kontejneru standardní knihovny C++ postačí pro většinu programovacích potřeb. Psaní a použití vlastní třídu alokátoru je rozšířená C++.

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

## <a name="insert"></a> Vložit

Vloží prvek nebo prvky, nebo rozsah prvků do vektoru na určené pozici.

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

*_Where*\
Pozice ve vektoru vloženy první prvek.

*Val*\
Hodnota prvku vloženého do vektoru.

*Počet*\
Počet elementů nebude vložen do vektoru.

*první*\
Pozice prvního prvku v rozsahu prvků, které se mají zkopírovat.

*poslední*\
Pozice prvního prvku mimo rozsah prvků, které se mají zkopírovat.

### <a name="return-value"></a>Návratová hodnota

První dva `insert` funkce vrátí iterátor, který odkazuje na místo, kde se nový prvek vložila do vektoru.

### <a name="remarks"></a>Poznámky

Podmínkou *první* a *poslední* nesmí být iterátory vektor, nebo není chování definováno. Všechny operace vložení může být nákladné, naleznete v tématu [vector – třída](../standard-library/vector-class.md) diskuzi o `vector` výkonu.

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

   const auto v2 = v1;
   v1.insert( v1.begin( )+1, v2.begin( )+2, v2.begin( )+4 );
   cout << "v1 =";
   for (Iter = v1.begin( ); Iter != v1.end( ); Iter++ )
      cout << " " << *Iter;
   cout << endl;

// initialize a vector of vectors by moving v1
   vector < vector <int> > vv1;

   vv1.insert( vv1.begin(), move( v1 ) );
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
v1 = 10 40 20 30
v1 = 10 40 50 50 50 50 20 30
v1 = 10 50 50 40 50 50 50 50 20 30
vv1[0] = 10 50 50 40 50 50 50 50 20 30
```

## <a name="iterator"></a> iterátor

Typ, který poskytuje iterátor náhodného přístupu, který může číst nebo upravovat libovolný prvek vektoru.

```cpp
typedef implementation-defined iterator;
```

### <a name="remarks"></a>Poznámky

Typ **iterátoru** lze použít ke změně hodnoty prvku.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [začít](#begin).

## <a name="max_size"></a> max_size

Vrátí maximální délku vektoru.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>Návratová hodnota

Maximální možná délka vektoru.

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

## <a name="op_at"></a> Operator [].

Vrátí odkaz na prvek vektoru na určené pozici.

```cpp
reference operator[](size_type Pos);

const_reference operator[](size_type Pos) const;
```

### <a name="parameters"></a>Parametry

*POS*\
Pozice prvku vektoru.

### <a name="return-value"></a>Návratová hodnota

Pokud je zadaná pozice větší nebo rovna velikosti kontejneru, výsledek je nedefinován.

### <a name="remarks"></a>Poznámky

Pokud návratová hodnota `operator[]` je přiřazen `const_reference`, objekt vektoru nelze upravit. Pokud návratová hodnota `operator[]` je přiřazena k odkazu, objekt vektoru lze upravit.

Při kompilaci pomocí [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) definováno jako 1 nebo 2, Chyba za běhu dochází, pokud se pokusíte o přístup k prvku mimo hranice vektoru.  Zobrazit [Checked Iterators](../standard-library/checked-iterators.md) Další informace.

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

## <a name="op_eq"></a> operátor =

Nahradí prvky objektu vektoru kopií jiného vektoru.

```cpp
vector& operator=(const vector& right);

vector& operator=(vector&& right);
```

### <a name="parameters"></a>Parametry

*doprava*\
[Vektoru](../standard-library/vector-class.md) kopírovaná do `vector`.

### <a name="remarks"></a>Poznámky

Po odstranění jakýchkoli prvků v `vector`, `operator=` kopíruje nebo přesouvá obsah *správné* do `vector`.

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

## <a name="pointer"></a> Ukazatel

Typ, který poskytuje ukazatel na prvek ve vektoru.

```cpp
typedef typename Allocator::pointer pointer;
```

### <a name="remarks"></a>Poznámky

Typ **ukazatel** lze použít ke změně hodnoty prvku.

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

## <a name="pop_back"></a> pop_back –

Odstraní prvek na konec vektoru.

```cpp
void pop_back();
```

### <a name="remarks"></a>Poznámky

Příklad kódu naleznete v tématu [vektoru:: push_back()](#push_back).

## <a name="push_back"></a> push_back

Přidá prvek na konec vektoru.

```cpp
void push_back(const T& Val);

void push_back(T&& Val);
```

### <a name="parameters"></a>Parametry

*Val*\
Hodnota, kterou chcete přiřadit k elementu přidány na konec vektoru.

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

## <a name="rbegin"></a> rbegin –

Vrátí iterátor na první prvek v obráceném objektu vektoru.

```cpp
reverse_iterator rbegin();
const_reverse_iterator rbegin() const;
```

### <a name="return-value"></a>Návratová hodnota

Zpětný iterátor náhodného přístupu adresující první prvek v obráceném objektu vektoru nebo adresování, co bylo posledním prvkem v neobráceném vektoru.

### <a name="remarks"></a>Poznámky

Pokud návratová hodnota `rbegin` je přiřazen `const_reverse_iterator`, objekt vektoru nelze upravit. Pokud návratová hodnota `rbegin` je přiřazen `reverse_iterator`, objekt vektoru lze upravit.

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

## <a name="reference"></a> Referenční dokumentace

Typ, který poskytuje odkaz na prvek uložený ve vektoru.

```cpp
typedef typename Allocator::reference reference;
```

### <a name="example"></a>Příklad

Naleznete v tématu [na](#at) příklad, jak používat **odkaz** ve třídě vektoru.

## <a name="rend"></a> rend –

Vrátí iterátor adresující umístění následující po posledním prvku v obráceném objektu vektoru.

```cpp
const_reverse_iterator rend() const;
reverse_iterator rend();
```

### <a name="return-value"></a>Návratová hodnota

Zpětný iterátor náhodného přístupu, který adresuje umístění následující po posledním prvku v obráceném objektu vektoru (umístění, ke které došlo před první prvek v neobráceném vektoru).

### <a name="remarks"></a>Poznámky

`rend` se používá s obráceném objektu vektoru stejně jako [end](#end) se používá s vektoru.

Pokud návratová hodnota `rend` je přiřazena `const_reverse_iterator`, pak objekt vektoru nelze upravit. Pokud návratová hodnota `rend` je přiřazen `reverse_iterator`, pak objekt vektoru lze upravit.

`rend` slouží k otestování pro Určuje, zda zpětný iterátor dosáhl konce jeho vektoru.

Hodnota vrácená `rend` by neměla být dereferencována.

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

## <a name="reserve"></a> Rezervovat

Rezervuje o minimální délce úložiště pro vektorový objekt, přidělení místa v případě potřeby.

```cpp
void reserve(size_type count);
```

### <a name="parameters"></a>Parametry

*Počet*\
Minimální délka úložiště, která bude přidělena pro vektor.

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

## <a name="resize"></a> Změna velikosti

Určuje novou velikost vektoru.

```cpp
void resize(size_type Newsize);
void resize(size_type Newsize, Type Val);
```

### <a name="parameters"></a>Parametry

*Newsize*\
Nová velikost vektoru.

*Val*\
Inicializační hodnotu nové elementy přidané do vektoru, pokud je nová velikost větší, původní velikost. Pokud je hodnota vynechána, nové objekty pomocí jejich výchozí konstruktor.

### <a name="remarks"></a>Poznámky

Pokud je velikost kontejneru menší než požadovaná velikost *Newsize*, prvky jsou přidány do vektoru, dokud nedosáhne požadované velikosti. Pokud velikost kontejneru je větší než požadovaná velikost, prvky nejblíže konci kontejneru jsou odstraněny, dokud nedosáhne velikosti kontejneru *Newsize*. Pokud je k dispozici velikost kontejneru je stejná jako požadovaná velikost, nedojde k žádné akci.

[velikost](#size) odráží aktuální velikost vektoru.

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

## <a name="reverse_iterator"></a> reverse_iterator –

Typ, který poskytuje iterátor náhodného přístupu, který může číst nebo upravovat libovolný prvek v obráceném objektu vektoru.

```cpp
typedef std::reverse_iterator<iterator> reverse_iterator;
```

### <a name="remarks"></a>Poznámky

Typ `reverse_iterator` se používá k iteraci v rámci vektoru, v opačném pořadí.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [rbegin –](#rbegin).

## <a name="shrink_to_fit"></a> shrink_to_fit –

Odstraní nadbytečnou kapacitu.

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

## <a name="size"></a> Velikost

Vrátí počet prvků ve vektoru.

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

## <a name="size_type"></a> size_type

Typ, který vrátí počet prvků ve vektoru.

```cpp
typedef typename Allocator::size_type size_type;
```

### <a name="example"></a>Příklad

Podívejte se na příklad pro [kapacity](#capacity).

## <a name="swap"></a> Prohození

Vymění prvky dvou vektorů.

```cpp
void swap(
    vector<Type, Allocator>& right);

friend void swap(
    vector<Type, Allocator>& left,
    vector<Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*doprava*\
Vektor poskytující prvky pro záměnu nebo vektor, jehož prvky mají být zaměněny vektoru *levé*.

*doleva*\
Vektor, jehož prvky mají být zaměněny vektoru *správné*.

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

## <a name="value_type"></a> value_type

Typ, který představuje datový typ uložený ve vektoru.

```cpp
typedef typename Allocator::value_type value_type;
```

### <a name="remarks"></a>Poznámky

`value_type` je synonymum pro parametr šablony `Type`.

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

## <a name="vector"></a> vektor

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

*Al*\
Třída alokátoru, která se má použít s tímto objektem. [get_allocator](#get_allocator) vrátí třídu alokátoru pro objekt.

*Počet*\
Počet prvků ve vytvořeném vektoru.

*Val*\
Hodnota prvků v sestaveném vektoru.

*doprava*\
Vektor, jehož bude vytvořený vektor kopií.

*první*\
Pozice prvního prvku v rozsahu prvků, které se mají zkopírovat.

*poslední*\
Pozice prvního prvku mimo rozsah prvků, které se mají zkopírovat.

*IList*\
Objekt initializer_list obsahující prvky ke zkopírování.

### <a name="remarks"></a>Poznámky

Všechny konstruktory ukládají objekt alokátoru (*Al*) a inicializují vektor.

První dva konstruktory určují prázdný počáteční vektor. Druhý explicitně určuje typ alokátoru (*Al*) který se má použít.

Třetí konstruktor určuje opakování zadaného počtu (*počet*) prvků výchozí hodnoty pro třídu `Type`.

Čtvrtý a pátý konstruktor určuje opakování (*počet*) prvků hodnoty *Val*.

Šestý konstruktor určuje kopii vektoru *vpravo*.

Sedmý konstruktor přesune vektor *vpravo*.

Osmý konstruktor používá k určení prvků objekt initializer_list.

Devátý a desátý konstruktor zkopíruje rozsah [`First`, `Last`) vektoru.

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

## <a name="see-also"></a>Viz také:

[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)<br/>
