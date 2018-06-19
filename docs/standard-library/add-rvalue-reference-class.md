---
title: add_rvalue_reference – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::add_rvalue_reference
dev_langs:
- C++
helpviewer_keywords:
- add_rvalue_reference Class
ms.assetid: 76b0cb7c-1031-45d0-b409-f03ab0297580
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1cceec4e7d954e07e1d776042f311dfa1a386300
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33850753"
---
# <a name="addrvaluereference-class"></a>add_rvalue_reference – třída

Vytvoří odkaz na typ rvalue parametr šablony, pokud je typ objektu nebo funkce. Jinak hodnota z důvodu sémantika odkaz sbalení, typ je stejný jako parametr šablony.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
struct add_rvalue_reference;

template <class T>
using add_rvalue_reference_t = typename add_rvalue_reference<T>::type;
```

### <a name="parameters"></a>Parametry

T typ, který chcete upravit.

## <a name="remarks"></a>Poznámky

`add_rvalue_reference` Třída obsahuje člena s názvem `type`, což je alias pro typ rvalue odkaz na parametr šablony `T`. Sémantika odkaz sbalení, implikují pro jiný objekt a není funkcí typy `T`, `T&&` je `T`. Například když `T` je typ odkazu lvalue `add_rvalue_reference<T>::type` je typ odkazu lvalue, není deklarátor odkazu.

Pro usnadnění práce \<type_traits > definuje šablonu pomocné rutiny, `add_rvalue_reference_t`, že aliasy `type` členem `add_rvalue_reference`.

## <a name="example"></a>Příklad

Tento příklad kódu používá static_assert zobrazíte vytváření rvalue odkazové typy pomocí `add_rvalue_reference` a `add_rvalue_reference_t`a jak výsledek `add_rvalue_reference` v odkazu lvalue typ není deklarátor odkazu, ale Hroutí k typ odkazu lvalue.

```cpp
// ex_add_rvalue_reference.cpp
// Build by using: cl /EHsc /W4 ex_add_rvalue_reference.cpp
#include <type_traits>
#include <iostream>
#include <string>

using namespace std;
int main()
{
    static_assert(is_same<add_rvalue_reference<string>::type, string&&>::value,
        "Expected add_rvalue_reference_t<string> to be string&&");
    static_assert(is_same<add_rvalue_reference_t<string*>, string*&&>::value,
        "Expected add_rvalue_reference_t<string*> to be string*&&");
    static_assert(is_same<add_rvalue_reference<string&>::type, string&>::value,
        "Expected add_rvalue_reference_t<string&> to be string&");
    static_assert(is_same<add_rvalue_reference_t<string&&>, string&&>::value,
        "Expected add_rvalue_reference_t<string&&> to be string&&");
    cout << "All static_assert tests of add_rvalue_reference passed." << endl;
    return 0;
}

/*Output:
All static_assert tests of add_rvalue_reference passed.
*/
```

## <a name="requirements"></a>Požadavky

Záhlaví: < type_traits > Namespace: – std

## <a name="see-also"></a>Viz také

[<type_traits>](../standard-library/type-traits.md)<br/>
[add_lvalue_reference – třída](../standard-library/add-lvalue-reference-class.md)<br/>
[is_rvalue_reference – třída](../standard-library/is-rvalue-reference-class.md)<br/>
