---
title: Třída ostreambuf_iterator | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- streambuf/std::ostreambuf_iterator
- iterator/std::ostreambuf_iterator::char_type
- iterator/std::ostreambuf_iterator::ostream_type
- iterator/std::ostreambuf_iterator::streambuf_type
- iterator/std::ostreambuf_iterator::traits_type
- iterator/std::ostreambuf_iterator::failed
dev_langs:
- C++
helpviewer_keywords:
- std::ostreambuf_iterator [C++]
- std::ostreambuf_iterator [C++], char_type
- std::ostreambuf_iterator [C++], ostream_type
- std::ostreambuf_iterator [C++], streambuf_type
- std::ostreambuf_iterator [C++], traits_type
- std::ostreambuf_iterator [C++], failed
ms.assetid: dad1e624-2f45-4e94-8887-a885e95f9071
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f71ea63fbb0fa11f470061ea5ee141d0c3b2bfb3
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="ostreambufiterator-class"></a>Třída ostreambuf_iterator

Ostreambuf_iterator – třída šablony popisuje objekt iterator výstup, který zapíše elementy po sobě jdoucích znaků do výstupního datového proudu s extrahování **operátor >>**. `ostreambuf_iterator`s lišit od těch, které [ostream_iterator – třída](../standard-library/ostream-iterator-class.md) v znaků místo obecného typu, které mají při typ objektu vkládání do výstupního datového proudu.

## <a name="syntax"></a>Syntaxe

```cpp
template <class CharType = char class Traits = char_traits <CharType>>
```

### <a name="parameters"></a>Parametry

`CharType` Typ, který představuje typ znaku pro ostreambuf_iterator. Tento argument je volitelný a výchozí hodnota je `char`.

`Traits` Typ, který představuje typ znaku pro ostreambuf_iterator. Tento argument je volitelný a výchozí hodnota je `char_traits` \< *CharType >.*

## <a name="remarks"></a>Poznámky

Třída ostreambuf_iterator musí splňovat požadavky na výstupní iterátor. Algoritmy lze zapisovat přímo do výstupní datové proudy pomocí `ostreambuf_iterator`. Třída poskytuje iterátor datového proudu na nízké úrovni, který umožňuje přístup k nezpracovanému (neformátovanému) proudu dat ve formě znaků a schopnost obejít ukládání do vyrovnávací paměti a překlady znaků spojené s iterátory datového proudu vysoké úrovně.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[ostreambuf_iterator](#ostreambuf_iterator_ostreambuf_iterator)|Vytvoří `ostreambuf_iterator` , je inicializováno zápis znaků do výstupního datového proudu.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[char_type](#char_type)|Typ, který poskytuje pro typ znak `ostreambuf_iterator`.|
|[ostream_type](#ostreambuf_iterator_ostream_type)|Typ, který poskytuje pro typ datového proudu `ostream_iterator`.|
|[streambuf_type](#streambuf_type)|Typ, který poskytuje pro typ datového proudu `ostreambuf_iterator`.|
|[traits_type](#traits_type)|Typ, který poskytuje pro typ vlastnosti znak `ostream_iterator`.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[Se nezdařilo](#failed)|Ověřuje selhání vložení do vyrovnávací paměti výstupního datového proudu.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operátor *](#op_star)|Při přesměrování operátor použít k implementaci výraz iterator výstup * `i`  =  `x`.|
|[Operator ++](#op_add_add)|Operátor přírůstku funkční, který vrátí `ostreambuf_iterator` ke stejnému objektu řešit předtím, než byla volána operace.|
|[operátor =](#op_eq)|Operátor vloží znak do přidružené vyrovnávací paměti datového proudu.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<iterator >

**Namespace:** – std

## <a name="char_type"></a>  ostreambuf_iterator::char_type

Typ, který poskytuje pro typ znak `ostreambuf_iterator`.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro parametr šablony **CharType**.

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
\* Output:
The characters written to the output stream
 by charOutBuf are: OUT.
*\
```

## <a name="failed"></a>  ostreambuf_iterator::Failed

Ověřuje selhání vložení do vyrovnávací paměti výstupního datového proudu.

```cpp
bool failed() const throw();
```

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE,** Pokud žádné vložení do výstupní vyrovnávací paměť datového proudu se nezdařilo dříve; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Členské funkce vrátí hodnotu **true** Pokud v jakékoli předchozí použití člena `operator=`, volání **subf**-> _ `sputc` vrátil **eof**.

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
\* Output:
abc are characters output individually.
No insertions failed.
*\
```

## <a name="op_star"></a>  ostreambuf_iterator::Operator *

Funkční při přesměrování operátor použít k implementaci výraz iterator výstup \* *i* = *x*.

```cpp
ostreambuf_iterator<CharType, Traits>& operator*();
```

### <a name="return-value"></a>Návratová hodnota

Objekt iterator ostreambuf.

### <a name="remarks"></a>Poznámky

Tento operátor funguje pouze ve výrazu iterator výstup \* *i* = *x* znaků výstup do vyrovnávací paměti datového proudu. Použije k iterovat ostreambuf, vrátí iterator;  **\*iter** vrátí **iter**,

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
\* Output:
Elements written to output stream:
OUT
*\
```

## <a name="op_add_add"></a>  ostreambuf_iterator::Operator ++

Operátor přírůstku funkční, který vrátí iterovat ostream – stejné znaku, který ho řešit před provedením operace byla volána.

```cpp
ostreambuf_iterator<CharType, Traits>& operator++();
ostreambuf_iterator<CharType, Traits>& operator++(int);
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na znak původně řešit nebo definované implementací objekt, který je převést na `ostreambuf_iterator` \< **CharType**, **vlastnosti**>.

### <a name="remarks"></a>Poznámky

Operátor je použít k implementaci výraz iterator výstup \* *i* = *x*.

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
\* Output:
Elements written to output stream:
OUT
*\
```

## <a name="op_eq"></a>  ostreambuf_iterator::Operator =

Operátor vloží znak do přidružené vyrovnávací paměti datového proudu.

```cpp
ostreambuf_iterator<CharType, Traits>& operator=(CharType _Char);
```

### <a name="parameters"></a>Parametry

`_Char` Znak, který má být vložen do vyrovnávací paměti datového proudu.

### <a name="return-value"></a>Návratová hodnota

Odkaz na znak vložit do vyrovnávací paměti datového proudu.

### <a name="remarks"></a>Poznámky

Operátor přiřazení použít k implementaci výraz iterator výstup \* *i* = *x* k zápisu do výstupního proudu.

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
\* Output:
Elements written to output stream:
OUT
*\
```

## <a name="ostreambuf_iterator_ostreambuf_iterator"></a>  ostreambuf_iterator::ostreambuf_iterator

Vytvoří `ostreambuf_iterator` , je inicializováno zápis znaků do výstupního datového proudu.

```cpp
ostreambuf_iterator(streambuf_type* strbuf) throw();
ostreambuf_iterator(ostream_type& Ostr) throw();
```

### <a name="parameters"></a>Parametry

`strbuf` Streambuf – výstupní objekt použitý k inicializaci ukazatele výstupní datový proud-vyrovnávací paměti.

`Ostr` Výstupní datový proud objekt použitý k inicializaci ukazatele výstupní datový proud-vyrovnávací paměti.

### <a name="remarks"></a>Poznámky

První konstruktor inicializuje ukazatel výstupní datový proud-vyrovnávací paměti s `strbuf`.

Druhý konstruktor inicializuje ukazatel výstupní datový proud-vyrovnávací paměti s `Ostr`. `rdbuf`. Uložené ukazatele nesmí být nulový ukazatel.

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
\* Output:
OUT are characters output individually.
These characters are being written to the output stream.
*\
```

## <a name="ostreambuf_iterator_ostream_type"></a>  ostreambuf_iterator::ostream_type

Typ, který poskytuje pro typ datového proudu `ostream_iterator`.

```cpp
typedef basicOstream<CharType, Traits> ostream_type;
```

### <a name="remarks"></a>Poznámky

Typ se jedná o synonymum `basicOstream` \< **CharType**, **vlastnosti**>

### <a name="example"></a>Příklad

V tématu [ostreambuf_iterator](#ostreambuf_iterator_ostreambuf_iterator) příklad toho, jak deklarace a používání `ostream_type`.

## <a name="streambuf_type"></a>  ostreambuf_iterator::streambuf_type

Typ, který poskytuje pro typ datového proudu `ostreambuf_iterator`.

```cpp
typedef basic_streambuf<CharType, Traits> streambuf_type;
```

### <a name="remarks"></a>Poznámky

Typ se jedná o synonymum `basic_streambuf` \< **CharType**, **vlastnosti**>, třídu datového proudu pro vstupně-výstupní vyrovnávací paměti, který se stane `streambuf` při specializuje na typ znak `char`.

### <a name="example"></a>Příklad

V tématu [ostreambuf_iterator](#ostreambuf_iterator_ostreambuf_iterator) příklad toho, jak deklarace a používání `streambuf_type`.

## <a name="traits_type"></a>  ostreambuf_iterator::traits_type

Typ, který poskytuje pro typ vlastnosti znak `ostream_iterator`.

```cpp
typedef Traits traits_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro parametr šablony **vlastnosti**.

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
\* Output:
The characters written to the output stream
 by charOutBuf are: OUT.
*\
```

## <a name="see-also"></a>Viz také

[\<iterator >](../standard-library/iterator.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)<br/>
