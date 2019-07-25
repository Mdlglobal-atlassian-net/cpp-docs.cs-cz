---
title: initializer_list – třída
ms.date: 11/04/2016
f1_keywords:
- initializer_list/std::initializer_list::initializer_list
- initializer_list/std::initializer_list::begin
- initializer_list/std::initializer_list::end
- initializer_list/std::initializer_list::size
ms.assetid: 1f2c0ff4-5636-4f79-b008-e75426e3d2ab
helpviewer_keywords:
- std::initializer_list::initializer_list
- std::initializer_list::begin
- std::initializer_list::end
- std::initializer_list::size
ms.openlocfilehash: acd11f3b3a3bf0ba17e34a802cc8988410e17b12
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68455360"
---
# <a name="initializerlist-class"></a>initializer_list – třída

Poskytuje přístup k poli prvků, ve kterých je každý člen zadaného typu.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Type>
class initializer_list
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*Typ*|Datový typ prvku, který bude uložen v `initializer_list`.|

## <a name="remarks"></a>Poznámky

`initializer_list` Může být vytvořen pomocí seznamu inicializátorů v závorkách:

```cpp
initializer_list<int> i1{ 1, 2, 3, 4 };
```

Kompilátor transformuje seznam inicializátorů v závorkách s homogenními prvky na `initializer_list` vždy, když signatura funkce `initializer_list`vyžaduje. Další informace o použití `initializer_list`naleznete v tématu [jednotná inicializace a delegování konstruktorů](../cpp/uniform-initialization-and-delegating-constructors.md) .

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[initializer_list](../standard-library/forward-list-class.md#forward_list)|Vytvoří objekt typu `initializer_list`.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|value_type|Typ prvků v `initializer_list`.|
|reference|Typ, který poskytuje odkaz na prvek v `initializer_list`.|
|const_reference|Typ, který poskytuje konstantní odkaz na prvek v `initializer_list`.|
|size_type|Typ, který představuje počet prvků v `initializer_list`.|
|iterátor|Typ, který poskytuje iterátor pro `initializer_list`.|
|const_iterator|Typ, který poskytuje konstantní iterátor pro `initializer_list`.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[ifunctiondiscovery](#begin)|Vrátí ukazatel na první prvek v `initializer_list`.|
|[účelu](#end)|Vrátí ukazatel na jeden za poslední prvek v `initializer_list`.|
|[hodnota](#size)|Vrátí počet prvků v `initializer_list`.|

## <a name="requirements"></a>Požadavky

**Hlavička:** \<initializer_list >

**Obor názvů:** std

## <a name="begin"></a>initializer_list:: begin

Vrátí ukazatel na první prvek v `initializer_list`.

```cpp
constexpr const InputIterator* begin() const noexcept;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na první prvek `initializer_list`. Pokud je seznam prázdný, ukazatel je stejný jako na začátku a na konci seznamu.

### <a name="remarks"></a>Poznámky

## <a name="end"></a>initializer_list:: end

Vrátí ukazatel na jeden za poslední prvek v `initializer list`.

```cpp
constexpr const InputIterator* end() const noexcept;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na jeden za poslední prvek v seznamu. Pokud je seznam prázdný, je stejný jako ukazatel na první prvek v seznamu.

## <a name="initializer_list"></a>initializer_list::initializer_list

Vytvoří objekt typu `initializer_list`.

```cpp
constexpr initializer_list() noexcept;
initializer_list(const InputIterator First, const InputIterator Last);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*První*|Pozice prvního prvku v rozsahu prvků, které mají být zkopírovány.|
|*Posledního*|Pozice prvního prvku mimo rozsah prvků, které mají být zkopírovány.|

### <a name="remarks"></a>Poznámky

`initializer_list` Je založen na poli objektů zadaného typu. `initializer_list` Kopírování vytvoří druhou instanci seznamu ukazující na stejné objekty; zdrojové objekty nejsou zkopírovány.

### <a name="example"></a>Příklad

```cpp
// initializer_list_class.cpp
// compile with: /EHsc
#include <initializer_list>
#include <iostream>

int main()
{
    using namespace std;
    // Create an empty initializer_list c0
    initializer_list <int> c0;

    // Create an initializer_list c1 with 1 element
    initializer_list <int> c1{ 3 };

    // Create an initializer_list c2 with 5 elements
    initializer_list <int> c2{ 5, 4, 3, 2, 1 };

    // Create a copy, initializer_list c3, of initializer_list c2
    initializer_list <int> c3(c2);

    // Create a initializer_list c4 by copying the range c3[ first,  last)
    const int* c3_ptr = c3.begin();
    c3_ptr++;
    c3_ptr++;
    initializer_list <int> c4(c3.begin(), c3_ptr);

    // Move initializer_list c4 to initializer_list c5
    initializer_list <int> c5(move(c4));

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
}
```

```Output
c1 = 3c2 = 5 4 3 2 1c3 = 5 4 3 2 1c4 = 5 4c5 = 5 4
```

## <a name="size"></a>initializer_list:: size

Vrátí počet prvků v seznamu.

```cpp
constexpr size_t size() const noexcept;
```

### <a name="return-value"></a>Návratová hodnota

Počet prvků v seznamu.

### <a name="remarks"></a>Poznámky

## <a name="see-also"></a>Viz také:

[<forward_list>](../standard-library/forward-list.md)
