---
title: add_rvalue_reference – třída
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::add_rvalue_reference
helpviewer_keywords:
- add_rvalue_reference Class
ms.assetid: 76b0cb7c-1031-45d0-b409-f03ab0297580
ms.openlocfilehash: 64694f2428c1dd536df4d242a17f3f011cfb290c
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456542"
---
# <a name="addrvaluereference-class"></a>add_rvalue_reference – třída

Vytvoří odkazový typ rvalue parametru šablony, pokud se jedná o typ objektu nebo funkce. V opačném případě, vzhledem k sémantikě sbalení odkazů, je typ stejný jako parametr šablony.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
struct add_rvalue_reference;

template <class T>
using add_rvalue_reference_t = typename add_rvalue_reference<T>::type;
```

### <a name="parameters"></a>Parametry

*Š*\
Typ, který chcete upravit.

## <a name="remarks"></a>Poznámky

Třída má člena s názvem `type`, což je alias pro typ odkazu rvalue na parametr šablony *T.* `add_rvalue_reference` Sémantika pro sbalení odkazů `T&&` znamená, že pro typy non-Object a non-Function *t*je *t*. Například když *T* je odkazový typ lvalue, `add_rvalue_reference<T>::type` je odkazový typ lvalue, nikoli odkaz rvalue.

Pro usnadnění \<type_traits > definuje pomocnou `add_rvalue_reference_t`šablonu, `add_rvalue_reference`která je `type` aliasem člena.

## <a name="example"></a>Příklad

Tento příklad kódu používá static_assert k zobrazení způsobu, jakým jsou vytvořeny typy odkazů `add_rvalue_reference` rvalue `add_rvalue_reference_t`pomocí a a jakým způsobem `add_rvalue_reference` výsledek na odkazovém typu lvalue není odkaz rvalue, ale sbalí na odkazový typ lvalue.

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

Záhlaví: \<type_traits >

Obor názvů: std

## <a name="see-also"></a>Viz také:

[< type_traits >](../standard-library/type-traits.md)\
[add_lvalue_reference – třída](../standard-library/add-lvalue-reference-class.md)\
[is_rvalue_reference – třída](../standard-library/is-rvalue-reference-class.md)
