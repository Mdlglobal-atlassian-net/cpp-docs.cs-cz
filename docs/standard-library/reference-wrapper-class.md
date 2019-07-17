---
title: reference_wrapper – třída
ms.date: 11/04/2016
f1_keywords:
- functional/std::reference_wrapper
- type_traits/std::reference_wrapper
- xrefwrap/std::reference_wrapper
- type_traits/std::reference_wrapper::get
- type_traits/std::reference_wrapper::operator()
- functional/std::reference_wrapper::result_type
- functional/std::reference_wrapper::type
- functional/std::reference_wrapper::get
- functional/std::reference_wrapper::operator()
helpviewer_keywords:
- std::reference_wrapper [C++]
- std::reference_wrapper [C++]
- std::reference_wrapper [C++], result_type
- std::reference_wrapper [C++], type
- std::reference_wrapper [C++], get
ms.assetid: 90b8ed62-e6f1-44ed-acc7-9619bd58865a
ms.openlocfilehash: 83b68d1fdf89519df0a26acd478467fddec8b662
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/16/2019
ms.locfileid: "68240264"
---
# <a name="referencewrapper-class"></a>reference_wrapper – třída

Obaluje referenci.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty>
class reference_wrapper
{
    typedef Ty type;

    reference_wrapper(Ty&) noexcept;
    operator Ty&() const noexcept;
    Ty& get() const noexcept;

    template <class... Types>
    auto operator()(Types&&... args) const ->
        decltype(std::invoke(get(), std::forward<Types>(args)...));
};
```

## <a name="remarks"></a>Poznámky

A `reference_wrapper<Ty>` je kopírovací a kopírování lze přiřadit obálku kolem odkaz na objekt nebo funkce typu `Ty`a drží ukazatel, který odkazuje na objekt daného typu. A `reference_wrapper` slouží k ukládání odkazů ve standardních kontejnerů a předat objekty s odkazem na `std::bind`.

Typ `Ty` musí být typem objektu nebo funkce typu nebo statický kontrolní výraz selže v době kompilace.

Pomocné funkce [std::ref](functional-functions.md#ref) a [std::cref](functional-functions.md#cref) slouží k vytvoření `reference_wrapper` objekty.

## <a name="members"></a>Členové

### <a name="constructors"></a>Konstruktory

|||
|-|-|
|[reference_wrapper](#reference_wrapper)|Vytvoří `reference_wrapper`.|

### <a name="typedefs"></a>Typedefs

|||
|-|-|
|[result_type](#result_type)|Typ výsledku Slabý odkaz zabalené.|
|[type](#type)|Typ zabalené odkazu.|

### <a name="functions"></a>Funkce

|||
|-|-|
|[get](#get)|Získá zabalené odkaz.|

### <a name="operators"></a>Operátory

|||
|-|-|
|[Operator Ty&amp;](#op_ty_amp)|Získá ukazatel na odkaz zabalené.|
|[operator()](#op_call)|Volá zabalené odkaz.|

## <a name="get"></a> získat

Získá zabalené odkaz.

```cpp
Ty& get() const noexcept;
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí zabalené odkaz.

### <a name="example"></a>Příklad

```cpp
// std__functional__reference_wrapper_get.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

int main() {
    int i = 1;
    std::reference_wrapper<int> rwi(i);

    std::cout << "i = " << i << std::endl;
    std::cout << "rwi = " << rwi << std::endl;
    rwi.get() = -1;
    std::cout << "i = " << i << std::endl;

    return (0);
}
```

```Output
i = 1
rwi = 1
i = -1
```

## <a name="op_ty_amp"></a> Operator Ty&amp;

Získá zabalené odkaz.

```cpp
operator Ty&() const noexcept;
```

### <a name="remarks"></a>Poznámky

Členský operátor vrátí `*ptr`.

### <a name="example"></a>Příklad

```cpp
// std__functional__reference_wrapper_operator_cast.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

int main() {
    int i = 1;
    std::reference_wrapper<int> rwi(i);

    std::cout << "i = " << i << std::endl;
    std::cout << "(int)rwi = " << (int)rwi << std::endl;

    return (0);
}
```

```Output
i = 1
(int)rwi = 1
```

## <a name="op_call"></a> Operator()

Volá zabalené odkaz.

```cpp
template <class... Types>
auto operator()(Types&&... args);
```

### <a name="parameters"></a>Parametry

*Typy*\
Typy seznamu argumentů.

*argumenty*\
Seznam argumentů.

### <a name="remarks"></a>Poznámky

Šablona člena `operator()` vrátí `std::invoke(get(), std::forward<Types>(args)...)`.

### <a name="example"></a>Příklad

```cpp
// std__functional__reference_wrapper_operator_call.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

int neg(int val) {
    return (-val);
}

int main() {
    std::reference_wrapper<int (int)> rwi(neg);

    std::cout << "rwi(3) = " << rwi(3) << std::endl;

    return (0);
}
```

```Output
rwi(3) = -3
```

## <a name="reference_wrapper"></a> reference_wrapper –

Vytvoří `reference_wrapper`.

```cpp
reference_wrapper(Ty& val) noexcept;
```

### <a name="parameters"></a>Parametry

*Ty*\
Typ, který má zabalit.

*Val*\
Hodnota určená k zabalení.

### <a name="remarks"></a>Poznámky

Konstruktor je uložená hodnota nastaví `ptr` k `&val`.

### <a name="example"></a>Příklad

```cpp
// std__functional__reference_wrapper_reference_wrapper.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

int neg(int val) {
    return (-val);
}

int main() {
    int i = 1;
    std::reference_wrapper<int> rwi(i);

    std::cout << "i = " << i << std::endl;
    std::cout << "rwi = " << rwi << std::endl;
    rwi.get() = -1;
    std::cout << "i = " << i << std::endl;

    return (0);
}
```

```Output
i = 1
rwi = 1
i = -1
```

## <a name="result_type"></a> result_type

Typ výsledku Slabý odkaz zabalené.

```cpp
typedef R result_type;
```

### <a name="remarks"></a>Poznámky

`result_type` Definice typedef je synonymum pro typ výsledku slabé zabalené funkce. Tato definice typedef má smysl pro typy funkcí pouze.

### <a name="example"></a>Příklad

```cpp
// std__functional__reference_wrapper_result_type.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

int neg(int val) {
    return (-val);
}

int main() {
    typedef std::reference_wrapper<int (int)> Mywrapper;
    Mywrapper rwi(neg);
    Mywrapper::result_type val = rwi(3);

    std::cout << "val = " << val << std::endl;

    return (0);
}
```

```Output
val = -3
```

## <a name="type"></a> Typ

Typ zabalené odkazu.

```cpp
typedef Ty type;
```

### <a name="remarks"></a>Poznámky

Typedef je synonymum pro argument šablony `Ty`.

### <a name="example"></a>Příklad

```cpp
// std__functional__reference_wrapper_type.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

int neg(int val) {
    return (-val);
}

int main() {
    int i = 1;
    typedef std::reference_wrapper<int> Mywrapper;
    Mywrapper rwi(i);
    Mywrapper::type val = rwi.get();

    std::cout << "i = " << i << std::endl;
    std::cout << "rwi = " << val << std::endl;

    return (0);
}
```

```Output
i = 1
rwi = 1
```
