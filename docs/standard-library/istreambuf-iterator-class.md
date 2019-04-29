---
title: istreambuf_iterator – třída
ms.date: 11/04/2016
f1_keywords:
- streambuf/std::istreambuf_iterator
- iterator/std::istreambuf_iterator::char_type
- iterator/std::istreambuf_iterator::int_type
- iterator/std::istreambuf_iterator::istream_type
- iterator/std::istreambuf_iterator::streambuf_type
- iterator/std::istreambuf_iterator::traits_type
- iterator/std::istreambuf_iterator::equal
helpviewer_keywords:
- std::istreambuf_iterator [C++]
- std::istreambuf_iterator [C++], char_type
- std::istreambuf_iterator [C++], int_type
- std::istreambuf_iterator [C++], istream_type
- std::istreambuf_iterator [C++], streambuf_type
- std::istreambuf_iterator [C++], traits_type
- std::istreambuf_iterator [C++], equal
ms.assetid: 39002da2-61a6-48a5-9d0c-5df8271f6038
ms.openlocfilehash: 41298909b53de1c7acf3cb8ae4b999eb6260765d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62413265"
---
# <a name="istreambufiterator-class"></a>istreambuf_iterator – třída

Třída šablony istreambuf_iterator popisuje objekt vstupního iterátoru extrahujícího prvky znaků z vyrovnávací paměti vstupního datového proudu, ke kterému přistupuje prostřednictvím objektu, který ukládá, typu ukazatele do `basic_streambuf` \< **CharType** , **Osobnostní rysy**>.

## <a name="syntax"></a>Syntaxe

```cpp
template <class CharType class Traits = char_traits <CharType>>
class istreambuf_iterator
: public iterator<input_iterator_tag, CharType, typename Traits ::off_type, CharType*, CharType&>
```

### <a name="parameters"></a>Parametry

*CharType*<br/>
Typ, který představuje typ znaku pro istreambuf_iterator.

*Osobnostní rysy*<br/>
Typ, který představuje typ znaku pro istreambuf_iterator. Tento argument je nepovinný a výchozí hodnota je `char_traits` \< *CharType >.*

## <a name="remarks"></a>Poznámky

Třída istreambuf_iterator musí splňovat požadavky na vstupní iterátor.

Po vytvoření nebo zvýšení objektu třídy istreambuf_iterator pomocí uloženého ukazatele bez hodnoty null, se objekt pokusí extrahovat a uložit objekt typu *CharType* z přidruženého vstupního datového proudu. Extrakci lze však odložit, dokud nebude objekt skutečně odkazován nebo zkopírován. Pokud se extrakce nezdaří, objekt nahradí uložený ukazatel ukazatelem s hodnotou null a vytvoří tak indikátor ukončení sekvence.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[istreambuf_iterator](#istreambuf_iterator)|Vytvoří `istreambuf_iterator` , která je inicializována pro čtení znaků ze vstupního datového proudu.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[char_type](#char_type)|Typ, který poskytuje typ znaku pro `ostreambuf_iterator`.|
|[int_type](#int_type)|Typ, který poskytuje typ integer pro `istreambuf_iterator`.|
|[istream_type](#istream_type)|Typ, který poskytuje typ toku pro `istream_iterator`.|
|[streambuf_type](#streambuf_type)|Typ, který poskytuje typ toku pro `istreambuf_iterator`.|
|[traits_type](../standard-library/istream-iterator-class.md#traits_type)|Typ, který poskytuje typ vlastností `istream_iterator`.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[rovno](#equal)|Ověřuje rovnost mezi dvěma iterátory vyrovnávací paměti vstupního toku.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[Operator *](#op_star)|Dereferenční operátor vrátí následující znak v toku.|
|[Operator ++](#op_add_add)|Vrátí buď následující znak ze vstupního toku, nebo zkopíruje objekt před jeho zvýšením a vrátí kopii.|
|[operator->](#op_arrow)|Vrátí hodnotu členu, pokud existuje.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<iterátor >

**Namespace:** std

## <a name="char_type"></a>  istreambuf_iterator::char_type

Typ, který poskytuje typ znaku pro `ostreambuf_iterator`.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro parametr šablony *CharType*.

### <a name="example"></a>Příklad

```cpp
// istreambuf_iterator_char_type.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>
#include <algorithm>

int main( )
{
   using namespace std;

   typedef istreambuf_iterator<char>::char_type CHT1;
   typedef istreambuf_iterator<char>::traits_type CHTR1;

   cout << "(Try the example: 'So many dots to be done'\n"
        << " then an Enter key to insert into the output,\n"
        << " & use a ctrl-Z Enter key combination to exit): ";

   // istreambuf_iterator for input stream
   istreambuf_iterator< CHT1, CHTR1> charInBuf ( cin );
   ostreambuf_iterator<char> charOut ( cout );

   // Used in conjunction with replace_copy algorithm
   // to insert into output stream and replace spaces
   // with dot-separators
   replace_copy ( charInBuf , istreambuf_iterator<char>( ),
        charOut , ' ' , '.' );
}
```

## <a name="equal"></a>  istreambuf_iterator::EQUAL

Testy pro ekvivalence mezi dvěma iterátory vyrovnávací paměti vstupního datového proudu.

```cpp
bool equal(const istreambuf_iterator<CharType, Traits>& right) const;
```

### <a name="parameters"></a>Parametry

*doprava*<br/>
Iterátor, pro který chcete zkontrolovat rovnosti.

### <a name="return-value"></a>Návratová hodnota

**true** Pokud mají oba `istreambuf_iterator`jsou s iterátory ukončení datového proudu nebo pokud ani jeden není ukončení datového proudu iterátoru; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Rozsah je definován `istreambuf_iterator` na aktuální pozici a ukončení datového proudu iterátoru, ale od všech jiných konce datového proudu iterátory jsou ekvivalentní pod `equal` členskou funkci, není možné definovat žádné podrozsahů pomocí `istreambuf_iterator`s. `==` a `!=` operátory mají stejnou sémantiku.

### <a name="example"></a>Příklad

```cpp
// istreambuf_iterator_equal.cpp
// compile with: /EHsc
#include <iterator>
#include <iostream>

int main( )
{
   using namespace std;

   cout << "(Try the example: 'Hello world!'\n"
        << " then an Enter key to insert into the output,\n"
        << " & use a ctrl-Z Enter key combination to exit): ";

   istreambuf_iterator<char> charReadIn1 ( cin );
   istreambuf_iterator<char> charReadIn2 ( cin );

   bool b1 = charReadIn1.equal ( charReadIn2 );

   if (b1)
      cout << "The iterators are equal." << endl;
   else
      cout << "The iterators are not equal." << endl;
}
```

## <a name="int_type"></a>  istreambuf_iterator::int_type

Typ, který poskytuje typ integer pro `istreambuf_iterator`.

```cpp
typedef typename traits_type::int_type int_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro `Traits::int_type`.

### <a name="example"></a>Příklad

```cpp
// istreambuf_iterator_int_type.cpp
// compile with: /EHsc
#include <iterator>
#include <iostream>

int main( )
{
   using namespace std;
   istreambuf_iterator<char>::int_type inttype1 = 100;
   cout << "The inttype1 = " << inttype1 << "." << endl;
}
/* Output:
The inttype1 = 100.
*/
```

## <a name="istream_type"></a>  istreambuf_iterator::istream_type

Typ, který poskytuje typ toku pro `istreambuf_iterator`.

```cpp
typedef basic_istream<CharType, Traits> istream_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro `basic_istream` \< **CharType**, **osobnostní rysy**>.

### <a name="example"></a>Příklad

Zobrazit [istreambuf_iterator](#istreambuf_iterator) příklad toho, jak deklarace a používání `istream_type`.

## <a name="istreambuf_iterator"></a>  istreambuf_iterator::istreambuf_iterator

Sestaví istreambuf_iterator, který je inicializován pro čtení znaků ze vstupního datového proudu.

```cpp
istreambuf_iterator(streambuf_type* strbuf = 0) throw();
istreambuf_iterator(istream_type& _Istr) throw();
```

### <a name="parameters"></a>Parametry

*strbuf*<br/>
Vyrovnávací paměti vstupního toku, ke kterému `istreambuf_iterator` je připojeno.

*_Istr*<br/>
Vstupní proud, do kterého `istreambuf_iterator` je připojeno.

### <a name="remarks"></a>Poznámky

První konstruktor inicializuje ukazatele vstupní vyrovnávací paměť datového proudu s *strbuf*. Druhý konstruktor inicializuje ukazatele vstupní vyrovnávací paměť datového proudu s *_Istr*. `rdbuf`a poté server se pokusí extrahovat a uložit objekt typu `CharType`.

### <a name="example"></a>Příklad

```cpp
// istreambuf_iterator_istreambuf_iterator.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <algorithm>
#include <iostream>

int main( )
{
   using namespace std;

   // Following declarations will not compile:
   istreambuf_iterator<char>::istream_type &istrm = cin;
   istreambuf_iterator<char>::streambuf_type *strmbf = cin.rdbuf( );

   cout << "(Try the example: 'Oh what a world!'\n"
      << " then an Enter key to insert into the output,\n"
      << " & use a ctrl-Z Enter key combination to exit): ";
   istreambuf_iterator<char> charReadIn ( cin );
   ostreambuf_iterator<char> charOut ( cout );

   // Used in conjunction with replace_copy algorithm
   // to insert into output stream and replace spaces
   // with hyphen-separators
   replace_copy ( charReadIn , istreambuf_iterator<char>( ),
      charOut , ' ' , '-' );
}
```

## <a name="op_star"></a>  istreambuf_iterator::Operator *

Dereferenční operátor vrátí následující znak v toku.

```cpp
CharType operator*() const;
```

### <a name="return-value"></a>Návratová hodnota

Další znak v datovém proudu.

### <a name="example"></a>Příklad

```cpp
// istreambuf_iterator_operator_deref.cpp
// compile with: /EHsc
#include <iterator>
#include <iostream>

int main( )
{
   using namespace std;

   cout << "Type string of characters & enter to output it,\n"
      << " with stream buffer iterators,(try: 'I'll be back.')\n"
      << " repeat as many times as desired,\n"
      << " then keystroke ctrl-Z Enter to exit program: ";
   istreambuf_iterator<char> inpos ( cin );
   istreambuf_iterator<char> endpos;
   ostreambuf_iterator<char> outpos ( cout );
   while ( inpos != endpos )
   {
*outpos = *inpos;   //Put value of outpos equal to inpos
      ++inpos;
      ++outpos;
   }
}
```

## <a name="op_add_add"></a>  istreambuf_iterator::Operator ++

Vrátí buď následující znak ze vstupního toku, nebo zkopíruje objekt před jeho zvýšením a vrátí kopii.

```cpp
istreambuf_iterator<CharType, Traits>& operator++();
istreambuf_iterator<CharType, Traits> operator++(int);
```

### <a name="return-value"></a>Návratová hodnota

`istreambuf_iterator` Nebo odkaz na `istreambuf_iterator`.

### <a name="remarks"></a>Poznámky

První operátor nakonec se pokusí extrahovat a uložit objekt typu `CharType` z přidruženého vstupního datového proudu. Druhý operátor vytvoří kopii tohoto objektu, zvýší na objekt a potom vrátí kopii.

### <a name="example"></a>Příklad

```cpp
// istreambuf_iterator_operator_incr.cpp
// compile with: /EHsc
#include <iterator>
#include <iostream>

int main( )
{
   using namespace std;

   cout << "Type string of characters & enter to output it,\n"
      << " with stream buffer iterators,(try: 'I'll be back.')\n"
      << " repeat as many times as desired,\n"
      << " then keystroke ctrl-Z Enter to exit program: ";
   istreambuf_iterator<char> inpos ( cin );
   istreambuf_iterator<char> endpos;
   ostreambuf_iterator<char> outpos ( cout );
   while ( inpos != endpos )
   {
*outpos = *inpos;
      ++inpos;   //Increment istreambuf_iterator
      ++outpos;
   }
}
```

## <a name="op_arrow"></a>  istreambuf_iterator::Operator-&gt;

Vrátí hodnotu členu, pokud existuje.

```cpp
const Elem* operator->() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí operátor  **& \* \*to**.

## <a name="streambuf_type"></a>  istreambuf_iterator::streambuf_type

Typ, který poskytuje typ toku pro istreambuf_iterator.

```cpp
typedef basic_streambuf<CharType, Traits> streambuf_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro `basic_streambuf` \< **CharType**, **osobnostní rysy**>.

### <a name="example"></a>Příklad

Zobrazit [istreambuf_iterator](#istreambuf_iterator) příklad toho, jak deklarace a používání `istreambuf_type`.

## <a name="traits_type"></a>  istreambuf_iterator::traits_type

Typ, který poskytuje typ vlastností `istream_iterator`.

```cpp
typedef Traits traits_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro parametr šablony *osobnostní rysy*.

### <a name="example"></a>Příklad

```cpp
// istreambuf_iterator_traits_type.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>
#include <algorithm>

int main( )
{
   using namespace std;

   typedef istreambuf_iterator<char>::char_type CHT1;
   typedef istreambuf_iterator<char>::traits_type CHTR1;

   cout << "(Try the example: 'So many dots to be done'\n"
        << " then an Enter key to insert into the output,\n"
        << " & use a ctrl-Z Enter key combination to exit): ";

   // istreambuf_iterator for input stream
   istreambuf_iterator< CHT1, CHTR1> charInBuf ( cin );
   ostreambuf_iterator<char> charOut ( cout );

   // Used in conjunction with replace_copy algorithm
   // to insert into output stream and replace spaces
   // with dot-separators
   replace_copy ( charInBuf , istreambuf_iterator<char>( ),
        charOut , ' ' , '.' );
}
```

## <a name="see-also"></a>Viz také:

[iterator – struktura](../standard-library/iterator-struct.md)<br/>
[\<iterator>](../standard-library/iterator.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)<br/>
