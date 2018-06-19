---
title: '&lt;zásobník&gt; operátory | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- stack/std::operator!=
- stack/std::operator&gt;
- stack/std::operator&gt;=
- stack/std::operator&lt;
- stack/std::operator&lt;=
- stack/std::operator==
dev_langs:
- C++
ms.assetid: 9c1fc282-2f61-4727-9e80-84ea5d4934a2
helpviewer_keywords:
- std::operator!= (stack)
- std::operator&gt; (stack)
- std::operator&gt;= (stack)
- std::operator&lt; (stack)
- std::operator&lt;= (stack)
- std::operator== (stack)
ms.openlocfilehash: 5d3bafd2d3112a2f4155f55a554b6c9c2e351b1f
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33861643"
---
# <a name="ltstackgt-operators"></a>&lt;zásobník&gt; operátory

||||
|-|-|-|
|[operator!=](#op_neq)|[Operátor&gt;](#op_gt)|[Operátor&gt;=](#op_gt_eq)|
|[Operátor&lt;](#op_lt)|[Operátor&lt;=](#op_lt_eq)|[operator==](#op_eq_eq)|

## <a name="op_neq"></a>  Operator! =

Testy, pokud zásobník objekt na levé straně operátor není rovno zásobníku objekt na pravé straně.

```cpp
bool operator!=(const stack <Type, Container>& left, const stack <Type, Container>& right,);
```

### <a name="parameters"></a>Parametry

`left` Objekt typu **zásobník**.

`right` Objekt typu **zásobník**.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE,** Pokud zásobníky nebo zásobníky nejsou stejné; **false** Pokud zásobníky nebo zásobníky jsou stejné.

### <a name="remarks"></a>Poznámky

Porovnání mezi objekty zásobníky je založena na pairwise porovnání jejich součástí. Dva zásobníky jsou stejné, pokud mají stejný počet elementů a jejich odpovídajících elementy mají stejné hodnoty. Jinak nerovné.

### <a name="example"></a>Příklad

```cpp
// stack_op_me.cpp
// compile with: /EHsc
#include <stack>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   // Declares stacks with vector base containers
   stack <int, vector<int> > s1, s2, s3;

   // The following would have cause an error because stacks with
   // different base containers are not equality comparable
   // stack <int, list<int> >  s3;

   s1.push( 1 );
   s2.push( 2 );
   s3.push( 1 );

   if ( s1 != s2 )
      cout << "The stacks s1 and s2 are not equal." << endl;
   else
      cout << "The stacks s1 and s2 are equal." << endl;

   if ( s1 != s3 )
      cout << "The stacks s1 and s3 are not equal." << endl;
   else
      cout << "The stacks s1 and s3 are equal." << endl;
}
```

```Output
The stacks s1 and s2 are not equal.
The stacks s1 and s3 are equal.
```

## <a name="op_lt"></a>  Operátor&lt;

Testy, pokud zásobník objekt na levé straně operátor je menší než zásobníku objekt na pravé straně.

```cpp
bool operator<(const stack <Type, Container>& left, const stack <Type, Container>& right);
```

### <a name="parameters"></a>Parametry

`left` Objekt typu **zásobník**.

`right` Objekt typu **zásobník**.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE,** Pokud zásobníku na levé straně operátoru je menší než a není rovno zásobníku na pravé straně operátoru; jinak hodnota **false**.

### <a name="remarks"></a>Poznámky

Porovnání mezi stack – objekty je založena na pairwise porovnání jejich součástí. Je menší – než vztah mezi dvěma objekty zásobníku je založen na porovnání první pár nerovné elementů.

### <a name="example"></a>Příklad

```cpp
// stack_op_lt.cpp
// compile with: /EHsc
#include <stack>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;

   // Declares stacks with list base container
   stack <int, list<int> > s1, s2, s3;

   s1.push( 2 );
   s1.push( 4 );
   s1.push( 6 );
   s1.push( 8 );
   s2.push( 5 );
   s2.push( 10 );
   s3.push( 2 );
   s3.push( 4 );
   s3.push( 6 );
   s3.push( 8 );

   if ( s1 >= s2 )
      cout << "The stack s1 is greater than or equal to "
           << "the stack s2." << endl;
   else
      cout << "The stack s1 is less than "
           << "the stack s2." << endl;

   if ( s1>= s3 )
      cout << "The stack s1 is greater than or equal to "
           << "the stack s3." << endl;
   else
      cout << "The stack s1 is less than "
           << "the stack s3." << endl;

   // to print out the stack s1 ( by unstacking the elements):
   stack <int>::size_type i_size_s1 = s1.size( );
   cout << "The stack s1 from the top down is: ( ";
   unsigned int i;
   for ( i = 1 ; i <= i_size_s1 ; i++ )
   {
      cout << s1.top( ) << " ";
      s1.pop( );
   }
   cout << ")." << endl;
}
```

```Output
The stack s1 is less than the stack s2.
The stack s1 is greater than or equal to the stack s3.
The stack s1 from the top down is: ( 8 6 4 2 ).
```

## <a name="op_lt_eq"></a>  Operátor&lt;=

Pokud zásobníku objekt na levé straně operátoru testů je menší než nebo rovno zásobníku objekt na pravé straně.

```cpp
bool operator<=(const stack <Type, Container>& left, const stack <Type, Container>& right);
```

### <a name="parameters"></a>Parametry

`left` Objekt typu **zásobník**.

`right` Objekt typu **zásobník**.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE,** Pokud zásobníku na levé straně operátoru je menší než nebo rovná zásobníku na pravé straně operátoru; jinak hodnota **false**.

### <a name="remarks"></a>Poznámky

Porovnání mezi stack – objekty je založena na pairwise porovnání jejich součástí. Je menší než nebo rovno vztah mezi dvěma objekty zásobníku je založena na porovnání první pár nerovné elementů.

### <a name="example"></a>Příklad

```cpp
// stack_op_le.cpp
// compile with: /EHsc
#include <stack>
#include <iostream>

int main( )
{
   using namespace std;

   // Declares stacks with default deque base container
   stack <int> s1, s2, s3;

   s1.push( 5 );
   s1.push( 10 );
   s2.push( 1 );
   s2.push( 2 );
   s3.push( 5 );
   s3.push( 10 );

   if ( s1 <= s2 )
      cout << "The stack s1 is less than or equal to "
           << "the stack s2." << endl;
   else
      cout << "The stack s1 is greater than "
           << "the stack s2." << endl;

   if ( s1 <= s3 )
      cout << "The stack s1 is less than or equal to "
           << "the stack s3." << endl;
   else
      cout << "The stack s1 is greater than "
           << "the stack s3." << endl;
}
```

```Output
The stack s1 is greater than the stack s2.
The stack s1 is less than or equal to the stack s3.
```

## <a name="op_eq_eq"></a>  Operator ==

Testy, pokud zásobník objekt na levé straně operátoru rovná zásobníku objekt na pravé straně.

```cpp
bool operator==(const stack <Type, Container>& left, const stack <Type, Container>& right);
```

### <a name="parameters"></a>Parametry

`left` Objekt typu **zásobník**.

`right` Objekt typu **zásobník**.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE,** Pokud zásobníky nebo zásobníky jsou si rovny; **false** Pokud zásobníky nebo zásobníky nejsou stejné.

### <a name="remarks"></a>Poznámky

Porovnání mezi stack – objekty je založena na pairwise porovnání jejich součástí. Dva zásobníky jsou stejné, pokud mají stejný počet elementů a jejich odpovídajících elementy mají stejné hodnoty. Jinak nerovné.

### <a name="example"></a>Příklad

```cpp
// stack_op_eq.cpp
// compile with: /EHsc
#include <stack>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   // Declares stacks with vector base containers
   stack <int, vector<int> > s1, s2, s3;

   // The following would have cause an error because stacks with
   // different base containers are not equality comparable
   // stack <int, list<int> > s3;

   s1.push( 1 );
   s2.push( 2 );
   s3.push( 1 );

   if ( s1 == s2 )
      cout << "The stacks s1 and s2 are equal." << endl;
   else
      cout << "The stacks s1 and s2 are not equal." << endl;

   if ( s1 == s3 )
      cout << "The stacks s1 and s3 are equal." << endl;
   else
      cout << "The stacks s1 and s3 are not equal." << endl;
}
```

```Output
The stacks s1 and s2 are not equal.
The stacks s1 and s3 are equal.
```

## <a name="op_gt"></a>  Operátor&gt;

Testy, pokud zásobník objekt na levé straně operátoru je větší než zásobníku objekt na pravé straně.

```cpp
bool operator>(const stack <Type, Container>& left, const stack <Type, Container>& right);
```

### <a name="parameters"></a>Parametry

`left` Objekt typu **zásobník**.

`right` Objekt typu **zásobník**.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE,** pokud zásobník na levé straně operátoru je větší než a není rovná zásobníku na pravé straně operátoru; jinak hodnota **false**.

### <a name="remarks"></a>Poznámky

Porovnání mezi stack – objekty je založena na pairwise porovnání jejich součástí. Delší – než vztah mezi dvěma objekty zásobníku je založen na porovnání první pár nerovné elementů.

### <a name="example"></a>Příklad

```cpp
// stack_op_gt.cpp
// compile with: /EHsc
#include <stack>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;

   // Declares stacks with list base container
   stack <int, list<int> > s1, s2, s3;

   s1.push( 1 );
   s1.push( 2 );
   s1.push( 3 );
   s2.push( 5 );
   s2.push( 10 );
   s3.push( 1 );
   s3.push( 2 );

   if ( s1 > s2 )
      cout << "The stack s1 is greater than "
           << "the stack s2." << endl;
   else
      cout << "The stack s1 is not greater than "
           << "the stack s2." << endl;

   if ( s1> s3 )
      cout << "The stack s1 is greater than "
           << "the stack s3." << endl;
   else
      cout << "The stack s1 is not greater than "
           << "the stack s3." << endl;
}
```

```Output
The stack s1 is not greater than the stack s2.
The stack s1 is greater than the stack s3.
```

## <a name="op_gt_eq"></a>  Operátor&gt;=

Testy, pokud je zásobník objekt na levé straně operátoru větší než nebo rovna hodnotě zásobníku objekt na pravé straně.

```cpp
bool operator>=(const stack <Type, Container>& left, const stack <Type, Container>& right);
```

### <a name="parameters"></a>Parametry

`left` Objekt typu **zásobník**.

`right` Objekt typu **zásobník**.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE,** pokud zásobník na levé straně operátoru je striktně menší než zásobníku na pravé straně operátoru; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Porovnání mezi stack – objekty je založena na pairwise porovnání jejich součástí. Větší než nebo rovna hodnotě vztah mezi dvěma stack – objekty podle porovnání první pár nerovné elementů.

### <a name="example"></a>Příklad

```cpp
// stack_op_ge.cpp
// compile with: /EHsc
#include <stack>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;

   // Declares stacks with list base container
   stack <int, list<int> > s1, s2, s3;

   s1.push( 1 );
   s1.push( 2 );
   s2.push( 5 );
   s2.push( 10 );
   s3.push( 1 );
   s3.push( 2 );

   if ( s1 >= s2 )
      cout << "The stack s1 is greater than or equal to "
           << "the stack s2." << endl;
   else
      cout << "The stack s1 is less than "
           << "the stack s2." << endl;

   if ( s1>= s3 )
      cout << "The stack s1 is greater than or equal to "
           << "the stack s3." << endl;
   else
      cout << "The stack s1 is less than "
           << "the stack s3." << endl;
}
```

```Output
The stack s1 is less than the stack s2.
The stack s1 is greater than or equal to the stack s3.
```

## <a name="see-also"></a>Viz také

[\<stack>](../standard-library/stack.md)<br/>
