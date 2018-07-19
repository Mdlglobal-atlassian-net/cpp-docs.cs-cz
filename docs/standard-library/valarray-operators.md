---
title: '&lt;valarray –&gt; operátory | Dokumentace Microsoftu'
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
ms.openlocfilehash: 0c297ddf24c1ed357a0756c5e0e5631e7b3d1c02
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38964831"
---
# <a name="ltvalarraygt-operators"></a>&lt;valarray –&gt; operátory

||||
|-|-|-|
|[operator!=](#op_neq)|[% – operátor](#op_mod)|[– Operátor&amp;](#op_amp)|
|[– Operátor&amp;&amp;](#op_amp_amp)|[– Operátor&gt;](#op_gt)|[– Operátor&gt;&gt;](#op_gt_gt)|
|[– Operátor&gt;=](#op_gt_eq)|[– Operátor&lt;](#op_lt)|[– Operátor&lt;&lt;](#op_lt_lt)|
|[– Operátor&lt;=](#op_lt_eq)|[Operator *](#op_star)|[Operator +](#op_add)|
|[Operator-](#operator-)|[Operator /](#op_div)|[operator==](#op_eq_eq)|
|[operátor ^](#op_xor)|[– operátor|](#op_or)|[– operátor||](#op_lor)|

## <a name="op_neq"></a>  Operator! =

Testuje, jestli odpovídající prvky dvou stejně velké valarrays nestejné nebo zda jsou všechny prvky valarray – nerovné zadanou hodnotu.

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

*doleva*  
 První dva valarrays, jehož prvky mají být testovány z hlediska nerovnost.

*doprava*  
 Druhé dvě valarrays, jehož prvky mají být testovány z hlediska nerovnost.

### <a name="return-value"></a>Návratová hodnota

Valarray z logické hodnoty, z nichž každý je:

- **Hodnota TRUE** Pokud odpovídající prvky nerovnost.

- **false** Pokud odpovídající prvky nejsou.

### <a name="remarks"></a>Poznámky

První šablona operátor vrací objekt třídy [valarray\<bool >](../standard-library/valarray-bool-class.md), každý z jehož prvků `I` je `left[I] != right[I]`.

Druhý operátor šablony jsou uloženy v elementu `I` `left[I] != right`.

Operátor třetí šablony jsou uloženy v elementu `I` `left != right[I]`.

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

Získá zbytek po dělení odpovídající prvky dva stejně velké valarrays nebo rozdělení valarray zadanou hodnotou nebo dělení valarray zadanou hodnotu.

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

*doleva*  
 Hodnota nebo valarray –, který slouží jako podíl na jinou hodnotu, která nebo valarray – je možné rozdělit.

*doprava*  
 Hodnota nebo valarray –, který slouží jako dělitel a, která vydělí jinou hodnotu nebo valarray.

### <a name="return-value"></a>Návratová hodnota

Valarray, jehož prvky jsou element-wise zbytků z *levé* dělený *správné*.

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

## <a name="op_amp"></a>  – Operátor&amp;

Získá bitový **a** mezi odpovídající prvky dvou valarrays stejně velké nebo valarray a určitou hodnotu na typ prvku.

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

*doleva*  
 První dva valarrays jehož příslušné prvky mají být kombinované pomocí bitového `AND` nebo hodnotu zadaného typu prvku a nelze jej zkombinovat bitovým operátorem pomocí každý prvek valarray.

*doprava*  
 Druhé dvě valarrays jehož příslušné prvky mají být kombinované pomocí bitového `AND` nebo hodnotu zadaného typu prvku a nelze jej zkombinovat bitovým operátorem pomocí každý prvek valarray.

### <a name="return-value"></a>Návratová hodnota

Valarray, jehož prvky jsou element-wise kombinací bitové operace AND z *levé* a *správné*.

### <a name="remarks"></a>Poznámky

Bitová operace jde použít jenom k manipulaci s bity v **char** a **int** datových typů a variant a ne v **float**, **double**, **longdouble**, **void**, **bool** nebo jiné, komplexnější datové typy.

Bitový `AND` má stejné tabulky pravdivých informací jako logický `AND` ale platí pro typ dat na úrovni jednotlivých bitů. [Operator & &](../standard-library/valarray-operators.md#amp) se vztahuje na úroveň element počítání všechny nenulové hodnoty jako true a výsledek je valarray z logické hodnoty. Bitový **ANDoperator &**, naopak může vést k valarray hodnot než 0 nebo 1, v závislosti na výsledcích bitová operace.

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

## <a name="op_amp_amp"></a>  – Operátor&amp;&amp;

Získá logickou **a** mezi odpovídající prvky dvou valarrays stejně velké nebo valarray a určitou hodnotu valarray element typu.

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

*doleva*  
 První dva valarrays jehož příslušné prvky mají být spojeny s logickou `AND` nebo hodnotu zadaného typu prvku a nelze jej zkombinovat s každý prvek valarray.

*doprava*  
 Druhé dvě valarrays jehož příslušné prvky mají být spojeny s logickou `AND` nebo hodnotu zadaného typu prvku a nelze jej zkombinovat s každý prvek valarray.

### <a name="return-value"></a>Návratová hodnota

Valarray –, jehož prvky jsou z typu bool a element-wise kombinace logické `AND` fungování *levé* a *správné*.

### <a name="remarks"></a>Poznámky

Logický `ANDoperator&&` se vztahuje na úroveň element počítání všechny nenulové hodnoty jako true a výsledek je valarray z logické hodnoty. Bitové verzi `AND`, [operátor &,](../standard-library/valarray-operators.md#op_amp), naopak může vést k valarray hodnot než 0 nebo 1, v závislosti na výsledcích bitová operace.

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

## <a name="op_gt"></a>  – Operátor&gt;

Ověřuje, zda prvky jeden valarray jsou větší než prvků stejně velké valarray nebo zda jsou všechny prvky valarray větší nebo menší než zadanou hodnotou.

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

*doleva*  
 První dva valarrays, jehož prvky mají být porovnány nebo zadanou hodnotu k porovnání s každý prvek valarray.

*doprava*  
 Druhé dvě valarrays, jehož prvky mají být porovnány nebo zadanou hodnotu k porovnání s každý prvek valarray.

### <a name="return-value"></a>Návratová hodnota

Valarray z logické hodnoty, z nichž každý je:

- **Hodnota TRUE** Pokud *levé* je větší než odpovídající element nebo hodnota *správné* element nebo hodnota.

- **false** Pokud *levé* není větší než odpovídající element nebo hodnota *správné* element nebo hodnotu.

### <a name="remarks"></a>Poznámky

Pokud se nerovná počtu prvků v dvě valarrays výsledek není definován.

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

## <a name="op_gt_eq"></a>  – Operátor&gt;=

Ověřuje, zda jsou elementy jeden valarray větší než nebo rovna hodnotě prvky stejně velké valarray nebo určuje, zda všechny prvky valarray jsou větší než nebo rovno nebo menší než nebo rovna zadané hodnotě.

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

*doleva*  
 První dva valarrays, jehož prvky mají být porovnány nebo zadanou hodnotu k porovnání s každý prvek valarray.

*doprava*  
 Druhé dvě valarrays, jehož prvky mají být porovnány nebo zadanou hodnotu k porovnání s každý prvek valarray.

### <a name="return-value"></a>Návratová hodnota

Valarray z logické hodnoty, z nichž každý je:

- **true** Pokud *levé* element nebo hodnota je větší než nebo rovno odpovídající *správné* element nebo hodnotu.

- **false** Pokud *levé* element nebo hodnota je menší než odpovídající *správné* element nebo hodnotu.

### <a name="remarks"></a>Poznámky

Pokud se nerovná počtu prvků v dvě valarrays výsledek není definován.

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

## <a name="op_gt_gt"></a>  – Operátor&gt;&gt;

Posuny doprava bity pro každý prvek valarray zadaný počet pozic, nebo částku element-wise určené druhý valarray.

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

*doleva*  
 Hodnota posunutí nebo valarray, jehož prvky mají být změněn.

*doprava*  
 Hodnota udávající dobu posunutí doprava nebo valarray jejíž prvky označovat element-wise množství posunutí doprava.

### <a name="return-value"></a>Návratová hodnota

Valarray –, jehož prvky mají posunuta doprava podle zadaného množství.

### <a name="remarks"></a>Poznámky

Čísla se znaménkem mají jejich znaménka zachovány.

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

## <a name="op_lt"></a>  – Operátor&lt;

Ověřuje, zda prvky valarray – jeden je menší než prvky stejně velké valarray nebo zda jsou všechny prvky valarray větší nebo menší než zadanou hodnotou.

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

*doleva*  
 První dva valarrays, jehož prvky mají být porovnány nebo zadanou hodnotu k porovnání s každý prvek valarray.

*doprava*  
 Druhé dvě valarrays, jehož prvky mají být porovnány nebo zadanou hodnotu k porovnání s každý prvek valarray.

### <a name="return-value"></a>Návratová hodnota

Valarray z logické hodnoty, z nichž každý je:

- **true** Pokud *levé* element nebo hodnota je menší než odpovídající *správné* element nebo hodnotu.

- **false** Pokud *levé* element nebo hodnota není menší než odpovídající *správné* element nebo hodnotu.

### <a name="remarks"></a>Poznámky

Pokud počet valarrays dva elementy se nerovná, výsledek není definován.

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

## <a name="op_lt_eq"></a>  – Operátor&lt;=

Testuje, jestli prvky jeden valarray jsou menší než nebo rovna hodnotě elementy stejně velké valarray nebo zda všechny prvky valarray jsou větší než nebo rovno nebo menší než nebo rovna zadané hodnotě.

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

*doleva*  
 První dva valarrays, jehož prvky mají být porovnány nebo zadanou hodnotu k porovnání s každý prvek valarray.

*doprava*  
 Druhé dvě valarrays, jehož prvky mají být porovnány nebo zadanou hodnotu k porovnání s každý prvek valarray.

### <a name="return-value"></a>Návratová hodnota

Valarray z logické hodnoty, z nichž každý je:

- **true** Pokud *levé* element nebo hodnota je menší než nebo rovno odpovídající *správné* element nebo hodnotu.

- **false** Pokud *levé* je větší než odpovídající element nebo hodnota *správné* element nebo hodnotu.

### <a name="remarks"></a>Poznámky

Pokud počet valarrays dva elementy se nerovná, výsledek není definován.

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

## <a name="op_lt_lt"></a>  – Operátor&lt;&lt;

Vlevo posune bitů pro každý prvek valarray zadaný počet pozic, nebo částku element-wise určené druhý valarray.

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

*doleva*  
 Hodnota posunutí nebo valarray, jehož prvky mají být změněn.

*doprava*  
 Hodnota udávající dobu posunutí doleva nebo valarray jejíž prvky označovat element-wise množství operátor posunu vlevo.

### <a name="return-value"></a>Návratová hodnota

Valarray, jejichž prvky byly posunuty vlevo o zadanou velikost.

### <a name="remarks"></a>Poznámky

Čísla se znaménkem mají jejich znaménka zachovány.

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

## <a name="op_star"></a>  Operator *

Získá produktu mezi odpovídající elementy ve dva stejně velké valarrays nebo mezi valarray zadanou hodnotu.

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

*doleva*  
 První dva valarrays, jehož prvky mají být vynásobené nebo zadanou hodnotou vynásobí každý prvek valarray.

*doprava*  
 Druhé dvě valarrays, jehož prvky mají být vynásobené nebo zadanou hodnotou vynásobí každý prvek valarray.

### <a name="return-value"></a>Návratová hodnota

Valarray, jehož prvky jsou produktu z *levé* a *správné*.

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

## <a name="op_add"></a>  Operator +

Získá element-wise součet mezi odpovídající elementy ve dva stejně velké valarrays nebo mezi valarray zadanou hodnotu.

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

*doleva*  
 První dva valarrays, jehož prvky mají být přidány nebo zadanou hodnotou přidat ke každému elementu valarray.

*doprava*  
 Druhé dvě valarrays, jehož prvky mají být přidány nebo zadanou hodnotou přidat ke každému elementu valarray.

### <a name="return-value"></a>Návratová hodnota

Valarray, jehož prvky jsou element-wise součet z *levé* a *správné*.

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

## <a name="operator-"></a>  Operator-

Získá element-wise rozdíl mezi odpovídající elementy ve dva stejně velké valarrays nebo mezi valarray zadanou hodnotu.

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

*doleva*  
 Hodnota nebo valarray –, který slouží jako minuend, ze kterého jiných hodnot nebo valarrays se bude odečítat v které tvoří rozdíl.

*doprava*  
 Hodnota nebo valarray –, který slouží jako, který se bude odečítat od jiných hodnot nebo valarrays v které tvoří rozdíl menšitel.

### <a name="return-value"></a>Návratová hodnota

Valarray, jehož prvky jsou element-wise rozdíl z *levé* a *správné*.

### <a name="remarks"></a>Poznámky

Aritmetické terminologii používané v popisující odčítání:

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

## <a name="op_div"></a>  Operator /

Získá element-wise podíl mezi odpovídající elementy ve dva stejně velké valarrays nebo mezi valarray zadanou hodnotu.

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

*doleva*  
 Hodnota nebo valarray –, který slouží jako podíl na jinou hodnotu, která nebo valarray – je možné rozdělit do tvořící podíl.

*doprava*  
 Hodnota nebo valarray –, který slouží jako dělitel a, která vydělí jinou hodnotu nebo valarray v tvořící podíl.

### <a name="return-value"></a>Návratová hodnota

Valarray, jehož prvky jsou element-wise podíl z *levé* dělený *správné*.

### <a name="remarks"></a>Poznámky

Aritmetické terminologii používané v popisující dělení:

podíl = Delenec / Delitel

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

Testy, zda odpovídající prvky dvou stejně velké valarrays se rovná nebo zda jsou všechny prvky valarray roven zadané hodnotě.

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

*doleva*  
 První dva valarrays, jehož prvky mají být testovány z hlediska rovnosti.

*doprava*  
 Druhé dvě valarrays, jehož prvky mají být testovány z hlediska rovnosti.

### <a name="return-value"></a>Návratová hodnota

Valarray z logické hodnoty, z nichž každý je:

- **Hodnota TRUE** Pokud odpovídající prvky jsou stejné.

- **false** Pokud odpovídající prvky nejsou stejné.

### <a name="remarks"></a>Poznámky

První šablona operátor vrací objekt třídy [valarray\<bool >](../standard-library/valarray-bool-class.md), každý z jehož prvků `I` je `left[I] == right[I]`. Druhý operátor šablony jsou uloženy v elementu `I` `left[I] == right`. Operátor třetí šablony jsou uloženy v elementu `I` `left == right[I]`.

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

## <a name="op_xor"></a>  operátor ^

Získá bitový exkluzivní `OR` ( **XOR**) mezi odpovídající prvky dvou valarrays stejně velké nebo valarray a určitou hodnotu na typ prvku.

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

*doleva*  
 První dva valarrays jehož příslušné prvky mají být kombinované pomocí bitového **XOR** nebo hodnotu zadaného typu prvku a nelze jej zkombinovat bitovým operátorem pomocí každý prvek valarray.

*doprava*  
 Druhé dvě valarrays jehož příslušné prvky mají být kombinované pomocí bitového **XOR** nebo hodnotu zadaného typu prvku a nelze jej zkombinovat bitovým operátorem pomocí každý prvek valarray.

### <a name="return-value"></a>Návratová hodnota

Valarray, jehož prvky jsou element-wise kombinaci bitového **XOR** fungování *levé* a *správné*.

### <a name="remarks"></a>Poznámky

Bitová operace jde použít jenom k manipulaci s bity v **char** a **int** datových typů a variant a ne v **float**, **double**, **long double**, **void**, **bool** nebo jiné, komplexnější datové typy.

Bitový exkluzivní `OR` ( **XOR**) tuto sémantiku: Zadaný bits *b*1 a *b*2, *b*1  **XOR** *b*2 je **true** Pokud právě jeden z bitů je true. **false** pokud obě bity jsou false nebo pokud jsou splněny obě bits.

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

## <a name="op_or"></a>  – operátor&#124;

Získá bitový `OR` mezi odpovídající prvky dvou valarrays stejně velké nebo valarray a určitou hodnotu na typ prvku.

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

*doleva*  
 První dva valarrays jehož příslušné prvky mají být kombinované pomocí bitového `OR` nebo hodnotu zadaného typu prvku a nelze jej zkombinovat bitovým operátorem pomocí každý prvek valarray.

*doprava*  
 Druhé dvě valarrays jehož příslušné prvky mají být kombinované pomocí bitového `OR` nebo hodnotu zadaného typu prvku a nelze jej zkombinovat bitovým operátorem pomocí každý prvek valarray.

### <a name="return-value"></a>Návratová hodnota

Valarray, jehož prvky jsou element-wise kombinaci bitového `OR` fungování *levé* a *správné*.

### <a name="remarks"></a>Poznámky

Bitová operace jde použít jenom k manipulaci s bity v **char** a **int** datových typů a variant a ne v **float**, **double**, **longdouble**, **void**, **bool** nebo jiné, komplexnější datové typy.

Bitový operátor OR má stejné tabulky pravdivých informací jako logický `OR`, ale platí pro typ dat na úrovni jednotlivých bitů. Zadaný bits *b*1 a *b*2, *b*1 `OR` *b*2 je **true** pokud alespoň jedna z bitů Hodnota TRUE nebo **false** Pokud jsou obě bitů hodnotu false. Logický `OR` [operátor&#124; &#124; ](../standard-library/valarray-operators.md#op_lor) se vztahuje na úrovni prvku, počítací všechny nenulové hodnoty jako **true**, a výsledek je valarray z logické hodnoty. Bitový operátor OR `operator|`, naopak může vést k valarray hodnot než 0 nebo 1, v závislosti na výsledcích bitová operace.

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

## <a name="op_lor"></a>  – operátor&#124;&#124;

Získá logickou `OR` mezi odpovídající prvky dvou valarrays stejně velké nebo valarray a určitou hodnotu na typ prvku valarray.

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

*doleva*  
 První dva valarrays jehož příslušné prvky mají být spojeny s logickou `OR` nebo hodnotu zadaného typu prvku a nelze jej zkombinovat s každý prvek valarray.

*doprava*  
 Druhé dvě valarrays jehož příslušné prvky mají být spojeny s logickou `OR` nebo hodnotu zadaného typu prvku a nelze jej zkombinovat s každý prvek valarray.

### <a name="return-value"></a>Návratová hodnota

Valarray, jehož prvky jsou typu **bool** a element-wise kombinace logické operace OR *levé* a *správné*.

### <a name="remarks"></a>Poznámky

Logický `OR` `operator||` se vztahuje na úrovni prvku, počítací všechny nenulové hodnoty jako **true**, a výsledek je valarray z logické hodnoty. Bitové verzi `OR`, [operátor&#124; ](../standard-library/valarray-operators.md#op_or) naopak může vést k valarray hodnot než 0 nebo 1, v závislosti na výsledcích bitová operace.

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

## <a name="see-also"></a>Viz také:

[\<valarray>](../standard-library/valarray.md)<br/>
