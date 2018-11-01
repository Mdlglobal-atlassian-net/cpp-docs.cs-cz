---
title: '&lt;Mapa&gt; operátory'
ms.date: 11/04/2016
f1_keywords:
- map/std::operator!=
- map/std::operator&gt;
- map/std::operator&gt;=
- map/std::operator&lt;
- map/std::operator&lt;=
- map/std::operator==
ms.assetid: 7df02b9f-701c-44ed-834a-a819badc5bd0
helpviewer_keywords:
- std::operator!= (map)
- std::operator&gt; (map)
- std::operator&gt;= (map)
- std::operator&lt; (map)
- std::operator&lt;= (map)
- std::operator== (map)
ms.openlocfilehash: 28acb02932ac2a6064ad49853adcb40dfb781520
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50504309"
---
# <a name="ltmapgt-operators"></a>&lt;Mapa&gt; operátory

||||
|-|-|-|
|[operator!=](#op_neq)|[– Operátor&gt;](#op_gt)|[– Operátor&gt;=](#op_gt_eq)|
|[– Operátor&lt;](#op_lt)|[– Operátor&lt;=](#op_lt_eq)|[operator==](#op_eq_eq)|
|[Operator! = (multimap)](#op_neq_multimap)|[– Operátor&gt;](#op_gt_multimap)|[– Operátor&gt;=](#op_gt_eq_multimap)|
|[– Operátor&lt;](#op_lt_multimap)|[– Operátor&lt;=](#op_lt_eq_multimap)|[operator==](#op_eq_eq_multimap)|

## <a name="op_neq"></a>  Operator! =

Testuje, zda je objekt map na levé straně operátoru není roven objektu map na pravé straně.

```cpp
bool operator!=(
      const map <Key, Type, Traits, Allocator>& left,
      const map <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*doleva*<br/>
Objekt typu `map`.

*doprava*<br/>
Objekt typu `map`.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud nejsou stejné; mapy **false** Pokud maps jsou si rovny.

### <a name="remarks"></a>Poznámky

Porovnání mezi objekty mapování vychází pairwise porovnání jejich prvky. Dvě mapy jsou stejné, pokud mají stejný počet prvků a jejich odpovídající elementy mají stejné hodnoty. V opačném případě nerovnost.

### <a name="example"></a>Příklad

```cpp
// map_op_ne.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int> m1, m2, m3;
   int i;
   typedef pair <int, int> Int_Pair;

   for ( i = 0 ; i < 3 ; i++ )
   {
      m1.insert ( Int_Pair ( i, i ) );
      m2.insert ( Int_Pair ( i, i * i ) );
      m3.insert ( Int_Pair ( i, i ) );
   }

   if ( m1 != m2 )
      cout << "The maps m1 and m2 are not equal." << endl;
   else
      cout << "The maps m1 and m2 are equal." << endl;

   if ( m1 != m3 )
      cout << "The maps m1 and m3 are not equal." << endl;
   else
      cout << "The maps m1 and m3 are equal." << endl;
}
/* Output:
The maps m1 and m2 are not equal.
The maps m1 and m3 are equal.
*/
```

## <a name="op_lt"></a>  – Operátor&lt;

Testuje, zda je objekt map na levé straně operátoru menší než objekt map na pravé straně.

```cpp
bool operator<(
      const map <Key, Type, Traits, Allocator>& left,
      const map <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*doleva*<br/>
Objekt typu `map`.

*doprava*<br/>
Objekt typu `map`.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud mapa na levé straně operátoru je striktně menší než mapování na pravé straně operátoru; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Porovnání mezi objekty mapování vychází pairwise porovnání jejich prvky. Větší-než vztah mezi dvěma objekty je založen na porovnání první pár prvků nerovnost.

### <a name="example"></a>Příklad

```cpp
// map_op_lt.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map<int, int> m1, m2, m3;
   int i;
   typedef pair<int, int> Int_Pair;

   for ( i = 1 ; i < 3 ; i++ )
   {
      m1.insert ( Int_Pair ( i, i ) );
      m2.insert ( Int_Pair ( i, i * i ) );
      m3.insert ( Int_Pair ( i, i - 1 ) );
   }

   if ( m1 < m2 )
      cout << "The map m1 is less than the map m2." << endl;
   else
      cout << "The map m1 is not less than the map m2." << endl;

   if ( m1 < m3 )
      cout << "The map m1 is less than the map m3." << endl;
   else
      cout << "The map m1 is not less than the map m3." << endl;
}
/* Output:
The map m1 is less than the map m2.
The map m1 is not less than the map m3.
*/
```

## <a name="op_lt_eq"></a>  – Operátor&lt;=

Testuje, zda na mapě objekt na levé straně operátoru je menší než nebo roven objektu map na pravé straně.

```cpp
bool operator<=(
      const map <Key, Type, Traits, Allocator>& left,
      const map <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*doleva*<br/>
Objekt typu `map`.

*doprava*<br/>
Objekt typu `map`.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud mapování na levé straně operátoru menší než nebo rovna mapování na pravé straně operátoru; v opačném případě **false**.

### <a name="example"></a>Příklad

```cpp
// map_op_le.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int> m1, m2, m3, m4;
   int i;
   typedef pair <int, int> Int_Pair;

   for ( i = 1 ; i < 3 ; i++ )
   {
      m1.insert ( Int_Pair ( i, i ) );
      m2.insert ( Int_Pair ( i, i * i ) );
      m3.insert ( Int_Pair ( i, i - 1 ) );
      m4.insert ( Int_Pair ( i, i ) );
   }

   if ( m1 <= m2 )
      cout << "The map m1 is less than or equal to the map m2." << endl;
   else
      cout << "The map m1 is greater than the map m2." << endl;

   if ( m1 <= m3 )
      cout << "The map m1 is less than or equal to the map m3." << endl;
   else
      cout << "The map m1 is greater than the map m3." << endl;

   if ( m1 <= m4 )
      cout << "The map m1 is less than or equal to the map m4." << endl;
   else
      cout << "The map m1 is greater than the map m4." << endl;
}
/* Output:
The map m1 is less than or equal to the map m2.
The map m1 is greater than the map m3.
The map m1 is less than or equal to the map m4.
*/
```

## <a name="op_eq_eq"></a>  Operator ==

Testuje, zda je objekt map na levé straně operátoru roven objektu map na pravé straně.

```cpp
bool operator==(
      const map <Key, Type, Traits, Allocator>& left,
      const map <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*doleva*<br/>
Objekt typu `map`.

*doprava*<br/>
Objekt typu `map`.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** mapování na levé straně operátoru je jinak mapování na pravé straně operátoru roven **false**.

### <a name="remarks"></a>Poznámky

Porovnání mezi objekty mapování vychází pairwise porovnání jejich prvky. Dvě mapy jsou stejné, pokud mají stejný počet prvků a jejich odpovídající elementy mají stejné hodnoty. V opačném případě nerovnost.

### <a name="example"></a>Příklad

```cpp
// map_op_eq.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map < int, int > m1, m2, m3;
   int i;
   typedef pair < int, int > Int_Pair;

   for ( i = 0 ; i < 3 ; i++ )
   {
      m1.insert ( Int_Pair ( i, i ) );
      m2.insert ( Int_Pair ( i, i * i ) );
      m3.insert ( Int_Pair ( i, i ) );
   }

   if ( m1 == m2 )
      cout << "The maps m1 and m2 are equal." << endl;
   else
      cout << "The maps m1 and m2 are not equal." << endl;

   if ( m1 == m3 )
      cout << "The maps m1 and m3 are equal." << endl;
   else
      cout << "The maps m1 and m3 are not equal." << endl;
}
/* Output:
The maps m1 and m2 are not equal.
The maps m1 and m3 are equal.
*/
```

## <a name="op_gt"></a>  – Operátor&gt;

Testuje, zda je objekt map na levé straně operátoru větší než objekt map na pravé straně.

```cpp
bool operator>(
      const map <Key, Type, Traits, Allocator>& left,
      const map <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*doleva*<br/>
Objekt typu `map`.

*doprava*<br/>
Objekt typu `map`.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** při mapování na levé straně operátoru větší než mapování na pravé straně operátoru; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Porovnání mezi objekty mapování vychází pairwise porovnání jejich prvky. Větší-než vztah mezi dvěma objekty je založen na porovnání první pár prvků nerovnost.

### <a name="example"></a>Příklad

```cpp
// map_op_gt.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map < int, int > m1, m2, m3;
   int i;
   typedef pair < int, int > Int_Pair;

   for ( i = 0 ; i < 3 ; i++ )
   {
      m1.insert ( Int_Pair ( i, i ) );
      m2.insert ( Int_Pair ( i, i * i ) );
      m3.insert ( Int_Pair ( i, i - 1 ) );
   }

   if ( m1 > m2 )
      cout << "The map m1 is greater than the map m2." << endl;
   else
      cout << "The map m1 is not greater than the map m2." << endl;

   if ( m1 > m3 )
      cout << "The map m1 is greater than the map m3." << endl;
   else
      cout << "The map m1 is not greater than the map m3." << endl;
}
/* Output:
The map m1 is not greater than the map m2.
The map m1 is greater than the map m3.
*/
```

## <a name="op_gt_eq"></a>  – Operátor&gt;=

Testuje, zda je objekt map na levé straně operátoru větší než nebo rovna hodnotě objekt map na pravé straně.

```cpp
bool operator>=(
      const map <Key, Type, Traits, Allocator>& left,
      const map <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*doleva*<br/>
Objekt typu `map`.

*doprava*<br/>
Objekt typu `map`.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** při mapování na levé straně operátoru větší než nebo rovna hodnotě mapování na pravé straně seznamu; v opačném případě **false**.

### <a name="example"></a>Příklad

```cpp
// map_op_ge.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map < int, int > m1, m2, m3, m4;
   int i;
   typedef pair < int, int > Int_Pair;

   for ( i = 1 ; i < 3 ; i++ )
   {
      m1.insert ( Int_Pair ( i, i ) );
      m2.insert ( Int_Pair ( i, i * i ) );
      m3.insert ( Int_Pair ( i, i - 1 ) );
      m4.insert ( Int_Pair ( i, i ) );
   }

   if ( m1 >= m2 )
      cout << "Map m1 is greater than or equal to map m2." << endl;
   else
      cout << "The map m1 is less than the map m2." << endl;

   if ( m1 >= m3 )
      cout << "Map m1 is greater than or equal to map m3." << endl;
   else
      cout << "The map m1 is less than the map m3." << endl;

   if ( m1 >= m4 )
      cout << "Map m1 is greater than or equal to map m4." << endl;
   else
      cout << "The map m1 is less than the map m4." << endl;
}
/* Output:
The map m1 is less than the map m2.
Map m1 is greater than or equal to map m3.
Map m1 is greater than or equal to map m4.
*/
```

## <a name="op_neq_multimap"></a>  Operator! = (multimap)

Testuje, zda je objektem multimap na levé straně operátoru není roven objektu multimap na pravé straně.

```cpp
bool operator!=(
      const multimap <Key, Type, Traits, Allocator>& left,
      const multimap <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*doleva*<br/>
Objekt typu `multimap`.

*doprava*<br/>
Objekt typu `multimap`.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud multimaps nejsou stejné; **false** Pokud multimaps jsou si rovny.

### <a name="remarks"></a>Poznámky

Porovnání mezi objekty multimap vychází pairwise porovnání jejich prvky. Pokud mají stejný počet prvků a jejich odpovídající elementy mají stejné hodnoty dvou multimaps jsou si rovny. V opačném případě nerovnost.

### <a name="example"></a>Příklad

```cpp
// multimap_op_ne.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1, m2, m3;
   int i;
   typedef pair <int, int> Int_Pair;

   for ( i = 0 ; i < 3 ; i++ )
   {
      m1.insert ( Int_Pair ( i, i ) );
      m2.insert ( Int_Pair ( i, i * i ) );
      m3.insert ( Int_Pair ( i, i ) );
   }

   if ( m1 != m2 )
      cout << "The multimaps m1 and m2 are not equal." << endl;
   else
      cout << "The multimaps m1 and m2 are equal." << endl;

   if ( m1 != m3 )
      cout << "The multimaps m1 and m3 are not equal." << endl;
   else
      cout << "The multimaps m1 and m3 are equal." << endl;
}
/* Output:
The multimaps m1 and m2 are not equal.
The multimaps m1 and m3 are equal.
*/
```

## <a name="op_lt_multimap"></a>  – Operátor&lt;

Testuje, zda je multimap objekt na levé straně operátoru menší než objektem multimap na pravé straně.

```cpp
bool operator<(
      const multimap <Key, Type, Traits, Allocator>& left,
      const multimap <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*doleva*<br/>
Objekt typu `multimap`.

*doprava*<br/>
Objekt typu `multimap`.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud multimap na levé straně operátoru je striktně menší než multimap na pravé straně operátoru; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Porovnání mezi objekty multimap vychází pairwise porovnání jejich prvky. Větší-než vztah mezi dvěma objekty je založen na porovnání první pár prvků nerovnost.

### <a name="example"></a>Příklad

```cpp
// multimap_op_lt.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap < int, int > m1, m2, m3;
   int i;
   typedef pair < int, int > Int_Pair;

   for ( i = 1 ; i < 3 ; i++ )
   {
      m1.insert ( Int_Pair ( i, i ) );
      m2.insert ( Int_Pair ( i, i * i ) );
      m3.insert ( Int_Pair ( i, i - 1 ) );
   }

   if ( m1 < m2 )
      cout << "The multimap m1 is less than the multimap m2." << endl;
   else
      cout << "The multimap m1 is not less than the multimap m2." << endl;

   if ( m1 < m3 )
      cout << "The multimap m1 is less than the multimap m3." << endl;
   else
      cout << "The multimap m1 is not less than the multimap m3." << endl;
}
/* Output:
The multimap m1 is less than the multimap m2.
The multimap m1 is not less than the multimap m3.
*/
```

## <a name="eq_multimap"></a>  – Operátor&lt;=

Testuje, zda je objekt multimap na levé straně operátoru je menší než nebo roven objektu multimap na pravé straně.

```cpp
bool operator<=(
      const multimap <Key, Type, Traits, Allocator>& left,
      const multimap <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*doleva*<br/>
Objekt typu `multimap`.

*doprava*<br/>
Objekt typu `multimap`.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud multimap na levé straně operátoru menší než nebo roven objektu multimap na pravé straně operátoru; v opačném případě **false**.

### <a name="example"></a>Příklad

```cpp
// multimap_op_le.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1, m2, m3, m4;
   int i;
   typedef pair <int, int> Int_Pair;

   for ( i = 1 ; i < 3 ; i++ )
   {
      m1.insert ( Int_Pair ( i, i ) );
      m2.insert ( Int_Pair ( i, i * i ) );
      m3.insert ( Int_Pair ( i, i - 1 ) );
      m4.insert ( Int_Pair ( i, i ) );
   }

   if ( m1 <= m2 )
      cout << "m1 is less than or equal to m2" << endl;
   else
      cout << "m1 is greater than m2" << endl;

   if ( m1 <= m3 )
      cout << "m1 is less than or equal to m3" << endl;
   else
      cout << "m1 is greater than m3" << endl;

   if ( m1 <= m4 )
      cout << "m1 is less than or equal to m4" << endl;
   else
      cout << "m1 is greater than m4" << endl;
}
/* Output:
m1 is less than or equal to m2
m1 is greater than m3
m1 is less than or equal to m4
*/
```

## <a name="op_eq_eq_multimap"></a>  Operator ==

Testuje, zda je objektem multimap na levé straně operátoru roven objektu multimap na pravé straně.

```cpp
bool operator==(
      const multimap <Key, Type, Traits, Allocator>& left,
      const multimap <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*doleva*<br/>
Objekt typu `multimap`.

*doprava*<br/>
Objekt typu `multimap`.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud multimap na levé straně operátoru roven objektu multimap na pravé straně operátoru; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Porovnání mezi objekty multimap vychází pairwise porovnání jejich prvky. Pokud mají stejný počet prvků a jejich odpovídající elementy mají stejné hodnoty dvou multimaps jsou si rovny. V opačném případě nerovnost.

### <a name="example"></a>Příklad

```cpp
// multimap_op_eq.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap<int, int> m1, m2, m3;
   int i;
   typedef pair<int, int> Int_Pair;

   for (i = 0; i < 3; i++)
   {
      m1.insert(Int_Pair(i, i));
      m2.insert(Int_Pair(i, i*i));
      m3.insert(Int_Pair(i, i));
   }

   if ( m1 == m2 )
      cout << "m1 and m2 are equal" << endl;
   else
      cout << "m1 and m2 are not equal" << endl;

   if ( m1 == m3 )
      cout << "m1 and m3 are equal" << endl;
   else
      cout << "m1 and m3 are not equal" << endl;
}
/* Output:
m1 and m2 are not equal
m1 and m3 are equal
*/
```

## <a name="op_gt_multimap"></a>  – Operátor&gt;

Testuje, zda je objektem multimap na levé straně operátoru větší než objektem multimap na pravé straně.

```cpp
bool operator>(
      const multimap <Key, Type, Traits, Allocator>& left,
      const multimap <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*doleva*<br/>
Objekt typu `multimap`.

*doprava*<br/>
Objekt typu `multimap`.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud multimap na levé straně operátoru větší než multimap na pravé straně operátoru; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Porovnání mezi objekty multimap vychází pairwise porovnání jejich prvky. Větší-než vztah mezi dvěma objekty je založen na porovnání první pár prvků nerovnost.

### <a name="example"></a>Příklad

```cpp
// multimap_op_gt.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap < int, int > m1, m2, m3;
   int i;
   typedef pair < int, int > Int_Pair;

   for ( i = 0 ; i < 3 ; i++ )
   {
      m1.insert ( Int_Pair ( i, i ) );
      m2.insert ( Int_Pair ( i, i * i ) );
      m3.insert ( Int_Pair ( i, i - 1 ) );
   }

   if ( m1 > m2 )
      cout << "The multimap m1 is greater than the multimap m2." << endl;
   else
      cout << "Multimap m1 is not greater than multimap m2." << endl;

   if ( m1 > m3 )
      cout << "The multimap m1 is greater than the multimap m3." << endl;
   else
      cout << "The multimap m1 is not greater than the multimap m3." << endl;
}
/* Output:
Multimap m1 is not greater than multimap m2.
The multimap m1 is greater than the multimap m3.
*/
```

## <a name="op_gt_eq_multimap"></a>  – Operátor&gt;=

Testuje, zda je objektem multimap na levé straně operátoru větší než nebo rovna hodnotě objektem multimap na pravé straně.

```cpp
bool operator>=(
      const multimap <Key, Type, Traits, Allocator>& left,
      const multimap <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*doleva*<br/>
Objekt typu `multimap`.

*doprava*<br/>
Objekt typu `multimap`.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud multimap na levé straně operátoru větší než nebo roven objektu multimap na pravé straně seznamu; v opačném případě **false**.

### <a name="example"></a>Příklad

```cpp
// multimap_op_ge.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap < int, int > m1, m2, m3, m4;
   int i;
   typedef pair < int, int > Int_Pair;

   for ( i = 1 ; i < 3 ; i++ )
   {
      m1.insert ( Int_Pair ( i, i ) );
      m2.insert ( Int_Pair ( i, i * i ) );
      m3.insert ( Int_Pair ( i, i - 1 ) );
      m4.insert ( Int_Pair ( i, i ) );
   }

   if ( m1 >= m2 )
      cout << "The multimap m1 is greater than or equal to the multimap m2." << endl;
   else
      cout << "The multimap m1 is less than the multimap m2." << endl;

   if ( m1 >= m3 )
      cout << "The multimap m1 is greater than or equal to the multimap m3." << endl;
   else
      cout << "The multimap m1 is less than the multimap m3." << endl;

   if ( m1 >= m4 )
      cout << "The multimap m1 is greater than or equal to the multimap m4." << endl;
   else
      cout << "The multimap m1 is less than the multimap m4." << endl;
}
/* Output:
The multimap m1 is less than the multimap m2.
The multimap m1 is greater than or equal to the multimap m3.
The multimap m1 is greater than or equal to the multimap m4.
*/
```

## <a name="see-also"></a>Viz také:

[\<map>](../standard-library/map.md)<br/>
