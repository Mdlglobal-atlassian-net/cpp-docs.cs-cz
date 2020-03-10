---
title: vector – třída
description: Referenční informace pro C++ implementaci vektoru třídy standardní knihovny Microsoft
ms.date: 02/07/2020
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
ms.openlocfilehash: ed987409dc99ea9b1dade632a5fa5deeb322347a
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78890850"
---
# <a name="vector-class"></a>vector – třída

Třída C++ vektoru standardní knihovny je šablona třídy pro kontejnery sekvence. Vektor ukládá prvky daného typu v lineárním uspořádání a umožňuje rychlé náhodný přístup k jakémukoli prvku. Vektor je preferovaný kontejner pro sekvenci, když je výkon náhodného přístupu na úrovni Premium.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Type, class Allocator = allocator<Type>>
class vector
```

### <a name="parameters"></a>Parametry

*Zadejte*\
Typ dat prvku, který bude uložen ve vektoru

\ *přidělování*
Typ, který představuje uložený objekt přidělování, který zapouzdřuje informace o přidělování a navracení paměti vektoru. Tento argument je nepovinný a výchozí hodnota je `allocator<Type>`.

## <a name="remarks"></a>Poznámky

Vektory umožňují vkládání a odstraňování konstantních časů na konci sekvence. Vložení nebo odstranění prvků uprostřed vektoru vyžaduje lineární čas. Kontejner [třídy deque](../standard-library/deque-class.md) je rychlejší na vkládání a odstraňování na začátku a konci sekvence. Kontejner [tříd seznamu](../standard-library/list-class.md) je rychlejší při vkládání a odstraňování v libovolném umístění v rámci sekvence.

K přerozdělení vektoru dojde, když členská funkce musí zvětšit sekvenci obsaženou v objektu Vector nad rámec aktuální kapacity úložiště. Další vložení a výmazy mohou změnit různé adresy úložiště v rámci sekvence. Ve všech takových případech se iterátory nebo odkazy, které ukazují na změněné části sekvence, stanou neplatnými. Pokud nedojde k žádnému přerozdělení, budou platit pouze iterátory a odkazy před tím, než bude bod vložení nebo odstranění platný.

[Vektorová\<bool > třída](../standard-library/vector-bool-class.md) je plná specializace vektoru šablony třídy pro prvky typu `bool`. Má Alokátor pro podkladový typ používaný specializací.

[Třída vector\<bool > Reference](../standard-library/vector-bool-class.md#reference_class) je vnořená třída, jejíž objekty mohou poskytnout odkazy na elementy (jednotlivé bity) v rámci vektorového\<bool objektu >.

## <a name="members"></a>Členové

### <a name="constructors"></a>Konstruktory

|||
|-|-|
|[vektorový](#vector)|Sestaví vektor konkrétní velikosti nebo s prvky určité hodnoty nebo pomocí konkrétního `allocator` nebo jako kopie nějakého jiného vektoru.|

### <a name="typedefs"></a>Typedefs

|||
|-|-|
|[allocator_type](#allocator_type)|Typ, který představuje třídu `allocator` pro objekt Vector.|
|[const_iterator](#const_iterator)|Typ, který poskytuje iterátor náhodného přístupu, který může číst prvek **const** ve vektoru.|
|[const_pointer](#const_pointer)|Typ, který poskytuje ukazatel na prvek **const** ve vektoru.|
|[const_reference](#const_reference)|Typ, který poskytuje odkaz na prvek **const** uložený ve vektoru. Používá se pro čtení a provádění operací **const** .|
|[const_reverse_iterator](#const_reverse_iterator)|Typ, který poskytuje iterátor náhodného přístupu, který může číst libovolný element **const** ve vektoru.|
|[difference_type](#difference_type)|Typ, který poskytuje rozdíl mezi adresami dvou prvků ve vektoru.|
|[iterátor](#iterator)|Typ, který poskytuje iterátor náhodného přístupu, který může číst nebo upravovat libovolný prvek ve vektoru.|
|[ukazatele](#pointer)|Typ, který poskytuje ukazatel na prvek ve vektoru.|
|[odkaz](#reference)|Typ, který poskytuje odkaz na prvek uložený ve vektoru.|
|[reverse_iterator](#reverse_iterator)|Typ, který poskytuje iterátor náhodného přístupu, který může číst nebo upravovat libovolný prvek v obráceném vektoru.|
|[size_type](#size_type)|Typ, který počítá počet prvků ve vektoru.|
|[value_type](#value_type)|Typ, který představuje datový typ uložený ve vektoru.|

### <a name="functions"></a>Functions

|||
|-|-|
|[řadit](#assign)|Smaže vektor a zkopíruje zadané prvky do prázdného vektoru.|
|[Počínaje](#at)|Vrátí odkaz na prvek v zadaném umístění ve vektoru.|
|[návrat](#back)|Vrátí odkaz na poslední prvek vektoru.|
|[ifunctiondiscovery](#begin)|Vrátí iterátor náhodného přístupu k prvnímu prvku ve vektoru.|
|[klíčivost](#capacity)|Vrátí počet prvků, které může vektor obsahovat, aniž by bylo potřeba přidělit větší úložiště.|
|[cbegin](#cbegin)|Vrátí konstantní iterátor s náhodným přístupem k prvnímu prvku ve vektoru.|
|[cend](#cend)|Vrátí konstantní iterátor s náhodným přístupem, který odkazuje hned za konec vektoru.|
|[crbegin –](#crbegin)|Vrátí konstantní iterátor na první prvek v obráceném vektoru.|
|[crend](#crend)|Vrátí konstantní iterátor na konec obráceného vektoru.|
|[jejich](#clear)|Vymaže prvky vektoru.|
|[údajů](#data)|Vrátí ukazatel na první prvek ve vektoru.|
|[emplace](#emplace)|Vloží prvek sestavený na místo do vektoru na zadané pozici.|
|[emplace_back](#emplace_back)|Přidá prvek konstruovaný na konec vektoru.|
|[obsahovat](#empty)|Testuje, zda je vektorový kontejner prázdný.|
|[účelu](#end)|Vrátí iterátor náhodného přístupu, který odkazuje na konec vektoru.|
|[ověřování](#erase)|Odebere prvek nebo rozsah prvků ve vektoru ze zadané pozice.|
|[dopředu](#front)|Vrátí odkaz na první prvek ve vektoru.|
|[get_allocator](#get_allocator)|Vrátí objekt pro třídu `allocator`, kterou používá vektor.|
|[zadat](#insert)|Vloží prvek nebo počet prvků do vektoru na zadané pozici.|
|[max_size](#max_size)|Vrátí maximální délku vektoru.|
|[pop_back](#pop_back)|Odstraní prvek na konci vektoru.|
|[push_back](#push_back)|Přidejte prvek na konec vektoru.|
|[rbegin](#rbegin)|Vrátí iterátor na první prvek v obráceném vektoru.|
|[rend](#rend)|Vrátí iterátor na konec obráceného vektoru.|
|[rezervační](#reserve)|Vyhrazuje minimální délku úložiště pro vektorový objekt.|
|[velikost](#resize)|Určuje novou velikost vektoru.|
|[shrink_to_fit](#shrink_to_fit)|Zahodí nadbytečnou kapacitu.|
|[hodnota](#size)|Vrátí počet prvků ve vektoru.|
|[adresu](#swap)|Vyměňuje prvky dvou vektorů.|

### <a name="operators"></a>Operátory

|||
|-|-|
|[podnikatel&#91;&#93;](#op_at)|Vrátí odkaz na prvek vektoru na určené pozici.|
|[operátor =](#op_eq)|Nahradí prvky vektoru kopií jiného vektoru.|

## <a name="allocator_type"></a>allocator_type

Typ, který představuje třídu přidělování pro objekt Vector.

```cpp
typedef Allocator allocator_type;
```

### <a name="remarks"></a>Poznámky

`allocator_type` je synonymum pro parametr šablony `Allocator`.

### <a name="example"></a>Příklad

Příklad, který používá `allocator_type`, najdete v příkladu pro [get_allocator](#get_allocator) .

## <a name="assign"></a>řadit

Smaže vektor a zkopíruje zadané prvky do prázdného vektoru.

```cpp
void assign(size_type count, const Type& value);
void assign(initializer_list<Type> init_list);

template <class InputIterator>
void assign(InputIterator first, InputIterator last);
```

### <a name="parameters"></a>Parametry

*první*\
Pozice prvního prvku v rozsahu prvků, které mají být zkopírovány.

*poslední*\
Pozice prvního prvku mimo rozsah prvků, které mají být zkopírovány.

*počet*\
Počet kopií prvku vloženého do vektoru.

*hodnota*\
Hodnota prvku vloženého do vektoru.

*init_list*\
Initializer_list obsahující prvky, které mají být vloženy.

### <a name="remarks"></a>Poznámky

Nejprve `assign` vymaže všechny existující prvky ve vektoru. Poté `assign` buď Vloží zadaný rozsah prvků z původního vektoru do vektoru, nebo vloží kopie nového zadaného prvku hodnoty do vektoru.

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

## <a name="at"></a>Počínaje

Vrátí odkaz na prvek v zadaném umístění ve vektoru.

```cpp
reference at(size_type position);

const_reference at(size_type position) const;
```

### <a name="parameters"></a>Parametry

\ *pozice*
Dolní index nebo číslo pozice prvku, na který se má odkazovat ve vektoru.

### <a name="return-value"></a>Návratová hodnota

Odkaz na element v dolním indexu v argumentu. Je-li *pozice* větší než velikost vektoru, `at` vyvolá výjimku.

### <a name="remarks"></a>Poznámky

Pokud je vrácená hodnota `at` přiřazena k `const_reference`, vektorový objekt nelze změnit. Pokud je vrácená hodnota `at` přiřazena k `reference`, objekt Vector lze upravit.

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

## <a name="back"></a>návrat

Vrátí odkaz na poslední prvek vektoru.

```cpp
reference back();

const_reference back() const;
```

### <a name="return-value"></a>Návratová hodnota

Poslední prvek vektoru. Pokud je vektor prázdný, návratová hodnota není definována.

### <a name="remarks"></a>Poznámky

Pokud je vrácená hodnota `back` přiřazena k `const_reference`, vektorový objekt nelze změnit. Pokud je vrácená hodnota `back` přiřazena k `reference`, objekt Vector lze upravit.

Při kompilaci pomocí [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) definovaného jako 1 nebo 2 dojde k chybě modulu runtime, pokud se pokusíte o přístup k prvku v prázdném vektoru. Další informace najdete v tématu [kontrolované iterátory](../standard-library/checked-iterators.md).

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

## <a name="begin"></a>ifunctiondiscovery

Vrátí iterátor náhodného přístupu k prvnímu prvku ve vektoru.

```cpp
const_iterator begin() const;

iterator begin();
```

### <a name="return-value"></a>Návratová hodnota

Iterátor náhodného přístupu, který adresuje první prvek v `vector` nebo do umístění, který je v prázdném `vector`. Vždy porovnejte hodnotu vrácenou funkcí [Vector:: end](#end) , aby bylo zajištěno, že je platná.

### <a name="remarks"></a>Poznámky

Pokud je vrácená hodnota `begin` přiřazena objektu [Vector:: const_iterator](#const_iterator), objekt `vector` nelze upravit. Pokud je vrácená hodnota `begin` přiřazena k [Vector:: iterátoru](#iterator), lze změnit objekt `vector`.

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

## <a name="capacity"></a>klíčivost

Vrátí počet prvků, které může vektor obsahovat, aniž by bylo potřeba přidělit větší úložiště.

```cpp
size_type capacity() const;
```

### <a name="return-value"></a>Návratová hodnota

Aktuální délka úložného prostoru přiděleného pro daný vektor.

### <a name="remarks"></a>Poznámky

[Změna velikosti](#resize) členské funkce bude efektivnější, pokud je k ní přičleněna dostatek paměti. K určení množství přidělené paměti použijte [rezervu](#reserve) členské funkce.

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

## <a name="cbegin"></a>cbegin

Vrátí **konstantní** iterátor, který adresuje první prvek v rozsahu.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>Návratová hodnota

Iterátor **náhodného** přístupu, který odkazuje na první prvek rozsahu nebo umístění hned za konec prázdného rozsahu (pro prázdný rozsah `cbegin() == cend()`).

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

Iterátor náhodného přístupu **const** , který odkazuje hned za konec rozsahu.

### <a name="remarks"></a>Poznámky

`cend` slouží k otestování, zda iterátor prošl na konci rozsahu.

Tuto členskou funkci lze použít místo `end()` členské funkce pro zajištění, že návratová hodnota je `const_iterator`. Obvykle se používá ve spojení s klíčovým slovem srážky typu [auto](../cpp/auto-cpp.md) , jak je znázorněno v následujícím příkladu. V příkladu zvažte `Container` jako upravitelný kontejner ( **nekonstantní**) libovolného druhu, který podporuje `end()` a `cend()`.

```cpp
auto i1 = Container.end();
// i1 is Container<T>::iterator
auto i2 = Container.cend();

// i2 is Container<T>::const_iterator
```

Hodnota vrácená `cend` by neměla být zpětně odkazovaná. Použijte ji pouze pro porovnání.

## <a name="clear"></a>jejich

Vymaže prvky vektoru.

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

## <a name="const_iterator"></a>const_iterator

Typ, který poskytuje iterátor náhodného přístupu, který může číst prvek **const** ve vektoru.

```cpp
typedef implementation-defined const_iterator;
```

### <a name="remarks"></a>Poznámky

Typ `const_iterator` nelze použít pro úpravu hodnoty prvku.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [zpět](#back) v příkladu, který používá `const_iterator`.

## <a name="const_pointer"></a>const_pointer

Typ, který poskytuje ukazatel na prvek **const** ve vektoru.

```cpp
typedef typename Allocator::const_pointer const_pointer;
```

### <a name="remarks"></a>Poznámky

Typ `const_pointer` nelze použít pro úpravu hodnoty prvku.

[Iterátor](#iterator) se častěji používá pro přístup k prvku Vector.

## <a name="const_reference"></a>const_reference

Typ, který poskytuje odkaz na prvek **const** uložený ve vektoru. Používá se pro čtení a provádění operací **const** .

```cpp
typedef typename Allocator::const_reference const_reference;
```

### <a name="remarks"></a>Poznámky

Typ `const_reference` nelze použít pro úpravu hodnoty prvku.

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

## <a name="const_reverse_iterator"></a>const_reverse_iterator

Typ, který poskytuje iterátor náhodného přístupu, který může číst libovolný element **const** ve vektoru.

```cpp
typedef std::reverse_iterator<const_iterator> const_reverse_iterator;
```

### <a name="remarks"></a>Poznámky

Typ `const_reverse_iterator` nemůže změnit hodnotu prvku a používá se k iterování skrze vektoru v opačném případě.

### <a name="example"></a>Příklad

Příklad, jak deklarovat a používat iterátor, naleznete v tématu [rbegin](#rbegin) .

## <a name="crbegin"></a>crbegin –

Vrátí konstantní iterátor na první prvek v obráceném vektoru.

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>Návratová hodnota

Iterátor reverzního náhodného přístupu, který adresuje první prvek v obráceném [vektoru](../standard-library/vector-class.md) nebo řeší, co byl poslední prvek v neobráceném `vector`.

### <a name="remarks"></a>Poznámky

S návratovou hodnotou `crbegin`nelze změnit objekt `vector`.

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

## <a name="crend"></a>crend

Vrátí konstantní iterátor, který adresuje umístění následující po posledním prvku v obráceném vektoru.

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>Návratová hodnota

Iterátor reverzního náhodného přístupu, který adresuje umístění následující po posledním prvku v obráceném [vektoru](../standard-library/vector-class.md) (umístění, které předchází první prvek v neobráceném `vector`).

### <a name="remarks"></a>Poznámky

`crend` se používá s obráceným `vector` stejně jako [Vector:: cend](#cend) se používá s `vector`.

S návratovou hodnotou `crend` (vhodně sníženo) nelze objekt `vector` změnit.

`crend` lze použít k otestování, zda reverzní iterátor dosáhl konce jeho `vector`.

Hodnota vrácená `crend` by neměla být zpětně odkazovaná. Použijte ji pouze pro porovnání.

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

## <a name="data"></a>údajů

Vrátí ukazatel na první prvek ve vektoru.

```cpp
const_pointer data() const;

pointer data();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na první prvek [vektoru](../standard-library/vector-class.md) nebo na umístění, který je v prázdném `vector`.

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
    vector<int>::pointer c1_ptr;
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
    c1_ptr = c1.data();
    *c1_ptr = 20;
    for (size_t n = c1.size(); 0 < n; --n, c1_ptr++)
    {
        cout << " " << *c1_ptr;
    }
    cout << endl;
}
```

```Output
The vector c1 contains elements: 1 2
The vector c1 now contains elements: 20 2
```

## <a name="difference_type"></a>difference_type

Typ, který poskytuje rozdíl mezi dvěma iterátory, které odkazují na prvky v rámci stejného vektoru.

```cpp
typedef typename Allocator::difference_type difference_type;
```

### <a name="remarks"></a>Poznámky

`difference_type` lze také popsat jako počet prvků mezi dvěma ukazateli, protože ukazatel na element obsahuje svou adresu.

[Iterátor](#iterator) se častěji používá pro přístup k prvku Vector.

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

## <a name="emplace"></a>emplace

Vloží prvek sestavený na místo do vektoru na zadané pozici.

```cpp
template <class... Types>
iterator emplace(
    const_iterator position,
    Types&&... args);
```

### <a name="parameters"></a>Parametry

\ *pozice*
Pozice ve [vektoru](../standard-library/vector-class.md) , kam je vložen první prvek.

\ *argumentů*
Argumenty konstruktoru. Funkce odvodí, které přetížení konstruktoru se vyvolá na základě zadaných argumentů.

### <a name="return-value"></a>Návratová hodnota

Funkce vrátí iterátor, který odkazuje na pozici, kam byl nový prvek vložen do `vector`.

### <a name="remarks"></a>Poznámky

Jakákoli operace vložení může být náročná, viz [Třída Vector](../standard-library/vector-class.md) a diskuze o výkonu `vector`.

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

## <a name="emplace_back"></a>emplace_back

Přidá prvek konstruovaný na konec vektoru.

```cpp
template <class... Types>
void emplace_back(Types&&... args);
```

### <a name="parameters"></a>Parametry

\ *argumentů*
Argumenty konstruktoru. Funkce odvodí, které přetížení konstruktoru se vyvolá na základě zadaných argumentů.

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

## <a name="empty"></a>obsahovat

Testuje, zda je vektor prázdný.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Návratová hodnota

**true** , pokud je vektor prázdný; **false** , pokud vektor není prázdný.

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

## <a name="end"></a>účelu

Vrátí iterátor za koncem.

```cpp
iterator end();

const_iterator end() const;
```

### <a name="return-value"></a>Návratová hodnota

Předchozí iterátor pro vektor. Pokud je vektor prázdný, pak `vector::end() == vector::begin()`.

### <a name="remarks"></a>Poznámky

Pokud je vrácená hodnota `end` přiřazena proměnné typu `const_iterator`, vektorový objekt nelze změnit. Pokud je vrácená hodnota `end` přiřazena proměnné typu `iterator`, objekt Vector lze upravit.

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

## <a name="erase"></a>ověřování

Odebere prvek nebo rozsah prvků ve vektoru ze zadané pozice.

```cpp
iterator erase(
    const_iterator position);

iterator erase(
    const_iterator first,
    const_iterator last);
```

### <a name="parameters"></a>Parametry

\ *pozice*
Pozice prvku, který má být odebrán z vektoru.

*první*\
Pozice prvního elementu odebraného z vektoru

*poslední*\
Pozice bezprostředně za posledním prvkem odebraným z vektoru.

### <a name="return-value"></a>Návratová hodnota

Iterátor, který určuje první prvek zbývající za odebranými prvky, nebo ukazatel na konec vektoru, pokud žádný takový prvek neexistuje.

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

## <a name="front"></a>dopředu

Vrátí odkaz na první prvek ve vektoru.

```cpp
reference front();

const_reference front() const;
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na první prvek v objektu Vector. Pokud je vektor prázdný, vrácení zpět není definováno.

### <a name="remarks"></a>Poznámky

Pokud je vrácená hodnota `front` přiřazena k `const_reference`, vektorový objekt nelze změnit. Pokud je vrácená hodnota `front` přiřazena k **odkazu**, lze objekt Vector upravit.

Při kompilaci pomocí [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) definovaného jako 1 nebo 2 dojde k chybě modulu runtime, pokud se pokusíte o přístup k prvku v prázdném vektoru. Další informace najdete v tématu [kontrolované iterátory](../standard-library/checked-iterators.md).

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

## <a name="get_allocator"></a>get_allocator

Vrátí kopii objektu přidělování, která se používá k vytvoření vektoru.

```cpp
Allocator get_allocator() const;
```

### <a name="return-value"></a>Návratová hodnota

Alokátor použitý vektorem.

### <a name="remarks"></a>Poznámky

Přidělování pro třídu Vector určují, jak Třída spravuje úložiště. Výchozí přidělující třídy kontejnerů C++ standardní knihovny jsou dostačující pro většinu programovacích potřeb. Vytváření a používání vlastního třídy přidělování je pokročilá C++ funkce.

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

## <a name="insert"></a>zadat

Vloží prvek, počet prvků nebo rozsah prvků do vektoru na zadané pozici.

```cpp
iterator insert(
    const_iterator position,
    const Type& value);

iterator insert(
    const_iterator position,
    Type&& value);

void insert(
    const_iterator position,
    size_type count,
    const Type& value);

template <class InputIterator>
void insert(
    const_iterator position,
    InputIterator first,
    InputIterator last);
```

### <a name="parameters"></a>Parametry

\ *pozice*
Pozice ve vektoru, kam je vložen první prvek.

*hodnota*\
Hodnota prvku vloženého do vektoru.

*počet*\
Počet prvků vložených do vektoru.

*první*\
Pozice prvního prvku v rozsahu prvků, které mají být zkopírovány.

*poslední*\
Pozice prvního prvku mimo rozsah prvků, které mají být zkopírovány.

### <a name="return-value"></a>Návratová hodnota

První dvě `insert` funkce vrátí iterátor, který odkazuje na pozici, kam byl nový prvek vložen do vektoru.

### <a name="remarks"></a>Poznámky

Jako předběžnou podmínkou nesmí být *první* a *Poslední* iterátory do vektoru, nebo není chování definované. Jakákoli operace vložení může být náročná, viz [Třída Vector](../standard-library/vector-class.md) a diskuze o výkonu `vector`.

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

## <a name="iterator"></a>iterátor

Typ, který poskytuje iterátor náhodného přístupu, který může číst nebo upravovat libovolný prvek ve vektoru.

```cpp
typedef implementation-defined iterator;
```

### <a name="remarks"></a>Poznámky

**Iterátor** typu lze použít pro úpravu hodnoty prvku.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [začátek](#begin).

## <a name="max_size"></a>max_size

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

## <a name="op_at"></a>operator [] – operátor

Vrátí odkaz na prvek vektoru na určené pozici.

```cpp
reference operator[](size_type position);

const_reference operator[](size_type position) const;
```

### <a name="parameters"></a>Parametry

\ *pozice*
Pozice prvku vektoru.

### <a name="return-value"></a>Návratová hodnota

Pokud je zadaná pozice větší nebo rovna velikosti kontejneru, výsledek je nedefinován.

### <a name="remarks"></a>Poznámky

Pokud je vrácená hodnota `operator[]` přiřazena k `const_reference`, vektorový objekt nelze změnit. Pokud je vrácená hodnota `operator[]` přiřazena k odkazu, lze objekt Vector upravit.

Při kompilaci pomocí [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) definovaného jako 1 nebo 2 dojde k chybě modulu runtime, pokud se pokusíte o přístup k prvku mimo hranice vektoru. Další informace najdete v tématu [kontrolované iterátory](../standard-library/checked-iterators.md).

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

## <a name="op_eq"></a>operátor =

Nahradí prvky vektoru kopií jiného vektoru.

```cpp
vector& operator=(const vector& right);

vector& operator=(vector&& right);
```

### <a name="parameters"></a>Parametry

*pravé*\
[Vektor](../standard-library/vector-class.md) , který se kopíruje do `vector`.

### <a name="remarks"></a>Poznámky

Po vymazání všech existujících prvků v `vector``operator=` buď zkopírování nebo přesunutí obsahu *přímo* do `vector`.

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

## <a name="pointer"></a>ukazatele

Typ, který poskytuje ukazatel na prvek ve vektoru.

```cpp
typedef typename Allocator::pointer pointer;
```

### <a name="remarks"></a>Poznámky

**Ukazatel** typu lze použít pro úpravu hodnoty prvku.

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

## <a name="pop_back"></a>pop_back

Odstraní prvek na konci vektoru.

```cpp
void pop_back();
```

### <a name="remarks"></a>Poznámky

Příklad kódu naleznete v tématu [Vector::p ush_back ()](#push_back).

## <a name="push_back"></a>push_back

Přidá prvek na konec vektoru.

```cpp
void push_back(const T& value);

void push_back(T&& value);
```

### <a name="parameters"></a>Parametry

*hodnota*\
Hodnota, která má být přiřazena k elementu přidanému na konec vektoru.

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

## <a name="rbegin"></a>rbegin

Vrátí iterátor na první prvek v obráceném vektoru.

```cpp
reverse_iterator rbegin();
const_reverse_iterator rbegin() const;
```

### <a name="return-value"></a>Návratová hodnota

Reverzní iterátor s náhodným přístupem, který adresuje první prvek v obráceném vektoru nebo řeší, co byl poslední prvek v neobráceném vektoru.

### <a name="remarks"></a>Poznámky

Pokud je vrácená hodnota `rbegin` přiřazena k `const_reverse_iterator`, vektorový objekt nelze změnit. Pokud je vrácená hodnota `rbegin` přiřazena k `reverse_iterator`, objekt Vector lze upravit.

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

## <a name="reference"></a>odkaz

Typ, který poskytuje odkaz na prvek uložený ve vektoru.

```cpp
typedef typename Allocator::reference reference;
```

### <a name="example"></a>Příklad

Příklad použití **odkazu** ve třídě Vector naleznete [v](#at) tématu.

## <a name="rend"></a>rend

Vrátí iterátor, který adresuje umístění následující po posledním prvku v obráceném vektoru.

```cpp
const_reverse_iterator rend() const;
reverse_iterator rend();
```

### <a name="return-value"></a>Návratová hodnota

Iterátor náhodného přístupu, který adresuje umístění následující po posledním prvku v obráceném vektoru (umístění, které předchází první prvek v neobráceném vektoru).

### <a name="remarks"></a>Poznámky

`rend` se používá s obráceným vektorem stejně jako [End](#end) se používá s vektorem.

Pokud je vrácená hodnota `rend` přiřazena k `const_reverse_iterator`, objekt Vector nelze upravit. Pokud je vrácená hodnota `rend` přiřazena k `reverse_iterator`, objekt Vector lze upravit.

`rend` lze použít k otestování, zda zpětný iterátor dosáhl konce jeho vektoru.

Hodnota vrácená `rend` by neměla být zpětně odkazovaná. Použijte ji pouze pro porovnání.

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

## <a name="reserve"></a>rezervační

Vyhradí minimální délku úložiště pro vektorový objekt a v případě potřeby přidělí prostor.

```cpp
void reserve(size_type count);
```

### <a name="parameters"></a>Parametry

*počet*\
Minimální délka úložiště, které má být přiděleno pro vektor.

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

## <a name="resize"></a>velikost

Určuje novou velikost vektoru.

```cpp
void resize(size_type new_size);
void resize(size_type new_size, Type value);
```

### <a name="parameters"></a>Parametry

*new_size*\
Nová velikost vektoru.

*hodnota*\
Inicializační hodnota nových prvků přidaných do vektoru, pokud je nová velikost větší než původní velikost. Pokud je hodnota vynechána, nové objekty použijí výchozí konstruktor.

### <a name="remarks"></a>Poznámky

Pokud je velikost kontejneru menší než požadovaná velikost, *new_size*`resize` přidá prvky do vektoru, dokud nedosáhne požadované velikosti. Pokud je velikost kontejneru větší než požadovaná velikost, `resize` odstraní prvky nejbližší ke konci kontejneru, dokud nedosáhne *new_size*velikosti. Pokud je současná velikost kontejneru stejná jako požadovaná velikost, není provedena žádná akce.

[Velikost](#size) odráží aktuální velikost vektoru.

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

## <a name="reverse_iterator"></a>reverse_iterator

Typ, který poskytuje iterátor náhodného přístupu, který může číst nebo upravovat libovolný prvek v obráceném vektoru.

```cpp
typedef std::reverse_iterator<iterator> reverse_iterator;
```

### <a name="remarks"></a>Poznámky

Typ `reverse_iterator` slouží k iterování skrze vektor v opačném případě.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [rbegin](#rbegin).

## <a name="shrink_to_fit"></a>shrink_to_fit

Zahodí nadbytečnou kapacitu.

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

## <a name="size"></a>hodnota

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

## <a name="size_type"></a>size_type

Typ, který počítá počet prvků ve vektoru.

```cpp
typedef typename Allocator::size_type size_type;
```

### <a name="example"></a>Příklad

Podívejte se na příklad [kapacity](#capacity).

## <a name="swap"></a>adresu

Vyměňuje prvky dvou vektorů.

```cpp
void swap(
    vector<Type, Allocator>& right);

friend void swap(
    vector<Type, Allocator>& left,
    vector<Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*pravé*\
Vektor, který poskytuje prvky, které mají být prohozeny. Nebo, vektor, jehož prvky mají být vyměněny pomocí prvků ve vektoru *vlevo*.

*levý*\
Vektor, jehož prvky mají být vyměněny pomocí prvků *ve vektoru*.

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

## <a name="value_type"></a>value_type

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

## <a name="vector"></a>vektorový

Vytvoří vektor. Přetížení vytvoří vektor konkrétní velikosti nebo s prvky určité hodnoty. Nebo jako kopie celého nebo části nějakého vektoru. Některá přetížení také umožňují určit přidělování, které se má použít.

```cpp
vector();
explicit vector(const Allocator& allocator);
explicit vector(size_type count);
vector(size_type count, const Type& value);
vector(size_type count, const Type& value, const Allocator& allocator);

vector(const vector& source);
vector(vector&& source);
vector(initializer_list<Type> init_list, const Allocator& allocator);

template <class InputIterator>
vector(InputIterator first, InputIterator last);
template <class InputIterator>
vector(InputIterator first, InputIterator last, const Allocator& allocator);
```

### <a name="parameters"></a>Parametry

\ *přidělování*
Třída alokátoru, která se má použít s tímto objektem. [get_allocator](#get_allocator) vrátí třídu přidělování pro objekt.

*počet*\
Počet prvků ve vytvořeném vektoru.

*hodnota*\
Hodnota prvků v sestaveném vektoru.

\ *zdroje*
Vektor, jehož bude vytvořený vektor kopií.

*první*\
Pozice prvního prvku v rozsahu prvků, které mají být zkopírovány.

*poslední*\
Pozice prvního prvku mimo rozsah prvků, které mají být zkopírovány.

*init_list*\
`initializer_list` obsahující prvky ke zkopírování.

### <a name="remarks"></a>Poznámky

Všechny konstruktory ukládají objekt přidělování (*Alokátor*) a inicializují vektor.

První dva konstruktory určují prázdný počáteční vektor. Druhý konstruktor explicitně určuje typ přidělování (*Alokátor*), který se má použít.

Třetí konstruktor určuje opakování zadaného počtu (*Count*) prvků výchozí hodnoty pro třídu `Type`.

Čtvrtý a pátý konstruktor určuje opakování (*počet*) *prvků hodnoty Value.*

Šestý konstruktor určuje kopii vektorového *zdroje*.

Sedmý konstruktor přesouvá *zdroj*vektoru.

Osmý konstruktor používá k určení prvků objekt initializer_list.

Devátý a desátý konstruktor zkopíruje rozsah [`first`, `last`) vektoru.

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

[Bezpečnost vlákna ve C++ standardní knihovně](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)
