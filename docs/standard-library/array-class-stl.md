---
title: třída pole (standardní knihovna Jazyka C++) | Dokumenty společnosti Microsoft
ms.date: 11/13/2019
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
ms.openlocfilehash: 90c68d00475a622ec89b81cc86639f63b1190d02
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364945"
---
# <a name="array-class-c-standard-library"></a>array – třída (standardní knihovna C++)

Popisuje objekt, který řídí posloupnost délky `N` prvků typu `Ty`. Sekvence je uložena jako `Ty`pole , `array<Ty, N>` obsažené v objektu.

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
|[const_reverse_iterator](#const_reverse_iterator)|Typ konstantní zpětného iterátoru pro řízenou sekvenci.|
|[difference_type](#difference_type)|Typ vzdálenosti se znaménkem mezi dvěma prvky|
|[Iterace](#iterator)|Typ iterátoru řízené sekvence|
|[ukazatel](#pointer)|Typ ukazatele na prvek|
|[Odkaz](#reference)|Typ odkazu na prvek|
|[reverse_iterator](#reverse_iterator)|Typ zpětného iterátoru pro řízenou sekvenci.|
|[size_type](#size_type)|Typ vzdálenosti bez znaménka mezi dvěma prvky|
|[value_type](#value_type)|Typ prvku|

|Členská funkce|Popis|
|-|-|
|[Pole](#array)|Vytvoří objekt pole.|
|[Přiřadit](#assign)|(Zastaralé. Použijte `fill`.) Nahradí všechny prvky.|
|[Na](#at)|Přistupuje k prvku na zadané pozici.|
|[Zpět](#back)|Přistupuje k poslednímu prvku.|
|[Začít](#begin)|Určuje začátek řízené sekvence.|
|[cbegin](#cbegin)|Vrátí random-access const iterator k prvnímu prvku v poli.|
|[cend](#cend)|Vrátí random-access const iterator, který odkazuje těsně za konec pole.|
|[crbegin](#crbegin)|Vrátí const iterátor na první prvek v obráceném poli.|
|[crend](#crend)|Vrátí const iterátor na konec obráceného pole.|
|[Dat](#data)|Získá adresu prvního prvku.|
|[empty](#empty)|Testuje, zda jsou přítomny prvky.|
|[Konec](#end)|Určuje konec řízené sekvence.|
|[fill](#fill)|Nahradí všechny prvky zadanou hodnotou.|
|[Přední](#front)|Přistupuje k prvnímu prvku.|
|[max_size](#max_size)|Spočítá počet prvků.|
|[rbegin](#rbegin)|Označuje začátek obrácené řízené sekvence.|
|[rend](#rend)|Označuje konec obrácené řízené sekvence.|
|[Velikost](#size)|Spočítá počet prvků.|
|[Swap](#swap)|Zamění obsah dvou kontejnerů.|

|Operátor|Popis|
|-|-|
|[pole::operátor=](#op_eq)|Nahradí řízenou sekvenci.|
|[pole::operátor\[\]](#op_at)|Přistupuje k prvku na zadané pozici.|

## <a name="remarks"></a>Poznámky

Typ má výchozí konstruktor `array()` a výchozí `operator=`operátor přiřazení a splňuje `aggregate`požadavky pro . Proto objekty `array<Ty, N>` typu lze inicializovat pomocí agregační inicializátor. Například:

```cpp
array<int, 4> ai = { 1, 2, 3 };
```

vytvoří objekt, `ai` který obsahuje čtyři celé hodnoty, inicializuje první tři prvky na hodnoty 1, 2 a 3 a inicializuje čtvrtý prvek na 0.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<> pole

**Obor názvů:** std

## <a name="arrayarray"></a><a name="array"></a>pole::pole

Vytvoří objekt pole.

```cpp
array();

array(const array& right);
```

### <a name="parameters"></a>Parametry

*Právo*\
Objekt nebo oblast, která chcete vložit.

### <a name="remarks"></a>Poznámky

Výchozí konstruktor `array()` ponechá řízenou sekvenci neinicializovanou (nebo výchozí inicializovanou). Slouží k určení neinicializované řízené sekvence.

Konstruktor `array(const array& right)` kopie inicializuje řízenou sekvenci sekvencí [ vpravo ,*vpravo).*`.begin()` *right*`.end()` Slouží k určení počáteční řízené sekvence, která je kopií sekvence řízené objektem pole *vpravo*.

### <a name="example"></a>Příklad

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    typedef std::array<int, 4> Myarray;

    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    Myarray c1(c0);

    // display contents " 0 1 2 3"
    for (const auto& it : c1)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
0 1 2 3
```

## <a name="arrayassign"></a><a name="assign"></a>pole::přiřadit

Zastaralé v jazyce C++11, nahrazeno [výplní](#fill). Nahradí všechny prvky.

## <a name="arrayat"></a><a name="at"></a>pole::at

Přistupuje k prvku na zadané pozici.

```cpp
reference at(size_type off);

constexpr const_reference at(size_type off) const;
```

### <a name="parameters"></a>Parametry

*vypnuto*\
Pozice prvku pro přístup.

### <a name="remarks"></a>Poznámky

Členské funkce vrátí odkaz na prvek řízené sekvence při *vypnuté*poloze . Pokud je tato pozice neplatná, funkce `out_of_range`vyvolá objekt třídy .

### <a name="example"></a>Příklad

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    // display odd elements " 1 3"
    std::cout << " " << c0.at(1);
    std::cout << " " << c0.at(3);
    std::cout << std::endl;

    return (0);
}
```

## <a name="arrayback"></a><a name="back"></a>pole::zpět

Přistupuje k poslednímu prvku.

```cpp
reference back();

constexpr const_reference back() const;
```

### <a name="remarks"></a>Poznámky

Členské funkce vrátí odkaz na poslední prvek řízené sekvence, který musí být neprázdný.

### <a name="example"></a>Příklad

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
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

## <a name="arraybegin"></a><a name="begin"></a>pole::begin

Určuje začátek řízené sekvence.

```cpp
iterator begin() noexcept;
const_iterator begin() const noexcept;
```

### <a name="remarks"></a>Poznámky

Členské funkce vrátí iterátor náhodného přístupu, který odkazuje na první prvek sekvence (nebo těsně za koncem prázdné sekvence).

### <a name="example"></a>Příklad

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
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

## <a name="arraycbegin"></a><a name="cbegin"></a>pole::cbegin

Vrátí **const** iterator, který řeší první prvek v rozsahu.

```cpp
const_iterator cbegin() const noexcept;
```

### <a name="return-value"></a>Návratová hodnota

**Const** random-access iterátor, který odkazuje na první prvek rozsahu nebo umístění těsně za koncem prázdné oblasti `cbegin() == cend()`(pro prázdný rozsah).

### <a name="remarks"></a>Poznámky

S vrácenou `cbegin`hodnotou , prvky v rozsahu nelze změnit.

Tuto člennou funkci můžete použít `begin()` místo členské funkce k `const_iterator`zajištění, že vrácená hodnota je . Obvykle se používá ve spojení s klíčovým slovem [automatického](../cpp/auto-cpp.md) odpočtu typu, jak je znázorněno v následujícím příkladu. V příkladu `Container` zvažte upravitelné (non-const) kontejner jakéhokoli druhu, `cbegin()`který podporuje **const** `begin()` a .

```cpp
auto i1 = Container.begin();
// i1 is Container<T>::iterator
auto i2 = Container.cbegin();

// i2 is Container<T>::const_iterator
```

## <a name="arraycend"></a><a name="cend"></a>pole::cend

Vrátí **const** iterator, který řeší umístění těsně za poslední prvek v rozsahu.

```cpp
const_iterator cend() const noexcept;
```

### <a name="return-value"></a>Návratová hodnota

Iterátor pro náhodný přístup, který ukazuje přesně za konec rozsahu.

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

## <a name="arrayconst_iterator"></a><a name="const_iterator"></a>pole::const_iterator

Typ konstantního iterátoru řízené sekvence

```cpp
typedef implementation-defined const_iterator;
```

### <a name="remarks"></a>Poznámky

Typ popisuje objekt, který může sloužit jako konstantní random-access iterátor pro řízené sekvence.

### <a name="example"></a>Příklad

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> MyArray;

int main()
{
    MyArray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    std::cout << "it1:";
    for (MyArray::const_iterator it1 = c0.begin();
        it1 != c0.end();
        ++it1) {
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

## <a name="arrayconst_pointer"></a><a name="const_pointer"></a>pole::const_pointer

Typ konstantního ukazatele na prvek

```cpp
typedef const Ty *const_pointer;
```

### <a name="remarks"></a>Poznámky

Typ popisuje objekt, který může sloužit jako konstantní ukazatel na prvky sekvence.

### <a name="example"></a>Příklad

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
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

## <a name="arrayconst_reference"></a><a name="const_reference"></a>pole::const_reference

Typ konstantního odkazu na prvek

```cpp
typedef const Ty& const_reference;
```

### <a name="remarks"></a>Poznámky

Typ popisuje objekt, který může sloužit jako konstantní odkaz na prvek řízené sekvence.

### <a name="example"></a>Příklad

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
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

## <a name="arrayconst_reverse_iterator"></a><a name="const_reverse_iterator"></a>pole::const_reverse_iterator

Typ konstantní zpětného iterátoru pro řízenou sekvenci.

```cpp
typedef std::reverse_iterator<const_iterator> const_reverse_iterator;
```

### <a name="remarks"></a>Poznámky

Typ popisuje objekt, který může sloužit jako konstantní reverzní iterátor pro řízené sekvence.

### <a name="example"></a>Příklad

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
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

## <a name="arraycrbegin"></a><a name="crbegin"></a>pole::crbegin

Vrátí const iterátor na první prvek v obráceném poli.

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>Návratová hodnota

Const reverzní random-access iterátor adresování první prvek v obrácené pole nebo adresování co byl poslední prvek v unreverse pole.

### <a name="remarks"></a>Poznámky

S vrácenou `crbegin`hodnotou aplikace nelze objekt pole změnit.

### <a name="example"></a>Příklad

```cpp
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

## <a name="arraycrend"></a><a name="crend"></a>pole::crend

Vrátí const iterátor, který řeší umístění, které následuje poslední prvek v obráceném poli.

```cpp
const_reverse_iterator crend() const noexcept;
```

### <a name="return-value"></a>Návratová hodnota

Const reverzní random-access iterátor, který řeší umístění následující poslední prvek v obráceném poli (umístění, které předcházelo první prvek v unreverse pole).

### <a name="remarks"></a>Poznámky

`crend`se používá s obráceným polem stejně jako [pole::cend](#cend) se používá s polem.

S návratovou `crend` hodnotou (vhodně snížena), objekt pole nelze změnit.

`crend`lze použít k testování, zda zpětný iterátor dosáhl konce svého pole.

Hodnota vrácená `crend` by neměla být odkazována.

### <a name="example"></a>Příklad

```cpp
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

## <a name="arraydata"></a><a name="data"></a>pole::data

Získá adresu prvního prvku.

```cpp
Ty *data();

const Ty *data() const;
```

### <a name="remarks"></a>Poznámky

Členské funkce vrátí adresu prvního prvku v řízené sekvenci.

### <a name="example"></a>Příklad

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
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

## <a name="arraydifference_type"></a><a name="difference_type"></a>pole::difference_type

Typ vzdálenosti se znaménkem mezi dvěma prvky

```cpp
typedef std::ptrdiff_t difference_type;
```

### <a name="remarks"></a>Poznámky

Typ podepsaného celého čísla popisuje objekt, který může představovat rozdíl mezi adresami libovolných dvou prvků v řízené sekvenci. Je synonymem pro `std::ptrdiff_t`typ .

### <a name="example"></a>Příklad

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
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

## <a name="arrayempty"></a><a name="empty"></a>pole::prázdné

Zkouší, zda nejsou přítomny žádné prvky.

```cpp
constexpr bool empty() const;
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí `N == 0`hodnotu true pouze v případě, že .

### <a name="example"></a>Příklad

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
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

## <a name="arrayend"></a><a name="end"></a>pole::konec

Určuje konec řízené sekvence.

```cpp
reference end();

const_reference end() const;
```

### <a name="remarks"></a>Poznámky

Členské funkce vrátí random-access iterátor, který odkazuje těsně za konec sekvence.

### <a name="example"></a>Příklad

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
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

## <a name="arrayfill"></a><a name="fill"></a>pole::výplň

Vymaže pole a zkopíruje zadané prvky do prázdného pole.

```cpp
void fill(const Type& val);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|-|-|
|*Val*|Hodnota prvku, který je vložen do pole.|

### <a name="remarks"></a>Poznámky

`fill`nahradí každý prvek pole zadanou hodnotou.

### <a name="example"></a>Příklad

```cpp
#include <array>
#include <iostream>

int main()
{
    using namespace std;
    array<int, 2> v1 = { 1, 2 };

    cout << "v1 = ";
    for (const auto& it : v1)
    {
        std::cout << " " << it;
    }
    cout << endl;

    v1.fill(3);
    cout << "v1 = ";
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    cout << endl;
}
```

## <a name="arrayfront"></a><a name="front"></a>pole::přední

Přistupuje k prvnímu prvku.

```cpp
reference front();

constexpr const_reference front() const;
```

### <a name="remarks"></a>Poznámky

Členské funkce vrátí odkaz na první prvek řízené sekvence, který musí být neprázdný.

### <a name="example"></a>Příklad

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
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

## <a name="arrayiterator"></a><a name="iterator"></a>pole::iterátor

Typ iterátoru řízené sekvence

```cpp
typedef implementation-defined iterator;
```

### <a name="remarks"></a>Poznámky

Typ popisuje objekt, který může sloužit jako iterátor náhodného přístupu pro řízenou sekvenci.

### <a name="example"></a>Příklad

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> MyArray;

int main()
{
    MyArray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    std::cout << "it1:";
    for (MyArray::iterator it1 = c0.begin();
        it1 != c0.end();
        ++it1) {
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

## <a name="arraymax_size"></a><a name="max_size"></a>pole::max_size

Spočítá počet prvků.

```cpp
constexpr size_type max_size() const;
```

### <a name="remarks"></a>Poznámky

Členská funkce `N`vrátí .

### <a name="example"></a>Příklad

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
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

## <a name="arrayoperator"></a><a name="op_at"></a>pole::operátor[]

Přistupuje k prvku na zadané pozici.

```cpp
reference operator[](size_type off);

constexpr const_reference operator[](size_type off) const;
```

### <a name="parameters"></a>Parametry

*vypnuto*\
Pozice prvku pro přístup.

### <a name="remarks"></a>Poznámky

Členské funkce vrátí odkaz na prvek řízené sekvence při *vypnuté*poloze . Pokud je tato pozice neplatná, chování není definováno.

K dispozici je také funkce [get](array-functions.md#get) bez člena, která získá odkaz na prvek **pole**.

### <a name="example"></a>Příklad

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
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

## <a name="arrayoperator"></a><a name="op_eq"></a>pole::operátor=

Nahradí řízenou sekvenci.

```cpp
array<Value> operator=(array<Value> right);
```

### <a name="parameters"></a>Parametry

*Právo*\
Kontejner ke kopírování.

### <a name="remarks"></a>Poznámky

Člen operátor přiřadí každý prvek *práva* odpovídající prvek řízené sekvence, pak vrátí `*this`. Slouží k nahrazení řízené sekvence kopií řízené sekvence *vpravo*.

### <a name="example"></a>Příklad

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    Myarray c1;
    c1 = c0;

    // display copied contents " 0 1 2 3"
        // display contents " 0 1 2 3"
    for (auto it : c1)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
0 1 2 3
```

## <a name="arraypointer"></a><a name="pointer"></a>pole::pointer

Typ ukazatele na prvek

```cpp
typedef Ty *pointer;
```

### <a name="remarks"></a>Poznámky

Typ popisuje objekt, který může sloužit jako ukazatel na prvky sekvence.

### <a name="example"></a>Příklad

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
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

## <a name="arrayrbegin"></a><a name="rbegin"></a>pole::rbegin

Označuje začátek obrácené řízené sekvence.

```cpp
reverse_iterator rbegin()noexcept;
const_reverse_iterator rbegin() const noexcept;
```

### <a name="remarks"></a>Poznámky

Členské funkce vrátí zpětný iterátor, který odkazuje těsně za konec řízené sekvence. Proto označuje začátek obrácené sekvence.

### <a name="example"></a>Příklad

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
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

## <a name="arrayreference"></a><a name="reference"></a>pole::odkaz

Typ odkazu na prvek

```cpp
typedef Ty& reference;
```

### <a name="remarks"></a>Poznámky

Typ popisuje objekt, který může sloužit jako odkaz na prvek řízené sekvence.

### <a name="example"></a>Příklad

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
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

## <a name="arrayrend"></a><a name="rend"></a>pole::rend

Označuje konec obrácené řízené sekvence.

```cpp
reverse_iterator rend()noexcept;
const_reverse_iterator rend() const noexcept;
```

### <a name="remarks"></a>Poznámky

Členské funkce vrátí zpětný iterátor, který odkazuje na první prvek sekvence (nebo těsně za koncem prázdné sekvence)). Proto označuje konec obrácené sekvence.

### <a name="example"></a>Příklad

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
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

## <a name="arrayreverse_iterator"></a><a name="reverse_iterator"></a>pole::reverse_iterator

Typ zpětného iterátoru pro řízenou sekvenci.

```cpp
typedef std::reverse_iterator<iterator> reverse_iterator;
```

### <a name="remarks"></a>Poznámky

Typ popisuje objekt, který může sloužit jako reverzní iterátor pro řízené sekvence.

### <a name="example"></a>Příklad

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
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

## <a name="arraysize"></a><a name="size"></a>pole::velikost

Spočítá počet prvků.

```cpp
constexpr size_type size() const;
```

### <a name="remarks"></a>Poznámky

Členská funkce `N`vrátí .

### <a name="example"></a>Příklad

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
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

## <a name="arraysize_type"></a><a name="size_type"></a>pole::size_type

Typ nepodepsané vzdálenosti mezi dvěma prvky.

```cpp
typedef std::size_t size_type;
```

### <a name="remarks"></a>Poznámky

Nepodepsaný typ celého čísla popisuje objekt, který může představovat délku libovolné řízené sekvence. Je synonymem pro `std::size_t`typ .

### <a name="example"></a>Příklad

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
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

## <a name="arrayswap"></a><a name="swap"></a>pole::swap

Zamění obsah tohoto pole s jiným polem.

```cpp
void swap(array& right);
```

### <a name="parameters"></a>Parametry

*Právo*\
Pole pro výměnu obsahu.

### <a name="remarks"></a>Poznámky

Členská funkce zamění řízené `*this` sekvence mezi a *vpravo*. Provádí počet přiřazení prvků a volání konstruktoru úměrné `N`.

K dispozici je také funkce [pro odkládací](array-functions.md#swap) funkci bez členů pro odhození dvou instancí **pole.**

### <a name="example"></a>Příklad

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    Myarray c1 = { 4, 5, 6, 7 };
    c0.swap(c1);

    // display swapped contents " 4 5 6 7"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    swap(c0, c1);

    // display swapped contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
4 5 6 7
0 1 2 3
```

## <a name="arrayvalue_type"></a><a name="value_type"></a>pole::value_type

Typ prvku

```cpp
typedef Ty value_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymem pro `Ty`parametr šablony .

### <a name="example"></a>Příklad

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        Myarray::value_type val = it;
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

[\<>pole](../standard-library/array.md)
