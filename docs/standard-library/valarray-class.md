---
title: valarray – třídy | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
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
caps.latest.revision: 23
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 69a02a47bdf086f75fc617988f44fd67b322255f
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="valarray-class"></a>valarray – třída

Šablony třídy popisuje objekt, který určuje posloupnost elementy typu **typ** které jsou uloženy jako pole, určený pro provádění vysokorychlostní matematické operace a optimalizované pro výpočetní výkon.

## <a name="remarks"></a>Poznámky

Třída je znázornění matematickém konceptu seřazené sady hodnot a elementy jsou číslované od nuly. Třída se označuje jako kontejner blízké, protože některé podporuje, ale ne všechny funkce to prvotřídní pořadí kontejnery, například [vektoru](../standard-library/vector-class.md), podporují. Liší se od vector – třída šablony důležité dvěma způsoby:

- Definuje množství aritmetické operace mezi odpovídající elementy **valarray –\<typ >** objekty stejného typu a délky, například *xarr* = cos ( *Yarr v jazyce*) + sin ( *zarr*).

- Definuje škálu zajímavé způsoby dolní index **valarray –\<typ >** objektu podle přetížení [operátor&#91;&#93;](#op_at).

Třída objektu **typ**:

- Má výchozí veřejný konstruktor, destruktor, kopírovacího konstruktoru a operátor přiřazení s konvenční chování.

- Definuje aritmetické operátory a matematické funkce, podle potřeby, které jsou definovány pro typy s plovoucí desetinnou čárkou, s konvenční chování.

Konkrétně žádné jemně lišit mohou existovat mezi vytváření kopie a výchozí konstrukce, za nímž následuje přiřazení. Žádná z operací u objektů třídy **typ** může vyvolat výjimky.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[valarray –](#valarray)|Vytvoří `valarray` určité velikosti nebo u elementů na konkrétní hodnoty, nebo jako kopii jiného `valarray` nebo některé jiné `valarray`.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[value_type](#value_type)|Typ, který reprezentuje typ elementu uložené v `valarray`.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[Použít](#apply)|Zadaná funkce se vztahuje na jednotlivé prvky `valarray`.|
|[cshift –](#cshift)|Cyklicky posune všechny elementy ve `valarray` o zadaný počet pozic.|
|[free](#free)|Uvolní množství paměti používané `valarray`.|
|[max](#max)|Vyhledá nejvyšší element v `valarray`.|
|[Min.](#min)|Vyhledá nejnižší element v `valarray`.|
|[Změna velikosti](#resize)|Změní počet elementů ve `valarray` na číslo, přidávání nebo odebírání elementů podle potřeby.|
|[Posunutí](#shift)|Posune všechny elementy ve `valarray` o zadaný počet pozic.|
|[Velikost](#size)|Zjistí počet elementů ve `valarray`.|
|[Součet](#sum)|Určuje součet všech elementů v `valarray` délky nenulové hodnoty.|
|[Swap](#swap)||

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[Operator – operátor!](#op_not)|Unární operátor, který získá logické `NOT` hodnoty každého prvku `valarray`.|
|[operator%=](#op_mod_eq)|Získá zbytek po dělení prvků pole element-wise buď zadané `valarray` nebo pomocí hodnoty typu prvku.|
|[operátor & =](#op_amp_eq)|Získá bitové hodnotě `AND` elementů v matici buď pomocí odpovídající elementy v zadané `valarray` nebo s hodnotou typu prvku.|
|[operátor >> =](#op_gt_gt_eq)|Pravé posuny bits pro jednotlivé elementy z `valarray` po zadaný počet pozic nebo o element-wise částku určeného Druhý operand `valarray`.|
|[operátor << =](#op_lt_lt_eq)|Levé posuny bits pro jednotlivé elementy z `valarray` po zadaný počet pozic nebo o element-wise částku určeného Druhý operand `valarray`.|
|[Operator * =](#op_star_eq)|Multiplies – elementy zadané `valarray` nebo hodnota typu prvku element-wise operand `valarray`.|
|[operátor +](#op_add)|Unární operátor, který se vztahuje plus každý prvek v `valarray`.|
|[operator+=](#op_add_eq)|Přidá elementy zadané `valarray` nebo hodnota typu prvku element-wise operand `valarray`.|
|[Operator –](#operator-)|Unární operátor, který se vztahuje minus každý prvek v `valarray`.|
|[-= – operátor](#operator-_eq)|Odečítá od elementy zadané `valarray` nebo hodnota typu prvku element-wise z operand `valarray`.|
|[/ = – operátor](#op_div_eq)|Rozdělí operand `valarray` element-wise podle elementy zadané `valarray` nebo hodnota typu prvku.|
|[operátor =](#op_eq)|Přiřadí elementů `valarray` jejichž hodnoty se zadávají, buď přímo, nebo jako součást jiného `valarray` , nebo `slice_array`, `gslice_array`, `mask_array`, nebo `indirect_array`.|
|[operátor&#91;&#93;](#op_at)|Vrátí odkaz na element nebo má hodnotu na zadaný index nebo podmnožinu zadaný.|
|[Operator ^ =](#op_xor_eq)|Získá element-wise exkluzivní logický operátor or ( `XOR`) z pole s zadaný valarray – nebo hodnota typu prvku.|
|[operator&#124;=](#op_or_eq)|Získá bitové hodnotě `OR` elementů v matici buď pomocí odpovídající elementy v zadané `valarray` nebo s hodnotou typu prvku.|
|[operator~](#op_dtor)|Unární operátor, který získá bitové hodnotě `NOT` hodnoty každého prvku `valarray`.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<valarray – >

**Namespace:** – std

## <a name="apply"></a>  valarray::apply

Zadaná funkce se vztahuje na každý prvek valarray –.

```cpp
valarray<Type> apply(Type _Func(Type)) const;

valarray<Type> apply(Type _Func(constType&)) const;
```

### <a name="parameters"></a>Parametry

*_Func(Type)* objekt funkce, které má být použita pro každý prvek valarray – operand.

*_Func(const Type&)* objekt funkce pro const má být použita pro každý prvek valarray – operand.

### <a name="return-value"></a>Návratová hodnota

Valarray – předtím jehož elementy `_Func` element-wise u elementů valarray – operand.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí objekt třídy [valarray –](../standard-library/valarray-class.md)**\<typ >**, délky [velikost](#size), každý z jehož elementy `I` je **func**((  **\*to**) [ `I`]).

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
\* Output:
The initial Right valarray is: ( 0 0 -2 3 0 -5 6 0 -8 9 )
The element-by-element result of applying MyApplyFunc to vaR is the
valarray: (  0 0 -4 6 0 -10 12 0 -16 18 )
*\
```

## <a name="cshift"></a>  valarray::cshift

Všechny elementy ve valarray – cyklicky posune zadaný počet pozic.

```cpp
valarray<Type> cshift(int count) const;
```

### <a name="parameters"></a>Parametry

`count` Počet míst elementy jsou Posunutí vpřed.

### <a name="return-value"></a>Návratová hodnota

Nové valarray –, ve kterém jsou všechny elementy byly přesunuty `count` pozic cyklicky směrem dopředu valarray –, ponecháno s ohledem na jejich umístění v valarray – operand.

### <a name="remarks"></a>Poznámky

Kladnou hodnotu `count` posune elementy cyklicky vlevo `count` umístí.

Záporná hodnota `count` posune cyklicky správné elementy `count` umístí.

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
\* Output:
The operand valarray va1 is: ( 0 1 2 3 4 5 6 7 8 9)
The cyclically shifted valarray va1 is:
va1.cshift (4) = ( 4 5 6 7 8 9 0 1 2 3)
The operand valarray va2 is: ( 10 9 8 7 6 5 4 3 2 1)
The cyclically shifted valarray va2 is:
va2.shift (-4) = ( 4 3 2 1 10 9 8 7 6 5)
*\
```

## <a name="free"></a>  valarray::Free

Uvolní množství paměti používané valarray –.

```cpp
void free();
```

### <a name="remarks"></a>Poznámky

Tato funkce nestandardní je ekvivalentní k přiřazení prázdný valarray –. Příklad:

```cpp
valarray<T> v;
v = valarray<T>();

// equivalent to v.free()
```

## <a name="max"></a>  valarray::max

Vyhledá nejvyšší element v valarray –.

```cpp
Type max() const;
```

### <a name="return-value"></a>Návratová hodnota

Maximální hodnota elementů v valarray – operand.

### <a name="remarks"></a>Poznámky

Členská funkce porovná hodnoty použitím **operátor\<**  nebo **operátor >** mezi páry elementů třídy **typu**, pro operátory, které musí být zadaná pro element **typu**.

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
\* Output:
The operand valarray is: ( 0 1 8 3 7 5 6 13 2 9 ).
The largest element in the valarray is: 13.
*\
```

## <a name="min"></a>  valarray::min

Vyhledá nejnižší element v valarray –.

```cpp
Type min() const;
```

### <a name="return-value"></a>Návratová hodnota

Minimální hodnota elementů v valarray – operand.

### <a name="remarks"></a>Poznámky

Členská funkce porovná hodnoty použitím **operátor\<**  nebo **operátor >** mezi páry elementů třídy **typu**, pro operátory, které musí být zadaná pro element **typu**.

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
\* Output:
The operand valarray is: ( 0 2 3 -3 8 0 -6 14 -3 -9 ).
The smallest element in the valarray is: -9.
*\
```

## <a name="op_not"></a>  valarray::Operator!

Unární operátor, který získá logické **není** hodnoty každého prvku valarray –.

```cpp
valarray<bool> operator!() const;
```

### <a name="return-value"></a>Návratová hodnota

Valarray – logické hodnoty, které jsou negace element hodnot valarray – operand.

### <a name="remarks"></a>Poznámky

Logický provoz **není** Neguje elementy, protože převede samými nulami do těch, které jsou a jde o všechny nenulové hodnoty jako ty, které a převede je na nuly. Vrácený valarray – hodnot logická hodnota je stejnou velikost jako valarray – operand.

K dispozici je také bitové **není**[valarray::operator ~](#op_dtor) který Neguje na úrovni jednotlivých bitů v rámci binární reprezentace `char` a `int` elementy valarray –.

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
\* Output:
The initial valarray is:  ( 0 0 0 2 0 4 0 6 0 8 ).
The element-by-element result of the logical NOT operator! is the
 valarray: ( 1 1 1 0 1 0 1 0 1 0 ).
*\
```

## <a name="op_mod_eq"></a>  valarray::Operator % =

Získá zbytek po dělení prvků pole element-wise zadaný valarray – nebo hodnotu typu prvku.

```cpp
valarray<Type>& operator%=(const valarray<Type>& right);

valarray<Type>& operator%=(const Type& right);
```

### <a name="parameters"></a>Parametry

`right` Valarray – nebo hodnota stejná jako ve valarray – operand, který je rozdělit element-wise, valarray operand – element typu.

### <a name="return-value"></a>Návratová hodnota

Valarray –, jehož elementy jsou zbývající z divize element-wise valarray – operand podle `right`

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
\* Output:
The initial valarray is: ( 53 -67 53 -67 53 -67 ).
The initial  right valarray is: ( 1 4 7 10 13 16 ).
The remainders from the element-by-element division is the
 valarray: ( 0 -3 4 -7 1 -3 ).
*\
```

## <a name="and_eq"></a>  valarray::Operator&amp;=

Získá bitové hodnotě **a** elementů v pole s odpovídající elementů v zadané valarray – nebo s hodnotou typu prvku.

```cpp
valarray<Type>& operator&=(const valarray<Type>& right);

valarray<Type>& operator&=(const Type& right);
```

### <a name="parameters"></a>Parametry

`right` Valarray – nebo hodnota typu element shodná s valarray – operand, který je možné kombinovat, element-wise podle logického **a** s valarray – operand.

### <a name="return-value"></a>Návratová hodnota

Valarray –, jehož elementy jsou element-wise logické **a** z valarray – operand podle `right`

### <a name="remarks"></a>Poznámky

Bitové operace lze použít pouze k manipulaci s bitů `char` a `int` datové typy a variantních proměnných a ne v **float**, **dvojité**, **longdouble**, `void`, `bool`, nebo jiných, komplexnější datové typy.

Bitové operace AND má stejné tabulce pravdivosti jako logické **a** , ale platí pro typ dat na úrovni jednotlivých bitů. Zadané bity *b*1 a *b*2, *b*1 **a** *b*2 je **true** pokud obě Služba BITS jsou true; **false** pokud alespoň jeden je false.

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
\* Output:
The initial valarray is:  ( 0 0 0 2 0 4 0 6 0 8 ).
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 8 9 ).
The element-by-element result of the logical AND operator&= is the
 valarray: ( 0 0 0 2 0 4 0 6 0 8 ).
*\
```

## <a name="op_gt_gt_eq"></a>  valarray::Operator&gt;&gt;=

Posuny vpravo bitů pro každý prvek operand valarray – po zadaný počet pozic nebo o element-wise částku určeného druhý valarray –.

```cpp
valarray<Type>& operator>>=(const valarray<Type>& right);

valarray<Type>& operator>>=(const Type& right);
```

### <a name="parameters"></a>Parametry

`right` Hodnota udávající dobu posunutí doprava nebo valarray –, jehož elementy znamenat element-wise množství posunutí doprava.

### <a name="return-value"></a>Návratová hodnota

Valarray –, jehož elementy byly zapuštěno právo hodnotě zadané v `right`.

### <a name="remarks"></a>Poznámky

Podepsaný čísla mají jejich znaménka zachovaná.

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
\* Output:
The initial operand valarray is: ( 64 -64 64 -64 64 -64 64 -64 ).
The  right valarray is: ( 0 1 2 3 4 5 6 7 ).
The element-by-element result of the right shift is the
 valarray: ( 64 -32 16 -8 4 -2 1 -1 ).
*\
```

## <a name="op_lt_lt_eq"></a>  valarray::Operator&lt;&lt;=

Posuny vlevo bitů pro každý prvek operand valarray – po zadaný počet pozic nebo o element-wise částku určeného druhý valarray –.

```cpp
valarray<Type>& operator<<=(const valarray<Type>& right);

valarray<Type>& operator<<=(const Type& right);
```

### <a name="parameters"></a>Parametry

`right` Hodnota udávající dobu posunutí doleva nebo valarray –, jehož elementy znamenat element-wise množství posunutí doleva.

### <a name="return-value"></a>Návratová hodnota

Valarray –, jehož elementy byly přesunuty parametru zbývajících hodnotě zadané v `right`.

### <a name="remarks"></a>Poznámky

Podepsaný čísla mají jejich znaménka zachovaná.

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
\* Output:
The initial operand valarray is: ( 1 -1 1 -1 1 -1 1 -1 ).
The  right valarray is: ( 0 1 2 3 4 5 6 7 ).
The element-by-element result of the left shift
 on the operand array is the valarray:
 ( 1 -2 4 -8 16 -32 64 -128 ).
*\
```

## <a name="op_star_eq"></a>  valarray::Operator * =

Vynásobí elementy zadaný valarray – nebo hodnota typu prvku element-wise, k valarray – operand.

```cpp
valarray<Type>& operator*=(const valarray<Type>& right);

valarray<Type>& operator*=(const Type& right);
```

### <a name="parameters"></a>Parametry

`right` Valarray – nebo hodnota stejná jako ve valarray – operand, které se mají vynásobit element-wise, valarray operand – element typu.

### <a name="return-value"></a>Návratová hodnota

Valarray –, jehož elementy jsou element-wise produkt valarray – operand a `right`.

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
\* Output:
The initial valarray is: ( 2 -1 2 -1 2 -1 2 -1 ).
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 ).
The element-by-element result of the multiplication is the
 valarray: ( 0 -1 4 -3 8 -5 12 -7 ).
*\
```

## <a name="op_add"></a>  valarray::Operator +

Unární operátor, který se vztahuje plus každý prvek v valarray –.

```cpp
valarray<Type> operator+() const;
```

### <a name="return-value"></a>Návratová hodnota

Valarray –, jehož elementy jsou plus ty operand pole.

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
\* Output:
The initial valarray is:  ( 0 0 -2 2 -4 4 -6 6 -8 8 ).
The element-by-element result of the operator+ is the
 valarray: ( 0 0 -2 2 -4 4 -6 6 -8 8 ).
*\
```

## <a name="op_add_eq"></a>  valarray::Operator +=

Přidá elementy zadaný valarray – nebo hodnotu typu prvku element-wise, do valarray – operand.

```cpp
valarray<Type>& operator+=(const valarray<Type>& right);

valarray<Type>& operator+=(const Type& right);
```

### <a name="parameters"></a>Parametry

`right` Valarray – nebo hodnota stejná jako ve valarray – operand, který má být přidán, element-wise, k valarray operand – element typu.

### <a name="return-value"></a>Návratová hodnota

Valarray –, jehož elementy jsou element-wise součet valarray – operand a `right`.

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
\* Output:
The initial valarray is: ( 2 -1 2 -1 2 -1 2 -1 ).
The initial  right valarray is: ( 0 1 2 3 4 5 6 7 ).
The element-by-element result of the sum is the
 valarray: ( 2 0 4 2 6 4 8 6 ).
*\
```

## <a name="valarray__operator-"></a>  valarray::Operator-

Unární operátor, který se vztahuje minus každý prvek v valarray –.

```cpp
valarray<Type> operator-() const;
```

### <a name="return-value"></a>Návratová hodnota

Valarray –, jehož elementy jsou minus ty operand pole.

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
\* Output:
The initial valarray is:  ( 0 0 -2 2 -4 4 -6 6 -8 8 ).
The element-by-element result of the operator+ is the
 valarray: ( 0 0 2 -2 4 -4 6 -6 8 -8 ).
*\
```

## <a name="valarray__operator-_eq"></a>  valarray::Operator-=

Odečte elementy zadaný valarray – nebo hodnotu typu prvku element-wise, z valarray – operand.

```cpp
valarray<Type>& operator-=(const valarray<Type>& right);

valarray<Type>& operator-=(const Type& right);
```

### <a name="parameters"></a>Parametry

`right` Valarray – nebo hodnota stejná jako ve valarray – operand, který se bude odečítat element-wise, od valarray operand – element typu.

### <a name="return-value"></a>Návratová hodnota

Valarray –, jehož elementy jsou element-wise rozdíl valarray – operand a `right`.

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
\* Output:
The initial valarray is: ( 10 0 10 0 10 0 10 0 ).
The initial  right valarray is: ( 0 1 2 3 4 5 6 7 ).
The element-by-element result of the difference is the
 valarray: ( 10 -1 8 -3 6 -5 4 -7 ).
*\
```

## <a name="op_div_eq"></a>  valarray::Operator / =

Vydělí valarray – operand element-wise elementy zadaný valarray – nebo hodnotu typu prvku.

```cpp
valarray<Type>& operator/=(const valarray<Type>& right);

valarray<Type>& operator/=(const Type& right);
```

### <a name="parameters"></a>Parametry

`right` Valarray – nebo hodnota stejná jako ve valarray – operand, který je možné rozdělit element-wise, do valarray operand – element typu.

### <a name="return-value"></a>Návratová hodnota

Dělený valarray –, jehož elementy jsou element-wise podíl valarray – operand `right`.

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
\* Output:
The initial valarray is: ( 100 -100 100 -100 100 -100 ).
The initial Right valarray is: ( 0 2 4 6 8 10 ).
The element-by-element result of the quotient is the
 valarray: ( inf -50 25 -16.6667 12.5 -10 ).
*\
```

## <a name="op_eq"></a>  valarray::Operator =

Přiřadí elementy valarray –, jejichž hodnoty se zadávají, buď přímo, nebo jako součást jiné valarray – nebo slice_array, gslice_array, mask_array nebo indirect_array.

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

`right` Valarray – které se mají zkopírovat do valarray – operand.

`val` Hodnota pro přiřazení k elementům valarray – operand.

`_Slicearray` Slice_array, které se mají zkopírovat do valarray – operand.

`_Gslicearray` Gslice_array, které se mají zkopírovat do valarray – operand.

`_Maskarray` Mask_array, které se mají zkopírovat do valarray – operand.

`_Indarray` Indirect_array, které se mají zkopírovat do valarray – operand.

### <a name="return-value"></a>Návratová hodnota

První člen operátor nahradí řízené sekvenci kopii pořadí řízené `right`.

Druhý člen operátor je stejný jako první, ale s [Rvalue – deklarátor odkazu: & &](../cpp/rvalue-reference-declarator-amp-amp.md).

Třetí operátor členů nahradí každý prvek řízené sekvenci kopii `val`.

Operátory zbývající členy nahradit tyto prvky řízené sekvenci vybraná jejich argumenty, které jsou generovány pouze systémem [operátor&#91;&#93;](#op_at).

Pokud hodnota člena v pořadí nahrazení řídí závisí na člena v řízené sekvenci počáteční, výsledkem nedefinovaný.

### <a name="remarks"></a>Poznámky

Pokud se změní délka řízené sekvenci, výsledkem je obecně definován. V této implementaci účinek je však jenom zneplatní všechny ukazatele nebo odkazy na elementy v řízené sekvenci.

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
\* Output:
The operand valarray va is: 0 1 2 3 4 5 6 7 8 9
The operand valarray vaR is: 10 9 8 7 6 5 4 3 2 1
The reassigned valarray va is: 10 9 8 7 6 5 4 3 2 1
The reassigned valarray va is: 10 10 10 10 10 10 10 10 10 10
*\
```

## <a name="op_at"></a>  valarray::Operator]

Vrátí odkaz na element nebo má hodnotu na zadaný index nebo podmnožinu zadaný.

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

`_Off` Index elementu, který chcete přiřadit hodnotu.

`_Slicearray` Slice_array valarray –, která určuje podmnožinu má být vybrána nebo vráceny do nové valarray –.

`_Gslicearray` Gslice_array valarray –, která určuje podmnožinu má být vybrána nebo vráceny do nové valarray –.

*_Boolarray* bool_array valarray –, která určuje podmnožinu má být vybrána nebo vráceny do nové valarray –.

`_Indarray` Indirect_array valarray –, která určuje podmnožinu má být vybrána nebo vráceny do nové valarray –.

### <a name="return-value"></a>Návratová hodnota

Odkaz na element nebo má hodnotu na zadaný index nebo podmnožinu zadaný.

### <a name="remarks"></a>Poznámky

Operátor člen je přetížen zajistit několik způsobů, jak vybrat pořadí prvků z těch, které řídí *\****to**. První skupinu pět operátory členy fungovat ve spojení s různými přetížení [operátor =](#op_eq) (a dalšími přiřazení operátory) umožňuje selektivní nahrazení (řezů) řízené sekvenci. Vybrané elementy musí existovat.

Při kompilaci pomocí [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) definován jako 1 nebo 2, Chyba za běhu dochází, pokud budete chtít přístup k elementu mimo hranice valarray –.  V tématu [zaškrtnutí iterátory](../standard-library/checked-iterators.md) Další informace.

### <a name="example"></a>Příklad

Podívejte se na příklady pro [slice::slice](../standard-library/slice-class.md#slice) a [gslice::gslice](../standard-library/gslice-class.md#gslice) příklad toho, jak deklarace a používání operátor.

## <a name="op_xor_eq"></a>  valarray::Operator ^ =

Získá element-wise exkluzivní logický operátor or ( **XOR**) z pole s zadaný valarray – nebo hodnota typu prvku.

```cpp
valarray<Type>& operator|=(const valarray<Type>& right);

valarray<Type>& operator|=(const Type& right);
```

### <a name="parameters"></a>Parametry

`right` Valarray – nebo hodnota typu element shodná s valarray – operand, který je možné kombinovat, element-wise logické exkluzivní **XOR** s valarray – operand.

### <a name="return-value"></a>Návratová hodnota

Valarray –, jehož elementy jsou element-wise, exkluzivní logické **XOR** z valarray – operand a `right`.

### <a name="remarks"></a>Poznámky

Exkluzivní logickou nebo označují jako **XOR**, má následující sémantiku: daný prvek *e*1 a *e*2, *e*1  **XOR** *e*2 je **true** Pokud právě jeden z elementů je true; **false** Pokud oba elementy false nebo pokud jsou splněny obě elementy.

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
\* Output:
The initial operand valarray is:  ( 1 0 1 0 1 0 1 0 1 0 ).
The  right valarray is: ( 0 0 1 3 3 4 6 6 7 9 ).
The element-by-element result of the bitwise XOR operator^= is the
 valarray: ( 1 0 0 3 2 4 7 6 6 9 ).
*\
```

## <a name="op_or_eq"></a>  valarray::Operator&#124;=

Získá bitové hodnotě `OR` elementů v pole s odpovídající elementů v zadané valarray – nebo s hodnotou typu prvku.

```cpp
valarray<Type>& operator|=(const valarray<Type>& right);

valarray<Type>& operator|=(const Type& right);
```

### <a name="parameters"></a>Parametry

`right` Valarray – nebo hodnota typu element shodná s valarray – operand, který je možné kombinovat, element-wise podle bitové hodnotě `OR` s valarray – operand.

### <a name="return-value"></a>Návratová hodnota

Valarray –, jehož elementy jsou element-wise bitový `OR` z valarray – operand podle `right`.

### <a name="remarks"></a>Poznámky

Bitové operace lze použít pouze k manipulaci s bitů `char` a `int` datové typy a variantních proměnných a ne v **float**, **dvojité**, **longdouble**, `void`, `bool`, nebo jiných, komplexnější datové typy.

Bitové hodnotě `OR` má stejné tabulce pravdivosti jako logické `OR` ale platí pro typ dat na úrovni jednotlivých bitů. Zadané bity *b*1 a *b*2, *b*1 `OR` *b*2 je **true** pokud alespoň jedna z bitů true; **false** Pokud jsou obě bits false.

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
\* Output:
The initial operand valarray is:
 ( 1 0 1 0 1 0 1 0 1 0 ).
The  right valarray is:
 ( 0 0 1 3 3 4 6 6 7 9 ).
The element-by-element result of the logical OR
 operator|= is the valarray:
 ( 1 0 1 3 3 4 7 6 7 9 ).
*\
```

## <a name="op_dtor"></a>  valarray::Operator ~

Unární operátor, který získá bitové hodnotě **není** hodnoty každého prvku valarray –.

```cpp
valarray<Type> operator~() const;
```

### <a name="return-value"></a>Návratová hodnota

Valarray – logické hodnoty, které jsou bitové hodnotě **není** element hodnot valarray – operand.

### <a name="remarks"></a>Poznámky

Bitové operace lze použít pouze k manipulaci s bitů `char` a `int` datové typy a variantních proměnných a ne v **float**, **dvojité**, **longdouble**, `void`, `bool` nebo jiných, komplexnější datové typy.

Bitové hodnotě **není** má stejné tabulce pravdivosti jako logické **není** , ale platí pro typ dat na úrovni jednotlivých bitů. Zadané bitové *b*, ~ *b* je hodnota true, pokud *b* je false a hodnotu false, pokud *b* hodnotu true. Logické **není**[operátor!](#op_not) použije na úroveň element počítání všechny nenulové hodnoty jako **true**, a výsledkem je valarray – hodnot logická hodnota. Bitové hodnotě **NOToperator ~**, naopak může mít za následek valarray – hodnot než 0 nebo 1, v závislosti na výsledek bitové operace.

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
\* Output:
The initial valarray <unsigned short int> is:  ( 0 5 2 15 4 25 6 35 8 45 ).
The element-by-element result of the bitwise NOT operator~ is the
 valarray: ( 65535 65530 65533 65520 65531 65510 65529 65500 65527 65490 ).

The initial valarray <int> is:  ( 0 -2 2 -6 4 -10 6 -14 8 -18 ).
The element-by-element result of the bitwise NOT operator~ is the
 valarray: ( -1 1 -3 5 -5 9 -7 13 -9 17 ).
The element-by-element result of adding one
 is the negative of the original elements the
 valarray: ( 0 2 -2 6 -4 10 -6 14 -8 18 ).
*\
```

## <a name="resize"></a>  valarray::Resize

Počet elementů ve valarray – změny určeného čísla.

```cpp
void resize(
    size_t _Newsize);

void resize(
    size_t _Newsize,
    const Type val);
```

### <a name="parameters"></a>Parametry

`_Newsize` Počet elementů v změněnou valarray –.

`val` Hodnota, která má být poskytnut k elementům změněnou valarray –.

### <a name="remarks"></a>Poznámky

První člen funkce inicializuje prvky s jejich výchozí konstruktor.

Všechny ukazatele nebo odkazy na elementy v řízené sekvenci jsou zneplatněny.

### <a name="example"></a>Příklad

Následující příklad ukazuje použití valarray::resize – členská funkce.

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

Všechny elementy ve valarray – posune zadaný počet míst.

```cpp
valarray<Type> shift(int count) const;
```

### <a name="parameters"></a>Parametry

`count` Počet míst elementy jsou Posunutí vpřed.

### <a name="return-value"></a>Návratová hodnota

Nové valarray –, ve kterém jsou všechny elementy byly přesunuty `count` pozice směrem dopředu valarray –, ponecháno s ohledem na jejich umístění v valarray – operand.

### <a name="remarks"></a>Poznámky

Kladnou hodnotu `count` posune elementy vlevo `count` umístí s nulové výplně.

Záporná hodnota `count` posune právo elementy `count` umístí s nulové výplně.

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
\* Output:
The operand valarray va1(10) is: ( 0 1 2 3 4 5 6 7 8 9 ).
The shifted valarray va1 is: va1.shift (4) = ( 4 5 6 7 8 9 0 0 0 0 ).
The operand valarray va2(10) is: ( 10 9 8 7 6 5 4 3 2 1 ).
The shifted valarray va2 is: va2.shift (-4) = ( 0 0 0 0 10 9 8 7 6 5 ).
*\
```

## <a name="size"></a>  valarray::size

Vyhledá v valarray – počet elementů.

```cpp
size_t size() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet elementů v valarray – operand.

### <a name="example"></a>Příklad

Následující příklad ukazuje použití valarray::size – členská funkce.

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

Určuje součet všech elementů v valarray – délky nenulové hodnoty.

```cpp
Type sum() const;
```

### <a name="return-value"></a>Návratová hodnota

Součet elementů valarray – operand.

### <a name="remarks"></a>Poznámky

Pokud délka je větší než 1, členské funkce přidá hodnoty součtem použitím `operator+=` mezi páry elementů třídy **typ**, které operátor v důsledku toho musí zajistit pro elementy typu  **Typ**.

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
\* Output:
The operand valarray va (10) is: ( 0 1 2 3 4 5 6 7 8 9 ).
The sum of elements in the valarray is: 45.
*\
```

## <a name="swap"></a>  valarray::swap

Výměny dva elementy `valarray`s.

```cpp
void swap(valarray& right);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|`right`|A `valarray` poskytuje prvky, které mají být vzájemně zaměněny.|

### <a name="remarks"></a>Poznámky

Členská funkce prohození řízené pořadí mezi `*this` a `right`. Dělá to tak konstantní včas, vyvolá nedocházelo k výjimkám a ho by způsobila neplatnost žádné odkazy, ukazatele nebo iterátory, které určit elementů ve dvou řízené pořadí.

## <a name="valarray"></a>  valarray::valarray

Valarray – určité velikosti nebo u elementů na konkrétní hodnoty, nebo jako kopii jiného valarray – nebo podmnožinu jiné valarray – vytvoří.

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

`Count` Počet elementů ve valarray –.

`Val` Hodnota, který se má použít při inicializaci elementů v valarray –.

`Ptr` Ukazatel na hodnoty, které mají být použitý k inicializaci elementů v valarray –.

`Right` Existující valarray – k inicializaci nové valarray –.

`SliceArray` Slice_array, jejichž hodnoty prvků mají být použita při inicializaci elementy valarray – vytvářen.

`GsliceArray` Gslice_array, jejichž hodnoty prvků mají být použita při inicializaci elementy valarray – vytvářen.

`MaskArray` Mask_array, jejichž hodnoty prvků mají být použita při inicializaci elementy valarray – vytvářen.

`IndArray` Indirect_array, jejichž hodnoty prvků mají být použita při inicializaci elementy valarray – vytvářen.

`IList` Initializer_list obsahující prvky pro kopírování.

### <a name="remarks"></a>Poznámky

První (výchozí) konstruktor inicializuje objekt, který má prázdné pole. Následující tři konstruktory inicializovat objekt, který má pole `Count` elementy následujícím způsobem:

- Pro explicitní `valarray(size_t Count)`, každý prvek je inicializován s výchozím konstruktorem.

- Pro `valarray(const Type& Val, Count)`, každý prvek je inicializován s `Val`.

- Pro `valarray(const Type* Ptr, Count)`, element na pozici `I` inicializován s `Ptr`[ `I`].

Každý zbývající konstruktor inicializuje objekt, který má valarray –\<typ > objekt určen podmnožinu zadaný v argumentu.

Poslední konstruktor je stejný jako další a poslední, v, ale s [Rvalue – deklarátor odkazu: & &](../cpp/rvalue-reference-declarator-amp-amp.md).

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

Typ, který představuje typ elementu uložené v valarray –.

```cpp
typedef Type value_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro parametr šablony **typu**.

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
\* Output:
The initial operand valarray is:  ( 0 -1 2 -1 4 -1 6 -1 8 -1 ).
The decalared value_type Right is: 10
The resulting valarray is:  ( 0 -10 20 -10 40 -10 60 -10 80 -10 ).
*\
```

## <a name="see-also"></a>Viz také

[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
