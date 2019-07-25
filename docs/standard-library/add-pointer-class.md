---
title: add_pointer – třída
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::add_pointer
helpviewer_keywords:
- add_pointer class
- add_pointer
ms.assetid: d8095cb0-6578-4143-b78f-87f82485298c
ms.openlocfilehash: 759867a542aa128755ba31e090984eb5b3fe6963
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456549"
---
# <a name="addpointer-class"></a>add_pointer – třída

Vytvoří ukazatel na typ z určeného typu.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
struct add_pointer;

template <class T>
using add_pointer_t = typename add_pointer<T>::type;
```

### <a name="parameters"></a>Parametry

*Š*\
Typ, který chcete upravit.

## <a name="remarks"></a>Poznámky

**Definice typedef** `type` člena má stejný typ jako `remove_reference<T>::type*`. Alias `add_pointer_t` je zástupce pro přístup k **definici TypeDef** `type`člena.

Vzhledem k tomu, že je neplatný pro vytvoření ukazatele z odkazu `add_pointer` , odebere odkaz, pokud existuje, ze zadaného typu před tím, než vytvoří ukazatel na typ. V důsledku toho můžete použít typ `add_pointer` bez ohledu na to, zda je typ odkaz.

## <a name="example"></a>Příklad

Následující příklad ukazuje, že `add_pointer` typ je stejný jako ukazatel na tento typ.

```cpp
#include <type_traits>
#include <iostream>

int main()
{
    std::add_pointer_t<int> *p = (int **)0;

    p = p;  // to quiet "unused" warning
    std::cout << "add_pointer_t<int> == "
        << typeid(*p).name() << std::endl;

    return (0);
}
```

```Output
add_pointer_t<int> == int *
```

## <a name="requirements"></a>Požadavky

**Hlavička:** \<type_traits >

**Obor názvů:** std

## <a name="see-also"></a>Viz také:

[< type_traits >](../standard-library/type-traits.md)\
[remove_pointer – třída](../standard-library/remove-pointer-class.md)
