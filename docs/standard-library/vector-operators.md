---
title: '&lt;vektor&gt; operátory | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vector/std::operator!=
- vector/std::operator&gt;
- vector/std::operator&gt;=
- vector/std::operator&lt;
- vector/std::operator&lt;=
- vector/std::operator==
dev_langs:
- C++
ms.assetid: 1d14f312-6f59-4ec7-88ae-95f89a558823
helpviewer_keywords:
- std::operator!= (vector)
- std::operator&gt; (vector)
- std::operator&gt;= (vector)
- std::operator&lt; (vector)
- std::operator&lt;= (vector)
- std::operator== (vector)
ms.openlocfilehash: b3a67fb381e262ddec71c36f226412b8f9b74b68
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45725124"
---
# <a name="ltvectorgt-operators"></a>&lt;vektor&gt; operátory

||||
|-|-|-|
|[operator!=](#op_neq)|[– Operátor&gt;](#op_gt)|[– Operátor&gt;=](#op_gt_eq)|
|[– Operátor&lt;](#op_lt)|[– Operátor&lt;=](#op_lt_eq)|[operator==](#op_eq_eq)|

## <a name="op_neq"></a>  Operator! =

Testuje, zda je objekt na levé straně operátoru není roven objektu na pravé straně.

```cpp
bool operator!=(const vector<Type, Allocator>& left, const vector<Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*doleva*<br/>
Objekt typu `vector`.

*doprava*<br/>
Objekt typu `vector`.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud vektory nejsou stejné; **false** Pokud jsou vektory stejné.

### <a name="remarks"></a>Poznámky

Dva vektory jsou stejné, pokud mají stejný počet prvků a jejich odpovídající elementy mají stejné hodnoty. V opačném případě nerovnost.

### <a name="example"></a>Příklad

```cpp
// vector_op_ne.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   vector <int> v1, v2;
   v1.push_back( 1 );
     v2.push_back( 2 );

   if ( v1 != v2 )
      cout << "Vectors not equal." << endl;
   else
      cout << "Vectors equal." << endl;
}
```

```Output
Vectors not equal.
```

## <a name="op_lt"></a>  – Operátor&lt;

Testuje, zda je objekt na levé straně operátoru menší než objekt na pravé straně.

```cpp
bool operator<(const vector<Type, Allocator>& left, const vector<Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*doleva*<br/>
Objekt typu `vector`.

*doprava*<br/>
Objekt typu `vector`.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud vektoru na levé straně operátoru menší než vektoru na pravé straně operátoru; v opačném případě **false**.

### <a name="example"></a>Příklad

```cpp
// vector_op_lt.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   vector <int> v1, v2;
   v1.push_back( 1 );
   v1.push_back( 2 );
   v1.push_back( 4 );

   v2.push_back( 1 );
   v2.push_back( 3 );

   if ( v1 < v2 )
      cout << "Vector v1 is less than vector v2." << endl;
   else
      cout << "Vector v1 is not less than vector v2." << endl;
}
```

```Output
Vector v1 is less than vector v2.
```

## <a name="op_lt_eq"></a>  – Operátor&lt;=

Testuje, zda je objekt na levé straně operátoru menší než nebo roven objektu na pravé straně.

```cpp
bool operator<=(const vector<Type, Allocator>& left, const vector<Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*doleva*<br/>
Objekt typu `vector`.

*doprava*<br/>
Objekt typu `vector`.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud vektoru na levé straně operátoru menší než nebo rovna hodnotě vektoru na pravé straně operátoru; v opačném případě **false**.

### <a name="example"></a>Příklad

```cpp
// vector_op_le.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   vector <int> v1, v2;
   v1.push_back( 1 );
   v1.push_back( 2 );
   v1.push_back( 4 );

   v2.push_back( 1 );
   v2.push_back( 3 );

   if ( v1 <= v2 )
      cout << "Vector v1 is less than or equal to vector v2." << endl;
   else
      cout << "Vector v1 is greater than vector v2." << endl;
}
```

```Output
Vector v1 is less than or equal to vector v2.
```

## <a name="op_eq_eq"></a>  Operator ==

Testuje, zda je objekt na levé straně operátoru roven objektu na pravé straně.

```cpp
bool operator==(const vector<Type, Allocator>& left, const vector<Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*doleva*<br/>
Objekt typu `vector`.

*doprava*<br/>
Objekt typu `vector`.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** vektoru na levé straně operátoru je jinak vektoru na pravé straně operátoru roven **false**.

### <a name="remarks"></a>Poznámky

Dva vektory jsou stejné, pokud mají stejný počet prvků a jejich odpovídající elementy mají stejné hodnoty. V opačném případě nerovnost.

### <a name="example"></a>Příklad

```cpp
// vector_op_eq.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   vector <int> v1, v2;
   v1.push_back( 1 );
   v2.push_back( 1 );

   if ( v1 == v2 )
      cout << "Vectors equal." << endl;
   else
      cout << "Vectors not equal." << endl;
}
```

```Output
Vectors equal.
```

## <a name="op_gt"></a>  – Operátor&gt;

Testuje, zda je objekt na levé straně operátoru větší než objekt na pravé straně.

```cpp
bool operator>(const vector<Type, Allocator>& left, const vector<Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*doleva*<br/>
Objekt typu `vector`.

*doprava*<br/>
Objekt typu `vector`.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud vektoru na levé straně operátoru větší než vektoru na pravé straně operátoru; v opačném případě **false**.

### <a name="example"></a>Příklad

```cpp
// vector_op_gt.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   vector <int> v1, v2;
   v1.push_back( 1 );
   v1.push_back( 3 );
   v1.push_back( 1 );

   v2.push_back( 1 );
   v2.push_back( 2 );
   v2.push_back( 2 );

   if ( v1 > v2 )
      cout << "Vector v1 is greater than vector v2." << endl;
   else
      cout << "Vector v1 is not greater than vector v2." << endl;
}
```

```Output
Vector v1 is greater than vector v2.
```

## <a name="op_gt_eq"></a>  – Operátor&gt;=

Testuje, zda je objekt na levé straně operátoru větší než nebo stejný jako objekt na pravé straně.

```cpp
bool operator>=(const vector<Type, Allocator>& left, const vector<Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*doleva*<br/>
Objekt typu `vector`.

*doprava*<br/>
Objekt typu `vector`.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud vektoru na levé straně operátoru větší než nebo rovna hodnotě vektoru na pravé straně vektoru; v opačném případě **false**.

### <a name="example"></a>Příklad

```cpp
// vector_op_ge.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   vector <int> v1, v2;
   v1.push_back( 1 );
   v1.push_back( 3 );
   v1.push_back( 1 );

     v2.push_back( 1 );
   v2.push_back( 2 );
   v2.push_back( 2 );

   if ( v1 >= v2 )
      cout << "Vector v1 is greater than or equal to vector v2." << endl;
   else
      cout << "Vector v1 is less than vector v2." << endl;
}
```

```Output
Vector v1 is greater than or equal to vector v2.
```

## <a name="see-also"></a>Viz také:

[\<vektor >](../standard-library/vector.md)<br/>
