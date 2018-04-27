---
title: Array – třída (standardní knihovna C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- array/std::array
- array/std::array::const_iterator
- array/std::array::const_pointer
- array/std::array::const_reference
- array/std::array::const_reverse_iterator
- array/std::array::difference_type
- array/std::array::iterator
- array/std::array::pointer
- array/std::array::reference
- array/std::array::reverse_iterator
- array/std::array::size_type
- array/std::array::value_type
- array/std::array::assign
- array/std::array::at
- array/std::array::back
- array/std::array::begin
- array/std::array::cbegin
- array/std::array::cend
- array/std::array::crbegin
- array/std::array::crend
- array/std::array::data
- array/std::array::empty
- array/std::array::end
- array/std::array::fill
- array/std::array::front
- array/std::array::max_size
- array/std::array::rbegin
- array/std::array::rend
- array/std::array::size
- array/std::array::swap
- array/std::array::operator=
- array/std::array::operator[]
dev_langs:
- C++
helpviewer_keywords:
- std::array [C++]
- std::array [C++], const_iterator
- std::array [C++], const_pointer
- std::array [C++], const_reference
- std::array [C++], const_reverse_iterator
- std::array [C++], difference_type
- std::array [C++], iterator
- std::array [C++], pointer
- std::array [C++], reference
- std::array [C++], reverse_iterator
- std::array [C++], size_type
- std::array [C++], value_type
- std::array [C++], assign
- std::array [C++], at
- std::array [C++], back
- std::array [C++], begin
- std::array [C++], cbegin
- std::array [C++], cend
- std::array [C++], crbegin
- std::array [C++], crend
- std::array [C++], data
- std::array [C++], empty
- std::array [C++], end
- std::array [C++], fill
- std::array [C++], front
- std::array [C++], max_size
- std::array [C++], rbegin
- std::array [C++], rend
- std::array [C++], size
- std::array [C++], swap
- ', '
- std::array [C++], const_iterator
- std::array [C++], const_pointer
- std::array [C++], const_reference
- std::array [C++], const_reverse_iterator
- std::array [C++], difference_type
- std::array [C++], iterator
- std::array [C++], pointer
- std::array [C++], reference
- std::array [C++], reverse_iterator
- std::array [C++], size_type
- std::array [C++], value_type
- std::array [C++], assign
- std::array [C++], at
- std::array [C++], back
- std::array [C++], begin
- std::array [C++], cbegin
- std::array [C++], cend
- std::array [C++], crbegin
- std::array [C++], crend
- std::array [C++], data
- std::array [C++], empty
- std::array [C++], end
- std::array [C++], fill
- std::array [C++], front
- std::array [C++], max_size
- std::array [C++], rbegin
- std::array [C++], rend
- std::array [C++], size
- std::array [C++], swap
ms.assetid: fdfd43a5-b2b5-4b9e-991f-93bf10fb4293
caps.latest.revision: 22
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c9bea1639ac72c86a4822b98f8ffb71a1fb28227
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="array-class-c-standard-library"></a>Array – třída (standardní knihovna C++)

Popisuje objekt, který určuje posloupnost délka `N` elementů typu `Ty`. Pořadí je uloženo jako pole `Ty`, obsažené v `array<Ty, N>` objektu.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty, std::size_t N>
class array;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|-|-|
|`Ty`|Typ prvku|
|`N`|Počet elementů.|

## <a name="members"></a>Členové

|Definice typu|Popis|
|-|-|
|[const_iterator](#const_iterator)|Typ konstantního iterátoru řízené sekvence|
|[const_pointer](#const_pointer)|Typ konstantního ukazatele na prvek|
|[const_reference](#const_reference)|Typ konstantního odkazu na prvek|
|[const_reverse_iterator](#const_reverse_iterator)|Typ konstantní zpětné iterator pro řízené sekvenci.|
|[difference_type](#difference_type)|Typ vzdálenosti se znaménkem mezi dvěma prvky|
|[Iterator](#iterator)|Typ iterátoru řízené sekvence|
|[Ukazatele](#pointer)|Typ ukazatele na prvek|
|[Referenční dokumentace](#reference)|Typ odkazu na prvek|
|[reverse_iterator](#reverse_iterator)|Typ zpětné iterator pro řízené sekvenci.|
|[size_type](#size_type)|Typ vzdálenosti bez znaménka mezi dvěma prvky|
|[value_type](#value_type)|Typ prvku|

|Členská funkce|Popis|
|-|-|
|[Pole](#array)|Vytvoří objekt array.|
|[přiřazení](#assign)|Nahradí všechny elementy.|
|[at](#at)|Přístup k elementu na zadané pozici.|
|[zpět](#back)|Přístup k posledním elementem.|
|[Začátek](#begin)|Určuje začátek řízené sekvence.|
|[cbegin –](#cbegin)|Vrátí první prvek v poli const iterator náhodným přístupem.|
|[cend –](#cend)|Vrátí const iterator náhodným přístupem této body právě přesahuje za konec pole.|
|[crbegin](#crbegin)|Vrátí const iterator prvním elementem v invertovaných pole.|
|[crend –](#crend)|Vrátí const iterator na konec odstínech pole.|
|[data](#data)|Získá adresu první prvek.|
|[prázdný](#empty)|Testy, jestli jsou elementy nabízejí.|
|[End](#end)|Určuje konec řízené sekvence.|
|[výplně](#fill)|Nahradí všechny elementy se zadanou hodnotou.|
|[Přední](#front)|Přístup k první prvek.|
|[max_size](#max_size)|Spočítá počet prvků.|
|[rbegin –](#rbegin)|Označuje začátek odstínech řízené sekvenci.|
|[rend –](#rend)|Označuje konec odstínech řízené sekvenci.|
|[Velikost](#size)|Spočítá počet prvků.|
|[Swap](#swap)|Zamění obsah dvou kontejnerů.|

|Operátor|Popis|
|-|-|
|[Array::Operator =](#op_eq)|Nahradí řízené sekvenci.|
|[Array::Operator]](#op_at)|Přístup k elementu na zadané pozici.|

## <a name="remarks"></a>Poznámky

Typ, má výchozí konstruktor `array()` a operátor přiřazení výchozí `operator=`a splňuje požadavky na `aggregate`. Proto objekty typu `array<Ty, N>` jde inicializovat pomocí inicializátoru agregační. Například

```cpp
array<int, 4> ai = { 1, 2, 3 };
```

Vytvoří objekt `ai` , obsahuje čtyři celočíselné hodnoty, inicializuje první tři prvky na hodnoty 1, 2 a 3, v uvedeném pořadí a inicializuje čtvrtý element na hodnotu 0.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<pole >

**Namespace:** – std

## <a name="array"></a>  Array::Array –

Vytvoří objekt array.

```cpp
array();

array(const array& right);
```

### <a name="parameters"></a>Parametry

*pravé* vložení objektu nebo rozsah.

### <a name="remarks"></a>Poznámky

Výchozí konstruktor `array()` opustí řízené pořadí Neinicializovaný (nebo výchozí inicializovat). Se používá k určení Neinicializovaný řízené sekvenci.

Konstruktor copy `array(const array& right)` inicializuje řízené sekvenci s pořadím [*správné*`.begin()`, *správné*`.end()`). Se používá k určení počáteční řízené sekvenci, který je kopií pořadí řízené objekt array *správné*.

### <a name="example"></a>Příklad

```cpp
// std__array__array_array.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
    {
    Myarray c0 = {0, 1, 2, 3};

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

    Myarray c1(c0);

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

    return (0);
    }

```

```Output
0 1 2 3
0 1 2 3
```

## <a name="assign"></a>  Array::Assign

Zastaralé v C ++ 11, nahrazuje [výplně](#fill). Nahradí všechny elementy.

```cpp
void assign(const Ty& val);
```

### <a name="parameters"></a>Parametry

`val` Hodnota pro přiřazení.

### <a name="remarks"></a>Poznámky

Členská funkce nahrazuje pořadí řízené `*this` s opakování `N` elementy hodnoty `val`.

### <a name="example"></a>Příklad

```cpp
// std__array__array_assign.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
    {
    Myarray c0 = {0, 1, 2, 3};

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

    Myarray c1;
    c1.assign(4);

// display contents " 4 4 4 4"
    for (Myarray::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

    return (0);
    }

```

```Output
0 1 2 3
4 4 4 4
```

## <a name="at"></a>  Array::AT

Přístup k elementu na zadané pozici.

```cpp
reference at(size_type off);

constexpr const_reference at(size_type off) const;
```

### <a name="parameters"></a>Parametry

`off` Pozice elementu přístup.

### <a name="remarks"></a>Poznámky

Členské funkce vrátí odkaz na element řízené sekvenci na pozici `off`. Pokud tuto pozici je neplatný, funkce vyvolá objekt třídy `out_of_range`.

### <a name="example"></a>Příklad

```cpp
// std__array__array_at.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
    {
    Myarray c0 = {0, 1, 2, 3};

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

// display odd elements " 1 3"
    std::cout << " " << c0.at(1);
    std::cout << " " << c0.at(3);
    std::cout << std::endl;

    return (0);
    }

```

## <a name="back"></a>  Array::back

Přístup k posledním elementem.

```cpp
reference back();

constexpr const_reference back() const;
```

### <a name="remarks"></a>Poznámky

Členské funkce vrátí odkaz na poslední elementu řízené sekvenci, která musí být neprázdný.

### <a name="example"></a>Příklad

```cpp
// std__array__array_back.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
    {
    Myarray c0 = {0, 1, 2, 3};

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

// display last element " 3"
    std::cout << " " << c0.back();
    std::cout << std::endl;

    return (0);
    }

```

```Output
0 1 2 3
3
```

## <a name="begin"></a>  Array::begin

Určuje začátek řízené sekvence.

```cpp
iterator begin() noexcept;
const_iterator begin() const noexcept;
```

### <a name="remarks"></a>Poznámky

Členské funkce vrátí iterator náhodný přístup tohoto body v prvním elementem pořadí (nebo jenom přesahuje za konec prázdnou sekvencí).

### <a name="example"></a>Příklad

```cpp
// std__array__array_begin.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
    {
    Myarray c0 = {0, 1, 2, 3};

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

// display first element " 0"
    Myarray::iterator it2 = c0.begin();
    std::cout << " " << *it2;
    std::cout << std::endl;

    return (0);
    }

```

```Output
0 1 2 3
0
```

## <a name="cbegin"></a>  Array::cbegin

Vrátí `const` iterator, která řeší prvním elementem v rozsahu.

```cpp
const_iterator cbegin() const noexcept;
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

## <a name="cend"></a>  Array::cend

Vrátí `const` iterator, která řeší umístění bezprostředně za posledním prvkem v rozsahu.

```cpp
const_iterator cend() const noexcept;
```

### <a name="return-value"></a>Návratová hodnota

Iterátor pro náhodný přístup, který ukazuje přesně za konec rozsahu.

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

## <a name="const_iterator"></a>  Array::const_iterator

Typ konstantního iterátoru řízené sekvence

```cpp
typedef implementation-defined const_iterator;
```

### <a name="remarks"></a>Poznámky

Popisuje typ objektu, který může sloužit jako konstantní iterator náhodný přístup pro řízené sekvenci.

### <a name="example"></a>Příklad

```cpp
// std__array__array_const_iterator.cpp
// compile with: /EHsc /W4
#include <array>
#include <iostream>

typedef std::array<int, 4> MyArray;

int main()
{
    MyArray c0 = {0, 1, 2, 3};

    // display contents " 0 1 2 3"
    std::cout << "it1:";
    for ( MyArray::const_iterator it1 = c0.begin();
          it1 != c0.end();
          ++it1 ) {
       std::cout << " " << *it1;
    }
    std::cout << std::endl;

    // display first element " 0"
    MyArray::const_iterator it2 = c0.begin();
    std::cout << "it2:";
    std::cout << " " << *it2;
    std::cout << std::endl;

    return (0);
}

```

```Output
it1: 0 1 2 3
it2: 0
```

## <a name="const_pointer"></a>  Array::const_pointer

Typ konstantního ukazatele na prvek

```cpp
typedef const Ty *const_pointer;
```

### <a name="remarks"></a>Poznámky

Popisuje typ objektu, který může sloužit jako konstantní ukazatel na elementy sekvence.

### <a name="example"></a>Příklad

```cpp
// std__array__array_const_pointer.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
    {
    Myarray c0 = {0, 1, 2, 3};

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

// display first element " 0"
    Myarray::const_pointer ptr = &*c0.begin();
    std::cout << " " << *ptr;
    std::cout << std::endl;

    return (0);
    }

```

```Output
0 1 2 3
0
```

## <a name="const_reference"></a>  Array::const_reference

Typ konstantního odkazu na prvek

```cpp
typedef const Ty& const_reference;
```

### <a name="remarks"></a>Poznámky

Popisuje typ objektu, který může sloužit jako konstantní odkaz na element řízené sekvenci.

### <a name="example"></a>Příklad

```cpp
// std__array__array_const_reference.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
    {
    Myarray c0 = {0, 1, 2, 3};

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

// display first element " 0"
    Myarray::const_reference ref = *c0.begin();
    std::cout << " " << ref;
    std::cout << std::endl;

    return (0);
    }

```

```Output
0 1 2 3
0
```

## <a name="const_reverse_iterator"></a>  Array::const_reverse_iterator

Typ konstantní zpětné iterator pro řízené sekvenci.

```cpp
typedef std::reverse_iterator<const_iterator> const_reverse_iterator;
```

### <a name="remarks"></a>Poznámky

Popisuje typ objektu, který může sloužit jako konstantní zpětné iterator pro řízené sekvenci.

### <a name="example"></a>Příklad

```cpp
// std__array__array_const_reverse_iterator.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
    {
    Myarray c0 = {0, 1, 2, 3};

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

// display last element " 3"
    Myarray::const_reverse_iterator it2 = c0.rbegin();
    std::cout << " " << *it2;
    std::cout << std::endl;

    return (0);
    }

```

```Output
0 1 2 3
3
```

## <a name="crbegin"></a>  Array::crbegin

Vrátí const iterator prvním elementem v invertovaných pole.

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>Návratová hodnota

Const reverse náhodný přístup iterator adresování prvním elementem v invertovaných pole nebo řešení, co je posledním prvkem v poli unreversed.

### <a name="remarks"></a>Poznámky

S návratovou hodnotou `crbegin`, nemůže být upraven objekt array.

### <a name="example"></a>Příklad

```cpp
// array_crbegin.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

int main( )
{
   using namespace std;
   array<int, 2> v1 = {1, 2};
   array<int, 2>::iterator v1_Iter;
   array<int, 2>::const_reverse_iterator v1_rIter;

   v1_Iter = v1.begin( );
   cout << "The first element of array is "
        << *v1_Iter << "." << endl;

   v1_rIter = v1.crbegin( );
   cout << "The first element of the reversed array is "
        << *v1_rIter << "." << endl;
}
```

```Output
The first element of array is 1.
The first element of the reversed array is 2.
```

## <a name="crend"></a>  Array::crend

Vrátí const iterator, která řeší umístění úspěšné posledním prvkem v invertovaných pole.

```cpp
const_reverse_iterator crend() const noexcept;
```

### <a name="return-value"></a>Návratová hodnota

Const reverse iterator náhodný přístup, která řeší umístění úspěšné posledním prvkem v invertovaných pole (umístění, které měl před první prvek v poli unreversed).

### <a name="remarks"></a>Poznámky

`crend` se používá s odstínech pole stejně jako [array::cend](#cend) se používá s polem.

S návratovou hodnotou `crend` (vhodně odečte), objekt pole nemůže být upraven.

`crend` dá se použít k testování na tom, jestli zpětné iterator dosáhne konce své pole.

Hodnoty vrácené `crend` by neměl být vyhodnoceny odkazy.

### <a name="example"></a>Příklad

```cpp
// array_crend.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

int main( )
{
   using namespace std;
   array<int, 2> v1 = {1, 2};
   array<int, 2>::const_reverse_iterator v1_rIter;

   for ( v1_rIter = v1.rbegin( ) ; v1_rIter != v1.rend( ) ; v1_rIter++ )
      cout << *v1_rIter << endl;
}
```

```Output
2
1
```

## <a name="data"></a>  Array::data –

Získá adresu první prvek.

```cpp
Ty *data();

const Ty *data() const;
```

### <a name="remarks"></a>Poznámky

Členské funkce zpáteční adresa první elementu v řízené sekvenci.

### <a name="example"></a>Příklad

```cpp
// std__array__array_data.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
    {
    Myarray c0 = {0, 1, 2, 3};

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

// display first element " 0"
    Myarray::pointer ptr = c0.data();
    std::cout << " " << *ptr;
    std::cout << std::endl;

    return (0);
    }

```

```Output
0 1 2 3
0
```

## <a name="difference_type"></a>  Array::difference_type

Typ vzdálenosti se znaménkem mezi dvěma prvky

```cpp
typedef std::ptrdiff_t difference_type;
```

### <a name="remarks"></a>Poznámky

Typ se znaménkem popisuje objekt, který může představovat rozdíl mezi dvěma prvky v řízené sekvenci adresy. Je synonymum pro typ `std::ptrdiff_t`.

### <a name="example"></a>Příklad

```cpp
// std__array__array_difference_type.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
    {
    Myarray c0 = {0, 1, 2, 3};

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

// display distance first-last " -4"
    Myarray::difference_type diff = c0.begin() - c0.end();
    std::cout << " " << diff;
    std::cout << std::endl;

    return (0);
    }

```

```Output
0 1 2 3
-4
```

## <a name="empty"></a>  Array::Empty

Zkouší, zda nejsou přítomny žádné prvky.

```cpp
constexpr bool empty() const;
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí hodnotu true pouze v případě `N == 0`.

### <a name="example"></a>Příklad

```cpp
// std__array__array_empty.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
    {
    Myarray c0 = {0, 1, 2, 3};

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

// display whether c0 is empty " false"
    std::cout << std::boolalpha << " " << c0.empty();
    std::cout << std::endl;

    std::array<int, 0> c1;

// display whether c1 is empty " true"
    std::cout << std::boolalpha << " " << c1.empty();
    std::cout << std::endl;

    return (0);
    }

```

```Output
0 1 2 3
false
true
```

## <a name="end"></a>  Array::end

Určuje konec řízené sekvence.

```cpp
reference end();

const_reference end() const;
```

### <a name="remarks"></a>Poznámky

Členské funkce vrátí iterator náhodný přístup tohoto body právě přesahuje za konec sekvenci.

### <a name="example"></a>Příklad

```cpp
// std__array__array_end.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
    {
    Myarray c0 = {0, 1, 2, 3};

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

// display last element " 3"
    Myarray::iterator it2 = c0.end();
    std::cout << " " << *--it2;
    std::cout << std::endl;

    return (0);
    }

```

```Output
0 1 2 3
3
```

## <a name="fill"></a>  Array::Fill

Pole se vymaže a zkopíruje zadaných elementů prázdné pole.

```cpp
void fill(const Type& val);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|-|-|
|`val`|Hodnota elementu vkládání do pole.|

### <a name="remarks"></a>Poznámky

`fill` nahrazuje každý element pole se zadanou hodnotou.

### <a name="example"></a>Příklad

```cpp
// array_fill.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

int main( )
{
   using namespace std;
   array<int, 2> v1 = {1, 2};
   array<int, 2>::iterator iter;

   cout << "v1 = " ;
   for (iter = v1.begin(); iter != v1.end(); iter++)
      cout << *iter << " ";
   cout << endl;

   v1.fill(3);
   cout << "v1 = " ;
   for (iter = v1.begin(); iter != v1.end(); iter++)
      cout << *iter << " ";
   cout << endl;
}
```

## <a name="front"></a>  Array::front

Přístup k první prvek.

```cpp
reference front();

constexpr const_reference front() const;
```

### <a name="remarks"></a>Poznámky

Členské funkce vrátí odkaz na první prvek řízené sekvenci, která musí být neprázdný.

### <a name="example"></a>Příklad

```cpp
// std__array__array_front.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
    {
    Myarray c0 = {0, 1, 2, 3};

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

// display first element " 0"
    std::cout << " " << c0.front();
    std::cout << std::endl;

    return (0);
    }

```

```Output
0 1 2 3
0
```

## <a name="iterator"></a>  Array::iterator

Typ iterátoru řízené sekvence

```cpp
typedef implementation-defined iterator;
```

### <a name="remarks"></a>Poznámky

Popisuje typ objektu, který může sloužit jako iterator náhodný přístup pro řízené sekvenci.

### <a name="example"></a>Příklad

```cpp
// std__array__array_iterator.cpp
// compile with: /EHsc /W4
#include <array>
#include <iostream>

typedef std::array<int, 4> MyArray;

int main()
{
    MyArray c0 = {0, 1, 2, 3};

    // display contents " 0 1 2 3"
    std::cout << "it1:";
    for ( MyArray::iterator it1 = c0.begin();
          it1 != c0.end();
          ++it1 ) {
       std::cout << " " << *it1;
    }
    std::cout << std::endl;

    // display first element " 0"
    MyArray::iterator it2 = c0.begin();
    std::cout << "it2:";
    std::cout << " " << *it2;
    std::cout << std::endl;

    return (0);
}

```

```Output
it1: 0 1 2 3

it2: 0

```

## <a name="max_size"></a>  Array::max_size

Spočítá počet prvků.

```cpp
constexpr size_type max_size() const;
```

### <a name="remarks"></a>Poznámky

Členské funkce vrátí hodnotu `N`.

### <a name="example"></a>Příklad

```cpp
// std__array__array_max_size.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
    {
    Myarray c0 = {0, 1, 2, 3};

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

// display (maximum) size " 4"
    std::cout << " " << c0.max_size();
    std::cout << std::endl;

    return (0);
    }

```

```Output
0 1 2 3
4
```

## <a name="op_at"></a>  Array::Operator]

Přístup k elementu na zadané pozici.

```cpp
reference operator[](size_type off);

constexpr const_reference operator[](size_type off) const;
```

### <a name="parameters"></a>Parametry

`off` Pozice elementu přístup.

### <a name="remarks"></a>Poznámky

Členské funkce vrátí odkaz na element řízené sekvenci na pozici `off`. Pokud tuto pozici je neplatná, není definován chování.

Je také třetí [získat](array-functions.md#get) funkce, které jsou k dispozici k získání odkazu na element `array`.

### <a name="example"></a>Příklad

```cpp
// std__array__array_operator_sub.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
    {
    Myarray c0 = {0, 1, 2, 3};

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

// display odd elements " 1 3"
    std::cout << " " << c0[1];
    std::cout << " " << c0[3];
    std::cout << std::endl;

    return (0);
    }

```

```Output
0 1 2 3
1 3
```

## <a name="op_eq"></a>  Array::Operator =

Nahradí řízené sekvenci.

```cpp
array <Value>%  operator=(array <Value>% right);
```

### <a name="parameters"></a>Parametry

správném kontejneru pro kopírování.

### <a name="remarks"></a>Poznámky

Operátor členů přiřadí každý element `right` do odpovídající elementu řízené sekvenci, vrátí `*this`. Můžete použít k nahrazení řízené sekvenci kopii v řízené sekvenci `right`.

### <a name="example"></a>Příklad

```cpp
// std__array__array_operator_as.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
    {
    Myarray c0 = {0, 1, 2, 3};

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

    Myarray c1;
    c1 = c0;

// display copied contents " 0 1 2 3"
    for (Myarray::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

    return (0);
    }

```

```Output
0 1 2 3
0 1 2 3
```

## <a name="pointer"></a>  Array::Pointer

Typ ukazatele na prvek

```cpp
typedef Ty *pointer;
```

### <a name="remarks"></a>Poznámky

Popisuje typ objektu, který může sloužit jako ukazatel na elementy sekvence.

### <a name="example"></a>Příklad

```cpp
// std__array__array_pointer.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
    {
    Myarray c0 = {0, 1, 2, 3};

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

// display first element " 0"
    Myarray::pointer ptr = &*c0.begin();
    std::cout << " " << *ptr;
    std::cout << std::endl;

    return (0);
    }

```

```Output
0 1 2 3
0
```

## <a name="rbegin"></a>  Array::rbegin

Označuje začátek odstínech řízené sekvenci.

```cpp
reverse_iterator rbegin()noexcept;
const_reverse_iterator rbegin() const noexcept;
```

### <a name="remarks"></a>Poznámky

Členské funkce vrátí zpětné iterator této body právě přesahuje za konec řízené sekvenci. Proto označí začátek zpětné pořadí.

### <a name="example"></a>Příklad

```cpp
// std__array__array_rbegin.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
    {
    Myarray c0 = {0, 1, 2, 3};

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

// display last element " 3"
    Myarray::const_reverse_iterator it2 = c0.rbegin();
    std::cout << " " << *it2;
    std::cout << std::endl;

    return (0);
    }

```

```Output
0 1 2 3
3
```

## <a name="reference"></a>  Array::Reference

Typ odkazu na prvek

```cpp
typedef Ty& reference;
```

### <a name="remarks"></a>Poznámky

Popisuje typ objektu, který může sloužit jako odkaz na element řízené sekvenci.

### <a name="example"></a>Příklad

```cpp
// std__array__array_reference.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
    {
    Myarray c0 = {0, 1, 2, 3};

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

// display first element " 0"
    Myarray::reference ref = *c0.begin();
    std::cout << " " << ref;
    std::cout << std::endl;

    return (0);
    }

```

```Output
0 1 2 3
0
```

## <a name="rend"></a>  Array::rend

Označuje konec odstínech řízené sekvenci.

```cpp
reverse_iterator rend()noexcept;
const_reverse_iterator rend() const noexcept;
```

### <a name="remarks"></a>Poznámky

Členské funkce vrátí zpětné iterator této body v prvním elementem pořadí (nebo jenom přesahuje za konec prázdnou sekvencí)). Proto označí konec zpětného pořadí.

### <a name="example"></a>Příklad

```cpp
// std__array__array_rend.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
    {
    Myarray c0 = {0, 1, 2, 3};

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

// display first element " 0"
    Myarray::const_reverse_iterator it2 = c0.rend();
    std::cout << " " << *--it2;
    std::cout << std::endl;

    return (0);
    }

```

```Output
0 1 2 3
0
```

## <a name="reverse_iterator"></a>  Array::reverse_iterator

Typ zpětné iterator pro řízené sekvenci.

```cpp
typedef std::reverse_iterator<iterator> reverse_iterator;
```

### <a name="remarks"></a>Poznámky

Popisuje typ objektu, který může sloužit jako reverzní iterator pro řízené sekvenci.

### <a name="example"></a>Příklad

```cpp
// std__array__array_reverse_iterator.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
    {
    Myarray c0 = {0, 1, 2, 3};

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

// display last element " 3"
    Myarray::reverse_iterator it2 = c0.rbegin();
    std::cout << " " << *it2;
    std::cout << std::endl;

    return (0);
    }

```

```Output
0 1 2 3
3
```

## <a name="size"></a>  Array::size

Spočítá počet prvků.

```cpp
constexpr size_type size() const;
```

### <a name="remarks"></a>Poznámky

Členské funkce vrátí hodnotu `N`.

### <a name="example"></a>Příklad

```cpp
// std__array__array_size.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
    {
    Myarray c0 = {0, 1, 2, 3};

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

// display size " 4"
    std::cout << " " << c0.size();
    std::cout << std::endl;

    return (0);
    }

```

```Output
0 1 2 3
4
```

## <a name="size_type"></a>  Array::size_type

Typ je nepodepsané vzdálenost mezi dvěma elementu.

```cpp
typedef std::size_t size_type;
```

### <a name="remarks"></a>Poznámky

Zadejte celé číslo bez znaménka popisuje objekt, který může představovat délka žádné řízené sekvenci. Je synonymum pro typ `std::size_t`.

### <a name="example"></a>Příklad

```cpp
// std__array__array_size_type.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
    {
    Myarray c0 = {0, 1, 2, 3};

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

// display distance last-first " 4"
    Myarray::size_type diff = c0.end() - c0.begin();
    std::cout << " " << diff;
    std::cout << std::endl;

    return (0);
    }

```

```Output
0 1 2 3
4
```

## <a name="swap"></a>  Array::swap

Zamění obsah toto pole s jiné pole.

```cpp
void swap(array& right);
```

### <a name="parameters"></a>Parametry

`right` Pole k výměně obsahu s.

### <a name="remarks"></a>Poznámky

Členská funkce prohození řízené pořadí mezi `*this` a `right`. Provede několika element přiřazení a volá konstruktor úměrná `N`.

Je také třetí [swap](array-functions.md#swap) funkce, které jsou k dispozici pro swap dva `array` instance.

### <a name="example"></a>Příklad

```cpp
// std__array__array_swap.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
    {
    Myarray c0 = {0, 1, 2, 3};

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

    Myarray c1 = {4, 5, 6, 7};
    c0.swap(c1);

// display swapped contents " 4 5 6 7"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

    swap(c0, c1);

// display swapped contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

    return (0);
    }

```

```Output
0 1 2 3
4 5 6 7
0 1 2 3
```

## <a name="value_type"></a>  Array::value_type

Typ prvku

```cpp
typedef Ty value_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro parametr šablony `Ty`.

### <a name="example"></a>Příklad

```cpp
// std__array__array_value_type.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
    {
    Myarray c0 = {0, 1, 2, 3};

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        {
        Myarray::value_type val = *it;
        std::cout << " " << val;
        }
    std::cout << std::endl;

    return (0);
    }

```

```Output
0 1 2 3
0 1 2 3
```

## <a name="see-also"></a>Viz také

[\<pole >](../standard-library/array.md)<br/>
