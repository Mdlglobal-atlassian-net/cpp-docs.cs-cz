---
title: gslice – třída
ms.date: 11/04/2016
f1_keywords:
- valarray/std::gslice
- valarray/std::gslice::size
- valarray/std::gslice::start
- valarray/std::gslice::stride
helpviewer_keywords:
- std::gslice [C++]
- std::gslice [C++], size
- std::gslice [C++], start
- std::gslice [C++], stride
ms.assetid: f47cffd0-ea59-4b13-848b-7a5ce1d7e2a3
ms.openlocfilehash: 9290fabc86ffbdb051b7c61fe1600cd2f7f17dca
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79421735"
---
# <a name="gslice-class"></a>gslice – třída

Třída nástrojů pro valarray, která se používá k definování multidimenzionálních podmnožin valarray. Pokud je valarray považována za multidimenzionální matici se všemi prvky v poli, pak řez vyextrahuje vektor z multidimenzionálního pole.

## <a name="remarks"></a>Poznámky

Třída ukládá parametry, které charakterizují objekt typu [gslice_array](../standard-library/gslice-array-class.md). Podmnožina valarray je nepřímo vytvořena, když se objekt třídy gslice zobrazí jako argument pro objekt třídy [valarray](../standard-library/valarray-class.md#op_at) **\<typ >** . Uložené hodnoty, které určují podmnožinu vybrané z nadřazené valarray, zahrnují:

- Počáteční index.

- Délka vektoru třídy `valarray<size_t>`.

- Vektor pro Rozteč třídy `valarray<size_t>`.

Dva vektory musí mít stejnou délku.

Pokud je sada definovaná pomocí gslice podmnožinou konstanty valarray, pak je gslice novým valarray. Pokud je sada definovaná pomocí gslice podmnožinou nekonstantního valarrayu, pak má gslice odkaz na původní valarray. Mechanismus vyhodnocení pro nekonstantní valarrays šetří čas a paměť.

Operace na valarrays jsou zaručeny pouze v případě, že zdrojové a cílové podmnožiny, které jsou definovány v gslices, jsou jedinečné a všechny indexy jsou platné.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[gslice](#gslice)|Definuje podmnožinu `valarray`, která se skládá z více řezů `valarray`, které všechny začínají na určeném prvku.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[hodnota](#size)|Vyhledá hodnoty pole určující počet prvků v obecné výseči `valarray`.|
|[start](#start)|Najde počáteční index obecného řezu `valarray`.|
|[mezer](#stride)|Najde vzdálenost mezi prvky v obecném řezu `valarray`.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<valarray >

**Obor názvů:** std

## <a name="gslice"></a>gslice:: gslice

Třída nástrojů pro valarray, která slouží k definování multidimenzionálních řezů valarray.

```cpp
gslice();

gslice(
    size_t _StartIndex,
    const valarray<size_t>& _LenArray,
    const valarray<size_t>& _IncArray);
```

### <a name="parameters"></a>Parametry

*_StartIndex*\
Index valarray prvního prvku v podmnožině.

*_LenArray*\
Pole určující počet prvků v každém řezu.

*_IncArray*\
Pole, které určuje rozteč v jednotlivých výsečích.

### <a name="return-value"></a>Návratová hodnota

Výchozí konstruktor ukládá hodnotu nula pro počáteční index a vektory s nulovou délkou pro délky a vektory mezer. Druhý konstruktor ukládá *_StartIndex* pro počáteční index, *_LenArray* pole length a *_IncArray* pro pole Rozteč.

### <a name="remarks"></a>Poznámky

**gslice** definuje podmnožinu valarray, která se skládá z více řezů valarray, které každý spustí na stejném zadaném elementu. Možnost používat pole k definování více řezů je jediným rozdílem mezi `gslice` a [řezů:: Slice](../standard-library/slice-class.md#slice). První řez má první element s indexem *_StartIndex*, počet prvků určený prvním prvkem *_LenArray*a mezerou určenou prvním prvkem *_IncArray*. Další sada kolmých řezů má první prvky, které jsou uvedeny v prvním řezu. Druhý prvek *_LenArray* určuje počet prvků. Rozteč je dána druhým prvkem *_IncArray*. Třetí rozměr řezů by převzal prvky dvojrozměrného pole jako počáteční prvky a pokračovaly obdobně.

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

## <a name="size"></a>gslice:: size

Najde hodnoty pole, které určují počet prvků v obecné výseči valarray.

```cpp
valarray<size_t> size() const;
```

### <a name="return-value"></a>Návratová hodnota

Valarray určující počet prvků v každém řezu řezu v rámci valarray.

### <a name="remarks"></a>Poznámky

Členská funkce vrací uložené délky řezů.

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

## <a name="start"></a>gslice:: Start

Najde počáteční index obecného řezu valarray.

```cpp
size_t start() const;
```

### <a name="return-value"></a>Návratová hodnota

Počáteční index celkového řezu valarray

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

## <a name="stride"></a>gslice:: rozteč

Najde vzdálenost mezi prvky v obecném řezu valarray.

```cpp
valarray<size_t> stride() const;
```

### <a name="return-value"></a>Návratová hodnota

Valarray určující vzdálenosti mezi elementy v každém řezu řezu v rámci valarray.

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

[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
