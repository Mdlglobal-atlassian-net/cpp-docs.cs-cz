---
title: ostream_iterator – třída
ms.date: 11/04/2016
f1_keywords:
- iterator/std::ostream_iterator
- iterator/std::ostream_iterator::char_type
- iterator/std::ostream_iterator::ostream_type
- iterator/std::ostream_iterator::traits_type
helpviewer_keywords:
- std::ostream_iterator [C++]
- std::ostream_iterator [C++], char_type
- std::ostream_iterator [C++], ostream_type
- std::ostream_iterator [C++], traits_type
ms.assetid: 24d842d3-9f45-4bf6-a697-62f5968f5a03
ms.openlocfilehash: a0c794fe2ff7897bcb6d6412613689100a977589
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373589"
---
# <a name="ostream_iterator-class"></a>ostream_iterator – třída

Šablona třídy ostream_iterator popisuje výstupní iterátor objekt, který zapisuje následné prvky do výstupního datového proudu s extrakcí `operator <<`.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Type class CharType = char class Traits = char_traits <CharType>>
class ostream_iterator
```

### <a name="parameters"></a>Parametry

*Typ*\
Typ objektu, který má být vložen do výstupního toku.

*Typ znaku*\
Typ, který představuje typ `ostream_iterator`znaku pro . Tento argument je volitelný a výchozí hodnota je **char**.

*Vlastnosti*\
Typ, který představuje typ `ostream_iterator`znaku pro . Tento argument je volitelný a `char_traits` \< výchozí hodnota je *CharType>.*

Třída ostream_iterator musí splňovat požadavky na výstupní iterátor. Algoritmy lze zapisovat přímo `ostream_iterator`do výstupních datových proudů pomocí .

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[ostream_iterator](#ostream_iterator)|`ostream_iterator` Vytvoří, který je inicializován a oddělen pro zápis do výstupního datového proudu.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[char_type](#char_type)|Typ, který poskytuje typ znaku `ostream_iterator`.|
|[ostream_type](#ostream_type)|Typ, který poskytuje pro typ `ostream_iterator`datového proudu .|
|[traits_type](#traits_type)|Typ, který poskytuje typ znakových `ostream_iterator`znaků typu .|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operátor*](#op_star)|Dereferencing operátor slouží k implementaci výstupního \* `i`  =  `x`výrazu iterátoru .|
|[operátor++](#op_add_add)|Operátor nefunkční přírůstek, `ostream_iterator` který vrací stejný objekt, který byl adresován před voláním operace.|
|[operátor =](#op_eq)|Operátor přiřazení slouží k implementaci výstupního \* `i`  =  `x` výrazu iterátoru pro zápis do výstupního datového proudu.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<> iterátoru

**Obor názvů:** std

## <a name="ostream_iteratorchar_type"></a><a name="char_type"></a>ostream_iterator::char_type

Typ, který poskytuje typ znaku iterátoru.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymem pro `CharType`parametr šablony .

### <a name="example"></a>Příklad

```cpp
// ostream_iterator_char_type.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   typedef ostream_iterator<int>::char_type CHT1;
   typedef ostream_iterator<int>::traits_type CHTR1;

   // ostream_iterator for stream cout
   // with new line delimiter:
    ostream_iterator<int, CHT1, CHTR1> intOut ( cout , "\n" );

   // Standard iterator interface for writing
   // elements to the output stream:
   cout << "The integers written to the output stream\n"
        << "by intOut are:" << endl;
*intOut = 10;
*intOut = 20;
*intOut = 30;
}
/* Output:
The integers written to the output stream
by intOut are:
10
20
30
*/
```

## <a name="ostream_iteratoroperator"></a><a name="op_star"></a>ostream_iterator::operátor*

Dereferencing operátor slouží k implementaci výstupního \* iterátoru výraz *ii* = *x*.

```cpp
ostream_iterator<Type, CharType, Traits>& operator*();
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na `ostream_iterator`.

### <a name="remarks"></a>Poznámky

Požadavky na výstupní iterátor, `ostream_iterator` který musí splňovat, \* vyžadují pouze výraz *ii* = *t* platný a neříká nic o **operátorovi** `operator=` nebo o sobě. Operátor člena v této implementaci vrátí ** \*toto**.

### <a name="example"></a>Příklad

```cpp
// ostream_iterator_op_deref.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   // ostream_iterator for stream cout
   // with new line delimiter
   ostream_iterator<int> intOut ( cout , "\n" );

   // Standard iterator interface for writing
   // elements to the output stream
   cout << "Elements written to output stream:" << endl;
*intOut = 10;
   intOut++;      // No effect on iterator position
*intOut = 20;
*intOut = 30;
}
/* Output:
Elements written to output stream:
10
20
30
*/
```

## <a name="ostream_iteratoroperator"></a><a name="op_add_add"></a>ostream_iterator::operátor++

Operátor nefunkční přírůstek, `ostream_iterator` který vrací stejný objekt, který byl adresován před voláním operace.

```cpp
ostream_iterator<Type, CharType, Traits>& operator++();
ostream_iterator<Type, CharType, Traits> operator++(int);
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na `ostream_iterator`.

### <a name="remarks"></a>Poznámky

Tyto členské operátory oba vrátit ** \*toto**.

### <a name="example"></a>Příklad

```cpp
// ostream_iterator_op_incr.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   // ostream_iterator for stream cout
   // with new line delimiter
   ostream_iterator<int> intOut ( cout , "\n" );

   // standard iterator interface for writing
   // elements to the output stream
   cout << "Elements written to output stream:" << endl;
*intOut = 10;
   intOut++;      // No effect on iterator position
*intOut = 20;
*intOut = 30;
}
/* Output:
Elements written to output stream:
10
20
30
*/
```

## <a name="ostream_iteratoroperator"></a><a name="op_eq"></a>ostream_iterator::operátor=

Operátor přiřazení používaný k \* `i`  =  `x` implementaci výrazu output_iterator pro zápis do výstupního datového proudu.

```cpp
ostream_iterator<Type, CharType, Traits>& operator=(const Type& val);
```

### <a name="parameters"></a>Parametry

*Val*\
Hodnota objektu typu, `Type` který má být vložen do výstupního datového proudu.

### <a name="return-value"></a>Návratová hodnota

Operátor vloží *val* do výstupního datového proudu přidruženého k objektu, následovaný oddělovačem zadaným v `ostream_iterator` [konstruktoru ostream_iterator](#ostream_iterator) (pokud existuje) a potom vrátí odkaz na .

### <a name="remarks"></a>Poznámky

Požadavky na výstupní iterátor, `ostream_iterator` který musí splňovat, \* `ii`  =  `t` vyžadují pouze výraz platný a neříká nic o operátoru nebo operátoru = samostatně. Tento operátor `*this`člena vrátí .

### <a name="example"></a>Příklad

```cpp
// ostream_iterator_op_assign.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   // ostream_iterator for stream cout
   // with new line delimiter
   ostream_iterator<int> intOut ( cout , "\n" );

   // Standard iterator interface for writing
   // elements to the output stream
   cout << "Elements written to output stream:" << endl;
*intOut = 10;
   intOut++;      // No effect on iterator position
*intOut = 20;
*intOut = 30;
}
/* Output:
Elements written to output stream:
10
20
30
*/
```

## <a name="ostream_iteratorostream_iterator"></a><a name="ostream_iterator"></a>ostream_iterator::ostream_iterator

`ostream_iterator` Vytvoří, který je inicializován a oddělen pro zápis do výstupního datového proudu.

```cpp
ostream_iterator(
    ostream_type& _Ostr);

ostream_iterator(
    ostream_type& _Ostr,
    const CharType* _Delimiter);
```

### <a name="parameters"></a>Parametry

*_Ostr*\
Výstupní datový proud typu [ostream_iterator::ostream_type,](#ostream_type) který má být iterován.

*_Delimiter*\
Oddělovač, který je vložen do výstupního datového proudu mezi hodnotami.

### <a name="remarks"></a>Poznámky

První konstruktor inicializuje ukazatel výstupního datového proudu s `&_Ostr`. Ukazatel řetězce oddělovače označuje prázdný řetězec.

Druhý konstruktor inicializuje ukazatel výstupního datového proudu `&_Ostr` s a ukazatel řetězce oddělovače s *_Delimiter*.

### <a name="example"></a>Příklad

```cpp
// ostream_iterator_ostream_iterator.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   // ostream_iterator for stream cout
   ostream_iterator<int> intOut ( cout , "\n" );
*intOut = 10;
   intOut++;
*intOut = 20;
   intOut++;

   int i;
   vector<int> vec;
   for ( i = 1 ; i < 7 ; ++i )
   {
      vec.push_back (  i );
   }

   // Write elements to standard output stream
   cout << "Elements output without delimiter: ";
   copy ( vec.begin ( ), vec.end ( ),
          ostream_iterator<int> ( cout ) );
   cout << endl;

   // Write elements with delimiter " : " to output stream
   cout << "Elements output with delimiter: ";
   copy ( vec.begin ( ), vec.end ( ),
          ostream_iterator<int> ( cout, " : " ) );
   cout << endl;
}
/* Output:
10
20
Elements output without delimiter: 123456
Elements output with delimiter: 1 : 2 : 3 : 4 : 5 : 6 :
*/
```

## <a name="ostream_iteratorostream_type"></a><a name="ostream_type"></a>ostream_iterator::ostream_type

Typ, který poskytuje pro typ datového proudu iterátoru.

```cpp
typedef basic_ostream<CharType, Traits> ostream_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymem [basic_ostream](../standard-library/basic-ostream-class.md)< `CharType`pro `Traits` basic_ostream ,>, třídy datového proudu hierarchie iostream, který definuje objekty, které lze použít pro psaní.

### <a name="example"></a>Příklad

Příklad, jak deklarovat a `ostream_type`používat aplikaci , naleznete [v ostream_iterator.](#ostream_iterator)

## <a name="ostream_iteratortraits_type"></a><a name="traits_type"></a>ostream_iterator::traits_type

Typ, který poskytuje znakové znaky typu iterátoru.

```cpp
typedef Traits traits_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymem pro `Traits`parametr šablony .

### <a name="example"></a>Příklad

```cpp
// ostream_iterator_traits_type.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   // The following not OK, but are just the default values:
   typedef ostream_iterator<int>::char_type CHT1;
   typedef ostream_iterator<int>::traits_type CHTR1;

   // ostream_iterator for stream cout
   // with new line delimiter:
    ostream_iterator<int, CHT1, CHTR1> intOut ( cout , "\n" );

   // Standard iterator interface for writing
   // elements to the output stream:
   cout << "The integers written to output stream\n"
        << "by intOut are:" << endl;
*intOut = 1;
*intOut = 10;
*intOut = 100;
}
/* Output:
The integers written to output stream
by intOut are:
1
10
100
*/
```

## <a name="see-also"></a>Viz také

[\<>iterátoru](../standard-library/iterator.md)\
[Bezpečnost vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Referenční příručka standardní knihovny jazyka C++](../standard-library/cpp-standard-library-reference.md)
