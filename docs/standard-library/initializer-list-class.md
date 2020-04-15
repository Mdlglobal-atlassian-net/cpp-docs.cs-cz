---
title: initializer_list – třída
description: Odkaz na třídu initializer_list v knihovně C++ Standard implementovaný společností Microsoft v sadě Visual Studio.
ms.date: 01/28/2020
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
ms.openlocfilehash: b1d33ce484948e731f8d3062b7a99df06ef26073
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373363"
---
# <a name="initializer_list-class"></a>initializer_list – třída

Poskytuje přístup k pole prvků, ve kterých každý člen je zadaného typu.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Type>
class initializer_list
```

### <a name="parameters"></a>Parametry

*Typ*\
Datový typ prvku, který `initializer_list`má být uložen v rozhraní .

## <a name="remarks"></a>Poznámky

Lze `initializer_list` sestavit pomocí vyztuženého inicializátoru seznamu:

```cpp
initializer_list<int> i1{ 1, 2, 3, 4 };
```

Kompilátor transformuje vyztužené inicializátorseznamy s homogenní prvky do `initializer_list` vždy, když podpis funkce vyžaduje `initializer_list`. Další informace o `initializer_list`použití naleznete [v tématu Jednotná inicializace a delegování konstruktorů](../cpp/uniform-initialization-and-delegating-constructors.md)

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[initializer_list](#initializer_list)|Vytvoří objekt typu `initializer_list`.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|`value_type`|Typ prvků v . `initializer_list`|
|`reference`|Typ, který poskytuje odkaz na `initializer_list`prvek v rozhraní .|
|`const_reference`|Typ, který poskytuje konstantní odkaz na `initializer_list`prvek v .|
|`size_type`|Typ, který představuje počet prvků `initializer_list`v rozhraní .|
|`iterator`|Typ, který poskytuje iterátor `initializer_list`pro .|
|`const_iterator`|Typ, který poskytuje konstantní iterátor `initializer_list`pro .|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[Začít](#begin)|Vrátí ukazatel na první prvek `initializer_list`v .|
|[Konec](#end)|Vrátí ukazatel na jeden za poslední `initializer_list`prvek v .|
|[Velikost](#size)|Vrátí počet prvků v `initializer_list`rozhraní .|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<initializer_list>

**Obor názvů:** std

## <a name="initializer_listbegin"></a><a name="begin"></a>initializer_list::začátek

Vrátí ukazatel na první prvek `initializer_list`v .

```cpp
constexpr const InputIterator* begin() const noexcept;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na první prvek `initializer_list`rozhraní . Pokud je seznam prázdný, ukazatel je stejný pro začátek a konec seznamu.

## <a name="initializer_listend"></a><a name="end"></a>initializer_list::konec

Vrátí ukazatel na jeden za poslední `initializer list`prvek v .

```cpp
constexpr const InputIterator* end() const noexcept;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na jeden za poslední prvek v seznamu. Pokud je seznam prázdný, je stejný jako ukazatel na první prvek v seznamu.

## <a name="initializer_listinitializer_list"></a><a name="initializer_list"></a>initializer_list::initializer_list

Vytvoří objekt typu `initializer_list`.

```cpp
constexpr initializer_list() noexcept;
initializer_list(const InputIterator First, const InputIterator Last);
```

### <a name="parameters"></a>Parametry

*První*\
Umístění prvního prvku v rozsahu prvků, které mají být zkopírovány.

*Poslední*\
Pozice první prvek mimo rozsah prvků, které mají být zkopírovány.

### <a name="remarks"></a>Poznámky

A `initializer_list` je založen na pole objektů zadaného typu. Kopírováním `initializer_list` vytvoříte druhou instanci seznamu směřujícího na stejné objekty; podkladové objekty se nezkopírují.

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

    cout << "c5 =";
    for (auto c : c5)
        cout << " " << c;
    cout << endl;
}
```

```Output
c1 = 3
c2 = 5 4 3 2 1
c3 = 5 4 3 2 1
c5 = 5 4
```

## <a name="initializer_listsize"></a><a name="size"></a>initializer_list::velikost

Vrátí počet prvků v seznamu.

```cpp
constexpr size_t size() const noexcept;
```

### <a name="return-value"></a>Návratová hodnota

Počet prvků v seznamu.

## <a name="see-also"></a>Viz také

[<forward_list>](../standard-library/forward-list.md)
