---
title: char_traits – struktura | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- iosfwd/std::char_traits
- iosfwd/std::char_traits::char_type
- iosfwd/std::char_traits::int_type
- iosfwd/std::char_traits::off_type
- iosfwd/std::char_traits::pos_type
- iosfwd/std::char_traits::state_type
- iosfwd/std::char_traits::assign
- iosfwd/std::char_traits::compare
- iosfwd/std::char_traits::copy
- iosfwd/std::char_traits::_Copy_s
- iosfwd/std::char_traits::eof
- iosfwd/std::char_traits::eq
- iosfwd/std::char_traits::eq_int_type
- iosfwd/std::char_traits::find
- iosfwd/std::char_traits::length
- iosfwd/std::char_traits::lt
- iosfwd/std::char_traits::move
- iosfwd/std::char_traits::_Move_s
- iosfwd/std::char_traits::not_eof
- iosfwd/std::char_traits::to_char_type
- iosfwd/std::char_traits::to_int_type
dev_langs:
- C++
helpviewer_keywords:
- char_traits struct
- char_traits class
ms.assetid: 568e59f0-4521-4207-9223-9dcf6a16d620
caps.latest.revision: 20
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6dfa04fb138e57daa483901dadc4efc6dfbda851
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="chartraits-struct"></a>char_traits – struktura

Char_traits – struktura popisuje atributy přidružené znak.

## <a name="syntax"></a>Syntaxe

```cpp
template <class CharType>
struct char_traits;
```

### <a name="parameters"></a>Parametry

`CharType` Datový typ elementu.

## <a name="remarks"></a>Poznámky

Struktura šablony popisuje různé vlastnosti znak pro typ **CharType**. Šablony třídy [basic_string](../standard-library/basic-string-class.md) i několik tříd šablon iostream, včetně [basic_ios](../standard-library/basic-ios-class.md), tyto informace použít k manipulaci s elementy typu **CharType** . Takové typ elementu nesmí vyžadovat explicitní vytváření nebo odstraňování. Ji musíte zadat výchozí konstruktor, kopírovacího konstruktoru a operátor přiřazení, s očekávanou sémantiku. Bitové kopie musí mít stejný účinek jako přiřazení. Žádná z členské funkce char_traits – struktura můžete vyvolat výjimky.

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[char_type](#char_type)|Typ znaku.|
|[int_type](#int_type)|Typ integer představující znak typu `char_type` nebo znakem end souboru (EOF).|
|[off_type –](#off_type)|Zadejte celé číslo, představující odsazení mezi pozice v datovém proudu.|
|[pos_type](#pos_type)|Zadejte celé číslo, představující pozice v datovém proudu.|
|[state_type](#state_type)|Typ, který reprezentuje stav převodu ve více-bajtové znaky v datovém proudu.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[přiřazení](#assign)|Přiřadí jeden znak hodnotu do jiné.|
|[compare](#compare)|Porovná až zadaný počet znaků v dva řetězce.|
|[Kopírování](#copy)|Zadaný počet znaků z jednoho řetězce zkopíruje do jiného. Zastaralé Použití [char_traits::_Copy_s](#copy_s) místo.|
|[_Copy_s](#copy_s)|Zadaný počet znaků z jednoho řetězce zkopíruje do jiného.|
|[eof](#eof)|Vrátí znak end souboru (EOF).|
|[EQ](#eq)|Kontroluje, zda dva `char_type` znaky jsou stejné.|
|[eq_int_type](#eq_int_type)|Kontroluje, zda dva znaky vyjádřené `int_type`s jsou stejné.|
|[Najít](#find)|Vyhledá první výskyt je zadaný znak v rozsah znaků.|
|[Délka](#length)|Vrátí délku řetězce.|
|[lt](#lt)|Ověřuje, zda jeden znak je menší než jiné.|
|[Přesunutí](#move)|Zkopíruje zadaný počet znaků v pořadí do druhého, možné překrývání, pořadí. Zastaralé Použití [char_traits::_Move_s](#move_s) místo.|
|[_Move_s](#move_s)|Zkopíruje zadaný počet znaků v pořadí do druhého, možné překrývání, pořadí.|
|[not_eof](#not_eof)|Ověřuje, zda znak je znak end souboru (EOF).|
|[to_char_type](#to_char_type)|Převede `int_type` znak do odpovídajících `char_type` znaku a vrátí výsledek.|
|[to_int_type](#to_int_type)|Převede `char_type` znak do odpovídajících `int_type` znaku a vrátí výsledek.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<řetězec >

**Namespace:** – std

## <a name="assign"></a>  char_traits::Assign

Přiřadí jeden znak hodnotu do jiné nebo rozsahu prvků v řetězci.

```cpp
static void assign(char_type& _CharTo,
    const char_type& _CharFrom);

static char_type *assign(char_type* strTo,
    size_t _Num,
    char_type _CharFrom);
```

### <a name="parameters"></a>Parametry

**_** *CharFrom* znak, jehož hodnota má být přiřazena.

*_CharTo* elementu, který má být přiřazena hodnota znaku.

* strTo * pole řetězec nebo znak, jehož počáteční elementy budou přiřazeny znakových hodnot.

`_Num` Počet elementů, které se chystáte přiřadit hodnoty.

### <a name="return-value"></a>Návratová hodnota

Druhý členská funkce vrací ukazatel na řetězec jejichž první `_Num` elementy byly přiřazeny hodnoty *_CharFrom*.

### <a name="example"></a>Příklad

```cpp
// char_traits_assign.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // The first member function assigning
   // one character value to another character
   char ChTo = 't';
   const char ChFrom = 'f';
   cout << "The initial characters ( ChTo , ChFrom ) are: ( "
        << ChTo << " , " << ChFrom << " )." << endl;
   char_traits<char>::assign ( ChTo , ChFrom );
   cout << "After assigning, the characters ( ChTo , ChFrom ) are: ( "
        << ChTo << " , " << ChFrom << " )." << endl << endl;

   // The second member function assigning
   // character values to initial part of a string
   char_traits<char>::char_type s1[] = "abcd-1234-abcd";
   char_traits<char>::char_type* result1;
   cout << "The target string s1 is: " << s1 << endl;
   result1 = char_traits<char>::assign ( s1 , 4 , 'f' );
   cout << "The result1 = assign ( s1 , 4 , 'f' ) is: "
        << result1 << endl;
}
```

```Output
The initial characters ( ChTo , ChFrom ) are: ( t , f ).
After assigning, the characters ( ChTo , ChFrom ) are: ( f , f ).

The target string s1 is: abcd-1234-abcd
The result1 = assign ( s1 , 4 , 'f' ) is: ffff-1234-abcd
```

## <a name="char_type"></a>  char_traits::char_type

Typ znaku.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro parametr šablony **CharType**.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [kopie](#copy) příklad toho, jak deklarace a používání `char_type`.

## <a name="compare"></a>  char_traits::Compare

Porovná až zadaný počet znaků v dva řetězce.

```cpp
static int compare(const char_type* str1,
    const char_type* str2,
    size_t _Num);
```

### <a name="parameters"></a>Parametry

* Str1 * první dva řetězce být porovnána k sobě navzájem.

* Str2 * sekundu dva řetězce být porovnána k sobě navzájem.

`_Num` Počet elementů v řetězcích, který se má porovnat.

### <a name="return-value"></a>Návratová hodnota

Záporná hodnota, pokud první řetězec je menší než druhý řetězec, 0, pokud jsou dva řetězce stejné, nebo kladnou hodnotu Pokud první řetězec je větší než druhý řetězec.

### <a name="remarks"></a>Poznámky

Porovnání mezi řetězce přišla element po elementu, nejprve testování rovnosti a poté, pokud testy není rovno pár elementů v pořadí, že je testována menší než.

Pokud dva řetězce porovnat rovna přes rozsah, ale jedna je delší než druhý, pak kratší dvou je menší než ten, který delší.

### <a name="example"></a>Příklad

```cpp
// char_traits_compare.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main() {
   using namespace std;

   char_traits<char>::char_type* s1 = "CAB";
   char_traits<char>::char_type* s2 = "ABC";
   char_traits<char>::char_type* s3 = "ABC";
   char_traits<char>::char_type* s4 = "ABCD";

   cout << "The string s1 is: " << s1 << endl;
   cout << "The string s2 is: " << s2 << endl;
   cout << "The string s3 is: " << s3 << endl;
   cout << "The string s4 is: " << s4 << endl;

   int comp1, comp2, comp3, comp4;
   comp1 = char_traits<char>::compare ( s1 , s2 , 2 );
   comp2 = char_traits<char>::compare ( s2 , s3 , 3 );
   comp3 = char_traits<char>::compare ( s3 , s4 , 4 );
   comp4 = char_traits<char>::compare ( s4 , s3 , 4 );
   cout << "compare ( s1 , s2 , 2 ) = " << comp1 << endl;
   cout << "compare ( s2 , s3 , 3 ) = " << comp2 << endl;
   cout << "compare ( s3 , s4 , 4 ) = " << comp3 << endl;
   cout << "compare ( s4 , s3 , 4 ) = " << comp4 << endl;
}
```

## <a name="copy"></a>  char_traits::copy

Zadaný počet znaků z jednoho řetězce zkopíruje do jiného.

Tato metoda je potenciálně nebezpečné, jako je závislé na volajícího, aby zkontrolujte správnost předané hodnoty. Zvažte použití [char_traits::_Copy_s](#copy_s) místo.

```cpp
static char_type *copy(char_type* _To,
    const char_type* _From,
    size_t _Num);
```

### <a name="parameters"></a>Parametry

`_To` Element na začátku řetězec nebo znak pole, které jsou cílené na přijímat zkopírovaný posloupnost znaků.

`_From` Element na začátku zdrojové řetězec nebo znak pole ke kopírování.

`_Num` Počet prvků který se má zkopírovat.

### <a name="return-value"></a>Návratová hodnota

První prvek zkopírován do pole řetězec nebo znak cílem přijímat zkopírovaný posloupnost znaků.

### <a name="remarks"></a>Poznámky

Zdrojové a cílové sekvence znaků se nesmí překrývat.

### <a name="example"></a>Příklad

```cpp
// char_traits_copy.cpp
// compile with: /EHsc /W3
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   char_traits<char>::char_type s1[] = "abcd-1234-abcd";
   char_traits<char>::char_type s2[] = "ABCD-1234";
   char_traits<char>::char_type* result1;
   cout << "The source string is: " << s1 << endl;
   cout << "The destination string is: " << s2 << endl;
   // Note: char_traits::copy is potentially unsafe, consider
   // using char_traits::_Copy_s instead.
   result1 = char_traits<char>::copy ( s1 , s2 , 4 );  // C4996
   cout << "The result1 = copy ( s1 , s2 , 4 ) is: "
        << result1 << endl;
}
```

```Output
The source string is: abcd-1234-abcd
The destination string is: ABCD-1234
The result1 = copy ( s1 , s2 , 4 ) is: ABCD-1234-abcd
```

## <a name="copy_s"></a>  char_traits::_Copy_s

Zadaný počet znaků z jednoho řetězce zkopíruje do jiného.

```cpp
static char_type *_Copy_s(
    char_type* dest,
    size_t dest_size,
    const char_type* _From,
    size_t count);
```

### <a name="parameters"></a>Parametry

`dest` Řetězec nebo znak pole cílové přijímat zkopírovaný posloupnost znaků.

`dest_size` Velikost `dest`. Pokud `char_type` je `char`, pak je tato velikost v bajtech. Pokud `char_type` je `wchar_t`, pak tato velikost je v slova.

`_From` Zdrojový řetězec nebo znak pole, které se mají zkopírovat.

`count` Počet prvků který se má zkopírovat.

### <a name="return-value"></a>Návratová hodnota

Řetězec nebo znak pole cílové přijímat zkopírovaný posloupnost znaků.

### <a name="remarks"></a>Poznámky

Zdrojové a cílové sekvence znaků se nesmí překrývat.

### <a name="example"></a>Příklad

```cpp
// char_traits__Copy_s.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
    using namespace std;

    char_traits<char>::char_type s1[] = "abcd-1234-abcd";
    char_traits<char>::char_type s2[] = "ABCD-1234";
    char_traits<char>::char_type* result1;
    cout << "The source string is: " << s1 << endl;
    cout << "The destination string is: " << s2 << endl;
    result1 = char_traits<char>::_Copy_s(s1,
        char_traits<char>::length(s1), s2, 4);
    cout << "The result1 = _Copy_s(s1, "
         << "char_traits<char>::length(s1), s2, 4) is: "
         << result1 << endl;
}
```

```Output
The source string is: abcd-1234-abcd
The destination string is: ABCD-1234
The result1 = _Copy_s(s1, char_traits<char>::length(s1), s2, 4) is: ABCD-1234-abcd
```

## <a name="eof"></a>  char_traits::EOF

Vrátí znak end souboru (EOF).

```cpp
static int_type eof();
```

### <a name="return-value"></a>Návratová hodnota

EOF znak.

### <a name="remarks"></a>Poznámky

Hodnotu, která představuje konec souboru (například `EOF` nebo `WEOF`).

Standardní C++ stavy, které tato hodnota nesmí odpovídat platným `char_type` hodnotu. Visual C++ compiler vynucuje toto omezení pro typ `char`, ale ne pro typ `wchar_t`. To zachycuje níže uvedený příklad.

### <a name="example"></a>Příklad

```cpp
// char_traits_eof.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main()
{
    using namespace std;

    char_traits<char>::char_type ch1 = 'x';
    char_traits<char>::int_type int1;
    int1 = char_traits<char>::to_int_type(ch1);
    cout << "char_type ch1 is '" << ch1 << "' and corresponds to int_type "
         << int1 << "." << endl << endl;

    char_traits<char>::int_type int2 = char_traits<char>::eof();
    cout << "The eof marker for char_traits<char> is: " << int2 << endl;

    char_traits<wchar_t>::int_type int3 = char_traits<wchar_t>::eof();
    cout << "The eof marker for char_traits<wchar_t> is: " << int3 << endl;
}
```

```Output
char_type ch1 is 'x' and corresponds to int_type 120.

The eof marker for char_traits<char> is: -1
The eof marker for char_traits<wchar_t> is: 65535
```

## <a name="eq"></a>  char_traits::eq

Kontroluje, zda dva `char_type` znaky jsou stejné.

```cpp
static bool eq(const char_type& _Ch1, const char_type& _Ch2);
```

### <a name="parameters"></a>Parametry

`_Ch1` První dva znaky má být testována rovnosti.

`_Ch2` Druhý dva znaky má být testována rovnosti.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE,** Pokud je první znak rovná druhé znak; jinak hodnota **false**.

### <a name="example"></a>Příklad

```cpp
// char_traits_eq.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   char_traits<char>::char_type ch1 =  'x';
   char_traits<char>::char_type ch2 =  'y';
   char_traits<char>::char_type ch3 =  'x';

   // Testing for equality
   bool b1 = char_traits<char>::eq ( ch1 , ch2 );
   if ( b1 )
      cout << "The character ch1 is equal "
           << "to the character ch2." << endl;
   else
      cout << "The character ch1 is not equal "
           << "to the character ch2." << endl;

   // An equivalent and alternatively test procedure
   if ( ch1 == ch3 )
      cout << "The character ch1 is equal "
           << "to the character ch3." << endl;
   else
      cout << "The character ch1 is not equal "
           << "to the character ch3." << endl;
}
```

```Output
The character ch1 is not equal to the character ch2.
The character ch1 is equal to the character ch3.
```

## <a name="eq_int_type"></a>  char_traits::eq_int_type

Kontroluje, zda dva znaky vyjádřené `int_type`s jsou stejné, nebo ne.

```cpp
static bool eq_int_type(const int_type& _Ch1, const int_type& _Ch2);
```

### <a name="parameters"></a>Parametry

`_Ch1` První dva znaky má být testována rovnosti jako **int_type –**s.

`_Ch2` Druhý dva znaky má být testována rovnosti jako `int_type`s.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE,** Pokud je první znak rovná druhé znak; jinak hodnota **false**.

### <a name="example"></a>Příklad

```cpp
// char_traits_eq_int_type.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   char_traits<char>::char_type ch1 =  'x';
   char_traits<char>::char_type ch2 =  'y';
   char_traits<char>::char_type ch3 =  'x';

   // Converting from char_type to int_type
   char_traits<char>::int_type int1, int2 , int3;
   int1 =char_traits<char>:: to_int_type ( ch1 );
   int2 =char_traits<char>:: to_int_type ( ch2 );
   int3 =char_traits<char>:: to_int_type ( ch3 );

   cout << "The char_types and corresponding int_types are:"
        << "\n    ch1 = " << ch1 << " corresponding to int1 = "
        << int1 << "."
        << "\n    ch2 = " << ch2 << " corresponding to int1 = "
        << int2 << "."
        << "\n    ch3 = " << ch3 << " corresponding to int1 = "
        << int3 << "." << endl << endl;

   // Testing for equality of int_type representations
   bool b1 = char_traits<char>::eq_int_type ( int1 , int2 );
   if ( b1 )
      cout << "The int_type representation of character ch1\n "
           << "is equal to the int_type representation of ch2."
           << endl;
   else
      cout << "The int_type representation of character ch1\n is "
           << "not equal to the int_type representation of ch2."
           << endl;

   // An equivalent and alternatively test procedure
   if ( int1 == int3 )
      cout << "The int_type representation of character ch1\n "
           << "is equal to the int_type representation of ch3."
           << endl;
   else
      cout << "The int_type representation of character ch1\n is "
           << "not equal to the int_type representation of ch3."
           << endl;
}
```

```Output
The char_types and corresponding int_types are:
    ch1 = x corresponding to int1 = 120.
    ch2 = y corresponding to int1 = 121.
    ch3 = x corresponding to int1 = 120.

The int_type representation of character ch1
 is not equal to the int_type representation of ch2.
The int_type representation of character ch1
 is equal to the int_type representation of ch3.
```

## <a name="find"></a>  char_traits::Find

Vyhledá první výskyt je zadaný znak v rozsah znaků.

```cpp
static const char_type* find(const char_type* str,
    size_t _Num,
    const char_type& _Ch);
```

### <a name="parameters"></a>Parametry

`str` První znak v řetězci chcete prohledat.

`_Num` Počet pozic, počítáno od první, v rozsahu prohledávání.

`_Ch` Znak, který má být vyhledán v rozsahu.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na první výskyt je zadaný znak v rozsahu, pokud je nalezena shoda; jinak hodnota ukazatele null.

### <a name="example"></a>Příklad

```cpp
// char_traits_find.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   const char* s1 = "f2d-1234-abcd";
   const char* result1;
   cout << "The string to be searched is: " << s1 << endl;

   // Searching for a 'd' in the first 6 positions of string s1
   result1 = char_traits<char>::find ( s1 , 6 , 'd');
   cout << "The character searched for in s1 is: "
        << *result1 << endl;
   cout << "The string beginning with the first occurrence\n "
        << "of the character 'd' is: " << result1 << endl;

   // When no match is found the NULL value is returned
   const char* result2;
   result2 = char_traits<char>::find ( s1 , 3 , 'a');
   if ( result2 == NULL )
      cout << "The result2 of the search is NULL." << endl;
   else
      cout << "The result2 of the search  is: " << result1
           << endl;
}
```

```Output
The string to be searched is: f2d-1234-abcd
The character searched for in s1 is: d
The string beginning with the first occurrence
 of the character 'd' is: d-1234-abcd
The result2 of the search is NULL.
```

## <a name="int_type"></a>  char_traits::int_type

Typ integer představující znak typu `char_type` nebo znakem end souboru (EOF).

```cpp
typedef long int_type;
```

### <a name="remarks"></a>Poznámky

Musí být možné na typ přetypování hodnotu typu **CharType** k `int_type` pak zpět na **CharType** beze změny původní hodnotu.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [eq_int_type –](#eq_int_type) příklad toho, jak deklarace a používání `int_type`.

## <a name="length"></a>  char_traits::length

Vrátí délku řetězce.

```cpp
static size_t length(const char_type* str);
```

### <a name="parameters"></a>Parametry

`str` C – řetězec, jehož délka je měření.

### <a name="return-value"></a>Návratová hodnota

Počet elementů v pořadí se měří bez zahrnutí ukončení hodnotu null.

### <a name="example"></a>Příklad

```cpp
// char_traits_length.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   const char* str1= "Hello";
   cout << "The C-string str1 is: " << str1 << endl;

   size_t lenStr1;
   lenStr1 = char_traits<char>::length ( str1 );
   cout << "The length of C-string str1 is: "
        << lenStr1 << "." << endl;
}
```

```Output
The C-string str1 is: Hello
The length of C-string str1 is: 5.
```

## <a name="lt"></a>  char_traits::lt

Ověřuje, zda jeden znak je menší než jiné.

```cpp
static bool lt(const char_type& _Ch1, const char_type& _Ch2);
```

### <a name="parameters"></a>Parametry

`_Ch1` První dva znaky má být testována pro menší než.

`_Ch2` Druhý dva znaky má být testována pro menší než.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE,** Pokud první znak je menší než druhý znak; jinak hodnota **false**.

### <a name="example"></a>Příklad

```cpp
// char_traits_lt.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   char_traits<char>::char_type ch1 =  'x';
   char_traits<char>::char_type ch2 =  'y';
   char_traits<char>::char_type ch3 =  'z';

   // Testing for less than
   bool b1 = char_traits<char>::lt ( ch1 , ch2 );
   if ( b1 )
      cout << "The character ch1 is less than "
           << "the character ch2." << endl;
   else
      cout << "The character ch1 is not less "
           << "than the character ch2." << endl;

   // An equivalent and alternatively test procedure
   if ( ch3 <  ch2 )
      cout << "The character ch3 is less than "
           << "the character ch2." << endl;
   else
      cout << "The character ch3 is not less "
           << "than the character ch2." << endl;
}
```

```Output
The character ch1 is less than the character ch2.
The character ch3 is not less than the character ch2.
```

## <a name="move"></a>  char_traits::Move

Zkopíruje zadaný počet znaků v pořadí do jiné, které by mohly mít překrývání pořadí.

Tato metoda je potenciálně nebezpečné, jako je závislé na volajícího, aby zkontrolujte správnost předané hodnoty. Zvažte použití [char_traits::_Move_s](#move_s) místo.

```cpp
static char_type *move(char_type* _To,
    const char_type* _From,
    size_t _Num);
```

### <a name="parameters"></a>Parametry

`_To` Element na začátku řetězec nebo znak pole, které jsou cílené na přijímat zkopírovaný posloupnost znaků.

`_From` Element na začátku zdrojové řetězec nebo znak pole ke kopírování.

`_Num` Počet prvků který se má zkopírovat z zdrojový řetězec.

### <a name="return-value"></a>Návratová hodnota

První prvek `_To` zkopírován do pole řetězec nebo znak cílem přijímat zkopírovaný posloupnost znaků.

### <a name="remarks"></a>Poznámky

Zdrojové a cílové překrývat.

### <a name="example"></a>Příklad

```cpp
// char_traits_move.cpp
// compile with: /EHsc /W3
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   char_traits<char>::char_type sFrom1[] =  "abcd-1234-abcd";
   char_traits<char>::char_type sTo1[] =  "ABCD-1234";
   char_traits<char>::char_type* result1;
   cout << "The source string sFrom1 is: " << sFrom1 << endl;
   cout << "The destination stringsTo1 is: " << sTo1 << endl;
   // Note: char_traits::move is potentially unsafe, consider
   // using char_traits::_Move_s instead.
   result1 = char_traits<char>::move ( sTo1 ,  sFrom1 , 4 );  // C4996
   cout << "The result1 = move ( sTo1 , sFrom1 , 4 ) is: "
        << result1 << endl << endl;

   // When source and destination overlap
   char_traits<char>::char_type sToFrom2[] = "abcd-1234-ABCD";
   char_traits<char>::char_type* result2;
   cout << "The source/destination string sToFrom2 is: "
        << sToFrom2 << endl;
   const char* findc = char_traits<char>::find ( sToFrom2 , 4 , 'c' );
   // Note: char_traits::move is potentially unsafe, consider
   // using char_traits::_Move_s instead.
   result2 = char_traits<char>::move ( sToFrom2 , findc , 8 );  // C4996
   cout << "The result2 = move ( sToFrom2 , findc , 8 ) is: "
        << result2 << endl;
}
```

```Output
The source string sFrom1 is: abcd-1234-abcd
The destination stringsTo1 is: ABCD-1234
The result1 = move ( sTo1 , sFrom1 , 4 ) is: abcd-1234

The source/destination string sToFrom2 is: abcd-1234-ABCD
The result2 = move ( sToFrom2 , findc , 8 ) is: cd-1234-4-ABCD
```

## <a name="move_s"></a>  char_traits::_Move_s

Zkopíruje zadaný počet znaků v pořadí do jiné, které by mohly mít překrývání pořadí.

```cpp
static char_type *_Move_s(
    char_type* dest,
    size_t dest_size,
    const char_type* _From,
    size_t count);
```

### <a name="parameters"></a>Parametry

`dest` Element na začátku řetězec nebo znak pole, které jsou cílené na přijímat zkopírovaný posloupnost znaků.

`dest_size` Velikost `dest`. Pokud `char_type` je `char`, je to v bajtech. Pokud `char_type` je `wchar_t`, bude tato slova.

`_From` Element na začátku zdrojové řetězec nebo znak pole ke kopírování.

`count` Počet prvků který se má zkopírovat z zdrojový řetězec.

### <a name="return-value"></a>Návratová hodnota

První prvek `dest` zkopírován do pole řetězec nebo znak cílem přijímat zkopírovaný posloupnost znaků.

### <a name="remarks"></a>Poznámky

Zdrojové a cílové překrývat.

### <a name="example"></a>Příklad

```cpp
// char_traits__Move_s.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
    using namespace std;

    char_traits<char>::char_type sFrom1[] =  "abcd-1234-abcd";
    char_traits<char>::char_type sTo1[] =  "ABCD-1234";
    char_traits<char>::char_type* result1;
    cout << "The source string sFrom1 is: " << sFrom1 << endl;
    cout << "The destination stringsTo1 is: " << sTo1 << endl;
    result1 = char_traits<char>::_Move_s(sTo1,
        char_traits<char>::length(sTo1), sFrom1, 4);
    cout << "The result1 = _Move_s(sTo1, "
         << "char_traits<char>::length(sTo1), sFrom1, 4) is: "
         << result1 << endl << endl;

    // When source and destination overlap
    char_traits<char>::char_type sToFrom2[] = "abcd-1234-ABCD";
    char_traits<char>::char_type* result2;
    cout << "The source/destination string sToFrom2 is: "
         << sToFrom2 << endl;
    const char* findc = char_traits<char>::find(sToFrom2, 4, 'c');
    result2 = char_traits<char>::_Move_s(sToFrom2,
        char_traits<char>::length(sToFrom2), findc, 8);
    cout << "The result2 = _Move_s(sToFrom2, "
        << "char_traits<char>::length(sToFrom2), findc, 8) is: "
         << result2 << endl;
}
```

```Output
The source string sFrom1 is: abcd-1234-abcd
The destination stringsTo1 is: ABCD-1234
The result1 = _Move_s(sTo1, char_traits<char>::length(sTo1), sFrom1, 4) is: abcd-1234

The source/destination string sToFrom2 is: abcd-1234-ABCD
The result2 = _Move_s(sToFrom2, char_traits<char>::length(sToFrom2), findc, 8) is: cd-1234-4-ABCD
```

## <a name="not_eof"></a>  char_traits::not_eof

Ověřuje, zda znak je znak end souboru (EOF), nebo EOF.

```cpp
static int_type not_eof(const int_type& _Ch);
```

### <a name="parameters"></a>Parametry

`_Ch` Znak vyjádřené `int_type` má být testována pro, zda je znak EOF nebo ne.

### <a name="return-value"></a>Návratová hodnota

`int_type` Reprezentace znaku testována, pokud **int_type –** znaku není rovno, hodnota EOF znaku.

Pokud je znak `int_type` hodnota se rovná EOF `int_type` hodnotu, pak **false**.

### <a name="example"></a>Příklad

```cpp
// char_traits_not_eof.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( ) {
   using namespace std;

   char_traits<char>::char_type ch1 =  'x';
   char_traits<char>::int_type int1;
   int1 = char_traits<char>:: to_int_type ( ch1 );
   cout << "The char_type ch1 is " << ch1
        << " corresponding to int_type: "
        << int1 << "." << endl;

   // EOF member function
   char_traits <char>::int_type int2 = char_traits<char>::eof ( );
   cout << "The eofReturn is: " << int2 << endl;

   // Testing for EOF or another character
   char_traits <char>::int_type eofTest1, eofTest2;
   eofTest1 = char_traits<char>::not_eof ( int1 );
   if ( !eofTest1 )
      cout << "The eofTest1 indicates ch1 is an EOF character."
              << endl;
   else
      cout << "The eofTest1 returns: " << eofTest1
           << ", which is the character: "
           <<  char_traits<char>::to_char_type ( eofTest1 )
           << "." << endl;

   eofTest2 = char_traits<char>::not_eof ( int2 );
   if ( !eofTest2 )
      cout << "The eofTest2 indicates int2 is an EOF character."
           << endl;
   else
      cout << "The eofTest1 returns: " << eofTest2
           << ", which is the character: "
           <<  char_traits<char>::to_char_type ( eofTest2 )
           << "." << endl;
}
```

```Output
The char_type ch1 is x corresponding to int_type: 120.
The eofReturn is: -1
The eofTest1 returns: 120, which is the character: x.
The eofTest2 indicates int2 is an EOF character.
```

## <a name="off_type"></a>  char_traits::off_type

Zadejte celé číslo, představující odsazení mezi pozice v datovém proudu.

```cpp
typedef streamoff off_type;
```

### <a name="remarks"></a>Poznámky

Typ se znaménkem popisující objekt, který může ukládat posun bajtů, která je zahrnutých v různých datového proudu umístění operace. Obvykle se jedná o synonymum [streamoff](../standard-library/ios-typedefs.md#streamoff), ale má v podstatě stejné vlastnosti jako typu.

## <a name="pos_type"></a>  char_traits::pos_type

Zadejte celé číslo, představující pozice v datovém proudu.

```cpp
typedef streampos pos_type;
```

### <a name="remarks"></a>Poznámky

Popisuje typ objektu, který může ukládat všechny informace potřebné k obnovení indikátor libovolný pozice souboru v rámci datového proudu. Obvykle se jedná o synonymum [streampos](../standard-library/ios-typedefs.md#streampos), ale v každém případě je v podstatě stejné vlastnosti jako typu.

## <a name="state_type"></a>  char_traits::state_type

Typ, který představuje stav převod vícebajtových znaků v datovém proudu.

```cpp
typedef implementation-defined state_type;
```

### <a name="remarks"></a>Poznámky

Typ popisuje objekt, který může představovat převod stavu. Obvykle se jedná o synonymum `mbstate_t`, ale v každém případě je v podstatě stejné vlastnosti jako typu.

## <a name="to_char_type"></a>  char_traits::to_char_type

Převede `int_type` znak do odpovídajících `char_type` znaku a vrátí výsledek.

```cpp
static char_type to_char_type(const int_type& _Ch);
```

### <a name="parameters"></a>Parametry

`_Ch` `int_type` Znak, který má být reprezentován jako `char_type`.

### <a name="return-value"></a>Návratová hodnota

`char_type` Znak odpovídající `int_type` znak.

Hodnota `_Ch` nemůže být reprezentován jako takový vypočítá neurčené výsledek.

### <a name="remarks"></a>Poznámky

Operace převodu [to_int_type –](#to_int_type) a `to_char_type` jsou inverzní k sobě navzájem, tak, aby:

`to_int_type` ( `to_char_type` ( *x* )) == *x*

pro libovolný `int_type` *x* a

`to_char_type` ( `to_int_type` ( *x* )) == *x*

pro libovolný `char_type` *x*.

### <a name="example"></a>Příklad

```cpp
// char_traits_to_char_type.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   char_traits<char>::char_type ch1 =  'a';
   char_traits<char>::char_type ch2 =  'b';
   char_traits<char>::char_type ch3 =  'a';

   // Converting from char_type to int_type
   char_traits<char>::int_type int1, int2 , int3;
   int1 =char_traits<char>:: to_int_type ( ch1 );
   int2 =char_traits<char>:: to_int_type ( ch2 );
   int3 =char_traits<char>:: to_int_type ( ch3 );

   cout << "The char_types and corresponding int_types are:"
        << "\n    ch1 = " << ch1 << " corresponding to int1 = "
        << int1 << "."
        << "\n    ch2 = " << ch2 << " corresponding to int1 = "
        << int2 << "."
        << "\n    ch3 = " << ch3 << " corresponding to int1 = "
        << int3 << "." << endl << endl;

   // Converting from int_type back to char_type
   char_traits<char>::char_type rec_ch1;
   rec_ch1 = char_traits<char>:: to_char_type ( int1);
   char_traits<char>::char_type rec_ch2;
   rec_ch2 = char_traits<char>:: to_char_type ( int2);

   cout << "The recovered char_types and corresponding int_types are:"
        << "\n    recovered ch1 = " << rec_ch1 << " from int1 = "
        << int1 << "."
        << "\n    recovered ch2 = " << rec_ch2 << " from int2 = "
        << int2 << "." << endl << endl;

   // Testing that the conversions are inverse operations
   bool b1 = char_traits<char>::eq ( rec_ch1 , ch1 );
   if ( b1 )
      cout << "The recovered char_type of ch1"
           << " is equal to the original ch1." << endl;
   else
      cout << "The recovered char_type of ch1"
           << " is not equal to the original ch1." << endl;

   // An equivalent and alternatively test procedure
   if ( rec_ch2 == ch2 )
      cout << "The recovered char_type of ch2"
           << " is equal to the original ch2." << endl;
   else
      cout << "The recovered char_type of ch2"
           << " is not equal to the original ch2." << endl;
}
```

```Output
The char_types and corresponding int_types are:
    ch1 = a corresponding to int1 = 97.
    ch2 = b corresponding to int1 = 98.
    ch3 = a corresponding to int1 = 97.

The recovered char_types and corresponding int_types are:
    recovered ch1 = a from int1 = 97.
    recovered ch2 = b from int2 = 98.

The recovered char_type of ch1 is equal to the original ch1.
The recovered char_type of ch2 is equal to the original ch2.
```

## <a name="to_int_type"></a>  char_traits::to_int_type

Převede `char_type` znak do odpovídajících `int_type` znaku a vrátí výsledek.

```cpp
static int_type to_int_type(const char_type& _Ch);
```

### <a name="parameters"></a>Parametry

`_Ch` `char_type` Znak, který má být reprezentován jako `int_type`.

### <a name="return-value"></a>Návratová hodnota

`int_type` Znak odpovídající `char_type` znak.

### <a name="remarks"></a>Poznámky

Operace převodu `to_int_type` a [to_char_type –](#to_char_type) jsou inverzní k sobě navzájem, tak, aby:

`to_int_type` ( `to_char_type` ( *x* )) == *x*

pro libovolný `int_type` *x*, a

`to_char_type` ( `to_int_type` ( *x* )) == *x*

pro libovolný `char_type` *x*.

### <a name="example"></a>Příklad

```cpp
// char_traits_to_int_type.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   char_traits<char>::char_type ch1 = 'a';
   char_traits<char>::char_type ch2 = 'b';
   char_traits<char>::char_type ch3 = 'a';

   // Converting from char_type to int_type
   char_traits<char>::int_type int1, int2 , int3;
   int1 =char_traits<char>:: to_int_type ( ch1 );
   int2 =char_traits<char>:: to_int_type ( ch2 );
   int3 =char_traits<char>:: to_int_type ( ch3 );

   cout << "The char_types and corresponding int_types are:"
        << "\n    ch1 = " << ch1 << " corresponding to int1 = "
        << int1 << "."
        << "\n    ch2 = " << ch2 << " corresponding to int1 = "
        << int2 << "."
        << "\n    ch3 = " << ch3 << " corresponding to int1 = "
        << int3 << "." << endl << endl;

   // Converting from int_type back to char_type
   char_traits<char>::char_type rec_ch1;
   rec_ch1 = char_traits<char>:: to_char_type ( int1);
   char_traits<char>::char_type rec_ch2;
   rec_ch2 = char_traits<char>:: to_char_type ( int2);

   cout << "The recovered char_types and corresponding int_types are:"
        << "\n    recovered ch1 = " << rec_ch1 << " from int1 = "
        << int1 << "."
        << "\n    recovered ch2 = " << rec_ch2 << " from int2 = "
        << int2 << "." << endl << endl;

   // Testing that the conversions are inverse operations
   bool b1 = char_traits<char>::eq ( rec_ch1 , ch1 );
   if ( b1 )
      cout << "The recovered char_type of ch1"
           << " is equal to the original ch1." << endl;
   else
      cout << "The recovered char_type of ch1"
           << " is not equal to the original ch1." << endl;

   // An equivalent and alternatively test procedure
   if ( rec_ch2 == ch2 )
      cout << "The recovered char_type of ch2"
           << " is equal to the original ch2." << endl;
   else
      cout << "The recovered char_type of ch2"
           << " is not equal to the original ch2." << endl;
}
```

```Output
The char_types and corresponding int_types are:
    ch1 = a corresponding to int1 = 97.
    ch2 = b corresponding to int1 = 98.
    ch3 = a corresponding to int1 = 97.

The recovered char_types and corresponding int_types are:
    recovered ch1 = a from int1 = 97.
    recovered ch2 = b from int2 = 98.

The recovered char_type of ch1 is equal to the original ch1.
The recovered char_type of ch2 is equal to the original ch2.
```

## <a name="see-also"></a>Viz také

[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
