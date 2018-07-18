---
title: '&lt;řetězec&gt; operátory | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
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
dev_langs:
- C++
ms.assetid: 33ce8f05-06c7-45d3-a0cb-bcd27cf93910
helpviewer_keywords:
- std::operator!= (string)
- std::operator&gt; (string)
- std::operator&gt;&gt; (string)
- std::operator&gt;= (string)
- std::operator&lt; (string)
- std::operator&lt;&lt; (string)
- std::operator&lt;= (string), std::operator== (string)
ms.openlocfilehash: 728a0f643a77b47bf857d409517407bec3a1b8b4
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38966618"
---
# <a name="ltstringgt-operators"></a>&lt;řetězec&gt; operátory

||||
|-|-|-|
|[operator!=](#op_neq)|[– Operátor&gt;](#op_gt)|[– Operátor&gt;&gt;](#op_gt_gt)|
|[– Operátor&gt;=](#op_gt_eq)|[– Operátor&lt;](#op_lt)|[– Operátor&lt;&lt;](#op_lt_lt)|
|[– Operátor&lt;=](#op_lt_eq)|[Operator +](#op_add)|[operator==](#op_eq_eq)|

## <a name="op_add"></a>  Operator +

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

*levé* řetězce ve stylu jazyka C nebo objekt typu `basic_string` ke zřetězení.

*správné* řetězce ve stylu jazyka C nebo objekt typu `basic_string` ke zřetězení.

### <a name="return-value"></a>Návratová hodnota

Řetězec, který je tvořen vstupního řetězce.

### <a name="remarks"></a>Poznámky

Přetížení funkce jednotlivých `operator+` ke zřetězení dvou objektů třídy šablony [basic_string – třída](../standard-library/basic-string-class.md). Všechny účinně návratový `basic_string` \< **CharType**, **osobnostní rysy**, **alokátoru**> (_ *vlevo*). [připojit](../standard-library/basic-string-class.md#append)(\_ *vpravo*).

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

## <a name="op_neq"></a>  Operator! =

Testuje, zda je na objekt řetězce na levé straně operátoru není roven objektu string na pravé straně.

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

*levé* řetězce ve stylu jazyka C nebo objekt typu `basic_string` k porovnání.

*správné* řetězce ve stylu jazyka C nebo objekt typu `basic_string` k porovnání.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud na objekt řetězce na levé straně operátoru není lexikograficky stejný řetězec objekt na pravé straně; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Porovnání mezi objekty řetězce vychází pairwise lexicographical porovnání jejich znaků. Dva řetězce rovnají, pokud mají stejný počet znaků a hodnoty jejich odpovídajících znaků jsou stejné. V opačném případě nerovnost.

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

## <a name="op_eq_eq"></a>  Operator ==

Testuje, zda na objekt řetězce na levé straně operátoru roven objektu řetězce na pravé straně.

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

*levé* řetězce ve stylu jazyka C nebo objekt typu `basic_string` k porovnání.

*správné* řetězce ve stylu jazyka C nebo objekt typu `basic_string` k porovnání.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud řetězec objekt na levé straně operátoru lexikograficky stejný řetězec objekt na pravé straně; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Porovnání mezi objekty řetězce vychází pairwise lexicographical porovnání jejich znaků. Dva řetězce rovnají, pokud mají stejný počet znaků a hodnoty jejich odpovídajících znaků jsou stejné. V opačném případě nerovnost.

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

## <a name="op_lt"></a>  – Operátor&lt;

Testuje, zda je na objekt řetězce na levé straně operátoru menší než do objektu string na pravé straně.

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

*levé* řetězce ve stylu jazyka C nebo objekt typu `basic_string` k porovnání.

*správné* řetězce ve stylu jazyka C nebo objekt typu `basic_string` k porovnání.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud řetězec objekt na levé straně operátoru méně lexikografický, než na objekt řetězce na pravé straně; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Lexicographical porovnání řetězců porovnává je znak po znaku do:

- Najde odpovídající dva znaky nerovnost a výsledek jejich porovnání se provede jako výsledek porovnání řetězců.

- Vyhledá žádný nerovnosti, ale jeden řetězec obsahuje více znaků, než druhý a kratší řetězec považuje za menší než řetězec delší dobu.

- Vyhledá žádný nerovnosti a zjistí, že řetězce mají stejný počet znaků, a proto jsou řetězce shodné.

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

## <a name="op_lt_eq"></a>  – Operátor&lt;=

Testuje, zda je řetězec, objekt na levé straně operátoru je menší než nebo rovno řetězci objekt na pravé straně.

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

*levé* řetězce ve stylu jazyka C nebo objekt typu `basic_string` k porovnání.

*správné* řetězce ve stylu jazyka C nebo objekt typu `basic_string` k porovnání.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud řetězec objekt na levé straně operátoru méně lexikografický, než nebo rovno řetězci objekt na pravé straně; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Lexicographical porovnání řetězců porovnává je znak po znaku do:

- Najde odpovídající dva znaky nerovnost a výsledek jejich porovnání se provede jako výsledek porovnání řetězců.

- Vyhledá žádný nerovnosti, ale jeden řetězec obsahuje více znaků, než druhý a kratší řetězec považuje za menší než řetězec delší dobu.

- Vyhledá žádný nerovnosti a zjistí, že řetězce mají stejný počet znaků, takže jsou řetězce shodné.

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

## <a name="op_lt_lt"></a>  – Operátor&lt;&lt;

Funkce šablony, který zapíše řetězec do výstupního datového proudu.

```cpp
template <class CharType, class Traits, class Allocator>
basic_ostream<CharType, Traits>& operator<<(
    basic_ostream<CharType, Traits>& _Ostr,
    const basic_string<CharType, Traits, Allocator>& str);
```

### <a name="parameters"></a>Parametry

*_Ostr* do výstupního datového proudu.

*Str* řetězec, který má být zadány do výstupního datového proudu.

### <a name="return-value"></a>Návratová hodnota

Zapíše hodnotu zadaného řetězce do výstupního datového proudu *_Ostr*.

### <a name="remarks"></a>Poznámky

Funkce přetížení šablon **operátor <<** vložit pomocí objektu _ *Str* třídy šablony [basic_string](../standard-library/basic-string-class.md) do datového proudu \_  *Ostr.* Funkce vrátí efektivně \_ *Ostr*. **zápis**( \_ *Str*. [c_str](../standard-library/basic-string-class.md#c_str), \_ *Str*. [velikost](../standard-library/basic-string-class.md#size)).

## <a name="op_gt"></a>  – Operátor&gt;

Testuje, zda je řetězec objekt na levé straně operátoru větší než objekt řetězce na pravé straně.

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

*levé* řetězce ve stylu jazyka C nebo objekt typu `basic_string` k porovnání.

*správné* řetězce ve stylu jazyka C nebo objekt typu `basic_string` k porovnání.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud řetězec objekt na levé straně operátoru lexikograficky větší než řetězec objekt na pravé straně; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Lexicographical porovnání řetězců porovnává je znak po znaku do:

- Najde odpovídající dva znaky nerovnost a výsledek jejich porovnání se provede jako výsledek porovnání řetězců.

- Vyhledá žádný nerovnosti, ale jeden řetězec obsahuje více znaků, než druhý a kratší řetězec považuje za menší než řetězec delší dobu.

- Vyhledá žádný nerovnosti a zjistí, že řetězce mají stejný počet znaků, a proto jsou řetězce shodné.

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

## <a name="op_gt_eq"></a>  – Operátor&gt;=

Testuje, zda je na objekt řetězce na levé straně operátoru větší než nebo rovno řetězci objekt na pravé straně.

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

*levé* řetězce ve stylu jazyka C nebo objekt typu `basic_string` k porovnání.

*správné* řetězce ve stylu jazyka C nebo objekt typu `basic_string` k porovnání.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud řetězec objekt na levé straně operátoru lexikograficky větší než nebo rovno řetězci objekt na pravé straně; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Lexicographical porovnání řetězců porovnává je znak po znaku do:

- Najde odpovídající dva znaky nerovnost a výsledek jejich porovnání se provede jako výsledek porovnání řetězců.

- Vyhledá žádný nerovnosti, ale jeden řetězec obsahuje více znaků, než druhý a kratší řetězec považuje za menší než řetězec delší dobu.

- Vyhledá žádný nerovnosti a zjistí, řetězce mají stejný počet znaků, a proto jsou řetězce shodné.

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

## <a name="op_gt_gt"></a>  – Operátor&gt;&gt;

Funkce šablony, přečte řetězce ze vstupního datového proudu.

```cpp
template <class CharType, class Traits, class Allocator>
basic_istream<CharType, Traits>& operator>>(
    basic_istream<CharType, Traits>& _Istr,
    basic_string<CharType, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*_Istr* vstupního datového proudu, používá k extrakci sekvence

*správné* řetězec, který je právě extrahován ze vstupního datového proudu.

### <a name="return-value"></a>Návratová hodnota

Načte hodnotu zadaného řetězce z *_Istr* a vrátí ji do *správné*.

### <a name="remarks"></a>Poznámky

Operátor, který přeskočí úvodní mezery, není-li `skipws` je nastavený příznak. Načte všechny následující znaky, dokud následující znak je prázdné znaky nebo je dosaženo konce souboru.

Funkce přetížení šablon **operátor >>** nahradit sekvence řízenou parametrem *správné* s sekvenci prvků extrahovat z datového proudu *_Istr*. Zastavení extrakce:

- Na konci souboru.

- Po funkci extrahuje `_Istr`. **Šířka** prvky, pokud je tato hodnota nenulovou hodnotu.

Po funkci extrahuje `_Istr`. [max_size](../standard-library/basic-string-class.md#max_size) elementy.

- Po funkci extrahuje element *ch* pro kterou [use_facet](../standard-library/basic-filebuf-class.md#open)< **ctype** \< **CharType**> > ( `getloc`). **je**( **ctype** \< **CharType**>:: **místo**, *ch*) má hodnotu true, v takovém případě je znak, který mělo vrátit .

Pokud funkci extrahuje žádné elementy, zavolá [setstate](../standard-library/basic-ios-class.md#setstate)(`ios_base::failbit`). V každém případě volá **istr**. **Šířka**(0) a vrátí \* **to**.

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

[\<řetězec >](../standard-library/string.md)<br/>
