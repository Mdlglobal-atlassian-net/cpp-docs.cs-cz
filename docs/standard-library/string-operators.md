---
title: '&lt;operátory řetězců&gt;'
ms.date: 11/04/2016
f1_keywords:
- string/std::operator!=
- string/std::operator&gt;
- string/std::operator&gt;&gt;
- string/std::operator&gt;=
- string/std::operator&lt;
- string/std::operator&lt;&lt;
- string/std::operator&lt;=
- string/std::operator+
- string/std::operator==
ms.assetid: 33ce8f05-06c7-45d3-a0cb-bcd27cf93910
helpviewer_keywords:
- std::operator!= (string)
- std::operator&gt; (string)
- std::operator&gt;&gt; (string)
- std::operator&gt;= (string)
- std::operator&lt; (string)
- std::operator&lt;&lt; (string)
- std::operator&lt;= (string), std::operator== (string)
ms.openlocfilehash: fef2eb784eca9c9eabbdcd727b051d5c2a4ccfd2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376651"
---
# <a name="ltstringgt-operators"></a>&lt;operátory řetězců&gt;

||||
|-|-|-|
|[operátor!=](#op_neq)|[Operátor&gt;](#op_gt)|[Operátor&gt;&gt;](#op_gt_gt)|
|[Operátor&gt;=](#op_gt_eq)|[Operátor&lt;](#op_lt)|[Operátor&lt;&lt;](#op_lt_lt)|
|[Operátor&lt;=](#op_lt_eq)|[operátor+](#op_add)|[operátor==](#op_eq_eq)|

## <a name="operator"></a><a name="op_add"></a>operátor+

Zřetězí dva objekty řetězce.

```cpp
template <class CharType, class Traits, class Allocator>
basic_string<CharType, Traits, Allocator> operator+(
    const basic_string<CharType, Traits, Allocator>& left,
    const basic_string<CharType, Traits, Allocator>& right);

template <class CharType, class Traits, class Allocator>
basic_string<CharType, Traits, Allocator> operator+(
    const basic_string<CharType, Traits, Allocator>& left,
    const CharType* right);

template <class CharType, class Traits, class Allocator>
basic_string<CharType, Traits, Allocator> operator+(
    const basic_string<CharType, Traits, Allocator>& left,
    const CharType right);

template <class CharType, class Traits, class Allocator>
basic_string<CharType, Traits, Allocator> operator+(
    const CharType* left,
    const basic_string<CharType, Traits, Allocator>& right);

template <class CharType, class Traits, class Allocator>
basic_string<CharType, Traits, Allocator> operator+(
    const CharType left,
    const basic_string<CharType, Traits, Allocator>& right);

template <class CharType, class Traits, class Allocator>
basic_string<CharType, Traits, Allocator>&& operator+(
    const basic_string<CharType, Traits, Allocator>& left,
    const basic_string<CharType, Traits, Allocator>&& right);

template <class CharType, class Traits, class Allocator>
basic_string<CharType, Traits, Allocator>&& operator+(
    const basic_string<CharType, Traits, Allocator>&& left,
    const basic_string<CharType, Traits, Allocator>& right);

template <class CharType, class Traits, class Allocator>
basic_string<CharType, Traits, Allocator>&& operator+(
    const basic_string<CharType, Traits, Allocator>&& left,
    const basic_string<CharType, Traits, Allocator>&& right);

template <class CharType, class Traits, class Allocator>
basic_string<CharType, Traits, Allocator>&& operator+(
    const basic_string<CharType, Traits, Allocator>&& left,
    const CharType* right);

template <class CharType, class Traits, class Allocator>
basic_string<CharType, Traits, Allocator>&& operator+(
    const basic_string<CharType, Traits, Allocator>&& left,
    CharType right);

template <class CharType, class Traits, class Allocator>
basic_string<CharType, Traits, Allocator>&& operator+(
    const CharType* left,
    const basic_string<CharType, Traits, Allocator>&& right);

template <class CharType, class Traits, class Allocator>
basic_string<CharType, Traits, Allocator>&& operator+(
    CharType left,
    const basic_string<CharType, Traits, Allocator>&& right);
```

### <a name="parameters"></a>Parametry

*Vlevo*\
Řetězec ve stylu C nebo `basic_string` objekt typu, který má být zřetězen.

*Právo*\
Řetězec ve stylu C nebo `basic_string` objekt typu, který má být zřetězen.

### <a name="return-value"></a>Návratová hodnota

Řetězec, který je zřetězení vstupní řetězce.

### <a name="remarks"></a>Poznámky

Funkce každé `operator+` přetížení zřetězit dva objekty šablony třídy [basic_string Class](../standard-library/basic-string-class.md). Všechny účinně `basic_string< CharType, Traits, Allocator>(Left).append(right)`vrátit . Další informace naleznete v [tématu append](../standard-library/basic-string-class.md#append).

### <a name="example"></a>Příklad

```cpp
// string_op_con.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   // Declaring an object of type basic_string<char>
   string s1 ( "anti" );
   string s2 ( "gravity" );
   cout << "The basic_string s1 = " << s1 << "." << endl;
   cout << "The basic_string s2 = " << s2 << "." << endl;

   // Declaring a C-style string
   char *s3 = "heroine";
   cout << "The C-style string s3 = " << s3 << "." << endl;

   // Declaring a character constant
   char c1 = '!';
   cout << "The character constant c1 = " << c1 << "." << endl;

   // First member function: concatenates an  object
   // of type basic_string with an object of type basic_string
   string s12 = s1 + s2;
   cout << "The string concatenating s1 & s2 is: " << s12 << endl;

   // Second & fourth member functions: concatenate an object
   // of type basic_string with an object of C-syle string type
   string s1s3 = s1 + s3;
   cout << "The string concatenating s1 & s3 is: " << s1s3 << endl;

   // Third & fifth member functions: concatenate an object
   // of type basic_string with a character constant
   string s1s3c1 = s1s3 + c1;
   cout << "The string concatenating s1 & s3 is: " << s1s3c1 << endl;
}
```

```Output
The basic_string s1 = anti.
The basic_string s2 = gravity.
The C-style string s3 = heroine.
The character constant c1 = !.
The string concatenating s1 & s2 is: antigravity
The string concatenating s1 & s3 is: antiheroine
The string concatenating s1 & s3 is: antiheroine!
```

## <a name="operator"></a><a name="op_neq"></a>operátor!=

Testy, pokud objekt řetězce na levé straně operátoru není rovna objektu řetězce na pravé straně.

```cpp
template <class CharType, class Traits, class Allocator>
bool operator!=(
    const basic_string<CharType, Traits, Allocator>& left,
    const basic_string<CharType, Traits, Allocator>& right);

template <class CharType, class Traits, class Allocator>
bool operator!=(
    const basic_string<CharType, Traits, Allocator>& left,
const CharType* right);

template <class CharType, class Traits, class Allocator>
bool operator!=(
    const CharType* left,
    const basic_string<CharType, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*Vlevo*\
Řetězec ve stylu C nebo `basic_string` objekt typu, který má být porovnán.

*Právo*\
Řetězec ve stylu C nebo `basic_string` objekt typu, který má být porovnán.

### <a name="return-value"></a>Návratová hodnota

**true** pokud objekt řetězce na levé straně operátoru není lexicograficky rovna objektu řetězce na pravé straně; jinak **false**.

### <a name="remarks"></a>Poznámky

Porovnání mezi řetězcovými objekty je založeno na párovém lexikografickém porovnání jejich znaků. Dva řetězce jsou stejné, pokud mají stejný počet znaků a jejich příslušné hodnoty znaků jsou stejné. V opačném případě jsou nerovné.

### <a name="example"></a>Příklad

```cpp
// string_op_ne.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // Declaring an objects of type basic_string<char>
   string s1 ( "pluck" );
   string s2 ( "strum" );
   cout << "The basic_string s1 = " << s1 << "." << endl;
   cout << "The basic_string s2 = " << s2 << "." << endl;

   // Declaring a C-style string
   char *s3 = "pluck";
   cout << "The C-style string s3 = " << s3 << "." << endl;

   // First member function: comparison between left-side object
   // of type basic_string & right-side object of type basic_string
   if ( s1 != s2 )
      cout << "The strings s1 & s2 are not equal." << endl;
   else
      cout << "The strings s1 & s2 are equal." << endl;

   // Second member function: comparison between left-side object
   // of type basic_string & right-side object of C-syle string type
   if ( s1 != s3 )
      cout << "The strings s1 & s3 are not equal." << endl;
   else
      cout << "The strings s1 & s3 are equal." << endl;

   // Third member function: comparison between left-side object
   // of C-syle string type & right-side object of type basic_string
   if ( s3 != s2 )
      cout << "The strings s3 & s2 are not equal." << endl;
   else
      cout << "The strings s3 & s2 are equal." << endl;
}
```

```Output
The basic_string s1 = pluck.
The basic_string s2 = strum.
The C-style string s3 = pluck.
The strings s1 & s2 are not equal.
The strings s1 & s3 are equal.
The strings s3 & s2 are not equal.
```

## <a name="operator"></a><a name="op_eq_eq"></a>operátor==

Testy, pokud objekt řetězce na levé straně operátoru se rovná objektu řetězce na pravé straně.

```cpp
template <class CharType, class Traits, class Allocator>
bool operator==(
    const basic_string<CharType, Traits, Allocator>& left,
    const basic_string<CharType, Traits, Allocator>& right);

template <class CharType, class Traits, class Allocator>
bool operator==(
    const basic_string<CharType, Traits, Allocator>& left,
    const CharType* right);

template <class CharType, class Traits, class Allocator>
bool operator==(
    const CharType* left,
    const basic_string<CharType, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*Vlevo*\
Řetězec ve stylu C nebo `basic_string` objekt typu, který má být porovnán.

*Právo*\
Řetězec ve stylu C nebo `basic_string` objekt typu, který má být porovnán.

### <a name="return-value"></a>Návratová hodnota

**true** pokud je objekt řetězce na levé straně operátoru lexikograficky roven objektu řetězce na pravé straně; jinak **false**.

### <a name="remarks"></a>Poznámky

Porovnání mezi řetězcovými objekty je založeno na párovém lexikografickém porovnání jejich znaků. Dva řetězce jsou stejné, pokud mají stejný počet znaků a jejich příslušné hodnoty znaků jsou stejné. V opačném případě jsou nerovné.

### <a name="example"></a>Příklad

```cpp
// string_op_eq.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // Declaring an objects of type basic_string<char>
   string s1 ( "pluck" );
   string s2 ( "strum" );
   cout << "The basic_string s1 = " << s1 << "." << endl;
   cout << "The basic_string s2 = " << s2 << "." << endl;

   // Declaring a C-style string
   char *s3 = "pluck";
   cout << "The C-style string s3 = " << s3 << "." << endl;

   // First member function: comparison between left-side object
   // of type basic_string & right-side object of type basic_string
   if ( s1 == s2 )
      cout << "The strings s1 & s2 are equal." << endl;
   else
      cout << "The strings s1 & s2 are not equal." << endl;

   // Second member function: comparison between left-side object
   // of type basic_string & right-side object of C-syle string type
   if ( s1 == s3 )
      cout << "The strings s1 & s3 are equal." << endl;
   else
      cout << "The strings s1 & s3 are not equal." << endl;

   // Third member function: comparison between left-side object
   // of C-syle string type & right-side object of type basic_string
   if ( s3 == s2 )
      cout << "The strings s3 & s2 are equal." << endl;
   else
      cout << "The strings s3 & s2 are not equal." << endl;
}
```

```Output
The basic_string s1 = pluck.
The basic_string s2 = strum.
The C-style string s3 = pluck.
The strings s1 & s2 are not equal.
The strings s1 & s3 are equal.
The strings s3 & s2 are not equal.
```

## <a name="operatorlt"></a><a name="op_lt"></a>Operátor&lt;

Testy, pokud objekt řetězce na levé straně operátoru je menší než objekt řetězce na pravé straně.

```cpp
template <class CharType, class Traits, class Allocator>
bool operator<(
    const basic_string<CharType, Traits, Allocator>& left,
    const basic_string<CharType, Traits, Allocator>& right);

template <class CharType, class Traits, class Allocator>
bool operator<(
    const basic_string<CharType, Traits, Allocator>& left,
    const CharType* right);

template <class CharType, class Traits, class Allocator>
bool operator<(
    const CharType* left,
    const basic_string<CharType, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*Vlevo*\
Řetězec ve stylu C nebo `basic_string` objekt typu, který má být porovnán.

*Právo*\
Řetězec ve stylu C nebo `basic_string` objekt typu, který má být porovnán.

### <a name="return-value"></a>Návratová hodnota

**true** pokud je objekt řetězce na levé straně operátoru lexikograficky menší než objekt řetězce na pravé straně; jinak **false**.

### <a name="remarks"></a>Poznámky

Lexikografické porovnání mezi řetězci je porovná znak po znaku, dokud:

- Najde dva odpovídající znaky nerovné a výsledek jejich porovnání je přijata v důsledku porovnání mezi řetězci.

- Nenajde žádné nerovnosti, ale jeden řetězec má více znaků než druhý a kratší řetězec je považován za menší než delší řetězec.

- Nenajde žádné nerovnosti a zjistí, že řetězce mají stejný počet znaků, a proto řetězce jsou stejné.

### <a name="example"></a>Příklad

```cpp
// string_op_lt.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   // Declaring an objects of type basic_string<char>
   string s1 ( "strict" );
   string s2 ( "strum" );
   cout << "The basic_string s1 = " << s1 << "." << endl;
   cout << "The basic_string s2 = " << s2 << "." << endl;

   // Declaring a C-style string
   char *s3 = "strict";
   cout << "The C-style string s3 = " << s3 << "." << endl;

   // First member function: comparison between left-side object
   // of type basic_string & right-side object of type basic_string
   if ( s1 < s2 )
      cout << "The string s1 is less than the string s2." << endl;
   else
      cout << "The string s1 is not less than the string s2." << endl;

   // Second member function: comparison between left-hand object
   // of type basic_string & right-hand object of C-syle string type
   if ( s1 < s3 )
      cout << "The string s1 is less than the string s3." << endl;
   else
      cout << "The string s1 is not less than the string s3." << endl;

   // Third member function: comparison between left-hand object
   // of C-syle string type & right-hand object of type basic_string
   if ( s3 < s2 )
      cout << "The string s3 is less than the string s2." << endl;
   else
      cout << "The string s3 is not less than the string s2." << endl;
}
```

```Output
The basic_string s1 = strict.
The basic_string s2 = strum.
The C-style string s3 = strict.
The string s1 is less than the string s2.
The string s1 is not less than the string s3.
The string s3 is less than the string s2.
```

## <a name="operatorlt"></a><a name="op_lt_eq"></a>Operátor&lt;=

Testy, pokud objekt řetězce na levé straně operátoru je menší nebo rovna objektu řetězce na pravé straně.

```cpp
template <class CharType, class Traits, class Allocator>
bool operator<=(
    const basic_string<CharType, Traits, Allocator>& left,
    const basic_string<CharType, Traits, Allocator>& right);

template <class CharType, class Traits, class Allocator>
bool operator<=(
    const basic_string<CharType, Traits, Allocator>& left,
    const CharType* right);

template <class CharType, class Traits, class Allocator>
bool operator<=(
    const CharType* left,
    const basic_string<CharType, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*Vlevo*\
Řetězec ve stylu C nebo `basic_string` objekt typu, který má být porovnán.

*Právo*\
Řetězec ve stylu C nebo `basic_string` objekt typu, který má být porovnán.

### <a name="return-value"></a>Návratová hodnota

**true** pokud je objekt řetězce na levé straně operátoru lexikograficky menší nebo roven objektu řetězce na pravé straně; jinak **false**.

### <a name="remarks"></a>Poznámky

Lexikografické porovnání mezi řetězci je porovná znak po znaku, dokud:

- Najde dva odpovídající znaky nerovné a výsledek jejich porovnání je přijata v důsledku porovnání mezi řetězci.

- Nenajde žádné nerovnosti, ale jeden řetězec má více znaků než druhý a kratší řetězec je považován za menší než delší řetězec.

- Nenajde žádné nerovnosti a zjistí, že řetězce mají stejný počet znaků, takže řetězce jsou stejné.

### <a name="example"></a>Příklad

```cpp
// string_op_le.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // Declaring an objects of type basic_string<char>
   string s1 ( "strict" );
   string s2 ( "strum" );
   cout << "The basic_string s1 = " << s1 << "." << endl;
   cout << "The basic_string s2 = " << s2 << "." << endl;

   // Declaring a C-style string
   char *s3 = "strict";
   cout << "The C-style string s3 = " << s3 << "." << endl;

   // First member function: comparison between left-side object
   // of type basic_string & right-side object of type basic_string
   if ( s1 <= s2 )
      cout << "The string s1 is less than or equal to "
           << "the string s2." << endl;
   else
      cout << "The string s1 is greater than "
           << "the string s2." << endl;

   // Second member function: comparison between left-side object
   // of type basic_string & right-side object of C-syle string type
   if ( s1 <= s3 )
      cout << "The string s1 is less than or equal to "
           << "the string s3." << endl;
   else
      cout << "The string s1 is greater than "
           << "the string s3." << endl;

   // Third member function: comparison between left-side object
   // of C-syle string type  & right-side object of type basic_string
   if ( s2 <= s3 )
      cout << "The string s2 is less than or equal to "
           << "the string s3." << endl;
   else
      cout << "The string s2 is greater than "
           << "the string s3." << endl;
}
```

```Output
The basic_string s1 = strict.
The basic_string s2 = strum.
The C-style string s3 = strict.
The string s1 is less than or equal to the string s2.
The string s1 is less than or equal to the string s3.
The string s2 is greater than the string s3.
```

## <a name="operatorltlt"></a><a name="op_lt_lt"></a>Operátor&lt;&lt;

Funkce šablony, která zapíše řetězec do výstupního datového proudu.

```cpp
template <class CharType, class Traits, class Allocator>
basic_ostream<CharType, Traits>& operator<<(
    basic_ostream<CharType, Traits>& _Ostr,
    const basic_string<CharType, Traits, Allocator>& str);
```

### <a name="parameters"></a>Parametry

*_Ostr*\
Výstupní datový proud zapisován do.

*Str*\
Řetězec, který má být zadán do výstupního datového proudu.

### <a name="return-value"></a>Návratová hodnota

Zapíše hodnotu zadaného řetězce do výstupního datového proudu *_Ostr*.

### <a name="remarks"></a>Poznámky

Operátor přetěžuje funkci šablony **<<** vložení objektu *str* šablony třídy [basic_string](../standard-library/basic-string-class.md) do datového proudu * \_Ostr*. Funkce se efektivně `_Ostr.write( str.c_str, str.size )`vrací .

## <a name="operatorgt"></a><a name="op_gt"></a>Operátor&gt;

Testy, pokud objekt řetězce na levé straně operátoru je větší než objekt řetězce na pravé straně.

```cpp
template <class CharType, class Traits, class Allocator>
bool operator>(
    const basic_string<CharType, Traits, Allocator>& left,
    const basic_string<CharType, Traits, Allocator>& right);

template <class CharType, class Traits, class Allocator>
bool operator>(
    const basic_string<CharType, Traits, Allocator>& left,
    const CharType* right);

template <class CharType, class Traits, class Allocator>
bool operator>(
    const CharType* left,
    const basic_string<CharType, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*Vlevo*\
Řetězec ve stylu C nebo `basic_string` objekt typu, který má být porovnán.

*Právo*\
Řetězec ve stylu C nebo `basic_string` objekt typu, který má být porovnán.

### <a name="return-value"></a>Návratová hodnota

**true** pokud je objekt řetězce na levé straně operátoru lexikograficky větší než objekt řetězce na pravé straně; jinak **false**.

### <a name="remarks"></a>Poznámky

Lexikografické porovnání mezi řetězci je porovná znak po znaku, dokud:

- Najde dva odpovídající znaky nerovné a výsledek jejich porovnání je přijata v důsledku porovnání mezi řetězci.

- Nenajde žádné nerovnosti, ale jeden řetězec má více znaků než druhý a kratší řetězec je považován za menší než delší řetězec.

- Nenajde žádné nerovnosti a zjistí, že řetězce mají stejný počet znaků, a proto řetězce jsou stejné.

### <a name="example"></a>Příklad

```cpp
// string_op_gt.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // Declaring an objects of type basic_string<char>
   string s1 ( "strict" );
   string s2 ( "strum" );
   cout << "The basic_string s1 = " << s1 << "." << endl;
   cout << "The basic_string s2 = " << s2 << "." << endl;

   // Declaring a C-style string
   char *s3 = "stricture";
   cout << "The C-style string s3 = " << s3 << "." << endl;

   // First member function: comparison between left-side object
   // of type basic_string & right-side object of type basic_string
   if ( s1 > s2 )
      cout << "The string s1 is greater than "
           << "the string s2." << endl;
   else
      cout << "The string s1 is not greater than "
           << "the string s2." << endl;

   // Second member function: comparison between left-side object
   // of type basic_string & right-side object of C-syle string type
   if ( s3 > s1 )
      cout << "The string s3 is greater than "
           << "the string s1." << endl;
   else
      cout << "The string s3 is not greater than "
           << "the string s1." << endl;

   // Third member function: comparison between left-side object
   // of C-syle string type & right-side object of type basic_string
   if ( s2 > s3 )
      cout << "The string s2 is greater than "
           << "the string s3." << endl;
   else
      cout << "The string s2 is not greater than "
           << "the string s3." << endl;
}
```

```Output
The basic_string s1 = strict.
The basic_string s2 = strum.
The C-style string s3 = stricture.
The string s1 is not greater than the string s2.
The string s3 is greater than the string s1.
The string s2 is greater than the string s3.
```

## <a name="operatorgt"></a><a name="op_gt_eq"></a>Operátor&gt;=

Testy, pokud objekt řetězce na levé straně operátoru je větší nebo rovna objektu řetězce na pravé straně.

```cpp
template <class CharType, class Traits, class Allocator>
bool operator>=(
    const basic_string<CharType, Traits, Allocator>& left,
    const basic_string<CharType, Traits, Allocator>& right);

template <class CharType, class Traits, class Allocator>
bool operator>=(
    const basic_string<CharType, Traits, Allocator>& left,
    const CharType* right);

template <class CharType, class Traits, class Allocator>
bool operator>=(
    const CharType* left,
    const basic_string<CharType, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*Vlevo*\
Řetězec ve stylu C nebo `basic_string` objekt typu, který má být porovnán.

*Právo*\
Řetězec ve stylu C nebo `basic_string` objekt typu, který má být porovnán.

### <a name="return-value"></a>Návratová hodnota

**true** pokud je objekt řetězce na levé straně operátoru lexikograficky větší nebo roven objektu řetězce na pravé straně; jinak **false**.

### <a name="remarks"></a>Poznámky

Lexikografické porovnání mezi řetězci je porovná znak po znaku, dokud:

- Najde dva odpovídající znaky nerovné a výsledek jejich porovnání je přijata v důsledku porovnání mezi řetězci.

- Nenajde žádné nerovnosti, ale jeden řetězec má více znaků než druhý a kratší řetězec je považován za menší než delší řetězec.

- Najde žádné nerovnosti a zjistí, že řetězce mají stejný počet znaků, a proto jsou řetězce stejné.

### <a name="example"></a>Příklad

```cpp
// string_op_ge.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // Declaring an objects of type basic_string<char>
   string s1 ( "strict" );
   string s2 ( "strum" );
   cout << "The basic_string s1 = " << s1 << "." << endl;
   cout << "The basic_string s2 = " << s2 << "." << endl;

   // Declaring a C-style string
   char *s3 = "stricture";
   cout << "The C-style string s3 = " << s3 << "." << endl;

   // First member function: comparison between left-side object
   // of type basic_string & right-side object of type basic_string
   if ( s1 >= s2 )
      cout << "The string s1 is greater than or equal to "
           << "the string s2." << endl;
   else
      cout << "The string s1 is less than "
           << "the string s2." << endl;

   // Second member function: comparison between left-side object
   // of type basic_string & right-side object of C-syle string type
   if ( s3 >= s1 )
      cout << "The string s3 is greater than or equal to "
           << "the string s1." << endl;
   else
      cout << "The string s3 is less than "
           << "the string s1." << endl;

   // Third member function: comparison between left-side object
   // of C-syle string type & right-side object of type basic_string
   if ( s2 >= s3 )
      cout << "The string s2 is greater than or equal to "
           << "the string s3." << endl;
   else
      cout << "The string s2 is less than "
           << "the string s3." << endl;
}
```

```Output
The basic_string s1 = strict.
The basic_string s2 = strum.
The C-style string s3 = stricture.
The string s1 is less than the string s2.
The string s3 is greater than or equal to the string s1.
The string s2 is greater than or equal to the string s3.
```

## <a name="operatorgtgt"></a><a name="op_gt_gt"></a>Operátor&gt;&gt;

Funkce šablony, která čte řetězec ze vstupního datového proudu.

```cpp
template <class CharType, class Traits, class Allocator>
basic_istream<CharType, Traits>& operator>>(
    basic_istream<CharType, Traits>& _Istr,
    basic_string<CharType, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*_Istr*\
Vstupní datový proud použitý k extrahování sekvence

*Právo*\
Řetězec, který je extrahován ze vstupního datového proudu.

### <a name="return-value"></a>Návratová hodnota

Přečte hodnotu zadaného řetězce z *_Istr* a vrátí ji do *pravého*.

### <a name="remarks"></a>Poznámky

Operátor přeskočí úvodní mezery, `skipws` pokud není nastaven příznak. Přečte všechny následující znaky, dokud další znak je prázdné místo nebo je dosaženo konce souboru.

Operátor funkce šablony přetěžuje **>>** nahradit pořadí řízené *právem* posloupností prvků extrahovaných z *datového*proudu _Istr . Odsávací zastávky:

- Na konci souboru.

- Po funkci extrahuje `_Istr`. **šířkové** prvky, pokud je tato hodnota nenulová.

Po funkci extrahuje `_Istr`. [max_size](../standard-library/basic-string-class.md#max_size) prvky.

- Po funkci extrahuje element *ch,* pro který `getloc` [use_facet](../standard-library/basic-filebuf-class.md#open)< **ctype** \< **CharType**> >( ). **is**( **ctype** \< **CharType**>:: **mezera**, *ch*) je true, v takovém případě je znak odložen zpět.

Pokud funkce extrahuje žádné prvky,`ios_base::failbit`volá [setstate](../standard-library/basic-ios-class.md#setstate)( ). V každém případě, to volá **istr**. **width**(0) \* a vrátí **tuto hodnotu**.

### <a name="example"></a>Příklad

```cpp
// string_op_read_.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   string c0;
   cout << "Input a string c0 ( try: Fibonacci numbers ): ";
   cin >> c0;
   cout << "The string entered is c0 = " << c0 << endl;
}
```

## <a name="see-also"></a>Viz také

[\<řetězec>](../standard-library/string.md)
