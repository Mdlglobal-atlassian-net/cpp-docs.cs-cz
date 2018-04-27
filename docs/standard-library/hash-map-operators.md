---
title: '&lt;hash_map –&gt; operátory | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- hash_map/std::operator!=
- hash_map/std::operator==
dev_langs:
- C++
ms.assetid: 24b9bb9e-e983-4060-bce5-2c7c8161ee61
caps.latest.revision: 13
manager: ghogen
ms.openlocfilehash: 0b4b2a2c98e47752dbfb30afb2a0de522bcbb9f7
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="lthashmapgt-operators"></a>&lt;hash_map –&gt; operátory

|||
|-|-|
|[operator!=](#op_neq)|[Operator! = (multimap)](#op_neq_mm)|
|[operator==](#op_eq_eq)|[operator== (multimap)](#op_eq_eq_mm)|

## <a name="op_neq"></a>  Operator! =

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_map – třída](unordered-map-class.md).

Testy, pokud hash_map objekt na levé straně operátoru není stejný jako hash_map objekt na pravé straně.

```cpp
bool operator!=(const hash_map <Key, Type, Traits, Allocator>& left, const hash_map <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

`left` Objekt typu `hash_map`.

`right` Objekt typu `hash_map`.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE,** Pokud hash_maps není stejný; **false** Pokud hash_maps jsou stejné.

### <a name="remarks"></a>Poznámky

Porovnání mezi hash_map – objekty je založena na pairwise porovnání jejich součástí. Dva hash_maps jsou stejné, pokud mají stejný počet elementů a jejich odpovídajících elementy mají stejné hodnoty. Jinak nerovné.

Členové [< hash_map >](hash-map.md) a [< hash_set >](hash-set.md) hlavičkové soubory v [ stdext – Namespace](stdext-namespace.md).

### <a name="example"></a>Příklad

```cpp
// hash_map_op_ne.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1, hm2, hm3;
   int i;
   typedef pair <int, int> Int_Pair;

   for ( i = 0 ; i < 3 ; i++ )
   {
      hm1.insert ( Int_Pair ( i, i ) );
      hm2.insert ( Int_Pair ( i, i * i ) );
      hm3.insert ( Int_Pair ( i, i ) );
   }

   if ( hm1 != hm2 )
      cout << "The hash_maps hm1 and hm2 are not equal." << endl;
   else
      cout << "The hash_maps hm1 and hm2 are equal." << endl;

   if ( hm1 != hm3 )
      cout << "The hash_maps hm1 and hm3 are not equal." << endl;
   else
      cout << "The hash_maps hm1 and hm3 are equal." << endl;
}
```

```Output
The hash_maps hm1 and hm2 are not equal.
The hash_maps hm1 and hm3 are equal.
```

## <a name="op_eq_eq"></a>  Operator ==

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_map – třída](unordered-map-class.md).

Testy, pokud hash_map objekt na levé straně operátoru rovná hash_map objekt na pravé straně.

```cpp
bool operator==(const hash_map <Key, Type, Traits, Allocator>& left, const hash_map <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

`left` Objekt typu `hash_map`.

`right` Objekt typu `hash_map`.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE,** Pokud hash_map na levé straně operátoru rovná hash_map na pravé straně operátoru; jinak hodnota **false**.

### <a name="remarks"></a>Poznámky

Porovnání mezi hash_map – objekty je založena na pairwise porovnání jejich součástí. Dva hash_maps jsou stejné, pokud mají stejný počet elementů a jejich odpovídajících elementy mají stejné hodnoty. Jinak nerovné.

### <a name="example"></a>Příklad

```cpp
// hash_map_op_eq.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1, hm2, hm3;
   int i;
   typedef pair <int, int> Int_Pair;

   for ( i = 0 ; i < 3 ; i++ )
   {
      hm1.insert ( Int_Pair ( i, i ) );
      hm2.insert ( Int_Pair ( i, i * i ) );
      hm3.insert ( Int_Pair ( i, i ) );
   }

   if ( hm1 == hm2 )
      cout << "The hash_maps hm1 and hm2 are equal." << endl;
   else
      cout << "The hash_maps hm1 and hm2 are not equal." << endl;

   if ( hm1 == hm3 )
      cout << "The hash_maps hm1 and hm3 are equal." << endl;
   else
      cout << "The hash_maps hm1 and hm3 are not equal." << endl;
}
```

```Output
The hash_maps hm1 and hm2 are not equal.
The hash_maps hm1 and hm3 are equal.
```

## <a name="op_neq_mm"></a>  Operator! = (hash_multimap)

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_multimap – třída](unordered-multimap-class.md).

Testy, pokud hash_multimap objekt na levé straně operátoru není stejný jako hash_multimap objekt na pravé straně.

```cpp
bool operator!=(const hash_multimap <Key, Type, Traits, Allocator>& left, const hash_multimap <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

`left` Objekt typu `hash_multimap`.

`right` Objekt typu `hash_multimap`.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE,** Pokud hash_multimaps není stejný; **false** Pokud hash_multimaps jsou stejné.

### <a name="remarks"></a>Poznámky

Porovnání mezi objekty hash_multimap je založena na pairwise porovnání jejich součástí. Dva hash_multimaps jsou stejné, pokud mají stejný počet elementů a jejich odpovídajících elementy mají stejné hodnoty. Jinak nerovné.

### <a name="example"></a>Příklad

```cpp
// hash_multimap_op_ne.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int> hm1, hm2, hm3;
   int i;
   typedef pair <int, int> Int_Pair;

   for ( i = 0 ; i < 3 ; i++ )
   {
      hm1.insert ( Int_Pair ( i, i ) );
      hm2.insert ( Int_Pair ( i, i * i ) );
      hm3.insert ( Int_Pair ( i, i ) );
   }

   if ( hm1 != hm2 )
      cout << "The hash_multimaps hm1 and hm2 are not equal." << endl;
   else
      cout << "The hash_multimaps hm1 and hm2 are equal." << endl;

   if ( hm1 != hm3 )
      cout << "The hash_multimaps hm1 and hm3 are not equal." << endl;
   else
      cout << "The hash_multimaps hm1 and hm3 are equal." << endl;
}
```

```Output
The hash_multimaps hm1 and hm2 are not equal.
The hash_multimaps hm1 and hm3 are equal.
```

## <a name="op_eq_eq_mm"></a>  Operator == (hash_multimap)

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_multimap – třída](unordered-multimap-class.md).

Testy, pokud hash_multimap objekt na levé straně operátoru rovná hash_multimap objekt na pravé straně.

```cpp
bool operator==(const hash_multimap <Key, Type, Traits, Allocator>& left, const hash_multimap <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

`left` Objekt typu `hash_multimap`.

`right` Objekt typu `hash_multimap`.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE,** Pokud hash_multimap na levé straně operátoru rovná hash_multimap na pravé straně operátoru; jinak hodnota **false**.

### <a name="remarks"></a>Poznámky

Porovnání mezi objekty hash_multimap je založena na pairwise porovnání jejich součástí. Dva hash_multimaps jsou stejné, pokud mají stejný počet elementů a jejich odpovídajících elementy mají stejné hodnoty. Jinak nerovné.

### <a name="example"></a>Příklad

```cpp
// hash_multimap_op_eq.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap<int, int> hm1, hm2, hm3;
   int i;
   typedef pair<int, int> Int_Pair;

   for (i = 0; i < 3; i++)
   {
      hm1.insert(Int_Pair(i, i));
      hm2.insert(Int_Pair(i, i*i));
      hm3.insert(Int_Pair(i, i));
   }

   if ( hm1 == hm2 )
      cout << "The hash_multimaps hm1 and hm2 are equal." << endl;
   else
      cout << "The hash_multimaps hm1 and hm2 are not equal." << endl;

   if ( hm1 == hm3 )
      cout << "The hash_multimaps hm1 and hm3 are equal." << endl;
   else
      cout << "The hash_multimaps hm1 and hm3 are not equal." << endl;
}
```

```Output
The hash_multimaps hm1 and hm2 are not equal.
The hash_multimaps hm1 and hm3 are equal.
```

## <a name="see-also"></a>Viz také

[<hash_map>](hash-map.md)<br/>
