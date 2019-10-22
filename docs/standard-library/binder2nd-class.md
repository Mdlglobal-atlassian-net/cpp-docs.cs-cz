---
title: binder2nd – třída
ms.date: 02/21/2019
f1_keywords:
- functional/std::binder2nd
helpviewer_keywords:
- binder2nd class
ms.assetid: b2a9c1d1-dfc4-4ca9-a10e-ae84e195a62d
ms.openlocfilehash: 46c8bb2ae450b3ef56f2729717fb9b5563a7c139
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689939"
---
# <a name="binder2nd-class"></a>binder2nd – třída

Šablona třídy poskytující konstruktor, který převádí objekt binární funkce na unární objekt funkce navázáním druhého argumentu binární funkce na zadanou hodnotu. Zastaralé v C++ 11, odebrané v C++ 17.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Operation>
class binder2nd
    : public unaryFunction <typename Operation::first_argument_type,
    typename Operation::result_type>
{
    typedef typename Operation::argument_type argument_type;
    typedef typename Operation::result_type result_type;
    binder2nd(
        const Operation& Func,
        const typename Operation::second_argument_type& right);

    result_type operator()(const argument_type& left) const;
    result_type operator()(argument_type& left) const;
};
```

### <a name="parameters"></a>Parametry

@No__t_1 *Func*
Objekt binární funkce, který má být převeden na unární objekt funkce.

*pravé* \
Hodnota, na kterou má být druhý argument objektu binární funkce svázán.

*levý* \
Hodnota argumentu, který upravený binární objekt porovnává s pevnou hodnotou druhého argumentu.

## <a name="return-value"></a>Návratová hodnota

Unární objekt funkce, který je výsledkem vazby druhého argumentu objektu binární funkce na hodnotu *Right*.

## <a name="remarks"></a>Poznámky

Šablona třídy uchovává kopii objektu binární funkce _ *Func* in `op` a kopii *přímo* v `value`. Definuje jeho členskou funkci `operator()` jako vrácení **op**(`left`, **hodnota**).

Pokud `Func` je objekt typu `Operation` a c je konstanta, pak [bind2nd –](../standard-library/functional-functions.md#bind2nd) (`Func`, `c`) je ekvivalentem konstruktoru třídy `binder2nd` `binder2nd` \< **operace**> (`Func`, 0) a pohodlnější.

## <a name="example"></a>Příklad

```cpp
// functional_binder2nd.cpp
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
        binder2nd<greater<int> >(greater<int>(), 10));
    cout << "The number of elements in v1 greater than 10 is: "
         << result1 << "." << endl;

    // Compare using binder1st fixing 1st argument:
    // count the number of integers < 10 in the vector
    vector<int>::iterator::difference_type result2;
    result2 = count_if(v1.begin(), v1.end(),
        binder1st<greater<int> >(greater<int>(), 10));
    cout << "The number of elements in v1 less than 10 is: "
         << result2 << "." << endl;
}
```

```Output
The vector v1 = ( 0 5 10 15 20 25 )
The number of elements in v1 greater than 10 is: 3.
The number of elements in v1 less than 10 is: 2.
```
