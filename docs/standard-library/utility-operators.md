---
title: '&lt;Nástroj&gt; operátory | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- utility/std::operator!=
- utility/std::operator&gt;
- utility/std::operator&gt;=
- utility/std::operator&lt;
- utility/std::operator&lt;=
- utility/std::operator==
dev_langs:
- C++
ms.assetid: a6617109-2cec-4a69-948f-6c87116eda5f
helpviewer_keywords:
- std::operator!= (utility)
- std::operator&gt; (utility)
- std::operator&gt;= (utility)
- std::operator&lt; (utility)
- std::operator&lt;= (utility)
- std::operator== (utility)
ms.openlocfilehash: 6c97e44e5110108351ac9c47f47434b828193fc7
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44099626"
---
# <a name="ltutilitygt-operators"></a>&lt;Nástroj&gt; operátory

||||
|-|-|-|
|[operator!=](#op_neq)|[– Operátor&gt;](#op_gt)|[– Operátor&gt;=](#op_gt_eq)|
|[– Operátor&lt;](#op_lt)|[– Operátor&lt;=](#op_lt_eq)|[operator==](#op_eq_eq)|

## <a name="op_neq"></a>  Operator! =

Testuje, zda je objekt dvojice na levé straně operátoru není roven párový objekt na pravé straně.

```cpp
template <class Type>
constexpr bool operator!=(const Type& left, const Type& right);

template <class T, class U>
constexpr bool operator!=(const pair<T, U>& left, const pair<T, U>& right);
```

### <a name="parameters"></a>Parametry

*doleva*  
Objekt typu `pair`.

*doprava*  
Objekt typu `pair`.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud dvojice nejsou stejné; **false** Pokud dvojice jsou si rovny.

### <a name="remarks"></a>Poznámky

Jednu dvojici je rovna jinou dvojici, pokud každý z jejich odpovídajících prvků rovná. Dvě dvojice rovny, pokud první nebo druhý prvek jednoho není shodný s odpovídající element páru.

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

## <a name="op_eq_eq"></a>  Operator ==

Testuje, zda objekt dvojice na levé straně operátoru roven objektu pair na pravé straně.

```cpp
template <class T, class U>
constexpr bool operator==(const pair<T, U>& left, const pair<T, U>& right);
```

### <a name="parameters"></a>Parametry

*doleva*<br/>
Objekt typu `pair`.

*doprava*<br/>
Objekt typu `pair`.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud dvojice rovnají. **false** Pokud `pair`s nejsou stejné.

### <a name="remarks"></a>Poznámky

Jednu dvojici je rovna jinou dvojici, pokud každý z jejich odpovídajících prvků rovná. Funkce vrátí `left`. **první** == `right`. **první** && `left`. **druhý** == `right`. **druhý**. Dvě dvojice rovny, pokud první nebo druhý prvek jednoho není shodný s odpovídající element páru.

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

## <a name="op_lt"></a>  – Operátor&lt;

Testuje, zda je pár objekt na levé straně operátoru je menší než objekt dvojice na pravé straně.

```cpp
template <class T, class U>
constexpr bool operator<(const pair<T, U>& left, const pair<T, U>& right);
```

### <a name="parameters"></a>Parametry

*doleva*  
Objekt typu `pair` na levé straně operátoru.

*doprava*  
Objekt typu `pair` na pravé straně operátoru.

### <a name="return-value"></a>Návratová hodnota

**true** Pokud `pair` na levé straně operátoru je striktně menší než `pair` na pravé straně operátoru; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

`left` `pair` Objektu se říká, že se striktně menší než `right` `pair` objekt by *levé* je menší a není rovno *správné*.

Porovnání dvojice první prvky dvě dvojice hodnot mají nejvyšší prioritu. Pokud se liší, je výsledek jejich porovnání považován za výsledek porovnání, které odpovídá páru licencí. Pokud nejsou hodnoty první prvků jiný, hodnoty druhý prvky jsou porovnány a výsledek jejich porovnání se bere jako výsledek porovnání, které odpovídá páru licencí.

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

## <a name="op_lt_eq"></a>  – Operátor&lt;=

Testuje, zda je pár objekt na levé straně operátoru je menší než nebo rovna hodnotě párový objekt na pravé straně.

```cpp
template <class Type>
constexpr bool operator<=(const Type& left, const Type& right);

template <class T, class U>
constexpr bool operator<=(const pair<T, U>& left, const pair<T, U>& right);
```

### <a name="parameters"></a>Parametry

*doleva*  
Objekt typu `pair` na levé straně operátoru.

*doprava*  
Objekt typu `pair` na pravé straně operátoru.

### <a name="return-value"></a>Návratová hodnota

**true** Pokud `pair` na levé straně operátoru je menší než nebo rovna hodnotě `pair` na pravé straně operátoru; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Porovnání dvojice první prvky dvě dvojice hodnot mají nejvyšší prioritu. Pokud se liší, je výsledek jejich porovnání považován za výsledek porovnání, které odpovídá páru licencí. Pokud nejsou hodnoty první prvků jiný, hodnoty druhý prvky jsou porovnány a výsledek jejich porovnání se bere jako výsledek porovnání, které odpovídá páru licencí.

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

## <a name="op_gt"></a>  – Operátor&gt;

Testuje, zda je objekt dvojice na levé straně operátoru větší než párový objekt na pravé straně.

```cpp
template <class Type>
constexpr bool operator>(const Type& left, const Type& right);

template <class T, class U>
constexpr bool operator>(const pair<T, U>& left, const pair<T, U>& right);
```

### <a name="parameters"></a>Parametry

*doleva*  
Objekt typu `pair` na levé straně operátoru.

*doprava*  
Objekt typu `pair` na pravé straně operátoru.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud `pair` na levé straně operátoru je výhradně větší než `pair` na pravé straně operátoru; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

`left` `pair` Objektu se říká, že být striktně větší než `right` `pair` objekt by *levé* je větší než a není rovno *správné*.

Porovnání dvojice první prvky dvě dvojice hodnot mají nejvyšší prioritu. Pokud se liší, je výsledek jejich porovnání považován za výsledek porovnání, které odpovídá páru licencí. Pokud nejsou hodnoty první prvků jiný, hodnoty druhý prvky jsou porovnány a výsledek jejich porovnání se bere jako výsledek porovnání, které odpovídá páru licencí.

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

## <a name="op_gt_eq"></a>  – Operátor&gt;=

Testuje, zda je objekt dvojice na levé straně operátoru větší než nebo rovna hodnotě párový objekt na pravé straně.

```cpp
template <class Type>
constexpr bool operator>=(const Type& left, const Type& right);

template <class T, class U>
constexpr bool operator>=(const pair<T, U>& left, const pair<T, U>& right);
```

### <a name="parameters"></a>Parametry

*doleva*  
Objekt typu `pair` na levé straně operátoru.

*doprava*  
Objekt typu `pair` na pravé straně operátoru.

### <a name="return-value"></a>Návratová hodnota

**true** Pokud `pair` na levé straně operátoru je větší než nebo rovna hodnotě `pair` na pravé straně operátoru; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Porovnání dvojice první prvky dvě dvojice hodnot mají nejvyšší prioritu. Pokud se liší, je výsledek jejich porovnání považován za výsledek porovnání, které odpovídá páru licencí. Pokud nejsou hodnoty první prvků jiný, hodnoty druhý prvky jsou porovnány a výsledek jejich porovnání se bere jako výsledek porovnání, které odpovídá páru licencí.

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

## <a name="see-also"></a>Viz také:

[\<Nástroje >](../standard-library/utility.md)<br/>
