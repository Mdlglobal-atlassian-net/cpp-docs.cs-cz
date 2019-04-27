---
title: is_member_object_pointer – třída
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_member_object_pointer
helpviewer_keywords:
- is_member_object_pointer class
- is_member_object_pointer
ms.assetid: 64f9cdf3-4621-4310-a076-a7bc986926b9
ms.openlocfilehash: 401beed2a45be0492ba1a5cbd57cc92153dbaa91
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62351076"
---
# <a name="ismemberobjectpointer-class"></a>is_member_object_pointer – třída

Testuje, zda je typ ukazatele na člena objektu.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty>
struct is_member_object_pointer;
```

### <a name="parameters"></a>Parametry

*Ty*<br/>
Typ, na který chcete odeslat dotaz.

## <a name="remarks"></a>Poznámky

Instance predikátu typu obsahuje hodnotu true, pokud typ *Ty* je ukazatel na člena objektu nebo `cv-qualified` ukazatel na člena objektu, jinak má hodnotu false. Všimněte si, že `is_member_object_pointer` false v případě blokování *Ty* je ukazatel na členskou funkci.

## <a name="example"></a>Příklad

```cpp
// std__type_traits__is_member_object_pointer.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

struct trivial
    {
    int val;
    };

struct functional
    {
    int f();
    };

int main()
    {
    std::cout << "is_member_object_pointer<trivial *> == "
        << std::boolalpha
        << std::is_member_object_pointer<trivial *>::value
        << std::endl;
    std::cout << "is_member_object_pointer<int trivial::*> == "
        << std::boolalpha
        << std::is_member_object_pointer<int trivial::*>::value
        << std::endl;
    std::cout << "is_member_object_pointer<int (functional::*)()> == "
        << std::boolalpha
        << std::is_member_object_pointer<int (functional::*)()>::value
        << std::endl;

    return (0);
    }
```

```Output
is_member_object_pointer<trivial *> == false
is_member_object_pointer<int trivial::*> == true
is_member_object_pointer<int (functional::*)()> == false
```

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<type_traits >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[<type_traits>](../standard-library/type-traits.md)<br/>
[is_member_pointer – třída](../standard-library/is-member-pointer-class.md)<br/>
