---
title: valarray – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 02bd6b1c5ed9cf29b87dc2a218f7a5e9eda3e3dc
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44319055"
---
# <a name="valarray-class"></a>valarray – třída

Třída šablony popisuje objekt, který řídí sekvence elementů typu `Type` , které jsou uloženy jako pole, pro provádění vysokorychlostní matematických operací navržené a optimalizované pro výpočetní výkon.

## <a name="remarks"></a>Poznámky

Třída je reprezentace matematické konceptu uspořádanou sadu hodnot a prvky jsou číslována od nuly. Třída je popsán jako kontejner téměř protože podporuje některé, ale ne všechny funkce, který prvotřídní pořadí kontejnery, jako například [vektoru](../standard-library/vector-class.md), podporují. Se liší od šablony třídy vektoru dvěma důležitými způsoby:

- Definuje mnoho aritmetické operace mezi odpovídající prvky `valarray<Type>` objekty stejného typu a délky, jako například *xarr* = cos ( *Yarr v jazyce*) + sin ( *zarr*).

- Definuje různé mnoha zajímavými způsoby dolní index `valarray<Type>` objekt přetěžováním [operátor&#91;&#93;](#op_at).

Objekt třídy `Type`:

- Nemá veřejný výchozí konstruktor, destruktor, kopírovací konstruktor a operátor přiřazení s konvenčním chování.

- Definuje aritmetické operátory a matematické funkce, podle potřeby, které jsou definovány pro typy s plovoucí desetinnou čárkou, s konvenčním chování.

Konkrétně se žádné lišila mohou existovat mezi konstrukci kopie a výchozí konstrukce, za nímž následuje přiřazení. Žádná z operací u objektů třídy `Type` může vyvolat výjimky.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[valarray –](#valarray)|Vytvoří `valarray` určité velikosti nebo s elementy s konkrétní hodnotou nebo jako kopii jiného `valarray` nebo podsady jiné `valarray`.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[value_type](#value_type)|Typ, který představuje typ prvků uložených v `valarray`.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[Použít](#apply)|Použije zadanou funkci na každý prvek `valarray`.|
|[cshift –](#cshift)|Cyklicky přesouvá všechny prvky `valarray` zadaný počet pozic.|
|[free](#free)|Uvolní paměť používanou `valarray`.|
|[max](#max)|Vyhledá největšího prvku ve `valarray`.|
|[min](#min)|Vyhledá nejnižší prvek v `valarray`.|
|[Změna velikosti](#resize)|Počet prvků v změní `valarray` na zadané číslo, přidání nebo odebrání prvků podle potřeby.|
|[SHIFT](#shift)|Posune všechny prvky `valarray` zadaný počet pozic.|
|[Velikost](#size)|Zjistí počet prvků v `valarray`.|
|[Součet](#sum)|Určuje součet všech prvků v `valarray` nenulovou délkou.|
|[Prohození](#swap)||

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operátor!](#op_not)|Unární operátor, který získá logické `NOT` hodnoty každého prvku `valarray`.|
|[operator%=](#op_mod_eq)|Získá zbytek po dělení element-wise prvků pole, buď pomocí zadaného `valarray` nebo podle hodnoty typu elementu.|
|[operátor & =](#op_amp_eq)|Získá bitový `AND` prvků v poli buď pomocí odpovídajících prvků v zadané `valarray` nebo s hodnotou typu elementu.|
|[operátor >> =](#op_gt_gt_eq)|Vpravo staffhubu bity pro každý prvek z `valarray` zadaný počet pozic, nebo částku element-wise určené Druhý operand `valarray`.|
|[operátor << =](#op_lt_lt_eq)|Vlevo staffhubu bity pro každý prvek z `valarray` zadaný počet pozic, nebo částku element-wise určené Druhý operand `valarray`.|
|[Operator * =](#op_star_eq)|Vynásobí prvky zadaného `valarray` nebo hodnota typu prvku element-wise operandem `valarray`.|
|[Operator +](#op_add)|Unární operátor, který se vztahuje na každý prvek v plus `valarray`.|
|[operator+=](#op_add_eq)|Přidá prvky zadaného `valarray` nebo hodnota typu prvku element-wise operandem `valarray`.|
|[Operator-](#operator-)|Unární operátor, který se vztahuje na každý prvek v minus `valarray`.|
|[operátor-=](#operator-_eq)|Odečte prvky zadaného `valarray` nebo hodnota typu prvku element-wise z operand `valarray`.|
|[/ = – operátor](#op_div_eq)|Vydělí operand `valarray` element-wise elementy zadaného `valarray` nebo hodnota typu elementu.|
|[operátor =](#op_eq)|Přiřadí prvků, které mají `valarray` jehož hodnoty jsou specifikované buď přímo, nebo jako součást některých dalších `valarray` , nebo `slice_array`, `gslice_array`, `mask_array`, nebo `indirect_array`.|
|[– operátor&#91;&#93;](#op_at)|Vrátí odkaz na prvek nebo její hodnotu na zadaný index nebo podmnožinu zadané.|
|[operátor ^ =](#op_xor_eq)|Získá element-wise exkluzivní logický or – operátor ( `XOR`) pomocí zadané valarray nebo hodnoty na typ prvku pole.|
|[operator&#124;=](#op_or_eq)|Získá bitový `OR` prvků v poli buď pomocí odpovídajících prvků v zadané `valarray` nebo s hodnotou typu elementu.|
|[operator~](#op_dtor)|Unární operátor, který získá bitový `NOT` hodnoty každého prvku `valarray`.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<valarray – >

**Namespace:** std

## <a name="apply"></a>  valarray::apply

Použije zadanou funkci na každý prvek valarray.

```cpp
valarray<Type> apply(Type _Func(Type)) const;

valarray<Type> apply(Type _Func(constType&)) const;
```

### <a name="parameters"></a>Parametry

*_Func(Type)*<br/>
 Objekt funkce, která se použije na každý prvek operand valarray.

*_Func(const Type&)*<br/>
 Objekt funkce pro const použije na každý prvek operand valarray.

### <a name="return-value"></a>Návratová hodnota

Valarray, jehož prvky mají `_Func` element-wise u elementů operand valarray.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí objekt třídy [valarray](../standard-library/valarray-class.md)**\<typ >**, délky [velikost](#size), každý z jehož prvky *můžu*je `_Func((*this)[I])`.

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
/* Output:
The initial Right valarray is: ( 0 0 -2 3 0 -5 6 0 -8 9 )
The element-by-element result of applying MyApplyFunc to vaR is the
valarray: (  0 0 -4 6 0 -10 12 0 -16 18 )
*/
```

## <a name="cshift"></a>  valarray::cshift

Všechny prvky valarray cyklicky posune zadaný počet pozic.

```cpp
valarray<Type> cshift(int count) const;
```

### <a name="parameters"></a>Parametry

*Počet*  
 Počet míst, které prvky jsou Posunutí vpřed.

### <a name="return-value"></a>Návratová hodnota

Nové valarray, ve kterém jsou všechny prvky přesunuly *počet* pozice cyklicky směrem k začátku valarray, left s ohledem na jejich umístění v operand valarray.

### <a name="remarks"></a>Poznámky

Kladná hodnota *počet* posune cyklicky zbývající prvky *počet* umístí.

Záporná hodnota *počet* posune cyklicky správné prvky *počet* umístí.

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
/* Output:
The operand valarray va1 is: ( 0 1 2 3 4 5 6 7 8 9)
The cyclically shifted valarray va1 is:
va1.cshift (4) = ( 4 5 6 7 8 9 0 1 2 3)
The operand valarray va2 is: ( 10 9 8 7 6 5 4 3 2 1)
The cyclically shifted valarray va2 is:
va2.shift (-4) = ( 4 3 2 1 10 9 8 7 6 5)
*/
```

## <a name="free"></a>  valarray::Free

Uvolní paměť používanou valarray.

```cpp
void free();
```

### <a name="remarks"></a>Poznámky

Tato nestandardní funkce je ekvivalentní k přiřazení prázdný valarray. Příklad:

```cpp
valarray<T> v;
v = valarray<T>();

// equivalent to v.free()
```

## <a name="max"></a>  valarray::max

Vyhledá v valarray největšího prvku.

```cpp
Type max() const;
```

### <a name="return-value"></a>Návratová hodnota

Maximální hodnota elementů v operand valarray.

### <a name="remarks"></a>Poznámky

Členská funkce porovná s použitím hodnoty **operátor\<**  nebo **operátoru >** mezi dvojice elementů třídy `Type`, pro operátory, které je třeba zadat pro element `Type`.

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
/* Output:
The operand valarray is: ( 0 1 8 3 7 5 6 13 2 9 ).
The largest element in the valarray is: 13.
*/
```

## <a name="min"></a>  valarray::min

Vyhledá v valarray nejmenší element.

```cpp
Type min() const;
```

### <a name="return-value"></a>Návratová hodnota

Minimální hodnota elementů v operand valarray.

### <a name="remarks"></a>Poznámky

Členská funkce porovná s použitím hodnoty **operátor\<**  nebo **operátoru >** mezi dvojice elementů třídy `Type`, pro operátory, které je třeba zadat pro element `Type`.

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

## <a name="op_not"></a>  valarray::Operator!

Unární operátor, který získá logické **není** hodnoty každého prvku valarray.

```cpp
valarray<bool> operator!() const;
```

### <a name="return-value"></a>Návratová hodnota

Valarray logické hodnoty, které jsou Negace hodnoty elementů operand valarray.

### <a name="remarks"></a>Poznámky

Logické operace **není** Neguje elementy, protože převede samými nulami do těch, které jsou a považuje všechny nenulové hodnoty jako těch, které jsou a převede je na nulami. Je vrácený valarray logické hodnoty stejné velikosti jako operand valarray.

K dispozici je také bitovou **není**[valarray::operator ~](#op_dtor) , které negují na úrovni jednotlivých bitů v rámci binární reprezentace **char** a **int**  elementy valarray.

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
        << "the logical NOT operator! is the\n valarray: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaNOT [ i ] << " ";
   cout << ")." << endl;
}
/* Output:
The initial valarray is:  ( 0 0 0 2 0 4 0 6 0 8 ).
The element-by-element result of the logical NOT operator! is the
 valarray: ( 1 1 1 0 1 0 1 0 1 0 ).
*/
```

## <a name="op_mod_eq"></a>  valarray::Operator % =

Získá zbytek po dělení prvky pole element-wise zadané valarray nebo hodnotu typu elementu.

```cpp
valarray<Type>& operator%=(const valarray<Type>& right);

valarray<Type>& operator%=(const Type& right);
```

### <a name="parameters"></a>Parametry

*doprava*  
 Valarray – nebo hodnota shodná s valarray operand, který je k rozdělení element-wise, operand valarray typu prvku.

### <a name="return-value"></a>Návratová hodnota

Valarray, jehož prvky jsou zbývající element-wise dělení operand valarray podle *vpravo*

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
        << "division is the\n valarray: ( ";
      for ( i = 0 ; i < 6 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;
}
/* Output:
The initial valarray is: ( 53 -67 53 -67 53 -67 ).
The initial  right valarray is: ( 1 4 7 10 13 16 ).
The remainders from the element-by-element division is the
 valarray: ( 0 -3 4 -7 1 -3 ).
*/
```

## <a name="and_eq"></a>  valarray::Operator&amp;=

Získá bitový **a** prvků v poli s odpovídající prvky v zadané valarray nebo s hodnotou typu elementu.

```cpp
valarray<Type>& operator&=(const valarray<Type>& right);

valarray<Type>& operator&=(const Type& right);
```

### <a name="parameters"></a>Parametry

*doprava*  
 Valarray – nebo hodnota typu prvku shodná s valarray operand, který je možné kombinovat, element-wise podle logického `AND` s operand valarray.

### <a name="return-value"></a>Návratová hodnota

Valarray, jehož prvky jsou element-wise logické `AND` z valarray operand podle *vpravo*

### <a name="remarks"></a>Poznámky

Bitová operace jde použít jenom k manipulaci s bity v **char** a **int** datových typů a variant a ne v **float**, **double**, **longdouble**, **void**, **bool**, nebo jiné, komplexnější datové typy.

Bitový operátor AND má stejné tabulky pravdivých informací jako logický `AND` ale platí pro typ dat na úrovni jednotlivých bitů. Zadaný bits *b*1 a *b*2, *b*1 `AND` *b*2 je **true** pokud platí obě bits; **false** pokud alespoň jednu hodnotu false.

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
        << "the logical AND operator&= is the\n valarray: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;
}
/* Output:
The initial valarray is:  ( 0 0 0 2 0 4 0 6 0 8 ).
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 8 9 ).
The element-by-element result of the logical AND operator&= is the
 valarray: ( 0 0 0 2 0 4 0 6 0 8 ).
*/
```

## <a name="op_gt_gt_eq"></a>  valarray::Operator&gt;&gt;=

Posuny doprava bity pro každý prvek valarray operand zadaný počet pozic, nebo částku element-wise určené druhý valarray.

```cpp
valarray<Type>& operator>>=(const valarray<Type>& right);

valarray<Type>& operator>>=(const Type& right);
```

### <a name="parameters"></a>Parametry

*doprava*  
 Hodnota udávající dobu posunutí doprava nebo valarray jejíž prvky označovat element-wise množství posunutí doprava.

### <a name="return-value"></a>Návratová hodnota

Valarray, jehož prvky mají byla posunuta doprava zadanou v *správné*.

### <a name="remarks"></a>Poznámky

Čísla se znaménkem mají jejich znaménka zachovány.

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
        << "the right shift is the\n valarray: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;
}
/* Output:
The initial operand valarray is: ( 64 -64 64 -64 64 -64 64 -64 ).
The  right valarray is: ( 0 1 2 3 4 5 6 7 ).
The element-by-element result of the right shift is the
 valarray: ( 64 -32 16 -8 4 -2 1 -1 ).
*/
```

## <a name="op_lt_lt_eq"></a>  valarray::Operator&lt;&lt;=

Posune doleva bity pro každý prvek valarray operand zadaný počet pozic, nebo částku element-wise určené druhý valarray.

```cpp
valarray<Type>& operator<<=(const valarray<Type>& right);

valarray<Type>& operator<<=(const Type& right);
```

### <a name="parameters"></a>Parametry

*doprava*  
 Hodnota udávající dobu posunutí doleva nebo valarray jejíž prvky označovat element-wise množství operátor posunu vlevo.

### <a name="return-value"></a>Návratová hodnota

Valarray, jehož prvky mají byla posunuta doleva zadanou v *správné*.

### <a name="remarks"></a>Poznámky

Čísla se znaménkem mají jejich znaménka zachovány.

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
        << "the left shift\n on the operand array is the valarray:\n ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;
}
/* Output:
The initial operand valarray is: ( 1 -1 1 -1 1 -1 1 -1 ).
The  right valarray is: ( 0 1 2 3 4 5 6 7 ).
The element-by-element result of the left shift
 on the operand array is the valarray:
 ( 1 -2 4 -8 16 -32 64 -128 ).
*/
```

## <a name="op_star_eq"></a>  valarray::Operator * =

Vynásobí prvků zadaného valarray nebo hodnotu na typ prvku element-wise, do valarray operand.

```cpp
valarray<Type>& operator*=(const valarray<Type>& right);

valarray<Type>& operator*=(const Type& right);
```

### <a name="parameters"></a>Parametry

*doprava*  
 Valarray – nebo hodnota shodná s valarray operand, který se má vynásobit element-wise, operand valarray je typu prvku.

### <a name="return-value"></a>Návratová hodnota

Valarray, jehož prvky jsou produktu ve operand valarray a *správné*.

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
        << "the multiplication is the\n valarray: ( ";
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

## <a name="op_add"></a>  valarray::Operator +

Unární operátor plus se vztahuje na každý prvek valarray.

```cpp
valarray<Type> operator+() const;
```

### <a name="return-value"></a>Návratová hodnota

Valarray –, jehož prvky jsou navíc u operandu pole.

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
        << "the operator+ is the\n valarray: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaPLUS [ i ] << " ";
   cout << ")." << endl;
}
/* Output:
The initial valarray is:  ( 0 0 -2 2 -4 4 -6 6 -8 8 ).
The element-by-element result of the operator+ is the
 valarray: ( 0 0 -2 2 -4 4 -6 6 -8 8 ).
*/
```

## <a name="op_add_eq"></a>  valarray::Operator +=

Přidá prvky zadané valarray nebo hodnotu na typ prvku element-wise, valarray operand.

```cpp
valarray<Type>& operator+=(const valarray<Type>& right);

valarray<Type>& operator+=(const Type& right);
```

### <a name="parameters"></a>Parametry

*doprava*  
 Valarray – nebo hodnota shodná s valarray operand, který má být přidán element-wise, do operand valarray typu prvku.

### <a name="return-value"></a>Návratová hodnota

Valarray, jehož prvky jsou element-wise součet operand valarray a *správné*.

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
        << "the sum is the\n valarray: ( ";
      for (i = 0 ; i < 8 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;
}
/* Output:
The initial valarray is: ( 2 -1 2 -1 2 -1 2 -1 ).
The initial  right valarray is: ( 0 1 2 3 4 5 6 7 ).
The element-by-element result of the sum is the
 valarray: ( 2 0 4 2 6 4 8 6 ).
*/
```

## <a name="valarray__operator-"></a>  valarray::Operator-

Unární operátor minus se vztahuje na každý prvek valarray.

```cpp
valarray<Type> operator-() const;
```

### <a name="return-value"></a>Návratová hodnota

Valarray –, jehož prvky jsou minus u operandu pole.

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
        << "the operator+ is the\n valarray: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaMINUS [ i ] << " ";
   cout << ")." << endl;
}
/* Output:
The initial valarray is:  ( 0 0 -2 2 -4 4 -6 6 -8 8 ).
The element-by-element result of the operator+ is the
 valarray: ( 0 0 2 -2 4 -4 6 -6 8 -8 ).
*/
```

## <a name="valarray__operator-_eq"></a>  valarray::Operator-=

Odečte prvků zadaného valarray nebo hodnotu na typ prvku element-wise, ze valarray operand.

```cpp
valarray<Type>& operator-=(const valarray<Type>& right);

valarray<Type>& operator-=(const Type& right);
```

### <a name="parameters"></a>Parametry

*doprava*  
 Valarray – nebo hodnota shodná s valarray operand, která se bude odečítat element-wise, od operand valarray typu prvku.

### <a name="return-value"></a>Návratová hodnota

Valarray, jehož prvky jsou element-wise rozdíl operand valarray a *správné*.

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
        << "the difference is the\n valarray: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;
}
/* Output:
The initial valarray is: ( 10 0 10 0 10 0 10 0 ).
The initial  right valarray is: ( 0 1 2 3 4 5 6 7 ).
The element-by-element result of the difference is the
 valarray: ( 10 -1 8 -3 6 -5 4 -7 ).
*/
```

## <a name="op_div_eq"></a>  valarray::Operator / =

Vydělí operand valarray element-wise prvků zadaného valarray nebo hodnotu typu elementu.

```cpp
valarray<Type>& operator/=(const valarray<Type>& right);

valarray<Type>& operator/=(const Type& right);
```

### <a name="parameters"></a>Parametry

*doprava*  
 Valarray – nebo hodnota shodná s valarray operand, který je možné rozdělit element-wise, do operand valarray typu prvku.

### <a name="return-value"></a>Návratová hodnota

Valarray, jehož prvky jsou element-wise podíl operand valarray dělený *správné*.

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
        << "the quotient is the\n valarray: ( ";
      for (i = 0 ; i < 6 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;
}
/* Output:
The initial valarray is: ( 100 -100 100 -100 100 -100 ).
The initial Right valarray is: ( 0 2 4 6 8 10 ).
The element-by-element result of the quotient is the
 valarray: ( inf -50 25 -16.6667 12.5 -10 ).
*/
```

## <a name="op_eq"></a>  valarray::Operator =

Valarray, jejichž hodnoty jsou specifikované buď přímo, nebo jako součást některých valarray nebo slice_array –, gslice_array –, mask_array – nebo indirect_array – přiřadí elementy.

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

*doprava*  
 Valarray – které se mají zkopírovat do operand valarray.

*Val*  
 Hodnota má být přiřazena k elementům operand valarray.

*_Slicearray*  
 Slice_array – které se mají zkopírovat do operand valarray.

*_Gslicearray*  
 Gslice_array – které se mají zkopírovat do operand valarray.

*_Maskarray*  
 Mask_array – které se mají zkopírovat do operand valarray.

*_Indarray*  
 Indirect_array – které se mají zkopírovat do operand valarray.

### <a name="return-value"></a>Návratová hodnota

První členský operátor nahradí kopii sekvence řízenou parametrem řízené sekvence *správné*.

Druhý operátor členu je stejný jako první, ale s [Rvalue Reference Declarator: & &](../cpp/rvalue-reference-declarator-amp-amp.md).

Třetí členský operátor nahradí kopii všech prvků objektu řízené sekvence *val*.

Zbývající operátory členů nahradit tyto prvky řízené sekvence ve své argumenty, které jsou generovány pouze vybrané [operátor&#91;&#93;](#op_at).

Pokud hodnota člena v náhradní řízené sekvence závisí na člen v počáteční řízenou sekvenci, výsledek není definován.

### <a name="remarks"></a>Poznámky

Pokud se změní délka řízenou sekvenci, výsledek není obecně definován. V této implementaci efekt je však pouze zneplatnit všechny ukazatele nebo odkazy na prvky řízené sekvence.

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
/* Output:
The operand valarray va is: 0 1 2 3 4 5 6 7 8 9
The operand valarray vaR is: 10 9 8 7 6 5 4 3 2 1
The reassigned valarray va is: 10 9 8 7 6 5 4 3 2 1
The reassigned valarray va is: 10 10 10 10 10 10 10 10 10 10
*/
```

## <a name="op_at"></a>  valarray::Operator]

Vrátí odkaz na prvek nebo její hodnotu na zadaný index nebo podmnožinu zadané.

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

*_Off*  
 Index prvku, který chcete přiřadit hodnotu.

*_Slicearray*  
 Slice_array – z valarray –, který určuje podmnožinu vybrali, nebo se vrátí do nové valarray.

*_Gslicearray*  
 Gslice_array – z valarray –, který určuje podmnožinu vybrali, nebo se vrátí do nové valarray.

*_Boolarray*  
 Bool_array valarray –, který určuje podmnožinu vybrali, nebo se vrátí do nové valarray.

*_Indarray*  
 Indirect_array – valarray –, který určuje podmnožinu vybrali, nebo se vrátí do nové valarray.

### <a name="return-value"></a>Návratová hodnota

Odkaz na prvek nebo její hodnotu na zadaný index nebo podmnožinu zadané.

### <a name="remarks"></a>Poznámky

Členský operátor je přetížena pro poskytuje několik způsobů, jak vybrat pořadí prvků z těch řídí  <strong>\*to</strong>. První skupina operátorů členské pět fungování ve spojení s různými přetížení [operátoru =](#op_eq) (a ostatní operátory přiřazení) umožňuje selektivní nahrazení (dělení) řízené sekvence. Vybrané elementy musí existovat.

Při kompilaci pomocí [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) definováno jako 1 nebo 2, Chyba za běhu dochází, pokud se pokusíte o přístup k prvku mimo hranice valarray.  Zobrazit [Checked Iterators](../standard-library/checked-iterators.md) Další informace.

### <a name="example"></a>Příklad

Podívejte se na příklady pro [slice::slice](../standard-library/slice-class.md#slice) a [gslice::gslice](../standard-library/gslice-class.md#gslice) příklad toho, jak deklarovat a použijte operátor.

## <a name="op_xor_eq"></a>  valarray::Operator ^ =

Získá element-wise exkluzivní logický or – operátor ( **XOR**) pomocí zadané valarray nebo hodnoty na typ prvku pole.

```cpp
valarray<Type>& operator|=(const valarray<Type>& right);

valarray<Type>& operator|=(const Type& right);
```

### <a name="parameters"></a>Parametry

*doprava*  
 Valarray – nebo hodnota typu prvku shodná s valarray operand, který je možné kombinovat, element-wise logické exkluzivní **XOR** s operand valarray.

### <a name="return-value"></a>Návratová hodnota

Valarray, jehož prvky jsou logické element-wise, exkluzivní **XOR** z operand valarray a *správné*.

### <a name="remarks"></a>Poznámky

Exkluzivní logické, nebo jen **XOR**, tuto sémantiku: uvedeny prvky *e*1 a *e*2, *e*1  **XOR** *e*2 je **true** Pokud přesně jeden z elementů je true. **false** Pokud oba prvky jsou false nebo pokud jsou pravdivé oba prvky.

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
        << "the bitwise XOR operator^= is the\n valarray: ( ";
      for (i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;
}
/* Output:
The initial operand valarray is:  ( 1 0 1 0 1 0 1 0 1 0 ).
The  right valarray is: ( 0 0 1 3 3 4 6 6 7 9 ).
The element-by-element result of the bitwise XOR operator^= is the
 valarray: ( 1 0 0 3 2 4 7 6 6 9 ).
*/
```

## <a name="op_or_eq"></a>  valarray::Operator&#124;=

Získá bitový `OR` prvků v poli s odpovídající prvky v zadané valarray nebo s hodnotou typu elementu.

```cpp
valarray<Type>& operator|=(const valarray<Type>& right);

valarray<Type>& operator|=(const Type& right);
```

### <a name="parameters"></a>Parametry

*doprava*  
 Valarray – nebo hodnota typu prvku shodná s valarray operand, který je možné kombinovat, element-wise pomocí bitového `OR` s operand valarray.

### <a name="return-value"></a>Návratová hodnota

Valarray, jehož prvky jsou element-wise bitový `OR` z valarray operand podle *správné*.

### <a name="remarks"></a>Poznámky

Bitová operace jde použít jenom k manipulaci s bity v **char** a **int** datových typů a variant a ne v **float**, **double**, **longdouble**, **void**, **bool**, nebo jiné, komplexnější datové typy.

Bitový `OR` má stejné tabulky pravdivých informací jako logický `OR` ale platí pro typ dat na úrovni jednotlivých bitů. Zadaný bits *b*1 a *b*2, *b*1 `OR` *b*2 je **true** pokud alespoň jedna z bitů Hodnota TRUE; **false** Pokud jsou obě bitů hodnotu false.

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

   cout << "The initial operand valarray is:\n ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The  right valarray is:\n ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaL |= vaR;
   cout << "The element-by-element result of "
        << "the logical OR\n operator|= is the valarray:\n ( ";
      for (i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;
}
/* Output:
The initial operand valarray is:
 ( 1 0 1 0 1 0 1 0 1 0 ).
The  right valarray is:
 ( 0 0 1 3 3 4 6 6 7 9 ).
The element-by-element result of the logical OR
 operator|= is the valarray:
 ( 1 0 1 3 3 4 7 6 7 9 ).
*/
```

## <a name="op_dtor"></a>  valarray::Operator ~

Unární operátor, který získá bitový `NOT` hodnoty každého prvku valarray.

```cpp
valarray<Type> operator~() const;
```

### <a name="return-value"></a>Návratová hodnota

Valarray logické hodnoty, které jsou bitový `NOT` element hodnot operand valarray.

### <a name="remarks"></a>Poznámky

Bitová operace jde použít jenom k manipulaci s bity v **char** a **int** datových typů a variant a ne v **float**, **double**, **longdouble**, **void**, **bool** nebo jiné, komplexnější datové typy.

Bitový `NOT` má stejné tabulky pravdivých informací jako logický `NOT` ale platí pro typ dat na úrovni jednotlivých bitů. Zadaný bit *b*, ~ *b* má hodnotu true Pokud *b* má hodnotu false a false v případě *b* má hodnotu true. Logický **není**[operátor!](#op_not) se vztahuje na úrovni prvku, počítací všechny nenulové hodnoty jako **true**, a výsledek je valarray z logické hodnoty. Bitový `NOToperator~`, naopak může vést k valarray hodnot než 0 nebo 1, v závislosti na výsledcích bitová operace.

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
        << "the bitwise NOT operator~ is the\n valarray: ( ";
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
        << "the bitwise NOT operator~ is the\n valarray: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaNOT2 [ i ] << " ";
   cout << ")." << endl;

   // The negative numbers are represented using
   // the two's complement approach, so adding one
   // to the flipped bits returns the negative elements
   vaNOT2 = vaNOT2 + 1;
   cout << "The element-by-element result of "
        << "adding one\n is the negative of the "
        << "original elements the\n valarray: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaNOT2 [ i ] << " ";
   cout << ")." << endl;
}

/* Output:
The initial valarray <unsigned short int> is:  ( 0 5 2 15 4 25 6 35 8 45 ).
The element-by-element result of the bitwise NOT operator~ is the
 valarray: ( 65535 65530 65533 65520 65531 65510 65529 65500 65527 65490 ).

The initial valarray <int> is:  ( 0 -2 2 -6 4 -10 6 -14 8 -18 ).
The element-by-element result of the bitwise NOT operator~ is the
 valarray: ( -1 1 -3 5 -5 9 -7 13 -9 17 ).
The element-by-element result of adding one
 is the negative of the original elements the
 valarray: ( 0 2 -2 6 -4 10 -6 14 -8 18 ).
*/
```

## <a name="resize"></a>  valarray::Resize

Počet prvků v valarray změní na zadané číslo.

```cpp
void resize(
    size_t _Newsize);

void resize(
    size_t _Newsize,
    const Type val);
```

### <a name="parameters"></a>Parametry

*_Newsize*  
 Počet prvků v změněnou valarray.

*Val*  
 Hodnota má být poskytnut na elementy jehož velikost byla změněna valarray.

### <a name="remarks"></a>Poznámky

První členská funkce inicializuje prvky s jejich výchozí konstruktor.

Nejsou zneplatněny žádné ukazatele nebo odkazy na prvky řízené sekvence.

### <a name="example"></a>Příklad

Následující příklad ukazuje použití valarray::resize členskou funkci.

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

## <a name="shift"></a>  valarray::SHIFT

Všechny prvky valarray posune zadaný počet míst.

```cpp
valarray<Type> shift(int count) const;
```

### <a name="parameters"></a>Parametry

*Počet*  
 Počet míst, které prvky jsou Posunutí vpřed.

### <a name="return-value"></a>Návratová hodnota

Nové valarray, ve kterém jsou všechny prvky přesunuly *počet* pozice směrem k začátku valarray, left s ohledem na jejich umístění v operand valarray.

### <a name="remarks"></a>Poznámky

Kladná hodnota *počet* posune elementy vlevo *počet* umístí s nulovou výplně.

Záporná hodnota *počet* posune elementy vpravo *počet* umístí s nulovou výplně.

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
/* Output:
The operand valarray va1(10) is: ( 0 1 2 3 4 5 6 7 8 9 ).
The shifted valarray va1 is: va1.shift (4) = ( 4 5 6 7 8 9 0 0 0 0 ).
The operand valarray va2(10) is: ( 10 9 8 7 6 5 4 3 2 1 ).
The shifted valarray va2 is: va2.shift (-4) = ( 0 0 0 0 10 9 8 7 6 5 ).
*/
```

## <a name="size"></a>  valarray::size

Počet prvků, které najde v valarray.

```cpp
size_t size() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet prvků v operand valarray.

### <a name="example"></a>Příklad

Následující příklad ukazuje použití valarray::size členskou funkci.

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
    cout << "After initializing two more elements,\n "
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

## <a name="sum"></a>  valarray::Sum

Určuje součet všech prvků v valarray nenulovou délkou.

```cpp
Type sum() const;
```

### <a name="return-value"></a>Návratová hodnota

Součet prvků operand valarray.

### <a name="remarks"></a>Poznámky

Pokud je větší než jedna délka, členská funkce přidá hodnoty součtem použitím `operator+=` mezi dvojice elementů třídy `Type`, operátoru, v důsledku toho musí být k dispozici pro prvky typu `Type`.

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
/* Output:
The operand valarray va (10) is: ( 0 1 2 3 4 5 6 7 8 9 ).
The sum of elements in the valarray is: 45.
*/
```

## <a name="swap"></a>  valarray::swap

Vymění prvky dvou `valarray`s.

```cpp
void swap(valarray& right);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*doprava*|A `valarray` poskytující prvky pro záměnu.|

### <a name="remarks"></a>Poznámky

Členská funkce Zamění řízené sekvence mezi `*this` a *správné*. Provádí se v konstantním času, nevyvolává žádné výjimky a zneplatní žádné odkazy, ukazatele nebo iterátory, které určují prvky v dané dvě řízené sekvence.

## <a name="valarray"></a>  valarray::valarray

Valarray – určité velikosti nebo s elementy s konkrétní hodnotu nebo jako kopii jiného valarray nebo podmnožinou jiné valarray vytvoří.

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

*Počet*  
 Počet prvků, které mají být v valarray.

*Val*  
 Hodnota se použije při inicializaci prvků v valarray.

*PTR*  
 Ukazatele na hodnoty, které se použijí k inicializaci prvků v valarray.

*doprava*  
 Existující valarray – inicializace nového valarray.

*SliceArray*  
 Slice_array –, jejichž hodnoty prvků se mají použít při inicializaci prvků valarray vytváří.

*GsliceArray*  
 Gslice_array –, jejichž hodnoty prvků se mají použít při inicializaci prvků valarray vytváří.

*MaskArray*  
 Mask_array –, jejichž hodnoty prvků se mají použít při inicializaci prvků valarray vytváří.

*IndArray*  
 Indirect_array –, jejichž hodnoty prvků se mají použít při inicializaci prvků valarray vytváří.

*IList*  
 Objekt initializer_list obsahující prvky ke zkopírování.

### <a name="remarks"></a>Poznámky

První (výchozí) konstruktor inicializuje objekt, který má prázdné pole. Následující tři konstruktory inicializují objekt na pole *počet* prvky následujícím způsobem:

- Pro explicitní `valarray(size_t Count)`, každý element je inicializovaná s konstruktorem default.

- Pro `valarray(const Type& Val, Count)`, každý element je inicializována s *Val*.

- Pro `valarray(const Type* Ptr, Count)`, prvek na pozici `I` je inicializována s `Ptr`[ `I`].

Každý zbývající konstruktor inicializuje objekt, který má valarray\<typ > objekt určené dílčí zadané v argumentu.

Poslední konstruktor je stejný jako vedle poslední v, ale s [Rvalue Reference Declarator: & &](../cpp/rvalue-reference-declarator-amp-amp.md).

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

    cout << "The new valarray initialized from the slice is vaSlice ="
        << "\nva[slice( 2, 4, 3)] = (";
    for (int i = 0; i < 3; i++) {
        cout << " " << vaSlice[i];
    }
    cout << " )" << endl;

    valarray<int> va2{{ 1, 2, 3, 4 }};
    for (auto& v : va2){
        cout << v << " ";
    }
    cout << endl;
}

```

```Output
The operand valarray va is:( 0 2 2 2 2 2 2 2 2 2 )The new valarray initialized from the slice is vaSlice =va[slice( 2, 4, 3)] = ( 0 0 0 )1 2 3 4
```

## <a name="value_type"></a>  valarray::value_type

Typ, který představuje typ prvků uložených v valarray.

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
/* Output:
The initial operand valarray is:  ( 0 -1 2 -1 4 -1 6 -1 8 -1 ).
The decalared value_type Right is: 10
The resulting valarray is:  ( 0 -10 20 -10 40 -10 60 -10 80 -10 ).
*/
```

## <a name="see-also"></a>Viz také:

[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
