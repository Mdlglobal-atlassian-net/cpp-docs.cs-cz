---
title: '&lt;národní&gt; prostředí funkce'
ms.date: 11/04/2016
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
ms.openlocfilehash: 6ebb1b1c80d5c2da19610a15e628fcbab5220719
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81351729"
---
# <a name="ltlocalegt-functions"></a>&lt;národní&gt; prostředí funkce

||||
|-|-|-|
|[has_facet](#has_facet)|[isalnum](#isalnum)|[isalpha](#isalpha)|
|[iscntrl](#iscntrl)|[isdigit](#isdigit)|[isgraf](#isgraph)|
|[je nižší](#islower)|[isprint](#isprint)|[ispunct](#ispunct)|
|[isspace](#isspace)|[isupper](#isupper)|[isxdigit](#isxdigit)|
|[Tolower](#tolower)|[Toupper](#toupper)|[use_facet](#use_facet)|

## <a name="has_facet"></a><a name="has_facet"></a>has_facet

Ověřuje, zda je v zadaném národním prostředí uložena konkrétní omezující vlastnost.

```cpp
template <class Facet>
bool has_facet(const locale& Loc);
```

### <a name="parameters"></a>Parametry

*Loc*\
Národní prostředí, které má být testováno na přítomnost omezující saze.

### <a name="return-value"></a>Návratová hodnota

**true,** pokud má národní prostředí testovaný aspekt; **false,** pokud tomu tak není.

### <a name="remarks"></a>Poznámky

Funkce šablony je užitečná pro kontrolu, zda jsou nepovinné `use_facet` omezující vlastnosti uvedeny v národním prostředí před je volána, aby se zabránilo výjimku, která by byla vyvolána, pokud nebyly k dispozici.

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

## <a name="isalnum"></a><a name="isalnum"></a>isalnum

Ověřuje, zda je prvek v národním prostředí abecední, nebo číselný znak.

```cpp
template <class CharType>
bool isalnum(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>Parametry

*Ch*\
Alfanumerický prvek, který má být testován.

*Loc*\
Národní prostředí obsahující alfanumerický prvek, který má být testován.

### <a name="return-value"></a>Návratová hodnota

**true,** pokud je testovaný prvek alfanumerický; **false,** pokud tomu tak není.

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

## <a name="isalpha"></a><a name="isalpha"></a>isalpha

Testuje, zda je prvek v národním prostředí abecední znak.

```cpp
template <class CharType>
bool isalpha(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>Parametry

*Ch*\
Prvek, který má být testován.

*Loc*\
Národní prostředí obsahující abecední prvek, který má být testován.

### <a name="return-value"></a>Návratová hodnota

**true,** pokud je testovaný prvek abecední; **false,** pokud tomu tak není.

### <a name="remarks"></a>Poznámky

Funkce šablony vrátí [use_facet](../standard-library/locale-functions.md#use_facet)< [ctype](../standard-library/ctype-class.md) \< `Loc` **CharType**> >( ). [is](../standard-library/ctype-class.md#is)( **ctype** \< **CharType**>:: **alfa**, `Ch`).

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

## <a name="iscntrl"></a><a name="iscntrl"></a>iscntrl

Ověřuje, zda je prvek v národním prostředí řídicí znak.

```cpp
template <class CharType>
bool iscntrl(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>Parametry

*Ch*\
Prvek, který má být testován.

*Loc*\
Národní prostředí obsahující prvek, který má být testován.

### <a name="return-value"></a>Návratová hodnota

**true,** pokud je testovaný prvek řídicí znak; **false,** pokud tomu tak není.

### <a name="remarks"></a>Poznámky

Funkce šablony vrátí [use_facet](../standard-library/locale-functions.md#use_facet)< [ctype](../standard-library/ctype-class.md) \< `Loc` **CharType**> >( ). [is](../standard-library/ctype-class.md#is)( **ctype** \< **CharType**>:: `Ch` **cntrl**, ).

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

## <a name="isdigit"></a><a name="isdigit"></a>isdigit

Ověřuje, zda je prvek v národním prostředí číselný znak.

```cpp
template <class CharType>
bool isdigit(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>Parametry

*Ch*\
Prvek, který má být testován.

*Loc*\
Národní prostředí obsahující prvek, který má být testován.

### <a name="return-value"></a>Návratová hodnota

**true,** pokud je testovaný prvek číselným znakem; **false,** pokud tomu tak není.

### <a name="remarks"></a>Poznámky

Funkce šablony vrátí [use_facet](../standard-library/locale-functions.md#use_facet)< [ctype](../standard-library/ctype-class.md) \< `Loc` **CharType**> >( ). [is](../standard-library/ctype-class.md#is)( **ctype** \< **CharType**>:: **číslice**, `Ch`).

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

## <a name="isgraph"></a><a name="isgraph"></a>isgraf

Ověřuje, zda je prvek v národním prostředí alfanumerický znak nebo znak interpunkce.

```cpp
template <class CharType>
bool isgraph(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>Parametry

*Ch*\
Prvek, který má být testován.

*Loc*\
Národní prostředí obsahující prvek, který má být testován.

### <a name="return-value"></a>Návratová hodnota

**true,** pokud je testovaný prvek alfanumerický nebo interpunkční znak; **false,** pokud tomu tak není.

### <a name="remarks"></a>Poznámky

Funkce šablony vrátí [use_facet](../standard-library/locale-functions.md#use_facet)< [ctype](../standard-library/ctype-class.md) \< `Loc` **CharType**> >( ). [is](../standard-library/ctype-class.md#is)( **ctype** \< **CharType**>:: **graf**, `Ch`).

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

## <a name="islower"></a><a name="islower"></a>je nižší

Ověřuje, zda je prvek v národním prostředí malé písmeno.

```cpp
template <class CharType>
bool islower(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>Parametry

*Ch*\
Prvek, který má být testován.

*Loc*\
Národní prostředí obsahující prvek, který má být testován.

### <a name="return-value"></a>Návratová hodnota

**true,** pokud je testovaný prvek malý znak; **false,** pokud tomu tak není.

### <a name="remarks"></a>Poznámky

Funkce šablony vrátí [use_facet](../standard-library/locale-functions.md#use_facet)< [ctype](../standard-library/ctype-class.md) \< `Loc` **CharType**> >( ). [is](../standard-library/ctype-class.md#is)( **ctype** \< **CharType**>:: **nižší**, `Ch`).

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

## <a name="isprint"></a><a name="isprint"></a>isprint

Ověřuje, zda je prvek v národním prostředí znak, který lze vytisknout.

```cpp
template <class CharType>
bool isprint(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>Parametry

*Ch*\
Prvek, který má být testován.

*Loc*\
Národní prostředí obsahující prvek, který má být testován.

### <a name="return-value"></a>Návratová hodnota

**true,** pokud je testovaný prvek tisknutelný; **false,** pokud tomu tak není.

### <a name="remarks"></a>Poznámky

Funkce šablony vrátí [use_facet](../standard-library/locale-functions.md#use_facet)< [ctype](../standard-library/ctype-class.md) \< `Loc` **CharType**> >( ). [is](../standard-library/ctype-class.md#is)( **ctype** \< **CharType**>:: **print**, `Ch`).

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

## <a name="ispunct"></a><a name="ispunct"></a>ispunct

Ověřuje, zda je prvek v národním prostředí znak interpunkce.

```cpp
template <class CharType>
bool ispunct(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>Parametry

*Ch*\
Prvek, který má být testován.

*Loc*\
Národní prostředí obsahující prvek, který má být testován.

### <a name="return-value"></a>Návratová hodnota

**true,** pokud je testovaný prvek interpunkční znak; **false,** pokud tomu tak není.

### <a name="remarks"></a>Poznámky

Funkce šablony vrátí [use_facet](../standard-library/locale-functions.md#use_facet)`<`[ctype](../standard-library/ctype-class.md) \< `Loc` **CharType**> >( ). [is](../standard-library/ctype-class.md#is)( **ctype** \< **CharType**>:: **punct**, `Ch`).

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

## <a name="isspace"></a><a name="isspace"></a>isspace

Ověřuje, zda je prvek v národním prostředí prázdný znak.

```cpp
template <class CharType>
bool isspace(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>Parametry

*Ch*\
Prvek, který má být testován.

*Loc*\
Národní prostředí obsahující prvek, který má být testován.

### <a name="return-value"></a>Návratová hodnota

**true,** pokud testovaný prvek je znak prázdné znaky; **false,** pokud tomu tak není.

### <a name="remarks"></a>Poznámky

Funkce šablony vrátí [use_facet](../standard-library/locale-functions.md#use_facet)< [ctype](../standard-library/ctype-class.md) \< `Loc` **CharType**> >( ). [is](../standard-library/ctype-class.md#is)( **ctype** \< **CharType**>:: **mezera**, `Ch`).

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

## <a name="isupper"></a><a name="isupper"></a>isupper

Testuje, zda je prvek v národním prostředí velkými písmeny.

```cpp
template <class CharType>
bool isupper(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>Parametry

*Ch*\
Prvek, který má být testován.

*Loc*\
Národní prostředí obsahující prvek, který má být testován.

### <a name="return-value"></a>Návratová hodnota

**true,** pokud je testovaný prvek velkými písmeny; **false,** pokud tomu tak není.

### <a name="remarks"></a>Poznámky

Funkce šablony vrátí [use_facet](../standard-library/locale-functions.md#use_facet)< [ctype](../standard-library/ctype-class.md) \< `Loc` **CharType**> >( ). [is](../standard-library/ctype-class.md#is)( **ctype** \< **CharType**>:: **horní**, `Ch`).

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

## <a name="isxdigit"></a><a name="isxdigit"></a>isxdigit

Ověřuje, zda je prvek v národním prostředí znak používaný ke znázornění šestnáctkového čísla.

```cpp
template <class CharType>
bool isxdigit(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>Parametry

*Ch*\
Prvek, který má být testován.

*Loc*\
Národní prostředí obsahující prvek, který má být testován.

### <a name="return-value"></a>Návratová hodnota

**true,** pokud je testovaný prvek znak emitovaný k reprezentaci šestnáctkového čísla; **false,** pokud tomu tak není.

### <a name="remarks"></a>Poznámky

Funkce šablony vrátí [use_facet](../standard-library/locale-functions.md#use_facet)< [ctype](../standard-library/ctype-class.md) \< `Loc` **CharType**> >( ). [is](../standard-library/ctype-class.md#is)( **ctype** \< **CharType**>:: **xdigit**, `Ch`).

Šestnáctkové číslice používají základní 16 představují čísla, pomocí čísla 0 až 9 plus malá a velká písmena A až F představují desetinná čísla 0 až 15.

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

## <a name="tolower"></a><a name="tolower"></a>Tolower

Převede znak na malé písmeno.

```cpp
template <class CharType>
CharType tolower(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>Parametry

*Ch*\
Znak, který má být převeden na malá písmena.

*Loc*\
Národní prostředí obsahující znak, který má být převeden.

### <a name="return-value"></a>Návratová hodnota

Znak převedený na malá písmena.

### <a name="remarks"></a>Poznámky

Funkce šablony vrátí [use_facet](../standard-library/locale-functions.md#use_facet)< [ctype](../standard-library/ctype-class.md) \< `Loc` **CharType**> >( ). [dolní](../standard-library/ctype-class.md#tolower)( `Ch`).

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

## <a name="toupper"></a><a name="toupper"></a>Toupper

Převede znak na velké písmeno.

```cpp
template <class CharType>
CharType toupper(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>Parametry

*Ch*\
Znak, který má být převeden na velká písmena.

*Loc*\
Národní prostředí obsahující znak, který má být převeden.

### <a name="return-value"></a>Návratová hodnota

Znak převedený na velká písmena.

### <a name="remarks"></a>Poznámky

Funkce šablony vrátí [use_facet](../standard-library/locale-functions.md#use_facet)< [ctype](../standard-library/ctype-class.md) \< `Loc` **CharType**> >( ). [kvečeří](../standard-library/ctype-class.md#toupper)( `Ch`).

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

## <a name="use_facet"></a><a name="use_facet"></a>use_facet

Vrátí odkaz na omezující vlastnost určitého typu uloženou v národním prostředí.

```cpp
template <class Facet>
const Facet& use_facet(const locale& Loc);
```

### <a name="parameters"></a>Parametry

*Loc*\
Const národní prostředí obsahující typ omezující souvislost odkazuje.

### <a name="return-value"></a>Návratová hodnota

Odkaz na omezující souvislost `Facet` třídy obsažené v národním prostředí argumentu.

### <a name="remarks"></a>Poznámky

Odkaz na omezující vlastnost vrácenou funkcí šablony zůstává platný, dokud existuje jakákoli kopie obsahujícího národního prostředí. Pokud žádný takový omezující `Facet` název objekt třídy je uveden v `bad_cast` národním prostředí argumentu, funkce vyvolá výjimku.

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

## <a name="see-also"></a>Viz také

[\<>národního prostředí](../standard-library/locale.md)
