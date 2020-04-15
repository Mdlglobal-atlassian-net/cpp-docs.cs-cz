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
ms.openlocfilehash: 05f87cbb6061e205f9731d2a903ce52a2482b214
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336717"
---
# <a name="slice-class"></a>slice – třída

Třída nástroje valarray, která se používá k definování jednorozměrných podmnožiny nadřazené valarray. Pokud je valarray považován za dvojrozměrnou matici se všemi prvky v poli, pak řez extrahuje vektor v jedné dimenzi z dvojrozměrného pole.

## <a name="remarks"></a>Poznámky

Třída ukládá parametry, které charakterizují objekt typu [slice_array](../standard-library/slice-array-class.md) Podmnožina valarray je nepřímo vytvořena, když se objekt řezu třídy zobrazí jako argument pro objekt třídy [valarray](../standard-library/valarray-class.md#op_at)**\<Type>**. Uložené hodnoty, které určují podmnožinu vybranou z nadřazeného pole valarray, zahrnují:

- Počáteční index v poli valarray.

- Celková délka nebo počet prvků v řezu.

- Krok nebo vzdálenost mezi následnými indexy prvků v poli valarray.

Pokud je sada definovaná řezem podmnožinou konstantního valarrayu, pak je řez novým valarrayem. Pokud je sada definovaná řezem podmnožinou nestálého pole valarray, pak má řez referenční sémantiku na původní valarray. Mechanismus vyhodnocení pro nekonstantní valarrays šetří čas a paměť.

Operace na valarrays jsou zaručeny pouze v případě, že zdrojové a cílové podmnožiny definované řezy jsou odlišné a všechny indexy jsou platné.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[Plátek](#slice)|Definuje podmnožinu, `valarray` která se skládá z několika prvků, které jsou od sebe vzdáleny ve stejné vzdálenosti a které začínají určeným prvkem.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[Velikost](#size)|Vyhledá počet prvků v řezu `valarray`.|
|[Spustit](#start)|Najde počáteční index řezu `valarray`.|
|[Krok](#stride)|Vyhledá vzdálenost mezi prvky v `valarray`řezu .|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<valarray>

**Obor názvů:** std

## <a name="slicesize"></a><a name="size"></a>řez:velikost

Vyhledá počet prvků v řezu valarray.

```cpp
size_t size() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet prvků v řezu valarray.

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

## <a name="sliceslice"></a><a name="slice"></a>řez::řez

Definuje podmnožinu valarray, který se skládá z počtu prvků, které jsou stejné vzdálenosti od sebe a které začínají na zadaný prvek.

```cpp
slice();

slice(
    size_t _StartIndex,
    size_t _Len,
    size_t stride);
```

### <a name="parameters"></a>Parametry

*_StartIndex*\
Index valarray prvního prvku v podsadě.

*_Len*\
Počet prvků v podsadě.

*Krok*\
Vzdálenost mezi prvky v podsadě.

### <a name="return-value"></a>Návratová hodnota

Výchozí konstruktor ukládá nuly pro počáteční index, celkovou délku a krok. Druhý konstruktor ukládá *_StartIndex* pro počáteční index, *_Len* pro celkovou délku a *krok* pro krok.

### <a name="remarks"></a>Poznámky

Krok může být negativní.

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

## <a name="slicestart"></a><a name="start"></a>řez:začátek

Najde počáteční index řezu valarray.

```cpp
size_t start() const;
```

### <a name="return-value"></a>Návratová hodnota

Počáteční index řezu valarray.

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

## <a name="slicestride"></a><a name="stride"></a>řez::krok

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
