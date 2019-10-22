---
title: operátory &lt;string &gt;
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
ms.openlocfilehash: f9aa07f7ca30ded5f61e77a327efafe91aa5c269
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2019
ms.locfileid: "72686000"
---
# <a name="ltstringgt-operators"></a>operátory &lt;string &gt;

||||
|-|-|-|
|[operator!=](#op_neq)|[operátor &gt;](#op_gt)|[operátor &gt; &gt;](#op_gt_gt)|
|[operátor &gt; =](#op_gt_eq)|[operátor &lt;](#op_lt)|[operátor &lt; &lt;](#op_lt_lt)|
|[operátor &lt; =](#op_lt_eq)|[operator + – operátor](#op_add)|[operator = = – operátor](#op_eq_eq)|

## <a name="op_add"></a>operator + – operátor

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

*levý* \
Řetězec ve stylu jazyka C nebo objekt typu `basic_string` mají být zřetězeny.

*pravé* \
Řetězec ve stylu jazyka C nebo objekt typu `basic_string` mají být zřetězeny.

### <a name="return-value"></a>Návratová hodnota

Řetězec, který je zřetězením vstupních řetězců.

### <a name="remarks"></a>Poznámky

Funkce každého přetížení `operator+` zřetězení dvou objektů třídy Template třídy [basic_string](../standard-library/basic-string-class.md). Všechno efektivně vrací `basic_string< CharType, Traits, Allocator>(Left).append(right)`. Další informace najdete v tématu věnovaném [připojení](../standard-library/basic-string-class.md#append).

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

## <a name="op_neq"></a>! = – operátor

Testuje, zda objekt String na levé straně operátoru není roven objektu řetězce na pravé straně.

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

*levý* \
Řetězec ve stylu jazyka C nebo objekt typu `basic_string`, které mají být porovnány.

*pravé* \
Řetězec ve stylu jazyka C nebo objekt typu `basic_string`, které mají být porovnány.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud objekt String na levé straně operátoru není lexikograficky rovný objektu řetězce na pravé straně; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Porovnání mezi objekty řetězce je založeno na lexicographical porovnání jejich znaků. Dva řetězce jsou stejné, pokud mají stejný počet znaků a jejich příslušné znakové hodnoty jsou stejné. V opačném případě jsou nerovné.

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

## <a name="op_eq_eq"></a>operator = = – operátor

Testuje, zda je objekt řetězce na levé straně operátoru roven objektu řetězce na pravé straně.

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

*levý* \
Řetězec ve stylu jazyka C nebo objekt typu `basic_string`, které mají být porovnány.

*pravé* \
Řetězec ve stylu jazyka C nebo objekt typu `basic_string`, které mají být porovnány.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud je objekt řetězce na levé straně operátoru lexikograficky rovný objektu řetězce na pravé straně; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Porovnání mezi objekty řetězce je založeno na lexicographical porovnání jejich znaků. Dva řetězce jsou stejné, pokud mají stejný počet znaků a jejich příslušné znakové hodnoty jsou stejné. V opačném případě jsou nerovné.

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

## <a name="op_lt"></a>operátor &lt;

Testuje, zda je objekt řetězce na levé straně operátoru menší než na objekt řetězce na pravé straně.

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

*levý* \
Řetězec ve stylu jazyka C nebo objekt typu `basic_string`, které mají být porovnány.

*pravé* \
Řetězec ve stylu jazyka C nebo objekt typu `basic_string`, které mají být porovnány.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud je objekt řetězce na levé straně operátoru lexikograficky menší než objekt řetězce na pravé straně; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Porovnání lexicographical mezi řetězci porovná je se znakem až do:

- Najde dva odpovídající znaky, které nejsou stejné a výsledek jejich porovnání je výsledkem porovnání řetězců.

- Nenajde žádné nerovnosti, ale jeden řetězec má více znaků než druhý a kratší řetězec je považován za méně než delší řetězec.

- Nenajde žádné nerovnosti a zjistí, že řetězce mají stejný počet znaků, a proto jsou řetězce stejné.

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

## <a name="op_lt_eq"></a>operátor &lt; =

Testuje, zda je objekt řetězce na levé straně operátoru menší než nebo roven objektu řetězce na pravé straně.

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

*levý* \
Řetězec ve stylu jazyka C nebo objekt typu `basic_string`, které mají být porovnány.

*pravé* \
Řetězec ve stylu jazyka C nebo objekt typu `basic_string`, které mají být porovnány.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud je objekt řetězce na levé straně operátoru lexikograficky menší než nebo roven objektu řetězce na pravé straně; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Porovnání lexicographical mezi řetězci porovná je se znakem až do:

- Najde dva odpovídající znaky, které nejsou stejné a výsledek jejich porovnání je výsledkem porovnání řetězců.

- Nenajde žádné nerovnosti, ale jeden řetězec má více znaků než druhý a kratší řetězec je považován za méně než delší řetězec.

- Nenajde žádné nerovnosti a zjistí, že řetězce mají stejný počet znaků, takže jsou řetězce stejné.

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

## <a name="op_lt_lt"></a>operátor &lt; &lt;

Funkce šablony, která zapisuje řetězec do výstupního datového proudu.

```cpp
template <class CharType, class Traits, class Allocator>
basic_ostream<CharType, Traits>& operator<<(
    basic_ostream<CharType, Traits>& _Ostr,
    const basic_string<CharType, Traits, Allocator>& str);
```

### <a name="parameters"></a>Parametry

*_Ostr* \
Výstupní datový proud, do kterého se zapisuje.

\ *str*
Řetězec, který má být zadán do výstupního datového proudu.

### <a name="return-value"></a>Návratová hodnota

Zapíše hodnotu zadaného řetězce do výstupního streamu *_Ostr*.

### <a name="remarks"></a>Poznámky

Funkce šablony přetěžování **< <** pro vložení objektového *str* šablony třídy [basic_string](../standard-library/basic-string-class.md) do *\_Ostr*streamu. Funkce efektivně vrátí `_Ostr.write( str.c_str, str.size )`.

## <a name="op_gt"></a>operátor &gt;

Testuje, zda je objekt řetězce na levé straně operátoru větší než na objekt řetězce na pravé straně.

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

*levý* \
Řetězec ve stylu jazyka C nebo objekt typu `basic_string`, které mají být porovnány.

*pravé* \
Řetězec ve stylu jazyka C nebo objekt typu `basic_string`, které mají být porovnány.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud je objekt řetězce na levé straně operátoru lexikograficky větší než objekt řetězce na pravé straně; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Porovnání lexicographical mezi řetězci porovná je se znakem až do:

- Najde dva odpovídající znaky, které nejsou stejné a výsledek jejich porovnání je výsledkem porovnání řetězců.

- Nenajde žádné nerovnosti, ale jeden řetězec má více znaků než druhý a kratší řetězec je považován za méně než delší řetězec.

- Nenajde žádné nerovnosti a zjistí, že řetězce mají stejný počet znaků, a proto jsou řetězce stejné.

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

## <a name="op_gt_eq"></a>operátor &gt; =

Testuje, zda je objekt řetězce na levé straně operátoru větší než nebo roven objektu řetězce na pravé straně.

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

*levý* \
Řetězec ve stylu jazyka C nebo objekt typu `basic_string`, které mají být porovnány.

*pravé* \
Řetězec ve stylu jazyka C nebo objekt typu `basic_string`, které mají být porovnány.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud je objekt řetězce na levé straně operátoru lexikograficky větší než nebo roven objektu řetězce na pravé straně; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Porovnání lexicographical mezi řetězci porovná je se znakem až do:

- Najde dva odpovídající znaky, které nejsou stejné a výsledek jejich porovnání je výsledkem porovnání řetězců.

- Nenajde žádné nerovnosti, ale jeden řetězec má více znaků než druhý a kratší řetězec je považován za méně než delší řetězec.

- Nenajde žádné nerovnosti a vyhledá řetězce mají stejný počet znaků, a proto jsou řetězce stejné.

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

## <a name="op_gt_gt"></a>operátor &gt; &gt;

Funkce šablony, která čte řetězec ze vstupního datového proudu.

```cpp
template <class CharType, class Traits, class Allocator>
basic_istream<CharType, Traits>& operator>>(
    basic_istream<CharType, Traits>& _Istr,
    basic_string<CharType, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*_Istr* \
Vstupní datový proud použitý k extrakci sekvence

*pravé* \
Řetězec, který se extrahuje ze vstupního datového proudu.

### <a name="return-value"></a>Návratová hodnota

Přečte hodnotu zadaného řetězce z *_Istr* a vrátí ji do *pravé*části.

### <a name="remarks"></a>Poznámky

Operátor přeskočí úvodní prázdné znaky, pokud není nastaven příznak `skipws`. Přečte všechny následující znaky, dokud je další znak mezerou nebo koncem souboru.

Funkce šablony přetěžuje **operátor > >** , aby nahradil sekvenci řízenou *pravou* s posloupností prvků extrahovaných z datového proudu *_Istr*. Extrakce se zastaví:

- Na konci souboru.

- Po extrahování funkce `_Istr`. element **Width** , pokud je tato hodnota nenulová.

Po extrahování funkce `_Istr`. [max_size](../standard-library/basic-string-class.md#max_size) elementy

- Poté, co funkce extrahuje prvek *ch* , pro který [use_facet](../standard-library/basic-filebuf-class.md#open) < **CType** \< **CharType**> > (`getloc`). **is**( **ctype** \< **CharType**>:: **Space**, *ch*) má hodnotu true. v takovém případě je znak vrácen zpět.

Pokud funkce neextrahuje žádné prvky, volá [setstate](../standard-library/basic-ios-class.md#setstate)(`ios_base::failbit`). V každém případě volá **ISTR**. **Width**(0) a **vrátí \*.**

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

## <a name="see-also"></a>Viz také:

[\<string >](../standard-library/string.md)
