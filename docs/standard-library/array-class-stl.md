---
title: Array – třída (standardní knihovna C++) | Dokumentace Microsoftu
ms.date: 11/04/2016
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
ms.openlocfilehash: fdc3705980ac8f763e0438f19920148437e7ed27
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62377501"
---
# <a name="array-class-c-standard-library"></a>Array – třída (standardní knihovna C++)

Popisuje objekt, který řídí sekvence délka `N` elementů typu `Ty`. Sekvence se ukládá jako pole `Ty`obsažený v `array<Ty, N>` objektu.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty, std::size_t N>
class array;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|-|-|
|`Ty`|Typ prvku|
|`N`|Počet prvků.|

## <a name="members"></a>Členové

|Definice typu|Popis|
|-|-|
|[const_iterator](#const_iterator)|Typ konstantního iterátoru řízené sekvence|
|[const_pointer](#const_pointer)|Typ konstantního ukazatele na prvek|
|[const_reference](#const_reference)|Typ konstantního odkazu na prvek|
|[const_reverse_iterator](#const_reverse_iterator)|Typ konstantního zpětného iterátoru řízené sekvence.|
|[difference_type](#difference_type)|Typ vzdálenosti se znaménkem mezi dvěma prvky|
|[iterator](#iterator)|Typ iterátoru řízené sekvence|
|[pointer](#pointer)|Typ ukazatele na prvek|
|[Referenční dokumentace](#reference)|Typ odkazu na prvek|
|[reverse_iterator](#reverse_iterator)|Typ "reverse iterator" pro řízenou sekvenci.|
|[size_type](#size_type)|Typ vzdálenosti bez znaménka mezi dvěma prvky|
|[value_type](#value_type)|Typ prvku|

|Členská funkce|Popis|
|-|-|
|[Pole](#array)|Vytvoří objekt typu pole.|
|[assign](#assign)|Nahradí všechny elementy.|
|[at](#at)|Přistupuje k element na určené pozici.|
|[Zpět](#back)|Přistupuje k poslední prvek.|
|[začít](#begin)|Určuje začátek řízené sekvence.|
|[cbegin](#cbegin)|Vrátí konstantní iterátor náhodného přístupu na první prvek v poli.|
|[cend](#cend)|Vrátí konstantní iterátor náhodného přístupu, na kterou odkazuje hned za koncem tohoto pole.|
|[crbegin](#crbegin)|Vrátí konstantní iterátor na první prvek v obráceném objektu array.|
|[crend](#crend)|Vrátí konstantní iterátor za účelem obráceném objektu array.|
|[data](#data)|Získá adresu prvního prvku.|
|[prázdný](#empty)|Testy, jestli prvky jsou k dispozici.|
|[ukončení](#end)|Určuje konec řízené sekvence.|
|[Výplň](#fill)|Nahradí všechny prvky se zadanou hodnotou.|
|[Přední](#front)|Přistupuje k první prvek.|
|[max_size](#max_size)|Spočítá počet prvků.|
|[rbegin](#rbegin)|Určuje začátek řízené obrácené sekvenci.|
|[rend –](#rend)|Určuje konec řízené obrácené sekvenci.|
|[Velikost](#size)|Spočítá počet prvků.|
|[swap](#swap)|Zamění obsah dvou kontejnerů.|

|Operátor|Popis|
|-|-|
|[Array::Operator =](#op_eq)|Nahradí řízené sekvence.|
|[Array::Operator\[\]](#op_at)|Přistupuje k element na určené pozici.|

## <a name="remarks"></a>Poznámky

Typ má výchozí konstruktor `array()` a operátor přiřazení výchozí `operator=`a splňuje požadavky na `aggregate`. Proto objekty typu `array<Ty, N>` lze inicializovat pomocí inicializátoru agregace. Například

```cpp
array<int, 4> ai = { 1, 2, 3 };
```

Vytvoří objekt `ai` , který obsahuje čtyři celočíselné hodnoty, inicializuje první tři prvky, které mají hodnoty 1, 2 a 3, v uvedeném pořadí a inicializuje čtvrtý prvek na hodnotu 0.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<pole >

**Namespace:** std

## <a name="array"></a>  Array::Array –

Vytvoří objekt typu pole.

```cpp
array();

array(const array& right);
```

### <a name="parameters"></a>Parametry

*doprava*<br/>
Objekt nebo rozsahu pro vložení.

### <a name="remarks"></a>Poznámky

Výchozí konstruktor `array()` opustí řízené sekvence neinicializované (nebo inicializované ve výchozím nastavení). Použijete ji k určení neinicializované řízené sekvence.

Kopírovací konstruktor `array(const array& right)` inicializuje řízené sekvence s pořadím [*správné*`.begin()`, *správné*`.end()`). Můžete ji použít k určení počáteční řízené sekvence, který je kopii sekvence řízenou parametrem objektu array *správné*.

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

*Val*<br/>
Hodnota, kterou chcete přiřadit.

### <a name="remarks"></a>Poznámky

Členská funkce se nahradí sekvence řízenou parametrem `*this` s opakování `N` prvků hodnoty *val*.

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

Přistupuje k element na určené pozici.

```cpp
reference at(size_type off);

constexpr const_reference at(size_type off) const;
```

### <a name="parameters"></a>Parametry

*off*<br/>
Pozice prvku přístup.

### <a name="remarks"></a>Poznámky

Členské funkce vrátí odkaz na prvek řízené sekvence na pozici *vypnout*. Je-li této pozici platný, funkce vyvolá objekt třídy `out_of_range`.

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

Přistupuje k poslední prvek.

```cpp
reference back();

constexpr const_reference back() const;
```

### <a name="remarks"></a>Poznámky

Členské funkce vrátí odkaz na poslední prvek řízené sekvence, která musí být neprázdný.

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

Členské funkce vrátí iterátor náhodného přístupu, na kterou odkazuje na první prvek pořadí (nebo přesně za konec k prázdné sekvenci).

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

Vrátí **const** iterátor adresující první prvek v rozsahu.

```cpp
const_iterator cbegin() const noexcept;
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

## <a name="cend"></a>  Array::cend

Vrátí **const** iterátor adresující umístění hned za posledním prvkem v rozsahu.

```cpp
const_iterator cend() const noexcept;
```

### <a name="return-value"></a>Návratová hodnota

Iterátor pro náhodný přístup, který ukazuje přesně za konec rozsahu.

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

## <a name="const_iterator"></a>  Array::const_iterator

Typ konstantního iterátoru řízené sekvence

```cpp
typedef implementation-defined const_iterator;
```

### <a name="remarks"></a>Poznámky

Typ popisuje objekt, který může sloužit jako konstantní iterátor s náhodným přístupem řízené sekvence.

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

Typ popisuje objekt, který může sloužit jako konstantní ukazatel na elementy sekvence.

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

Typ popisuje objekt, který může sloužit jako konstantní odkaz na prvek řízené sekvence.

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

Typ konstantního zpětného iterátoru řízené sekvence.

```cpp
typedef std::reverse_iterator<const_iterator> const_reverse_iterator;
```

### <a name="remarks"></a>Poznámky

Typ popisuje objekt, který může sloužit jako konstantní zpětného iterátoru řízené sekvence.

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

Vrátí konstantní iterátor na první prvek v obráceném objektu array.

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>Návratová hodnota

Reverse konstantní iterátor adresující první prvek v obráceném objektu pole nebo adresování, co bylo posledním prvkem v neobráceném pole s náhodným přístupem.

### <a name="remarks"></a>Poznámky

S návratovou hodnotou `crbegin`, objekt pole nelze změnit.

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

Vrátí konstantní iterátor adresující umístění následující po posledním prvku v obráceném objektu array.

```cpp
const_reverse_iterator crend() const noexcept;
```

### <a name="return-value"></a>Návratová hodnota

Const reverse iterátor s náhodným přístupem, který adresuje umístění následující po posledním prvku v obráceném objektu pole (umístění, ke které došlo před první prvek v neobráceném pole).

### <a name="remarks"></a>Poznámky

`crend` se používá s obrácený pole stejně jako [array::cend](#cend) se používá s polem.

S návratovou hodnotou `crend` (vhodně snížen), pole objektu nelze upravit.

`crend` slouží k otestování pro Určuje, zda zpětný iterátor dosáhl konce jeho pole.

Hodnota vrácená `crend` by neměla být dereferencována.

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

Získá adresu prvního prvku.

```cpp
Ty *data();

const Ty *data() const;
```

### <a name="remarks"></a>Poznámky

Členské funkce vrátí adresu prvního prvku v řízené sekvenci.

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

## <a name="difference_type"></a>  array::difference_type

Typ vzdálenosti se znaménkem mezi dvěma prvky

```cpp
typedef std::ptrdiff_t difference_type;
```

### <a name="remarks"></a>Poznámky

Typ celé číslo se znaménkem, který popisuje objekt, který může představovat rozdíl mezi adresami dva prvky řízené sekvence. Je synonymum pro typ `std::ptrdiff_t`.

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

Členské funkce vrátí iterátor náhodného přístupu, na kterou odkazuje přesně za konec sekvence.

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

Vymaže pole a zkopíruje do prázdné pole zadané elementy.

```cpp
void fill(const Type& val);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|-|-|
|*Val*|Hodnota prvku vloženého do pole.|

### <a name="remarks"></a>Poznámky

`fill` nahrazuje každý prvek pole se zadanou hodnotou.

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

Přistupuje k první prvek.

```cpp
reference front();

constexpr const_reference front() const;
```

### <a name="remarks"></a>Poznámky

Členské funkce vrátí odkaz na první prvek řízené sekvence, která musí být neprázdný.

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

Typ popisuje objekt, který může sloužit jako iterátor náhodného přístupu řízené sekvence.

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

Členská funkce vrátí `N`.

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

Přistupuje k element na určené pozici.

```cpp
reference operator[](size_type off);

constexpr const_reference operator[](size_type off) const;
```

### <a name="parameters"></a>Parametry

*off*<br/>
Pozice prvku přístup.

### <a name="remarks"></a>Poznámky

Členské funkce vrátí odkaz na prvek řízené sekvence na pozici *vypnout*. Je-li této pozice neplatná, není chování definováno.

Existuje také třetí [získat](array-functions.md#get) funkce, které jsou k dispozici k získání odkazu na element **pole**.

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

Nahradí řízené sekvence.

```cpp
array<Value> operator=(array<Value> right);
```

### <a name="parameters"></a>Parametry

*doprava*<br/>
Kontejner pro kopírování.

### <a name="remarks"></a>Poznámky

Členský operátor přiřadí každý prvek *správné* odpovídající element řízené sekvence vrátí `*this`. Můžete použít k nahraďte kopii řízené sekvence v řízené sekvenci *správné*.

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

Typ popisuje objekt, který může sloužit jako ukazatel na elementy sekvence.

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

Určuje začátek řízené obrácené sekvenci.

```cpp
reverse_iterator rbegin()noexcept;
const_reverse_iterator rbegin() const noexcept;
```

### <a name="remarks"></a>Poznámky

Členské funkce vrátí "reverse iterator", na kterou odkazuje přesně za konec řízené sekvence. Proto určuje začátek opačném pořadí.

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

Typ popisuje objekt, který může sloužit jako odkaz na prvek řízené sekvence.

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

Určuje konec řízené obrácené sekvenci.

```cpp
reverse_iterator rend()noexcept;
const_reverse_iterator rend() const noexcept;
```

### <a name="remarks"></a>Poznámky

Členské funkce vrátí "reverse iterator", na kterou odkazuje na první prvek pořadí (nebo přesně za konec k prázdné sekvenci)). Proto označuje konec opačném pořadí.

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

Typ "reverse iterator" pro řízenou sekvenci.

```cpp
typedef std::reverse_iterator<iterator> reverse_iterator;
```

### <a name="remarks"></a>Poznámky

Typ popisuje objekt, který může sloužit jako "reverse iterator" pro řízenou sekvenci.

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

Členská funkce vrátí `N`.

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

Typ vzdálenosti bez znaménka mezi dvěma elementu.

```cpp
typedef std::size_t size_type;
```

### <a name="remarks"></a>Poznámky

Typ celé číslo bez znaménka, který popisuje objekt, který může představovat délka jakékoli řízené sekvence. Je synonymum pro typ `std::size_t`.

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

Zamění obsah tohoto pole s jiným polem.

```cpp
void swap(array& right);
```

### <a name="parameters"></a>Parametry

*doprava*<br/>
Pole k výměně obsahu s.

### <a name="remarks"></a>Poznámky

Členská funkce Zamění řízené sekvence mezi `*this` a *správné*. Provede několik přiřazení elementu a konstruktoru volá úměrný `N`.

Existuje také třetí [prohození](array-functions.md#swap) funkce, které jsou k dispozici pro prohození dvě **pole** instancí.

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

## <a name="see-also"></a>Viz také:

[\<array>](../standard-library/array.md)<br/>
