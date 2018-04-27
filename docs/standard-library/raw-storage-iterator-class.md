---
title: raw_storage_iterator – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- memory/std::raw_storage_iterator
- memory/std::raw_storage_iterator::element_type
- memory/std::raw_storage_iterator::iter_type
dev_langs:
- C++
helpviewer_keywords:
- std::raw_storage_iterator [C++]
- std::raw_storage_iterator [C++], element_type
- std::raw_storage_iterator [C++], iter_type
ms.assetid: 6f033f15-f48e-452a-a326-647ea2cf346f
caps.latest.revision: 17
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b5eacac6614bb5a58baff3a3014dcc28146d6fd3
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="rawstorageiterator-class"></a>raw_storage_iterator – třída

Třída adaptéru, která je k dispozici pro povolení algoritmů pro ukládání výsledků do neinicializované paměti.

## <a name="syntax"></a>Syntaxe

```cpp
template <class OutputIterator, class Type>
class raw_storage_iterator
```

### <a name="parameters"></a>Parametry

`OutputIterator` Určuje iterator výstup pro daný objekt uložené.

*Typ* typ objektu, pro který je přidělen úložiště.

## <a name="remarks"></a>Poznámky

Třída popisuje iterátor výstup, který vytvoří objekty typu **typ** v pořadí, vygeneruje. Třída objektu `raw_storage_iterator` \< **ForwardIterator**, **typ**> úložiště přistupuje prostřednictvím objekt dopředného iterator třídy **ForwardIterator**, zda jste zadali při vytvoření objektu. Pro objekt první třídy **ForwardIterator**, výraz  **& \*první** musí určit unconstructed úložiště pro další objekt (typu **typu** ) v generované pořadí.

Tato třída adaptéru se používá, když je potřeba oddělit přidělování paměti a vytváření objektů. `raw_storage_iterator` Lze použít k objektům kopírování do neinicializovaného úložiště, jako je paměť přidělená pomocí `malloc` funkce.

## <a name="members"></a>Členové

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[raw_storage_iterator](#raw_storage_iterator)|Vytvoří iterator úložiště pomocí zadané základní iterator výstup.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[element_type](#element_type)|Poskytuje možnosti pro typ, který odpovídá elementu být uložená iterator úložiště.|
|[iter_type](#iter_type)|Poskytuje typ, který popisuje iterovat podkladovou iterator úložiště.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operátor *](#op_star)|Při přesměrování operátor použít k implementaci výraz iterator výstup * `ii`  =  `x`.|
|[operátor =](#op_eq)|Operátor přiřazení použít k implementaci výraz iterator úložiště * `i`  =  `x` pro ukládání do paměti.|
|[Operator ++](#op_add_add)|Preincrement a postincrement operátory iterátory úložiště.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<paměti >

**Namespace:** – std

## <a name="element_type"></a>  raw_storage_iterator::ELEMENT_TYPE

Poskytuje možnosti pro typ, který odpovídá elementu být uložená iterator úložiště.

```cpp
typedef Type element_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro parametr šablony raw_storage_iterator – třída **typu**.

## <a name="iter_type"></a>  raw_storage_iterator::iter_type

Poskytuje typ, který popisuje iterovat podkladovou iterator úložiště.

```cpp
typedef ForwardIterator iter_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro parametr šablony **ForwardIterator**.

## <a name="op_star"></a>  raw_storage_iterator::Operator *

Při přesměrování operátor použít k implementaci výraz iterator úložiště \* *ii* = *x*.

```cpp
raw_storage_iterator<ForwardIterator, Type>& operator*();
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na iterator úložiště

### <a name="remarks"></a>Poznámky

Požadavky **ForwardIterator** si, že nezpracovaná iterator úložiště musí splňovat vyžadovat pouze výraz \* *ii* = *t* být platný a že se nic říká o **operátor** nebo `operator=` samostatně. Vrátí operátory členy v této implementaci  **\*to**tak, aby [operátor =](#op_eq)( **constType**&) ve výrazu, můžete provést skutečné úložiště například \* *ptr* = `val`.

### <a name="example"></a>Příklad

```cpp
// raw_storage_iterator_op_deref.cpp
// compile with: /EHsc
#include <iostream>
#include <iterator>
#include <memory>
#include <list>
using namespace std;

class Int
{
public:
   Int(int i)
   {
      cout << "Constructing " << i << endl;
      x = i;
      bIsConstructed = true;
   };

   Int &operator=(int i)
   {
      if (!bIsConstructed)
         cout << "Not constructed.\n";
      cout << "Copying " << i << endl;
      x = i;
      return *this;
   };

   int x;

private:
   bool bIsConstructed;
};

int main( void)
{
   Int *pInt = ( Int* ) malloc( sizeof( Int ) );
   memset( pInt, 0, sizeof( Int ) ); // Set bIsConstructed to false;
 *pInt = 5;
   raw_storage_iterator< Int*, Int > it( pInt );
 *it = 5;
}
\* Output:
Not constructed.
Copying 5
Constructing 5
*\
```

## <a name="op_eq"></a>  raw_storage_iterator::Operator =

Operátor přiřazení použít k implementaci výraz iterator úložiště \* *i* = *x* pro ukládání do paměti.

```cpp
raw_storage_iterator<ForwardIterator, Type>& operator=(
    const Type& val);
```

### <a name="parameters"></a>Parametry

`val` Hodnota typu objektu **typ** má být vložen do paměti.

### <a name="return-value"></a>Návratová hodnota

Operátor vložení `val` do paměti a vrátí odkaz na iterator úložiště.

### <a name="remarks"></a>Poznámky

Požadavky **ForwardIterator** stavu, který musí splňovat iterator úložiště vyžadovat pouze výraz \* *ii* = *t* být platný, a že se nic říká o **operátor** nebo `operator=` samostatně. Vrátí tyto operátory členy  **\*to**.

Operátor přiřazení vytvoří další objekt v pořadí výstup pomocí hodnoty uložené iterator nejprve vyhodnocením výrazu nové umístění **nové** (( `void` \*) &\* **první**) **typ**( `val`).

### <a name="example"></a>Příklad

```cpp
// raw_storage_iterator_op_assign.cpp
// compile with: /EHsc
#include <iostream>
#include <iterator>
#include <memory>
#include <list>
using namespace std;

class Int
{
public:
   Int( int i )
   {
      cout << "Constructing " << i << endl;
      x = i;
      bIsConstructed = true;
   };
   Int &operator=( int i )
   {
      if ( !bIsConstructed )
         cout << "Not constructed.\n";
      cout << "Copying " << i << endl; x = i;
      return *this;
   };
   int x;
private:
   bool bIsConstructed;
};

int main( void )
{
   Int *pInt = ( Int* )malloc( sizeof( Int ) );
   memset( pInt, 0, sizeof( Int ) ); // Set bIsConstructed to false;

*pInt = 5;

   raw_storage_iterator<Int*, Int> it( pInt );
 *it = 5;
}
\* Output:
Not constructed.
Copying 5
Constructing 5
*\
```

## <a name="op_add_add"></a>  raw_storage_iterator::Operator ++

Preincrement a postincrement operátory iterátory úložiště.

```cpp
raw_storage_iterator<ForwardIterator, Type>& operator++();

raw_storage_iterator<ForwardIterator, Type> operator++(int);
```

### <a name="return-value"></a>Návratová hodnota

Iterátor úložiště nebo odkaz na iterovat úložiště.

### <a name="remarks"></a>Poznámky

První operátor nakonec pokusí extrahovat a uložit objekt typu **CharType** z přidružených vstupního datového proudu. Druhý operátor vytvoří kopii objektu, zvýší objekt a vrátí kopie.

První preincrement operátor zvýší objekt iterator uložené výstup a vrátí  **\*to**.

Druhý postincrement operátor vytvoří kopii  **\*to**, zvýší objekt iterator uložené výstup a vrátí kopie.

Konstruktor úložiště **první** jako objekt iterator výstup.

### <a name="example"></a>Příklad

```cpp
// raw_storage_iterator_op_incr.cpp
// compile with: /EHsc
#include <iostream>
#include <iterator>
#include <memory>
#include <list>
using namespace std;

int main( void )
{
   int *pInt = new int[5];
   std::raw_storage_iterator<int*,int> it( pInt );
   for ( int i = 0; i < 5; i++, it++ ) {
 *it = 2 * i;
};

   for ( int i = 0; i < 5; i++ ) cout << "array " << i << " = " << pInt[i] << endl;;

   delete[] pInt;
}
\* Output:
array 0 = 0
array 1 = 2
array 2 = 4
array 3 = 6
array 4 = 8
*\
```

## <a name="raw_storage_iterator"></a>  raw_storage_iterator::raw_storage_iterator

Vytvoří iterator úložiště pomocí zadané základní iterator výstup.

```cpp
explicit raw_storage_iterator(ForwardIterator first);
```

### <a name="parameters"></a>Parametry

`first` Předat dál iterator, které tvoří základ, je `raw_storage_iterator` objektu vytvářen.

### <a name="example"></a>Příklad

```cpp
// raw_storage_iterator_ctor.cpp
// compile with: /EHsc /W3
#include <iostream>
#include <iterator>
#include <memory>
#include <list>
using namespace std;

class Int
{
public:
   Int(int i)
   {
      cout << "Constructing " << i << endl;
      x = i;
      bIsConstructed = true;
   };
   Int &operator=( int i )
   {
      if (!bIsConstructed)
         cout << "Error! I'm not constructed!\n";
      cout << "Copying " << i << endl;  x = i; return *this;
   };
   int x;
   bool bIsConstructed;
};

int main( void )
{
   std::list<int> l;
   l.push_back( 1 );
   l.push_back( 2 );
   l.push_back( 3 );
   l.push_back( 4 );

   Int *pInt = (Int*)malloc(sizeof(Int)*l.size( ));
   memset (pInt, 0, sizeof(Int)*l.size( ));
   // Hack: make sure bIsConstructed is false

   std::copy( l.begin( ), l.end( ), pInt );  // C4996
   for (unsigned int i = 0; i < l.size( ); i++)
      cout << "array " << i << " = " << pInt[i].x << endl;;

   memset (pInt, 0, sizeof(Int)*l.size( ));
   // hack: make sure bIsConstructed is false

   std::copy( l.begin( ), l.end( ),
      std::raw_storage_iterator<Int*,Int>(pInt));  // C4996
   for (unsigned int i = 0; i < l.size( ); i++ )
      cout << "array " << i << " = " << pInt[i].x << endl;

   free(pInt);
}
\* Output:
Error! I'm not constructed!
Copying 1
Error! I'm not constructed!
Copying 2
Error! I'm not constructed!
Copying 3
Error! I'm not constructed!
Copying 4
array 0 = 1
array 1 = 2
array 2 = 3
array 3 = 4
Constructing 1
Constructing 2
Constructing 3
Constructing 4
array 0 = 1
array 1 = 2
array 2 = 3
array 3 = 4
*\
```

## <a name="see-also"></a>Viz také

[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
