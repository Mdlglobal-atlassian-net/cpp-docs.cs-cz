---
title: operátory &lt;hash_map&gt;
ms.date: 11/04/2016
f1_keywords:
- hash_map/std::operator!=
- hash_map/std::operator==
ms.assetid: 24b9bb9e-e983-4060-bce5-2c7c8161ee61
ms.openlocfilehash: c4cc73feb3c8163a2be9f0122f57eaa0fb8ab3b8
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79419012"
---
# <a name="lthash_mapgt-operators"></a>operátory &lt;hash_map&gt;

|||
|-|-|
|[operator!=](#op_neq)|[operator! = (multimap) – operátor](#op_neq_mm)|
|[operator = = – operátor](#op_eq_eq)|[operator = = (multimap) – operátor](#op_eq_eq_mm)|

## <a name="op_neq"></a>! = – operátor

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativa je [Unordered_map třídy](unordered-map-class.md).

Testuje, zda hash_map objekt na levé straně operátoru není roven objektu hash_map na pravé straně.

```cpp
bool operator!=(const hash_map <Key, Type, Traits, Allocator>& left, const hash_map <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*levý*\
Objekt typu `hash_map`.

*pravé*\
Objekt typu `hash_map`.

### <a name="return-value"></a>Návratová hodnota

**true** , Pokud hash_maps nejsou stejné; **false** , pokud je hash_maps rovna.

### <a name="remarks"></a>Poznámky

Porovnání mezi hash_map objekty je založeno na porovnávacím porovnání jejich prvků. Dva hash_maps jsou stejné, pokud mají stejný počet prvků a jejich příslušné prvky mají stejné hodnoty. V opačném případě jsou nerovné.

Členové [< hash_map >](hash-map.md) a < soubory hlaviček [hash_set >](hash-set.md) v [oboru názvů stdext](stdext-namespace.md).

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

## <a name="op_eq_eq"></a>operator = = – operátor

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativa je [Unordered_map třídy](unordered-map-class.md).

Testuje, zda je objekt hash_map na levé straně operátoru roven objektu hash_map na pravé straně.

```cpp
bool operator==(const hash_map <Key, Type, Traits, Allocator>& left, const hash_map <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*levý*\
Objekt typu `hash_map`.

*pravé*\
Objekt typu `hash_map`.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud je hash_map na levé straně operátoru rovno hash_map na pravé straně operátoru; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Porovnání mezi hash_map objekty je založeno na porovnávacím porovnání jejich prvků. Dva hash_maps jsou stejné, pokud mají stejný počet prvků a jejich příslušné prvky mají stejné hodnoty. V opačném případě jsou nerovné.

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

## <a name="op_neq_mm"></a>operator! = (hash_multimap) – operátor

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativa je [Unordered_multimap třídy](unordered-multimap-class.md).

Testuje, zda hash_multimap objekt na levé straně operátoru není roven objektu hash_multimap na pravé straně.

```cpp
bool operator!=(const hash_multimap <Key, Type, Traits, Allocator>& left, const hash_multimap <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*levý*\
Objekt typu `hash_multimap`.

*pravé*\
Objekt typu `hash_multimap`.

### <a name="return-value"></a>Návratová hodnota

**true** , Pokud hash_multimaps nejsou stejné; **false** , pokud je hash_multimaps rovna.

### <a name="remarks"></a>Poznámky

Porovnání mezi hash_multimap objekty je založeno na porovnávacím porovnání jejich prvků. Dva hash_multimaps jsou stejné, pokud mají stejný počet prvků a jejich příslušné prvky mají stejné hodnoty. V opačném případě jsou nerovné.

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

## <a name="op_eq_eq_mm"></a>operator = = (hash_multimap) – operátor

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativa je [Unordered_multimap třídy](unordered-multimap-class.md).

Testuje, zda je objekt hash_multimap na levé straně operátoru roven objektu hash_multimap na pravé straně.

```cpp
bool operator==(const hash_multimap <Key, Type, Traits, Allocator>& left, const hash_multimap <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*levý*\
Objekt typu `hash_multimap`.

*pravé*\
Objekt typu `hash_multimap`.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud je hash_multimap na levé straně operátoru rovno hash_multimap na pravé straně operátoru; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Porovnání mezi hash_multimap objekty je založeno na porovnávacím porovnání jejich prvků. Dva hash_multimaps jsou stejné, pokud mají stejný počet prvků a jejich příslušné prvky mají stejné hodnoty. V opačném případě jsou nerovné.

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

[<hash_map>](hash-map.md)
