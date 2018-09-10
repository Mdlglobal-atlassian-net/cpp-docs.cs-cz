---
title: '&lt;hash_map –&gt; operátory | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- hash_map/std::operator!=
- hash_map/std::operator==
dev_langs:
- C++
ms.assetid: 24b9bb9e-e983-4060-bce5-2c7c8161ee61
ms.openlocfilehash: bd140fed954c097fa73f179c92cbc64f3148e77c
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44108458"
---
# <a name="lthashmapgt-operators"></a>&lt;hash_map –&gt; operátory

|||
|-|-|
|[operator!=](#op_neq)|[Operator! = (multimap)](#op_neq_mm)|
|[operator==](#op_eq_eq)|[operator== (multimap)](#op_eq_eq_mm)|

## <a name="op_neq"></a>  Operator! =

> [!NOTE]
> Toto rozhraní API je zastaralé. Alternativou je [unordered_map – třída](unordered-map-class.md).

Testuje, zda je objekt hash_map na levé straně operátoru není roven objektu hash_map na pravé straně.

```cpp
bool operator!=(const hash_map <Key, Type, Traits, Allocator>& left, const hash_map <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*doleva*<br/>
Objekt typu `hash_map`.

*doprava*<br/>
Objekt typu `hash_map`.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud hash_maps nejsou stejné; **false** Pokud hash_maps jsou si rovny.

### <a name="remarks"></a>Poznámky

Porovnání mezi hash_map – objekty podle pairwise porovnání jejich prvky. Pokud mají stejný počet prvků a jejich odpovídající elementy mají stejné hodnoty dvou hash_maps jsou si rovny. V opačném případě nerovnost.

Členové [< hash_map >](hash-map.md) a [< hash_set >](hash-set.md) hlavičkové soubory v [ stdext Namespace](stdext-namespace.md).

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

Testuje, zda objekt hash_map na levé straně operátoru roven objektu hash_map na pravé straně.

```cpp
bool operator==(const hash_map <Key, Type, Traits, Allocator>& left, const hash_map <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*doleva*<br/>
Objekt typu `hash_map`.

*doprava*<br/>
Objekt typu `hash_map`.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** hash_map na levé straně operátoru je jinak hash_map na pravé straně operátoru roven **false**.

### <a name="remarks"></a>Poznámky

Porovnání mezi hash_map – objekty podle pairwise porovnání jejich prvky. Pokud mají stejný počet prvků a jejich odpovídající elementy mají stejné hodnoty dvou hash_maps jsou si rovny. V opačném případě nerovnost.

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

Testuje, zda je objekt hash_multimap na levé straně operátoru není roven objektu hash_multimap na pravé straně.

```cpp
bool operator!=(const hash_multimap <Key, Type, Traits, Allocator>& left, const hash_multimap <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*doleva*<br/>
Objekt typu `hash_multimap`.

*doprava*<br/>
Objekt typu `hash_multimap`.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud hash_multimaps nejsou stejné; **false** Pokud hash_multimaps jsou si rovny.

### <a name="remarks"></a>Poznámky

Porovnání mezi objekty hash_multimap vychází pairwise porovnání jejich prvky. Pokud mají stejný počet prvků a jejich odpovídající elementy mají stejné hodnoty dvou hash_multimaps jsou si rovny. V opačném případě nerovnost.

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

Testuje, zda objekt hash_multimap na levé straně operátoru roven objektu hash_multimap na pravé straně.

```cpp
bool operator==(const hash_multimap <Key, Type, Traits, Allocator>& left, const hash_multimap <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*doleva*<br/>
Objekt typu `hash_multimap`.

*doprava*<br/>
Objekt typu `hash_multimap`.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** hash_multimap na levé straně operátoru je jinak hash_multimap na pravé straně operátoru roven **false**.

### <a name="remarks"></a>Poznámky

Porovnání mezi objekty hash_multimap vychází pairwise porovnání jejich prvky. Pokud mají stejný počet prvků a jejich odpovídající elementy mají stejné hodnoty dvou hash_multimaps jsou si rovny. V opačném případě nerovnost.

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

## <a name="see-also"></a>Viz také:

[<hash_map>](hash-map.md)<br/>
