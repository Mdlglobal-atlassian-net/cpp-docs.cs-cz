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
ms.openlocfilehash: 07c987fb08a213bb66da628bec3021a3bf9ba24a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370622"
---
# <a name="gslice-class"></a>gslice – třída

Třída nástroje valarray, která se používá k definování vícerozměrných podmnožiny valarray. Pokud je valarray považován za vícerozměrnou matici se všemi prvky v poli, pak řez extrahuje vektor z vícerozměrného pole.

## <a name="remarks"></a>Poznámky

Třída ukládá parametry, které charakterizují objekt typu [gslice_array](../standard-library/gslice-array-class.md). Podmnožina valarray je nepřímo vytvořena, když se objekt gslice třídy zobrazí jako argument pro objekt třídy [valarray](../standard-library/valarray-class.md#op_at)**\<Type>**. Uložené hodnoty, které určují podmnožinu vybranou z nadřazeného pole valarray, zahrnují:

- Počáteční index.

- Délka vektortřídy `valarray<size_t>`.

- Vektor kroku třídy `valarray<size_t>`.

Dva vektory musí mít stejnou délku.

Pokud je množina definovaná gslice podmnožinou konstantního valarray, pak je gslice novým valarrayem. Pokud je množina definovaná gslice podmnožinou nestálého valarray, pak má gslice referenční sémantiku na původní valarray. Mechanismus vyhodnocení pro nekonstantní valarrays šetří čas a paměť.

Operace na valarrays jsou zaručeny pouze v případě, že zdrojové a cílové podmnožiny definované gslice jsou odlišné a všechny indexy jsou platné.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[gslice](#gslice)|Definuje podmnožinu, `valarray` která se skládá z `valarray` více řezů, které všechny začínají na zadaném prvku.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[Velikost](#size)|Najde hodnoty pole určující počet prvků v obecném `valarray`řezu .|
|[Spustit](#start)|Vyhledá počáteční index obecného řezu `valarray`.|
|[Krok](#stride)|Vyhledá vzdálenost mezi prvky v `valarray`obecném řezu .|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<valarray>

**Obor názvů:** std

## <a name="gslicegslice"></a><a name="gslice"></a>gslice::gslice

Třída nástroje valarray, která se používá k definování vícerozměrných řezů valarray.

```cpp
gslice();

gslice(
    size_t _StartIndex,
    const valarray<size_t>& _LenArray,
    const valarray<size_t>& _IncArray);
```

### <a name="parameters"></a>Parametry

*_StartIndex*\
Index valarray prvního prvku v podsadě.

*_LenArray*\
Pole určující počet prvků v každém řezu.

*_IncArray*\
Pole určující krok v každém řezu.

### <a name="return-value"></a>Návratová hodnota

Výchozí konstruktor ukládá nulu pro počáteční index a vektory nulové délky pro vektory délky a kroku. Druhý konstruktor ukládá *_StartIndex* pro počáteční index, *_LenArray* pro pole length a *_IncArray* pro pole kroku.

### <a name="remarks"></a>Poznámky

**gslice** definuje podmnožinu valarray, která se skládá z více řezů valarray, které každý začíná na stejném zadaném prvku. Možnost použití polí k definování více řezů je `gslice` jediným rozdílem mezi [řezem::slice](../standard-library/slice-class.md#slice). První řez má první prvek s indexem *_StartIndex*, počet prvků určených prvním prvkem *_LenArray*a krok daný prvním prvkem *_IncArray*. Další sada ortogoňálních řezů má první prvky dané prvním řezem. Druhý prvek *_LenArray* určuje počet prvků. Krok je dán druhým prvkem *_IncArray*. Třetí rozměr řezů by vzal prvky dvojrozměrného pole jako počáteční prvky a postupoval analogicky

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

## <a name="gslicesize"></a><a name="size"></a>gslice::velikost

Najde hodnoty pole určující počet prvků v obecném řezu valarray.

```cpp
valarray<size_t> size() const;
```

### <a name="return-value"></a>Návratová hodnota

Valarray určující počet prvků v každém řezu obecného řezu valarray.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí uložené délky řezů.

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

## <a name="gslicestart"></a><a name="start"></a>gslice::start

Najde počáteční index obecného řezu valarray.

```cpp
size_t start() const;
```

### <a name="return-value"></a>Návratová hodnota

Počáteční index obecné ho rescence pole.

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

## <a name="gslicestride"></a><a name="stride"></a>gslice::krok

Vyhledá vzdálenost mezi prvky v obecném řezu valarray.

```cpp
valarray<size_t> stride() const;
```

### <a name="return-value"></a>Návratová hodnota

Valarray určující vzdálenosti mezi prvky v každém řezu obecného řezu valarray.

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
