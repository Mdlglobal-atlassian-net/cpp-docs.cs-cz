---
title: '&lt;řetězec&gt; operátory | Microsoft Docs'
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
ms.openlocfilehash: b0ca7da732786c2f0ff6087052b5867150702a5e
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="ltstringgt-operators"></a>&lt;řetězec&gt; operátory

||||
|-|-|-|
|[operator!=](#op_neq)|[Operátor&gt;](#op_gt)|[Operátor&gt;&gt;](#op_gt_gt)|
|[Operátor&gt;=](#op_gt_eq)|[Operátor&lt;](#op_lt)|[Operátor&lt;&lt;](#op_lt_lt)|
|[Operátor&lt;=](#op_lt_eq)|[operátor +](#op_add)|[operator==](#op_eq_eq)|

## <a name="op_add"></a>  operátor +

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

`left` Řetězec stylu jazyka C nebo objekt typu `basic_string` má být zřetězen.

`right` Řetězec stylu jazyka C nebo objekt typu `basic_string` má být zřetězen.

### <a name="return-value"></a>Návratová hodnota

Řetězec, který je zřetězení vstupní řetězce.

### <a name="remarks"></a>Poznámky

Přetížení funkce každý `operator+` ke zřetězení dva objekty třídy šablony [basic_string – třída](../standard-library/basic-string-class.md). Všechny efektivně návratový `basic_string` \< **CharType**, **vlastnosti**, **Allocator**> (_ *doleva*). [připojit](../standard-library/basic-string-class.md#append)(\_ *vpravo*).

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

Testy, pokud řetězec objekt na levé straně operátoru není stejný jako řetězec objekt na pravé straně.

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

`left` Řetězec stylu jazyka C nebo objekt typu `basic_string` být porovnána.

`right` Řetězec stylu jazyka C nebo objekt typu `basic_string` být porovnána.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE,** Pokud řetězec objekt na levé straně operátoru není lexicographically rovná řetězec objekt na pravé straně; jinak hodnota **false**.

### <a name="remarks"></a>Poznámky

Porovnání mezi objekty řetězec vychází pairwise lexicographical porovnání jejich znaků. Dva řetězce jsou stejné, pokud mají stejný počet znaků a hodnoty jejich odpovídajících znaků jsou stejné. Jinak nerovné.

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

Testy, pokud řetězec objekt na levé straně operátoru rovná řetězec objekt na pravé straně.

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

`left` Řetězec stylu jazyka C nebo objekt typu `basic_string` být porovnána.

`right` Řetězec stylu jazyka C nebo objekt typu `basic_string` být porovnána.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE,** Pokud je řetězec objekt na levé straně operátoru lexicographically rovná řetězec objekt na pravé straně; jinak hodnota **false**.

### <a name="remarks"></a>Poznámky

Porovnání mezi objekty řetězec vychází pairwise lexicographical porovnání jejich znaků. Dva řetězce jsou stejné, pokud mají stejný počet znaků a hodnoty jejich odpovídajících znaků jsou stejné. Jinak nerovné.

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

## <a name="op_lt"></a>  Operátor&lt;

Testuje, pokud objekt na levé straně operátoru řetězce je menší než na objekt řetězce na pravé straně.

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

`left` Řetězec stylu jazyka C nebo objekt typu `basic_string` být porovnána.

`right` Řetězec stylu jazyka C nebo objekt typu `basic_string` být porovnána.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE,** Pokud řetězec objekt na levé straně operátoru lexicographically menší než řetězec objekt na pravé straně; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Lexicographical srovnání řetězce porovná je znak po znaku dokud:

- Nerovné najde odpovídající dva znaky a výsledek jejich porovnání se provede na základě porovnání mezi řetězce.

- Najde žádné nerovnosti, ale jeden řetězec obsahuje více znaků, než dalších a kratší řetězec, který je považován za méně než delší řetězec.

- Najde žádné nerovnosti a najde řetězce mít stejný počet znaků, a proto řetězce jsou stejné.

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

## <a name="op_lt_eq"></a>  Operátor&lt;=

Pokud řetězec objekt na levé straně operátoru testů je menší než nebo rovna hodnotě objekt řetězce na pravé straně.

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

`left` Řetězec stylu jazyka C nebo objekt typu `basic_string` být porovnána.

`right` Řetězec stylu jazyka C nebo objekt typu `basic_string` být porovnána.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE,** Pokud řetězec objekt na levé straně operátoru lexicographically menší než nebo rovná řetězec objekt na pravé straně; jinak hodnota **false**.

### <a name="remarks"></a>Poznámky

Lexicographical srovnání řetězce porovná je znak po znaku dokud:

- Nerovné najde odpovídající dva znaky a výsledek jejich porovnání se provede na základě porovnání mezi řetězce.

- Najde žádné nerovnosti, ale jeden řetězec obsahuje více znaků, než dalších a kratší řetězec, který je považován za méně než delší řetězec.

- Najde žádné nerovnosti a najde, že řetězce mají stejný počet znaků, takže řetězce jsou stejné.

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

## <a name="op_lt_lt"></a>  Operátor&lt;&lt;

Funkce šablony, která zapisuje řetězec do výstupního datového proudu.

```cpp
template <class CharType, class Traits, class Allocator>
basic_ostream<CharType, Traits>& operator<<(
    basic_ostream<CharType, Traits>& _Ostr,
    const basic_string<CharType, Traits, Allocator>& str);
```

### <a name="parameters"></a>Parametry

_Ostr zapisuje do výstupního datového proudu.

`str` Řetězec, který je třeba zadat do výstupního datového proudu.

### <a name="return-value"></a>Návratová hodnota

Hodnota řetězce zadaná zapíše do výstupního datového proudu `_Ostr`.

### <a name="remarks"></a>Poznámky

Přetížení funkce šablony **operátor <<** vložit pomocí objektu _ *Str* třídy šablony [basic_string](../standard-library/basic-string-class.md) do datového proudu \_  *Ostr.* Funkce efektivně vrátí \_ *Ostr*. **zápis**( \_ *Str*. [c_str](../standard-library/basic-string-class.md#c_str), \_ *Str*. [velikost](../standard-library/basic-string-class.md#size)).

## <a name="op_gt"></a>  Operátor&gt;

Testy, pokud je řetězec objekt na levé straně operátoru větší než na objekt řetězce na pravé straně.

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

`left` Řetězec stylu jazyka C nebo objekt typu `basic_string` být porovnána.

`right` Řetězec stylu jazyka C nebo objekt typu `basic_string` být porovnána.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE,** Pokud je řetězec objekt na levé straně operátoru lexicographically větší než řetězec objekt na pravé straně; jinak hodnota **false**.

### <a name="remarks"></a>Poznámky

Lexicographical srovnání řetězce porovná je znak po znaku dokud:

- Nerovné najde odpovídající dva znaky a výsledek jejich porovnání se provede na základě porovnání mezi řetězce.

- Najde žádné nerovnosti, ale jeden řetězec obsahuje více znaků, než dalších a kratší řetězec, který je považován za méně než delší řetězec.

- Najde žádné nerovnosti a najde řetězce mít stejný počet znaků, a proto řetězce jsou stejné.

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

## <a name="op_gt_eq"></a>  Operátor&gt;=

Testy, pokud je řetězec objekt na levé straně operátoru větší než nebo rovna hodnotě řetězec objekt na pravé straně.

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

`left` Řetězec stylu jazyka C nebo objekt typu `basic_string` být porovnána.

`right` Řetězec stylu jazyka C nebo objekt typu `basic_string` být porovnána.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE,** Pokud je řetězec objekt na levé straně operátoru lexicographically větší než nebo rovná řetězec objekt na pravé straně; jinak hodnota **false**.

### <a name="remarks"></a>Poznámky

Lexicographical srovnání řetězce porovná je znak po znaku dokud:

- Nerovné najde odpovídající dva znaky a výsledek jejich porovnání se provede na základě porovnání mezi řetězce.

- Najde žádné nerovnosti, ale jeden řetězec obsahuje více znaků, než dalších a kratší řetězec, který je považován za méně než delší řetězec.

- Najde žádné nerovnosti a najde řetězce mít stejný počet znaků, a proto řetězce jsou stejné.

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

## <a name="op_gt_gt"></a>  Operátor&gt;&gt;

Funkce šablony, který čte řetězec ze vstupního datového proudu.

```cpp
template <class CharType, class Traits, class Allocator>
basic_istream<CharType, Traits>& operator>>(
    basic_istream<CharType, Traits>& _Istr,
    basic_string<CharType, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

`_Istr` Vstupní datový proud použitou k extrakci sekvenci

`right` Řetězec, který je se extrahují z vstupního datového proudu.

### <a name="return-value"></a>Návratová hodnota

Načte hodnotu zadaného řetězce z `_Istr` a vrátí ji do `right`.

### <a name="remarks"></a>Poznámky

Operátor Přeskočí úvodní mezery prázdné, pokud `skipws` je nastavený příznak. Přečte všechny následující znaky, dokud další znak je prázdné znaky nebo je dosaženo konce souboru.

Přetížení funkce šablony **operátor >>** nahradit pořadí řízené `right` s pořadí elementů extrahovat z datového proudu `_Istr`. Extrakce zastaví:

- Na konci souboru.

- Po extrahuje funkce `_Istr`. **Šířka** prvky, pokud je tato hodnota nenulové.

Po extrahuje funkce `_Istr`. [max_size –](../standard-library/basic-string-class.md#max_size) elementy.

- Po funkce extrahuje element *ch* pro kterou [use_facet](../standard-library/basic-filebuf-class.md#open)< **ctype** \< **CharType**> > ( `getloc`). **je**( **ctype** \< **CharType**>:: **místo**, *ch*) má hodnotu true, v takovém případě znak je vrátit zpět .

Pokud funkci extrahuje žádné elementy, zavolá [setstate –](../standard-library/basic-ios-class.md#setstate)( `ios_base::failbit`). V každém případě volá **istr**. **Šířka**(0) a vrátí \* **to**.

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

[\<řetězec >](../standard-library/string.md)<br/>
