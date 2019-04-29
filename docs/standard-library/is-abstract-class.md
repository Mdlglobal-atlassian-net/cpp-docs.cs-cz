---
title: is_abstract – třída
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_abstract
helpviewer_keywords:
- is_abstract class
- is_abstract
ms.assetid: 8867f660-3434-404c-ba90-c26607a5e0d2
ms.openlocfilehash: 02863f5694f519e8cca54d07622a185f69de82d4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62404816"
---
# <a name="isabstract-class"></a>is_abstract – třída

Testuje, zda je typ je abstraktní třída.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty>
struct is_abstract;
```

### <a name="parameters"></a>Parametry

*Ty*<br/>
Typ, na který chcete odeslat dotaz.

## <a name="remarks"></a>Poznámky

Instance predikátu typu obsahuje hodnotu true, pokud typ *Ty* je třída, která má alespoň jednu prázdnou virtuální funkci, jinak obsahuje hodnotu false.

## <a name="example"></a>Příklad

```cpp
// std__type_traits__is_abstract.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

struct trivial
    {
    int val;
    };

struct abstract
    {
    virtual int val() = 0;
    };

int main()
    {
    std::cout << "is_abstract<trivial> == " << std::boolalpha
        << std::is_abstract<trivial>::value << std::endl;
    std::cout << "is_abstract<abstract> == " << std::boolalpha
        << std::is_abstract<abstract>::value << std::endl;

    return (0);
    }
```

```Output
is_abstract<trivial> == false
is_abstract<abstract> == true
```

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<type_traits >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[<type_traits>](../standard-library/type-traits.md)<br/>
[is_polymorphic – třída](../standard-library/is-polymorphic-class.md)<br/>
