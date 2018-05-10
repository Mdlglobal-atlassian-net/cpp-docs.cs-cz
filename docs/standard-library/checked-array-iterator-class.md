---
title: checked_array_iterator – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- iterator/checked_array_iterator
- iterator/stdext::checked_array_iterator::difference_type
- iterator/stdext::checked_array_iterator::pointer
- iterator/stdext::checked_array_iterator::reference
- iterator/stdext::checked_array_iterator::base
dev_langs:
- C++
helpviewer_keywords:
- stdext::checked_array_iterator [C++], difference_type
- stdext::checked_array_iterator [C++], pointer
- stdext::checked_array_iterator [C++], reference
- stdext::checked_array_iterator [C++], base
ms.assetid: 7f07185e-d588-4ae3-9c4f-84ec4aa25a28
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 35ac7686706aad871b95f8b94d2bb11b459a64e8
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="checkedarrayiterator-class"></a>checked_array_iterator – třída

`checked_array_iterator` Třída umožňuje transformovat pole nebo ukazatel do zaškrtnutý iterátor. Tato třída slouží jako obálku (pomocí [make_checked_array_iterator](../standard-library/iterator-functions.md#make_checked_array_iterator) funkce) pro nezpracovanou ukazatele nebo pole jako cílové způsob zajistit kontroly a ke správě upozornění nezaškrtnuté ukazatel místo globálně silencing tato upozornění. Pokud třeba, můžete použít nezaškrtnuté verze této třídy [unchecked_array_iterator](../standard-library/unchecked-array-iterator-class.md).

> [!NOTE]
> Tato třída je rozšíření Microsoft standardní knihovny jazyka C++. Kód implementovaný pomocí této funkce není přenosný do standardního prostředí pro sestavování v jazyce C++, která toto rozšíření společnosti Microsoft nepodporují. Jak napsat kód, který nevyžaduje použití této třídy, viz druhý příklad.

## <a name="syntax"></a>Syntaxe

```cpp
template <class _Iterator>
class checked_array_iterator;
```

## <a name="remarks"></a>Poznámky

Tato třída je definována v [stdext –](../standard-library/stdext-namespace.md) oboru názvů.

Další informace a ukázkový kód na funkci zaškrtnuté iterator najdete v tématu [zaškrtnutí iterátory](../standard-library/checked-iterators.md).

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak definovat a používat iterátor zkontrolovaného pole.

Pokud cíl není dostatečně velký pro všechny prvky, které jsou kopírovány, jako by tomu bylo při změně řádku:

```cpp
copy(a, a + 5, checked_array_iterator<int*>(b, 5));
```

až

```cpp
copy(a, a + 5, checked_array_iterator<int*>(b, 4));
```

Dojde k chybě modulu runtime.

```cpp
// compile with: /EHsc /W4 /MTd
#include <algorithm>
#include <iostream>

using namespace std;
using namespace stdext;

int main() {
   int a[]={0, 1, 2, 3, 4};
   int b[5];
   copy(a, a + 5, checked_array_iterator<int*>(b, 5));

   cout << "(";
   for (int i = 0 ; i < 5 ; i++)
      cout << " " << b[i];
   cout << " )" << endl;

   // constructor example
   checked_array_iterator<int*> checked_out_iter(b, 5);
   copy(a, a + 5, checked_out_iter);

   cout << "(";
   for (int i = 0 ; i < 5 ; i++)
      cout << " " << b[i];
   cout << " )" << endl;
}
\* Output:
( 0 1 2 3 4 )
( 0 1 2 3 4 )
*\
```

## <a name="example"></a>Příklad

Aby se zabránilo potřebu `checked_array_iterator` třída při použití standardní knihovna C++ algoritmy, zvažte použití `vector` místo dynamicky přidělené pole. Následující příklad demonstruje, jak to udělat.

```cpp
// compile with: /EHsc /W4 /MTd

#include <algorithm>
#include <iostream>
#include <vector>

using namespace std;

int main()
{
    std::vector<int> v(10);
    int *arr = new int[10];
    for (int i = 0; i < 10; ++i)
    {
        v[i] = i;
        arr[i] = i;
    }

    // std::copy(v.begin(), v.end(), arr); will result in
    // warning C4996. To avoid this warning while using int *,
    // use the Microsoft extension checked_array_iterator.
    std::copy(v.begin(), v.end(),
              stdext::checked_array_iterator<int *>(arr, 10));

    // Instead of using stdext::checked_array_iterator and int *,
    // consider using std::vector to encapsulate the array. This will
    // result in no warnings, and the code will be portable.
    std::vector<int> arr2(10);    // Similar to int *arr = new int[10];
    std::copy(v.begin(), v.end(), arr2.begin());

    for (int j = 0; j < arr2.size(); ++j)
    {
        cout << " " << arr2[j];
    }
    cout << endl;

    return 0;
}
\* Output:
 0 1 2 3 4 5 6 7 8 9
*\
```

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[checked_array_iterator](#checked_array_iterator)|Vytvoří výchozí `checked_array_iterator` nebo `checked_array_iterator` ze základní iterator.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[difference_type](#difference_type)|Typ, který poskytuje rozdíl mezi dvěma `checked_array_iterator`s odkazy na elementy ve stejném kontejneru.|
|[Ukazatele](#pointer)|Typ, který poskytuje ukazatel na element používala `checked_array_iterator`.|
|[Referenční dokumentace](#reference)|Typ, který obsahuje odkaz na element používala `checked_array_iterator`.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[base](#base)|Obnoví základní iterator z jeho `checked_array_iterator`.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operator==](#op_eq_eq)|Dva testy `checked_array_iterator`s rovnosti.|
|[operator!=](#op_neq)|Dva testy `checked_array_iterator`s nerovnost.|
|[operátor <](#op_lt)|Pokud testy `checked_array_iterator` na levé straně operátoru je menší než `checked_array_iterator` na pravé straně.|
|[operátor >](#op_gt)|Pokud testy `checked_array_iterator` na levé straně operátoru je větší než `checked_array_iterator` na pravé straně.|
|[Operator < =](#op_lt_eq)|Testuje, pokud `checked_array_iterator` na levé straně operátoru je menší než nebo rovno `checked_array_iterator` na pravé straně.|
|[operator>=](#op_gt_eq)|Testuje, pokud `checked_array_iterator` na levé straně operátoru je větší než nebo rovno `checked_array_iterator` na pravé straně.|
|[operátor *](#op_star)|Vrátí prvek `checked_array_iterator` adresy.|
|[-> – operátor](#op_arrow)|Vrací ukazatel na element používala `checked_array_iterator`.|
|[Operator ++](#op_add_add)|Zvýší `checked_array_iterator` na další prvek.|
|[--– operátor](#operator--)|Snižuje `checked_array_iterator` do předchozí elementu.|
|[operator+=](#op_add_eq)|Přidá zadaný posun `checked_array_iterator`.|
|[operátor +](#op_add)|Přidá posun do iterovat a vrátí nové `checked_array_iterator` adresování vložené element na pozici posunutí nové.|
|[-= – operátor](#operator-_eq)|Snižuje zadaný posun od `checked_array_iterator`.|
|[Operator –](#operator-)|Snižuje na posun od iterovat a vrátí nové `checked_array_iterator` adresování vložené element na pozici posunutí nové.|
|[operátor&#91;&#93;](#op_at)|Vrátí odkaz na element posun z prvku používala `checked_array_iterator` o zadaný počet pozic.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<iterator >

**Namespace:** stdext –

## <a name="base"></a>  checked_array_iterator::Base

Obnoví základní iterator z jeho `checked_array_iterator`.

```cpp
_Iterator base() const;
```

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [zaškrtnutí iterátory](../standard-library/checked-iterators.md).

### <a name="example"></a>Příklad

```cpp
// checked_array_iterators_base.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main() {
   using namespace std;

   int V1[10];

   for (int i = 0; i < 10 ; i++)
      V1[i] = i;

   int* bpos;

   stdext::checked_array_iterator<int*> rpos(V1, 10);
   rpos++;

   bpos = rpos.base ( );
   cout << "The iterator underlying rpos is bpos & it points to: "
        << *bpos << "." << endl;
}
\* Output:
The iterator underlying rpos is bpos & it points to: 1.
*\
```

## <a name="checked_array_iterator"></a>  checked_array_iterator::checked_array_iterator

Vytvoří výchozí `checked_array_iterator` nebo `checked_array _iterator` ze základní iterator.

```cpp
checked_array_iterator();

checked_array_iterator(
    ITerator ptr,
    size_t size,
    size_t index = 0);
```

### <a name="parameters"></a>Parametry

`ptr` Ukazatel na pole.

`size` Velikost pole.

`index` (Volitelné) Element v poli, k chybě při inicializaci iteraci.  Ve výchozím nastavení iterace smyčky první prvek v poli.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [zaškrtnutí iterátory](../standard-library/checked-iterators.md).

### <a name="example"></a>Příklad

```cpp
// checked_array_iterators_ctor.cpp
// compile with: /EHsc
#include <iterator>
#include <iostream>

using namespace std;
using namespace stdext;

int main() {
   int a[] = {0, 1, 2, 3, 4};
   int b[5];
   copy(a, a + 5, checked_array_iterator<int*>(b,5));

   for (int i = 0 ; i < 5 ; i++)
      cout << b[i] << " ";
   cout << endl;

   checked_array_iterator<int*> checked_output_iterator(b,5);
   copy (a, a + 5, checked_output_iterator);
   for (int i = 0 ; i < 5 ; i++)
      cout << b[i] << " ";
   cout << endl;

   checked_array_iterator<int*> checked_output_iterator2(b,5,3);
   cout << *checked_output_iterator2 << endl;
}
\* Output:
0 1 2 3 4
0 1 2 3 4
3
*\
```

## <a name="difference_type"></a>  checked_array_iterator::difference_type

Typ, který poskytuje rozdíl mezi dvěma `checked_array_iterator`s odkazy na elementy ve stejném kontejneru.

```cpp
typedef typename iterator_traits<_Iterator>::difference_type difference_type;
```

### <a name="remarks"></a>Poznámky

`checked_array_iterator` Typ rozdíl je stejný jako typ iterator rozdíl.

V tématu [checked_array_iterator::operator []](#op_at) pro ukázku kódu.

Další informace najdete v tématu [zaškrtnutí iterátory](../standard-library/checked-iterators.md).

## <a name="op_eq_eq"></a>  checked_array_iterator::Operator ==

Dva testy `checked_array_iterator`s rovnosti.

```cpp
bool operator==(const checked_array_iterator<_Iterator>& right) const;
```

### <a name="parameters"></a>Parametry

`right` `checked_array_iterator` Vůči kterému chcete kontrolu rovnosti.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [zaškrtnutí iterátory](../standard-library/checked-iterators.md).

### <a name="example"></a>Příklad

```cpp
// checked_array_iterators_opeq.cpp
// compile with: /EHsc
#include <iterator>
#include <iostream>

using namespace std;
using namespace stdext;

int main() {
   int a[] = {0, 1, 2, 3, 4};
   int b[5];
   copy(a, a + 5, checked_array_iterator<int*>(b,5));
   copy(a, a + 5, checked_array_iterator<int*>(b,5));

   checked_array_iterator<int*> checked_output_iterator(b,5);
   checked_array_iterator<int*> checked_output_iterator2(b,5);

   if (checked_output_iterator2 == checked_output_iterator)
      cout << "checked_array_iterators are equal" << endl;
   else
      cout << "checked_array_iterators are not equal" << endl;

   copy (a, a + 5, checked_output_iterator);
   checked_output_iterator++;

   if (checked_output_iterator2 == checked_output_iterator)
      cout << "checked_array_iterators are equal" << endl;
   else
      cout << "checked_array_iterators are not equal" << endl;
}
\* Output:
checked_array_iterators are equal
checked_array_iterators are not equal
*\
```

## <a name="op_neq"></a>  checked_array_iterator::Operator! =

Dva testy `checked_array_iterator`s nerovnost.

```cpp
bool operator!=(const checked_array_iterator<_Iterator>& right) const;
```

### <a name="parameters"></a>Parametry

`right` `checked_array_iterator` Vůči kterému chcete zkontrolovat nerovnost.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [zaškrtnutí iterátory](../standard-library/checked-iterators.md).

### <a name="example"></a>Příklad

```cpp
// checked_array_iterators_opneq.cpp
// compile with: /EHsc
#include <iterator>
#include <iostream>

using namespace std;
using namespace stdext;

int main() {
   int a[] = {0, 1, 2, 3, 4};
   int b[5];
   copy(a, a + 5, checked_array_iterator<int*>(b,5));
   copy(a, a + 5, checked_array_iterator<int*>(b,5));

   checked_array_iterator<int*> checked_output_iterator(b,5);
   checked_array_iterator<int*> checked_output_iterator2(b,5);

   if (checked_output_iterator2 != checked_output_iterator)
      cout << "checked_array_iterators are not equal" << endl;
   else
      cout << "checked_array_iterators are equal" << endl;

   copy (a, a + 5, checked_output_iterator);
   checked_output_iterator++;

   if (checked_output_iterator2 != checked_output_iterator)
      cout << "checked_array_iterators are not equal" << endl;
   else
      cout << "checked_array_iterators are equal" << endl;
}
\* Output:
checked_array_iterators are equal
checked_array_iterators are not equal
*\
```

## <a name="op_lt"></a>  checked_array_iterator::Operator&lt;

Pokud testy `checked_array_iterator` na levé straně operátoru je menší než `checked_array_iterator` na pravé straně.

```cpp
bool operator<(const checked_array_iterator<_Iterator>& right) const;
```

### <a name="parameters"></a>Parametry

`right` `checked_array_iterator` Vůči kterému chcete zkontrolovat nerovnost.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [zaškrtnutí iterátory](../standard-library/checked-iterators.md).

### <a name="example"></a>Příklad

```cpp
// checked_array_iterators_oplt.cpp
// compile with: /EHsc
#include <iterator>
#include <iostream>

using namespace std;
using namespace stdext;

int main() {
   int a[] = {0, 1, 2, 3, 4};
   int b[5];
   copy(a, a + 5, checked_array_iterator<int*>(b,5));
   copy(a, a + 5, checked_array_iterator<int*>(b,5));

   checked_array_iterator<int*> checked_output_iterator(b,5);
   checked_array_iterator<int*> checked_output_iterator2(b,5);

   if (checked_output_iterator2 < checked_output_iterator)
      cout << "checked_output_iterator2 is less than checked_output_iterator" << endl;
   else
      cout << "checked_output_iterator2 is not less than checked_output_iterator" << endl;

   copy (a, a + 5, checked_output_iterator);
   checked_output_iterator++;

   if (checked_output_iterator2 < checked_output_iterator)
      cout << "checked_output_iterator2 is less than checked_output_iterator" << endl;
   else
      cout << "checked_output_iterator2 is not less than checked_output_iterator" << endl;
}
\* Output:
checked_output_iterator2 is not less than checked_output_iterator
checked_output_iterator2 is less than checked_output_iterator
*\
```

## <a name="op_gt"></a>  checked_array_iterator::Operator&gt;

Pokud testy `checked_array_iterator` na levé straně operátoru je větší než `checked_array_iterator` na pravé straně.

```cpp
bool operator>(const checked_array_iterator<_Iterator>& right) const;
```

### <a name="parameters"></a>Parametry

`right` `checked_array_iterator` Pro porovnání.

### <a name="remarks"></a>Poznámky

V tématu [checked_array_iterator::operator&lt; ](#op_lt) pro ukázku kódu.

Další informace najdete v tématu [zaškrtnutí iterátory](../standard-library/checked-iterators.md).

## <a name="lt_eq"></a>  checked_array_iterator::Operator&lt;=

Testuje, pokud `checked_array_iterator` na levé straně operátoru je menší než nebo rovno `checked_array_iterator` na pravé straně.

```cpp
bool operator<=(const checked_array_iterator<_Iterator>& right) const;
```

### <a name="parameters"></a>Parametry

`right` `checked_array_iterator` Pro porovnání.

### <a name="remarks"></a>Poznámky

V tématu [checked_array_iterator::operator&gt; = ](#op_gt_eq) pro ukázku kódu.

Další informace najdete v tématu [zaškrtnutí iterátory](../standard-library/checked-iterators.md).

## <a name="gt_eq"></a>  checked_array_iterator::Operator&gt;=

Testuje, pokud `checked_array_iterator` na levé straně operátoru je větší než nebo rovno `checked_array_iterator` na pravé straně.

```cpp
bool operator>=(const checked_array_iterator<_Iterator>& right) const;
```

### <a name="parameters"></a>Parametry

`right` `checked_array_iterator` Pro porovnání.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [zaškrtnutí iterátory](../standard-library/checked-iterators.md).

### <a name="example"></a>Příklad

```cpp
// checked_array_iterators_opgteq.cpp
// compile with: /EHsc
#include <iterator>
#include <iostream>

using namespace std;
using namespace stdext;

int main() {
   int a[] = {0, 1, 2, 3, 4};
   int b[5];
   copy(a, a + 5, checked_array_iterator<int*>(b,5));
   copy(a, a + 5, checked_array_iterator<int*>(b,5));

   checked_array_iterator<int*> checked_output_iterator(b,5);
   checked_array_iterator<int*> checked_output_iterator2(b,5);

   if (checked_output_iterator2 >= checked_output_iterator)
      cout << "checked_output_iterator2 is greater than or equal to checked_output_iterator" << endl;
   else
      cout << "checked_output_iterator2 is less than checked_output_iterator" << endl;

   copy (a, a + 5, checked_output_iterator);
   checked_output_iterator++;

   if (checked_output_iterator2 >= checked_output_iterator)
      cout << "checked_output_iterator2 is greater than or equal to checked_output_iterator" << endl;
   else
      cout << "checked_output_iterator2 is less than checked_output_iterator" << endl;
}
\* Output:
checked_output_iterator2 is greater than or equal to checked_output_iterator
checked_output_iterator2 is less than checked_output_iterator
*\
```

## <a name="op_star"></a>  checked_array_iterator::Operator *

Vrátí prvek `checked_array_iterator` adresy.

```cpp
reference operator*() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota elementu používala `checked_array_iterator`.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [zaškrtnutí iterátory](../standard-library/checked-iterators.md).

### <a name="example"></a>Příklad

```cpp
// checked_array_iterator_pointer.cpp
// compile with: /EHsc
#include <iterator>
#include <algorithm>
#include <vector>
#include <utility>
#include <iostream>

using namespace std;
using namespace stdext;

int main() {
   int a[] = {0, 1, 2, 3, 4};
   int b[5];
   pair<int, int> c[1];
   copy(a, a + 5, checked_array_iterator<int*>(b,5));

   for (int i = 0 ; i < 5 ; i++)
      cout << b[i] << endl;

    c[0].first = 10;
    c[0].second = 20;

   checked_array_iterator<int*> checked_output_iterator(b,5);
   checked_array_iterator<int*>::pointer p = &(*checked_output_iterator);
   checked_array_iterator<pair<int, int>*> chk_c(c, 1);
   checked_array_iterator<pair<int, int>*>::pointer p_c = &(*chk_c);

   cout << "b[0] = " << *p << endl;
   cout << "c[0].first = " << p_c->first << endl;
}
\* Output:
0
1
2
3
4
b[0] = 0
c[0].first = 10
*\
```

## <a name="op_arrow"></a>  checked_array_iterator::Operator-&gt;

Vrací ukazatel na element používala `checked_array_iterator`.

```cpp
pointer operator->() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na element používala `checked_array_iterator`.

### <a name="remarks"></a>Poznámky

V tématu [checked_array_iterator::pointer](#pointer) pro ukázku kódu.

Další informace najdete v tématu [zaškrtnutí iterátory](../standard-library/checked-iterators.md).

## <a name="op_add_add"></a>  checked_array_iterator::Operator ++

Zvýší `checked_array_iterator` na další prvek.

```cpp
checked_array_iterator& operator++();

checked_array_iterator<_Iterator> operator++(int);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí první operátor preincremented `checked_array_iterator` a druhý, postincrement operátor kopii zvýšena `checked_array_iterator`.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [zaškrtnutí iterátory](../standard-library/checked-iterators.md).

### <a name="example"></a>Příklad

```cpp
// checked_array_iterators_op_plus_plus.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main() {
   using namespace stdext;
   using namespace std;
   int a[] = {6, 3, 77, 199, 222};
   int b[5];
   copy(a, a + 5, checked_array_iterator<int*>(b,5));

   checked_array_iterator<int*> checked_output_iterator(b,5);

   cout << *checked_output_iterator << endl;
   ++checked_output_iterator;
   cout << *checked_output_iterator << endl;
   checked_output_iterator++;
   cout << *checked_output_iterator << endl;
}
\* Output:
6
3
77
*\
```

## <a name="checked_array_iterator__operator--"></a>  checked_array_iterator::Operator--

Snižuje `checked_array_iterator` do předchozí elementu.

```cpp
checked_array_iterator<_Iterator>& operator--();

checked_array_iterator<_Iterator> operator--(int);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí první operátor predecremented `checked_array_iterator` a druhý, postdecrement operátor kopii odečte `checked_array_iterator`.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [zaškrtnutí iterátory](../standard-library/checked-iterators.md).

### <a name="example"></a>Příklad

```cpp
// checked_array_iterators_op_minus_minus.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main() {
   using namespace stdext;
   using namespace std;
   int a[] = {6, 3, 77, 199, 222};
   int b[5];
   copy(a, a + 5, checked_array_iterator<int*>(b,5));

   checked_array_iterator<int*> checked_output_iterator(b,5);

   cout << *checked_output_iterator << endl;
   checked_output_iterator++;
   cout << *checked_output_iterator << endl;
   checked_output_iterator--;
   cout << *checked_output_iterator << endl;
}
\* Output:
6
3
6
*\
```

## <a name="op_add_eq"></a>  checked_array_iterator::Operator +=

Přidá zadaný posun `checked_array_iterator`.

```cpp
checked_array_iterator<_Iterator>& operator+=(difference_type _Off);
```

### <a name="parameters"></a>Parametry

`_Off` Posun, podle kterého se zvýší iterator.

### <a name="return-value"></a>Návratová hodnota

Odkaz na element používala `checked_array_iterator`.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [zaškrtnutí iterátory](../standard-library/checked-iterators.md).

### <a name="example"></a>Příklad

```cpp
// checked_array_iterators_op_plus_eq.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main() {
   using namespace stdext;
   using namespace std;
   int a[] = {6, 3, 77, 199, 222};
   int b[5];
   copy(a, a + 5, checked_array_iterator<int*>(b,5));

   checked_array_iterator<int*> checked_output_iterator(b,5);

   cout << *checked_output_iterator << endl;
   checked_output_iterator += 3;
   cout << *checked_output_iterator << endl;
}
\* Output:
6
199
*\
```

## <a name="op_add"></a>  checked_array_iterator::Operator +

Přidá posun do iterovat a vrátí nové `checked_array_iterator` adresování vložené element na pozici posunutí nové.

```cpp
checked_array_iterator<_Iterator> operator+(difference_type _Off) const;
```

### <a name="parameters"></a>Parametry

`_Off` Posun pro přidání do `checked_array_iterator`.

### <a name="return-value"></a>Návratová hodnota

A `checked_array_iterator` adresování posunutí elementu.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [zaškrtnutí iterátory](../standard-library/checked-iterators.md).

### <a name="example"></a>Příklad

```cpp
// checked_array_iterators_op_plus.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main() {
   using namespace stdext;
   using namespace std;
   int a[] = {6, 3, 77, 199, 222};
   int b[5];
   copy(a, a + 5, checked_array_iterator<int*>(b,5));

   checked_array_iterator<int*> checked_output_iterator(b,5);

   cout << *checked_output_iterator << endl;
   checked_output_iterator = checked_output_iterator + 3;
   cout << *checked_output_iterator << endl;
}
\* Output:
6
199
*\
```

## <a name="checked_array_iterator__operator-_eq"></a>  checked_array_iterator::Operator-=

Snižuje zadaný posun od `checked_array_iterator`.

```cpp
checked_array_iterator<_Iterator>& operator-=(difference_type _Off);
```

### <a name="parameters"></a>Parametry

`_Off` Posun, podle kterého se zvýší iterator.

### <a name="return-value"></a>Návratová hodnota

Odkaz na element používala `checked_array_iterator`.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [zaškrtnutí iterátory](../standard-library/checked-iterators.md).

### <a name="example"></a>Příklad

```cpp
// checked_array_iterators_op_minus_eq.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main() {
   using namespace stdext;
   using namespace std;
   int a[] = {6, 3, 77, 199, 222};
   int b[5];
   copy(a, a + 5, checked_array_iterator<int*>(b,5));

   checked_array_iterator<int*> checked_output_iterator(b,5);

   checked_output_iterator += 3;
   cout << *checked_output_iterator << endl;
   checked_output_iterator -= 2;
   cout << *checked_output_iterator << endl;
}
\* Output:
199
3
*\
```

## <a name="checked_array_iterator__operator-"></a>  checked_array_iterator::Operator-

Snižuje na posun od iterovat a vrátí nové `checked_array_iterator` adresování vložené element na pozici posunutí nové.

```cpp
checked_array_iterator<_Iterator> operator-(difference_type _Off) const;

difference_type operator-(const checked_array_iterator& right) const;
```

### <a name="parameters"></a>Parametry

`_Off` Posun se odečte od `checked_array_iterator`.

### <a name="return-value"></a>Návratová hodnota

A `checked_array_iterator` adresování posunutí elementu.

### <a name="remarks"></a>Poznámky

V tématu [checked_array_iterator::operator -](#operator-) pro ukázku kódu.

Další informace najdete v tématu [zaškrtnutí iterátory](../standard-library/checked-iterators.md).

## <a name="op_at"></a>  checked_array_iterator::Operator]

Vrátí odkaz na element posun z prvku používala `checked_array_iterator` o zadaný počet pozic.

```cpp
reference operator[](difference_type _Off) const;
```

### <a name="parameters"></a>Parametry

`_Off` Posun od `checked_array_iterator` adresu.

### <a name="return-value"></a>Návratová hodnota

Odkaz na element posun.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [zaškrtnutí iterátory](../standard-library/checked-iterators.md).

### <a name="example"></a>Příklad

```cpp
// checked_array_iterators_op_diff.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main() {
   using namespace std;
   int V1[10];

   for (int i = 0; i < 10 ; i++)
      V1[i] = i;

   // Declare a difference type for a parameter
   stdext::checked_array_iterator<int*>::difference_type diff = 2;

   stdext::checked_array_iterator<int*> VChkIter(V1, 10);

   stdext::checked_array_iterator<int*>::reference refrpos = VChkIter [diff];

   cout << refrpos + 1 << endl;
}
\* Output:
3
*\
```

## <a name="pointer"></a>  checked_array_iterator::Pointer

Typ, který poskytuje ukazatel na element používala `checked_array_iterator`.

```cpp
typedef typename iterator_traits<_Iterator>::pointer pointer;
```

### <a name="remarks"></a>Poznámky

V tématu [checked_array_iterator::operator *](#op_star) pro ukázku kódu.

Další informace najdete v tématu [zaškrtnutí iterátory](../standard-library/checked-iterators.md).

## <a name="reference"></a>  checked_array_iterator::Reference

Typ, který obsahuje odkaz na element používala `checked_array_iterator`.

```cpp
typedef typename iterator_traits<_Iterator>::reference reference;
```

### <a name="remarks"></a>Poznámky

V tématu [checked_array_iterator::operator []](#op_at) pro ukázku kódu.

Další informace najdete v tématu [zaškrtnutí iterátory](../standard-library/checked-iterators.md).

## <a name="see-also"></a>Viz také

[\<iterator >](../standard-library/iterator.md)<br/>
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)<br/>
