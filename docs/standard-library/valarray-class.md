---
title: valarray – třída
ms.date: 03/27/2019
f1_keywords:
- valarray/std::valarray
- valarray/std::valarray::value_type
- valarray/std::valarray::apply
- valarray/std::valarray::cshift
- valarray/std::valarray::free
- valarray/std::valarray::max
- valarray/std::valarray::min
- valarray/std::valarray::resize
- valarray/std::valarray::shift
- valarray/std::valarray::size
- valarray/std::valarray::sum
- valarray/std::valarray::swap
helpviewer_keywords:
- std::valarray [C++]
- std::valarray [C++], value_type
- std::valarray [C++], apply
- std::valarray [C++], cshift
- std::valarray [C++], free
- std::valarray [C++], max
- std::valarray [C++], min
- std::valarray [C++], resize
- std::valarray [C++], shift
- std::valarray [C++], size
- std::valarray [C++], sum
- std::valarray [C++], swap
ms.assetid: 19b862f9-5d09-4003-8844-6ddd02c1a3a7
ms.openlocfilehash: f116758591461614acfa7c171bff2b1675f453e4
ms.sourcegitcommit: 49cf365176557456f56c994e06ea1a38f73e938b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2020
ms.locfileid: "78937418"
---
# <a name="valarray-class"></a>valarray – třída

Šablona třídy popisuje objekt, který řídí sekvenci prvků typu `Type`, které jsou uloženy jako pole, navržené pro provádění vysokorychlostních matematických operací a optimalizované pro výpočetní výkon.

## <a name="remarks"></a>Poznámky

Třída je reprezentace matematického konceptu seřazené sady hodnot a prvky jsou číslovány sekvenčně od nuly. Třída je popsána jako poblíž kontejneru, protože podporuje některé, ale ne všechny funkce, které mají první třída kontejnery sekvence, jako je například [Vector](../standard-library/vector-class.md), podpora. Liší se od vektoru šablony třídy dvěma důležitými způsoby:

- Definuje mnoho aritmetických operací mezi odpovídajícími prvky `valarray<Type>` objekty stejného typu a délky, například *xarr* = cos ( *Yarr*) + sin ( *Zarr*).

- Definuje celou řadu zajímavých způsobů, jak podskriptovat `valarray<Type>` objekt, pomocí [operátoru&#91;](#op_at)přetížení.

Objekt třídy `Type`:

- Má veřejný výchozí konstruktor, destruktor, kopírovací konstruktor a operátor přiřazení s konvenčním chováním.

- Definuje aritmetické operátory a matematické funkce podle potřeby, které jsou definovány pro typy s plovoucí desetinnou čárkou s konvenčním chováním.

Zejména, mezi konstrukcí kopírování a výchozím konstrukcí, které následují přiřazení, nesmí existovat žádné drobné rozdíly. Žádná operace s objekty třídy `Type` nemůže vyvolat výjimky.

## <a name="members"></a>Členové

### <a name="constructors"></a>Konstruktory

|||
|-|-|
|[valarray](#valarray)|Sestaví `valarray` konkrétní velikosti nebo pomocí prvků konkrétní hodnoty nebo jako kopie jiného `valarray` nebo podmnožiny jiného `valarray`.|

### <a name="typedefs"></a>Typedefs

|||
|-|-|
|[value_type](#value_type)|Typ, který představuje typ elementu uložený ve `valarray`.|

### <a name="functions"></a>Functions

|||
|-|-|
|[vyrovnat](#apply)|Aplikuje zadanou funkci na každý prvek `valarray`.|
|[cshift](#cshift)|Cyklicky posouvá všechny prvky v `valarray` o zadaný počet pozic.|
|[free](#free)|Uvolňuje paměť využívané `valarray`.|
|[počet](#max)|Najde největší prvek v `valarray`.|
|[dlouhé](#min)|Najde nejmenší prvek v `valarray`.|
|[velikost](#resize)|Změní počet prvků v `valarray` na zadané číslo, přidání nebo odebrání prvků podle potřeby.|
|[posouvá](#shift)|Posune všechny prvky v `valarray` o zadaný počet pozic.|
|[hodnota](#size)|Najde počet prvků v `valarray`.|
|[zapůjčen](#sum)|Určuje součet všech prvků v `valarray` nenulové délky.|
|[adresu](#swap)||

### <a name="operators"></a>Operátory

|||
|-|-|
|[podnikatel!](#op_not)|Unární operátor, který získá logické `NOT` hodnoty každého prvku v `valarray`.|
|[% = – operátor](#op_mod_eq)|Získá zbytek dělení na prvky pole, které jsou ovlivněny buď zadaným `valarray`, nebo hodnotou typu prvku.|
|[operátor & =](#op_and_eq)|Získá bitové `AND` prvků v poli buď pomocí odpovídajících prvků v zadaném `valarray` nebo s hodnotou typu prvku.|
|[operátor > > =](#op_gt_gt_eq)|Posune pravou část bitů pro každý prvek `valarray` operandu za zadaný počet pozic nebo podle prvku, který je určený druhým `valarray`.|
|[operátor < < =](#op_lt_lt_eq)|Posune doleva pro každý prvek `valarray` operandu o zadaný počet pozic nebo o hodnotu v prvku, kterou určuje druhý `valarray`.|
|[operator * = – operátor](#op_star_eq)|Vynásobí prvky zadaného `valarray` nebo hodnotu typu prvku, přítyp prvku, k operandu `valarray`.|
|[operator + – operátor](#op_add)|Unární operátor, který používá znaménko plus pro každý prvek v `valarray`.|
|[operator + = – operátor](#op_add_eq)|Přidá prvky zadaného `valarray` nebo hodnotu typu prvku, vhodné prvku, do operandu `valarray`.|
|[podnikatel](#operator-)|Unární operátor, který u každého prvku v `valarray`aplikuje mínus.|
|[-= – operátor](#operator-_eq)|Odečte prvky zadaného `valarray` nebo hodnotu typu prvku, z prvku, z operandu `valarray`.|
|[operator/= – operátor](#op_div_eq)|Vydělí operand `valarray` elementu, který je ovlivněn prvky zadaného `valarray` nebo hodnotou typu prvku.|
|[operátor =](#op_eq)|Přiřadí prvky `valarray`, jejichž hodnoty jsou zadány přímo nebo jako součást nějakého jiného `valarray` nebo `slice_array`, `gslice_array`, `mask_array`nebo `indirect_array`.|
|[podnikatel&#91;&#93;](#op_at)|Vrátí odkaz na element nebo jeho hodnotu v zadaném indexu nebo v zadané podmnožině.|
|[operátor ^ =](#op_xor_eq)|Získá výhradní logický operátor OR (`XOR`) pole s buď zadaným valarray nebo hodnotou typu prvku.|
|[operátor&#124;=](#op_or_eq)|Získá bitové `OR` prvků v poli buď pomocí odpovídajících prvků v zadaném `valarray` nebo s hodnotou typu prvku.|
|[~ – operátor](#op_dtor)|Unární operátor, který získá bitové `NOT` hodnoty každého prvku v `valarray`.|

## <a name="apply"></a>vyrovnat

Aplikuje zadanou funkci na každý prvek valarray.

```cpp
valarray<Type> apply(Type _Func(Type)) const;

valarray<Type> apply(Type _Func(constType&)) const;
```

### <a name="parameters"></a>Parametry

*_Func (typ)* \
Objekt funkce, který se má použít u každého prvku operandu valarray.

*_Func (typ const &)* \
Objekt funkce pro typ const, který má být použit pro každý prvek operandu valarray.

### <a name="return-value"></a>Návratová hodnota

Valarray, jehož prvky měly `_Func` aplikovaný na prvky valarray operandu.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí objekt třídy [valarray](../standard-library/valarray-class.md) **\<typ >** [, jehož délka je](#size), každý z *jehož prvků je* `_Func((*this)[I])`.

### <a name="example"></a>Příklad

```cpp
// valarray_apply.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

using namespace std;

int __cdecl MyApplyFunc( int n )
{
   return n*2;
}

int main( int argc, char* argv[] )
{
   valarray<int> vaR(10), vaApplied(10);
   int i;

   for ( i = 0; i < 10; i += 3 )
      vaR[i] = i;

   for ( i = 1; i < 10; i += 3 )
      vaR[i] = 0;

   for ( i = 2; i < 10; i += 3 )
      vaR[i] = -i;

   cout << "The initial Right valarray is: (";
   for   ( i=0; i < 10; ++i )
      cout << " " << vaR[i];
   cout << " )" << endl;

   vaApplied = vaR.apply( MyApplyFunc );

   cout << "The element-by-element result of "
       << "applying MyApplyFunc to vaR is the\nvalarray: ( ";
   for ( i = 0; i < 10; ++i )
      cout << " " << vaApplied[i];
   cout << " )" << endl;
}
```

```Output
The initial Right valarray is: ( 0 0 -2 3 0 -5 6 0 -8 9 )
The element-by-element result of applying MyApplyFunc to vaR is the
valarray: (  0 0 -4 6 0 -10 12 0 -16 18 )
```

## <a name="cshift"></a>cshift

Cyklicky posouvá všechny prvky v valarray o zadaný počet pozic.

```cpp
valarray<Type> cshift(int count) const;
```

### <a name="parameters"></a>Parametry

*počet*\
Počet míst, po který mají být prvky posunuty.

### <a name="return-value"></a>Návratová hodnota

Nový valarray, ve kterém byly všechny *prvky přesunuty* , cyklicky směrem k začátku valarray, v závislosti na jejich pozicích v valarray operandu.

### <a name="remarks"></a>Poznámky

Kladná hodnota *Count* posune elementy v *počtu* zbývajících míst doleva.

Záporná hodnota *Count* posune prvky cyklicky vpravo na *počtu* míst.

### <a name="example"></a>Příklad

```cpp
// valarray_cshift.cpp
// compile with: /EHsc

#include <valarray>
#include <iostream>

int main()
{
    using namespace std;
    int i;

    valarray<int> va1(10), va2(10);
    for (i = 0; i < 10; i+=1)
        va1[i] = i;
    for (i = 0; i < 10; i+=1)
        va2[i] = 10 - i;

    cout << "The operand valarray va1 is: (";
    for (i = 0; i < 10; i++)
        cout << " " << va1[i];
    cout << ")" << endl;

    // A positive parameter shifts elements right
    va1 = va1.cshift(4);
    cout << "The cyclically shifted valarray va1 is:\nva1.cshift (4) = (";
    for (i = 0; i < 10; i++)
        cout << " " << va1[i];
    cout << ")" << endl;

    cout << "The operand valarray va2 is: (";
    for (i = 0; i < 10; i++)
        cout << " " << va2[i];
    cout << ")" << endl;

    // A negative parameter shifts elements left
    va2 = va2.cshift(-4);
    cout << "The cyclically shifted valarray va2 is:\nva2.shift (-4) = (";
    for (i = 0; i < 10; i++)
        cout << " " << va2[i];
    cout << ")" << endl;
}
```

```Output
The operand valarray va1 is: ( 0 1 2 3 4 5 6 7 8 9)
The cyclically shifted valarray va1 is:
va1.cshift (4) = ( 4 5 6 7 8 9 0 1 2 3)
The operand valarray va2 is: ( 10 9 8 7 6 5 4 3 2 1)
The cyclically shifted valarray va2 is:
va2.shift (-4) = ( 4 3 2 1 10 9 8 7 6 5)
```

## <a name="free"></a>dost

Uvolňuje paměť, kterou používá valarray.

```cpp
void free();
```

### <a name="remarks"></a>Poznámky

Tato nestandardní funkce je shodná s přiřazením prázdného valarray. Příklad:

```cpp
valarray<T> v;
v = valarray<T>();

// equivalent to v.free()
```

## <a name="max"></a>počet

Najde největší prvek v valarray.

```cpp
Type max() const;
```

### <a name="return-value"></a>Návratová hodnota

Maximální hodnota prvků v operandu valarray.

### <a name="remarks"></a>Poznámky

Členská funkce porovnává hodnoty pomocí **operátoru\<** nebo **operátoru >** mezi páry prvků třídy `Type`, pro které musí být pro prvek `Type`k dispozici operátory.

### <a name="example"></a>Příklad

```cpp
// valarray_max.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i, MaxValue;

   valarray<int> vaR ( 10 );
   for ( i = 0 ; i < 10 ; i += 3 )
      vaR [ i ] =  i;
   for ( i = 1 ; i < 10 ; i += 3 )
      vaR [ i ] =  2*i - 1;
   for ( i = 2 ; i < 10 ; i += 3 )
      vaR [ i ] =  10 - i;

   cout << "The operand valarray is: ( ";
      for (i = 0 ; i < 10 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   MaxValue = vaR.max (  );
   cout << "The largest element in the valarray is: "
        << MaxValue  << "." << endl;
}
```

```Output
The operand valarray is: ( 0 1 8 3 7 5 6 13 2 9 ).
The largest element in the valarray is: 13.
```

## <a name="min"></a>dlouhé

Najde nejmenší prvek v valarray.

```cpp
Type min() const;
```

### <a name="return-value"></a>Návratová hodnota

Minimální hodnota prvků v operandu valarray.

### <a name="remarks"></a>Poznámky

Členská funkce porovnává hodnoty pomocí **operátoru\<** nebo **operátoru >** mezi páry prvků třídy `Type`, pro které musí být pro prvek `Type`k dispozici operátory.

### <a name="example"></a>Příklad

```cpp
// valarray_min.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i, MinValue;

   valarray<int> vaR ( 10 );
   for ( i = 0 ; i < 10 ; i += 3 )
      vaR [ i ] =  -i;
   for ( i = 1 ; i < 10 ; i += 3 )
      vaR [ i ] =  2*i;
   for ( i = 2 ; i < 10 ; i += 3 )
      vaR [ i ] =  5 - i;

   cout << "The operand valarray is: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   MinValue = vaR.min ( );
   cout << "The smallest element in the valarray is: "
        << MinValue  << "." << endl;
}
/* Output:
The operand valarray is: ( 0 2 3 -3 8 0 -6 14 -3 -9 ).
The smallest element in the valarray is: -9.
*/
```

## <a name="op_not"></a>podnikatel!

Unární operátor, který získá logické hodnoty **Not** pro každý prvek v valarray.

```cpp
valarray<bool> operator!() const;
```

### <a name="return-value"></a>Návratová hodnota

Valarray logických hodnot, které jsou negací hodnot prvků valarray operandu.

### <a name="remarks"></a>Poznámky

Logická **operace** nenegace elementů, protože převede všechny nuly na hodnoty a bere v úvahu všechny nenulové hodnoty jako ty a převede je na nuly. Vrácený valarray logických hodnot má stejnou velikost jako operand valarray.

K dispozici je také bitový operátor **Not**[valarray:: operator ~](#op_dtor) , který se negací úrovně jednotlivých bitů v rámci binární reprezentace prvků **char** a **int** prvku valarray.

### <a name="example"></a>Příklad

```cpp
// valarray_op_lognot.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 10 );
   valarray<bool> vaNOT ( 10 );
   for ( i = 0 ; i < 10 ; i += 2 )
      vaL [ i ] =  0;
   for ( i = 1 ; i < 10 ; i += 2 )
      vaL [ i ] =  i-1;

   cout << "The initial valarray is:  ( ";
      for (i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   vaNOT = !vaL;
   cout << "The element-by-element result of "
        << "the logical NOT operator! is the"
        << endl << "valarray: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaNOT [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial valarray is:  ( 0 0 0 2 0 4 0 6 0 8 ).
The element-by-element result of the logical NOT operator! is the
valarray: ( 1 1 1 0 1 0 1 0 1 0 ).
```

## <a name="op_mod_eq"></a>% = – operátor

Získá zbytek dělení na prvky pole, které jsou ovlivněny buď zadaným valarray, nebo hodnotou typu prvku.

```cpp
valarray<Type>& operator%=(const valarray<Type>& right);

valarray<Type>& operator%=(const Type& right);
```

### <a name="parameters"></a>Parametry

*pravé*\
Valarray nebo hodnota typu prvku se shoduje s hodnotou valarray operandu, která má být rozdělena, přechází na prvek, operand valarray.

### <a name="return-value"></a>Návratová hodnota

Valarray, jehož prvky jsou zbytkem z prvku, který je v rámci operandu valarray, *vpravo*

### <a name="example"></a>Příklad

```cpp
// valarray_class_op_rem.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 6 ), vaR ( 6 );
   for ( i = 0 ; i < 6 ; i += 2 )
      vaL [ i ] =  53;
   for ( i = 1 ; i < 6 ; i += 2 )
      vaL [ i ] =  -67;
   for ( i = 0 ; i < 6 ; i++ )
      vaR [ i ] =  3*i+1;

   cout << "The initial valarray is: ( ";
      for ( i = 0 ; i < 6 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial  right valarray is: ( ";
      for ( i = 0 ; i < 6 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaL %= vaR;
   cout << "The remainders from the element-by-element "
        << "division is the"
        << endl << "valarray: ( ";
      for ( i = 0 ; i < 6 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial valarray is: ( 53 -67 53 -67 53 -67 ).
The initial  right valarray is: ( 1 4 7 10 13 16 ).
The remainders from the element-by-element division is the
valarray: ( 0 -3 4 -7 1 -3 ).
```

## <a name="op_and_eq"></a>operátor&amp;=

Získá bitové **a** prvky v poli buď s odpovídajícími prvky v zadaném valarray nebo s hodnotou typu prvku.

```cpp
valarray<Type>& operator&=(const valarray<Type>& right);

valarray<Type>& operator&=(const Type& right);
```

### <a name="parameters"></a>Parametry

*pravé*\
Valarray nebo hodnota typu prvku se shoduje s typem operandu valarray, který má být kombinován, což je prvek ovlivněn logickým `AND` s operandem valarray.

### <a name="return-value"></a>Návratová hodnota

Valarray, jehož prvky jsou `AND` logického prvku valarray operandu na základě *pravého*

### <a name="remarks"></a>Poznámky

Bitová operace se dá použít jenom k manipulaci s bity v datových typech **char** a **int** a variantách, ne na **float**, **Double**, **longdouble**, **void**, **bool**nebo jiném, složitějších datových typech.

Bitový operátor a má stejnou tabulku pravdy jako logický `AND`, ale vztahuje se na datový typ na úrovni jednotlivých bitů. Vzhledem k počtu bitů *b*1 a *b*2, *b*1 `AND` *b*2 je **true** , pokud jsou obě bity pravdivé; **false** , pokud alespoň jedna má hodnotu false.

### <a name="example"></a>Příklad

```cpp
// valarray_class_op_bitand.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 10 ), vaR ( 10 );
   for ( i = 0 ; i < 10 ; i += 2 )
      vaL [ i ] =  0;
   for ( i = 1 ; i < 10 ; i += 2 )
      vaL [ i ] =  i-1;
   for ( i = 0 ; i < 10 ; i++ )
      vaR [ i ] =  i;

   cout << "The initial valarray is:  ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaL &= vaR;
   cout << "The element-by-element result of "
        << "the logical AND operator&= is the"
        << endl << "valarray: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial valarray is:  ( 0 0 0 2 0 4 0 6 0 8 ).
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 8 9 ).
The element-by-element result of the logical AND operator&= is the
valarray: ( 0 0 0 2 0 4 0 6 0 8 ).
```

## <a name="op_gt_gt_eq"></a>operátor&gt;&gt;=

Posune pravou hodnotu bitů pro každý prvek valarray operandu za zadaný počet pozic nebo podle prvku, který je určený druhým valarray.

```cpp
valarray<Type>& operator>>=(const valarray<Type>& right);

valarray<Type>& operator>>=(const Type& right);
```

### <a name="parameters"></a>Parametry

*pravé*\
Hodnota, která označuje množství pravého posunutí nebo valarray, jehož prvky ukazují množství správného posunu posunutého prvku.

### <a name="return-value"></a>Návratová hodnota

Valarray, jehož prvky byly posunuty vpravo o zadanou hodnotu *vpravo.*

### <a name="remarks"></a>Poznámky

Podepsaná čísla mají zachována znaménka.

### <a name="example"></a>Příklad

```cpp
// valarray_class_op_rs.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 8 ), vaR ( 8 );
   for ( i = 0 ; i < 8 ; i += 2 )
      vaL [ i ] =  64;
   for ( i = 1 ; i < 8 ; i += 2 )
      vaL [ i ] =  -64;
   for ( i = 0 ; i < 8 ; i++ )
      vaR [ i ] =  i;

   cout << "The initial operand valarray is: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The  right valarray is: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaL >>= vaR;
   cout << "The element-by-element result of "
        << "the right shift is the"
        << endl << "valarray: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial operand valarray is: ( 64 -64 64 -64 64 -64 64 -64 ).
The  right valarray is: ( 0 1 2 3 4 5 6 7 ).
The element-by-element result of the right shift is the
valarray: ( 64 -32 16 -8 4 -2 1 -1 ).
```

## <a name="op_lt_lt_eq"></a>operátor&lt;&lt;=

Posune hodnotu bitů pro každý prvek valarray operandu a zadaného počtu pozic nebo podle prvku, který je určený druhým valarray.

```cpp
valarray<Type>& operator<<=(const valarray<Type>& right);

valarray<Type>& operator<<=(const Type& right);
```

### <a name="parameters"></a>Parametry

*pravé*\
Hodnota, která označuje množství levého posunu nebo valarray, jehož prvky označují množství posunutého posunu doleva.

### <a name="return-value"></a>Návratová hodnota

Valarray, jehož prvky byly posunuty doleva o zadanou hodnotu *vpravo*.

### <a name="remarks"></a>Poznámky

Podepsaná čísla mají zachována znaménka.

### <a name="example"></a>Příklad

```cpp
// valarray_class_op_ls.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 8 ), vaR ( 8 );
   for ( i = 0 ; i < 8 ; i += 2 )
      vaL [ i ] =  1;
   for ( i = 1 ; i < 8 ; i += 2 )
      vaL [ i ] =  -1;
   for ( i = 0 ; i < 8 ; i++ )
      vaR [ i ] =  i;

   cout << "The initial operand valarray is: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The  right valarray is: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaL <<= vaR;
   cout << "The element-by-element result of "
        << "the left shift"
        << endl << "on the operand array is the valarray:"
        << endl << "( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial operand valarray is: ( 1 -1 1 -1 1 -1 1 -1 ).
The  right valarray is: ( 0 1 2 3 4 5 6 7 ).
The element-by-element result of the left shift
on the operand array is the valarray:
( 1 -2 4 -8 16 -32 64 -128 ).
```

## <a name="op_star_eq"></a>operator * = – operátor

Vynásobí prvky zadaného valarray nebo hodnoty typu prvku, prvku, na operand valarray.

```cpp
valarray<Type>& operator*=(const valarray<Type>& right);

valarray<Type>& operator*=(const Type& right);
```

### <a name="parameters"></a>Parametry

*pravé*\
Valarray nebo hodnota typu elementu se shoduje s typem operandu valarray, který se má vynásobit, z prvku na operand valarray.

### <a name="return-value"></a>Návratová hodnota

Valarray, jehož prvky jsou prvkem, který je produktovým produktem pro operand valarray a *Right*.

### <a name="example"></a>Příklad

```cpp
// valarray_op_emult.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 8 ), vaR ( 8 );
   for ( i = 0 ; i < 8 ; i += 2 )
      vaL [ i ] =  2;
   for ( i = 1 ; i < 8 ; i += 2 )
      vaL [ i ] =  -1;
   for ( i = 0 ; i < 8 ; i++ )
      vaR [ i ] =  i;

   cout << "The initial valarray is: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaL *= vaR;
   cout << "The element-by-element result of "
        << "the multiplication is the"
        << endl << "valarray: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;
}
/* Output:
The initial valarray is: ( 2 -1 2 -1 2 -1 2 -1 ).
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 ).
The element-by-element result of the multiplication is the
valarray: ( 0 -1 4 -3 8 -5 12 -7 ).
*/
```

## <a name="op_add"></a>operator + – operátor

Unární operátor, který používá znaménko plus pro každý prvek v valarray.

```cpp
valarray<Type> operator+() const;
```

### <a name="return-value"></a>Návratová hodnota

Valarray, jehož prvky jsou plus pole operandu.

### <a name="example"></a>Příklad

```cpp
// valarray_op_eplus.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 10 );
   valarray<int> vaPLUS ( 10 );
   for ( i = 0 ; i < 10 ; i += 2 )
      vaL [ i ] =  -i;
   for ( i = 1 ; i < 10 ; i += 2 )
      vaL [ i ] =  i-1;

   cout << "The initial valarray is:  ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   vaPLUS = +vaL;
   cout << "The element-by-element result of "
        << "the operator+ is the"
        << endl << "valarray: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaPLUS [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial valarray is:  ( 0 0 -2 2 -4 4 -6 6 -8 8 ).
The element-by-element result of the operator+ is the
valarray: ( 0 0 -2 2 -4 4 -6 6 -8 8 ).
```

## <a name="op_add_eq"></a>operator + = – operátor

Přidá prvky zadaného valarray nebo hodnoty typu prvku, prvku do operandu valarray.

```cpp
valarray<Type>& operator+=(const valarray<Type>& right);

valarray<Type>& operator+=(const Type& right);
```

### <a name="parameters"></a>Parametry

*pravé*\
Valarray nebo hodnota typu prvku se shoduje s typem operandu valarray, který má být přidán, z prvku na operand valarray.

### <a name="return-value"></a>Návratová hodnota

Valarray, jehož prvky jsou nadmnožinou souhrnu operandu valarray a *pravého*prvku.

### <a name="example"></a>Příklad

```cpp
// valarray_op_eadd.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 8 ), vaR ( 8 );
   for ( i = 0 ; i < 8 ; i += 2 )
      vaL [ i ] =  2;
   for ( i = 1 ; i < 8 ; i += 2 )
      vaL [ i ] =  -1;
   for ( i = 0 ; i < 8 ; i++ )
      vaR [ i ] =  i;

   cout << "The initial valarray is: ( ";
      for (i = 0 ; i < 8 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial  right valarray is: ( ";
      for (i = 0 ; i < 8 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaL += vaR;
   cout << "The element-by-element result of "
        << "the sum is the"
        << endl << "valarray: ( ";
      for (i = 0 ; i < 8 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial valarray is: ( 2 -1 2 -1 2 -1 2 -1 ).
The initial  right valarray is: ( 0 1 2 3 4 5 6 7 ).
The element-by-element result of the sum is the
valarray: ( 2 0 4 2 6 4 8 6 ).
```

## <a name="operator-"></a>podnikatel

Unární operátor, který pro každý prvek v valarray používá znaménko mínus.

```cpp
valarray<Type> operator-() const;
```

### <a name="return-value"></a>Návratová hodnota

Valarray, jehož prvky jsou mínus z pole operandu.

### <a name="example"></a>Příklad

```cpp
// valarray_op_eminus.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 10 );
   valarray<int> vaMINUS ( 10 );
   for ( i = 0 ; i < 10 ; i += 2 )
      vaL [ i ] =  -i;
   for ( i = 1 ; i < 10 ; i += 2 )
      vaL [ i ] =  i-1;

   cout << "The initial valarray is:  ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   vaMINUS = -vaL;
   cout << "The element-by-element result of "
        << "the operator+ is the"
        << endl << "valarray: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaMINUS [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial valarray is:  ( 0 0 -2 2 -4 4 -6 6 -8 8 ).
The element-by-element result of the operator+ is the
valarray: ( 0 0 2 -2 4 -4 6 -6 8 -8 ).
```

## <a name="operator-_eq"></a>-= – operátor

Odečte prvky zadaného valarray nebo hodnotu typu prvku, z operandu valarray.

```cpp
valarray<Type>& operator-=(const valarray<Type>& right);

valarray<Type>& operator-=(const Type& right);
```

### <a name="parameters"></a>Parametry

*pravé*\
Valarray nebo hodnota typu elementu se shoduje s typem operandu valarray, který má být odečten, z operandů valarray.

### <a name="return-value"></a>Návratová hodnota

Valarray, jehož prvky jsou v důsledku prvku rozdílové *od valarray operandu.*

### <a name="example"></a>Příklad

```cpp
// valarray_op_esub.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 8 ), vaR ( 8 );
   for ( i = 0 ; i < 8 ; i += 2 )
      vaL [ i ] =  10;
   for ( i = 1 ; i < 8 ; i += 2 )
      vaL [ i ] =  0;
   for ( i = 0 ; i < 8 ; i++ )
      vaR [ i ] =  i;

   cout << "The initial valarray is: ( ";
      for (i = 0 ; i < 8 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial  right valarray is: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaL -= vaR;
   cout << "The element-by-element result of "
        << "the difference is the"
        << endl << "valarray: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial valarray is: ( 10 0 10 0 10 0 10 0 ).
The initial  right valarray is: ( 0 1 2 3 4 5 6 7 ).
The element-by-element result of the difference is the
valarray: ( 10 -1 8 -3 6 -5 4 -7 ).
```

## <a name="op_div_eq"></a>operator/= – operátor

Vydělí operand valarray elementu, který je ovlivněn prvky zadaného valarray nebo hodnotou typu prvku.

```cpp
valarray<Type>& operator/=(const valarray<Type>& right);

valarray<Type>& operator/=(const Type& right);
```

### <a name="parameters"></a>Parametry

*pravé*\
Valarray nebo hodnota typu prvku se shoduje s typem operandu valarray, který má být rozdělen, z prvku do operandu valarray.

### <a name="return-value"></a>Návratová hodnota

Valarray, jehož prvky jsou poměrnou hodnotou prvku v operandu valarray dělený *pravou*.

### <a name="example"></a>Příklad

```cpp
// valarray_op_ediv.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<double> vaL ( 6 ), vaR ( 6 );
   for ( i = 0 ; i < 6 ; i += 2 )
      vaL [ i ] =  100;
   for ( i = 1 ; i < 6 ; i += 2 )
      vaL [ i ] =  -100;
   for ( i = 0 ; i < 6 ; i++ )
      vaR [ i ] =  2*i;

   cout << "The initial valarray is: ( ";
      for (i = 0 ; i < 6 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for (i = 0 ; i < 6 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaL /= vaR;
   cout << "The element-by-element result of "
        << "the quotient is the"
        << endl << "valarray: ( ";
      for (i = 0 ; i < 6 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial valarray is: ( 100 -100 100 -100 100 -100 ).
The initial Right valarray is: ( 0 2 4 6 8 10 ).
The element-by-element result of the quotient is the
valarray: ( inf -50 25 -16.6667 12.5 -10 ).
```

## <a name="op_eq"></a>operátor =

Přiřadí prvky do valarray, jehož hodnoty jsou zadány přímo nebo jako součást nějakého jiného valarray nebo slice_array, gslice_array, mask_array nebo indirect_array.

```cpp
valarray<Type>& operator=(const valarray<Type>& right);

valarray<Type>& operator=(valarray<Type>&& right);

valarray<Type>& operator=(const Type& val);

valarray<Type>& operator=(const slice_array<Type>& _Slicearray);

valarray<Type>& operator=(const gslice_array<Type>& _Gslicearray);

valarray<Type>& operator=(const mask_array<Type>& _Maskarray);

valarray<Type>& operator=(const indirect_array<Type>& _Indarray);
```

### <a name="parameters"></a>Parametry

*pravé*\
Valarray ke zkopírování do valarray operandu.

\ *Val*
Hodnota, která má být přiřazena k prvkům valarray operandu.

*_Slicearray*\
Slice_array pro zkopírování do operandu valarray.

*_Gslicearray*\
Gslice_array pro zkopírování do operandu valarray.

*_Maskarray*\
Mask_array pro zkopírování do operandu valarray.

*_Indarray*\
Indirect_array pro zkopírování do operandu valarray.

### <a name="return-value"></a>Návratová hodnota

První operátor členu nahradí řízenou sekvenci kopií řízené sekvence *napravo*.

Druhý operátor členu je stejný jako první, ale s [odkazem rvalue deklarátor: & &](../cpp/rvalue-reference-declarator-amp-amp.md).

Třetí členský operátor nahradí každý prvek řízené sekvence kopií *Val*.

Zbývající členské operátory nahradí tyto prvky řízené sekvence vybrané jejich argumenty, které jsou generovány pouze pomocí [operátoru&#91;](#op_at).

Pokud hodnota člena v kontrolované sekvenci nahrazení závisí na členu v počáteční řízené sekvenci, není výsledek definován.

### <a name="remarks"></a>Poznámky

Pokud se délka řízené sekvence změní, je výsledek obecně nedefinovaný. V této implementaci je však vliv pouze na zrušení platnosti všech ukazatelů nebo odkazů na prvky v řízené sekvenci.

### <a name="example"></a>Příklad

```cpp
// valarray_op_assign.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> va ( 10 ), vaR ( 10 );
   for ( i = 0 ; i < 10 ; i += 1 )
      va [ i ] = i;
   for ( i = 0 ; i < 10 ; i+=1 )
      vaR [ i ] = 10 -  i;

   cout << "The operand valarray va is:";
   for ( i = 0 ; i < 10 ; i++ )
      cout << " " << va [ i ];
   cout << endl;

   cout << "The operand valarray vaR is:";
      for ( i = 0 ; i < 10 ; i++ )
         cout << " " << vaR [ i ];
   cout << endl;

   // Assigning vaR to va with the first member functon
   va = vaR;
   cout << "The reassigned valarray va is:";
   for ( i = 0 ; i < 10 ; i++ )
      cout << " " << va [ i ];
   cout << endl;

   // Assigning elements of value 10 to va
   // with the second member functon
   va = 10;
   cout << "The reassigned valarray va is:";
      for ( i = 0 ; i < 10 ; i++ )
         cout << " " << va [ i ];
   cout << endl;
}
```

```Output
The operand valarray va is: 0 1 2 3 4 5 6 7 8 9
The operand valarray vaR is: 10 9 8 7 6 5 4 3 2 1
The reassigned valarray va is: 10 9 8 7 6 5 4 3 2 1
The reassigned valarray va is: 10 10 10 10 10 10 10 10 10 10

```

## <a name="op_at"></a>operator [] – operátor

Vrátí odkaz na element nebo jeho hodnotu v zadaném indexu nebo v zadané podmnožině.

```cpp
Type& operator[](size_t _Off);

slice_array<Type> operator[](slice _Slicearray);

gslice_array<Type> operator[](const gslice& _Gslicearray);

mask_array<Type> operator[](const valarray<bool>& _Boolarray);

indirect_array<Type> operator[](const valarray<size_t>& _Indarray);

Type operator[](size_t _Off) const;

valarray<Type> operator[](slice _Slice) const;

valarray<Type> operator[](const gslice& _Gslicearray) const;

valarray<Type> operator[](const valarray<bool>& _Boolarray) const;

valarray<Type> operator[](const valarray<size_t>& _Indarray) const;
```

### <a name="parameters"></a>Parametry

*_Off*\
Index elementu, kterému má být přiřazena hodnota

*_Slicearray*\
Slice_array valarray, který určuje podmnožinu, která se má vybrat nebo vrátit k novému valarray.

*_Gslicearray*\
Gslice_array valarray, který určuje podmnožinu, která se má vybrat nebo vrátit k novému valarray.

*_Boolarray*\
Bool_array valarray, který určuje podmnožinu, která se má vybrat nebo vrátit k novému valarray.

*_Indarray*\
Indirect_array valarray, který určuje podmnožinu, která se má vybrat nebo vrátit k novému valarray.

### <a name="return-value"></a>Návratová hodnota

Odkaz na element nebo jeho hodnotu v zadaném indexu nebo v zadané podmnožině.

### <a name="remarks"></a>Poznámky

Členský operátor je přetížen, aby poskytoval několik způsobů výběru sekvencí prvků z těch, které jsou ovládány <strong>\*</strong>. První skupina pěti členských operátorů pracuje ve spojení s různými přetíženími [operátoru =](#op_eq) (a jinými operátory přiřazení), aby bylo možné selektivní nahrazování (dělení) řízené sekvence. Vybrané elementy musí existovat.

Při kompilaci pomocí [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) definovaného jako 1 nebo 2 dojde k chybě modulu runtime, pokud se pokusíte o přístup k prvku mimo hranice valarray.  Další informace najdete v tématu [kontrolované iterátory](../standard-library/checked-iterators.md) .

### <a name="example"></a>Příklad

Příklad, jak deklarovat a používat operátor, naleznete v části Příklady pro [řezy:: Slice](../standard-library/slice-class.md#slice) a [gslice:: gslice](../standard-library/gslice-class.md#gslice) .

## <a name="op_xor_eq"></a>operátor ^ =

Získá výhradní logický operátor OR ( **XOR**) prvku pole se zadaným valarray nebo hodnotou typu prvku.

```cpp
valarray<Type>& operator|=(const valarray<Type>& right);

valarray<Type>& operator|=(const Type& right);
```

### <a name="parameters"></a>Parametry

*pravé*\
Valarray nebo hodnota typu prvku se shoduje s hodnotou valarray operandu, která má být kombinována, s prvkem, a to exkluzivní logickou **XOR** s operandem valarray.

### <a name="return-value"></a>Návratová hodnota

Valarray, jehož prvky jsou prvkem, exkluzivní logický **XOR** s operandem valarray a *Right*.

### <a name="remarks"></a>Poznámky

Exkluzivní logická hodnota nebo, označovaná jako **XOR**, má následující sémantiku: dané elementy *e*1 a *e*2, *e*1 **XOR** *e*2 má **hodnotu true** , pokud je přesně jeden z elementů true; **false** , pokud jsou oba elementy false, nebo pokud jsou oba elementy true.

### <a name="example"></a>Příklad

```cpp
// valarray_op_exor.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
    using namespace std;
    int i;

    valarray<int> vaL ( 10 ), vaR ( 10 );
    for ( i = 0 ; i < 10 ; i += 2 )
        vaL [ i ] =  1;
    for ( i = 1 ; i < 10 ; i += 2 )
        vaL [ i ] =  0;
    for ( i = 0 ; i < 10 ; i += 3 )
        vaR [ i ] =  i;
    for ( i = 1 ; i < 10 ; i += 3 )
        vaR [ i ] =  i-1;
    for ( i = 2 ; i < 10 ; i += 3 )
        vaR [ i ] =  i-1;

    cout << "The initial operand valarray is:  ( ";
        for (i = 0 ; i < 10 ; i++ )
            cout << vaL [ i ] << " ";
    cout << ")." << endl;

    cout << "The  right valarray is: ( ";
        for ( i = 0 ; i < 10 ; i++ )
            cout << vaR [ i ] << " ";
    cout << ")." << endl;

    vaL ^= vaR;
    cout << "The element-by-element result of "
        << "the bitwise XOR operator^= is the"
        << endl << "valarray: ( ";
        for (i = 0 ; i < 10 ; i++ )
            cout << vaL [ i ] << " ";
    cout << ")." << endl;
}
```

```Output
The initial operand valarray is:  ( 1 0 1 0 1 0 1 0 1 0 ).
The  right valarray is: ( 0 0 1 3 3 4 6 6 7 9 ).
The element-by-element result of the bitwise XOR operator^= is the
valarray: ( 1 0 0 3 2 4 7 6 6 9 ).
```

## <a name="op_or_eq"></a>operátor&#124;=

Získá bitové `OR` prvků v poli buď pomocí odpovídajících prvků v zadané valarray nebo s hodnotou typu prvku.

```cpp
valarray<Type>& operator|=(const valarray<Type>& right);

valarray<Type>& operator|=(const Type& right);
```

### <a name="parameters"></a>Parametry

*pravé*\
Valarray nebo hodnota typu prvku se shoduje s hodnotou valarray operandu, která má být kombinována, což je element `OR`-s operandem valarray.

### <a name="return-value"></a>Návratová hodnota

Valarray, jehož prvky jsou bitové `OR` valarray operandu *, která je*vhodná pro element.

### <a name="remarks"></a>Poznámky

Bitová operace se dá použít jenom k manipulaci s bity v datových typech **char** a **int** a variantách, ne na **float**, **Double**, **longdouble**, **void**, **bool**nebo jiném, složitějších datových typech.

Bitový `OR` má stejnou tabulku pravdy jako logický `OR`, ale vztahuje se na datový typ na úrovni jednotlivých bitů. Vzhledem k počtu bitů *b*1 a *b*2, *b*1 `OR` *b*2 má **hodnotu true** , pokud je alespoň jedna z bitů true; **false** , pokud jsou obě bity nepravdivé.

### <a name="example"></a>Příklad

```cpp
// valarray_class_op_bitor.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 10 ), vaR ( 10 );
   for ( i = 0 ; i < 10 ; i += 2 )
      vaL [ i ] =  1;
   for ( i = 1 ; i < 10 ; i += 2 )
      vaL [ i ] =  0;
   for ( i = 0 ; i < 10 ; i += 3 )
      vaR [ i ] =  i;
   for ( i = 1 ; i < 10 ; i += 3 )
      vaR [ i ] =  i-1;
   for ( i = 2 ; i < 10 ; i += 3 )
      vaR [ i ] =  i-1;

   cout << "The initial operand valarray is:"
        << endl << "( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The  right valarray is:"
        << endl << "( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaL |= vaR;
   cout << "The element-by-element result of "
        << "the logical OR"
        << endl << "operator|= is the valarray:"
        << endl << "( ";
      for (i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial operand valarray is:
( 1 0 1 0 1 0 1 0 1 0 ).
The  right valarray is:
( 0 0 1 3 3 4 6 6 7 9 ).
The element-by-element result of the logical OR
operator|= is the valarray:
( 1 0 1 3 3 4 7 6 7 9 ).
```

## <a name="op_dtor"></a>~ – operátor

Unární operátor, který získá bitové `NOT` hodnoty každého prvku v prvku valarray.

```cpp
valarray<Type> operator~() const;
```

### <a name="return-value"></a>Návratová hodnota

Valarray logických hodnot, které jsou bitové `NOT` hodnot prvků valarray operandu.

### <a name="remarks"></a>Poznámky

Bitová operace se dá použít jenom k manipulaci s bity v datových typech **char** a **int** a variantách, ne na **float**, **Double**, **longdouble**, **void**, **bool** nebo jiném, složitějších datových typech.

Bitový `NOT` má stejnou tabulku pravdy jako logický `NOT`, ale vztahuje se na datový typ na úrovni jednotlivých bitů. V případě *, že b je false* a hodnota false, pokud je hodnota *b* true *, má dané* *bity b hodnotu*true. Logický operátor **Not**[!](#op_not) platí na úrovni elementu, počítání všech nenulových hodnot jako **true**a výsledkem je valarray logických hodnot. Bitový `NOToperator~`naproti tomu může mít za následek valarray hodnoty jiné než 0 nebo 1, v závislosti na výsledku bitové operace.

### <a name="example"></a>Příklad

```cpp
// valarray_op_bitnot.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
    using namespace std;
    int i;

    valarray<unsigned short int> vaL1 ( 10 );
    valarray<unsigned short int> vaNOT1 ( 10 );
    for ( i = 0 ; i < 10 ; i += 2 )
        vaL1 [ i ] =  i;
    for ( i = 1 ; i < 10 ; i += 2 )
        vaL1 [ i ] =  5*i;

    cout << "The initial valarray <unsigned short int> is:  ( ";
        for ( i = 0 ; i < 10 ; i++ )
            cout << vaL1 [ i ] << " ";
    cout << ")." << endl;

    vaNOT1 = ~vaL1;
    cout << "The element-by-element result of "
        << "the bitwise NOT operator~ is the"
        << endl << "valarray: ( ";
        for ( i = 0 ; i < 10 ; i++ )
            cout << vaNOT1 [ i ] << " ";
    cout << ")." << endl << endl;

    valarray<int> vaL2 ( 10 );
    valarray<int> vaNOT2 ( 10 );
    for ( i = 0 ; i < 10 ; i += 2 )
        vaL2 [ i ] =  i;
    for ( i = 1 ; i < 10 ; i += 2 )
        vaL2 [ i ] =  -2 * i;

    cout << "The initial valarray <int> is:  ( ";
        for ( i = 0 ; i < 10 ; i++ )
            cout << vaL2 [ i ] << " ";
    cout << ")." << endl;

    vaNOT2 = ~vaL2;
    cout << "The element-by-element result of "
        << "the bitwise NOT operator~ is the"
        << endl << "valarray: ( ";
        for ( i = 0 ; i < 10 ; i++ )
            cout << vaNOT2 [ i ] << " ";
    cout << ")." << endl;

    // The negative numbers are represented using
    // the two's complement approach, so adding one
    // to the flipped bits returns the negative elements
    vaNOT2 = vaNOT2 + 1;
    cout << "The element-by-element result of "
        << "adding one"
        << endl << "is the negative of the "
        << "original elements the"
        << endl << "valarray: ( ";
        for ( i = 0 ; i < 10 ; i++ )
            cout << vaNOT2 [ i ] << " ";
    cout << ")." << endl;
}
```

```Output
The initial valarray <unsigned short int> is:  ( 0 5 2 15 4 25 6 35 8 45 ).
The element-by-element result of the bitwise NOT operator~ is the
valarray: ( 65535 65530 65533 65520 65531 65510 65529 65500 65527 65490 ).

The initial valarray <int> is:  ( 0 -2 2 -6 4 -10 6 -14 8 -18 ).
The element-by-element result of the bitwise NOT operator~ is the
valarray: ( -1 1 -3 5 -5 9 -7 13 -9 17 ).
The element-by-element result of adding one
is the negative of the original elements the
valarray: ( 0 2 -2 6 -4 10 -6 14 -8 18 ).
```

## <a name="resize"></a>velikost

Změní počet prvků v valarray na zadané číslo.

```cpp
void resize(
    size_t _Newsize);

void resize(
    size_t _Newsize,
    const Type val);
```

### <a name="parameters"></a>Parametry

*_Newsize*\
Počet prvků v valarray se změněnou velikostí

\ *Val*
Hodnota, která má být předána prvkům valarray se změněnou velikostí.

### <a name="remarks"></a>Poznámky

První členská funkce inicializuje prvky s jejich výchozím konstruktorem.

Všechny ukazatele nebo odkazy na prvky v kontrolované sekvenci jsou neověřené.

### <a name="example"></a>Příklad

Následující příklad ukazuje použití členské funkce valarray:: Resize.

```cpp
// valarray_resize.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main()
{
    using namespace std;
    int i;
    size_t size1, sizeNew;

    valarray<int> va1(10);
    for (i = 0; i < 10; i+=1)
        va1[i] = i;

    cout << "The valarray contains ( ";
        for (i = 0; i < 10; i++)
            cout << va1[i] << " ";
    cout << ")." << endl;

    size1 = va1.size();
    cout << "The number of elements in the valarray is: "
         << size1  << "." <<endl << endl;

    va1.resize(15, 10);

    cout << "The valarray contains ( ";
        for (i = 0; i < 15; i++)
            cout << va1[i] << " ";
    cout << ")." << endl;
    sizeNew = va1.size();
    cout << "The number of elements in the resized valarray is: "
         << sizeNew  << "." <<endl << endl;
}
```

```Output
The valarray contains ( 0 1 2 3 4 5 6 7 8 9 ).
The number of elements in the valarray is: 10.

The valarray contains ( 10 10 10 10 10 10 10 10 10 10 10 10 10 10 10 ).
The number of elements in the resized valarray is: 15.
```

## <a name="shift"></a>posouvá

Posune všechny prvky v valarray o zadaný počet míst.

```cpp
valarray<Type> shift(int count) const;
```

### <a name="parameters"></a>Parametry

*počet*\
Počet míst, po který mají být prvky posunuty.

### <a name="return-value"></a>Návratová hodnota

Nový valarray, do kterého *byly přesunuty* všechny prvky pozice směrem k přední straně valarray, v závislosti na jejich pozicích v valarray operandu.

### <a name="remarks"></a>Poznámky

Kladná hodnota *Count* posune prvky *o zbývajících místech* s nulovou výplní.

Záporná hodnota *Count* posune prvky o *počet* míst, kde jsou umístěny vpravo, s nulovou výplní.

### <a name="example"></a>Příklad

```cpp
// valarray_shift.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> va1 ( 10 ), va2 ( 10 );
   for ( i = 0 ; i < 10 ; i += 1 )
      va1 [ i ] =  i;
   for ( i = 0 ; i < 10 ; i += 1 )
      va2 [ i ] = 10 -  i;

   cout << "The operand valarray va1(10) is: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << va1 [ i ] << " ";
   cout << ")." << endl;

   // A positive parameter shifts elements left
   va1 = va1.shift ( 4 );
   cout << "The shifted valarray va1 is: va1.shift (4) = ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << va1 [ i ] << " ";
   cout << ")." << endl;

   cout << "The operand valarray va2(10) is: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << va2 [ i ] << " ";
   cout << ")." << endl;

   // A negative parameter shifts elements right
   va2 = va2.shift ( - 4 );
   cout << "The shifted valarray va2 is: va2.shift (-4) = ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << va2 [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The operand valarray va1(10) is: ( 0 1 2 3 4 5 6 7 8 9 ).
The shifted valarray va1 is: va1.shift (4) = ( 4 5 6 7 8 9 0 0 0 0 ).
The operand valarray va2(10) is: ( 10 9 8 7 6 5 4 3 2 1 ).
The shifted valarray va2 is: va2.shift (-4) = ( 0 0 0 0 10 9 8 7 6 5 ).
```

## <a name="size"></a>hodnota

Najde počet prvků v valarray.

```cpp
size_t size() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet prvků v operandu valarray.

### <a name="example"></a>Příklad

Následující příklad ukazuje použití členské funkce valarray:: size.

```cpp
// valarray_size.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main()
{
    using namespace std;
    int i;
    size_t size1, size2;

    valarray<int> va1(10), va2(12);
    for (i = 0; i < 10; i += 1)
        va1[i] =  i;
    for (i = 0; i < 10; i += 1)
        va2[i] =  i;

    cout << "The operand valarray va1(10) is: ( ";
        for (i = 0; i < 10; i++)
            cout << va1[i] << " ";
    cout << ")." << endl;

    size1 = va1.size();
    cout << "The number of elements in the valarray va1 is: va1.size = "
         << size1  << "." <<endl << endl;

    cout << "The operand valarray va2(12) is: ( ";
        for (i = 0; i < 10; i++)
            cout << va2[i] << " ";
    cout << ")." << endl;

    size2 = va2.size();
    cout << "The number of elements in the valarray va2 is: va2.size = "
         << size2  << "." << endl << endl;

    // Initializing two more elements to va2
    va2[10] = 10;
    va2[11] = 11;
    cout << "After initializing two more elements,\n"
         << "the operand valarray va2(12) is now: ( ";
        for (i = 0; i < 12; i++)
            cout << va2[i] << " ";
    cout << ")." << endl;
    cout << "The number of elements in the valarray va2 is still: "
         << size2  << "." << endl;
}
```

```Output
The operand valarray va1(10) is: ( 0 1 2 3 4 5 6 7 8 9 ).
The number of elements in the valarray va1 is: va1.size = 10.

The operand valarray va2(12) is: ( 0 1 2 3 4 5 6 7 8 9 ).
The number of elements in the valarray va2 is: va2.size = 12.

After initializing two more elements,
the operand valarray va2(12) is now: ( 0 1 2 3 4 5 6 7 8 9 10 11 ).
The number of elements in the valarray va2 is still: 12.
```

## <a name="sum"></a>zapůjčen

Určuje součet všech prvků v valarray nenulové délky.

```cpp
Type sum() const;
```

### <a name="return-value"></a>Návratová hodnota

Součet prvků valarray operandu.

### <a name="remarks"></a>Poznámky

Pokud je délka větší než jedna, členská funkce přidá hodnoty do součtu tím, že použije `operator+=` mezi páry prvků třídy `Type`, který operátor, tedy, je nutné poskytnout pro prvky typu `Type`.

### <a name="example"></a>Příklad

```cpp
// valarray_sum.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
    using namespace std;
    int i;
    int sumva = 0;

    valarray<int> va ( 10 );
    for ( i = 0 ; i < 10 ; i+=1 )
        va [ i ] =  i;

    cout << "The operand valarray va (10) is: ( ";
        for ( i = 0 ; i < 10 ; i++ )
            cout << va [ i ] << " ";
    cout << ")." << endl;

    sumva = va.sum ( );
    cout << "The sum of elements in the valarray is: "
        << sumva  << "." <<endl;
}
```

```Output
The operand valarray va (10) is: ( 0 1 2 3 4 5 6 7 8 9 ).
The sum of elements in the valarray is: 45.
```

## <a name="swap"></a>adresu

Vyměňuje prvky dvou `valarray`s.

```cpp
void swap(valarray& right);
```

### <a name="parameters"></a>Parametry

*pravé*\
`valarray`, které poskytují prvky pro záměnu.

### <a name="remarks"></a>Poznámky

Členská funkce přemění kontrolované sekvence mezi `*this` a *pravou*. V konstantním čase to nevyvolává žádné výjimky a neověřuje žádné odkazy, ukazatele nebo iterátory, které určují elementy ve dvou řízených sekvencích.

## <a name="valarray"></a>valarray

Sestaví valarray konkrétní velikosti nebo s prvky konkrétní hodnoty nebo jako kopii jiného valarray nebo podmnožiny jiného valarray.

```cpp
valarray();

explicit valarray(
    size_t Count);

valarray(
    const Type& Val,
    size_t Count);

valarray(
    const Type* Ptr,
    size_t Count);

valarray(
    const valarray<Type>& Right);

valarray(
    const slice_array<Type>& SliceArray);

valarray(
    const gslice_array<Type>& GsliceArray);

valarray(
    const mask_array<Type>& MaskArray);

valarray(
    const indirect_array<Type>& IndArray);

valarray(
    valarray<Type>&& Right);

valarray(
    initializer_list<Type> IList);
```

### <a name="parameters"></a>Parametry

*Počet*\
Počet prvků, které mají být v valarray.

\ *Val*
Hodnota, která se má použít při inicializaci prvků v valarray.

\ *PTR*
Ukazatel na hodnoty, které mají být použity k inicializaci prvků v valarray.

*Pravé*\
Existující valarray pro inicializaci nového valarray.

*SliceArray*\
Slice_array, jejichž hodnoty elementů mají být použity při inicializaci prvků valarray konstrukce.

*GsliceArray*\
Gslice_array, jejichž hodnoty elementů mají být použity při inicializaci prvků valarray konstrukce.

*MaskArray*\
Mask_array, jejichž hodnoty elementů mají být použity při inicializaci prvků valarray konstrukce.

*IndArray*\
Indirect_array, jejichž hodnoty elementů mají být použity při inicializaci prvků valarray konstrukce.

\ *IList*
Initializer_list obsahující prvky ke zkopírování.

### <a name="remarks"></a>Poznámky

První (výchozí) konstruktor inicializuje objekt do prázdného pole. Následující tři konstruktory každý inicializuje objekt na pole *počtu elementů* následujícím způsobem:

- Pro explicitní `valarray(size_t Count)`je každý element inicializován s výchozím konstruktorem.

- Pro `valarray(const Type& Val, Count)`je každý prvek inicializován pomocí *Val*.

- Pro `valarray(const Type* Ptr, Count)`je prvek na pozici `I` inicializován s `Ptr`[`I`].

Každý zbývající konstruktor inicializuje objekt na valarray typ\<> objekt určený podmnožinou určenou v argumentu.

Poslední konstruktor je stejný jako u poslední, ale s [odkazem rvalue deklarátor: & &](../cpp/rvalue-reference-declarator-amp-amp.md).

### <a name="example"></a>Příklad

```cpp
// valarray_ctor.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main()
{
    using namespace std;
    int i;

    // The second member function
    valarray<int> va(10);
    for (auto i : va){
        va[i] = 2 * (i + 1);
    }

    cout << "The operand valarray va is:\n(";
    for (auto i : va) {
        cout << " " << va[i];
    }
    cout << " )" << endl;

    slice Slice(2, 4, 3);

    // The fifth member function
    valarray<int> vaSlice = va[Slice];

    cout << "The new valarray initialized from the slice is vaSlice =\n"
        << "va[slice( 2, 4, 3)] = (";
    for (int i = 0; i < 3; i++) {
        cout << " " << vaSlice[i];
    }
    cout << " )" << endl;

    valarray<int> va2{{ 1, 2, 3, 4 }};
    for (auto& v : va2) {
        cout << v << " ";
    }
    cout << endl;
}
```

```Output
The operand valarray va is:
( 0 2 2 2 2 2 2 2 2 2 )
The new valarray initialized from the slice is vaSlice =
va[slice( 2, 4, 3)] = ( 0 0 0 )
1 2 3 4
```

## <a name="value_type"></a>value_type

Typ, který představuje typ elementu uložený ve valarray.

```cpp
typedef Type value_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro parametr šablony `Type`.

### <a name="example"></a>Příklad

```cpp
// valarray_value_type.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
    using namespace std;
    int i;
    valarray<int> va ( 10 );
    for ( i = 0 ; i < 10 ; i += 2 )
        va [ i ] =  i;
    for ( i = 1 ; i < 10 ; i += 2 )
        va [ i ] =  -1;

    cout << "The initial operand valarray is:  ( ";
        for ( i = 0 ; i < 10 ; i++ )
            cout << va [ i ] << " ";
    cout << ")." << endl;

    // value_type declaration and initialization:
    valarray<int>::value_type Right = 10;

    cout << "The decalared value_type Right is: "
            << Right << endl;
    va *= Right;
    cout << "The resulting valarray is:  ( ";
        for ( i = 0 ; i < 10 ; i++ )
            cout << va [ i ] << " ";
    cout << ")." << endl;
}
```

```Output
The initial operand valarray is:  ( 0 -1 2 -1 4 -1 6 -1 8 -1 ).
The decalared value_type Right is: 10
The resulting valarray is:  ( 0 -10 20 -10 40 -10 60 -10 80 -10 ).
```

## <a name="see-also"></a>Viz také

[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
