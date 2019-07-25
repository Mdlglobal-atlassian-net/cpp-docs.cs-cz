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
ms.openlocfilehash: 68ee602c44a8515e1d41f04a4bd0fbb7edc924b7
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68452299"
---
# <a name="checkedarrayiterator-class"></a>checked_array_iterator – třída

`checked_array_iterator` Třída umožňuje transformovat pole nebo ukazatel na kontrolovaný iterátor. Tuto třídu můžete použít jako obálku (pomocí funkce [make_checked_array_iterator](../standard-library/iterator-functions.md#make_checked_array_iterator) ) pro nezpracované ukazatele nebo pole jako cílový způsob, jak poskytnout kontrolu a spravovat nezaškrtnutá upozornění na ukazatele namísto globálně vyměření těchto upozornění. V případě potřeby můžete použít nekontrolované verze této třídy [unchecked_array_iterator](../standard-library/unchecked-array-iterator-class.md).

> [!NOTE]
> Tato třída je rozšířením společnosti Microsoft pro C++ standardní knihovnu. Kód implementovaný pomocí této funkce není přenosný do standardního prostředí pro sestavování v jazyce C++, která toto rozšíření společnosti Microsoft nepodporují. Jak napsat kód, který nevyžaduje použití této třídy, viz druhý příklad.

## <a name="syntax"></a>Syntaxe

```cpp
template <class _Iterator>
class checked_array_iterator;
```

## <a name="remarks"></a>Poznámky

Tato třída je definována v oboru názvů [stdext](../standard-library/stdext-namespace.md) .

Další informace a příklad kódu pro funkci kontrolovaného iterátoru najdete v tématu [kontrolované iterátory](../standard-library/checked-iterators.md).

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
/* Output:
( 0 1 2 3 4 )
( 0 1 2 3 4 )
*/
```

## <a name="example"></a>Příklad

Chcete-li se vyhnout potřebě `checked_array_iterator` třídy při použití C++ algoritmů standardní knihovny `vector` , zvažte použití namísto dynamicky přiděleného pole. Následující příklad demonstruje, jak to udělat.

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
|[checked_array_iterator](#checked_array_iterator)|Vytvoří výchozí `checked_array_iterator` `checked_array_iterator` nebo ze základního iterátoru.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[difference_type](#difference_type)|Typ, který poskytuje rozdíl mezi dvěma `checked_array_iterator`s odkazujícími na prvky v rámci stejného kontejneru.|
|[pointer](#pointer)|Typ, který poskytuje ukazatel na prvek řešený `checked_array_iterator`.|
|[Referenční dokumentace](#reference)|Typ, který poskytuje odkaz na prvek řešený `checked_array_iterator`.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[base](#base)|Obnoví základní iterátor z jeho `checked_array_iterator`.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operator==](#op_eq_eq)|Testuje dva `checked_array_iterator`s pro rovnost.|
|[operator!=](#op_neq)|Testuje dva `checked_array_iterator`s pro nerovnost.|
|[operátor <](#op_lt)|Testuje, `checked_array_iterator` zda je na levé straně operátoru menší `checked_array_iterator` než na pravé straně.|
|[operátor >](#op_gt)|Testuje, `checked_array_iterator` zda je na levé straně operátoru větší `checked_array_iterator` než na pravé straně.|
|[operátor < =](#op_lt_eq)|Testuje, `checked_array_iterator` zda je na levé straně operátoru menší než nebo rovno `checked_array_iterator` na pravé straně.|
|[operator>=](#op_gt_eq)|Testuje, `checked_array_iterator` zda je na levé straně operátoru větší než nebo rovno `checked_array_iterator` na pravé straně.|
|[podnikatel](#op_star)|Vrátí prvek, který obsahuje `checked_array_iterator` adresy.|
|[operátor->](#op_arrow)|Vrátí ukazatel na prvek řešený `checked_array_iterator`.|
|[operator + + – operátor](#op_add_add)|Přivýší `checked_array_iterator` k dalšímu prvku.|
|[--– operátor](#operator--)|`checked_array_iterator` Sníží na předchozí prvek.|
|[operator+=](#op_add_eq)|Přidá zadaný posun k `checked_array_iterator`.|
|[operator + – operátor](#op_add)|Přidá posun k iterátoru a vrátí nový `checked_array_iterator` adresující vložený prvek na nové pozici posunu.|
|[operator-=](#operator-_eq)|Sníží zadaný posun z `checked_array_iterator`.|
|[podnikatel](#operator-)|Sníží posun z iterátoru a vrátí nový `checked_array_iterator` adresující vložený prvek na nové pozici posunu.|
|[podnikatel&#91;&#93;](#op_at)|Vrátí odkaz na posun prvku z prvku, který adresuje `checked_array_iterator` podle zadaného počtu pozic.|

## <a name="requirements"></a>Požadavky

**Hlavička:** \<iterátor >

**Obor názvů:** stdext

## <a name="base"></a>checked_array_iterator:: Base

Obnoví základní iterátor z jeho `checked_array_iterator`.

```cpp
_Iterator base() const;
```

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [kontrolované iterátory](../standard-library/checked-iterators.md).

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

## <a name="checked_array_iterator"></a>checked_array_iterator::checked_array_iterator

Vytvoří výchozí `checked_array_iterator` `checked_array _iterator` nebo ze základního iterátoru.

```cpp
checked_array_iterator();

checked_array_iterator(
    ITerator ptr,
    size_t size,
    size_t index = 0);
```

### <a name="parameters"></a>Parametry

*střed*\
Ukazatel na pole.

*hodnota*\
Velikost pole.

*indexovacím*\
Volitelné Prvek v poli pro inicializaci iterátoru.  Ve výchozím nastavení je iterátor inicializován na první prvek v poli.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [kontrolované iterátory](../standard-library/checked-iterators.md).

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

## <a name="difference_type"></a>checked_array_iterator::d ifference_type

Typ, který poskytuje rozdíl mezi dvěma `checked_array_iterator`s odkazujícími na prvky v rámci stejného kontejneru.

```cpp
typedef typename iterator_traits<_Iterator>::difference_type difference_type;
```

### <a name="remarks"></a>Poznámky

`checked_array_iterator` Rozdílový typ je stejný jako typ rozdílu iterátoru.

Ukázku kódu naleznete v tématu [checked_array_iterator:: operator []](#op_at) .

Další informace najdete v tématu [kontrolované iterátory](../standard-library/checked-iterators.md).

## <a name="op_eq_eq"></a>checked_array_iterator:: operator = = – operátor

Testuje dva `checked_array_iterator`s pro rovnost.

```cpp
bool operator==(const checked_array_iterator<_Iterator>& right) const;
```

### <a name="parameters"></a>Parametry

*Kliknutím*\
, `checked_array_iterator` U kterého se má kontrolovat rovnost.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [kontrolované iterátory](../standard-library/checked-iterators.md).

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

## <a name="op_neq"></a>checked_array_iterator:: operator! =

Testuje dva `checked_array_iterator`s pro nerovnost.

```cpp
bool operator!=(const checked_array_iterator<_Iterator>& right) const;
```

### <a name="parameters"></a>Parametry

*Kliknutím*\
, `checked_array_iterator` U kterého se má kontrolovat nerovnost.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [kontrolované iterátory](../standard-library/checked-iterators.md).

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

## <a name="op_lt"></a>checked_array_iterator:: operator&lt;

Testuje, `checked_array_iterator` zda je na levé straně operátoru menší `checked_array_iterator` než na pravé straně.

```cpp
bool operator<(const checked_array_iterator<_Iterator>& right) const;
```

### <a name="parameters"></a>Parametry

*Kliknutím*\
, `checked_array_iterator` U kterého se má kontrolovat nerovnost.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [kontrolované iterátory](../standard-library/checked-iterators.md).

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

## <a name="op_gt"></a>checked_array_iterator:: operator&gt;

Testuje, `checked_array_iterator` zda je na levé straně operátoru větší `checked_array_iterator` než na pravé straně.

```cpp
bool operator>(const checked_array_iterator<_Iterator>& right) const;
```

### <a name="parameters"></a>Parametry

*Kliknutím*\
`checked_array_iterator` Pro porovnání s.

### <a name="remarks"></a>Poznámky

Ukázku kódu naleznete v tématu [checked_array_iterator:: operator&lt; ](#op_lt) .

Další informace najdete v tématu [kontrolované iterátory](../standard-library/checked-iterators.md).

## <a name="op_lt_eq"></a>checked_array_iterator:: operator&lt;=

Testuje, `checked_array_iterator` zda je na levé straně operátoru menší než nebo rovno `checked_array_iterator` na pravé straně.

```cpp
bool operator<=(const checked_array_iterator<_Iterator>& right) const;
```

### <a name="parameters"></a>Parametry

*Kliknutím*\
`checked_array_iterator` Pro porovnání s.

### <a name="remarks"></a>Poznámky

Ukázku kódu naleznete v tématu [checked_array_iterator:: operator&gt; = ](#op_gt_eq) .

Další informace najdete v tématu [kontrolované iterátory](../standard-library/checked-iterators.md).

## <a name="op_gt_eq"></a>checked_array_iterator:: operator&gt;=

Testuje, `checked_array_iterator` zda je na levé straně operátoru větší než nebo rovno `checked_array_iterator` na pravé straně.

```cpp
bool operator>=(const checked_array_iterator<_Iterator>& right) const;
```

### <a name="parameters"></a>Parametry

*Kliknutím*\
`checked_array_iterator` Pro porovnání s.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [kontrolované iterátory](../standard-library/checked-iterators.md).

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

## <a name="op_star"></a>checked_array_iterator:: operator * – operátor

Vrátí prvek, který obsahuje `checked_array_iterator` adresy.

```cpp
reference operator*() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota prvku adresovaného `checked_array_iterator`.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [kontrolované iterátory](../standard-library/checked-iterators.md).

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

## <a name="op_arrow"></a>checked_array_iterator:: operator-&gt;

Vrátí ukazatel na prvek řešený `checked_array_iterator`.

```cpp
pointer operator->() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na element adresovaný `checked_array_iterator`.

### <a name="remarks"></a>Poznámky

Ukázku kódu naleznete v tématu [checked_array_iterator::p ointer](#pointer) .

Další informace najdete v tématu [kontrolované iterátory](../standard-library/checked-iterators.md).

## <a name="op_add_add"></a>checked_array_iterator:: operator + +

Přivýší `checked_array_iterator` k dalšímu prvku.

```cpp
checked_array_iterator& operator++();

checked_array_iterator<_Iterator> operator++(int);
```

### <a name="return-value"></a>Návratová hodnota

První operátor vrátí předem přírůstek `checked_array_iterator` a druhý, operátor postinkrement, vrátí kopii `checked_array_iterator`zvýšení.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [kontrolované iterátory](../standard-library/checked-iterators.md).

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

## <a name="operator--"></a>checked_array_iterator:: operator--

`checked_array_iterator` Sníží na předchozí prvek.

```cpp
checked_array_iterator<_Iterator>& operator--();

checked_array_iterator<_Iterator> operator--(int);
```

### <a name="return-value"></a>Návratová hodnota

První operátor vrátí hodnotu předsníženo `checked_array_iterator` a druhý, postdekrement operátor vrátí kopii `checked_array_iterator`snížené hodnoty.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [kontrolované iterátory](../standard-library/checked-iterators.md).

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

## <a name="op_add_eq"></a>checked_array_iterator:: operator + =

Přidá zadaný posun k `checked_array_iterator`.

```cpp
checked_array_iterator<_Iterator>& operator+=(difference_type _Off);
```

### <a name="parameters"></a>Parametry

*_Off*\
Posun, o který se má zvýšit iterátor

### <a name="return-value"></a>Návratová hodnota

Odkaz na element adresovaný `checked_array_iterator`.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [kontrolované iterátory](../standard-library/checked-iterators.md).

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

## <a name="op_add"></a>checked_array_iterator:: operator + – operátor

Přidá posun k iterátoru a vrátí nový `checked_array_iterator` adresující vložený prvek na nové pozici posunu.

```cpp
checked_array_iterator<_Iterator> operator+(difference_type _Off) const;
```

### <a name="parameters"></a>Parametry

*_Off*\
Posun, který má být přidán do `checked_array_iterator`.

### <a name="return-value"></a>Návratová hodnota

`checked_array_iterator` Adresování posunutí elementu.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [kontrolované iterátory](../standard-library/checked-iterators.md).

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

## <a name="operator-_eq"></a>checked_array_iterator:: operator-=

Sníží zadaný posun z `checked_array_iterator`.

```cpp
checked_array_iterator<_Iterator>& operator-=(difference_type _Off);
```

### <a name="parameters"></a>Parametry

*_Off*\
Posun, o který se má zvýšit iterátor

### <a name="return-value"></a>Návratová hodnota

Odkaz na element adresovaný `checked_array_iterator`.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [kontrolované iterátory](../standard-library/checked-iterators.md).

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

## <a name="operator-"></a>checked_array_iterator:: operator-

Sníží posun z iterátoru a vrátí nový `checked_array_iterator` adresující vložený prvek na nové pozici posunu.

```cpp
checked_array_iterator<_Iterator> operator-(difference_type _Off) const;

difference_type operator-(const checked_array_iterator& right) const;
```

### <a name="parameters"></a>Parametry

*_Off*\
Posun, který má být snížen z `checked_array_iterator`.

### <a name="return-value"></a>Návratová hodnota

`checked_array_iterator` Adresování posunutí elementu.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [kontrolované iterátory](../standard-library/checked-iterators.md).

## <a name="op_at"></a>checked_array_iterator:: operator [] – operátor

Vrátí odkaz na posun prvku z prvku, který adresuje `checked_array_iterator` podle zadaného počtu pozic.

```cpp
reference operator[](difference_type _Off) const;
```

### <a name="parameters"></a>Parametry

*_Off*\
Posun od `checked_array_iterator` adresy.

### <a name="return-value"></a>Návratová hodnota

Odkaz na posunutí elementu.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [kontrolované iterátory](../standard-library/checked-iterators.md).

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

## <a name="pointer"></a>checked_array_iterator::p ointer

Typ, který poskytuje ukazatel na prvek řešený `checked_array_iterator`.

```cpp
typedef typename iterator_traits<_Iterator>::pointer pointer;
```

### <a name="remarks"></a>Poznámky

Ukázku kódu naleznete v tématu [checked_array_iterator:: operator *](#op_star) .

Další informace najdete v tématu [kontrolované iterátory](../standard-library/checked-iterators.md).

## <a name="reference"></a>checked_array_iterator:: Reference

Typ, který poskytuje odkaz na prvek řešený `checked_array_iterator`.

```cpp
typedef typename iterator_traits<_Iterator>::reference reference;
```

### <a name="remarks"></a>Poznámky

Ukázku kódu naleznete v tématu [checked_array_iterator:: operator []](#op_at) .

Další informace najdete v tématu [kontrolované iterátory](../standard-library/checked-iterators.md).

## <a name="see-also"></a>Viz také:

[\<iterátor >](../standard-library/iterator.md)\
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)
