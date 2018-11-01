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
ms.openlocfilehash: de925f73ac206113aafb8661a8d5b347503150c5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50466908"
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
|*Typ*|Typ dat prvku, který bude uložen do `initializer_list`.|

## <a name="remarks"></a>Poznámky

`initializer_list` Lze sestavit pomocí seznamu inicializátorů v závorkách:

```cpp
initializer_list<int> i1{ 1, 2, 3, 4 };
```

Kompilátor převede seznamy inicializátorů v závorkách se homogenní prvky do `initializer_list` vždy, když se podpis funkce vyžaduje `initializer_list`. Další podrobnosti o použití `initializer_list`, naleznete v tématu [jednotná inicializace a delegování konstruktorů](../cpp/uniform-initialization-and-delegating-constructors.md)

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
|[začít](#begin)|Vrací ukazatel na první prvek v `initializer_list`.|
|[ukončení](#end)|Vrací ukazatel na jedno místo za posledním prvkem v `initializer_list`.|
|[Velikost](#size)|Vrátí počet prvků v `initializer_list`.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<initializer_list >

**Namespace:** std

## <a name="begin"></a>  initializer_list::begin

Vrací ukazatel na první prvek v `initializer_list`.

```cpp
constexpr const InputIterator* begin() const noexcept;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na první prvek `initializer_list`. Pokud je seznam prázdný, ukazatel je stejný jako začátek a konec seznamu.

### <a name="remarks"></a>Poznámky

## <a name="end"></a>  initializer_list::end

Vrací ukazatel na jedno místo za posledním prvkem v `initializer list`.

```cpp
constexpr const InputIterator* end() const noexcept;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na jedno místo za posledním prvkem v seznamu. Pokud je seznam prázdný, to je stejný jako ukazatel na první prvek v seznamu.

## <a name="initializer_list"></a>  initializer_list::initializer_list

Vytvoří objekt typu `initializer_list`.

```cpp
constexpr initializer_list() noexcept;
initializer_list(const InputIterator First, const InputIterator Last);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*první*|Pozice prvního prvku v rozsahu prvků, které se mají zkopírovat.|
|*poslední*|Pozice prvního prvku mimo rozsah prvků, které se mají zkopírovat.|

### <a name="remarks"></a>Poznámky

`initializer_list` Je založen na poli objektů zadaného typu. Kopírování `initializer_list` vytvoří druhou instanci seznamu ukazující na stejné objekty; objekty nejsou zkopírovány.

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

## <a name="size"></a>  initializer_list::size

Vrátí počet prvků v seznamu.

```cpp
constexpr size_t size() const noexcept;
```

### <a name="return-value"></a>Návratová hodnota

Počet prvků v seznamu.

### <a name="remarks"></a>Poznámky

## <a name="see-also"></a>Viz také:

[<forward_list>](../standard-library/forward-list.md)<br/>
