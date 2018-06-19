---
title: istream_iterator – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- iterator/std::istream_iterator
- iterator/std::istream_iterator::char_type
- iterator/std::istream_iterator::istream_type
- iterator/std::istream_iterator::traits_type
dev_langs:
- C++
helpviewer_keywords:
- std::istream_iterator [C++]
- std::istream_iterator [C++], char_type
- std::istream_iterator [C++], istream_type
- std::istream_iterator [C++], traits_type
ms.assetid: fb52a8cd-7f71-48d1-b73e-4b064e2a8d16
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 74c62c1d6d80f21054f03f78e0151c2cddf00e2c
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33859222"
---
# <a name="istreamiterator-class"></a>istream_iterator – třída

Popisuje objekt vstupního iterátoru. Extrahuje objekty třídy `Type` ze vstupního datového proudu, který přistupuje prostřednictvím objektu je úložiště typu `pointer` k `basic_istream` <  `CharType`, `Traits`>.

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

`Type` Typ objektu extrahovaným ze vstupního datového proudu.

`CharType` Typ, který představuje typ znaku pro `istream_iterator`. Tento argument je volitelný a výchozí hodnota je `char`.

`Traits` Typ, který představuje typ znaku pro `istream_iterator`. Tento argument je volitelný a výchozí hodnota je `char_traits` <  `CharType`>.

`Distance` Integrální typ, který představuje typ rozdíl pro podepsané A `istream_iterator`. Tento argument je volitelný a výchozí hodnota je `ptrdiff_t`.

Po vytváření nebo zvyšování objekt istream_iterator – třída pomocí nenulový uložené ukazatele, objekt pokusí o extrahování a uložit objekt typu `Type` z přidružených vstupního datového proudu. Pokud se extrakce nezdaří, objekt nahradí uložený ukazatel ukazatelem s hodnotou null a vytvoří tak indikátor ukončení sekvence.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[istream_iterator](#istream_iterator)|Vytvoří iterátor end datového proudu jako výchozí `istream_iterator` nebo `istream_iterator` inicializována tak, aby typ datového proudu iteraci, ze které čte.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[char_type](#char_type)|Typ, který poskytuje pro typ znak `istream_iterator`.|
|[istream_type](#istream_type)|Typ, který poskytuje pro typ datového proudu `istream_iterator`.|
|[traits_type](#traits_type)|Typ, který poskytuje pro typ vlastnosti znak `istream_iterator`.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operátor *](#op_star)|Při přesměrování operátor vrací objekt uložené typu `Type` řešené pomocí `istream_iterator`.|
|[-> – operátor](#op_arrow)|Vrátí hodnotu členu, pokud existuje.|
|[Operator ++](#op_add_add)|Buď zkopíruje zvýšený objekt ze vstupního datového proudu, nebo zkopíruje objekt před jeho zvýšením a vrátí kopii.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<iterator >

**Namespace:** – std

## <a name="char_type"></a>  istream_iterator::char_type

Typ, který poskytuje pro typ znak `istream_iterator`.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro parametr šablony **Chartype**.

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

## <a name="istream_iterator"></a>  istream_iterator::istream_iterator

Vytvoří iterátor end datového proudu jako výchozí `istream_iterator` nebo `istream_iterator` inicializována tak, aby typ datového proudu iteraci, ze které čte.

```cpp
istream_iterator();

istream_iterator(istream_type& _Istr);
```

### <a name="parameters"></a>Parametry

`_Istr` Vstupní datový proud čtení použijte k chybě při inicializaci `istream_iterator`.

### <a name="remarks"></a>Poznámky

První konstruktor inicializuje ukazatel vstupního datového proudu s ukazatele null a vytvoří iterovat end datového proudu. Druhý konstruktor inicializuje ukazatel vstupního datového proudu s *& _Istr*, pokusí se extrahovat a uložit objekt typu **typu**.

Iterator end datového proudu můžete použít k testování jestli `istream_iterator` byl dosažen konec datového proudu.

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

## <a name="istream_type"></a>  istream_iterator::istream_type

Typ, který poskytuje pro typ datového proudu `istream_iterator`.

```cpp
typedef basic_istream<CharType, Traits> istream_type;
```

### <a name="remarks"></a>Poznámky

Typ se jedná o synonymum `basic_istream` \< **CharType**, **vlastnosti**>.

### <a name="example"></a>Příklad

V tématu [istream_iterator](#istream_iterator) příklad toho, jak deklarace a používání `istream_type`.

## <a name="op_star"></a>  istream_iterator::Operator *

Při přesměrování operátor vrací objekt uložené typu **typ** řešené pomocí `istream_iterator`.

```cpp
const Type& operator*() const;
```

### <a name="return-value"></a>Návratová hodnota

Uložené objektu typu **typu**.

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

## <a name="op_arrow"></a>  istream_iterator::Operator-&gt;

Vrátí hodnotu členu, pokud existuje.

```cpp
const Type* operator->() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota člena, pokud existuje.

### <a name="remarks"></a>Poznámky

*i* -> je ekvivalentní (\* *i*). *m*

Vrátí operátor  **& \* \*to**.

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

## <a name="op_add_add"></a>  istream_iterator::Operator ++

Buď zkopíruje zvýšený objekt ze vstupního datového proudu, nebo zkopíruje objekt před jeho zvýšením a vrátí kopii.

```cpp
istream_iterator<Type, CharType, Traits, Distance>& operator++();

istream_iterator<Type, CharType, Traits, Distance> operator++(int);
```

### <a name="return-value"></a>Návratová hodnota

První člen operátor vrátí odkaz na objekt zvýšena typu **typ** extrahovaných ze vstupního datového proudu a druhý funkce vrátí člen kopii objektu.

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

## <a name="traits_type"></a>  istream_iterator::traits_type

Typ, který poskytuje pro typ vlastnosti znak `istream_iterator`.

```cpp
typedef Traits traits_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro parametr šablony **vlastnosti**.

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

[input_iterator_tag – struktura](../standard-library/input-iterator-tag-struct.md)<br/>
[iterator – struktura](../standard-library/iterator-struct.md)<br/>
[\<iterator >](../standard-library/iterator.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)<br/>
