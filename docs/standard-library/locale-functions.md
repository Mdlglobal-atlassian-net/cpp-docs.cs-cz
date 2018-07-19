---
title: '&lt;národní prostředí&gt; funkce | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- locale/std::has_facet
- locale/std::isalnum
- locale/std::isalpha
- locale/std::iscntrl
- locale/std::isdigit
- locale/std::isgraph
- locale/std::islower
- locale/std::isprint
- locale/std::ispunct
- locale/std::isspace
- locale/std::isupper
- locale/std::isxdigit
- locale/std::tolower
- locale/std::toupper
- locale/std::use_facet
ms.assetid: b06c1ceb-33a7-48d3-8d4b-2714bbb27f14
helpviewer_keywords:
- std::has_facet [C++]
- std::isalnum [C++]
- std::isalpha [C++]
- std::iscntrl [C++]
- std::isdigit [C++]
- std::isgraph [C++]
- std::islower [C++]
- std::isprint [C++]
- std::ispunct [C++]
- std::isspace [C++]
- std::isupper [C++]
- std::isxdigit [C++]
- std::tolower [C++]
- std::toupper [C++]
- std::use_facet [C++]
ms.openlocfilehash: 8b3f6ed544bd4726b8bed2b63394a8b28c54c339
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38956069"
---
# <a name="ltlocalegt-functions"></a>&lt;národní prostředí&gt; funkce

||||
|-|-|-|
|[has_facet](#has_facet)|[isalnum](#isalnum)|[isalpha](#isalpha)|
|[iscntrl](#iscntrl)|[IsDigit](#isdigit)|[isgraph](#isgraph)|
|[islower](#islower)|[isprint](#isprint)|[ispunct](#ispunct)|
|[isspace](#isspace)|[isupper](#isupper)|[isxdigit](#isxdigit)|
|[ToLower](#tolower)|[ToUpper](#toupper)|[use_facet](#use_facet)|

## <a name="has_facet"></a>  has_facet

Ověřuje, zda je v zadaném národním prostředí uložena konkrétní omezující vlastnost.

```cpp
template <class Facet>
bool has_facet(const locale& Loc);
```

### <a name="parameters"></a>Parametry

*Loc* má být testována přítomnost omezující vlastnost národního prostředí.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud jsou testovány z hlediska; omezující vlastnost národního prostředí **false** Pokud tomu tak není.

### <a name="remarks"></a>Poznámky

Funkce šablon je užitečné pro kontrolu, jestli nonmandatory omezujících vlastností jsou uvedeny v národním prostředí než `use_facet` je volána k výjimce, která bude vyvolána, pokud by nebyl k dispozici vyhnout.

### <a name="example"></a>Příklad

```cpp
// locale_has_facet.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   bool result = has_facet <ctype<char> > ( loc );
   cout << result << endl;
}
```

```Output
1
```

## <a name="isalnum"></a>  isalnum

Ověřuje, zda je prvek v národním prostředí abecední, nebo číselný znak.

```cpp
template <class CharType>
bool isalnum(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>Parametry

*Ch* alfanumerické element má být testována.

*Loc* národní prostředí, který obsahuje alfanumerické element má být testována.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud testovaný prvek je alfanumerické; **false** nesplnění.

### <a name="example"></a>Příklad

```cpp
// locale_isalnum.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>

using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   bool result1 = isalnum ( 'L', loc);
   bool result2 = isalnum ( '@', loc);
   bool result3 = isalnum ( '3', loc);

   if ( result1 )
      cout << "The character 'L' in the locale is "
           << "alphanumeric." << endl;
   else
      cout << "The character 'L' in the locale is "
           << " not alphanumeric." << endl;

   if ( result2 )
      cout << "The character '@' in the locale is "
           << "alphanumeric." << endl;
   else
      cout << "The character '@' in the locale is "
           << " not alphanumeric." << endl;

   if ( result3 )
      cout << "The character '3' in the locale is "
           << "alphanumeric." << endl;
   else
      cout << "The character '3' in the locale is "
           << " not alphanumeric." << endl;
}
```

```Output
The character 'L' in the locale is alphanumeric.
The character '@' in the locale is  not alphanumeric.
The character '3' in the locale is alphanumeric.
```

## <a name="isalpha"></a>  isalpha

Testuje, zda je prvek v národním prostředí abecední znak.

```cpp
template <class CharType>
bool isalpha(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>Parametry

*Ch* elementu, který chcete testovat.

*Loc* národní prostředí, který obsahuje abecední element má být testována.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud testovaný prvek je abecední; **false** nesplnění.

### <a name="remarks"></a>Poznámky

Šablona funkce vrátí [use_facet](../standard-library/locale-functions.md#use_facet)< [ctype](../standard-library/ctype-class.md) \< **CharType**>> ( `Loc`). [je](../standard-library/ctype-class.md#is)( **ctype** \< **CharType**>:: **alfa**, `Ch`).

### <a name="example"></a>Příklad

```cpp
// locale_isalpha.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>

using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   bool result1 = isalpha ( 'L', loc);
   bool result2 = isalpha ( '@', loc);
   bool result3 = isalpha ( '3', loc);

   if ( result1 )
      cout << "The character 'L' in the locale is "
           << "alphabetic." << endl;
   else
      cout << "The character 'L' in the locale is "
           << " not alphabetic." << endl;

   if ( result2 )
      cout << "The character '@' in the locale is "
           << "alphabetic." << endl;
   else
      cout << "The character '@' in the locale is "
           << " not alphabetic." << endl;

   if ( result3 )
      cout << "The character '3' in the locale is "
           << "alphabetic." << endl;
   else
      cout << "The character '3' in the locale is "
           << " not alphabetic." << endl;
}
```

## <a name="iscntrl"></a>  iscntrl

Ověřuje, zda je prvek v národním prostředí řídicí znak.

```cpp
template <class CharType>
bool iscntrl(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>Parametry

*Ch* elementu, který chcete testovat.

*Loc* národní prostředí, který obsahuje element, který má být testována.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud testovaný prvek je řídicí znak; **false** nesplnění.

### <a name="remarks"></a>Poznámky

Šablona funkce vrátí [use_facet](../standard-library/locale-functions.md#use_facet)< [ctype](../standard-library/ctype-class.md) \< **CharType**>> ( `Loc`). [je](../standard-library/ctype-class.md#is)( **ctype** \< **CharType**>:: **stisknutím kláves CTRL +**, `Ch`).

### <a name="example"></a>Příklad

```cpp
// locale_iscntrl.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>

using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   bool result1 = iscntrl ( 'L', loc );
   bool result2 = iscntrl ( '\n', loc );
   bool result3 = iscntrl ( '\t', loc );

   if ( result1 )
      cout << "The character 'L' in the locale is "
           << "a control character." << endl;
   else
      cout << "The character 'L' in the locale is "
           << " not a control character." << endl;

   if ( result2 )
      cout << "The character-set 'backslash-n' in the locale\n is "
           << "a control character." << endl;
   else
      cout << "The character-set 'backslash-n' in the locale\n is "
           << " not a control character." << endl;

   if ( result3 )
      cout << "The character-set 'backslash-t' in the locale\n is "
           << "a control character." << endl;
   else
      cout << "The character-set 'backslash-n' in the locale \n is "
           << " not a control character." << endl;
}
```

## <a name="isdigit"></a>  IsDigit

Ověřuje, zda je prvek v národním prostředí číselný znak.

```cpp
template <class CharType>
bool isdigit(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>Parametry

*Ch* elementu, který chcete testovat.

*Loc* národní prostředí, který obsahuje element, který má být testována.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud testovaný prvek je číselný znak; **false** nesplnění.

### <a name="remarks"></a>Poznámky

Šablona funkce vrátí [use_facet](../standard-library/locale-functions.md#use_facet)< [ctype](../standard-library/ctype-class.md) \< **CharType**>> ( `Loc`). [je](../standard-library/ctype-class.md#is)( **ctype** \< **CharType**>:: **číslice**, `Ch`).

### <a name="example"></a>Příklad

```cpp
// locale_is_digit.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>

using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   bool result1 = isdigit ( 'L', loc );
   bool result2 = isdigit ( '@', loc );
   bool result3 = isdigit ( '3', loc );

   if ( result1 )
      cout << "The character 'L' in the locale is "
           << "a numeric character." << endl;
   else
      cout << "The character 'L' in the locale is "
           << " not a numeric character." << endl;

   if ( result2 )
      cout << "The character '@' in the locale is "
           << "a numeric character." << endl;
   else
      cout << "The character '@' in the locale is "
           << " not a numeric character." << endl;

   if ( result3 )
      cout << "The character '3' in the locale is "
           << "a numeric character." << endl;
   else
      cout << "The character '3' in the locale is "
           << " not a numeric character." << endl;
}
```

## <a name="isgraph"></a>  isgraph

Ověřuje, zda je prvek v národním prostředí alfanumerický znak nebo znak interpunkce.

```cpp
template <class CharType>
bool isgraph(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>Parametry

*Ch* elementu, který chcete testovat.

*Loc* národní prostředí, který obsahuje element, který má být testována.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud testovaný prvek je alfanumerické znaky nebo znak interpunkce; **false** nesplnění.

### <a name="remarks"></a>Poznámky

Šablona funkce vrátí [use_facet](../standard-library/locale-functions.md#use_facet)< [ctype](../standard-library/ctype-class.md) \< **CharType**>> ( `Loc`). [je](../standard-library/ctype-class.md#is)( **ctype** \< **CharType**>:: **grafu**, `Ch`).

### <a name="example"></a>Příklad

```cpp
// locale_is_graph.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>

using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   bool result1 = isgraph ( 'L', loc );
   bool result2 = isgraph ( '\t', loc );
   bool result3 = isgraph ( '.', loc );

   if ( result1 )
      cout << "The character 'L' in the locale is\n "
           << "an alphanumeric or punctuation character." << endl;
   else
      cout << "The character 'L' in the locale is\n "
           << " not an alphanumeric or punctuation character." << endl;

   if ( result2 )
      cout << "The character 'backslash-t' in the locale is\n "
           << "an alphanumeric or punctuation character." << endl;
   else
      cout << "The character 'backslash-t' in the locale is\n "
           << "not an alphanumeric or punctuation character." << endl;

   if ( result3 )
      cout << "The character '.' in the locale is\n "
           << "an alphanumeric or punctuation character." << endl;
   else
      cout << "The character '.' in the locale is\n "
           << " not an alphanumeric or punctuation character." << endl;
}
```

## <a name="islower"></a>  islower

Ověřuje, zda je prvek v národním prostředí malé písmeno.

```cpp
template <class CharType>
bool islower(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>Parametry

*Ch* elementu, který chcete testovat.

*Loc* národní prostředí, který obsahuje element, který má být testována.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud testovaný prvek je znak malého písmene; **false** nesplnění.

### <a name="remarks"></a>Poznámky

Šablona funkce vrátí [use_facet](../standard-library/locale-functions.md#use_facet)< [ctype](../standard-library/ctype-class.md) \< **CharType**>> ( `Loc`). [je](../standard-library/ctype-class.md#is)( **ctype** \< **CharType**>:: **nižší**, `Ch`).

### <a name="example"></a>Příklad

```cpp
// locale_islower.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>

using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   bool result1 = islower ( 'L', loc );
   bool result2 = islower ( 'n', loc );
   bool result3 = islower ( '3', loc );

   if ( result1 )
      cout << "The character 'L' in the locale is "
           << "a lowercase character." << endl;
   else
      cout << "The character 'L' in the locale is "
           << " not a lowercase character." << endl;

   if ( result2 )
      cout << "The character 'n' in the locale is "
           << "a lowercase character." << endl;
   else
      cout << "The character 'n' in the locale is "
           << " not a lowercase character." << endl;

   if ( result3 )
      cout << "The character '3' in the locale is "
           << "a lowercase character." << endl;
   else
      cout << "The character '3' in the locale is "
           << " not a lowercase character." << endl;
}
```

## <a name="isprint"></a>  isprint

Ověřuje, zda je prvek v národním prostředí znak, který lze vytisknout.

```cpp
template <class CharType>
bool isprint(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>Parametry

*Ch* elementu, který chcete testovat.

*Loc* národní prostředí, který obsahuje element, který má být testována.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud testovaný prvek je tisknutelný; **false** nesplnění.

### <a name="remarks"></a>Poznámky

Šablona funkce vrátí [use_facet](../standard-library/locale-functions.md#use_facet)< [ctype](../standard-library/ctype-class.md) \< **CharType**>> ( `Loc`). [je](../standard-library/ctype-class.md#is)( **ctype** \< **CharType**>:: **tisk**, `Ch`).

### <a name="example"></a>Příklad

```cpp
// locale_isprint.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc ( "German_Germany" );

   bool result1 = isprint ( 'L', loc );
   if ( result1 )
      cout << "The character 'L' in the locale is "
           << "a printable character." << endl;
   else
      cout << "The character 'L' in the locale is "
           << " not a printable character." << endl;

   bool result2 = isprint( '\t', loc );
   if ( result2 )
      cout << "The character 'backslash-t' in the locale is "
           << "a printable character." << endl;
   else
      cout << "The character 'backslash-t' in the locale is "
           << " not a printable character." << endl;

   bool result3 = isprint( '\n', loc );
   if ( result3 )
      cout << "The character 'backslash-n' in the locale is "
           << "a printable character." << endl;
   else
      cout << "The character 'backslash-n' in the locale is "
           << " not a printable character." << endl;
}
```

## <a name="ispunct"></a>  ispunct

Ověřuje, zda je prvek v národním prostředí znak interpunkce.

```cpp
template <class CharType>
bool ispunct(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>Parametry

*Ch* elementu, který chcete testovat.

*Loc* národní prostředí, který obsahuje element, který má být testována.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud testovaný prvek je znak interpunkce; **false** nesplnění.

### <a name="remarks"></a>Poznámky

Šablona funkce vrátí [use_facet](../standard-library/locale-functions.md#use_facet)`<`[ctype](../standard-library/ctype-class.md) \< **CharType**>> ( `Loc`). [je](../standard-library/ctype-class.md#is)( **ctype** \< **CharType**>:: **punct**, `Ch`).

### <a name="example"></a>Příklad

```cpp
// locale_ispunct.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>

using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   bool result1 = ispunct ( 'L', loc );
   bool result2 = ispunct ( ';', loc );
   bool result3 = ispunct ( '*', loc );

   if ( result1 )
      cout << "The character 'L' in the locale is "
           << "a punctuation character." << endl;
   else
      cout << "The character 'L' in the locale is "
           << " not a punctuation character." << endl;

   if ( result2 )
      cout << "The character ';' in the locale is "
           << "a punctuation character." << endl;
   else
      cout << "The character ';' in the locale is "
           << " not a punctuation character." << endl;

   if ( result3 )
      cout << "The character '*' in the locale is "
           << "a punctuation character." << endl;
   else
      cout << "The character '*' in the locale is "
           << " not a punctuation character." << endl;
}
```

## <a name="isspace"></a>  isspace

Ověřuje, zda je prvek v národním prostředí prázdný znak.

```cpp
template <class CharType>
bool isspace(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>Parametry

*Ch* elementu, který chcete testovat.

*Loc* národní prostředí, který obsahuje element, který má být testována.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud testovaný prvek je prázdný znak; **false** nesplnění.

### <a name="remarks"></a>Poznámky

Šablona funkce vrátí [use_facet](../standard-library/locale-functions.md#use_facet)< [ctype](../standard-library/ctype-class.md) \< **CharType**>> ( `Loc`). [je](../standard-library/ctype-class.md#is)( **ctype** \< **CharType**>:: **místo**, `Ch`).

### <a name="example"></a>Příklad

```cpp
// locale_isspace.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>

using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   bool result1 = isspace ( 'L', loc );
   bool result2 = isspace ( '\n', loc );
   bool result3 = isspace ( ' ', loc );

   if ( result1 )
      cout << "The character 'L' in the locale is "
           << "a whitespace character." << endl;
   else
      cout << "The character 'L' in the locale is "
           << " not a whitespace character." << endl;

   if ( result2 )
      cout << "The character 'backslash-n' in the locale is "
           << "a whitespace character." << endl;
   else
      cout << "The character 'backslash-n' in the locale is "
           << " not a whitespace character." << endl;

   if ( result3 )
      cout << "The character ' ' in the locale is "
           << "a whitespace character." << endl;
   else
      cout << "The character ' ' in the locale is "
           << " not a whitespace character." << endl;
}
```

## <a name="isupper"></a>  isupper

Testuje, zda je prvek v národním prostředí velkými písmeny.

```cpp
template <class CharType>
bool isupper(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>Parametry

*Ch* elementu, který chcete testovat.

*Loc* národní prostředí, který obsahuje element, který má být testována.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud testovaný prvek je znak velkého písmene; **false** nesplnění.

### <a name="remarks"></a>Poznámky

Šablona funkce vrátí [use_facet](../standard-library/locale-functions.md#use_facet)< [ctype](../standard-library/ctype-class.md) \< **CharType**>> ( `Loc`). [je](../standard-library/ctype-class.md#is)( **ctype** \< **CharType**>:: **horní**, `Ch`).

### <a name="example"></a>Příklad

```cpp
// locale_isupper.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>

using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   bool result1 = isupper ( 'L', loc );
   bool result2 = isupper ( 'n', loc );
   bool result3 = isupper ( '3', loc );

   if ( result1 )
      cout << "The character 'L' in the locale is "
           << "a uppercase character." << endl;
   else
      cout << "The character 'L' in the locale is "
           << " not a uppercase character." << endl;

   if ( result2 )
      cout << "The character 'n' in the locale is "
           << "a uppercase character." << endl;
   else
      cout << "The character 'n' in the locale is "
           << " not a uppercase character." << endl;

   if ( result3 )
      cout << "The character '3' in the locale is "
           << "a uppercase character." << endl;
   else
      cout << "The character '3' in the locale is "
           << " not a uppercase character." << endl;
}
```

## <a name="isxdigit"></a>  isxdigit

Ověřuje, zda je prvek v národním prostředí znak používaný ke znázornění šestnáctkového čísla.

```cpp
template <class CharType>
bool isxdigit(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>Parametry

*Ch* elementu, který chcete testovat.

*Loc* národní prostředí, který obsahuje element, který má být testována.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud testovaný prvek je znak používaný ke znázornění šestnáctkového čísla; **false** nesplnění.

### <a name="remarks"></a>Poznámky

Šablona funkce vrátí [use_facet](../standard-library/locale-functions.md#use_facet)< [ctype](../standard-library/ctype-class.md) \< **CharType**>> ( `Loc`). [je](../standard-library/ctype-class.md#is)( **ctype** \< **CharType**>:: **xdigit**, `Ch`).

Šestnáctkové číslice použít základní 16 pro reprezentaci čísel pomocí čísla 0 až 9 a písmena velká a malá písmena A až F představující desetinné číslice 0 až 15.

### <a name="example"></a>Příklad

```cpp
// locale_isxdigit.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>

using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   bool result1 = isxdigit ( '5', loc );
   bool result2 = isxdigit ( 'd', loc );
   bool result3 = isxdigit ( 'q', loc );

   if ( result1 )
      cout << "The character '5' in the locale is "
           << "a hexidecimal digit-character." << endl;
   else
      cout << "The character '5' in the locale is "
           << " not a hexidecimal digit-character." << endl;

   if ( result2 )
      cout << "The character 'd' in the locale is "
           << "a hexidecimal digit-character." << endl;
   else
      cout << "The character 'd' in the locale is "
           << " not a hexidecimal digit-character." << endl;

   if ( result3 )
      cout << "The character 'q' in the locale is "
           << "a hexidecimal digit-character." << endl;
   else
      cout << "The character 'q' in the locale is "
           << " not a hexidecimal digit-character." << endl;
}
```

## <a name="tolower"></a>  ToLower

Převede znak na malé písmeno.

```cpp
template <class CharType>
CharType tolower(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>Parametry

*ch* znak, který má být převeden na malá písmena.

*Loc* národní prostředí, který obsahuje znak, který má být převeden.

### <a name="return-value"></a>Návratová hodnota

Znak je převeden na malá písmena.

### <a name="remarks"></a>Poznámky

Šablona funkce vrátí [use_facet](../standard-library/locale-functions.md#use_facet)< [ctype](../standard-library/ctype-class.md) \< **CharType**>> ( `Loc`). [ToLower](../standard-library/ctype-class.md#tolower)( `Ch`).

### <a name="example"></a>Příklad

```cpp
// locale_tolower.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   char result1 = tolower ( 'H', loc );
   cout << "The lower case of 'H' in the locale is: "
        << result1 << "." << endl;
   char result2 = tolower ( 'h', loc );
   cout << "The lower case of 'h' in the locale is: "
        << result2 << "." << endl;
   char result3 = tolower ( '$', loc );
   cout << "The lower case of '$' in the locale is: "
        << result3 << "." << endl;
}
```

## <a name="toupper"></a>  ToUpper

Převede znak na velké písmeno.

```cpp
template <class CharType>
CharType toupper(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>Parametry

*ch* znak, který má být převeden na velká písmena.

*Loc* národní prostředí, který obsahuje znak, který má být převeden.

### <a name="return-value"></a>Návratová hodnota

Znak je převeden na velká písmena.

### <a name="remarks"></a>Poznámky

Šablona funkce vrátí [use_facet](../standard-library/locale-functions.md#use_facet)< [ctype](../standard-library/ctype-class.md) \< **CharType**>> ( `Loc`). [ToUpper](../standard-library/ctype-class.md#toupper)( `Ch`).

### <a name="example"></a>Příklad

```cpp
// locale_toupper.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   char result1 = toupper ( 'h', loc );
   cout << "The upper case of 'h' in the locale is: "
        << result1 << "." << endl;
   char result2 = toupper ( 'H', loc );
   cout << "The upper case of 'H' in the locale is: "
        << result2 << "." << endl;
   char result3 = toupper ( '$', loc );
   cout << "The upper case of '$' in the locale is: "
        << result3 << "." << endl;
}
```

## <a name="use_facet"></a>  use_facet

Vrátí odkaz na omezující vlastnost určitého typu uloženou v národním prostředí.

```cpp
template <class Facet>
const Facet& use_facet(const locale& Loc);
```

### <a name="parameters"></a>Parametry

*Loc* const národní prostředí obsahující typ omezující vlastnost, na kterou se odkazuje.

### <a name="return-value"></a>Návratová hodnota

Odkaz na omezující vlastnost třídy `Facet` obsažené v argumentu národního prostředí.

### <a name="remarks"></a>Poznámky

Odkaz na omezující vlastnost vrácené funkcí šablony zůstává v platnosti, dokud všechny kopie obsahující národního prostředí existuje. Pokud žádný takový objekt omezující vlastnosti třídy `Facet` je uveden v národním prostředí argument, funkce vyvolá výjimku `bad_cast` výjimky.

### <a name="example"></a>Příklad

```cpp
// locale_use_facet.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc1 ( "German_Germany" ), loc2 ( "English_Australia" );
   bool result1 = use_facet<ctype<char> > ( loc1 ).is(
   ctype_base::alpha, 'a'
);
   bool result2 = use_facet<ctype<char> > ( loc2 ).is( ctype_base::alpha, '!'
   );

   if ( result1 )
      cout << "The character 'a' in locale loc1 is alphabetic."
           << endl;
   else
      cout << "The character 'a' in locale loc1 is not alphabetic."
           << endl;

   if ( result2 )
      cout << "The character '!' in locale loc2 is alphabetic."
           << endl;
   else
      cout << "The character '!' in locale loc2 is not alphabetic."
           << endl;
}
```

```Output
The character 'a' in locale loc1 is alphabetic.
The character '!' in locale loc2 is not alphabetic.
```

## <a name="see-also"></a>Viz také:

[\<národní prostředí >](../standard-library/locale.md)<br/>
