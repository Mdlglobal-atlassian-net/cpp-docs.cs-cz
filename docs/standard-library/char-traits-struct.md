---
title: char_traits – struktura
ms.date: 05/07/2019
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
helpviewer_keywords:
- char_traits struct
- char_traits class
ms.assetid: 568e59f0-4521-4207-9223-9dcf6a16d620
ms.openlocfilehash: 3d707ff963170b6b4f14ad1f04e9420b8062b520
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366708"
---
# <a name="char_traits-struct"></a>char_traits – struktura

Struktura char_traits popisuje atributy přidružené ke znaku.

## <a name="syntax"></a>Syntaxe

```cpp
template <class CharType>
struct char_traits;
```

### <a name="parameters"></a>Parametry

*Typ znaku*\
Datový typ prvku.

## <a name="remarks"></a>Poznámky

Struktura šablony popisuje různé znakové znaky `CharType`pro typ . Šablona třídy [basic_string](../standard-library/basic-string-class.md) stejně jako několik šablon tříd iostream, včetně [basic_ios](../standard-library/basic-ios-class.md), použijte tyto informace k manipulaci s prvky typu `CharType`. Takový typ prvku nesmí vyžadovat explicitní konstrukci nebo zničení. Musí poskytnout výchozí konstruktor, konstruktor kopie a operátor přiřazení s očekávanou sémantikou. Bitová kopie musí mít stejný účinek jako přiřazení. Žádná z členských funkcí struktury char_traits může vyvolat výjimky.

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[char_type](#char_type)|Typ znaku.|
|[int_type](#int_type)|Celočíselný typ, který může představovat znak typu `char_type` nebo znak konce souboru (EOF).|
|[off_type](#off_type)|Typ celéčíslo, který může představovat posuny mezi pozicemi v datovém proudu.|
|[pos_type](#pos_type)|Typ celéčíslo, který může představovat pozice v datovém proudu.|
|[state_type](#state_type)|Typ, který představuje stav převodu v pro vícebajtové znaky v datovém proudu.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[Přiřadit](#assign)|Přiřadí hodnotu jednoho znaku jinému znaku.|
|[Porovnat](#compare)|Porovná až zadaný počet znaků ve dvou řetězcích.|
|[Kopírovat](#copy)|Zkopíruje zadaný počet znaků z jednoho řetězce do druhého. Zastaralé Místo toho použijte [char_traits::_Copy_s.](#copy_s)|
|[_Copy_s](#copy_s)|Zkopíruje zadaný počet znaků z jednoho řetězce do druhého.|
|[eof](#eof)|Vrátí znak konce souboru (EOF).|
|[Eq](#eq)|Testuje, `char_type` zda jsou dva znaky stejné.|
|[eq_int_type](#eq_int_type)|Testuje, zda jsou `int_type`dva znaky reprezentované jako s stejné.|
|[find](#find)|Vyhledá první výskyt zadaného znaku v rozsahu znaků.|
|[Délka](#length)|Vrátí délku řetězce.|
|[Lt](#lt)|Testuje, zda jeden znak je menší než jiný.|
|[Přesunout](#move)|Zkopíruje zadaný počet znaků v sekvenci do jiného, možného překrývání, sekvence. Zastaralé Použijte místo toho [char_traits::_Move_s.](#move_s)|
|[_Move_s](#move_s)|Zkopíruje zadaný počet znaků v sekvenci do jiného, možného překrývání, sekvence.|
|[not_eof](#not_eof)|Testuje, zda znak je znak konce souboru (EOF) znak.|
|[to_char_type](#to_char_type)|Převede `int_type` znak na `char_type` odpovídající znak a vrátí výsledek.|
|[to_int_type](#to_int_type)|Převede `char_type` znak na `int_type` odpovídající znak a vrátí výsledek.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<řetězec>

**Obor názvů:** std

## <a name="char_traitsassign"></a><a name="assign"></a>char_traits::přiřadit

Přiřadí jednu hodnotu znaku jinému nebo rozsahu prvků v řetězci.

```cpp
static void assign(char_type& _CharTo,
    const char_type& _CharFrom);

static char_type *assign(char_type* strTo,
    size_t _Num,
    char_type _CharFrom);
```

### <a name="parameters"></a>Parametry

**_** *CharFrom* Znak, jehož hodnota má být přiřazena.

*_CharTo*\
Prvek, který má být přiřazen hodnotu znaku.

*strTo*\
Pole řetězce nebo znaků, jehož počáteční prvky mají být přiřazeny hodnoty znaků.

*_Num*\
Počet prvků, které budou přiřazeny hodnoty.

### <a name="return-value"></a>Návratová hodnota

Druhá členská funkce vrátí ukazatel na řetězec, jehož prvním *_Num* prvkům byly přiřazeny hodnoty *_CharFrom*.

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

## <a name="char_traitschar_type"></a><a name="char_type"></a>char_traits::char_type

Typ znaku.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymem pro `CharType`parametr šablony .

### <a name="example"></a>Příklad

Příklad pro [kopii](#copy) naleznete v příkladu, `char_type`jak deklarovat a používat .

## <a name="char_traitscompare"></a><a name="compare"></a>char_traits::porovnat

Porovná až zadaný počet znaků ve dvou řetězcích.

```cpp
static int compare(const char_type* str1,
    const char_type* str2,
    size_t _Num);
```

### <a name="parameters"></a>Parametry

*str1*\
První ze dvou řetězců, které mají být vzájemně porovnány.

*str2*\
Druhý ze dvou řetězců, které mají být vzájemně porovnány.

*_Num*\
Počet prvků v řetězce, které mají být porovnány.

### <a name="return-value"></a>Návratová hodnota

Záporná hodnota, pokud je první řetězec menší než druhý řetězec, 0, pokud jsou dva řetězce stejné, nebo kladnou hodnotu, pokud je první řetězec větší než druhý řetězec.

### <a name="remarks"></a>Poznámky

Porovnání mezi řetězci se provádí element po elementu, nejprve testování rovnosti a pak, pokud dvojice prvků v sekvenční testy nejsou stejné, jsou testovány na menší než.

Pokud dva řetězce porovnat rovná v rozsahu, ale jeden je delší než ostatní, pak kratší z nich je menší než delší.

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

## <a name="char_traitscopy"></a><a name="copy"></a>char_traits::kopírování

Zkopíruje zadaný počet znaků z jednoho řetězce do druhého.

Tato metoda je potenciálně nebezpečné, protože spoléhá na volajícího zkontrolovat, že předané hodnoty jsou správné. Zvažte použití [char_traits::_Copy_s.](#copy_s)

```cpp
static char_type *copy(char_type* _To,
    const char_type* _From,
    size_t _Num);
```

### <a name="parameters"></a>Parametry

*_To*\
Prvek na začátku řetězce nebo pole znaků zaměřených na příjem zkopírované sekvence znaků.

*_From*\
Prvek na začátku zdrojového řetězce nebo pole znaků, které mají být zkopírovány.

*_Num*\
Počet prvků, které mají být zkopírovány.

### <a name="return-value"></a>Návratová hodnota

První prvek zkopírovaný do pole řetězce nebo znaků cílený pro příjem zkopírované sekvence znaků.

### <a name="remarks"></a>Poznámky

Sekvence zdrojových a cílových znaků se nesmí překrývat.

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

## <a name="char_traits_copy_s"></a><a name="copy_s"></a>char_traits::_Copy_s

Zkopíruje zadaný počet znaků z jednoho řetězce do druhého.

```cpp
static char_type *_Copy_s(
    char_type* dest,
    size_t dest_size,
    const char_type* _From,
    size_t count);
```

### <a name="parameters"></a>Parametry

*Dest*\
Pole řetězce nebo znaků určené pro příjem zkopírované sekvence znaků.

*dest_size*\
Velikost *dest*. Pokud `char_type` je **char**, pak tato velikost je v bajtů. Pokud `char_type` je **wchar_t**, pak tato velikost je ve slovech.

*_From*\
Zdrojový řetězec nebo pole znaků, které mají být zkopírovány.

*Počet*\
Počet prvků, které mají být zkopírovány.

### <a name="return-value"></a>Návratová hodnota

Pole řetězce nebo znaků určené pro příjem zkopírované sekvence znaků.

### <a name="remarks"></a>Poznámky

Sekvence zdrojových a cílových znaků se nesmí překrývat.

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

## <a name="char_traitseof"></a><a name="eof"></a>char_traits::eof

Vrátí znak konce souboru (EOF).

```cpp
static int_type eof();
```

### <a name="return-value"></a>Návratová hodnota

Znak EOF.

### <a name="remarks"></a>Poznámky

Hodnota, která představuje konec souboru (například EOF nebo WEOF).

Standard Jazyka C++ uvádí, že tato `char_type` hodnota nesmí odpovídat platné hodnotě. Kompilátor Microsoft C++ vynucuje toto omezení pro **typ char**, ale ne pro typ **wchar_t**. To zachycuje níže uvedený příklad.

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

## <a name="char_traitseq"></a><a name="eq"></a>char_traits::eq

Testuje, `char_type` zda jsou dva znaky stejné.

```cpp
static bool eq(const char_type& _Ch1, const char_type& _Ch2);
```

### <a name="parameters"></a>Parametry

*_Ch1*\
První ze dvou znaků, které mají být testovány na rovnost.

*_Ch2*\
Druhý ze dvou znaků, které mají být testovány na rovnost.

### <a name="return-value"></a>Návratová hodnota

**true,** pokud se první znak rovná druhému znaku; jinak **false**.

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

## <a name="char_traitseq_int_type"></a><a name="eq_int_type"></a>char_traits::eq_int_type

Testuje, zda jsou `int_type`dva znaky reprezentované jako s stejné nebo ne.

```cpp
static bool eq_int_type(const int_type& _Ch1, const int_type& _Ch2);
```

### <a name="parameters"></a>Parametry

*_Ch1*\
První ze dvou znaků, které mají být `int_type`testovány na rovnost jako s.

*_Ch2*\
Druhý ze dvou znaků, které mají být `int_type`testovány na rovnost jako s.

### <a name="return-value"></a>Návratová hodnota

**true,** pokud se první znak rovná druhému znaku; jinak **false**.

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

## <a name="char_traitsfind"></a><a name="find"></a>char_traits::najít

Vyhledá první výskyt zadaného znaku v rozsahu znaků.

```cpp
static const char_type* find(const char_type* str,
    size_t _Num,
    const char_type& _Ch);
```

### <a name="parameters"></a>Parametry

*Str*\
První znak v řetězci, který má být prohledán.

*_Num*\
Počet pozic, počítáno od prvního, v rozsahu, který má být prohledán.

*_Ch*\
Znak, který má být vyhledán v rozsahu.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na první výskyt zadaného znaku v oblasti, pokud je nalezena shoda; jinak ukazatel null.

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

## <a name="char_traitsint_type"></a><a name="int_type"></a>char_traits::int_type

Celočíselný typ, který může představovat znak typu `char_type` nebo znak konce souboru (EOF).

```cpp
typedef long int_type;
```

### <a name="remarks"></a>Poznámky

Musí být možné zadat přetypování `CharType` `int_type` hodnoty typu `CharType` do té doby zpět, aniž by došlo ke změně původní hodnoty.

### <a name="example"></a>Příklad

Příklad pro [eq_int_type](#eq_int_type) najdete příklad, jak `int_type`deklarovat a používat .

## <a name="char_traitslength"></a><a name="length"></a>char_traits::délka

Vrátí délku řetězce.

```cpp
static size_t length(const char_type* str);
```

### <a name="parameters"></a>Parametry

*Str*\
Řetězec C, jehož délka se měří.

### <a name="return-value"></a>Návratová hodnota

Počet prvků v pořadí se měří, bez hodnoty null zakončení.

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

## <a name="char_traitslt"></a><a name="lt"></a>char_traits::Lt

Testuje, zda jeden znak je menší než jiný.

```cpp
static bool lt(const char_type& _Ch1, const char_type& _Ch2);
```

### <a name="parameters"></a>Parametry

*_Ch1*\
První ze dvou znaků, které mají být testovány na méně než.

*_Ch2*\
Druhý ze dvou znaků, které mají být testovány na menší než.

### <a name="return-value"></a>Návratová hodnota

**true,** pokud je první znak menší než druhý znak; jinak **false**.

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

## <a name="char_traitsmove"></a><a name="move"></a>char_traits::přesunout

Zkopíruje zadaný počet znaků v sekvenci do jiné, případně překrývající se sekvence.

Tato metoda je potenciálně nebezpečné, protože spoléhá na volajícího zkontrolovat, že předané hodnoty jsou správné. Zvažte použití [char_traits::_Move_s.](#move_s)

```cpp
static char_type *move(char_type* _To,
    const char_type* _From,
    size_t _Num);
```

### <a name="parameters"></a>Parametry

*_To*\
Prvek na začátku řetězce nebo pole znaků zaměřených na příjem zkopírované sekvence znaků.

*_From*\
Prvek na začátku zdrojového řetězce nebo pole znaků, které mají být zkopírovány.

*_Num*\
Počet prvků, které mají být zkopírovány ze zdrojového řetězce.

### <a name="return-value"></a>Návratová hodnota

První prvek *_To* zkopírován do pole řetězce nebo znaků, které má být určeno pro příjem zkopírované posloupnosti znaků.

### <a name="remarks"></a>Poznámky

Zdroj a cíl se mohou překrývat.

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

## <a name="char_traits_move_s"></a><a name="move_s"></a>char_traits::_Move_s

Zkopíruje zadaný počet znaků v sekvenci do jiné, případně překrývající se sekvence.

```cpp
static char_type *_Move_s(
    char_type* dest,
    size_t dest_size,
    const char_type* _From,
    size_t count);
```

### <a name="parameters"></a>Parametry

*Dest*\
Prvek na začátku řetězce nebo pole znaků zaměřených na příjem zkopírované sekvence znaků.

*dest_size*\
Velikost *dest*. Pokud `char_type` je **char**, pak je to v bajtů. Pokud `char_type` je **wchar_t**, pak je to ve slovech.

*_From*\
Prvek na začátku zdrojového řetězce nebo pole znaků, které mají být zkopírovány.

*Počet*\
Počet prvků, které mají být zkopírovány ze zdrojového řetězce.

### <a name="return-value"></a>Návratová hodnota

První prvek *dest* zkopírovány do řetězce nebo pole znaků cílené na příjem zkopírované sekvence znaků.

### <a name="remarks"></a>Poznámky

Zdroj a cíl se mohou překrývat.

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

## <a name="char_traitsnot_eof"></a><a name="not_eof"></a>char_traits::not_eof

Testuje, zda znak není znak konce souboru (EOF) znak nebo je EOF.

```cpp
static int_type not_eof(const int_type& _Ch);
```

### <a name="parameters"></a>Parametry

*_Ch*\
Znak reprezentovaný jako `int_type` a má být testován, zda se jedná o znak EOF nebo ne.

### <a name="return-value"></a>Návratová hodnota

Reprezentace `int_type` testovaného znaku, `int_type` pokud znak není roven znaku Znak EOF.

Pokud je `int_type` hodnota znaku rovna hodnotě EOF, `int_type` pak **false**.

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

## <a name="char_traitsoff_type"></a><a name="off_type"></a>char_traits::off_type

Typ celéčíslo, který může představovat posuny mezi pozicemi v datovém proudu.

```cpp
typedef streamoff off_type;
```

### <a name="remarks"></a>Poznámky

Typ je podepsané celé číslo, které popisuje objekt, který může uložit posun bajtu zapojený do různých operací umístění datového proudu. Obvykle je synonymem pro [streamoff](../standard-library/ios-typedefs.md#streamoff), ale má v podstatě stejné vlastnosti jako tento typ.

## <a name="char_traitspos_type"></a><a name="pos_type"></a>char_traits::pos_type

Typ celéčíslo, který může představovat pozice v datovém proudu.

```cpp
typedef streampos pos_type;
```

### <a name="remarks"></a>Poznámky

Typ popisuje objekt, který můžete uložit všechny informace potřebné k obnovení indikátoru libovolné pozice souboru v rámci datového proudu. Obvykle je synonymem pro [streampos](../standard-library/ios-typedefs.md#streampos), ale v každém případě má v podstatě stejné vlastnosti jako tento typ.

## <a name="char_traitsstate_type"></a><a name="state_type"></a>char_traits::state_type

Typ, který představuje stav převodu vícebajtových znaků v datovém proudu.

```cpp
typedef implementation-defined state_type;
```

### <a name="remarks"></a>Poznámky

Typ popisuje objekt, který může představovat stav převodu. Obvykle je synonymem `mbstate_t`pro , ale v každém případě má v podstatě stejné vlastnosti jako tento typ.

## <a name="char_traitsto_char_type"></a><a name="to_char_type"></a>char_traits::to_char_type

Převede `int_type` znak na `char_type` odpovídající znak a vrátí výsledek.

```cpp
static char_type to_char_type(const int_type& _Ch);
```

### <a name="parameters"></a>Parametry

*_Ch*\
Znak, `int_type` který má `char_type`být reprezentován jako .

### <a name="return-value"></a>Návratová hodnota

Znak `char_type` odpovídající znaku. `int_type`

Hodnota *_Ch,* které nemohou být reprezentovány jako takové výnosy nespecifikovaný výsledek.

### <a name="remarks"></a>Poznámky

Operace převodu `to_char_type` [to_int_type](#to_int_type) a jsou k sobě inverzní, takže:

`to_int_type`( `to_char_type` ( *x* ) == *x*

pro `int_type` všechny *x* a

`to_char_type`( `to_int_type` ( *x* ) == *x*

pro `char_type` všechny *x*.

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

## <a name="char_traitsto_int_type"></a><a name="to_int_type"></a>char_traits::to_int_type

Převede `char_type` znak na `int_type` odpovídající znak a vrátí výsledek.

```cpp
static int_type to_int_type(const char_type& _Ch);
```

### <a name="parameters"></a>Parametry

*_Ch*\
Znak, `char_type` který má `int_type`být reprezentován jako .

### <a name="return-value"></a>Návratová hodnota

Znak `int_type` odpovídající znaku. `char_type`

### <a name="remarks"></a>Poznámky

Operace `to_int_type` převodu a [to_char_type](#to_char_type) jsou inverzní k sobě navzájem, tak, že:

`to_int_type`( `to_char_type` ( *x* ) == *x*

pro `int_type` všechny *x*a

`to_char_type`( `to_int_type` ( *x* ) == *x*

pro `char_type` všechny *x*.

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

[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
