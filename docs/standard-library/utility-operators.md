---
title: '&gt; operátory &lt;Utility'
ms.date: 11/04/2016
f1_keywords:
- utility/std::operator!=
- utility/std::operator&gt;
- utility/std::operator&gt;=
- utility/std::operator&lt;
- utility/std::operator&lt;=
- utility/std::operator==
ms.assetid: a6617109-2cec-4a69-948f-6c87116eda5f
helpviewer_keywords:
- std::operator!= (utility)
- std::operator&gt; (utility)
- std::operator&gt;= (utility)
- std::operator&lt; (utility)
- std::operator&lt;= (utility)
- std::operator== (utility)
ms.openlocfilehash: ec6c996487dc2e6c5ce628fe5e080b4f601479d9
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78854857"
---
# <a name="ltutilitygt-operators"></a>&gt; operátory &lt;Utility

> [!NOTE]
> Operátory používající `Type&` jsou součástí `namespace rel_ops`.

## <a name="op_neq"></a>! = – operátor

Testuje, zda dvojice objektu na levé straně operátoru není rovna objektu páru na pravé straně.

```cpp
template <class Type>
    constexpr bool operator!=(const Type& left, const Type& right);

template <class T, class U>
    constexpr bool operator!=(const pair<T, U>& left, const pair<T, U>& right);
```

### <a name="parameters"></a>Parametry

*levý*\
Objekt typu `pair`.

*pravé*\
Objekt typu `pair`.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud nejsou páry stejné; **false** , pokud jsou páry stejné.

### <a name="remarks"></a>Poznámky

Jedna dvojice je rovna jiné dvojici, pokud je každý z jejich odpovídajících prvků stejný. Dva páry jsou nerovné, pokud buď první nebo druhý prvek jednoho není roven odpovídajícímu elementu druhé dvojice.

### <a name="example"></a>Příklad

```cpp
// utility_op_ne.cpp
// compile with: /EHsc
#include <utility>
#include <iomanip>
#include <iostream>

int main( )
{
   using namespace std;
   pair <int, double> p1, p2, p3;

   p1 = make_pair ( 10, 1.11e-1 );
   p2 = make_pair ( 1000, 1.11e-3 );
   p3 = make_pair ( 10, 1.11e-1 );

   cout.precision ( 3 );
   cout << "The pair p1 is: ( " << p1.first << ", "
        << p1.second << " )." << endl;
   cout << "The pair p2 is: ( " << p2.first << ", "
        << p2.second << " )." << endl;
   cout << "The pair p3 is: ( " << p3.first << ", "
        << p3.second << " )." << endl << endl;

   if ( p1 != p2 )
      cout << "The pairs p1 and p2 are not equal." << endl;
   else
      cout << "The pairs p1 and p2 are equal." << endl;

   if ( p1 != p3 )
      cout << "The pairs p1 and p3 are not equal." << endl;
   else
      cout << "The pairs p1 and p3 are equal." << endl;
}
```

```Output
The pair p1 is: ( 10, 0.111 ).
The pair p2 is: ( 1000, 0.00111 ).
The pair p3 is: ( 10, 0.111 ).

The pairs p1 and p2 are not equal.
The pairs p1 and p3 are equal.
```

## <a name="op_eq_eq"></a>operator = = – operátor

Testuje, zda je objekt dvojice na levé straně operátoru roven objektu páru na pravé straně.

```cpp
template <class T, class U>
constexpr bool operator==(const pair<T, U>& left, const pair<T, U>& right);
```

### <a name="parameters"></a>Parametry

*levý*\
Objekt typu `pair`.

*pravé*\
Objekt typu `pair`.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud jsou páry stejné; **false** , pokud `pair`s nejsou stejné.

### <a name="remarks"></a>Poznámky

Jedna dvojice je rovna jiné dvojici, pokud je každý z jejich odpovídajících prvků stejný. Funkce vrátí `left`. **první** == `right`. **první** && `left`. **druhý** == `right`. **sekunda**. Dva páry jsou nerovné, pokud buď první nebo druhý prvek jednoho není roven odpovídajícímu elementu druhé dvojice.

### <a name="example"></a>Příklad

```cpp
// utility_op_eq.cpp
// compile with: /EHsc
#include <utility>
#include <iomanip>
#include <iostream>

int main( )
{
   using namespace std;
   pair <int, double> p1, p2, p3;

   p1 = make_pair ( 10, 1.11e-1 );
   p2 = make_pair ( 1000, 1.11e-3 );
   p3 = make_pair ( 10, 1.11e-1 );

   cout.precision ( 3 );
   cout << "The pair p1 is: ( " << p1.first << ", "
        << p1.second << " )." << endl;
   cout << "The pair p2 is: ( " << p2.first << ", "
        << p2.second << " )." << endl;
   cout << "The pair p3 is: ( " << p3.first << ", "
        << p3.second << " )." << endl << endl;

   if ( p1 == p2 )
      cout << "The pairs p1 and p2 are equal." << endl;
   else
      cout << "The pairs p1 and p2 are not equal." << endl;

   if ( p1 == p3 )
      cout << "The pairs p1 and p3 are equal." << endl;
   else
      cout << "The pairs p1 and p3 are not equal." << endl;
}
```

## <a name="op_lt"></a>operátor&lt;

Testuje, zda je objekt dvojice na levé straně operátoru menší než objekt dvojice na pravé straně.

```cpp
template <class T, class U>
constexpr bool operator<(const pair<T, U>& left, const pair<T, U>& right);
```

### <a name="parameters"></a>Parametry

*levý*\
Objekt typu `pair` na levé straně operátoru.

*pravé*\
Objekt typu `pair` na pravé straně operátoru.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud `pair` na levé straně operátoru je výhradně menší než `pair` na pravé straně operátoru; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Objekt `left` `pair` je označován jako striktně menší než objekt `right` `pair`, pokud *Left* je menší než a není rovno *pravému*.

V porovnání párů mají hodnoty první prvky dvou párů nejvyšší prioritu. Pokud se liší, pak výsledek jejich porovnání je výsledkem porovnání páru. Pokud se hodnoty prvních prvků neliší, pak jsou porovnány hodnoty druhých prvků a výsledek jejich porovnání se považuje za výsledek porovnání páru.

### <a name="example"></a>Příklad

```cpp
// utility_op_lt.cpp
// compile with: /EHsc
#include <utility>
#include <iomanip>
#include <iostream>

int main( )
{
   using namespace std;
   pair <int, double> p1, p2, p3;

   p1 = make_pair ( 10, 2.22e-1 );
   p2 = make_pair ( 100, 1.11e-1 );
   p3 = make_pair ( 10, 1.11e-1 );

   cout.precision ( 3 );
   cout << "The pair p1 is: ( " << p1.first << ", "
        << p1.second << " )." << endl;
   cout << "The pair p2 is: ( " << p2.first << ", "
        << p2.second << " )." << endl;
   cout << "The pair p3 is: ( " << p3.first << ", "
        << p3.second << " )." << endl << endl;

   if ( p1 < p2 )
      cout << "The pair p1 is less than the pair p2." << endl;
   else
      cout << "The pair p1 is not less than the pair p2." << endl;

   if ( p1 < p3 )
      cout << "The pair p1 is less than the pair p3." << endl;
   else
      cout << "The pair p1 is not less than the pair p3." << endl;
}
```

```Output
The pair p1 is: ( 10, 0.222 ).
The pair p2 is: ( 100, 0.111 ).
The pair p3 is: ( 10, 0.111 ).

The pair p1 is less than the pair p2.
The pair p1 is not less than the pair p3.
```

## <a name="op_lt_eq"></a>operátor&lt;=

Testuje, zda je objekt dvojice na levé straně operátoru menší než nebo roven objektu páru na pravé straně.

```cpp
template <class Type>
constexpr bool operator<=(const Type& left, const Type& right);

template <class T, class U>
constexpr bool operator<=(const pair<T, U>& left, const pair<T, U>& right);
```

### <a name="parameters"></a>Parametry

*levý*\
Objekt typu `pair` na levé straně operátoru.

*pravé*\
Objekt typu `pair` na pravé straně operátoru.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud je `pair` na levé straně operátoru menší než nebo rovno `pair` na pravé straně operátoru; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

V porovnání párů mají hodnoty první prvky dvou párů nejvyšší prioritu. Pokud se liší, pak výsledek jejich porovnání je výsledkem porovnání páru. Pokud se hodnoty prvních prvků neliší, pak jsou porovnány hodnoty druhých prvků a výsledek jejich porovnání se považuje za výsledek porovnání páru.

### <a name="example"></a>Příklad

```cpp
// utility_op_le.cpp
// compile with: /EHsc
#include <utility>
#include <iomanip>
#include <iostream>

int main( )
{
   using namespace std;
   pair <int, double> p1, p2, p3, p4;

   p1 = make_pair ( 10, 2.22e-1 );
   p2 = make_pair ( 100, 1.11e-1 );
   p3 = make_pair ( 10, 1.11e-1 );
   p4 = make_pair ( 10, 2.22e-1 );

   cout.precision ( 3 );
   cout << "The pair p1 is: ( " << p1.first << ", "
        << p1.second << " )." << endl;
   cout << "The pair p2 is: ( " << p2.first << ", "
        << p2.second << " )." << endl;
   cout << "The pair p3 is: ( " << p3.first << ", "
        << p3.second << " )." << endl;
   cout << "The pair p4 is: ( " << p4.first << ", "
        << p4.second << " )." << endl << endl;

   if ( p1 <= p2 )
      cout << "The pair p1 is less than or equal to the pair p2." << endl;
   else
      cout << "The pair p1 is greater than the pair p2." << endl;

   if ( p1 <= p3 )
      cout << "The pair p1 is less than or equal to the pair p3." << endl;
   else
      cout << "The pair p1 is greater than the pair p3." << endl;

   if ( p1 <= p4 )
      cout << "The pair p1 is less than or equal to the pair p4." << endl;
   else
      cout << "The pair p1 is greater than the pair p4." << endl;
}
```

```Output
The pair p1 is: ( 10, 0.222 ).
The pair p2 is: ( 100, 0.111 ).
The pair p3 is: ( 10, 0.111 ).
The pair p4 is: ( 10, 0.222 ).

The pair p1 is less than or equal to the pair p2.
The pair p1 is greater than the pair p3.
The pair p1 is less than or equal to the pair p4.
```

## <a name="op_gt"></a>operátor&gt;

Testuje, zda je objekt dvojice na levé straně operátoru větší než dvojice objektu na pravé straně.

```cpp
template <class Type>
constexpr bool operator>(const Type& left, const Type& right);

template <class T, class U>
constexpr bool operator>(const pair<T, U>& left, const pair<T, U>& right);
```

### <a name="parameters"></a>Parametry

*levý*\
Objekt typu `pair` na levé straně operátoru.

*pravé*\
Objekt typu `pair` na pravé straně operátoru.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud je `pair` na levé straně operátoru striktně větší než `pair` na pravé straně operátoru; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Objekt `left` `pair` je označován jako striktně větší než objekt `right` `pair`, pokud je *Left* větší než a není rovno *pravému*.

V porovnání párů mají hodnoty první prvky dvou párů nejvyšší prioritu. Pokud se liší, pak výsledek jejich porovnání je výsledkem porovnání páru. Pokud se hodnoty prvních prvků neliší, pak jsou porovnány hodnoty druhých prvků a výsledek jejich porovnání se považuje za výsledek porovnání páru.

### <a name="example"></a>Příklad

```cpp
// utility_op_gt.cpp
// compile with: /EHsc
#include <utility>
#include <iomanip>
#include <iostream>

int main( )
{
   using namespace std;
   pair <int, double> p1, p2, p3, p4;

   p1 = make_pair ( 10, 2.22e-1 );
   p2 = make_pair ( 100, 1.11e-1 );
   p3 = make_pair ( 10, 1.11e-1 );
   p4 = make_pair ( 10, 2.22e-1 );

   cout.precision ( 3 );
   cout << "The pair p1 is: ( " << p1.first << ", "
        << p1.second << " )." << endl;
   cout << "The pair p2 is: ( " << p2.first << ", "
        << p2.second << " )." << endl;
   cout << "The pair p3 is: ( " << p3.first << ", "
        << p3.second << " )." << endl;
   cout << "The pair p4 is: ( " << p4.first << ", "
        << p4.second << " )." << endl << endl;

   if ( p1 > p2 )
      cout << "The pair p1 is greater than the pair p2." << endl;
   else
      cout << "The pair p1 is not greater than the pair p2." << endl;

   if ( p1 > p3 )
      cout << "The pair p1 is greater than the pair p3." << endl;
   else
      cout << "The pair p1 is not greater than the pair p3." << endl;

   if ( p1 > p4 )
      cout << "The pair p1 is greater than the pair p4." << endl;
   else
      cout << "The pair p1 is not greater than the pair p4." << endl;
}
```

```Output
The pair p1 is: ( 10, 0.222 ).
The pair p2 is: ( 100, 0.111 ).
The pair p3 is: ( 10, 0.111 ).
The pair p4 is: ( 10, 0.222 ).

The pair p1 is not greater than the pair p2.
The pair p1 is greater than the pair p3.
The pair p1 is not greater than the pair p4.
```

## <a name="op_gt_eq"></a>operátor&gt;=

Testuje, zda je objekt dvojice na levé straně operátoru větší než nebo roven objektu páru na pravé straně.

```cpp
template <class Type>
    constexpr bool operator>=(const Type& left, const Type& right);

template <class T, class U>
    constexpr bool operator>=(const pair<T, U>& left, const pair<T, U>& right);
```

### <a name="parameters"></a>Parametry

*levý*\
Objekt typu `pair` na levé straně operátoru.

*pravé*\
Objekt typu `pair` na pravé straně operátoru.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud je `pair` na levé straně operátoru větší než nebo rovno `pair` na pravé straně operátoru; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

V porovnání párů mají hodnoty první prvky dvou párů nejvyšší prioritu. Pokud se liší, pak výsledek jejich porovnání je výsledkem porovnání páru. Pokud se hodnoty prvních prvků neliší, pak jsou porovnány hodnoty druhých prvků a výsledek jejich porovnání se považuje za výsledek porovnání páru.

### <a name="example"></a>Příklad

```cpp
// utility_op_ge.cpp
// compile with: /EHsc
#include <utility>
#include <iomanip>
#include <iostream>

int main( )
{
   using namespace std;
   pair <int, double> p1, p2, p3, p4;

   p1 = make_pair ( 10, 2.22e-1 );
   p2 = make_pair ( 100, 1.11e-1 );
   p3 = make_pair ( 10, 1.11e-1 );
   p4 = make_pair ( 10, 2.22e-1 );

   cout.precision ( 3 );
   cout << "The pair p1 is: ( " << p1.first << ", "
        << p1.second << " )." << endl;
   cout << "The pair p2 is: ( " << p2.first << ", "
        << p2.second << " )." << endl;
   cout << "The pair p3 is: ( " << p3.first << ", "
        << p3.second << " )." << endl;
   cout << "The pair p4 is: ( " << p4.first << ", "
        << p4.second << " )." << endl << endl;

   if ( p1 >= p2 )
      cout << "Pair p1 is greater than or equal to pair p2." << endl;
   else
      cout << "The pair p1 is less than the pair p2." << endl;

   if ( p1 >= p3 )
      cout << "Pair p1 is greater than or equal to pair p3." << endl;
   else
      cout << "The pair p1 is less than the pair p3." << endl;

   if ( p1 >= p4 )
      cout << "Pair p1 is greater than or equal to pair p4." << endl;
   else
      cout << "The pair p1 is less than the pair p4." << endl;
}
```

```Output
The pair p1 is: ( 10, 0.222 ).
The pair p2 is: ( 100, 0.111 ).
The pair p3 is: ( 10, 0.111 ).
The pair p4 is: ( 10, 0.222 ).

The pair p1 is less than the pair p2.
Pair p1 is greater than or equal to pair p3.
Pair p1 is greater than or equal to pair p4.
```
