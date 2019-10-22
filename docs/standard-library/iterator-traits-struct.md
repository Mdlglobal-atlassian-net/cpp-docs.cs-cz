---
title: iterator_traits – struktura
ms.date: 11/04/2016
f1_keywords:
- xutility/std::iterator_traits
helpviewer_keywords:
- iterator_traits struct
- iterator_traits class
ms.assetid: 8b92c2c5-f658-402f-8ca1-e7ae301b8514
ms.openlocfilehash: 924ca5ae1d32753bbe315252d942425712962639
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689454"
---
# <a name="iterator_traits-struct"></a>iterator_traits – struktura

Struktura pomocné šablony sloužící k určení všech definic typu kritického typu, které by měl mít iterátor.

## <a name="syntax"></a>Syntaxe

```cpp
struct iterator_traits {
   typedef typename Iterator::iterator_category iterator_category;
   typedef typename Iterator::value_type value_type;
   typedef typename Iterator::difference_type difference_type;
   typedef difference_type distance_type;
   typedef typename Iterator::pointer pointer;
   typedef typename Iterator::reference reference;
   };
```

## <a name="remarks"></a>Poznámky

Struktura šablony definuje typy členů.

- `iterator_category`: synonymum pro `Iterator::iterator_category`.

- `value_type`: synonymum pro `Iterator::value_type`.

- `difference_type`: synonymum pro `Iterator::difference_type`.

- `distance_type`: synonymum pro `Iterator::difference_type.`

- `pointer`: synonymum pro `Iterator::pointer`.

- `reference`: synonymum pro `Iterator::reference`.

Částečné specializace určují kritické typy přidružené k ukazateli **objektu typu typ** <strong>\*</strong> nebo **typ const** <strong>\*</strong>.

V této implementaci můžete také použít několik funkcí šablon, které nevyužívají částečnou specializaci:

```cpp
template <class Category, class Type, class Diff>
C _Iter_cat(const iterator<Category, Ty, Diff>&);

template <class Ty>
random_access_iterator_tag _Iter_cat(const Ty *);

template <class Category, class Ty, class Diff>
Ty *val_type(const iterator<Category, Ty, Diff>&);

template <class Ty>
Ty *val_type(const Ty *);

template <class Category, class Ty, class Diff>
Diff *_Dist_type(const iterator<Category, Ty, Diff>&);

template <class Ty>
ptrdiff_t *_Dist_type(const Ty *);
```

což určuje, že některé typy jsou mnohem nepřímo. Tyto funkce použijete jako argumenty volání funkce. Jejich jediným účelem je dodat do volané funkce užitečný parametr šablony třídy.

## <a name="example"></a>Příklad

```cpp
// iterator_traits.cpp
// compile with: /EHsc
#include <iostream>
#include <iterator>
#include <vector>
#include <list>

using namespace std;

template< class it >
void
function( it i1, it i2 )
{
   iterator_traits<it>::iterator_category cat;
   cout << typeid( cat ).name( ) << endl;
   while ( i1 != i2 )
   {
      iterator_traits<it>::value_type x;
      x = *i1;
      cout << x << " ";
      i1++;
   };
   cout << endl;
};

int main( )
{
   vector<char> vc( 10,'a' );
   list<int> li( 10 );
   function( vc.begin( ), vc.end( ) );
   function( li.begin( ), li.end( ) );
}
/* Output:
struct std::random_access_iterator_tag
a a a a a a a a a a
struct std::bidirectional_iterator_tag
0 0 0 0 0 0 0 0 0 0
*/
```

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<iterator >

**Obor názvů:** std

## <a name="see-also"></a>Viz také:

[\<iterator >](../standard-library/iterator.md) \
[Bezpečnost vlákna ve C++ standardní knihovně](../standard-library/thread-safety-in-the-cpp-standard-library.md) \
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)
