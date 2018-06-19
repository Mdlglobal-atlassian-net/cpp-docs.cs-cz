---
title: '&lt;valarray –&gt; operátory | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
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
dev_langs:
- C++
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
ms.openlocfilehash: e65d11ef95b5305988fe77ab258bb39c2b80de57
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33862465"
---
# <a name="ltvalarraygt-operators"></a>&lt;valarray –&gt; operátory

||||
|-|-|-|
|[operator!=](#op_neq)|[% – operátor](#op_mod)|[Operátor&amp;](#op_amp)|
|[Operátor&amp;&amp;](#op_amp_amp)|[Operátor&gt;](#op_gt)|[Operátor&gt;&gt;](#op_gt_gt)|
|[Operátor&gt;=](#op_gt_eq)|[Operátor&lt;](#op_lt)|[Operátor&lt;&lt;](#op_lt_lt)|
|[Operátor&lt;=](#op_lt_eq)|[operátor *](#op_star)|[operátor +](#op_add)|
|[Operator –](#operator-)|[operátor nebo](#op_div)|[operator==](#op_eq_eq)|
|[Operator ^](#op_xor)|[– operátor|](#op_or)|[– operátor||](#op_lor)|

## <a name="op_neq"></a>  Operator! =

Testuje, jestli odpovídající elementy dva stejně velké valarray – třídy jsou různé nebo zda jsou všechny elementy valarray – nerovné zadanou hodnotou.

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

`left` První dva valarray – třídy, jehož elementy jsou má být testována nerovnost.

`right` Druhý dva valarray – třídy, jehož elementy jsou má být testována nerovnost.

### <a name="return-value"></a>Návratová hodnota

Valarray – logické hodnoty, z nichž každý je:

- **Hodnota TRUE,** Pokud odpovídající prvky nerovné.

- **false** Pokud odpovídající elementy nejsou.

### <a name="remarks"></a>Poznámky

Vrátí první operátor šablony objekt třídy [valarray –\<bool >](../standard-library/valarray-bool-class.md), každý z jehož elementy `I` je `left[I] != right[I]`.

Druhá šablona operátor ukládá v elementu `I` `left[I] != right`.

Třetí operátor šablony ukládá v elementu `I` `left != right[I]`.

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
        << "the not equal comparison test is the\n valarray: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaNE [ i ] << " ";
   cout << ")." << endl;
}
\* Output:
The initial Left valarray is: ( 0 1 -2 3 -4 5 -6 7 -8 9 ).
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 8 9 ).
The element-by-element result of the not equal comparison test is the
 valarray: ( 0 0 1 0 1 0 1 0 1 0 ).
*\
```

## <a name="op_mod"></a>  % – operátor

Získá zbytek po dělení odpovídající elementy dva stejně velké valarray – třídy nebo dělení valarray – zadanou hodnotou nebo dělení valarray – zadanou hodnotou.

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

`left` Hodnota nebo valarray –, která slouží jako dělenec, do které jinou hodnotu nebo valarray – je možné rozdělit.

`right` Hodnota nebo valarray –, který slouží jako dělitel a který rozděluje jinou hodnotu nebo valarray –.

### <a name="return-value"></a>Návratová hodnota

Valarray –, jehož elementy jsou element-wise zbytků z `left` dělený `right`.

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
        << "division is the\n valarray: ( ";
      for ( i = 0 ; i < 6 ; i++ )
         cout << vaREM [ i ] << " ";
   cout << ")." << endl;
}
\* Output:
The initial Left valarray is: ( 53 -67 53 -67 53 -67 ).
The initial Right valarray is: ( 1 4 7 10 13 16 ).
The remainders from the element-by-element division is the
 valarray: ( 0 -3 4 -7 1 -3 ).
*\
```

## <a name="op_amp"></a>  Operátor&amp;

Získá bitové hodnotě **a** mezi odpovídající elementy dva stejně velké valarray – třídy nebo valarray – a zadanou hodnotu typu prvku.

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

`left` První dva valarray – třídy, jejichž příslušné prvky jsou a nelze jej zkombinovat s bitové hodnotě **a** nebo zadaná hodnota typu prvku a nelze jej zkombinovat bitový s každý prvek valarray –.

`right` Druhý dva valarray – třídy, jejichž příslušné prvky jsou a nelze jej zkombinovat s bitové hodnotě **a** nebo zadaná hodnota typu prvku a nelze jej zkombinovat bitový s každý prvek valarray –.

### <a name="return-value"></a>Návratová hodnota

Valarray –, jehož elementy jsou element-wise kombinace bitové operace AND z `left` a `right`.

### <a name="remarks"></a>Poznámky

Bitové operace lze použít pouze k manipulaci s bitů `char` a `int` datové typy a variantních proměnných a ne v **float**, **dvojité**, **longdouble**, `void`, `bool` nebo jiných, komplexnější datové typy.

Bitové hodnotě **a** má stejné tabulce pravdivosti jako logické **a** , ale platí pro typ dat na úrovni jednotlivých bitů. [Operátor & &](../standard-library/valarray-operators.md#amp) se vztahuje na úroveň element počítání všechny nenulové hodnoty jako true a výsledek je valarray – hodnot logická hodnota. Bitové hodnotě **ANDoperator &**, naopak může mít za následek valarray – hodnot než 0 nebo 1, v závislosti na výsledek bitové operace.

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
        << "the bitwise operator & is the\n valarray: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaBWA [ i ] << " ";
   cout << ")." << endl;
}
\* Output:
The initial Left valarray is:  ( 0 2 0 4 0 6 0 8 0 10 ).
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 8 9 ).
The element-by-element result of the bitwise operator & is the
 valarray: ( 0 0 0 0 0 4 0 0 0 8 ).
*\
```

## <a name="op_amp_amp"></a>  Operátor&amp;&amp;

Získá logické **a** mezi odpovídající elementy dva stejně velké valarray – třídy nebo valarray – a zadanou hodnotu valarray – element typu.

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

`left` První dva valarray – třídy, jejichž příslušné prvky jsou a nelze jej zkombinovat s logické **a** nebo zadaná hodnota typu prvku a nelze jej zkombinovat s každý prvek valarray –.

`right` Druhý dva valarray – třídy, jejichž příslušné prvky jsou a nelze jej zkombinovat s logické **a** nebo zadaná hodnota typu prvku a nelze jej zkombinovat s každý prvek valarray –.

### <a name="return-value"></a>Návratová hodnota

Valarray –, jehož elementy jsou logického typu a element-wise kombinace logické **a** operace `left` a `right`.

### <a name="remarks"></a>Poznámky

Logické **ANDoperator & &** se vztahuje na úroveň element počítání všechny nenulové hodnoty jako true a výsledek je valarray – hodnot logická hodnota. Bitové verzi **a**, [operátor &,](../standard-library/valarray-operators.md#op_amp), naopak může mít za následek valarray – hodnot než 0 nebo 1, v závislosti na výsledek bitové operace.

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
        << "the logical AND operator&& is the\n valarray: ( ";
      for (i = 0 ; i < 10 ; i++ )
         cout << vaLAA [ i ] << " ";
   cout << ")." << endl;
}
\* Output:
The initial Left valarray is:  ( 0 0 0 2 0 4 0 6 0 8 ).
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 8 9 ).
The element-by-element result of the logical AND operator&& is the
 valarray: ( 0 0 0 1 0 1 0 1 0 1 ).
*\
```

## <a name="op_gt"></a>  Operátor&gt;

Ověřuje, zda prvky jeden valarray – jsou větší než elementy stejně velké valarray – nebo zda jsou všechny elementy valarray – větší nebo menší než zadanou hodnotou.

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

`left` První dva valarray – třídy, jehož elementy jsou být porovnána nebo zadaná hodnota se porovná s každý prvek valarray –.

`right` Druhý dva valarray – třídy, jehož elementy jsou být porovnána nebo zadaná hodnota se porovná s každý prvek valarray –.

### <a name="return-value"></a>Návratová hodnota

Valarray – logické hodnoty, z nichž každý je:

- **Hodnota TRUE,** Pokud `left` je větší než odpovídající element nebo hodnota `right` element nebo hodnota.

- **false** Pokud `left` není větší než odpovídající element nebo hodnota `right` element nebo hodnota.

### <a name="remarks"></a>Poznámky

Pokud počet elementů ve dvou valarray – třídy není rovno, výsledkem nedefinovaný.

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
        << "the greater than comparison test is the\n valarray: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaNE [ i ] << " ";
   cout << ")." << endl;
}
\* Output:
The initial Left valarray is: ( 0 1 -2 3 -4 5 -6 7 -8 9 ).
The initial Right valarray is: ( -1 0 1 2 3 4 5 6 7 8 ).
The element-by-element result of the greater than comparison test is the
 valarray: ( 1 1 0 1 0 1 0 1 0 1 ).
*\
```

## <a name="op_gt_eq"></a>  Operátor&gt;=

Ověřuje, zda prvky jeden valarray – jsou větší než nebo rovna hodnotě elementy stejně velké valarray – nebo jestli všechny elementy valarray – jsou větší než nebo rovno nebo menší než nebo roven zadané hodnotě.

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

`left` První dva valarray – třídy, jehož elementy jsou být porovnána nebo zadaná hodnota se porovná s každý prvek valarray –.

`right` Druhý dva valarray – třídy, jehož elementy jsou být porovnána nebo zadaná hodnota se porovná s každý prvek valarray –.

### <a name="return-value"></a>Návratová hodnota

Valarray – logické hodnoty, z nichž každý je:

- **Hodnota TRUE,** Pokud `left` element nebo hodnota je větší než nebo rovna hodnotě odpovídající `right` element nebo hodnota.

- **false** Pokud `left` element nebo hodnota je menší než odpovídající `right` element nebo hodnota.

### <a name="remarks"></a>Poznámky

Pokud počet elementů ve dvou valarray – třídy není rovno, výsledkem nedefinovaný.

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
        << "the greater than or equal test is the\n valarray: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaNE [ i ] << " ";
   cout << ")." << endl;
}
\* Output:
The initial Left valarray is: ( 0 1 -2 3 -4 5 -6 7 -8 9 ).
The initial Right valarray is: ( -1 0 1 2 3 4 5 6 7 8 ).
The element-by-element result of the greater than or equal test is the
 valarray: ( 1 1 0 1 0 1 0 1 0 1 ).
*\
```

## <a name="op_gt_gt"></a>  Operátor&gt;&gt;

Posuny vpravo bits pro jednotlivé elementy valarray – po zadaný počet pozic nebo o element-wise částku určeného druhý valarray –.

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

`left` Hodnota posunutí nebo valarray –, jehož elementy jsou posunutí.

`right` Hodnota udávající dobu posunutí doprava nebo valarray –, jehož elementy znamenat element-wise množství posunutí doprava.

### <a name="return-value"></a>Návratová hodnota

Valarray –, jehož elementy mít právo posunuty, o zadanou velikost.

### <a name="remarks"></a>Poznámky

Podepsaný čísla mají jejich znaménka zachovaná.

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
        << "the right shift is the\n valarray: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaNE [ i ] << " ";
   cout << ")." << endl;
}
\* Output:
The initial Left valarray is: ( 64 -64 64 -64 64 -64 64 -64 ).
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 ).
The element-by-element result of the right shift is the
 valarray: ( 64 -32 16 -8 4 -2 1 -1 ).
*\
```

## <a name="op_lt"></a>  Operátor&lt;

Ověřuje, zda elementy jeden valarray – je nižší než elementy stejně velké valarray – nebo zda jsou všechny elementy valarray – větší nebo menší než zadanou hodnotou.

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

`left` První dva valarray – třídy, jehož elementy jsou být porovnána nebo zadaná hodnota se porovná s každý prvek valarray –.

`right` Druhý dva valarray – třídy, jehož elementy jsou být porovnána nebo zadaná hodnota se porovná s každý prvek valarray –.

### <a name="return-value"></a>Návratová hodnota

Valarray – logické hodnoty, z nichž každý je:

- **Hodnota TRUE,** Pokud `left` element nebo hodnota je menší než odpovídající `right` element nebo hodnota.

- **false** Pokud `left` element nebo hodnota je menší než odpovídající `right` element nebo hodnota.

### <a name="remarks"></a>Poznámky

Pokud počet elementů dva valarray – třídy není rovno, výsledkem nedefinovaný.

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
        << "the less-than comparson test is the\n valarray: ( ";
      for (i = 0 ; i < 10 ; i++ )
         cout << vaNE [ i ] << " ";
   cout << ")." << endl;
}
\* Output:
The initial Left valarray is: ( 0 1 -2 3 -4 5 -6 7 -8 9 ).
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 8 9 ).
The element-by-element result of the less-than comparson test is the
 valarray: ( 0 0 1 0 1 0 1 0 1 0 ).
*\
```

## <a name="op_lt_eq"></a>  Operátor&lt;=

Testuje, zda jsou elementy valarray – jeden, menší než nebo rovna hodnotě elementy stejně velké valarray – nebo zda všechny elementy valarray – jsou větší než nebo rovno nebo menší než nebo roven zadané hodnotě.

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

`left` První dva valarray – třídy, jehož elementy jsou být porovnána nebo zadaná hodnota se porovná s každý prvek valarray –.

`right` Druhý dva valarray – třídy, jehož elementy jsou být porovnána nebo zadaná hodnota se porovná s každý prvek valarray –.

### <a name="return-value"></a>Návratová hodnota

Valarray – logické hodnoty, z nichž každý je:

- **Hodnota TRUE,** Pokud `left` element nebo hodnota je menší než nebo rovna do odpovídajících `right` element nebo hodnota.

- **false** Pokud `left` je větší než odpovídající element nebo hodnota `right` element nebo hodnota.

### <a name="remarks"></a>Poznámky

Pokud počet elementů dva valarray – třídy není rovno, výsledkem nedefinovaný.

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
        << "the less than or equal test is the\n valarray: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaNE [ i ] << " ";
   cout << ")." << endl;
}
\* Output:
The initial Left valarray is: ( 0 1 -2 3 -4 5 -6 7 -8 9 ).
The initial Right valarray is: ( -1 0 1 2 3 4 5 6 7 8 ).
The element-by-element result of the less than or equal test is the
 valarray: ( 0 0 1 0 1 0 1 0 1 0 ).
*\
```

## <a name="op_lt_lt"></a>  Operátor&lt;&lt;

Levé posune bitů pro jednotlivé elementy valarray – po zadaný počet pozic nebo o element-wise částku určeného druhý valarray –.

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

`left` Hodnota posunutí nebo valarray –, jehož elementy jsou posunutí.

`right` Hodnota udávající dobu posunutí doleva nebo valarray –, jehož elementy znamenat element-wise množství posunutí doleva.

### <a name="return-value"></a>Návratová hodnota

Valarray –, jehož elementy byly posunuty doleva o zadanou velikost.

### <a name="remarks"></a>Poznámky

Podepsaný čísla mají jejich znaménka zachovaná.

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
        << "the left shift is the\n valarray: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaNE [ i ] << " ";
   cout << ")." << endl;
}
\* Output:
The initial Left valarray is: ( 1 -1 1 -1 1 -1 1 -1 ).
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 ).
The element-by-element result of the left shift is the
 valarray: ( 1 -2 4 -8 16 -32 64 -128 ).
*\
```

## <a name="op_star"></a>  operátor *

Získá element-wise produktu mezi odpovídající elementy dva stejně velké valarray – třídy nebo z mezi valarray – zadanou hodnotou.

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

`left` První dva valarray – třídy, jehož elementy jsou vynásobí nebo zadanou hodnotu vynásobí jednotlivé prvky valarray –.

`right` Druhý dva valarray – třídy, jehož elementy jsou vynásobí nebo zadanou hodnotu vynásobí jednotlivé prvky valarray –.

### <a name="return-value"></a>Návratová hodnota

Valarray –, jehož elementy jsou element-wise produktu z `left` a `right`.

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
        << "the multiplication is the\n valarray: ( ";
      for (i = 0 ; i < 8 ; i++ )
         cout << vaNE [ i ] << " ";
   cout << ")." << endl;
}
\* Output:
The initial Left valarray is: ( 2 -1 2 -1 2 -1 2 -1 ).
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 ).
The element-by-element result of the multiplication is the
 valarray: ( 0 -1 4 -3 8 -5 12 -7 ).
*\
```

## <a name="op_add"></a>  operátor +

Získá element-wise součet mezi odpovídající elementy dva stejně velké valarray – třídy nebo z mezi valarray – zadanou hodnotou.

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

`left` První dva valarray – třídy, jehož elementy jsou přidávaného nebo zadaná hodnota má být přidán s každý prvek valarray –.

`right` Druhý dva valarray – třídy, jehož elementy jsou přidávaného nebo zadanou hodnotou přidávaného s každý prvek valarray –.

### <a name="return-value"></a>Návratová hodnota

Valarray –, jehož elementy jsou element-wise sum z `left` a `right`.

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
        << "the sum is the\n valarray: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaNE [ i ] << " ";
   cout << ")." << endl;
}
\* Output:
The initial Left valarray is: ( 2 -1 2 -1 2 -1 2 -1 ).
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 ).
The element-by-element result of the sum is the
 valarray: ( 2 0 4 2 6 4 8 6 ).
*\
```

## <a name="operator-"></a>  Operator –

Získá element-wise rozdíl mezi odpovídající elementy dva stejně velké valarray – třídy nebo z mezi valarray – zadanou hodnotou.

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

`left` Hodnota nebo valarray –, která slouží jako minuend, ze kterého jiných hodnot nebo valarray – třídy se bude odečítat v, které tvoří rozdíl.

`right` Hodnota nebo valarray –, která slouží jako subtrahend, která se bude odečítat od jiných hodnot nebo valarray – třídy, ve které tvoří rozdíl.

### <a name="return-value"></a>Návratová hodnota

Valarray –, jehož elementy jsou element-wise rozdíl z `left` a `right`.

### <a name="remarks"></a>Poznámky

Aritmetické technologiím použitým v popisující odčítání:

rozdíl = minuend - subtrahend

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
        << "the difference is the\n valarray: ( ";
      for (i = 0 ; i < 8 ; i++ )
         cout << vaNE [ i ] << " ";
   cout << ")." << endl;
}
\* Output:
The initial Left valarray is: ( 10 0 10 0 10 0 10 0 ).
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 ).
The element-by-element result of the difference is the
 valarray: ( 10 -1 8 -3 6 -5 4 -7 ).
*\
```

## <a name="op_div"></a>  operátor nebo

Získá element-wise podílu mezi odpovídající elementy dva stejně velké valarray – třídy nebo z mezi valarray – zadanou hodnotou.

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

`left` Hodnota nebo valarray –, která slouží jako dělenec, do které jinou hodnotu nebo valarray – je možné rozdělit v tvořící podílu.

`right` Hodnota nebo valarray –, který slouží jako dělitel a který rozděluje jiná hodnota nebo valarray – v tvořící podílu.

### <a name="return-value"></a>Návratová hodnota

Valarray –, jehož elementy jsou element-wise podílu z `left` dělený `right`.

### <a name="remarks"></a>Poznámky

Aritmetické technologiím použitým v popisující dělení:

koeficient = dělenec / dělitel

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
        << "the quotient is the\n valarray: ( ";
      for ( i = 0 ; i < 6 ; i++ )
         cout << vaNE [ i ] << " ";
   cout << ")." << endl;
}
\* Output:
The initial Left valarray is: ( 100 -100 100 -100 100 -100 ).
The initial Right valarray is: ( 0 2 4 6 8 10 ).
The element-by-element result of the quotient is the
 valarray: ( inf -50 25 -16.6667 12.5 -10 ).
*\
```

## <a name="op_eq_eq"></a>  Operator ==

Testy, jestli odpovídající elementy dva stejně velké valarray – třídy jsou stejné, nebo zda jsou všechny elementy valarray – rovnat zadanou hodnotou.

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

`left` První dva valarray – třídy, jehož elementy jsou má být testována rovnosti.

`right` Druhý dva valarray – třídy, jehož elementy jsou má být testována rovnosti.

### <a name="return-value"></a>Návratová hodnota

Valarray – logické hodnoty, z nichž každý je:

- **Hodnota TRUE,** Pokud odpovídající elementy jsou stejné.

- **false** Pokud odpovídající elementy nejsou stejné.

### <a name="remarks"></a>Poznámky

Vrátí první operátor šablony objekt třídy [valarray –\<bool >](../standard-library/valarray-bool-class.md), každý z jehož elementy `I` je `left[I] == right[I]`. Druhá šablona operátor ukládá v elementu `I` `left[I] == right`. Třetí operátor šablony ukládá v elementu `I` `left == right[I]`.

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
        << "the equality comparison test is the\n valarray: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaNE [ i ] << " ";
   cout << ")." << endl;
}
\* Output:
The initial Left valarray is: ( 0 1 -2 3 -4 5 -6 7 -8 9 ).
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 8 9 ).
The element-by-element result of the equality comparison test is the
 valarray: ( 1 1 0 1 0 1 0 1 0 1 ).
*\
```

## <a name="op_xor"></a>  Operator ^

Získá bitový exkluzivní `OR` ( **XOR**) mezi odpovídající elementy dva stejně velké valarray – třídy nebo valarray – a zadanou hodnotu typu prvku.

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

`left` První dva valarray – třídy, jejichž příslušné prvky jsou a nelze jej zkombinovat s bitové hodnotě **XOR** nebo zadaná hodnota typu prvku a nelze jej zkombinovat bitový s každý prvek valarray –.

`right` Druhý dva valarray – třídy, jejichž příslušné prvky jsou a nelze jej zkombinovat s bitové hodnotě **XOR** nebo zadaná hodnota typu prvku a nelze jej zkombinovat bitový s každý prvek valarray –.

### <a name="return-value"></a>Návratová hodnota

Valarray –, jehož elementy jsou element-wise kombinace bitové hodnotě **XOR** operace `left` a `right`.

### <a name="remarks"></a>Poznámky

Bitové operace lze použít pouze k manipulaci s bitů `char` a `int` datové typy a variantních proměnných a ne v **float**, **dvojité**, `long double`, `void`, `bool` nebo jiných, komplexnější datové typy.

Bitový exkluzivní `OR` ( **XOR**) má následující sémantiku: zadané bity *b*1 a *b*2, *b*1  **XOR** *b*2 je **true** Pokud právě jeden z bitů pravdivá; **false** Pokud jsou obě bits false nebo pokud jsou splněny obě služby bits.

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
        << "the bitwise XOR operator^ is the\n valarray: ( ";
           for ( i = 0 ; i < 10 ; i++ )
         cout << vaLAA [ i ] << " ";
   cout << ")." << endl;
}
\* Output:
The initial Left valarray is:  ( 1 0 1 0 1 0 1 0 1 0 ).
The initial Right valarray is: ( 0 0 1 3 3 4 6 6 7 9 ).
The element-by-element result of the bitwise XOR operator^ is the
 valarray: ( 1 0 0 3 2 4 7 6 6 9 ).
*\
```

## <a name="op_or"></a>  operátor&#124;

Získá bitové hodnotě `OR` mezi odpovídající elementy dva stejně velké valarray – třídy nebo valarray – a zadanou hodnotu typu prvku.

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

`left` První dva valarray – třídy, jejichž příslušné prvky jsou a nelze jej zkombinovat s bitové hodnotě `OR` nebo zadaná hodnota typu prvku a nelze jej zkombinovat bitový s každý prvek valarray –.

`right` Druhý dva valarray – třídy, jejichž příslušné prvky jsou a nelze jej zkombinovat s bitové hodnotě `OR` nebo zadaná hodnota typu prvku a nelze jej zkombinovat bitový s každý prvek valarray –.

### <a name="return-value"></a>Návratová hodnota

Valarray –, jehož elementy jsou element-wise kombinace bitové hodnotě `OR` operace `left` a `right`.

### <a name="remarks"></a>Poznámky

Bitové operace lze použít pouze k manipulaci s bitů `char` a `int` datové typy a variantních proměnných a ne v **float**, **dvojité**, **longdouble**, `void`, `bool` nebo jiných, komplexnější datové typy.

Bitová hodnota OR má stejné tabulce pravdivosti jako logické `OR`, ale platí pro typ dat na úrovni jednotlivých bitů. Zadané bity *b*1 a *b*2, *b*1 `OR` *b*2 je **true** pokud alespoň jedna z bitů Hodnota TRUE, nebo **false** Pokud jsou obě bits false. Logické `OR` [operátor&#124; &#124; ](../standard-library/valarray-operators.md#op_lor) se vztahuje na úroveň element počítání všechny nenulové hodnoty jako **true**, a výsledkem je valarray – hodnot logická hodnota. Bitová hodnota OR `operator|`, naopak může mít za následek valarray – hodnot než 0 nebo 1, v závislosti na výsledek bitové operace.

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
        << "the bitwise OR operator| is the\n valarray: ( ";
      for (i = 0 ; i < 10 ; i++ )
         cout << vaLAA [ i ] << " ";
   cout << ")." << endl;
}
\* Output:
The initial Left valarray is:  ( 1 0 1 0 1 0 1 0 1 0 ).
The initial Right valarray is: ( 0 0 1 3 3 4 6 6 7 9 ).
The element-by-element result of the bitwise OR operator| is the
 valarray: ( 1 0 1 3 3 4 7 6 7 9 ).
*\
```

## <a name="op_lor"></a>  operátor&#124;&#124;

Získá logické `OR` mezi odpovídající elementy dva stejně velké valarray – třídy nebo mezi valarray – a zadanou hodnotu valarray – typ elementu.

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

`left` První dva valarray – třídy, jejichž příslušné prvky jsou a nelze jej zkombinovat s logické `OR` nebo zadaná hodnota typu prvku a nelze jej zkombinovat s každý prvek valarray –.

`right` Druhý dva valarray – třídy, jejichž příslušné prvky jsou a nelze jej zkombinovat s logické `OR` nebo zadaná hodnota typu prvku a nelze jej zkombinovat s každý prvek valarray –.

### <a name="return-value"></a>Návratová hodnota

Valarray –, jehož elementy jsou typu `bool` a jsou element-wise kombinace logický provoz nebo `left` a `right`.

### <a name="remarks"></a>Poznámky

Logické `OR` `operator||` se vztahuje na úroveň element počítání všechny nenulové hodnoty jako **true**, a výsledkem je valarray – hodnot logická hodnota. Bitové verzi `OR`, [operátor&#124; ](../standard-library/valarray-operators.md#op_or) naopak může mít za následek valarray – hodnot než 0 nebo 1, v závislosti na výsledek bitové operace.

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
        << "the logical OR operator|| is the\n valarray: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaLOR [ i ] << " ";
   cout << ")." << endl;
}
\* Output:
The initial Left valarray is:  ( 0 0 0 2 0 4 0 6 0 8 ).
The initial Right valarray is: ( 0 0 0 3 0 0 6 0 0 9 ).
The element-by-element result of the logical OR operator|| is the
 valarray: ( 0 0 0 1 0 1 1 1 0 1 ).
*\
```

## <a name="see-also"></a>Viz také

[\<valarray>](../standard-library/valarray.md)<br/>
