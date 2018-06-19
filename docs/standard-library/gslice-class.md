---
title: gslice – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- valarray/std::gslice
- valarray/std::gslice::size
- valarray/std::gslice::start
- valarray/std::gslice::stride
dev_langs:
- C++
helpviewer_keywords:
- std::gslice [C++]
- std::gslice [C++], size
- std::gslice [C++], start
- std::gslice [C++], stride
ms.assetid: f47cffd0-ea59-4b13-848b-7a5ce1d7e2a3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 127e1d4d39a79350dc050e1b9fb7636bce63c156
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33850623"
---
# <a name="gslice-class"></a>gslice – třída

Třída nástrojů k valarray –, který se používá k definování multidimenzionální podmnožiny valarray –. Pokud valarray – považuje za multidimenzionální matice se všechny elementy ve pole, řez extrahuje vector mimo multidimenzionálního pole.

## <a name="remarks"></a>Poznámky

Třída ukládá parametry, které charakterizovat objekt typu [gslice_array](../standard-library/gslice-array-class.md). Jakmile se zobrazí objekt gslice – třída jako argument pro objekt třídy nepřímo sestavený podmnožinu valarray – [valarray –](../standard-library/valarray-class.md#op_at)**\<typ >**. Uložené hodnoty, které zadejte do něj podmnožinu vybraný z nadřazené valarray – patří:

- Počáteční index.

- Délka vektoru třídy **valarray – < size_t >**.

- Stride vektoru třídy **valarray – < size_t >**.

Dva vektory musí mít stejnou délku.

Pokud sada definované gslice je podmnožinou konstantní valarray –, pak gslice je nové valarray –. Pokud je sada definované gslice podmnožinu nonconstant valarray –, má gslice odkaz sémantiku původní valarray –. Vyhodnocení mechanismus pro nonconstant valarray – třídy šetří čas a paměti.

Operace na valarray – třídy jsou zaručit pouze v případě, že zdrojový a cílový podmnožiny, které jsou definované gslices se liší a jsou platné všechny indexy.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[gslice –](#gslice)|Definuje podmnožinu `valarray` , se skládá z několika řezů `valarray` všechny začínají zadaný element.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[Velikost](#size)|Vyhledá hodnoty pole určení počtu prvky v obecné řezy `valarray`.|
|[Spuštění](#start)|Vyhledá počáteční index obecné řezy `valarray`.|
|[STRIDE](#stride)|Najde rozdíl mezi prvky v obecné řezy `valarray`.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<valarray – >

**Namespace:** – std

## <a name="gslice"></a>  gslice::gslice

Třída nástrojů k valarray –, který se používá k definování vícerozměrných řezy valarray –.

```cpp
gslice();

gslice(
    size_t _StartIndex,
    const valarray<size_t>& _LenArray,
    const valarray<size_t>& _IncArray);
```

### <a name="parameters"></a>Parametry

`_StartIndex` Valarray – index první prvek v podmnožině.

`_LenArray` Pole určující počet elementů v každý řez.

`_IncArray` Pole určující stride v každý řez.

### <a name="return-value"></a>Návratová hodnota

Výchozí konstruktor ukládá nula pro počáteční index a mezi vektory délku a stride vektory nulové délky. Druhý konstruktor úložiště `_StartIndex` pro počáteční index, `_LenArray` pro pole Délka a `_IncArray` stride pole.

### <a name="remarks"></a>Poznámky

**gslice** definuje podmnožinu valarray –, která se skládá z více řezů valarray – aby každý spustit v stejné zadaný element. Možnost použít pole definovat více řezů je jediným rozdílem mezi `gslice` a [slice::slice](../standard-library/slice-class.md#slice). První řez má první element s indexem `_StartIndex`, počet elementů určeného první prvek `_LenArray`a stride, poskytují první prvek `_IncArray`. Další sadu ortogonální řezy má první prvků poskytují první řez. Druhý elementu `_LenArray` určuje počet elementů. Stride je dán druhého prvku `_IncArray`. Třetí dimenze řezy by trvat prvky dvourozměrná pole jako počáteční elementy a pokračovat analogicky

### <a name="example"></a>Příklad

```cpp
// gslice_ctor.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> va ( 20 ), vaResult;
   for ( i = 0 ; i < 20 ; i+=1 )
      va [ i ] =  i;

   cout << "The operand valarray va is:" << endl << "(";
   for ( i = 0 ; i < 20 ; i++ )
      cout << " " << va [ i ];
   cout << " )" << endl;

   valarray<size_t> Len ( 2 ), Stride ( 2 );
   Len [0] = 4;
   Len [1] = 4;
   Stride [0] = 7;
   Stride [1] = 4;

   gslice vaGSlice ( 0, Len, Stride );
   vaResult = va [ vaGSlice ];

   cout << "The valarray for vaGSlice is vaResult:" << endl
        << "va[vaGSlice] = (";

   for ( i = 0 ; i < 8 ; i++ )
      cout << " " << vaResult [ i ];
   cout << ")" << endl;
}
```

```Output
The operand valarray va is:
( 0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 )
The valarray for vaGSlice is vaResult:
va[vaGSlice] = ( 0 4 8 12 7 11 15 19)
```

## <a name="size"></a>  gslice::size

Vyhledá určení počtu prvky v obecné řezy valarray – hodnoty pole.

```cpp
valarray<size_t> size() const;
```

### <a name="return-value"></a>Návratová hodnota

Valarray – určení počet elementů v každý řez obecné řezy valarray –.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí uložené délek řezy.

### <a name="example"></a>Příklad

```cpp
// gslice_size.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;
   size_t sizeVA;

   valarray<int> va ( 20 ), vaResult;
   for ( i = 0 ; i < 20 ; i+=1 )
      va [ i ] =  i;

   cout << "The operand valarray va is:\n ( ";
      for ( i = 0 ; i < 20 ; i++ )
         cout << va [ i ] << " ";
   cout << ")." << endl;

   sizeVA = va.size ( );
   cout << "The size of the valarray is: "
        << sizeVA << "." << endl << endl;

   valarray<size_t> Len ( 2 ), Stride ( 2 );
   Len [0] = 4;
   Len [1] = 4;
   Stride [0] = 7;
   Stride [1] = 4;

   gslice vaGSlice ( 0, Len, Stride );
   vaResult = va [ vaGSlice ];
   const valarray <size_t> sizeGS = vaGSlice.size ( );

   cout << "The valarray for vaGSlice is vaResult:"
        << "\n va[vaGSlice] = ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaResult [ i ] << " ";
   cout << ")." << endl;

   cout << "The size of vaResult is:"
        << "\n vaGSlice.size ( ) = ( ";
      for ( i = 0 ; i < 2 ; i++ )
         cout << sizeGS[ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The operand valarray va is:
 ( 0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 ).
The size of the valarray is: 20.

The valarray for vaGSlice is vaResult:
 va[vaGSlice] = ( 0 4 8 12 7 11 15 19 ).
The size of vaResult is:
 vaGSlice.size ( ) = ( 4 4 ).
```

## <a name="start"></a>  gslice::Start

Vyhledá počáteční index obecné řezy valarray –.

```cpp
size_t start() const;
```

### <a name="return-value"></a>Návratová hodnota

Počáteční index obecné řezy valarray –.

### <a name="example"></a>Příklad

```cpp
// gslice_start.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> va ( 20 ), vaResult;
   for (i = 0 ; i < 20 ; i+=1 )
      va [ i ] =  i;

   cout << "The operand valarray va is:\n ( ";
      for ( i = 0 ; i < 20 ; i++ )
         cout << va [ i ] << " ";
   cout << ")." << endl;

   valarray<size_t> Len ( 2 ), Stride ( 2 );
   Len [0] = 4;
   Len [1] = 4;
   Stride [0] = 7;
   Stride [1] = 4;

   gslice vaGSlice ( 0, Len, Stride );
   vaResult = va [ vaGSlice ];
   size_t vaGSstart = vaGSlice.start ( );

   cout << "The valarray for vaGSlice is vaResult:"
        << "\n va[vaGSlice] = ( ";
      for (i = 0 ; i < 8 ; i++ )
         cout << vaResult [ i ] << " ";
   cout << ")." << endl;

   cout << "The index of the first element of vaResult is: "
        << vaGSstart << "." << endl;
}
```

```Output
The operand valarray va is:
 ( 0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 ).
The valarray for vaGSlice is vaResult:
 va[vaGSlice] = ( 0 4 8 12 7 11 15 19 ).
The index of the first element of vaResult is: 0.
```

## <a name="stride"></a>  gslice::STRIDE

Najde rozdíl mezi prvky v obecné řezy valarray –.

```cpp
valarray<size_t> stride() const;
```

### <a name="return-value"></a>Návratová hodnota

Valarray – zadání vzdálenosti mezi elementy v každý řez obecné řezy valarray –.

### <a name="example"></a>Příklad

```cpp
// gslice_stride.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> va ( 20 ), vaResult;
   for (i = 0 ; i < 20 ; i+=1 )
      va [ i ] =  i;

   cout << "The operand valarray va is:\n ( ";
      for (i = 0 ; i < 20 ; i++ )
         cout << va [ i ] << " ";
   cout << ")." << endl;

   valarray<size_t> Len ( 2 ), Stride ( 2 );
   Len [0] = 4;
   Len [1] = 4;
   Stride [0] = 7;
   Stride [1] = 4;

   gslice vaGSlice ( 0, Len, Stride );
   vaResult = va [ vaGSlice ];
   const valarray <size_t> strideGS = vaGSlice.stride ( );

   cout << "The valarray for vaGSlice is vaResult:"
        << "\n va[vaGSlice] = ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaResult [ i ] << " ";
   cout << ")." << endl;

   cout << "The strides of vaResult are:"
        << "\n vaGSlice.stride ( ) = ( ";
      for ( i = 0 ; i < 2 ; i++ )
         cout << strideGS[ i ] << " ";
   cout << ")." << endl;

}
```

```Output
The operand valarray va is:
 ( 0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 ).
The valarray for vaGSlice is vaResult:
 va[vaGSlice] = ( 0 4 8 12 7 11 15 19 ).
The strides of vaResult are:
 vaGSlice.stride ( ) = ( 7 4 ).
```

## <a name="see-also"></a>Viz také

[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
