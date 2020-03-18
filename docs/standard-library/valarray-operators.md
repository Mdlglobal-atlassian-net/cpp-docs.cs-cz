---
title: '&lt;operátory&gt; valarray'
ms.date: 03/27/2019
f1_keywords:
- valarray/std::operator!=
- valarray/std::operator%
- valarray/std::operator&amp;
- valarray/std::operator&amp;&amp;
- valarray/std::operator&gt;
- valarray/std::operator&gt;&gt;
- valarray/std::operator&gt;=
- valarray/std::operator&lt;
- valarray/std::operator&lt;&lt;
- valarray/std::operator&lt;=
- valarray/std::operator*
- valarray/std::operator+
- valarray/std::operator-
- valarray/std::operator/
- valarray/std::operator==
- valarray/std::operator^
- valarray/std::operator|
- valarray/std::operator||
ms.assetid: 8a53562c-90ab-4eb3-85d3-ada5259d90b0
helpviewer_keywords:
- std::operator!= (valarray), std::operator&amp; (valarray)
- std::operator&amp;&amp; (valarray)
- std::operator&gt; (valarray)
- std::operator&gt;&gt; (valarray)
- std::operator&gt;= (valarray)
- std::operator&lt; (valarray)
- std::operator&lt;&lt; (valarray)
- std::operator&lt;= (valarray), std::operator== (valarray)
ms.openlocfilehash: 231bad65e2af1ee2ab800890c83cc50e584a8c6a
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79422386"
---
# <a name="ltvalarraygt-operators"></a>&lt;operátory&gt; valarray

## <a name="op_neq"></a>! = – operátor

Testuje, zda odpovídající prvky dvou velikostí valarrays jsou nerovné nebo zda všechny prvky valarray nejsou rovny zadané hodnotě.

```cpp
template <class Type>
valarray<bool>
operator!=(
    const valarray<Type>& left,
    const valarray<Type>& right);

template <class Type>
valarray<bool>
operator!=(
    const valarray<Type>& left,
    const Type& right);

template <class Type>
valarray<bool>
operator!=(
    const Type& left,
    const valarray<Type>& right);
```

### <a name="parameters"></a>Parametry

*levý*\
První ze dvou valarrays, jejichž prvky mají být testovány na nerovnost.

*pravé*\
Druhý ze dvou valarrays, jejichž prvky mají být testovány na nerovnost.

### <a name="return-value"></a>Návratová hodnota

Valarray logických hodnot, z nichž každá je:

- **true** , pokud odpovídající prvky nejsou stejné.

- **false** , pokud odpovídající prvky nejsou rovny.

### <a name="remarks"></a>Poznámky

První operátor šablony vrátí objekt třídy [valarray\<bool >](../standard-library/valarray-bool-class.md), přičemž každý z nich `I` je `left[I] != right[I]`.

Druhý operátor šablony ukládá do elementu `I` `left[I] != right`.

Třetí operátor šablony ukládá do elementu `I` `left != right[I]`.

### <a name="example"></a>Příklad

```cpp
// valarray_op_ne.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 10 ), vaR ( 10 );
   valarray<bool> vaNE ( 10 );
   for ( i = 0 ; i < 10 ; i += 2 )
      vaL [ i ] =  -i;
   for ( i = 1 ; i < 10 ; i += 2 )
      vaL [ i ] =  i;
   for ( i = 0 ; i < 10 ; i++ )
      vaR [ i ] =  i;

   cout << "The initial Left valarray is: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaNE = ( vaL != vaR );
   cout << "The element-by-element result of "
        << "the not equal comparison test is the\n"
        << "valarray: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaNE [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial Left valarray is: ( 0 1 -2 3 -4 5 -6 7 -8 9 ).
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 8 9 ).
The element-by-element result of the not equal comparison test is the
valarray: ( 0 0 1 0 1 0 1 0 1 0 ).
```

## <a name="op_mod"></a>podnikatel

Získá zbytek dělení odpovídajících prvků dvou stejně velkých valarrays nebo dělení valarray zadanou hodnotou nebo rozdělením zadané hodnoty hodnotou valarray.

```cpp
template <class Type>
valarray<Type>
operator%(
    const valarray<Type>& left,
    const valarray<Type>& right);

template <class Type>
valarray<Type>
operator%(
    const valarray<Type>& left,
    const Type& right);

template <class Type>
valarray<Type>
operator%(
    const Type& left,
    const valarray<Type>& right);
```

### <a name="parameters"></a>Parametry

*levý*\
Hodnota nebo valarray, která slouží jako dividenda, do které má být rozdělena jiná hodnota nebo valarray.

*pravé*\
Hodnota nebo valarray, která slouží jako dělitel a který rozděluje jinou hodnotu nebo valarray.

### <a name="return-value"></a>Návratová hodnota

Valarray, jehož prvky jsou zbylé zbytky *zleva* dělené *pravou*.

### <a name="example"></a>Příklad

```cpp
// valarray_op_rem.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 6 ), vaR ( 6 );
   valarray<int> vaREM ( 6 );
   for ( i = 0 ; i < 6 ; i += 2 )
      vaL [ i ] =  53;
   for ( i = 1 ; i < 6 ; i += 2 )
      vaL [ i ] =  -67;
   for ( i = 0 ; i < 6 ; i++ )
      vaR [ i ] =  3*i+1;

   cout << "The initial Left valarray is: ( ";
      for ( i = 0 ; i < 6 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for ( i = 0 ; i < 6 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaREM = ( vaL % vaR );
   cout << "The remainders from the element-by-element "
        << "division is the\n"
        << "valarray: ( ";
      for ( i = 0 ; i < 6 ; i++ )
         cout << vaREM [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial Left valarray is: ( 53 -67 53 -67 53 -67 ).
The initial Right valarray is: ( 1 4 7 10 13 16 ).
The remainders from the element-by-element division is the
valarray: ( 0 -3 4 -7 1 -3 ).
```

## <a name="op_amp"></a>operátor&amp;

Získá bitovou **a** mezi odpovídajícími prvky dvou stejně velkých valarrays nebo mezi valarray a zadanou hodnotou typu prvku.

```cpp
template <class Type>
valarray<Type>
operator&(
    const valarray<Type>& left,
    const valarray<Type>& right);

template <class Type>
valarray<Type>
operator&(
    const valarray<Type>& left,
    const Type& right);

template <class Type>
valarray<Type>
operator&(
    const Type& left,
    const valarray<Type>& right);
```

### <a name="parameters"></a>Parametry

*levý*\
První ze dvou valarrays, jejichž příslušné prvky mají být kombinovány s bitovým `AND` nebo zadanou hodnotou typu prvku, aby byly kombinovány s každým prvkem valarray.

*pravé*\
Druhý ze dvou valarrays, jejichž příslušné prvky mají být kombinovány s bitovým `AND` nebo zadanou hodnotou typu prvku, který má být sloučen s každým prvkem valarray.

### <a name="return-value"></a>Návratová hodnota

Valarray, jehož prvky představují kombinaci mezi prvkem a operací *levého* a *pravého*prvku.

### <a name="remarks"></a>Poznámky

Bitová operace se dá použít jenom k manipulaci s bity v datových typech **char** a **int** a variantách, ne na **float**, **Double**, **longdouble**, **void**, **bool** nebo jiném, složitějších datových typech.

Bitový `AND` má stejnou tabulku pravdy jako logický `AND`, ale vztahuje se na datový typ na úrovni jednotlivých bitů. [Operátor & &](#op_amp_amp) se vztahuje na úroveň elementu, počítá všechny nenulové hodnoty jako true a výsledek je valarray logických hodnot. Operátor bitového `AND` [&](#op_amp)na rozdíl od může mít za následek valarray hodnoty jiné než 0 nebo 1, v závislosti na výsledku bitové operace.

### <a name="example"></a>Příklad

```cpp
// valarray_op_bitand.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 10 ), vaR ( 10 );
   valarray<int> vaBWA ( 10 );
   for ( i = 0 ; i < 10 ; i += 2 )
      vaL [ i ] =  0;
   for ( i = 1 ; i < 10 ; i += 2 )
      vaL [ i ] =  i+1;
   for ( i = 0 ; i < 10 ; i++ )
      vaR [ i ] =  i;

   cout << "The initial Left valarray is:  ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaBWA = ( vaL & vaR );
   cout << "The element-by-element result of "
        << "the bitwise operator & is the\n"
        << "valarray: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaBWA [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial Left valarray is:  ( 0 2 0 4 0 6 0 8 0 10 ).
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 8 9 ).
The element-by-element result of the bitwise operator & is the
valarray: ( 0 0 0 0 0 4 0 0 0 8 ).
```

## <a name="op_amp_amp"></a>operátor&amp;&amp;

Získá logickou **a** mezi odpovídajícími prvky dvou velikostí valarrays nebo mezi valarray a zadanou hodnotou typu elementu valarray.

```cpp
template <class Type>
valarray<bool>
operator&&(
    const valarray<Type>& left,
    const valarray<Type>& right);

template <class Type>
valarray<bool>
operator&&(
    const valarray<Type>& left,
    const Type& right);

template <class Type>
valarray<bool>
operator&&(
    const Type& left,
    const valarray<Type>& right);
```

### <a name="parameters"></a>Parametry

*levý*\
První ze dvou valarrays, jejichž příslušné prvky mají být kombinovány s logickým `AND` nebo zadanou hodnotou typu prvku, který má být kombinován s každým prvkem valarray.

*pravé*\
Druhý ze dvou valarrays, jejichž příslušné prvky mají být kombinovány s logickým `AND` nebo zadanou hodnotou typu prvku, který má být kombinován s každým prvkem valarray.

### <a name="return-value"></a>Návratová hodnota

Valarray, jehož prvky jsou typu bool a představují kombinaci prvku s logickou `AND`ou operací *levého* a *pravého*prvku.

### <a name="remarks"></a>Poznámky

Logický `ANDoperator&&` se vztahuje na úroveň elementu, počítá všechny nenulové hodnoty jako true a výsledkem je valarray logických hodnot. Bitová verze `AND`, [operátor &,](#op_amp)na rozdíl od, může mít za následek valarray hodnoty jiné než 0 nebo 1, v závislosti na výsledku bitové operace.

### <a name="example"></a>Příklad

```cpp
// valarray_op_logand.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 10 ), vaR ( 10 );
   valarray<bool> vaLAA ( 10 );
   for ( i = 0 ; i < 10 ; i += 2 )
      vaL [ i ] =  0;
   for ( i = 1 ; i < 10 ; i += 2 )
      vaL [ i ] =  i-1;
   for ( i = 0 ; i < 10 ; i++ )
      vaR [ i ] =  i;

   cout << "The initial Left valarray is:  ( ";
      for (i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for (i = 0 ; i < 10 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaLAA = ( vaL && vaR );
   cout << "The element-by-element result of "
        << "the logical AND operator&& is the\n"
        << "valarray: ( ";
      for (i = 0 ; i < 10 ; i++ )
         cout << vaLAA [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial Left valarray is:  ( 0 0 0 2 0 4 0 6 0 8 ).
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 8 9 ).
The element-by-element result of the logical AND operator&& is the
valarray: ( 0 0 0 1 0 1 0 1 0 1 ).
```

## <a name="op_gt"></a>operátor&gt;

Testuje, zda prvky jednoho valarray jsou větší než prvky stejné velikosti valarray nebo zda jsou všechny prvky valarray větší nebo menší než zadaná hodnota.

```cpp
template <class Type>
valarray<bool>
operator>(
    const valarray<Type>& left,
    const valarray<Type>& right);

template <class Type>
valarray<bool>
operator>(
    const valarray<Type>& left,
    const Type& right);

template <class Type>
valarray<bool>
operator>(
    const Type& left,
    const valarray<Type>& right);
```

### <a name="parameters"></a>Parametry

*levý*\
První ze dvou valarrays, jejichž prvky mají být porovnány, nebo zadanou hodnotu, která má být porovnána s každým prvkem valarray.

*pravé*\
Druhý ze dvou valarrays, jejichž prvky mají být porovnány, nebo zadanou hodnotu, která má být porovnána s každým prvkem valarray.

### <a name="return-value"></a>Návratová hodnota

Valarray logických hodnot, z nichž každá je:

- **true** , pokud je *levý* prvek nebo hodnota větší než odpovídající *pravý* prvek nebo hodnota.

- **false** , pokud *levý* prvek nebo hodnota není větší než odpovídající *pravý* prvek nebo hodnota.

### <a name="remarks"></a>Poznámky

Pokud počet prvků ve dvou valarrays není rovno, výsledek není definován.

### <a name="example"></a>Příklad

```cpp
// valarray_op_gt.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 10 ), vaR ( 10 );
   valarray<bool> vaNE ( 10 );
   for ( i = 0 ; i < 10 ; i += 2 )
      vaL [ i ] =  -i;
   for ( i = 1 ; i < 10 ; i += 2 )
      vaL [ i ] =  i;
   for ( i = 0 ; i < 10 ; i++ )
      vaR [ i ] =  i - 1;

   cout << "The initial Left valarray is: ( ";
      for (i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaNE = ( vaL > vaR );
   cout << "The element-by-element result of "
        << "the greater than comparison test is the\n"
        << "valarray: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaNE [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial Left valarray is: ( 0 1 -2 3 -4 5 -6 7 -8 9 ).
The initial Right valarray is: ( -1 0 1 2 3 4 5 6 7 8 ).
The element-by-element result of the greater than comparison test is the
valarray: ( 1 1 0 1 0 1 0 1 0 1 ).
```

## <a name="op_gt_eq"></a>operátor&gt;=

Testuje, zda prvky jednoho valarray jsou větší než nebo rovny prvkům valarray stejné velikosti nebo zda jsou všechny prvky valarray větší nebo rovny zadané hodnotě.

```cpp
template <class Type>
valarray<bool>
operator>=(
    const valarray<Type>& left,
    const valarray<Type>& right);

template <class Type>
valarray<bool>
operator>=(
    const valarray<Type>& left,
    const Type& right);

template <class Type>
valarray<bool>
operator>=(
    const Type& left,
    const valarray<Type>& right);
```

### <a name="parameters"></a>Parametry

*levý*\
První ze dvou valarrays, jejichž prvky mají být porovnány, nebo zadanou hodnotu, která má být porovnána s každým prvkem valarray.

*pravé*\
Druhý ze dvou valarrays, jejichž prvky mají být porovnány, nebo zadanou hodnotu, která má být porovnána s každým prvkem valarray.

### <a name="return-value"></a>Návratová hodnota

Valarray logických hodnot, z nichž každá je:

- **true** , pokud je *levý* prvek nebo hodnota větší nebo rovna odpovídajícímu *pravému* prvku nebo hodnotě.

- **false** , pokud *levý* prvek nebo hodnota je menší než odpovídající *pravý* prvek nebo hodnota.

### <a name="remarks"></a>Poznámky

Pokud počet prvků ve dvou valarrays není rovno, výsledek není definován.

### <a name="example"></a>Příklad

```cpp
// valarray_op_ge.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 10 ), vaR ( 10 );
   valarray<bool> vaNE ( 10 );
   for ( i = 0 ; i < 10 ; i += 2 )
      vaL [ i ] =  -i;
   for ( i = 1 ; i < 10 ; i += 2 )
      vaL [ i ] =  i;
   for ( i = 0 ; i < 10 ; i++ )
      vaR [ i ] =  i - 1;

   cout << "The initial Left valarray is: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaNE = ( vaL >= vaR );
   cout << "The element-by-element result of "
        << "the greater than or equal test is the\n"
        << "valarray: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaNE [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial Left valarray is: ( 0 1 -2 3 -4 5 -6 7 -8 9 ).
The initial Right valarray is: ( -1 0 1 2 3 4 5 6 7 8 ).
The element-by-element result of the greater than or equal test is the
valarray: ( 1 1 0 1 0 1 0 1 0 1 ).
```

## <a name="op_gt_gt"></a>operátor&gt;&gt;

Posune pravou část bitů pro každý prvek valarray o zadaný počet pozic nebo o hodnotu v rámci prvku určenou druhým valarray.

```cpp
template <class Type>
valarray<Type>
operator>>(
    const valarray<Type>& left,
    const valarray<Type>& right);

template <class Type>
valarray<Type>
operator>>(
    const valarray<Type>& left,
    const Type& right);

template <class Type>
valarray<Type>
operator>>(
    const Type& left,
    const valarray<Type>& right);
```

### <a name="parameters"></a>Parametry

*levý*\
Hodnota, která má být posunuta nebo valarray, jehož prvky mají být posunuty.

*pravé*\
Hodnota, která označuje množství pravého posunutí nebo valarray, jehož prvky ukazují množství správného posunu posunutého prvku.

### <a name="return-value"></a>Návratová hodnota

Valarray, jehož prvky byly posunuty vpravo o zadanou velikost.

### <a name="remarks"></a>Poznámky

Podepsaná čísla mají zachována znaménka.

### <a name="example"></a>Příklad

```cpp
// valarray_op_rs.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 8 ), vaR ( 8 );
   valarray<int> vaNE ( 8 );
   for ( i = 0 ; i < 8 ; i += 2 )
      vaL [ i ] =  64;
   for ( i = 1 ; i < 8 ; i += 2 )
      vaL [ i ] =  -64;
   for ( i = 0 ; i < 8 ; i++ )
      vaR [ i ] =  i;

   cout << "The initial Left valarray is: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaNE = ( vaL >> vaR );
   cout << "The element-by-element result of "
        << "the right shift is the\n"
        << "valarray: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaNE [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial Left valarray is: ( 64 -64 64 -64 64 -64 64 -64 ).
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 ).
The element-by-element result of the right shift is the
valarray: ( 64 -32 16 -8 4 -2 1 -1 ).
```

## <a name="op_lt"></a>operátor&lt;

Testuje, zda jsou prvky jednoho valarray menší než prvky stejné velikosti valarray, nebo zda jsou všechny prvky valarray větší nebo menší než zadaná hodnota.

```cpp
template <class Type>
valarray<bool>
operator<(
    const valarray<Type>& left,
    const valarray<Type>& right);

template <class Type>
valarray<bool>
operator<(
    const valarray<Type>& left,
    const Type& right);

template <class Type>
valarray<bool>
operator<(
    const Type& left,
    const valarray<Type>& right);
```

### <a name="parameters"></a>Parametry

*levý*\
První ze dvou valarrays, jejichž prvky mají být porovnány, nebo zadanou hodnotu, která má být porovnána s každým prvkem valarray.

*pravé*\
Druhý ze dvou valarrays, jejichž prvky mají být porovnány, nebo zadanou hodnotu, která má být porovnána s každým prvkem valarray.

### <a name="return-value"></a>Návratová hodnota

Valarray logických hodnot, z nichž každá je:

- **true** , pokud *levý* prvek nebo hodnota je menší než odpovídající *pravý* prvek nebo hodnota.

- **false** , pokud *levý* prvek nebo hodnota není menší než odpovídající *pravý* prvek nebo hodnota.

### <a name="remarks"></a>Poznámky

Pokud počet prvků 2 valarrays není rovno, výsledek není definován.

### <a name="example"></a>Příklad

```cpp
// valarray_op_lt.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 10 ), vaR ( 10 );
   valarray<bool> vaNE ( 10 );
   for ( i = 0 ; i < 10 ; i += 2 )
      vaL [ i ] =  -i;
   for ( i = 1 ; i < 10 ; i += 2 )
      vaL [ i ] =  i;
   for ( i = 0 ; i < 10 ; i++ )
      vaR [ i ] =  i;

   cout << "The initial Left valarray is: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaNE = ( vaL < vaR );
   cout << "The element-by-element result of "
        << "the less-than comparson test is the\n"
        << "valarray: ( ";
      for (i = 0 ; i < 10 ; i++ )
         cout << vaNE [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial Left valarray is: ( 0 1 -2 3 -4 5 -6 7 -8 9 ).
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 8 9 ).
The element-by-element result of the less-than comparson test is the
valarray: ( 0 0 1 0 1 0 1 0 1 0 ).
```

## <a name="op_lt_eq"></a>operátor&lt;=

Testuje, zda jsou prvky jednoho valarray menší nebo rovny prvkům valarray stejné velikosti, nebo zda jsou všechny prvky valarray větší nebo rovny hodnotě nebo menší než zadaná hodnota.

```cpp
template <class Type>
valarray<bool>
operator<=(
    const valarray<Type>& left,
    const valarray<Type>& right);

template <class Type>
valarray<bool>
operator<=(
    const valarray<Type>& left,
    const Type& right);

template <class Type>
valarray<bool>
operator<=(
    const Type& left,
    const valarray<Type>& right);
```

### <a name="parameters"></a>Parametry

*levý*\
První ze dvou valarrays, jejichž prvky mají být porovnány, nebo zadanou hodnotu, která má být porovnána s každým prvkem valarray.

*pravé*\
Druhý ze dvou valarrays, jejichž prvky mají být porovnány, nebo zadanou hodnotu, která má být porovnána s každým prvkem valarray.

### <a name="return-value"></a>Návratová hodnota

Valarray logických hodnot, z nichž každá je:

- **true** , pokud je *levý* prvek nebo hodnota menší nebo rovna odpovídajícímu *pravému* prvku nebo hodnotě.

- **false** , pokud je *levý* prvek nebo hodnota větší než odpovídající *pravý* prvek nebo hodnota.

### <a name="remarks"></a>Poznámky

Pokud počet prvků 2 valarrays není rovno, výsledek není definován.

### <a name="example"></a>Příklad

```cpp
// valarray_op_le.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 10 ), vaR ( 10 );
   valarray<bool> vaNE ( 10 );
   for ( i = 0 ; i < 10 ; i += 2 )
      vaL [ i ] =  -i;
   for ( i = 1 ; i < 10 ; i += 2 )
      vaL [ i ] =  i;
   for ( i = 0 ; i < 10 ; i++ )
      vaR [ i ] =  i - 1;

   cout << "The initial Left valarray is: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaNE = ( vaL <= vaR );
   cout << "The element-by-element result of "
        << "the less than or equal test is the\n"
        << "valarray: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaNE [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial Left valarray is: ( 0 1 -2 3 -4 5 -6 7 -8 9 ).
The initial Right valarray is: ( -1 0 1 2 3 4 5 6 7 8 ).
The element-by-element result of the less than or equal test is the
valarray: ( 0 0 1 0 1 0 1 0 1 0 ).
```

## <a name="op_lt_lt"></a>operátor&lt;&lt;

Levý posune bity pro každý prvek valarray o zadaný počet pozic nebo o požadovanou hodnotu prvku určenou druhým valarray.

```cpp
template <class Type>
valarray<Type>
operator<<(
    const valarray<Type>& left,
    const valarray<Type>& right);

template <class Type>
valarray<Type>
operator<<(
    const valarray<Type>& left,
    const Type& right);

template <class Type>
valarray<Type>
operator<<(
    const Type& left,
    const valarray<Type>& right);
```

### <a name="parameters"></a>Parametry

*levý*\
Hodnota, která má být posunuta nebo valarray, jehož prvky mají být posunuty.

*pravé*\
Hodnota, která označuje množství levého posunu nebo valarray, jehož prvky označují množství posunutého posunu doleva.

### <a name="return-value"></a>Návratová hodnota

Valarray, jehož prvky byly posunuty doleva o zadanou velikost.

### <a name="remarks"></a>Poznámky

Podepsaná čísla mají zachována znaménka.

### <a name="example"></a>Příklad

```cpp
// valarray_op_ls.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 8 ), vaR ( 8 );
   valarray<int> vaNE ( 8 );
   for ( i = 0 ; i < 8 ; i += 2 )
      vaL [ i ] =  1;
   for ( i = 1 ; i < 8 ; i += 2 )
      vaL [ i ] =  -1;
   for ( i = 0 ; i < 8 ; i++ )
      vaR [ i ] =  i;

   cout << "The initial Left valarray is: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaNE = ( vaL << vaR );
   cout << "The element-by-element result of "
        << "the left shift is the\n"
        << "valarray: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaNE [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial Left valarray is: ( 1 -1 1 -1 1 -1 1 -1 ).
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 ).
The element-by-element result of the left shift is the
valarray: ( 1 -2 4 -8 16 -32 64 -128 ).
```

## <a name="op_star"></a>podnikatel

Získá produkt z prvku, který je v souladu s odpovídajícími prvky dvou stejně velkých valarrays nebo mezi valarray a zadanou hodnotou.

```cpp
template <class Type>
valarray<Type>
operator*(
    const valarray<Type>& left,
    const valarray<Type>& right);

template <class Type>
valarray<Type>
operator*(
    const valarray<Type>& left,
    const Type& right);

template <class Type>
valarray<Type>
operator*(
    const Type& left,
    const valarray<Type>& right);
```

### <a name="parameters"></a>Parametry

*levý*\
První ze dvou valarrays, jejichž prvky mají být vynásobeny nebo zadanou hodnotou, která má být vynásobena každým prvkem valarray.

*pravé*\
Druhý ze dvou valarrays, jejichž prvky mají být vynásobeny nebo zadanou hodnotou, která má být vynásobena každým prvkem valarray.

### <a name="return-value"></a>Návratová hodnota

Valarray, jehož prvky jsou produktovým produktem, který je v *levé* a *pravé*části.

### <a name="example"></a>Příklad

```cpp
// valarray_op_eprod.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 8 ), vaR ( 8 );
   valarray<int> vaNE ( 8 );
   for ( i = 0 ; i < 8 ; i += 2 )
      vaL [ i ] =  2;
   for ( i = 1 ; i < 8 ; i += 2 )
      vaL [ i ] =  -1;
   for ( i = 0 ; i < 8 ; i++ )
      vaR [ i ] =  i;

   cout << "The initial Left valarray is: ( ";
      for (i = 0 ; i < 8 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for (i = 0 ; i < 8 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaNE = ( vaL * vaR );
   cout << "The element-by-element result of "
        << "the multiplication is the\n"
        << "valarray: ( ";
      for (i = 0 ; i < 8 ; i++ )
         cout << vaNE [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial Left valarray is: ( 2 -1 2 -1 2 -1 2 -1 ).
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 ).
The element-by-element result of the multiplication is the
valarray: ( 0 -1 4 -3 8 -5 12 -7 ).
```

## <a name="op_add"></a>operator + – operátor

Získá poměrné hodnoty mezi odpovídajícími prvky dvou stejně velkých valarrays nebo mezi valarray a zadanou hodnotou.

```cpp
template <class Type>
valarray<Type>
operator+(
    const valarray<Type>& left,
    const valarray<Type>& right);

template <class Type>
valarray<Type>
operator+(
    const valarray<Type>& left,
    const Type& right);

template <class Type>
valarray<Type>
operator+(
    const Type& left,
    const valarray<Type>& right);
```

### <a name="parameters"></a>Parametry

*levý*\
První ze dvou valarrays, jejichž prvky mají být přidány, nebo zadanou hodnotu, která má být přidána s každým prvkem valarray.

*pravé*\
Druhý ze dvou valarrays, jejichž prvky mají být přidány, nebo zadanou hodnotu, která má být přidána s každým prvkem valarray.

### <a name="return-value"></a>Návratová hodnota

Valarray, jehož prvky jsou v rámci prvku souhrnně čteny *zleva* a *pravá*.

### <a name="example"></a>Příklad

```cpp
// valarray_op_esum.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 8 ), vaR ( 8 );
   valarray<int> vaNE ( 8 );
   for ( i = 0 ; i < 8 ; i += 2 )
      vaL [ i ] =  2;
   for ( i = 1 ; i < 8 ; i += 2 )
      vaL [ i ] =  -1;
   for ( i = 0 ; i < 8 ; i++ )
      vaR [ i ] =  i;

   cout << "The initial Left valarray is: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaNE = ( vaL + vaR );
   cout << "The element-by-element result of "
        << "the sum is the\n"
        << "valarray: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaNE [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial Left valarray is: ( 2 -1 2 -1 2 -1 2 -1 ).
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 ).
The element-by-element result of the sum is the
valarray: ( 2 0 4 2 6 4 8 6 ).
```

## <a name="operator-"></a>podnikatel

Získá rozdíl mezi odpovídajícími prvky ze dvou odpovídajících prvků, které mají stejnou velikost valarrays, nebo mezi valarray a zadanou hodnotou.

```cpp
template <class Type>
valarray<Type>
operator-(
    const valarray<Type>& left,
    const valarray<Type>& right);

template <class Type>
valarray<Type>
operator-(
    const valarray<Type>& left,
    const Type& right);

template <class Type>
valarray<Type>
operator-(
    const Type& left,
    const valarray<Type>& right);
```

### <a name="parameters"></a>Parametry

*levý*\
Hodnota nebo valarray, která slouží jako minuend, ze které se odečtou jiné hodnoty nebo valarrays v podobě rozdílu.

*pravé*\
Hodnota nebo valarray, která slouží jako subtrahend, jež má být odečtena od jiných hodnot nebo valarrays v důsledku vytvoření rozdílu.

### <a name="return-value"></a>Návratová hodnota

Valarray, jehož prvky jsou v rámci prvku a jsou v něm rozdíly *zleva* a *Right*.

### <a name="remarks"></a>Poznámky

Aritmetická terminologie používaná v popisu odčítání:

rozdíl = minuend-subtrahend

### <a name="example"></a>Příklad

```cpp
// valarray_op_ediff.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 8 ), vaR ( 8 );
   valarray<int> vaNE ( 8 );
   for ( i = 0 ; i < 8 ; i += 2 )
      vaL [ i ] =  10;
   for ( i = 1 ; i < 8 ; i += 2 )
      vaL [ i ] =  0;
   for ( i = 0 ; i < 8 ; i++ )
      vaR [ i ] =  i;

   cout << "The initial Left valarray is: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaNE = ( vaL - vaR );
   cout << "The element-by-element result of "
        << "the difference is the\n"
        << "valarray: ( ";
      for (i = 0 ; i < 8 ; i++ )
         cout << vaNE [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial Left valarray is: ( 10 0 10 0 10 0 10 0 ).
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 ).
The element-by-element result of the difference is the
valarray: ( 10 -1 8 -3 6 -5 4 -7 ).
```

## <a name="op_div"></a>podnikatel

Získá podíl poměrné hodnoty mezi odpovídajícími prvky dvou stejně velkých valarrays nebo mezi valarray a zadanou hodnotou.

```cpp
template <class Type>
valarray<Type>
operator/(
    const valarray<Type>& left,
    const valarray<Type>& right);

template <class Type>
valarray<Type>
operator/(
    const valarray<Type>& left,
    const Type& right);

template <class Type>
valarray<Type>
operator/(
    const Type& left,
    const valarray<Type>& right);
```

### <a name="parameters"></a>Parametry

*levý*\
Hodnota nebo valarray, která slouží jako dividenda, do které je rozdělena jiná hodnota nebo valarray v podobě podílu.

*pravé*\
Hodnota nebo valarray, která slouží jako dělitel a který rozděluje jinou hodnotu nebo valarray v podobě podílu.

### <a name="return-value"></a>Návratová hodnota

Valarray, jehož prvky jsou podílem *zbývajícího* prvku, který je dělen *napravo*.

### <a name="remarks"></a>Poznámky

Aritmetická terminologie použitá v popisu rozdělení:

podíl = dividenda/dělitel

### <a name="example"></a>Příklad

```cpp
// valarray_op_equo.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<double> vaL ( 6 ), vaR ( 6 );
   valarray<double> vaNE ( 6 );
   for ( i = 0 ; i < 6 ; i += 2 )
      vaL [ i ] =  100;
   for ( i = 1 ; i < 6 ; i += 2 )
      vaL [ i ] =  -100;
   for ( i = 0 ; i < 6 ; i++ )
      vaR [ i ] =  2*i;

   cout << "The initial Left valarray is: ( ";
      for ( i = 0 ; i < 6 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for ( i = 0 ; i < 6 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaNE = ( vaL / vaR );
   cout << "The element-by-element result of "
        << "the quotient is the\n"
        << "valarray: ( ";
      for ( i = 0 ; i < 6 ; i++ )
         cout << vaNE [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial Left valarray is: ( 100 -100 100 -100 100 -100 ).
The initial Right valarray is: ( 0 2 4 6 8 10 ).
The element-by-element result of the quotient is the
valarray: ( inf -50 25 -16.6667 12.5 -10 ).
```

## <a name="op_eq_eq"></a>operator = = – operátor

Testuje, zda odpovídající prvky dvou velikostí valarrays jsou stejné nebo zda jsou všechny prvky valarray rovny zadané hodnotě.

```cpp
template <class Type>
valarray<bool>
operator==(
    const valarray<Type>& left,
    const valarray<Type>& right);

template <class Type>
valarray<bool>
operator==(
    const valarray<Type>& left,
    const Type& right);

template <class Type>
valarray<bool>
operator==(
    const Type& left,
    const valarray<Type>& right);
```

### <a name="parameters"></a>Parametry

*levý*\
První ze dvou valarrays, jejichž prvky mají být testovány pro rovnost.

*pravé*\
Druhý ze dvou valarrays, jejichž prvky mají být testovány pro rovnost.

### <a name="return-value"></a>Návratová hodnota

Valarray logických hodnot, z nichž každá je:

- **true** , pokud jsou odpovídající prvky stejné.

- **false** , pokud odpovídající prvky nejsou stejné.

### <a name="remarks"></a>Poznámky

První operátor šablony vrátí objekt třídy [valarray\<bool >](../standard-library/valarray-bool-class.md), přičemž každý z nich `I` je `left[I] == right[I]`. Druhý operátor šablony ukládá do elementu `I` `left[I] == right`. Třetí operátor šablony ukládá do elementu `I` `left == right[I]`.

### <a name="example"></a>Příklad

```cpp
// valarray_op_eq.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 10 ), vaR ( 10 );
   valarray<bool> vaNE ( 10 );
   for ( i = 0 ; i < 10 ; i += 2 )
      vaL [ i ] =  -i;
   for ( i = 1 ; i < 10 ; i += 2 )
      vaL [ i ] =  i;
   for ( i = 0 ; i < 10 ; i++ )
      vaR [ i ] =  i;

   cout << "The initial Left valarray is: ( ";
      for (i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaNE = ( vaL == vaR );
   cout << "The element-by-element result of "
        << "the equality comparison test is the\n"
        << "valarray: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaNE [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial Left valarray is: ( 0 1 -2 3 -4 5 -6 7 -8 9 ).
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 8 9 ).
The element-by-element result of the equality comparison test is the
valarray: ( 1 1 0 1 0 1 0 1 0 1 ).
```

## <a name="op_xor"></a>operátor ^

Získá bitovou exkluzivní `OR` ( **XOR**) mezi odpovídajícími prvky dvou stejně velkých valarrays nebo mezi valarray a zadanou hodnotou typu prvku.

```cpp
template <class Type>
valarray<Type>
operator^(
    const valarray<Type>& left,
    const valarray<Type>& right);

template <class Type>
valarray<Type>
operator^(
    const valarray<Type>& left,
    const Type& right);

template <class Type>
valarray<Type>
operator^(
    const Type& left,
    const valarray<Type>& right);
```

### <a name="parameters"></a>Parametry

*levý*\
První ze dvou valarrays, jejichž příslušné prvky mají být kombinovány s bitovým **operátorem XOR** nebo zadanou hodnotou typu prvku, aby byly kombinovány s každým prvkem valarray.

*pravé*\
Druhý ze dvou valarrays, jejichž příslušné prvky mají být kombinovány s bitovým **operátorem XOR** nebo zadanou hodnotou typu prvku, které mají být kombinovány s každým prvkem valarray.

### <a name="return-value"></a>Návratová hodnota

Valarray, jehož prvky jsou v kombinaci s prvkem, což je vhodná kombinace operace bitového **operátoru XOR** *vlevo* a *vpravo*.

### <a name="remarks"></a>Poznámky

Bitová operace se dá použít jenom k manipulaci s bity v datových typech **char** a **int** a variantách, ne na **float**, **Double**, **Long Double**, **void**, **bool** nebo jiném, složitějších datových typech.

Bitový exkluzivní `OR` ( **XOR**) má následující sémantiku: dané bity *b*1 a *b*2, *b*1 **XOR** *b*2 má **hodnotu true** , pokud je přesně jedna z bitů true; **false** , pokud jsou obě bity false, nebo pokud jsou obě bity pravdivé.

### <a name="example"></a>Příklad

```cpp
// valarray_op_xor.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 10 ), vaR ( 10 );
   valarray<int> vaLAA ( 10 );
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

   cout << "The initial Left valarray is:  ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaLAA = ( vaL ^ vaR );
   cout << "The element-by-element result of "
        << "the bitwise XOR operator^ is the\n"
        << "valarray: ( ";
           for ( i = 0 ; i < 10 ; i++ )
         cout << vaLAA [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial Left valarray is:  ( 1 0 1 0 1 0 1 0 1 0 ).
The initial Right valarray is: ( 0 0 1 3 3 4 6 6 7 9 ).
The element-by-element result of the bitwise XOR operator^ is the
valarray: ( 1 0 0 3 2 4 7 6 6 9 ).
```

## <a name="op_or"></a>podnikatel&#124;

Získá bitový `OR` mezi odpovídajícími prvky dvou stejně velkých valarrays nebo mezi valarray a zadanou hodnotou typu prvku.

```cpp
template <class Type>
valarray<Type>
operator|(
    const valarray<Type>& left,
    const valarray<Type>& right);

template <class Type>
valarray<Type>
operator|(
    const valarray<Type>& left,
    const Type& right);

template <class Type>
valarray<Type>
operator|(
    const Type& left,
    const valarray<Type>& right);
```

### <a name="parameters"></a>Parametry

*levý*\
První ze dvou valarrays, jejichž příslušné prvky mají být kombinovány s bitovým `OR` nebo zadanou hodnotou typu prvku, aby byly kombinovány s každým prvkem valarray.

*pravé*\
Druhý ze dvou valarrays, jejichž příslušné prvky mají být kombinovány s bitovým `OR` nebo zadanou hodnotou typu prvku, který má být sloučen s každým prvkem valarray.

### <a name="return-value"></a>Návratová hodnota

Valarray, jehož prvky jsou v kombinaci s prvkem, což je vhodná kombinace bitové operace `OR` *doleva* a *doprava*.

### <a name="remarks"></a>Poznámky

Bitová operace se dá použít jenom k manipulaci s bity v datových typech **char** a **int** a variantách, ne na **float**, **Double**, **longdouble**, **void**, **bool** nebo jiném, složitějších datových typech.

Bitový operátor OR má stejnou tabulku pravdy jako logický `OR`, ale platí pro datový typ na úrovni jednotlivých bitů. V případě bitů *b*1 a *b*2, *b*1 `OR` *b*2 má **hodnotu true** , pokud je alespoň jeden z bitů true nebo **false** , pokud jsou obě bity nepravdivé. [Operátor&#124; ](../standard-library/valarray-operators.md#op_lor) logického `OR`se vztahuje na úroveň elementu, počítá všechny nenulové hodnoty jako **true**a výsledkem je valarray logických hodnot. Bitový operátor OR `operator|`naproti tomu může mít za následek valarray hodnoty jiné než 0 nebo 1, v závislosti na výsledku bitové operace.

### <a name="example"></a>Příklad

```cpp
// valarray_op_bitor.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 10 ), vaR ( 10 );
   valarray<int> vaLAA ( 10 );
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

   cout << "The initial Left valarray is:  ( ";
      for (i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for (i = 0 ; i < 10 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaLAA = ( vaL | vaR );
   cout << "The element-by-element result of "
        << "the bitwise OR operator| is the\n"
        << "valarray: ( ";
      for (i = 0 ; i < 10 ; i++ )
         cout << vaLAA [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial Left valarray is:  ( 1 0 1 0 1 0 1 0 1 0 ).
The initial Right valarray is: ( 0 0 1 3 3 4 6 6 7 9 ).
The element-by-element result of the bitwise OR operator| is the
valarray: ( 1 0 1 3 3 4 7 6 7 9 ).
```

## <a name="op_lor"></a>podnikatel&#124;&#124;

Získá logickou `OR` mezi odpovídajícími prvky dvou stejně velkých valarrays nebo mezi valarray a zadanou hodnotou typu elementu valarray.

```cpp
template <class Type>
valarray<bool>
operator||(
    const valarray<Type>& left,
    const valarray<Type>& right);

template <class Type>
valarray<bool>
operator||(
    const valarray<Type>& left,
    const Type& right);

template <class Type>
valarray<bool>
operator||(
    const Type& left,
    const valarray<Type>& right);
```

### <a name="parameters"></a>Parametry

*levý*\
První ze dvou valarrays, jejichž příslušné prvky mají být kombinovány s logickým `OR` nebo zadanou hodnotou typu prvku, který má být kombinován s každým prvkem valarray.

*pravé*\
Druhý ze dvou valarrays, jejichž příslušné prvky mají být kombinovány s logickým `OR` nebo zadanou hodnotou typu prvku, který má být kombinován s každým prvkem valarray.

### <a name="return-value"></a>Návratová hodnota

Valarray, jehož prvky jsou typu **bool** a představují kombinaci prvku s logickou nebo operací *levého* a *pravého*prvku.

### <a name="remarks"></a>Poznámky

Logický `OR` `operator||` se vztahuje na úroveň elementu, počítá všechny nenulové hodnoty jako **true**a výsledek je valarray logických hodnot. Bitová verze `OR`, [operátor&#124; ](../standard-library/valarray-operators.md#op_or) naopak, může mít za následek valarray hodnoty jiné než 0 nebo 1, v závislosti na výsledku bitové operace.

### <a name="example"></a>Příklad

```cpp
// valarray_op_logor.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 10 ), vaR ( 10 );
   valarray<bool> vaLOR ( 10 );
   for ( i = 0 ; i < 10 ; i += 2 )
      vaL [ i ] =  0;
   for ( i = 1 ; i < 10 ; i += 2 )
      vaL [ i ] =  i-1;
   for ( i = 0 ; i < 10 ; i += 3 )
      vaR [ i ] =  i;
   for ( i = 1 ; i < 10 ; i += 3 )
      vaR [ i ] =  0;
   for ( i = 2 ; i < 10 ; i += 3 )
      vaR [ i ] =  0;

   cout << "The initial Left valarray is:  ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaLOR = ( vaL || vaR );
   cout << "The element-by-element result of "
        << "the logical OR operator|| is the\n"
        << "valarray: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaLOR [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial Left valarray is:  ( 0 0 0 2 0 4 0 6 0 8 ).
The initial Right valarray is: ( 0 0 0 3 0 0 6 0 0 9 ).
The element-by-element result of the logical OR operator|| is the
valarray: ( 0 0 0 1 0 1 1 1 0 1 ).
```
