---
title: Třída ostreambuf_iterator
ms.date: 11/04/2016
f1_keywords:
- streambuf/std::ostreambuf_iterator
- iterator/std::ostreambuf_iterator::char_type
- iterator/std::ostreambuf_iterator::ostream_type
- iterator/std::ostreambuf_iterator::streambuf_type
- iterator/std::ostreambuf_iterator::traits_type
- iterator/std::ostreambuf_iterator::failed
helpviewer_keywords:
- std::ostreambuf_iterator [C++]
- std::ostreambuf_iterator [C++], char_type
- std::ostreambuf_iterator [C++], ostream_type
- std::ostreambuf_iterator [C++], streambuf_type
- std::ostreambuf_iterator [C++], traits_type
- std::ostreambuf_iterator [C++], failed
ms.assetid: dad1e624-2f45-4e94-8887-a885e95f9071
ms.openlocfilehash: 815647deb7c11f4d7be5650e0ec2e635338551ad
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68448181"
---
# <a name="ostreambufiterator-class"></a>Třída ostreambuf_iterator

Třída šablony ostreambuf_iterator popisuje výstupní objekt iterátoru, který zapisuje do výstupního datového proudu prvky po sobě jdoucí znak, a to pomocí operátoru extrakce **> >** . S se liší od těch [třídy ostream_iterator](../standard-library/ostream-iterator-class.md) , ve které mají znaky namísto obecného typu na typ objektu, který je vložen do výstupního datového proudu. `ostreambuf_iterator`

## <a name="syntax"></a>Syntaxe

```cpp
template <class CharType = char class Traits = char_traits <CharType>>
```

### <a name="parameters"></a>Parametry

*CharType*\
Typ, který představuje typ znaku pro ostreambuf_iterator. Tento argument je nepovinný a výchozí hodnota je **char**.

*Traits*\
Typ, který představuje typ znaku pro ostreambuf_iterator. Tento argument je nepovinný a výchozí hodnota `char_traits` je \< *CharType >.*

## <a name="remarks"></a>Poznámky

Třída ostreambuf_iterator musí splňovat požadavky na výstupní iterátor. Algoritmy lze zapisovat přímo do výstupních datových proudů `ostreambuf_iterator`pomocí. Třída poskytuje iterátor datového proudu na nízké úrovni, který umožňuje přístup k nezpracovanému (neformátovanému) proudu dat ve formě znaků a schopnost obejít ukládání do vyrovnávací paměti a překlady znaků spojené s iterátory datového proudu vysoké úrovně.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[ostreambuf_iterator](#ostreambuf_iterator_ostreambuf_iterator)|Vytvoří inicializaci, která je inicializována pro zápis znaků do výstupního datového proudu. `ostreambuf_iterator`|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[char_type](#char_type)|Typ, který poskytuje typ `ostreambuf_iterator`znaku pro.|
|[ostream_type](#ostreambuf_iterator_ostream_type)|Typ, který poskytuje typ `ostream_iterator`datového proudu.|
|[streambuf_type](#streambuf_type)|Typ, který poskytuje typ `ostreambuf_iterator`datového proudu.|
|[traits_type](#traits_type)|Typ, který poskytuje znaky typu `ostream_iterator`pro.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[Nepovedlo se](#failed)|Ověřuje selhání vložení do vyrovnávací paměti výstupního datového proudu.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[podnikatel](#op_star)|Operátor přesměrování \* používaný k implementaci výrazu `i`  =  `x`výstupního iterátoru.|
|[operator + + – operátor](#op_add_add)|Nefunkční operátor přírůstku, který vrací `ostreambuf_iterator` na stejný objekt, který byl vyřešen před voláním operace.|
|[operátor =](#op_eq)|Operátor vloží znak do přidružené vyrovnávací paměti datového proudu.|

## <a name="requirements"></a>Požadavky

**Hlavička:** \<iterátor >

**Obor názvů:** std

## <a name="char_type"></a>ostreambuf_iterator::char_type

Typ, který poskytuje typ `ostreambuf_iterator`znaku pro.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro parametr `CharType`šablony.

### <a name="example"></a>Příklad

```cpp
// ostreambuf_iterator_char_type.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   typedef ostreambuf_iterator<char>::char_type CHT1;
   typedef ostreambuf_iterator<char>::traits_type CHTR1;

   // ostreambuf_iterator for stream cout
   // with new line delimiter:
    ostreambuf_iterator< CHT1, CHTR1> charOutBuf ( cout );

   // Standard iterator interface for writing
   // elements to the output streambuf:
   cout << "The characters written to the output stream\n"
        << " by charOutBuf are: ";
*charOutBuf = 'O';
   charOutBuf++;
*charOutBuf = 'U';
   charOutBuf++;
*charOutBuf = 'T';
   charOutBuf++;
   cout << "." << endl;
}
/* Output:
The characters written to the output stream
by charOutBuf are: OUT.
*/
```

## <a name="failed"></a>ostreambuf_iterator:: failed

Ověřuje selhání vložení do vyrovnávací paměti výstupního datového proudu.

```cpp
bool failed() const throw();
```

### <a name="return-value"></a>Návratová hodnota

**true** , pokud žádné vložení do vyrovnávací paměti výstupního datového proudu neproběhlo dříve; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí **hodnotu true** , pokud v jakémkoli předchozím použití člena `operator=`volání **subf**_-> `sputc` vrátilo **EOF**.

### <a name="example"></a>Příklad

```cpp
// ostreambuf_iterator_failed.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   // ostreambuf_iterator for stream cout
   ostreambuf_iterator<char> charOut ( cout );

*charOut = 'a';
   charOut ++;
*charOut  = 'b';
   charOut ++;
*charOut = 'c';
   cout << " are characters output individually." << endl;

   bool b1 = charOut.failed ( );
   if (b1)
       cout << "At least one insertion failed." << endl;
   else
       cout << "No insertions failed." << endl;
}
/* Output:
abc are characters output individually.
No insertions failed.
*/
```

## <a name="op_star"></a>ostreambuf_iterator:: operator\*

Nefunkční operátor přesměrování používaný k \* implementaci výrazu výstupního iterátoru *i* = *x*.

```cpp
ostreambuf_iterator<CharType, Traits>& operator*();
```

### <a name="return-value"></a>Návratová hodnota

Objekt iterátoru ostreambuf

### <a name="remarks"></a>Poznámky

Tento operátor funguje pouze \* ve výrazu výstupního iterátoru *i* = *x* pro výstup znaků do vyrovnávací paměti datového proudu. Aplikuje se na iterátor ostreambuf, který vrátí iterátor; ITER vrátí **ITER**,  **\***

### <a name="example"></a>Příklad

```cpp
// ostreambuf_iterator_op_deref.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   // ostreambuf_iterator for stream cout
   // with new line delimiter
   ostreambuf_iterator<char> charOutBuf ( cout );

   // Standard iterator interface for writing
   // elements to the output stream
   cout << "Elements written to output stream:" << endl;
*charOutBuf = 'O';
   charOutBuf++;   // no effect on iterator position
*charOutBuf = 'U';
*charOutBuf = 'T';
}
/* Output:
Elements written to output stream:
OUT
*/
```

## <a name="op_add_add"></a>ostreambuf_iterator:: operator + +

Nefunkční operátor přírůstku, který vrací iterátor ostream ke stejnému znaku, který byl vyřešen před voláním operace.

```cpp
ostreambuf_iterator<CharType, Traits>& operator++();
ostreambuf_iterator<CharType, Traits>& operator++(int);
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na znak, který byl původně adresován nebo uživatelsky definovanému objektu, který lze převést `ostreambuf_iterator` \< na **CharType**, **vlastnosti**>.

### <a name="remarks"></a>Poznámky

Operátor slouží k \* implementaci výrazu výstupního iterátoru *i* = *x*.

### <a name="example"></a>Příklad

```cpp
// ostreambuf_iterator_op_incr.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   // ostreambuf_iterator for stream cout
   // with new line delimiter
   ostreambuf_iterator<char> charOutBuf ( cout );

   // Standard iterator interface for writing
   // elements to the output stream
   cout << "Elements written to output stream:" << endl;
*charOutBuf = 'O';
   charOutBuf++;      // No effect on iterator position
*charOutBuf = 'U';
*charOutBuf = 'T';
}
/* Output:
Elements written to output stream:
OUT
*/
```

## <a name="op_eq"></a>ostreambuf_iterator:: operator =

Operátor vloží znak do přidružené vyrovnávací paměti datového proudu.

```cpp
ostreambuf_iterator<CharType, Traits>& operator=(CharType _Char);
```

### <a name="parameters"></a>Parametry

*_Char*\
Znak, který má být vložen do vyrovnávací paměti datového proudu.

### <a name="return-value"></a>Návratová hodnota

Odkaz na znak vložený do vyrovnávací paměti datového proudu.

### <a name="remarks"></a>Poznámky

Operátor přiřazení používaný k \* implementaci výrazu výstupního iterátoru *i* = *x* pro zápis do výstupního datového proudu.

### <a name="example"></a>Příklad

```cpp
// ostreambuf_iterator_op_assign.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   // ostreambuf_iterator for stream cout
   // with new line delimiter
   ostreambuf_iterator<char> charOutBuf ( cout );

   // Standard iterator interface for writing
   // elements to the output stream
   cout << "Elements written to output stream:" << endl;
*charOutBuf = 'O';
   charOutBuf++;      // No effect on iterator position
*charOutBuf = 'U';
*charOutBuf = 'T';
}
/* Output:
Elements written to output stream:
OUT
*/
```

## <a name="ostreambuf_iterator_ostreambuf_iterator"></a>ostreambuf_iterator::ostreambuf_iterator

Vytvoří inicializaci, která je inicializována pro zápis znaků do výstupního datového proudu. `ostreambuf_iterator`

```cpp
ostreambuf_iterator(streambuf_type* strbuf) throw();
ostreambuf_iterator(ostream_type& Ostr) throw();
```

### <a name="parameters"></a>Parametry

*strbuf*\
Výstupní objekt streambuf, který slouží k inicializaci výstupního datového proudu – ukazatel vyrovnávací paměti.

*Ostr*\
Výstupní datový proud, který se používá k inicializaci výstupního datového proudu – ukazatel vyrovnávací paměti.

### <a name="remarks"></a>Poznámky

První konstruktor inicializuje výstupní datový proud ukazatele vyrovnávací paměti pomocí *strbuf*.

Druhý konstruktor inicializuje výstupní datový proud s `Ostr`ukazatelem vyrovnávací paměti. `rdbuf`. Uložený ukazatel nesmí být ukazatel s hodnotou null.

### <a name="example"></a>Příklad

```cpp
// ostreambuf_iteratorOstreambuf_iterator.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   // ostreambuf_iterator for stream cout
   ostreambuf_iterator<char> charOut ( cout );

*charOut = 'O';
   charOut ++;
*charOut  = 'U';
   charOut ++;
*charOut = 'T';
   cout << " are characters output individually." << endl;

   ostreambuf_iterator<char> strOut ( cout );
   string str = "These characters are being written to the output stream.\n ";
   copy ( str.begin ( ), str. end ( ), strOut );
}
/* Output:
OUT are characters output individually.
These characters are being written to the output stream.
*/
```

## <a name="ostreambuf_iterator_ostream_type"></a>ostreambuf_iterator::ostream_type

Typ, který poskytuje typ `ostream_iterator`datového proudu.

```cpp
typedef basicOstream<CharType, Traits> ostream_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum `basicOstream` pro \< **CharType**, **vlastnosti** .>

### <a name="example"></a>Příklad

Příklad [](#ostreambuf_iterator_ostreambuf_iterator) , jak deklarovat a používat `ostream_type`, naleznete v tématu ostreambuf_iterator.

## <a name="streambuf_type"></a>ostreambuf_iterator::streambuf_type

Typ, který poskytuje typ `ostreambuf_iterator`datového proudu.

```cpp
typedef basic_streambuf<CharType, Traits> streambuf_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum `basic_streambuf` pro  \< CharType, **vlastnosti**>, třídu Stream pro vyrovnávací paměti I/O, které se stávají `streambuf` při specializovaném na znak typu **char**.

### <a name="example"></a>Příklad

Příklad [](#ostreambuf_iterator_ostreambuf_iterator) , jak deklarovat a používat `streambuf_type`, naleznete v tématu ostreambuf_iterator.

## <a name="traits_type"></a>ostreambuf_iterator::traits_type

Typ, který poskytuje znaky typu `ostream_iterator`pro.

```cpp
typedef Traits traits_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro parametr `Traits`šablony.

### <a name="example"></a>Příklad

```cpp
// ostreambuf_iterator_traits_type.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   typedef ostreambuf_iterator<char>::char_type CHT1;
   typedef ostreambuf_iterator<char>::traits_type CHTR1;

   // ostreambuf_iterator for stream cout
   // with new line delimiter:
    ostreambuf_iterator< CHT1, CHTR1> charOutBuf ( cout );

   // Standard iterator interface for writing
   // elements to the output streambuf:
   cout << "The characters written to the output stream\n"
        << " by charOutBuf are: ";
*charOutBuf = 'O';
   charOutBuf++;
*charOutBuf = 'U';
   charOutBuf++;
*charOutBuf = 'T';
   charOutBuf++;
   cout << "." << endl;
}
/* Output:
The characters written to the output stream
by charOutBuf are: OUT.
*/
```

## <a name="see-also"></a>Viz také:

[\<iterátor >](../standard-library/iterator.md)\
[Bezpečnost vlákna ve C++ standardní knihovně](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)
