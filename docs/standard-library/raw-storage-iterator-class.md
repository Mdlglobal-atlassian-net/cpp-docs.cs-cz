---
title: raw_storage_iterator – třída
ms.date: 11/04/2016
f1_keywords:
- memory/std::raw_storage_iterator
- memory/std::raw_storage_iterator::element_type
- memory/std::raw_storage_iterator::iter_type
helpviewer_keywords:
- std::raw_storage_iterator [C++]
- std::raw_storage_iterator [C++], element_type
- std::raw_storage_iterator [C++], iter_type
ms.assetid: 6f033f15-f48e-452a-a326-647ea2cf346f
ms.openlocfilehash: eb32d1846c4e94fbd275dcc416de4f37d9bb53f1
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/16/2019
ms.locfileid: "68240380"
---
# <a name="rawstorageiterator-class"></a>raw_storage_iterator – třída

Třída adaptéru, která je k dispozici pro povolení algoritmů pro ukládání výsledků do neinicializované paměti.

## <a name="syntax"></a>Syntaxe

```cpp
template <class OutputIterator, class Type>
    class raw_storage_iterator
```

### <a name="parameters"></a>Parametry

*OutputIterator*\
Určuje výstupní iterátor pro objekt uložené.

*Typ*\
Typ objektu, pro který je přidělen úložiště.

## <a name="remarks"></a>Poznámky

Tato třída popisuje výstupní iterátor, který Konstruuje objekt typu `Type` postupně generuje. Objekt třídy `raw_storage_iterator` \< **ForwardIterator**, **typ**> přistupuje k úložišti prostřednictvím objektu dopředný iterátor, který třídy `ForwardIterator`, když zadáte vám Vytvoření objektu. Pro objekt první třídy `ForwardIterator`, výraz  **& \*první** musíte rovněž unconstructed úložiště pro další objekt (typu `Type`) v generovaných sekvenčních.

Tato třída adaptéru se používá v případě potřeby k oddělení přidělování paměti a konstrukce objektu. `raw_storage_iterator` Je možné zkopírovat do neinicializovaného úložiště, jako je paměť přidělena pomocí objektů `malloc` funkce.

## <a name="members"></a>Členové

### <a name="constructors"></a>Konstruktory

|||
|-|-|
|[raw_storage_iterator](#raw_storage_iterator)|Vytvoří iterátor úložiště pomocí zadané základní iterátor výstupu.|

### <a name="typedefs"></a>Typedefs

|||
|-|-|
|[element_type](#element_type)|Obsahuje typ, který popisuje element, který má být uložena iterátor úložiště.|
|[iter_type](#iter_type)|Obsahuje typ, který popisuje iterátoru, které je základem iterátor úložiště.|

### <a name="operators"></a>Operátory

|||
|-|-|
|[Operator *](#op_star)|Operátor přesměrování používaný k implementaci výrazu výstupního iterátoru \* `ii`  =  `x`.|
|[operátor =](#op_eq)|Operátor přiřazení používaný k implementaci výrazu iterátoru úložiště \* `i`  =  `x` pro ukládání do paměti.|
|[Operator ++](#op_add_add)|Operátory preincrement a následného zvýšení u iterátorů úložiště.|

### <a name="element_type"></a> ELEMENT_TYPE

Obsahuje typ, který popisuje element, který má být uložena iterátor úložiště.

```cpp
typedef Type element_type;
```

#### <a name="remarks"></a>Poznámky

Typ je synonymum pro parametr šablony raw_storage_iterator – třída `Type`.

### <a name="iter_type"></a> iter_type

Obsahuje typ, který popisuje iterátoru, které je základem iterátor úložiště.

```cpp
typedef ForwardIterator iter_type;
```

#### <a name="remarks"></a>Poznámky

Typ je synonymum pro parametr šablony `ForwardIterator`.

### <a name="op_star"></a> – Operátor\*

Operátor přesměrování používaný k implementaci výrazu iterátoru úložiště \* *ii* = *x*.

```cpp
raw_storage_iterator<ForwardIterator, Type>& operator*();
```

#### <a name="return-value"></a>Návratová hodnota

Odkaz na iterátor úložiště

#### <a name="remarks"></a>Poznámky

Požadavky `ForwardIterator` si, že nezpracovaná úložiště iterátoru musí splňovat vyžadují pouze výraz \* *ii* = *t* platné a že neříká nic o **operátor** nebo `operator=` sami. Vrátí operátory členů v této implementaci  **\*to**tak, aby [operátor =](#op_eq)(**constType**&) můžete provádět skutečný úložiště ve výrazu například \* *ptr* = `val`.

#### <a name="example"></a>Příklad

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
```

```Output
Not constructed.
Copying 5
Constructing 5
```

### <a name="op_eq"></a> operátor =

Operátor přiřazení používaný k implementaci výrazu iterátoru úložiště \* *můžu* = *x* pro ukládání do paměti.

```cpp
raw_storage_iterator<ForwardIterator, Type>& operator=(
    const Type& val);
```

#### <a name="parameters"></a>Parametry

*Val*\
Hodnota objektu typu `Type` má být vložen do paměti.

#### <a name="return-value"></a>Návratová hodnota

Operátor vloží `val` do paměti a následně vrátí odkaz na iterátor úložiště.

#### <a name="remarks"></a>Poznámky

Požadavky `ForwardIterator` stavu, ve kterém úložiště iterátoru musí splňovat vyžadují pouze výraz \* *ii* = *t* platné a že neříká nic o **operátor** nebo `operator=` sami. Tyto operátory členů vrátit  **\*to**.

Operátor přiřazení vytvoří další objekt v pořadí výstupu pomocí uloženého iterátoru hodnoty nejprve vyhodnocením výrazu nové umístění **nové** (( `void` \*) &\* **první**) **typ**( `val`).

#### <a name="example"></a>Příklad

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
```

```Output
Not constructed.
Copying 5
Constructing 5
```

### <a name="op_add_add"></a> Operator ++

Operátory preincrement a následného zvýšení u iterátorů úložiště.

```cpp
raw_storage_iterator<ForwardIterator, Type>& operator++();

raw_storage_iterator<ForwardIterator, Type> operator++(int);
```

#### <a name="return-value"></a>Návratová hodnota

Iterátor úložiště nebo odkaz na iterátor úložiště.

#### <a name="remarks"></a>Poznámky

První operátor nakonec se pokusí extrahovat a uložit objekt typu `CharType` z přidruženého vstupního datového proudu. Druhý operátor vytvoří kopii tohoto objektu, zvýší na objekt a potom vrátí kopii.

První operátor preincrement zvýší uložený výstupní objekt iterátoru a vrátí  **\*to**.

Druhý operátor o vytvoří kopii tohoto  **\*to**, zvýší uložený výstupní objekt iterátoru a vrátí kopii.

Konstruktor ukládá `first` jako výstupní objekt iterátoru.

#### <a name="example"></a>Příklad

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
```

```Output
array 0 = 0
array 1 = 2
array 2 = 4
array 3 = 6
array 4 = 8
```

### <a name="raw_storage_iterator"></a> raw_storage_iterator –

Vytvoří iterátor úložiště pomocí zadané základní iterátor výstupu.

```cpp
explicit raw_storage_iterator(ForwardIterator first);
```

#### <a name="parameters"></a>Parametry

*první*\
Dopředný iterátor, který tvoří základ, je `raw_storage_iterator` objektu při konstrukci.

#### <a name="example"></a>Příklad

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
```

```Output
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
```