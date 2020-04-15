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
ms.openlocfilehash: 3766a93d7cba9096ce3ff775d94c17a85456fb00
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363104"
---
# <a name="istream_iterator-class"></a>istream_iterator – třída

Popisuje objekt vstupního iterátoru. Extrahuje objekty `Type` třídy ze vstupního datového proudu, ke `pointer` kterému `basic_istream` <  `CharType`přistupuje prostřednictvím objektu, který ukládá, typu , `Traits`>.

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

*Typ*\
Typ objektu, který má být extrahován ze vstupního datového proudu.

*Typ znaku*\
Typ, který představuje typ `istream_iterator`znaku pro . Tento argument je volitelný a výchozí hodnota je **char**.

*Vlastnosti*\
Typ, který představuje typ `istream_iterator`znaku pro . Tento argument je volitelný a `char_traits` <  `CharType` výchozí hodnota je>.

*Vzdálenost*\
Podepsaný integrální typ, který `istream_iterator`představuje typ rozdílu pro . Tento argument je volitelný a `ptrdiff_t`výchozí hodnota je .

Po vytvoření nebo zvýšení objektu třídy istream_iterator s nenulovým uloženým ukazatelem se objekt `Type` pokusí extrahovat a uložit objekt typu z přidruženého vstupního datového proudu. Pokud se extrakce nezdaří, objekt nahradí uložený ukazatel ukazatelem s hodnotou null a vytvoří tak indikátor ukončení sekvence.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[istream_iterator](#istream_iterator)|Vytvoří buď end-of-stream iterátor jako `istream_iterator` výchozí `istream_iterator` nebo inicializována iterátoru typu datového proudu, ze kterého čte.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[char_type](#char_type)|Typ, který poskytuje typ znaku `istream_iterator`.|
|[istream_type](#istream_type)|Typ, který poskytuje pro typ `istream_iterator`datového proudu .|
|[traits_type](#traits_type)|Typ, který poskytuje typ znakových `istream_iterator`znaků typu .|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operátor*](#op_star)|Operátor dereferencing vrátí uložený `Type` objekt typu, `istream_iterator`který je adresován .|
|[operátor->](#op_arrow)|Vrátí hodnotu členu, pokud existuje.|
|[operátor++](#op_add_add)|Buď zkopíruje zvýšený objekt ze vstupního datového proudu, nebo zkopíruje objekt před jeho zvýšením a vrátí kopii.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<> iterátoru

**Obor názvů:** std

## <a name="istream_iteratorchar_type"></a><a name="char_type"></a>istream_iterator::char_type

Typ, který poskytuje typ znaku `istream_iterator`.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymem pro `Chartype`parametr šablony .

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

## <a name="istream_iteratoristream_iterator"></a><a name="istream_iterator"></a>istream_iterator::istream_iterator

Vytvoří buď end-of-stream iterátor jako `istream_iterator` výchozí `istream_iterator` nebo inicializována iterátoru typu datového proudu, ze kterého čte.

```cpp
istream_iterator();

istream_iterator(istream_type& _Istr);
```

### <a name="parameters"></a>Parametry

*_Istr*\
Vstupní datový proud, který má být `istream_iterator`přečten, slouží k inicializaci .

### <a name="remarks"></a>Poznámky

První konstruktor inicializuje ukazatel vstupního datového proudu s ukazatelem null a vytvoří iterátor konce datového proudu. Druhý konstruktor inicializuje ukazatel vstupního datového proudu s *&_Istr*a `Type`poté se pokusí extrahovat a uložit objekt typu .

Uskutečňovat iterátor konce datového proudu `istream_iterator` lze použít k testování, zda dosáhl konce datového proudu.

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

## <a name="istream_iteratoristream_type"></a><a name="istream_type"></a>istream_iterator::istream_type

Typ, který poskytuje pro typ `istream_iterator`datového proudu .

```cpp
typedef basic_istream<CharType, Traits> istream_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymem `basic_istream` \< pro **CharType**, **vlastnosti**>.

### <a name="example"></a>Příklad

Příklad, jak deklarovat a `istream_type`používat aplikaci , naleznete [v istream_iterator.](#istream_iterator)

## <a name="istream_iteratoroperator"></a><a name="op_star"></a>istream_iterator::operátor*

Operátor dereferencing vrátí uložený `Type` objekt typu, `istream_iterator`který je adresován .

```cpp
const Type& operator*() const;
```

### <a name="return-value"></a>Návratová hodnota

Uložený objekt `Type`typu .

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

## <a name="istream_iteratoroperator-gt"></a><a name="op_arrow"></a>istream_iterator::operátor-&gt;

Vrátí hodnotu členu, pokud existuje.

```cpp
const Type* operator->() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota člena, pokud existuje.

### <a name="remarks"></a>Poznámky

`i->m`je ekvivalentní`(*i).m`

Operátor vrátí `&*this`.

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

## <a name="istream_iteratoroperator"></a><a name="op_add_add"></a>istream_iterator::operátor++

Buď zkopíruje zvýšený objekt ze vstupního datového proudu, nebo zkopíruje objekt před jeho zvýšením a vrátí kopii.

```cpp
istream_iterator<Type, CharType, Traits, Distance>& operator++();

istream_iterator<Type, CharType, Traits, Distance> operator++(int);
```

### <a name="return-value"></a>Návratová hodnota

První operátor člena vrátí odkaz na přírůstý `Type` objekt typu extrahovaného ze vstupního datového proudu a druhá členská funkce vrátí kopii objektu.

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

## <a name="istream_iteratortraits_type"></a><a name="traits_type"></a>istream_iterator::traits_type

Typ, který poskytuje typ znakových `istream_iterator`znaků typu .

```cpp
typedef Traits traits_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymem pro *vlastnosti*parametru šablony .

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

[input_iterator_tag Struct](../standard-library/input-iterator-tag-struct.md)\
[iterátor Struct](../standard-library/iterator-struct.md)\
[\<>iterátoru](../standard-library/iterator.md)\
[Bezpečnost vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Referenční příručka standardní knihovny jazyka C++](../standard-library/cpp-standard-library-reference.md)
