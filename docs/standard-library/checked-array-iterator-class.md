---
title: checked_array_iterator – třída
ms.date: 03/27/2019
f1_keywords:
- iterator/checked_array_iterator
- iterator/stdext::checked_array_iterator::difference_type
- iterator/stdext::checked_array_iterator::pointer
- iterator/stdext::checked_array_iterator::reference
- iterator/stdext::checked_array_iterator::base
helpviewer_keywords:
- stdext::checked_array_iterator [C++], difference_type
- stdext::checked_array_iterator [C++], pointer
- stdext::checked_array_iterator [C++], reference
- stdext::checked_array_iterator [C++], base
ms.assetid: 7f07185e-d588-4ae3-9c4f-84ec4aa25a28
ms.openlocfilehash: f177a45e700ab15852cd9c6d947873d247cf3828
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363866"
---
# <a name="checked_array_iterator-class"></a>checked_array_iterator – třída

Třída `checked_array_iterator` umožňuje transformovat pole nebo ukazatel do zaškrtnuté iterátoru. Tuto třídu použijte jako obálku (pomocí [funkce make_checked_array_iterator)](../standard-library/iterator-functions.md#make_checked_array_iterator) pro nezpracované ukazatele nebo pole jako cílený způsob, jak zajistit kontrolu a spravovat nekontrolovaná upozornění ukazatele namísto globálního umlčení těchto upozornění. V případě potřeby můžete použít nekontrolovnou verzi této [třídy, unchecked_array_iterator](../standard-library/unchecked-array-iterator-class.md).

> [!NOTE]
> Tato třída je rozšíření Microsoft standardní knihovny C++. Kód implementovaný pomocí této funkce není přenosný do standardního prostředí pro sestavování v jazyce C++, která toto rozšíření společnosti Microsoft nepodporují. Jak napsat kód, který nevyžaduje použití této třídy, viz druhý příklad.

## <a name="syntax"></a>Syntaxe

```cpp
template <class _Iterator>
class checked_array_iterator;
```

## <a name="remarks"></a>Poznámky

Tato třída je definována v oboru názvů [stdext.](../standard-library/stdext-namespace.md)

Další informace a ukázkový kód v kontrolované funkci iterátoru naleznete [v tématu Checked Iterators](../standard-library/checked-iterators.md).

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak definovat a používat iterátor zkontrolovaného pole.

Pokud cíl není dostatečně velký pro všechny prvky, které jsou kopírovány, jako by tomu bylo při změně řádku:

```cpp
copy(a, a + 5, checked_array_iterator<int*>(b, 5));
```

na

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
/* Output:
( 0 1 2 3 4 )
( 0 1 2 3 4 )
*/
```

## <a name="example"></a>Příklad

Chcete-li se `checked_array_iterator` vyhnout nutnosti třídy při použití algoritmů `vector` standardní knihovny jazyka C++, zvažte použití místo dynamicky přiděleného pole. Následující příklad demonstruje, jak to udělat.

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
/* Output:
0 1 2 3 4 5 6 7 8 9
*/
```

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[checked_array_iterator](#checked_array_iterator)|Vytvoří výchozí `checked_array_iterator` nebo `checked_array_iterator` z podkladového iterátoru.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[difference_type](#difference_type)|Typ, který poskytuje rozdíl `checked_array_iterator`mezi dvěma s odkazující na prvky v rámci stejného kontejneru.|
|[ukazatel](#pointer)|Typ, který poskytuje ukazatel na prvek `checked_array_iterator`adresovaný .|
|[Odkaz](#reference)|Typ, který poskytuje odkaz na prvek `checked_array_iterator`adresovaný .|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[base](#base)|Obnoví základní iterátor z `checked_array_iterator`jeho .|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operátor==](#op_eq_eq)|Testuje `checked_array_iterator`dva s pro rovnost.|
|[operátor!=](#op_neq)|Testy `checked_array_iterator`dva s pro nerovnost.|
|[operátor<](#op_lt)|Zkoušky, `checked_array_iterator` pokud je na levé straně operátora menší než `checked_array_iterator` na pravé straně.|
|[operátor>](#op_gt)|Testuje, `checked_array_iterator` zda je na levé straně operátora větší než `checked_array_iterator` na pravé straně.|
|[operátor<=](#op_lt_eq)|Zkoušky, `checked_array_iterator` pokud na levé straně operátora je menší `checked_array_iterator` nebo rovno na pravé straně.|
|[operátor>=](#op_gt_eq)|Zkoušky, `checked_array_iterator` pokud na levé straně operátoru je větší `checked_array_iterator` nebo rovna na pravé straně.|
|[operátor*](#op_star)|Vrátí prvek, `checked_array_iterator` který adresy.|
|[operátor->](#op_arrow)|Vrátí ukazatel na prvek, který `checked_array_iterator`je adresován rozhraním .|
|[operátor++](#op_add_add)|Zintáží `checked_array_iterator` na další prvek.|
|[operátora--](#operator--)|Sníží `checked_array_iterator` na předchozí prvek.|
|[operátor+=](#op_add_eq)|Přidá zadaný posun `checked_array_iterator`do .|
|[operátor+](#op_add)|Přidá posun do iterátoru a `checked_array_iterator` vrátí nové adresování vloženého prvku v nové pozici odsazení.|
|[operátor-=](#operator-_eq)|Sníží zadaný posun od `checked_array_iterator`.|
|[operátor-](#operator-)|Sníží posun od iterátoru a vrátí nové `checked_array_iterator` adresování vloženého prvku v nové pozici odsazení.|
|[operátor&#91;&#93;](#op_at)|Vrátí odkaz na posun prvku od prvku `checked_array_iterator` adresovaného a o zadaný počet pozic.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<> iterátoru

**Obor názvů:** stdext

## <a name="checked_array_iteratorbase"></a><a name="base"></a>checked_array_iterator::základna

Obnoví základní iterátor z `checked_array_iterator`jeho .

```cpp
_Iterator base() const;
```

### <a name="remarks"></a>Poznámky

Další informace naleznete [v tématu Checked Iterators](../standard-library/checked-iterators.md).

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
/* Output:
The iterator underlying rpos is bpos & it points to: 1.
*/
```

## <a name="checked_array_iteratorchecked_array_iterator"></a><a name="checked_array_iterator"></a>checked_array_iterator::checked_array_iterator

Vytvoří výchozí `checked_array_iterator` nebo `checked_array _iterator` z podkladového iterátoru.

```cpp
checked_array_iterator();

checked_array_iterator(
    ITerator ptr,
    size_t size,
    size_t index = 0);
```

### <a name="parameters"></a>Parametry

*Ptr*\
Ukazatel na pole.

*Velikost*\
Velikost pole.

*Index*\
(Nepovinné) Prvek v poli, chcete-li inicializovat iterátor.  Ve výchozím nastavení je iterátor inicializován na první prvek v poli.

### <a name="remarks"></a>Poznámky

Další informace naleznete [v tématu Checked Iterators](../standard-library/checked-iterators.md).

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
/* Output:
0 1 2 3 4
0 1 2 3 4
3
*/
```

## <a name="checked_array_iteratordifference_type"></a><a name="difference_type"></a>checked_array_iterator::difference_type

Typ, který poskytuje rozdíl `checked_array_iterator`mezi dvěma s odkazující na prvky v rámci stejného kontejneru.

```cpp
typedef typename iterator_traits<_Iterator>::difference_type difference_type;
```

### <a name="remarks"></a>Poznámky

Typ `checked_array_iterator` rozdílu je stejný jako typ rozdílu iterátoru.

Ukázku kódu naleznete [checked_array_iterator::operator[].](#op_at)

Další informace naleznete [v tématu Checked Iterators](../standard-library/checked-iterators.md).

## <a name="checked_array_iteratoroperator"></a><a name="op_eq_eq"></a>checked_array_iterator::operátor==

Testuje `checked_array_iterator`dva s pro rovnost.

```cpp
bool operator==(const checked_array_iterator<_Iterator>& right) const;
```

### <a name="parameters"></a>Parametry

*Právo*\
Proti `checked_array_iterator` kterému ke kontrole rovnosti.

### <a name="remarks"></a>Poznámky

Další informace naleznete [v tématu Checked Iterators](../standard-library/checked-iterators.md).

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
/* Output:
checked_array_iterators are equal
checked_array_iterators are not equal
*/
```

## <a name="checked_array_iteratoroperator"></a><a name="op_neq"></a>checked_array_iterator::operátor!=

Testy `checked_array_iterator`dva s pro nerovnost.

```cpp
bool operator!=(const checked_array_iterator<_Iterator>& right) const;
```

### <a name="parameters"></a>Parametry

*Právo*\
Proti `checked_array_iterator` kterému kontrolovat nerovnost.

### <a name="remarks"></a>Poznámky

Další informace naleznete [v tématu Checked Iterators](../standard-library/checked-iterators.md).

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
/* Output:
checked_array_iterators are equal
checked_array_iterators are not equal
*/
```

## <a name="checked_array_iteratoroperatorlt"></a><a name="op_lt"></a>checked_array_iterator::operátor&lt;

Zkoušky, `checked_array_iterator` pokud je na levé straně operátora menší než `checked_array_iterator` na pravé straně.

```cpp
bool operator<(const checked_array_iterator<_Iterator>& right) const;
```

### <a name="parameters"></a>Parametry

*Právo*\
Proti `checked_array_iterator` kterému kontrolovat nerovnost.

### <a name="remarks"></a>Poznámky

Další informace naleznete [v tématu Checked Iterators](../standard-library/checked-iterators.md).

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
/* Output:
checked_output_iterator2 is not less than checked_output_iterator
checked_output_iterator2 is less than checked_output_iterator
*/
```

## <a name="checked_array_iteratoroperatorgt"></a><a name="op_gt"></a>checked_array_iterator::operátor&gt;

Testuje, `checked_array_iterator` zda je na levé straně operátora větší než `checked_array_iterator` na pravé straně.

```cpp
bool operator>(const checked_array_iterator<_Iterator>& right) const;
```

### <a name="parameters"></a>Parametry

*Právo*\
Porovnat `checked_array_iterator` proti.

### <a name="remarks"></a>Poznámky

Viz [checked_array_iterator::operátor&lt; ](#op_lt) pro ukázku kódu.

Další informace naleznete [v tématu Checked Iterators](../standard-library/checked-iterators.md).

## <a name="checked_array_iteratoroperatorlt"></a><a name="op_lt_eq"></a>checked_array_iterator::operátor&lt;=

Zkoušky, `checked_array_iterator` pokud na levé straně operátora je menší `checked_array_iterator` nebo rovno na pravé straně.

```cpp
bool operator<=(const checked_array_iterator<_Iterator>& right) const;
```

### <a name="parameters"></a>Parametry

*Právo*\
Porovnat `checked_array_iterator` proti.

### <a name="remarks"></a>Poznámky

Viz [checked_array_iterator::operátor&gt; ](#op_gt_eq) pro ukázku kódu.

Další informace naleznete [v tématu Checked Iterators](../standard-library/checked-iterators.md).

## <a name="checked_array_iteratoroperatorgt"></a><a name="op_gt_eq"></a>checked_array_iterator::operátor&gt;=

Zkoušky, `checked_array_iterator` pokud na levé straně operátoru je větší `checked_array_iterator` nebo rovna na pravé straně.

```cpp
bool operator>=(const checked_array_iterator<_Iterator>& right) const;
```

### <a name="parameters"></a>Parametry

*Právo*\
Porovnat `checked_array_iterator` proti.

### <a name="remarks"></a>Poznámky

Další informace naleznete [v tématu Checked Iterators](../standard-library/checked-iterators.md).

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
/* Output:
checked_output_iterator2 is greater than or equal to checked_output_iterator
checked_output_iterator2 is less than checked_output_iterator
*/
```

## <a name="checked_array_iteratoroperator"></a><a name="op_star"></a>checked_array_iterator::operátor*

Vrátí prvek, `checked_array_iterator` který adresy.

```cpp
reference operator*() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota prvku, který je `checked_array_iterator`adresován .

### <a name="remarks"></a>Poznámky

Další informace naleznete [v tématu Checked Iterators](../standard-library/checked-iterators.md).

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
/* Output:
0
1
2
3
4
b[0] = 0
c[0].first = 10
*/
```

## <a name="checked_array_iteratoroperator-gt"></a><a name="op_arrow"></a>checked_array_iterator::operátor-&gt;

Vrátí ukazatel na prvek, který `checked_array_iterator`je adresován rozhraním .

```cpp
pointer operator->() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na prvek, který `checked_array_iterator`je adresován rozhraním .

### <a name="remarks"></a>Poznámky

Viz [checked_array_iterator::pointer](#pointer) pro ukázku kódu.

Další informace naleznete [v tématu Checked Iterators](../standard-library/checked-iterators.md).

## <a name="checked_array_iteratoroperator"></a><a name="op_add_add"></a>checked_array_iterator::operátor++

Zintáží `checked_array_iterator` na další prvek.

```cpp
checked_array_iterator& operator++();

checked_array_iterator<_Iterator> operator++(int);
```

### <a name="return-value"></a>Návratová hodnota

První operátor vrátí preincremented `checked_array_iterator` a druhý, operátor postincrement, vrátí kopii `checked_array_iterator`přírůstku .

### <a name="remarks"></a>Poznámky

Další informace naleznete [v tématu Checked Iterators](../standard-library/checked-iterators.md).

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
/* Output:
6
3
77
*/
```

## <a name="checked_array_iteratoroperator--"></a><a name="operator--"></a>checked_array_iterator::operátor--

Sníží `checked_array_iterator` na předchozí prvek.

```cpp
checked_array_iterator<_Iterator>& operator--();

checked_array_iterator<_Iterator> operator--(int);
```

### <a name="return-value"></a>Návratová hodnota

První operátor vrátí predecremented `checked_array_iterator` a druhý, operátor postdecrement, vrátí kopii `checked_array_iterator`dekreed .

### <a name="remarks"></a>Poznámky

Další informace naleznete [v tématu Checked Iterators](../standard-library/checked-iterators.md).

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
/* Output:
6
3
6
*/
```

## <a name="checked_array_iteratoroperator"></a><a name="op_add_eq"></a>checked_array_iterator::operátor+=

Přidá zadaný posun `checked_array_iterator`do .

```cpp
checked_array_iterator<_Iterator>& operator+=(difference_type _Off);
```

### <a name="parameters"></a>Parametry

*_Off*\
Posun, o který chcete posít iterátor.

### <a name="return-value"></a>Návratová hodnota

Odkaz na prvek, na `checked_array_iterator`který se vztahuje rozhraní .

### <a name="remarks"></a>Poznámky

Další informace naleznete [v tématu Checked Iterators](../standard-library/checked-iterators.md).

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
/* Output:
6
199
*/
```

## <a name="checked_array_iteratoroperator"></a><a name="op_add"></a>checked_array_iterator::operátor+

Přidá posun do iterátoru a `checked_array_iterator` vrátí nové adresování vloženého prvku v nové pozici odsazení.

```cpp
checked_array_iterator<_Iterator> operator+(difference_type _Off) const;
```

### <a name="parameters"></a>Parametry

*_Off*\
Posun, který má `checked_array_iterator`být přidán do .

### <a name="return-value"></a>Návratová hodnota

Adresování `checked_array_iterator` prvek posun.

### <a name="remarks"></a>Poznámky

Další informace naleznete [v tématu Checked Iterators](../standard-library/checked-iterators.md).

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
/* Output:
6
199
*/
```

## <a name="checked_array_iteratoroperator-"></a><a name="operator-_eq"></a>checked_array_iterator::operátor-=

Sníží zadaný posun od `checked_array_iterator`.

```cpp
checked_array_iterator<_Iterator>& operator-=(difference_type _Off);
```

### <a name="parameters"></a>Parametry

*_Off*\
Posun, o který chcete posít iterátor.

### <a name="return-value"></a>Návratová hodnota

Odkaz na prvek, na `checked_array_iterator`který se vztahuje rozhraní .

### <a name="remarks"></a>Poznámky

Další informace naleznete [v tématu Checked Iterators](../standard-library/checked-iterators.md).

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
/* Output:
199
3
*/
```

## <a name="checked_array_iteratoroperator-"></a><a name="operator-"></a>checked_array_iterator::operátor-

Sníží posun od iterátoru a vrátí nové `checked_array_iterator` adresování vloženého prvku v nové pozici odsazení.

```cpp
checked_array_iterator<_Iterator> operator-(difference_type _Off) const;

difference_type operator-(const checked_array_iterator& right) const;
```

### <a name="parameters"></a>Parametry

*_Off*\
Posun, který má být snížen `checked_array_iterator`z .

### <a name="return-value"></a>Návratová hodnota

Adresování `checked_array_iterator` prvek posun.

### <a name="remarks"></a>Poznámky

Další informace naleznete [v tématu Checked Iterators](../standard-library/checked-iterators.md).

## <a name="checked_array_iteratoroperator"></a><a name="op_at"></a>checked_array_iterator::operátor[]

Vrátí odkaz na posun prvku od prvku `checked_array_iterator` adresovaného a o zadaný počet pozic.

```cpp
reference operator[](difference_type _Off) const;
```

### <a name="parameters"></a>Parametry

*_Off*\
Posun od `checked_array_iterator` adresy.

### <a name="return-value"></a>Návratová hodnota

Odkaz na posun prvku.

### <a name="remarks"></a>Poznámky

Další informace naleznete [v tématu Checked Iterators](../standard-library/checked-iterators.md).

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
/* Output:
3
*/
```

## <a name="checked_array_iteratorpointer"></a><a name="pointer"></a>checked_array_iterator::pointer

Typ, který poskytuje ukazatel na prvek `checked_array_iterator`adresovaný .

```cpp
typedef typename iterator_traits<_Iterator>::pointer pointer;
```

### <a name="remarks"></a>Poznámky

Ukázku kódu naleznete [checked_array_iterator::operator*.](#op_star)

Další informace naleznete [v tématu Checked Iterators](../standard-library/checked-iterators.md).

## <a name="checked_array_iteratorreference"></a><a name="reference"></a>checked_array_iterator::odkaz

Typ, který poskytuje odkaz na prvek `checked_array_iterator`adresovaný .

```cpp
typedef typename iterator_traits<_Iterator>::reference reference;
```

### <a name="remarks"></a>Poznámky

Ukázku kódu naleznete [checked_array_iterator::operator[].](#op_at)

Další informace naleznete [v tématu Checked Iterators](../standard-library/checked-iterators.md).

## <a name="see-also"></a>Viz také

[\<>iterátoru](../standard-library/iterator.md)\
[Referenční příručka standardní knihovny jazyka C++](../standard-library/cpp-standard-library-reference.md)
