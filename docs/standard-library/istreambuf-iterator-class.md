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
ms.openlocfilehash: 80bca2160f2e60938e9d0c85557b11a273c23264
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363066"
---
# <a name="istreambuf_iterator-class"></a>istreambuf_iterator – třída

Šablona třídy istreambuf_iterator popisuje vstupní iterátor objekt, který extrahuje prvky znaků ze vyrovnávací paměti vstupního `basic_streambuf` \< datového proudu, ke kterému přistupuje prostřednictvím objektu, který ukládá, ukazatele typu **CharType**, **Vlastnosti**>.

## <a name="syntax"></a>Syntaxe

```cpp
template <class CharType class Traits = char_traits <CharType>>
class istreambuf_iterator
: public iterator<input_iterator_tag, CharType, typename Traits ::off_type, CharType*, CharType&>
```

### <a name="parameters"></a>Parametry

*Typ znaku*\
Typ, který představuje typ znaku pro istreambuf_iterator.

*Vlastnosti*\
Typ, který představuje typ znaku pro istreambuf_iterator. Tento argument je volitelný a `char_traits` \< výchozí hodnota je *CharType>.*

## <a name="remarks"></a>Poznámky

Třída istreambuf_iterator musí splňovat požadavky na vstupní iterátor.

Po vytvoření nebo zvýšení objektu třídy istreambuf_iterator s nenulovým uloženým ukazatelem se objekt efektivně pokusí extrahovat a uložit objekt typu *CharType* z přidruženého vstupního datového proudu. Extrakci lze však odložit, dokud nebude objekt skutečně odkazován nebo zkopírován. Pokud se extrakce nezdaří, objekt nahradí uložený ukazatel ukazatelem s hodnotou null a vytvoří tak indikátor ukončení sekvence.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[istreambuf_iterator](#istreambuf_iterator)|`istreambuf_iterator` Vytvoří, který je inicializován pro čtení znaků ze vstupního datového proudu.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[char_type](#char_type)|Typ, který poskytuje typ znaku `ostreambuf_iterator`.|
|[int_type](#int_type)|Typ, který poskytuje typ celé `istreambuf_iterator`číslo pro .|
|[istream_type](#istream_type)|Typ, který poskytuje pro typ `istream_iterator`datového proudu .|
|[streambuf_type](#streambuf_type)|Typ, který poskytuje pro typ `istreambuf_iterator`datového proudu .|
|[traits_type](../standard-library/istream-iterator-class.md#traits_type)|Typ, který poskytuje typ znakových `istream_iterator`znaků typu .|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[Stejné](#equal)|Ověřuje rovnost mezi dvěma iterátory vyrovnávací paměti vstupního toku.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operátor*](#op_star)|Dereferenční operátor vrátí následující znak v toku.|
|[operátor++](#op_add_add)|Vrátí buď následující znak ze vstupního toku, nebo zkopíruje objekt před jeho zvýšením a vrátí kopii.|
|[operátor->](#op_arrow)|Vrátí hodnotu členu, pokud existuje.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<> iterátoru

**Obor názvů:** std

## <a name="istreambuf_iteratorchar_type"></a><a name="char_type"></a>istreambuf_iterator::char_type

Typ, který poskytuje typ znaku `ostreambuf_iterator`.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymem pro parametr šablony *CharType*.

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

## <a name="istreambuf_iteratorequal"></a><a name="equal"></a>istreambuf_iterator::rovná se

Testy rovnocennosti mezi dvěma iterátory vyrovnávací paměti vstupního proudu.

```cpp
bool equal(const istreambuf_iterator<CharType, Traits>& right) const;
```

### <a name="parameters"></a>Parametry

*Právo*\
Iterátor, pro který chcete zkontrolovat rovnost.

### <a name="return-value"></a>Návratová hodnota

**true,** `istreambuf_iterator`pokud jsou oba s iterátory konce proudu nebo pokud ani jeden z nich není iterátor konce proudu; jinak **false**.

### <a name="remarks"></a>Poznámky

Rozsah je definován `istreambuf_iterator` na aktuální pozici a end-of-stream iterátor, ale protože všechny non-end-of stream iterátory jsou ekvivalentní v rámci `equal` členské `istreambuf_iterator`funkce, není možné definovat žádné podrozsahy pomocí s. A `==` `!=` operátory mají stejnou sémantiku.

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

## <a name="istreambuf_iteratorint_type"></a><a name="int_type"></a>istreambuf_iterator::int_type

Typ, který poskytuje typ celé `istreambuf_iterator`číslo pro .

```cpp
typedef typename traits_type::int_type int_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymem `Traits::int_type`pro .

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

## <a name="istreambuf_iteratoristream_type"></a><a name="istream_type"></a>istreambuf_iterator::istream_type

Typ, který poskytuje pro typ `istreambuf_iterator`datového proudu .

```cpp
typedef basic_istream<CharType, Traits> istream_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymem `basic_istream` \< pro **CharType**, **vlastnosti**>.

### <a name="example"></a>Příklad

Příklad, jak deklarovat a `istream_type`používat aplikaci , naleznete [v istreambuf_iterator.](#istreambuf_iterator)

## <a name="istreambuf_iteratoristreambuf_iterator"></a><a name="istreambuf_iterator"></a>istreambuf_iterator::istreambuf_iterator

Vytvoří istreambuf_iterator, která je inicializována pro čtení znaků ze vstupního datového proudu.

```cpp
istreambuf_iterator(streambuf_type* strbuf = 0) throw();
istreambuf_iterator(istream_type& _Istr) throw();
```

### <a name="parameters"></a>Parametry

*strbuf (Strbuf)*\
Vyrovnávací paměť vstupního `istreambuf_iterator` datového proudu, ke které je připojen.

*_Istr*\
Vstupní datový proud, `istreambuf_iterator` ke kterému je připojen.

### <a name="remarks"></a>Poznámky

První konstruktor inicializuje vstupní stream-buffer ukazatel *strbuf*. Druhý konstruktor inicializuje ukazatel vyrovnávací paměti vstupního datového proudu s *_Istr*. `rdbuf`a nakonec se pokusí extrahovat a uložit `CharType`objekt typu .

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

## <a name="istreambuf_iteratoroperator"></a><a name="op_star"></a>istreambuf_iterator::operátor*

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

## <a name="istreambuf_iteratoroperator"></a><a name="op_add_add"></a>istreambuf_iterator::operátor++

Vrátí buď následující znak ze vstupního toku, nebo zkopíruje objekt před jeho zvýšením a vrátí kopii.

```cpp
istreambuf_iterator<CharType, Traits>& operator++();
istreambuf_iterator<CharType, Traits> operator++(int);
```

### <a name="return-value"></a>Návratová hodnota

Nebo `istreambuf_iterator` odkaz na `istreambuf_iterator`.

### <a name="remarks"></a>Poznámky

První operátor se nakonec pokusí extrahovat a `CharType` uložit objekt typu z přidruženého vstupního datového proudu. Druhý operátor vytvoří kopii objektu, zintáží objekt a potom vrátí kopii.

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

## <a name="istreambuf_iteratoroperator-gt"></a><a name="op_arrow"></a>istreambuf_iterator::operátor-&gt;

Vrátí hodnotu členu, pokud existuje.

```cpp
const Elem* operator->() const;
```

### <a name="return-value"></a>Návratová hodnota

Operátor vrátí ** & \* \*toto**.

## <a name="istreambuf_iteratorstreambuf_type"></a><a name="streambuf_type"></a>istreambuf_iterator::streambuf_type

Typ, který poskytuje pro typ datového proudu istreambuf_iterator.

```cpp
typedef basic_streambuf<CharType, Traits> streambuf_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymem `basic_streambuf` \< pro **CharType**, **vlastnosti**>.

### <a name="example"></a>Příklad

Příklad, jak deklarovat a `istreambuf_type`používat aplikaci , naleznete [v istreambuf_iterator.](#istreambuf_iterator)

## <a name="istreambuf_iteratortraits_type"></a><a name="traits_type"></a>istreambuf_iterator::traits_type

Typ, který poskytuje typ znakových `istream_iterator`znaků typu .

```cpp
typedef Traits traits_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymem pro *vlastnosti*parametru šablony .

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

## <a name="see-also"></a>Viz také

[iterátor Struct](../standard-library/iterator-struct.md)\
[\<>iterátoru](../standard-library/iterator.md)\
[Bezpečnost vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Referenční příručka standardní knihovny jazyka C++](../standard-library/cpp-standard-library-reference.md)
