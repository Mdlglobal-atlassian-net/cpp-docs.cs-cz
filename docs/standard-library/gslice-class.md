---
title: gslice – třída | Dokumentace Microsoftu
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
ms.openlocfilehash: c5c47f91a3e029175d40bd1a762fb6e6ff527ee7
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38955811"
---
# <a name="gslice-class"></a>gslice – třída

Třídy nástrojů pro valarray –, který se používá k definování multidimenzionální podmnožiny valarray. Pokud valarray se považuje za multidimenzionální matice s všechny elementy v matici, řez extrahuje vektor z multidimenzionálního pole.

## <a name="remarks"></a>Poznámky

Třída obsahuje parametry, které charakterizují objekt typu [gslice_array –](../standard-library/gslice-array-class.md). Dílčí sadu valarray zkonstruování nepřímo když objekt gslice – třída se objeví jako argument pro objekt třídy [valarray](../standard-library/valarray-class.md#op_at)**\<typ >**. Uložené hodnoty, které určují dílčí vybrat z nadřazené valarray patří:

- Počáteční index.

- Délka vektoru třídy `valarray<size_t>`.

- Vektor stride třídy `valarray<size_t>`.

Dva vektory musí mít stejnou délku.

Pokud množiny definované gslice – je podmnožinou konstantní valarray, gslice – je nová valarray. Pokud množiny definované gslice – je podmnožinou nekonstantním valarray, gslice – má sémantiku odkazu pro původní valarray. Vyhodnocení mechanismus pro nekonstantním valarrays šetří čas a paměti.

Operace s valarrays zaručeno pouze v případě, že zdrojové a cílové podmnožiny určené gslices se liší a jsou platné všechny indexy.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[gslice –](#gslice)|Definuje podmnožinu `valarray` , který se skládá z více částí `valarray` všechny začínají na zadaný prvek.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[Velikost](#size)|Vyhledá pole hodnoty určující počet prvků v obecné řezu `valarray`.|
|[Spuštění](#start)|Vyhledá počáteční index obecné řezu `valarray`.|
|[STRIDE](#stride)|Vyhledá vzdálenost mezi prvky v obecné řezu `valarray`.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<valarray – >

**Namespace:** std

## <a name="gslice"></a>  gslice::gslice

Třídy nástrojů pro valarray –, který se používá k definování multidimenzionální řezů valarray.

```cpp
gslice();

gslice(
    size_t _StartIndex,
    const valarray<size_t>& _LenArray,
    const valarray<size_t>& _IncArray);
```

### <a name="parameters"></a>Parametry

*_StartIndex* valarray index prvního prvku v podmnožině rozhraní.

*_LenArray* pole určující počet prvků v každém řezu.

*_IncArray* pole zadáte stride v každém řezu.

### <a name="return-value"></a>Návratová hodnota

Výchozí konstruktor ukládá nulu pro počáteční index a vektory nulové délky pro délku a stride vektory. Druhý konstruktor ukládá *_StartIndex* pro počáteční index *_LenArray* pro pole délky a *_IncArray* stride pole.

### <a name="remarks"></a>Poznámky

**gslice –** definuje podmnožinu valarray –, který se skládá z více částí valarray, že každý začínají na stejné zadaný element. Možnost používat pole k definování více řezů je jediným rozdílem mezi `gslice` a [slice::slice](../standard-library/slice-class.md#slice). První řez je první prvek s indexem *_StartIndex*, počet elementů určené na první prvek *_LenArray*a stride Dal první prvek *_IncArray* . Další sadu ortogonální řezy má první prvků Dal první řez. Druhý prvek *_LenArray* určuje počet prvků. Stride je dán druhý prvek *_IncArray*. Třetí rozměr řezů by trvat prvky dvourozměrné pole jako počáteční elementy a pokračovat analogicky

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

Vyhledá zadání počtu elementů v obecné řezu valarray hodnoty pole.

```cpp
valarray<size_t> size() const;
```

### <a name="return-value"></a>Návratová hodnota

Valarray – zadání počtu elementů v každém řezu obecné řezu valarray.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí uložený délky řezy.

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

Počáteční index obecné řezu valarray najde.

```cpp
size_t start() const;
```

### <a name="return-value"></a>Návratová hodnota

Počáteční index obecné řezu valarray.

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

Vyhledá vzdálenost mezi prvky v obecné řezu valarray.

```cpp
valarray<size_t> stride() const;
```

### <a name="return-value"></a>Návratová hodnota

Valarray – určení vzdálenosti mezi prvky v obecné řezu valarray každý řez.

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

## <a name="see-also"></a>Viz také:

[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
