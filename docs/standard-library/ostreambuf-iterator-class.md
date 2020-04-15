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
ms.openlocfilehash: 8e9fa10888b511ad2a500f64faf610dc7dd5ba03
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373566"
---
# <a name="ostreambuf_iterator-class"></a>Třída ostreambuf_iterator

Šablona třídy ostreambuf_iterator popisuje výstupní iterátor objekt, který zapisuje po sobě jdoucí prvky znaků do výstupního datového proudu s **operátorem **extrakce>>. S `ostreambuf_iterator`se liší od těch [ostream_iterator Class](../standard-library/ostream-iterator-class.md) v tom, že znaky namísto obecného typu na typ objektu, který je vložen do výstupního datového proudu.

## <a name="syntax"></a>Syntaxe

```cpp
template <class CharType = char class Traits = char_traits <CharType>>
```

### <a name="parameters"></a>Parametry

*Typ znaku*\
Typ, který představuje typ znaku pro ostreambuf_iterator. Tento argument je volitelný a výchozí hodnota je **char**.

*Vlastnosti*\
Typ, který představuje typ znaku pro ostreambuf_iterator. Tento argument je volitelný a `char_traits` \< výchozí hodnota je *CharType>.*

## <a name="remarks"></a>Poznámky

Třída ostreambuf_iterator musí splňovat požadavky na výstupní iterátor. Algoritmy lze zapisovat přímo `ostreambuf_iterator`do výstupních datových proudů pomocí . Třída poskytuje iterátor datového proudu na nízké úrovni, který umožňuje přístup k nezpracovanému (neformátovanému) proudu dat ve formě znaků a schopnost obejít ukládání do vyrovnávací paměti a překlady znaků spojené s iterátory datového proudu vysoké úrovně.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[ostreambuf_iterator](#ostreambuf_iterator_ostreambuf_iterator)|Vytvoří, `ostreambuf_iterator` který je inicializován pro zápis znaků do výstupního datového proudu.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[char_type](#char_type)|Typ, který poskytuje typ znaku `ostreambuf_iterator`.|
|[ostream_type](#ostreambuf_iterator_ostream_type)|Typ, který poskytuje pro typ `ostream_iterator`datového proudu .|
|[streambuf_type](#streambuf_type)|Typ, který poskytuje pro typ `ostreambuf_iterator`datového proudu .|
|[traits_type](#traits_type)|Typ, který poskytuje typ znakových `ostream_iterator`znaků typu .|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[Se nezdařilo](#failed)|Ověřuje selhání vložení do vyrovnávací paměti výstupního datového proudu.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operátor*](#op_star)|Dereferencing operátor slouží k implementaci výstupního \* `i`  =  `x`výrazu iterátoru .|
|[operátor++](#op_add_add)|Operátor nefunkční přírůstek, `ostreambuf_iterator` který vrací stejný objekt, který byl adresován před voláním operace.|
|[operátor =](#op_eq)|Operátor vloží znak do přidružené vyrovnávací paměti datového proudu.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<> iterátoru

**Obor názvů:** std

## <a name="ostreambuf_iteratorchar_type"></a><a name="char_type"></a>ostreambuf_iterator::char_type

Typ, který poskytuje typ znaku `ostreambuf_iterator`.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymem pro `CharType`parametr šablony .

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

## <a name="ostreambuf_iteratorfailed"></a><a name="failed"></a>ostreambuf_iterator::selhalo

Ověřuje selhání vložení do vyrovnávací paměti výstupního datového proudu.

```cpp
bool failed() const throw();
```

### <a name="return-value"></a>Návratová hodnota

**true,** pokud žádné vložení do vyrovnávací paměti výstupního datového proudu se nezdařilo dříve; jinak **false**.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí **hodnotu true,** `operator=`pokud při jakémkoli předchozím použití `sputc` člena volání **subf**_-> **vráceno eof**.

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

## <a name="ostreambuf_iteratoroperator"></a><a name="op_star"></a>ostreambuf_iterator::operátor\*

Nefunkční dereferencing operátor slouží k implementaci výstupního \* iterátoru výraz *i* = *x*.

```cpp
ostreambuf_iterator<CharType, Traits>& operator*();
```

### <a name="return-value"></a>Návratová hodnota

Objekt iterátoru ostreambuf.

### <a name="remarks"></a>Poznámky

Tento operátor funguje pouze ve výstupním \* výrazu iterátoru *i* = *x* pro výstupní znaky do vyrovnávací paměti datového proudu. Aplikuje se na iterátor ostreambuf, vrátí iterátor; iter vrátí **iter**, ** \***

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

## <a name="ostreambuf_iteratoroperator"></a><a name="op_add_add"></a>ostreambuf_iterator::operátor++

Operátor nefunkční přírůstek, který vrací ostream iterátor na stejný znak, který byl adresován před voláním operace.

```cpp
ostreambuf_iterator<CharType, Traits>& operator++();
ostreambuf_iterator<CharType, Traits>& operator++(int);
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na znak původně adresované nebo implementací definovaný `ostreambuf_iterator` \< objekt, který je převoditelný na **CharType**, **vlastnosti**>.

### <a name="remarks"></a>Poznámky

Operátor se používá k implementaci výstupního \* výrazu iterátoru *i* = *x*.

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

## <a name="ostreambuf_iteratoroperator"></a><a name="op_eq"></a>ostreambuf_iterator::operátor=

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

Operátor přiřazení používaný k implementaci výstupního \* výrazu iterátoru *i* = *x* pro zápis do výstupního datového proudu.

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

## <a name="ostreambuf_iteratorostreambuf_iterator"></a><a name="ostreambuf_iterator_ostreambuf_iterator"></a>ostreambuf_iterator::ostreambuf_iterator

Vytvoří, `ostreambuf_iterator` který je inicializován pro zápis znaků do výstupního datového proudu.

```cpp
ostreambuf_iterator(streambuf_type* strbuf) throw();
ostreambuf_iterator(ostream_type& Ostr) throw();
```

### <a name="parameters"></a>Parametry

*strbuf (Strbuf)*\
Výstupní objekt streambuf použitý k inicializaci ukazatele vyrovnávací paměti výstupního datového proudu.

*Ostr*\
Výstupní objekt datového proudu slouží k inicializaci výstupu ukazatele vyrovnávací paměti datového proudu.

### <a name="remarks"></a>Poznámky

První konstruktor inicializuje výstupní stream-buffer ukazatel *strbuf*.

Druhý konstruktor inicializuje výstupní ukazatel vyrovnávací `Ostr`paměti datového proudu s . `rdbuf`. Uložený ukazatel nesmí být ukazatel null.

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

## <a name="ostreambuf_iteratorostream_type"></a><a name="ostreambuf_iterator_ostream_type"></a>ostreambuf_iterator::ostream_type

Typ, který poskytuje pro typ `ostream_iterator`datového proudu .

```cpp
typedef basicOstream<CharType, Traits> ostream_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymem `basicOstream` \< pro **CharType**, **Vlastnosti**>

### <a name="example"></a>Příklad

Příklad, jak deklarovat a `ostream_type`používat aplikaci , naleznete [v ostreambuf_iterator.](#ostreambuf_iterator_ostreambuf_iterator)

## <a name="ostreambuf_iteratorstreambuf_type"></a><a name="streambuf_type"></a>ostreambuf_iterator::streambuf_type

Typ, který poskytuje pro typ `ostreambuf_iterator`datového proudu .

```cpp
typedef basic_streambuf<CharType, Traits> streambuf_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymem `basic_streambuf` \< pro **CharType**, **vlastnosti**>, třída datového `streambuf` proudu pro vstupně-v., která se stane, když se specializuje na **znakový**typ char .

### <a name="example"></a>Příklad

Příklad, jak deklarovat a `streambuf_type`používat aplikaci , naleznete [v ostreambuf_iterator.](#ostreambuf_iterator_ostreambuf_iterator)

## <a name="ostreambuf_iteratortraits_type"></a><a name="traits_type"></a>ostreambuf_iterator::traits_type

Typ, který poskytuje typ znakových `ostream_iterator`znaků typu .

```cpp
typedef Traits traits_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymem pro `Traits`parametr šablony .

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

## <a name="see-also"></a>Viz také

[\<>iterátoru](../standard-library/iterator.md)\
[Bezpečnost vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Referenční příručka standardní knihovny jazyka C++](../standard-library/cpp-standard-library-reference.md)
