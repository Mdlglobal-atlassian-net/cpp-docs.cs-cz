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
ms.openlocfilehash: 63bf0a9e3f458b35421ca53d32a2d6be4b701e58
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2019
ms.locfileid: "72687244"
---
# <a name="ostream_iterator-class"></a>ostream_iterator – třída

Šablona třídy ostream_iterator popisuje výstupní objekt iterátoru, který zapisuje po sobě jdoucí prvky do výstupního datového proudu pomocí `operator <<` extrakce.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Type class CharType = char class Traits = char_traits <CharType>>
class ostream_iterator
```

### <a name="parameters"></a>Parametry

*Zadejte* \
Typ objektu, který má být vložen do výstupního toku.

*CharType* \
Typ, který představuje typ znaku pro `ostream_iterator`. Tento argument je nepovinný a výchozí hodnota je **char**.

@No__t_1 *vlastností*
Typ, který představuje typ znaku pro `ostream_iterator`. Tento argument je nepovinný a výchozí hodnota je `char_traits` \< *CharType >.*

Třída ostream_iterator musí splňovat požadavky na výstupní iterátor. Algoritmy lze zapisovat přímo do výstupních datových proudů pomocí `ostream_iterator`.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[ostream_iterator](#ostream_iterator)|Sestaví `ostream_iterator`, který je inicializován a oddělený pro zápis do výstupního datového proudu.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[char_type](#char_type)|Typ, který poskytuje typ znaku `ostream_iterator`.|
|[ostream_type](#ostream_type)|Typ, který poskytuje typ datového proudu `ostream_iterator`.|
|[traits_type](#traits_type)|Typ, který poskytuje typ znakových vlastností `ostream_iterator`.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[podnikatel](#op_star)|Operátor přesměrování používaný k implementaci výrazu výstupního iterátoru \* `i`  =  `x`.|
|[operator + + – operátor](#op_add_add)|Nefunkční operátor přírůstku, který vrací `ostream_iterator` ke stejnému objektu, který byl vyřešen před voláním operace.|
|[operátor =](#op_eq)|Operátor přiřazení používaný k implementaci výrazu výstupního iterátoru \* `i`  =  `x` pro zápis do výstupního datového proudu.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<iterator >

**Obor názvů:** std

## <a name="char_type"></a>ostream_iterator::char_type

Typ, který poskytuje typ znaku iterátoru.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro parametr šablony `CharType`.

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

## <a name="op_star"></a>ostream_iterator:: operator * – operátor

Operátor přesměrování používaný k implementaci výrazu výstupního iterátoru \* *ii*  = *x*.

```cpp
ostream_iterator<Type, CharType, Traits>& operator*();
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na `ostream_iterator`.

### <a name="remarks"></a>Poznámky

Požadavky na výstupní iterátor, které musí `ostream_iterator` splňovat, vyžadují, aby byl platný jenom výraz \* *ii*  = *t* a neříkají nic o **operátoru** nebo `operator=` sám o sobě. Operátor member v této implementaci vrací **\*this**.

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

## <a name="op_add_add"></a>ostream_iterator:: operator + +

Nefunkční operátor přírůstku, který vrací `ostream_iterator` ke stejnému objektu, který byl vyřešen před voláním operace.

```cpp
ostream_iterator<Type, CharType, Traits>& operator++();
ostream_iterator<Type, CharType, Traits> operator++(int);
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na `ostream_iterator`.

### <a name="remarks"></a>Poznámky

Tyto členské operátory vrátí **\*this**.

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

## <a name="op_eq"></a>ostream_iterator:: operator =

Operátor přiřazení používaný k implementaci výrazu output_iterator \* `i`  =  `x` pro zápis do výstupního datového proudu.

```cpp
ostream_iterator<Type, CharType, Traits>& operator=(const Type& val);
```

### <a name="parameters"></a>Parametry

\ *Val*
Hodnota objektu typu `Type`, který má být vložen do výstupního datového proudu.

### <a name="return-value"></a>Návratová hodnota

Operátor vloží hodnotu *Val* do výstupního datového proudu přidruženého k objektu, následovaný oddělovačem zadaným v [konstruktoru ostream_iterator](#ostream_iterator) (pokud existuje) a poté vrátí odkaz na `ostream_iterator`.

### <a name="remarks"></a>Poznámky

Požadavky na výstupní iterátor, které musí `ostream_iterator` splňovat, vyžadují pouze výraz \* `ii`  =  `t` být platné a neříká nic o operátoru nebo operátoru = sám o sobě. Tento členský operátor vrací `*this`.

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

## <a name="ostream_iterator"></a>ostream_iterator::ostream_iterator

Sestaví `ostream_iterator`, který je inicializován a oddělený pro zápis do výstupního datového proudu.

```cpp
ostream_iterator(
    ostream_type& _Ostr);

ostream_iterator(
    ostream_type& _Ostr,
    const CharType* _Delimiter);
```

### <a name="parameters"></a>Parametry

*_Ostr* \
Výstupní datový proud typu [ostream_iterator:: ostream_type](#ostream_type) , který se má iterovat.

*_Delimiter* \
Oddělovač, který je vložen do výstupního datového proudu mezi hodnotami.

### <a name="remarks"></a>Poznámky

První konstruktor inicializuje ukazatel výstupního datového proudu s `&_Ostr`. Ukazatel řetězce oddělovače označuje prázdný řetězec.

Druhý konstruktor inicializuje ukazatel výstupního datového proudu pomocí `&_Ostr` a ukazatele na řetězec oddělovače s *_Delimiter*.

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

## <a name="ostream_type"></a>ostream_iterator::ostream_type

Typ, který poskytuje typ datového proudu iterátoru.

```cpp
typedef basic_ostream<CharType, Traits> ostream_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro [basic_ostream](../standard-library/basic-ostream-class.md) <  `CharType`, `Traits` >, třída Stream hierarchie iostream –, která definuje objekty, které lze použít pro zápis.

### <a name="example"></a>Příklad

Příklad, jak deklarovat a používat `ostream_type`, naleznete v tématu [ostream_iterator](#ostream_iterator) .

## <a name="traits_type"></a>ostream_iterator::traits_type

Typ, který poskytuje typ znaků typu iterátoru.

```cpp
typedef Traits traits_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro parametr šablony `Traits`.

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

## <a name="see-also"></a>Viz také:

[\<iterator >](../standard-library/iterator.md) \
[Bezpečnost vlákna ve C++ standardní knihovně](../standard-library/thread-safety-in-the-cpp-standard-library.md) \
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)
