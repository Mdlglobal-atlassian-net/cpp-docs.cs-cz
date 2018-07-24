---
title: ostream_iterator – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- iterator/std::ostream_iterator
- iterator/std::ostream_iterator::char_type
- iterator/std::ostream_iterator::ostream_type
- iterator/std::ostream_iterator::traits_type
dev_langs:
- C++
helpviewer_keywords:
- std::ostream_iterator [C++]
- std::ostream_iterator [C++], char_type
- std::ostream_iterator [C++], ostream_type
- std::ostream_iterator [C++], traits_type
ms.assetid: 24d842d3-9f45-4bf6-a697-62f5968f5a03
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 308254fded0ac38a794233fb3f4eacd4d7d6fd19
ms.sourcegitcommit: 7eadb968405bcb92ffa505e3ad8ac73483e59685
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2018
ms.locfileid: "39207916"
---
# <a name="ostreamiterator-class"></a>ostream_iterator – třída

Třída šablony ostream_iterator popisuje výstupní objekt iterátoru, který zapisuje po sobě jdoucí prvky do výstupního toku s extrakce `operator <<`.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Type class CharType = char class Traits = char_traits <CharType>>
class ostream_iterator
```

### <a name="parameters"></a>Parametry

*Typ* typ objektu, který má být vložen do výstupního datového proudu.

*CharType* typ, který představuje typ znaku pro `ostream_iterator`. Tento argument je nepovinný a výchozí hodnota je **char**.

*Vlastnosti* typ, který představuje typ znaku pro `ostream_iterator`. Tento argument je nepovinný a výchozí hodnota je `char_traits` \< *CharType >.*

Třída ostream_iterator musí splňovat požadavky na výstupní iterátor. Algoritmy lze zapsat přímo do výstupních toků pomocí `ostream_iterator`.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[ostream_iterator](#ostream_iterator)|Vytvoří `ostream_iterator` do výstupního datového proudu, který je inicializován a oddělen pro zápis.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[char_type](#char_type)|Typ, který poskytuje typ znaku pro `ostream_iterator`.|
|[ostream_type](#ostream_type)|Typ, který poskytuje typ toku pro `ostream_iterator`.|
|[traits_type](#traits_type)|Typ, který poskytuje typ vlastností `ostream_iterator`.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[Operator *](#op_star)|Operátor přesměrování používaný k implementaci výrazu výstupního iterátoru \* `i`  =  `x`.|
|[Operator ++](#op_add_add)|Nefunkční operátor přírůstku, který vrátí `ostream_iterator` na stejný objekt, který adresoval před voláním operace.|
|[operátor =](#op_eq)|Operátor přiřazení používaný k implementaci výrazu výstupního iterátoru \* `i`  =  `x` pro zápis do výstupního proudu.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<iterátor >

**Namespace:** std

## <a name="char_type"></a>  ostream_iterator::char_type

Typ, který poskytuje typ znaku pro iteraci.

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
\* Output:
The integers written to the output stream
by intOut are:
10
20
30
*\
```

## <a name="op_star"></a>  ostream_iterator::Operator *

Operátor přesměrování používaný k implementaci výrazu výstupního iterátoru \* *ii* = *x*.

```cpp
ostream_iterator<Type, CharType, Traits>& operator*();
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na `ostream_iterator`.

### <a name="remarks"></a>Poznámky

Požadavky na výstupní iterátor, který `ostream_iterator` musí splňovat vyžadují pouze výraz \* *ii* = *t* platné a neříká nic o **operátor** nebo `operator=` sami. Vrátí členský operátor v této implementaci  **\*to**.

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
\* Output:
Elements written to output stream:
10
20
30
*\
```

## <a name="op_add_add"></a>  ostream_iterator::Operator ++

Nefunkční operátor přírůstku, který vrátí `ostream_iterator` na stejný objekt, který adresoval před voláním operace.

```cpp
ostream_iterator<Type, CharType, Traits>& operator++();
ostream_iterator<Type, CharType, Traits> operator++(int);
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na `ostream_iterator`.

### <a name="remarks"></a>Poznámky

Tyto operátory členy obou vrátit  **\*to**.

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
\* Output:
Elements written to output stream:
10
20
30
*\
```

## <a name="op_eq"></a>  ostream_iterator::Operator =

Operátor přiřazení používaný k implementaci výrazu output_iterator \* `i`  =  `x` pro zápis do výstupního proudu.

```cpp
ostream_iterator<Type, CharType, Traits>& operator=(const Type& val);
```

### <a name="parameters"></a>Parametry

*Val* hodnotu objektu typu `Type` má být vložen do výstupního datového proudu.

### <a name="return-value"></a>Návratová hodnota

Operátor vloží *val* do výstupního datového proudu přidružená k objektu, za nímž následuje oddělovač zadané v [ostream_iterator konstruktor](#ostream_iterator) (pokud existuje) a vrátí odkaz na `ostream_iterator`.

### <a name="remarks"></a>Poznámky

Požadavky na výstupní iterátor, který `ostream_iterator` musí splňovat vyžadují pouze výraz \* `ii`  =  `t` platné a neříká nic o operátor nebo operátor = sami. Tento členský operátor vrátí `*this`.

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
\* Output:
Elements written to output stream:
10
20
30
*\
```

## <a name="ostream_iterator"></a>  ostream_iterator::ostream_iterator

Vytvoří `ostream_iterator` do výstupního datového proudu, který je inicializován a oddělen pro zápis.

```cpp
ostream_iterator(
    ostream_type& _Ostr);

ostream_iterator(
    ostream_type& _Ostr,
    const CharType* _Delimiter);
```

### <a name="parameters"></a>Parametry

*_Ostr* výstupního datového proudu typu [ostream_iterator::ostream_type](#ostream_type) chcete provést iteraci.

*_Mezeru* oddělovač, který je vložen do výstupního datového proudu mezi hodnotami.

### <a name="remarks"></a>Poznámky

První konstruktor inicializuje ukazatele výstupní datový proud s `&_Ostr`. Ukazatel na řetězec oddělovače určí prázdný řetězec.

Druhý konstruktor inicializuje ukazatele výstupní datový proud s `&_Ostr` a ukazatel na řetězec oddělovače s *_mezeru*.

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
\* Output:
10
20
Elements output without delimiter: 123456
Elements output with delimiter: 1 : 2 : 3 : 4 : 5 : 6 :
*\
```

## <a name="ostream_type"></a>  ostream_iterator::ostream_type

Typ, který poskytuje typ datového proudu iterátoru.

```cpp
typedef basic_ostream<CharType, Traits> ostream_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro [basic_ostream –](../standard-library/basic-ostream-class.md)< `CharType`, `Traits`>, datový proud třída iostream – hierarchie, která definuje objekty, které lze použít pro zápis.

### <a name="example"></a>Příklad

Zobrazit [ostream_iterator](#ostream_iterator) příklad toho, jak deklarace a používání `ostream_type`.

## <a name="traits_type"></a>  ostream_iterator::traits_type

Typ, který poskytuje typ vlastností znaku iterátoru.

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
\* Output:
The integers written to output stream
by intOut are:
1
10
100
*\
```

## <a name="see-also"></a>Viz také:

[\<iterátor >](../standard-library/iterator.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)<br/>
