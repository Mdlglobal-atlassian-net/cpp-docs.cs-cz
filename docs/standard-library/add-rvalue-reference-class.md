---
title: add_rvalue_reference – třída | Dokumentace Microsoftu
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
ms.openlocfilehash: ba90002bc16dee6def7f8de69314668204ff5466
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38966614"
---
# <a name="addrvaluereference-class"></a>add_rvalue_reference – třída

Odkazový typ parametru šablony vytvoří, pokud je to typ objektu nebo funkce. Jinak kvůli sémantiky pro sbalování odkazu, typ je stejný jako parametru šablony.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
struct add_rvalue_reference;

template <class T>
using add_rvalue_reference_t = typename add_rvalue_reference<T>::type;
```

### <a name="parameters"></a>Parametry

*T* typ, který chcete upravit.

## <a name="remarks"></a>Poznámky

`add_rvalue_reference` Třída má člen nazvaný `type`, což je alias pro typ odkaz rvalue na parametru šablony *T*. Sémantika pro sbalování odkazu znamenat, že, pro typy neobjektové a funkci bez *T*, `T&&` je *T*. Například když *T* je typem odkazu l-hodnoty `add_rvalue_reference<T>::type` je typ odkazu l-hodnotou, není odkaz rvalue.

Pro usnadnění práce \<type_traits > definuje šablonu pomocné rutiny `add_rvalue_reference_t`, že aliasy `type` člen `add_rvalue_reference`.

## <a name="example"></a>Příklad

Tento příklad kódu používá k zobrazení, jak typy odkazu r-hodnoty jsou vytvořeny pomocí static_assert `add_rvalue_reference` a `add_rvalue_reference_t`a jak výsledek `add_rvalue_reference` na odkaz na lvalue typ není odkaz rvalue, ale sbalí na typ odkazu l-hodnoty.

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

Záhlaví: < type_traits > Namespace: std

## <a name="see-also"></a>Viz také:

[<type_traits>](../standard-library/type-traits.md)<br/>
[add_lvalue_reference – třída](../standard-library/add-lvalue-reference-class.md)<br/>
[is_rvalue_reference – třída](../standard-library/is-rvalue-reference-class.md)<br/>
