---
title: Slice – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- valarray/std::slice
- valarray/std::slice::size
- valarray/std::slice::start
- valarray/std::slice::stride
dev_langs:
- C++
helpviewer_keywords:
- std::slice [C++]
- std::slice [C++], size
- std::slice [C++], start
- std::slice [C++], stride
ms.assetid: 00f0b03d-d657-4b81-ba53-5a9034bb2bf2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6a2cff4aea707c98a4bce7060b16ce695d25c47d
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44109003"
---
# <a name="slice-class"></a>slice – třída

Třídy nástrojů pro valarray –, který se používá k definování jednorozměrné podmnožiny valarray nadřazené. Pokud valarray se považuje za dvojrozměrné matici po všechny elementy v matici, řez extrahuje vektor v jedné dimenzi mimo dvourozměrné pole.

## <a name="remarks"></a>Poznámky

Třída obsahuje parametry, které charakterizují objekt typu [slice_array –](../standard-library/slice-array-class.md) podmnožinu valarray zkonstruování nepřímo když objekt třídy řez se objeví jako argument pro objekt třídy [valarray ](../standard-library/valarray-class.md#op_at)  **\<Typ >**. Uložené hodnoty, které určují dílčí vybrat z nadřazené valarray patří:

- Počáteční index valarray.

- Celková délka, nebo počet elementů v řezu.

- Stride nebo vzdálenost mezi následné indexy prvků valarray.

Pokud množiny definované řez je podmnožinou konstantní valarray, je řez nové valarray. Pokud množiny definované řez je podmnožinou nekonstantním valarray, řez má sémantiku odkazu pro původní valarray. Vyhodnocení mechanismus pro nekonstantním valarrays šetří čas a paměti.

Operace s valarrays zaručeno pouze v případě, že zdrojové a cílové podmnožiny určené řezy se liší a jsou platné všechny indexy.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[řez](#slice)|Definuje podmnožinu `valarray` , který se skládá z počet prvků, které jsou stejné vzdálenosti a, která začínají na zadaný prvek.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[Velikost](#size)|Zjistí počet prvků v řez `valarray`.|
|[Spuštění](#start)|Vyhledá počáteční index řez `valarray`.|
|[STRIDE](#stride)|Najde rozdíl mezi prvky v řez `valarray`.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<valarray – >

**Namespace:** std

## <a name="size"></a>  Slice::size

Zjistí počet prvků v řezu valarray.

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

## <a name="slice"></a>  Slice::Slice

Definuje podmnožinu valarray –, který se skládá z počet prvků, které jsou stejné vzdálenosti a, která začínají na zadaný prvek.

```cpp
slice();

slice(
    size_t _StartIndex,
    size_t _Len,
    size_t stride);
```

### <a name="parameters"></a>Parametry

*_StartIndex*<br/>
Valarray – index prvního prvku v podmnožině rozhraní.

*_Len*<br/>
Počet prvků v podmnožině rozhraní.

*STRIDE*<br/>
Vzdálenost mezi prvky v podmnožině rozhraní.

### <a name="return-value"></a>Návratová hodnota

Výchozí konstruktor ukládá nulami pro počáteční index, celková délka a stride. Druhý konstruktor ukládá *_StartIndex* pro počáteční index *_Len* celkové délky a *stride* pro stride.

### <a name="remarks"></a>Poznámky

Stride může být záporná.

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

## <a name="start"></a>  Slice::Start

Počáteční index řezu valarray najde.

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

## <a name="stride"></a>  Slice::STRIDE

Vyhledá vzdálenost mezi prvky v řezu valarray.

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

## <a name="see-also"></a>Viz také:

[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
