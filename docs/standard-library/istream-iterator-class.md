---
title: istream_iterator – třída
ms.date: 11/04/2016
f1_keywords:
- iterator/std::istream_iterator
- iterator/std::istream_iterator::char_type
- iterator/std::istream_iterator::istream_type
- iterator/std::istream_iterator::traits_type
helpviewer_keywords:
- std::istream_iterator [C++]
- std::istream_iterator [C++], char_type
- std::istream_iterator [C++], istream_type
- std::istream_iterator [C++], traits_type
ms.assetid: fb52a8cd-7f71-48d1-b73e-4b064e2a8d16
ms.openlocfilehash: 941d625e388edc75dfe25a2de0e609c6d955ff19
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78869887"
---
# <a name="istream_iterator-class"></a>istream_iterator – třída

Popisuje objekt vstupního iterátoru. Extrahuje objekty třídy `Type` ze vstupního datového proudu, ke kterému přistupuje prostřednictvím objektu, který ukládá, typu `pointer` na `basic_istream`< `CharType``Traits`>.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Type, class CharType = char, class Traits = char_traits<CharType>, class Distance = ptrdiff_t,>
class istream_iterator
: public iterator<
    input_iterator_tag, Type, Distance,
    const Type *,
    const Type&>;
```

### <a name="parameters"></a>Parametry

*Zadejte*\
Typ objektu, který má být extrahován ze vstupního datového proudu.

*CharType*\
Typ, který představuje typ znaku pro `istream_iterator`. Tento argument je nepovinný a výchozí hodnota je **char**.

\ *vlastností*
Typ, který představuje typ znaku pro `istream_iterator`. Tento argument je nepovinný a výchozí hodnota je `char_traits`< `CharType`>.

\ *vzdálenosti*
Podepsaný integrální typ, který představuje typ rozdílu pro `istream_iterator`. Tento argument je nepovinný a výchozí hodnota je `ptrdiff_t`.

Po sestavení nebo zvýšení objektu třídy istream_iterator s nenulovým uloženým ukazatelem se objekt pokusí extrahovat a uložit objekt typu `Type` z přidruženého vstupního datového proudu. Pokud se extrakce nezdaří, objekt nahradí uložený ukazatel ukazatelem s hodnotou null a vytvoří tak indikátor ukončení sekvence.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[istream_iterator](#istream_iterator)|Vytvoří buď iterátor koncového datového proudu jako výchozí `istream_iterator` nebo `istream_iterator` inicializovaný jako typ datového proudu iterátoru, ze kterého čte.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[char_type](#char_type)|Typ, který poskytuje typ znaku `istream_iterator`.|
|[istream_type](#istream_type)|Typ, který poskytuje typ datového proudu `istream_iterator`.|
|[traits_type](#traits_type)|Typ, který poskytuje typ znakových vlastností `istream_iterator`.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[podnikatel](#op_star)|Operátor přesměrování vrací uložený objekt typu `Type` adresovaná `istream_iterator`.|
|[operátor->](#op_arrow)|Vrátí hodnotu členu, pokud existuje.|
|[operator + + – operátor](#op_add_add)|Buď zkopíruje zvýšený objekt ze vstupního datového proudu, nebo zkopíruje objekt před jeho zvýšením a vrátí kopii.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<iterátor >

**Obor názvů:** std

## <a name="char_type"></a>istream_iterator:: char_type

Typ, který poskytuje typ znaku `istream_iterator`.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro parametr šablony `Chartype`.

### <a name="example"></a>Příklad

```cpp
// istream_iterator_char_type.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   typedef istream_iterator<int>::char_type CHT1;
   typedef istream_iterator<int>::traits_type CHTR1;

   // Standard iterator interface for reading
   // elements from the input stream:
   cout << "Enter integers separated by spaces & then\n"
        << " any character ( try example: '2 4 f' ): ";

   // istream_iterator for reading int stream
   istream_iterator<int, CHT1, CHTR1> intRead ( cin );

   // End-of-stream iterator
   istream_iterator<int, CHT1, CHTR1> EOFintRead;

   while ( intRead != EOFintRead )
   {
      cout << "Reading:  " << *intRead << endl;
      ++intRead;
   }
   cout << endl;
}
```

## <a name="istream_iterator"></a>istream_iterator:: istream_iterator

Vytvoří buď iterátor koncového datového proudu jako výchozí `istream_iterator` nebo `istream_iterator` inicializovaný jako typ datového proudu iterátoru, ze kterého čte.

```cpp
istream_iterator();

istream_iterator(istream_type& _Istr);
```

### <a name="parameters"></a>Parametry

*_Istr*\
Vstupní datový proud, který má být použit pro inicializaci `istream_iterator`.

### <a name="remarks"></a>Poznámky

První konstruktor inicializuje ukazatel vstupního datového proudu s ukazatelem s hodnotou null a vytvoří iterátor konec datového proudu. Druhý konstruktor inicializuje ukazatel vstupního datového proudu pomocí *& _Istr*a potom se pokusí extrahovat a uložit objekt typu `Type`.

Iterátor konce datového proudu lze použít k otestování, zda `istream_iterator` dosáhla konce datového proudu.

### <a name="example"></a>Příklad

```cpp
// istream_iterator_istream_iterator.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <algorithm>
#include <iostream>

int main( )
{
   using namespace std;

   // Used in conjunction with copy algorithm
   // to put elements into a vector read from cin
   vector<int> vec ( 4 );
   vector <int>::iterator Iter;

   cout << "Enter 4 integers separated by spaces & then\n"
        << " a character ( try example: '2 4 6 8 a' ): ";
   istream_iterator<int> intvecRead ( cin );

   // Default constructor will test equal to end of stream
   // for delimiting source range of vecor
   copy ( intvecRead , istream_iterator<int>( ) , vec.begin ( ) );
   cin.clear ( );

   cout << "vec = ";
   for ( Iter = vec.begin( ) ; Iter != vec.end( ) ; Iter++ )
      cout << *Iter << " "; cout << endl;
}
```

## <a name="istream_type"></a>istream_iterator:: istream_type

Typ, který poskytuje typ datového proudu `istream_iterator`.

```cpp
typedef basic_istream<CharType, Traits> istream_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro `basic_istream`\< **CharType**, **vlastnosti**>.

### <a name="example"></a>Příklad

Příklad, jak deklarovat a používat `istream_type`, naleznete v tématu [istream_iterator](#istream_iterator) .

## <a name="op_star"></a>istream_iterator:: operator *

Operátor přesměrování vrací uložený objekt typu `Type` adresovaná `istream_iterator`.

```cpp
const Type& operator*() const;
```

### <a name="return-value"></a>Návratová hodnota

Uložený objekt typu `Type`.

### <a name="example"></a>Příklad

```cpp
// istream_iterator_operator.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <algorithm>
#include <iostream>

int main( )
{
   using namespace std;

   cout << "Enter integers separated by spaces & then\n"
        << " a character ( try example: '2 4 6 8 a' ): ";

   // istream_iterator from stream cin
   istream_iterator<int> intRead ( cin );

   // End-of-stream iterator
   istream_iterator<int> EOFintRead;

   while ( intRead != EOFintRead )
   {
      cout << "Reading:  " << *intRead << endl;
      ++intRead;
   }
   cout << endl;
}
```

## <a name="op_arrow"></a>istream_iterator:: operator-&gt;

Vrátí hodnotu členu, pokud existuje.

```cpp
const Type* operator->() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota člena, pokud existuje.

### <a name="remarks"></a>Poznámky

`i->m` je ekvivalentem `(*i).m`

Operátor vrací `&*this`.

### <a name="example"></a>Příklad

```cpp
// istream_iterator_operator_vm.cpp
// compile with: /EHsc
#include <iterator>
#include <iostream>
#include <complex>

using namespace std;

int main( )
{
   cout << "Enter complex numbers separated by spaces & then\n"
        << " a character pair ( try example: '(1,2) (3,4) (a,b)' ): ";

   // istream_iterator from stream cin
   istream_iterator< complex<double> > intRead ( cin );

   // End-of-stream iterator
   istream_iterator<complex<double> > EOFintRead;

   while ( intRead != EOFintRead )
   {
      cout << "Reading the real part: " << intRead ->real( ) << endl;
      cout << "Reading the imaginary part: " << intRead ->imag( ) << endl;
      ++intRead;
   }
   cout << endl;
}
```

## <a name="op_add_add"></a>istream_iterator:: operator + +

Buď zkopíruje zvýšený objekt ze vstupního datového proudu, nebo zkopíruje objekt před jeho zvýšením a vrátí kopii.

```cpp
istream_iterator<Type, CharType, Traits, Distance>& operator++();

istream_iterator<Type, CharType, Traits, Distance> operator++(int);
```

### <a name="return-value"></a>Návratová hodnota

První operátor členu vrátí odkaz na přírůstek objektu typu `Type` extrahován ze vstupního datového proudu a druhá členská funkce vrátí kopii objektu.

### <a name="example"></a>Příklad

```cpp
// istream_iterator_operator_incr.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <algorithm>
#include <iostream>

int main( )
{
   using namespace std;

   cout << "Enter integers separated by spaces & then\n"
        << " a character ( try example: '2 4 6 8 a' ): ";

   // istream_iterator from stream cin
   istream_iterator<int> intRead ( cin );

   // End-of-stream iterator
   istream_iterator<int> EOFintRead;

   while ( intRead != EOFintRead )
   {
      cout << "Reading:  " << *intRead << endl;
      ++intRead;
   }
   cout << endl;
}
```

## <a name="traits_type"></a>istream_iterator:: traits_type

Typ, který poskytuje typ znakových vlastností `istream_iterator`.

```cpp
typedef Traits traits_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro *vlastnosti*parametrů šablony.

### <a name="example"></a>Příklad

```cpp
// istream_iterator_traits_type.cpp
// compile with: /EHsc
#include <iterator>
#include <iostream>

int main( )
{
   using namespace std;

   typedef istream_iterator<int>::char_type CHT1;
   typedef istream_iterator<int>::traits_type CHTR1;

   // Standard iterator interface for reading
   // elements from the input stream:
   cout << "Enter integers separated by spaces & then\n"
        << " any character ( try example: '10 20 a' ): ";

   // istream_iterator for reading int stream
   istream_iterator<int, CHT1, CHTR1> intRead ( cin );

   // End-of-stream iterator
   istream_iterator<int, CHT1, CHTR1> EOFintRead;

   while ( intRead != EOFintRead )
   {
      cout << "Reading:  " << *intRead << endl;
      ++intRead;
   }
   cout << endl;
}
```

## <a name="see-also"></a>Viz také

[Input_iterator_tag struktura](../standard-library/input-iterator-tag-struct.md)\
\ [struktury iterátoru](../standard-library/iterator-struct.md)
[> iterátoru\<](../standard-library/iterator.md)\
[Bezpečnost vlákna ve C++ standardní knihovně](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)
