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
ms.openlocfilehash: 9372fa884d75e10c1a0f2ec92d6cca9caa65808e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80167612"
---
# <a name="raw_storage_iterator-class"></a>raw_storage_iterator – třída

Třída adaptéru, která je k dispozici pro povolení algoritmů pro ukládání výsledků do neinicializované paměti.

## <a name="syntax"></a>Syntaxe

```cpp
template <class OutputIterator, class Type>
    class raw_storage_iterator
```

### <a name="parameters"></a>Parametry

*OutputIterator*\
Určuje výstupní iterátor pro objekt, který se ukládá.

*Zadejte*\
Typ objektu, pro který je úložiště přiděleno.

## <a name="remarks"></a>Poznámky

Třída popisuje výstupní iterátor, který vytváří objekty typu `Type` v sekvenci, kterou generuje. Objekt třídy `raw_storage_iterator`\< **ForwardIterator**, **typ**> přistupuje k úložišti prostřednictvím objektu dopředné iterátory třídy `ForwardIterator`, který zadáte při vytváření objektu. Pro objekt, který je první z `ForwardIterator`třídy, výraz **&\*nejdříve** musí určit nekonstruované úložiště pro další objekt (typu `Type`) ve vygenerované sekvenci.

Tato třída adaptéru se používá v případě, že je nutné rozdělit přidělení paměti a konstrukci objektu. `raw_storage_iterator` lze použít ke kopírování objektů do neinicializovaného úložiště, jako je například paměť přidělená pomocí funkce `malloc`.

## <a name="members"></a>Členové

### <a name="constructors"></a>Konstruktory

|||
|-|-|
|[raw_storage_iterator](#raw_storage_iterator)|Vytvoří iterátor nezpracovaného úložiště se zadaným podkladovým výstupním iterátorem.|

### <a name="typedefs"></a>Typedefs

|||
|-|-|
|[element_type](#element_type)|Poskytuje typ, který popisuje prvek pro uložení iterátoru nezpracovaného úložiště.|
|[iter_type](#iter_type)|Poskytuje typ, který popisuje iterátor, který představuje nezpracovaný iterátor úložiště.|

### <a name="operators"></a>Operátory

|||
|-|-|
|[podnikatel](#op_star)|Operátor přesměrování používaný k implementaci výrazu výstupního iterátoru \* `ii` = `x`.|
|[operátor =](#op_eq)|Operátor přiřazení používaný k implementaci výrazu iterátoru nezpracovaného úložiště \* `i` = `x` pro ukládání do paměti.|
|[operator + + – operátor](#op_add_add)|Postinkrement operátory pro zpracování nezpracovaných iterátorů úložiště.|

### <a name="element_type"></a><a name="element_type"></a>element_type

Poskytuje typ, který popisuje prvek pro uložení iterátoru nezpracovaného úložiště.

```cpp
typedef Type element_type;
```

#### <a name="remarks"></a>Poznámky

Typ je synonymum pro parametr raw_storage_iterator třídy šablony `Type`.

### <a name="iter_type"></a><a name="iter_type"></a>iter_type

Poskytuje typ, který popisuje iterátor, který představuje nezpracovaný iterátor úložiště.

```cpp
typedef ForwardIterator iter_type;
```

#### <a name="remarks"></a>Poznámky

Typ je synonymum pro parametr šablony `ForwardIterator`.

### <a name="operator"></a><a name="op_star"></a>operátor\*

Operátor přesměrování používaný k implementaci výrazu iterátoru nezpracovaného úložiště \* *ii* = *x*.

```cpp
raw_storage_iterator<ForwardIterator, Type>& operator*();
```

#### <a name="return-value"></a>Návratová hodnota

Odkaz na iterátor nezpracovaného úložiště

#### <a name="remarks"></a>Poznámky

Požadavky na `ForwardIterator` jsou v tom, že iterátor nezpracovaného úložiště musí splňovat podmínky, že by byl platný jenom výraz \* *ii* = *t* a že není nic o **operátoru** nebo `operator=` sám o sobě. Členské operátory v této implementaci vrátí **\*this**, takže [operátor =](#op_eq)(**constType**&) může ve výrazu provádět skutečné úložiště, jako je například \* *PTR* = `val`.

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

### <a name="operator"></a><a name="op_eq"></a>operátor =

Operátor přiřazení používaný k implementaci výrazu iterátoru nezpracovaného úložiště \* *i* = *x* pro ukládání do paměti.

```cpp
raw_storage_iterator<ForwardIterator, Type>& operator=(
    const Type& val);
```

#### <a name="parameters"></a>Parametry

\ *Val*
Hodnota objektu typu `Type`, který se má vložit do paměti

#### <a name="return-value"></a>Návratová hodnota

Operátor vloží `val` do paměti a potom vrátí odkaz na nezpracovaný iterátor úložiště.

#### <a name="remarks"></a>Poznámky

Požadavky na `ForwardIterator` stav, které musí splňovat nezpracovaný iterátor úložiště, vyžadovat pouze výraz \* *ii* = *t* , a že se nic o **operátoru** nebo `operator=` neprojeví. Tyto členské operátory vrací **\*this**.

Operátor přiřazení sestaví další objekt ve výstupní sekvenci pomocí hodnoty uloženého iterátoru jako první, a to vyhodnocením nového výrazu **New** ((`void` \*) &\* **First**) **typu**(`val`).

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

### <a name="operator"></a><a name="op_add_add"></a>operator + + – operátor

Postinkrement operátory pro zpracování nezpracovaných iterátorů úložiště.

```cpp
raw_storage_iterator<ForwardIterator, Type>& operator++();

raw_storage_iterator<ForwardIterator, Type> operator++(int);
```

#### <a name="return-value"></a>Návratová hodnota

Iterátor nezpracovaného úložiště nebo odkaz na iterátor nezpracovaného úložiště.

#### <a name="remarks"></a>Poznámky

První operátor se nakonec pokusí extrahovat a uložit objekt typu `CharType` z přidruženého vstupního streamu. Druhý operátor vytvoří kopii objektu, zvýší objekt a vrátí kopii.

První operátor přírůstku zvýší uložený výstupní objekt iterátoru a potom vrátí **\*** .

Druhý postinkrement operátor vytvoří kopii **tohoto\*** , zvýší uložený výstupní objekt iterátoru a pak kopii vrátí.

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

### <a name="raw_storage_iterator"></a><a name="raw_storage_iterator"></a>raw_storage_iterator

Vytvoří iterátor nezpracovaného úložiště se zadaným podkladovým výstupním iterátorem.

```cpp
explicit raw_storage_iterator(ForwardIterator first);
```

#### <a name="parameters"></a>Parametry

*první*\
Dopředný iterátor, který je základem objektu `raw_storage_iterator`, který je vytvářen.

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
