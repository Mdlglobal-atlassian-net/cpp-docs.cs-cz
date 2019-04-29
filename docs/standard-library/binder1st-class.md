---
title: binder1st – třída
ms.date: 02/21/2019
f1_keywords:
- functional/std::binder1st
helpviewer_keywords:
- binder1st class
ms.assetid: 6b8ee343-c82f-48f8-867d-06f9d1d324c0
ms.openlocfilehash: f70a1a4a0903b66edf5f42e59788b9a2d97fc967
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62388212"
---
# <a name="binder1st-class"></a>binder1st – třída

Třída šablony poskytující konstruktor, který převádí objekt binární funkce na objekt jednočlenné funkce navázáním prvního argumentu binární funkce na zadanou hodnotu. Zastaralé v C ++ 11 nahrazený [svázat](functional-functions.md#bind)a v C ++ 17 odebrané.

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
        const Operation& binary_fn,
        const typename Operation::first_argument_type& left);

    result_type operator()(const argument_type& right) const;
    result_type operator()(const argument_type& right) const;

protected:
    Operation op;
    typename Operation::first_argument_type value;
};
```

### <a name="parameters"></a>Parametry

*binary_fn*<br/>
Objekt binární funkce pro převod na objekt jednočlenné funkce.

*doleva*<br/>
Hodnota, na které má být vázaný prvního argumentu binární funkce na objekt.

*doprava*<br/>
Hodnota argumentu, který porovná objekt adaptovaného binární pevnou hodnotu druhého argumentu.

## <a name="return-value"></a>Návratová hodnota

Objekt jednočlenné funkce, která je výsledkem vazby prvního argumentu binární funkce na objekt na hodnotu *levé*.

## <a name="remarks"></a>Poznámky

Třída šablony ukládá jejich kopii objekt binární funkce *binary_fn* v `op`a kopii *levé* v `value`. Definuje jeho členskou funkci `operator()` jako vracející `op( value, right )`.

Pokud *binary_fn* je objekt typu `Operation` a `c` je konstanta, pak `bind1st( binary_fn, c )` je pohodlnější ekvivalentem `binder1st<Operation>( binary_fn, c )`. Další informace najdete v tématu [bind1st –](../standard-library/functional-functions.md#bind1st).

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
/* Output:
The vector v1 = ( 0 5 10 15 20 25 )
The number of elements in v1 greater than 10 is: 3.
The number of elements in v1 less than 10 is: 2.
*/
```

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<funkční >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)<br/>
