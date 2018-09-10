---
title: binder2nd – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- xfunctional/std::binder2nd
dev_langs:
- C++
helpviewer_keywords:
- binder2nd class
ms.assetid: b2a9c1d1-dfc4-4ca9-a10e-ae84e195a62d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 040687a4218f24bb57f20ea3307dbf69ffa3f37d
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44108394"
---
# <a name="binder2nd-class"></a>binder2nd – třída

Třída šablony poskytující konstruktor, který převádí objekt binární funkce na objekt jednočlenné funkce navázáním druhého argumentu binární funkce na zadanou hodnotu.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Operation>
class binder2nd
    : public unaryFunction <typename Operation::first_argument_type,
    typename Operation::result_type>
{
public:
    typedef typename Operation::argument_type argument_type;
    typedef typename Operation::result_type result_type;
    binder2nd(
        const Operation& Func,
        const typename Operation::second_argument_type& right);

    result_type operator()(const argument_type& left) const;
    result_type operator()(argument_type& left) const;

protected:
    Operation op;
    typename Operation::second_argument_type value;
};
```

### <a name="parameters"></a>Parametry

*Func*<br/>
Objekt binární funkce pro převod na objekt jednočlenné funkce.

*doprava*<br/>
Hodnota, na které má být vázaný druhého argumentu binární funkce na objekt.

*doleva*<br/>
Hodnota argumentu, který porovná objekt adaptovaného binární pevnou hodnotu druhého argumentu.

## <a name="return-value"></a>Návratová hodnota

Objekt jednočlenné funkce, která je výsledkem vazby druhého argumentu binární funkce na objekt na hodnotu *správné*.

## <a name="remarks"></a>Poznámky

Třída šablony ukládá jejich kopii _ objekt binární funkce *Func* v `op`a kopii *správné* v `value`. Definuje jeho členskou funkci `operator()` jako vracející **op**( `left`, **hodnotu**).

Pokud `Func` je objekt typu `Operation` a jazyka c je konstanta, pak [bind2nd –](../standard-library/functional-functions.md#bind2nd) ( `Func`, `c` ) odpovídá `binder2nd` konstruktoru třídy `binder2nd` \<  **Operace**> ( `Func`, `c` ) a pohodlnější.

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
