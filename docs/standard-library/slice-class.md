---
title: slice – třída
ms.date: 11/04/2016
f1_keywords:
- valarray/std::slice
- valarray/std::slice::size
- valarray/std::slice::start
- valarray/std::slice::stride
helpviewer_keywords:
- std::slice [C++]
- std::slice [C++], size
- std::slice [C++], start
- std::slice [C++], stride
ms.assetid: 00f0b03d-d657-4b81-ba53-5a9034bb2bf2
ms.openlocfilehash: 830e345eb7522cef44dbf6e727a976fb79c1e081
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/11/2020
ms.locfileid: "79094841"
---
# <a name="slice-class"></a>slice – třída

Třída nástrojů pro valarray, která se používá k definování jednorozměrné podmnožiny nadřazeného valarray. Pokud je valarray považována za dvourozměrnou matici se všemi prvky v poli, pak řez z dvojrozměrného pole vyextrahuje vektor v jednom rozměru.

## <a name="remarks"></a>Poznámky

Třída ukládá parametry, které charakterizují objekt typu [slice_array](../standard-library/slice-array-class.md) podmnožina valarray je nepřímo vytvořena, když se objekt řezu zobrazí jako argument pro objekt třídy [valarray](../standard-library/valarray-class.md#op_at) **\<typu >** . Uložené hodnoty, které určují podmnožinu vybrané z nadřazené valarray, zahrnují:

- Počáteční index v valarray.

- Celková délka nebo počet prvků v řezu.

- Rozteč nebo vzdálenost mezi následnými indexy prvků v valarray.

Je-li sada definovaná v řezu podmnožinou konstantního valarray, pak je řez novou valarray. Je-li sada definovaná v řezu podmnožinou nekonstantního valarray, pak má řez referenční sémantiku původní valarray. Mechanismus vyhodnocení pro nekonstantní valarrays šetří čas a paměť.

Operace na valarrays jsou zaručeny pouze v případě, že zdrojové a cílové podmnožiny, které jsou definovány řezy, jsou jedinečné a všechny indexy jsou platné.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[průřez](#slice)|Definuje podmnožinu `valarray`, která se skládá z několika prvků, které jsou rovny stejné vzdálenosti a které začínají specifikovaným elementem.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[hodnota](#size)|Najde počet prvků v řezu `valarray`.|
|[start](#start)|Najde počáteční index řezu `valarray`.|
|[mezer](#stride)|Najde vzdálenost mezi prvky v řezu `valarray`.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<valarray >

**Obor názvů:** std

## <a name="size"></a>řez:: velikost

Najde počet prvků v řezu valarray.

```cpp
size_t size() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet elementů v řezu valarray.

### <a name="example"></a>Příklad

```cpp
// slice_size.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;
   size_t sizeVA, sizeVAR;

   valarray<int> va ( 20 ), vaResult;
   for ( i = 0 ; i < 20 ; i += 1 )
      va [ i ] =  i+1;

   cout << "The operand valarray va is:\n ( ";
      for ( i = 0 ; i < 20 ; i++ )
         cout << va [ i ] << " ";
   cout << ")." << endl;

   sizeVA = va.size ( );
   cout << "The size of the valarray is: "
        << sizeVA << "." << endl << endl;

   slice vaSlice ( 3 , 6 , 3 );
   vaResult = va [ vaSlice ];

   cout << "The slice of valarray va is vaResult = "
        << "va[slice( 3, 6, 3)] =\n ( ";
      for ( i = 0 ; i < 6 ; i++ )
         cout << vaResult [ i ] << " ";
   cout << ")." << endl;

   sizeVAR = vaSlice.size ( );
   cout << "The size of slice vaSlice is: "
        << sizeVAR << "." << endl;
}
```

```Output
The operand valarray va is:
( 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 ).
The size of the valarray is: 20.

The slice of valarray va is vaResult = va[slice( 3, 6, 3)] =
( 4 7 10 13 16 19 ).
The size of slice vaSlice is: 6.
```

## <a name="slice"></a>řez:: Slice

Definuje podmnožinu valarray, která se skládá z několika prvků, které jsou rovny stejné vzdálenosti a které začínají specifikovaným elementem.

```cpp
slice();

slice(
    size_t _StartIndex,
    size_t _Len,
    size_t stride);
```

### <a name="parameters"></a>Parametry

*_StartIndex*\
Index valarray prvního prvku v podmnožině.

*_Len*\
Počet prvků v podmnožině.

\ *mezer*
Vzdálenost mezi prvky v podmnožině.

### <a name="return-value"></a>Návratová hodnota

Výchozí konstruktor ukládá nuly pro počáteční index, celkovou délku a rozteč. Druhý konstruktor ukládá *_StartIndex* pro počáteční index, *_LEN* pro celkovou délku a *Rozteč* pro rozteč.

### <a name="remarks"></a>Poznámky

Rozteč může být záporná.

### <a name="example"></a>Příklad

```cpp
// slice_ctor.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> va ( 20 ), vaResult;
   for ( i = 0 ; i < 20 ; i+=1 )
      va [ i ] =  2 * (i + 1 );

   cout << "The operand valarray va is:\n( ";
      for ( i = 0 ; i < 20 ; i++ )
         cout << va [ i ] << " ";
   cout << ")." << endl;

   slice vaSlice ( 1 , 7 , 3 );
   vaResult = va [ vaSlice ];

   cout << "\nThe slice of valarray va is vaResult:"
        << "\nva[slice( 1, 7, 3)] = ( ";
      for ( i = 0 ; i < 7 ; i++ )
         cout << vaResult [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The operand valarray va is:
( 2 4 6 8 10 12 14 16 18 20 22 24 26 28 30 32 34 36 38 40 ).

The slice of valarray va is vaResult:
va[slice( 1, 7, 3)] = ( 4 10 16 22 28 34 40 ).
```

## <a name="start"></a>řez:: Start

Najde počáteční index řezu valarray.

```cpp
size_t start() const;
```

### <a name="return-value"></a>Návratová hodnota

Počáteční index řezu valarray

### <a name="example"></a>Příklad

```cpp
// slice_start.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;
   size_t startVAR;

   valarray<int> va ( 20 ), vaResult;
   for ( i = 0 ; i < 20 ; i += 1 )
      va [ i ] = i+1;

   cout << "The operand valarray va is:\n ( ";
      for ( i = 0 ; i < 20 ; i++ )
         cout << va [ i ] << " ";
   cout << ")." << endl;

   slice vaSlice ( 3 , 6 , 3 );
   vaResult = va [ vaSlice ];

   cout << "The slice of valarray va is vaResult = "
        << "va[slice( 3, 6, 3)] =\n ( ";
      for ( i = 0 ; i < 6 ; i++ )
         cout << vaResult [ i ] << " ";
   cout << ")." << endl;

   startVAR = vaSlice.start ( );
   cout << "The start index of slice vaSlice is: "
        << startVAR << "." << endl;
}
```

```Output
The operand valarray va is:
( 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 ).
The slice of valarray va is vaResult = va[slice( 3, 6, 3)] =
( 4 7 10 13 16 19 ).
The start index of slice vaSlice is: 3.
```

## <a name="stride"></a>Slice:: rozteč

Najde vzdálenost mezi prvky v řezu valarray.

```cpp
size_t stride() const;
```

### <a name="return-value"></a>Návratová hodnota

Vzdálenost mezi prvky v řezu valarray.

### <a name="example"></a>Příklad

```cpp
// slice_stride.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;
   size_t strideVAR;

   valarray<int> va ( 20 ), vaResult;
   for ( i = 0 ; i < 20 ; i += 1 )
      va [ i ] =  3 * ( i + 1 );

   cout << "The operand valarray va is:\n ( ";
      for ( i = 0 ; i < 20 ; i++ )
         cout << va [ i ] << " ";
   cout << ")." << endl;

   slice vaSlice ( 4 , 5 , 3 );
   vaResult = va [ vaSlice ];

   cout << "The slice of valarray va is vaResult = "
        << "va[slice( 4, 5, 3)] =\n ( ";
      for ( i = 0 ; i < 5 ; i++ )
         cout << vaResult [ i ] << " ";
   cout << ")." << endl;

   strideVAR = vaSlice.stride ( );
   cout << "The stride of slice vaSlice is: "
        << strideVAR << "." << endl;
}
```

```Output
The operand valarray va is:
( 3 6 9 12 15 18 21 24 27 30 33 36 39 42 45 48 51 54 57 60 ).
The slice of valarray va is vaResult = va[slice( 4, 5, 3)] =
( 15 24 33 42 51 ).
The stride of slice vaSlice is: 3.
```

## <a name="see-also"></a>Viz také

[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
