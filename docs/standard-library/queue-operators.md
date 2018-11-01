---
title: '&lt;fronty&gt; operátory'
ms.date: 11/04/2016
f1_keywords:
- queue/std::operator!=
- queue/std::operator&gt;
- queue/std::operator&gt;=
- queue/std::operator&lt;
- queue/std::operator&lt;=
- queue/std::operator==
ms.assetid: 7c435b48-175c-45b0-88eb-24561044019c
helpviewer_keywords:
- std::operator!= (queue)
- std::operator&gt; (queue)
- std::operator&gt;= (queue)
- std::operator&lt; (queue)
- std::operator&lt;= (queue)
- std::operator== (queue)
ms.openlocfilehash: 496b728b67c4539a63d5bf3c783f8c9145c1de42
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50537485"
---
# <a name="ltqueuegt-operators"></a>&lt;fronty&gt; operátory

||||
|-|-|-|
|[operator!=](#op_neq)|[– Operátor&gt;](#op_gt)|[– Operátor&gt;=](#op_gt_eq)|
|[– Operátor&lt;](#op_lt)|[– Operátor&lt;=](#op_lt_eq)|[operator==](#op_eq_eq)|

## <a name="op_neq"></a>  Operator! =

Testuje, zda je objekt fronty na levé straně operátoru není roven objektu fronty na pravé straně.

```cpp
bool operator!=(const queue <Type, Container>& left, const queue <Type, Container>& right,);
```

### <a name="parameters"></a>Parametry

*doleva*<br/>
Objekt typu `queue`.

*doprava*<br/>
Objekt typu `queue`.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud fronty nejsou stejné; **false** Pokud fronty jsou si rovny.

### <a name="remarks"></a>Poznámky

Porovnání mezi objekty fronty je založen na pairwise porovnání jejich prvky. Pokud mají stejný počet prvků a jejich odpovídající elementy mají stejné hodnoty dvě fronty jsou si rovny. V opačném případě nerovnost.

### <a name="example"></a>Příklad

```cpp
// queue_op_ne.cpp
// compile with: /EHsc
#include <queue>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;

   // Declares queues with list base containers
   queue <int, list<int> > q1, q2, q3;

   // The following line would have caused an error because vector
   // does not support pop_front( ) and so cannot be adapted
   // by queue as a base container
   // queue <int, vector<int> > q1, q2, q3;

   q1.push( 1 );
   q2.push( 1 );
   q2.push( 2 );
   q3.push( 1 );

   if ( q1 != q2 )
      cout << "The queues q1 and q2 are not equal." << endl;
   else
      cout << "The queues q1 and q2 are equal." << endl;

   if ( q1 != q3 )
      cout << "The queues q1 and q3 are not equal." << endl;
   else
      cout << "The queues q1 and q3 are equal." << endl;
}
```

```Output
The queues q1 and q2 are not equal.
The queues q1 and q3 are equal.
```

## <a name="op_lt"></a>  – Operátor&lt;

Testuje, zda je objekt fronty na levé straně operátoru menší než objekt fronty na pravé straně.

```cpp
bool operator<(const queue <Type, Container>& left, const queue <Type, Container>& right,);
```

### <a name="parameters"></a>Parametry

*doleva*<br/>
Objekt typu `queue`.

*doprava*<br/>
Objekt typu `queue`.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud fronty na levé straně operátoru menší než a ne do fronty na pravé straně operátoru jinak **false**.

### <a name="remarks"></a>Poznámky

Porovnání mezi objekty fronty je založen na pairwise porovnání jejich prvky. Větší-než vztah mezi dvěma objekty fronty je založen na porovnání první pár prvků nerovnost.

### <a name="example"></a>Příklad

```cpp
// queue_op_lt.cpp
// compile with: /EHsc
#include <queue>
#include <iostream>

int main( )
{
   using namespace std;

   // Declares queues with default deque base container
   queue <int> q1, q2, q3;

   q1.push( 1 );
   q1.push( 2 );
   q2.push( 5 );
   q2.push( 10 );
   q3.push( 1 );
   q3.push( 2 );

   if ( q1 < q2 )
      cout << "The queue q1 is less than the queue q2." << endl;
   else
      cout << "The queue q1 is not less than the queue q2." << endl;

   if ( q1 < q3 )
      cout << "The queue q1 is less than the queue q3." << endl;
   else
      cout << "The queue q1 is not less than the queue q3." << endl;
}
```

```Output
The queue q1 is less than the queue q2.
The queue q1 is not less than the queue q3.
```

## <a name="op_lt_eq"></a>  – Operátor&lt;=

Testuje, zda je objekt fronty na levé straně operátoru je menší než nebo rovna hodnotě objekt fronty na pravé straně.

```cpp
bool operator<=(const queue <Type, Container>& left, const queue <Type, Container>& right,);
```

### <a name="parameters"></a>Parametry

*doleva*<br/>
Objekt typu `queue`.

*doprava*<br/>
Objekt typu `queue`.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud fronta na levé straně operátoru je striktně menší než fronty na pravé straně operátoru; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Porovnání mezi objekty fronty je založen na pairwise porovnání jejich prvky. Je menší než nebo rovna vztah mezi dvěma objekty podle porovnání první pár prvků nerovnost.

### <a name="example"></a>Příklad

```cpp
// queue_op_le.cpp
// compile with: /EHsc
#include <queue>
#include <iostream>

int main( )
{
   using namespace std;
   queue <int> q1, q2, q3;

   q1.push( 5 );
   q1.push( 10 );
   q2.push( 1 );
   q2.push( 2 );
   q3.push( 5 );
   q3.push( 10 );

   if ( q1 <= q2 )
      cout << "The queue q1 is less than or equal to "
           << "the queue q2." << endl;
   else
      cout << "The queue q1 is greater than "
           << "the queue q2." << endl;

   if ( q1 <= q3 )
      cout << "The queue q1 is less than or equal to "
           << "the queue q3." << endl;
   else
      cout << "The queue q1 is greater than "
           << "the queue q3." << endl;
}
```

```Output
The queue q1 is greater than the queue q2.
The queue q1 is less than or equal to the queue q3.
```

## <a name="op_eq_eq"></a>  Operator ==

Testuje, zda je objekt fronty na levé straně operátoru roven objektu fronty na pravé straně.

```cpp
bool operator==(const queue <Type, Container>& left, const queue <Type, Container>& right,);
```

### <a name="parameters"></a>Parametry

*doleva*<br/>
Objekt typu `queue`.

*doprava*<br/>
Objekt typu `queue`.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud fronty nejsou stejné; **false** Pokud fronty jsou si rovny.

### <a name="remarks"></a>Poznámky

Porovnání mezi objekty fronty je založen na pairwise porovnání jejich prvky. Pokud mají stejný počet prvků a jejich odpovídající elementy mají stejné hodnoty dvě fronty jsou si rovny. V opačném případě nerovnost.

### <a name="example"></a>Příklad

```cpp
// queue_op_eq.cpp
// compile with: /EHsc
#include <queue>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;

   // Declares queues with list base containers
   queue <int, list<int> > q1, q2, q3;

   // The following line would have caused an error because vector
   // does not support pop_front( ) and so cannot be adapted
   // by queue as a base container
   // queue <int, vector<int> > q1, q2, q3;

   q1.push( 1 );
   q2.push( 2 );
   q3.push( 1 );

   if ( q1 != q2 )
      cout << "The queues q1 and q2 are not equal." << endl;
   else
      cout << "The queues q1 and q2 are equal." << endl;

   if ( q1 != q3 )
      cout << "The queues q1 and q3 are not equal." << endl;
   else
      cout << "The queues q1 and q3 are equal." << endl;
}
```

```Output
The queues q1 and q2 are not equal.
The queues q1 and q3 are equal.
```

## <a name="op_gt"></a>  – Operátor&gt;

Testuje, zda je objekt fronty na levé straně operátoru větší než objekt fronty na pravé straně.

```cpp
bool operator>(const queue <Type, Container>& left, const queue <Type, Container>& right,);
```

### <a name="parameters"></a>Parametry

*doleva*<br/>
Objekt typu `queue`.

*doprava*<br/>
Objekt typu `queue`.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud fronta na levé straně operátoru je striktně menší než fronty na pravé straně operátoru; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Porovnání mezi objekty fronty je založen na pairwise porovnání jejich prvky. Větší-než vztah mezi dvěma objekty fronty je založen na porovnání první pár prvků nerovnost.

### <a name="example"></a>Příklad

```cpp
// queue_op_gt.cpp
// compile with: /EHsc
#include <queue>
#include <iostream>

int main( )
{
   using namespace std;
   queue <int> q1, q2, q3;

   q1.push( 1 );
   q1.push( 2 );
   q1.push( 3 );
   q2.push( 5 );
   q2.push( 10 );
   q3.push( 1 );
   q3.push( 2 );

   if ( q1 > q2 )
      cout << "The queue q1 is greater than "
           << "the queue q2." << endl;
   else
      cout << "The queue q1 is not greater than "
           << "the queue q2." << endl;

   if ( q1> q3 )
      cout << "The queue q1 is greater than "
           << "the queue q3." << endl;
   else
      cout << "The queue q1 is not greater than "
           << "the queue q3." << endl;
}
```

```Output
The queue q1 is not greater than the queue q2.
The queue q1 is greater than the queue q3.
```

## <a name="op_gt_eq"></a>  – Operátor&gt;=

Testuje, zda je objekt fronty na levé straně operátoru větší než nebo rovna hodnotě objekt fronty na pravé straně.

```cpp
bool operator>=(const queue <Type, Container>& left, const queue <Type, Container>& right,);
```

### <a name="parameters"></a>Parametry

*doleva*<br/>
Objekt typu `queue`.

*doprava*<br/>
Objekt typu `queue`.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud fronta na levé straně operátoru je striktně menší než fronty na pravé straně operátoru; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Porovnání mezi objekty fronty je založen na pairwise porovnání jejich prvky. Pokud mají stejný počet prvků a jejich odpovídající elementy mají stejné hodnoty dvě fronty jsou si rovny. V opačném případě nerovnost.

### <a name="example"></a>Příklad

```cpp
// queue_op_ge.cpp
// compile with: /EHsc
#include <queue>
#include <iostream>

int main( )
{
   using namespace std;
   queue <int> q1, q2, q3;

   q1.push( 1 );
   q1.push( 2 );
   q2.push( 5 );
   q2.push( 10 );
   q3.push( 1 );
   q3.push( 2 );

   if ( q1 >= q2 )
      cout << "The queue q1 is greater than or equal to "
           << "the queue q2." << endl;
   else
      cout << "The queue q1 is less than "
           << "the queue q2." << endl;

   if ( q1>= q3 )
      cout << "The queue q1 is greater than or equal to "
           << "the queue q3." << endl;
   else
      cout << "The queue q1 is less than "
           << "the queue q3." << endl;
}
```

```Output
The queue q1 is less than the queue q2.
The queue q1 is greater than or equal to the queue q3.
```

## <a name="see-also"></a>Viz také:

[\<fronty >](../standard-library/queue.md)<br/>
