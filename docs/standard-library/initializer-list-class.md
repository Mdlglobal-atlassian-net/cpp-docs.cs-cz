---
title: initializer_list třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- initializer_list/std::initializer_list::initializer_list
- initializer_list/std::initializer_list::begin
- initializer_list/std::initializer_list::end
- initializer_list/std::initializer_list::size
dev_langs:
- C++
ms.assetid: 1f2c0ff4-5636-4f79-b008-e75426e3d2ab
caps.latest.revision: 17
author: corob-msft
ms.author: corob
manager: ghogen
helpviewer_keywords:
- std::initializer_list::initializer_list
- std::initializer_list::begin
- std::initializer_list::end
- std::initializer_list::size
ms.workload:
- cplusplus
ms.openlocfilehash: 5ec1af899892b52e09b7436339a5a4acd09cab01
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="initializerlist-class"></a>initializer_list – třída

Poskytuje přístup k pole elementy, ve kterých je každý člen zadaného typu.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Type>
class initializer_list
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|`Type`|Element datový typ se neukládají v `initializer_list`.|


## <a name="remarks"></a>Poznámky

`initializer_list` Lze sestavit pomocí braced inicializátoru seznamu:

```cpp
initializer_list<int> i1{ 1, 2, 3, 4 };
```

Kompilátor transformuje braced inicializační seznamy homogenní elementy do `initializer_list` vždy, když podpis funkce vyžaduje `initializer_list`. Další podrobnosti o použití `initializer_list`, najdete v části [jednotná inicializace a delegování konstruktorů](../cpp/uniform-initialization-and-delegating-constructors.md)

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[initializer_list](../standard-library/forward-list-class.md#forward_list)|Vytvoří objekt typu `initializer_list`.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|value_type|Typ elementů v `initializer_list`.|
|reference|Typ, který obsahuje odkaz na element v `initializer_list`.|
|const_reference|Typ, který poskytuje konstantní odkaz na element v `initializer_list`.|
|size_type|Typ, který reprezentuje počet elementů ve `initializer_list`.|
|iterátor|Typ, který poskytuje iterace pro `initializer_list`.|
|const_iterator|Typ, který poskytuje konstantní iterator pro `initializer_list`.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[Začátek](#begin)|Vrací ukazatel na prvním elementem v `initializer_list`.|
|[End](#end)|Vrací ukazatel na jednu po posledním prvkem v `initializer_list`.|
|[Velikost](#size)|Vrátí počet prvků v `initializer_list`.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<initializer_list >

**Namespace:** – std

## <a name="begin"></a>  initializer_list::begin

Vrací ukazatel na prvním elementem v `initializer_list`.

```cpp
constexpr const InputIterator* begin() const noexcept;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na první prvek `initializer_list`. Pokud je seznam prázdný, ukazatele je stejný pro začátek a konec seznamu.

### <a name="remarks"></a>Poznámky

## <a name="end"></a>  initializer_list::end

Vrací ukazatel na jednu po posledním prvkem v `initializer list`.

```cpp
constexpr const InputIterator* end() const noexcept;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na jednu po posledním prvkem v seznamu. Pokud je seznam prázdný, je to stejné jako má ukazatel na prvním elementem v seznamu.

## <a name="initializer_list"></a>  initializer_list::initializer_list

Vytvoří objekt typu `initializer_list`.

```cpp
constexpr initializer_list() noexcept;
initializer_list(const InputIterator First, const InputIterator Last);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|`First`|Pozice první prvek v rozsahu elementy, které se mají zkopírovat.|
|`Last`|Pozice první prvek mimo rozsah elementy, které se mají zkopírovat.|

### <a name="remarks"></a>Poznámky

`initializer_list` Je založena na pole objektů zadaného typu. Kopírování `initializer_list` vytvoří druhou instanci seznamu odkazující na stejné objekty; základní objekty nejsou zkopírovány.

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

Počet elementů v seznamu.

### <a name="remarks"></a>Poznámky

## <a name="see-also"></a>Viz také

[<forward_list>](../standard-library/forward-list.md)<br/>
