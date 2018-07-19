---
title: binder1st – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- xfunctional/std::binder1st
dev_langs:
- C++
helpviewer_keywords:
- binder1st class
ms.assetid: 6b8ee343-c82f-48f8-867d-06f9d1d324c0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8191b572595b8ada96f59357af095baf5d846bc4
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38961718"
---
# <a name="binder1st-class"></a>binder1st – třída

Třída šablony poskytující konstruktor, který převádí objekt binární funkce na objekt jednočlenné funkce navázáním prvního argumentu binární funkce na zadanou hodnotu.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Operation>
class binder1st
    : public unaryFunction <typename Operation::second_argument_type,
                             typename Operation::result_type>
{
public:
    typedef typename Operation::argument_type argument_type;
    typedef typename Operation::result_type result_type;
    binder1st(
        const Operation& Func,
        const typename Operation::first_argument_type& left);

    result_type operator()(const argument_type& right) const;
    result_type operator()(const argument_type& right) const;

protected:
    Operation op;
    typename Operation::first_argument_type value;
};
```

### <a name="parameters"></a>Parametry

*Func* objekt binární funkce pro převod na objekt jednočlenné funkce.

*levé* hodnotu, do kterého má být vázaný prvního argumentu binární funkce na objekt.

*správné* hodnota argumentu, který porovná objekt adaptovaného binární pevnou hodnotu druhého argumentu.

## <a name="return-value"></a>Návratová hodnota

Objekt jednočlenné funkce, která je výsledkem vazby prvního argumentu binární funkce na objekt na hodnotu *levé*.

## <a name="remarks"></a>Poznámky

Třída šablony ukládá jejich kopii objekt binární funkce *Func* v `op`a kopii *levé* v `value`. Definuje jeho členskou funkci `operator()` jako vracející **op**( **hodnotu**, `right`).

Pokud *Func* je objekt typu `Operation` a `c` je konstanta, pak [bind1st –](../standard-library/functional-functions.md#bind1st) ( `Func`, `c` ) odpovídá `binder1st` konstruktoru třídy `binder1st` \< **Operace**> ( `Func`, `c` ) a pohodlnější.

## <a name="example"></a>Příklad

```cpp
// functional_binder1st.cpp
// compile with: /EHsc
#include <vector>
#include <functional>
#include <algorithm>
#include <iostream>

using namespace std;

int main()
{
    vector<int> v1;
    vector<int>::iterator Iter;

    int i;
    for (i = 0; i <= 5; i++)
    {
        v1.push_back(5 * i);
    }

    cout << "The vector v1 = ( ";
    for (Iter = v1.begin(); Iter != v1.end(); Iter++)
        cout << *Iter << " ";
    cout << ")" << endl;

    // Count the number of integers > 10 in the vector
    vector<int>::iterator::difference_type result1;
    result1 = count_if(v1.begin(), v1.end(),
        binder1st<less<int> >(less<int>(), 10));
    cout << "The number of elements in v1 greater than 10 is: "
         << result1 << "." << endl;

    // Compare use of binder2nd fixing 2nd argument:
    // count the number of integers < 10 in the vector
    vector<int>::iterator::difference_type result2;
    result2 = count_if(v1.begin(), v1.end(),
        binder2nd<less<int> >(less<int>(), 10));
    cout << "The number of elements in v1 less than 10 is: "
         << result2 << "." << endl;
}
\* Output:
The vector v1 = ( 0 5 10 15 20 25 )
The number of elements in v1 greater than 10 is: 3.
The number of elements in v1 less than 10 is: 2.
*\
```

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<funkční >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)<br/>
