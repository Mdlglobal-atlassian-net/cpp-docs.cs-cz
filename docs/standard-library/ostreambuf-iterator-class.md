---
title: ostreambuf_iterator – třída | Dokumentace Microsoftu
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
ms.openlocfilehash: cec1f3fe6a3a1955b18dacd695d5a459b5550c05
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44318691"
---
# <a name="ostreambufiterator-class"></a>Třída ostreambuf_iterator

Třída šablony ostreambuf_iterator popisuje výstupní objekt iterátoru, který zapisuje po sobě jdoucích znaků prvky do výstupního toku s extrakce **operátor >>**. `ostreambuf_iterator`Se liší od těch, které [ostream_iterator – třída](../standard-library/ostream-iterator-class.md) tím, že namísto obecného typu v typu objektu vkládaného do výstupního datového proudu.

## <a name="syntax"></a>Syntaxe

```cpp
template <class CharType = char class Traits = char_traits <CharType>>
```

### <a name="parameters"></a>Parametry

*CharType*<br/>
Typ, který představuje typ znaku pro ostreambuf_iterator. Tento argument je nepovinný a výchozí hodnota je **char**.

*Osobnostní rysy*<br/>
Typ, který představuje typ znaku pro ostreambuf_iterator. Tento argument je nepovinný a výchozí hodnota je `char_traits` \< *CharType >.*

## <a name="remarks"></a>Poznámky

Třída ostreambuf_iterator musí splňovat požadavky na výstupní iterátor. Algoritmy lze zapsat přímo do výstupních toků pomocí `ostreambuf_iterator`. Třída poskytuje iterátor datového proudu na nízké úrovni, který umožňuje přístup k nezpracovanému (neformátovanému) proudu dat ve formě znaků a schopnost obejít ukládání do vyrovnávací paměti a překlady znaků spojené s iterátory datového proudu vysoké úrovně.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[ostreambuf_iterator](#ostreambuf_iterator_ostreambuf_iterator)|Vytvoří `ostreambuf_iterator` , který je inicializován pro zápis znaků do výstupního datového proudu.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[char_type](#char_type)|Typ, který poskytuje typ znaku pro `ostreambuf_iterator`.|
|[ostream_type](#ostreambuf_iterator_ostream_type)|Typ, který poskytuje typ toku pro `ostream_iterator`.|
|[streambuf_type](#streambuf_type)|Typ, který poskytuje typ toku pro `ostreambuf_iterator`.|
|[traits_type](#traits_type)|Typ, který poskytuje typ vlastností `ostream_iterator`.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[Se nezdařilo](#failed)|Ověřuje selhání vložení do vyrovnávací paměti výstupního datového proudu.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[Operator *](#op_star)|Operátor přesměrování používaný k implementaci výrazu výstupního iterátoru \* `i`  =  `x`.|
|[Operator ++](#op_add_add)|Nefunkční operátor přírůstku, který vrátí `ostreambuf_iterator` na stejný objekt, který adresoval před voláním operace.|
|[operátor =](#op_eq)|Operátor vloží znak do přidružené vyrovnávací paměti datového proudu.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<iterátor >

**Namespace:** std

## <a name="char_type"></a>  ostreambuf_iterator::char_type

Typ, který poskytuje typ znaku pro `ostreambuf_iterator`.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro parametr šablony `CharType`.

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

## <a name="failed"></a>  ostreambuf_iterator::Failed

Ověřuje selhání vložení do vyrovnávací paměti výstupního datového proudu.

```cpp
bool failed() const throw();
```

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud bez vložení do výstupní mezipaměti datového proudu se nezdařilo dříve; jinak vrátí hodnotu **false**.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí **true** if, v jakékoli předchozí použití členu `operator=`, volání **subf**-> _ `sputc` vrátil **eof**.

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

## <a name="op_star"></a>  ostreambuf_iterator::Operator\*

Nefunkční operátor přesměrování používaný k implementaci výrazu výstupního iterátoru \* *můžu* = *x*.

```cpp
ostreambuf_iterator<CharType, Traits>& operator*();
```

### <a name="return-value"></a>Návratová hodnota

Objekt ostreambuf iterátoru.

### <a name="remarks"></a>Poznámky

Tento operátor funguje pouze ve výrazu výstupního iterátoru \* *můžu* = *x* na výstupní znaky do vyrovnávací paměti datového proudu. Použít na iterátor ostreambuf, vrátí iterátor;  **\*iter** vrátí **iter**,

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

## <a name="op_add_add"></a>  ostreambuf_iterator::Operator ++

Nefunkční operátor přírůstku, která vrací iterátor ostream stejným znakem, který adresoval před provedením operace byla volána.

```cpp
ostreambuf_iterator<CharType, Traits>& operator++();
ostreambuf_iterator<CharType, Traits>& operator++(int);
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na znak, který původně zákazníky a vyřešené nebo definované implementací objektu, který lze převést na `ostreambuf_iterator` \< **CharType**, **osobnostní rysy**>.

### <a name="remarks"></a>Poznámky

Operátor, který se používá k implementaci výrazu výstupního iterátoru \* *můžu* = *x*.

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

## <a name="op_eq"></a>  ostreambuf_iterator::Operator =

Operátor vloží znak do přidružené vyrovnávací paměti datového proudu.

```cpp
ostreambuf_iterator<CharType, Traits>& operator=(CharType _Char);
```

### <a name="parameters"></a>Parametry

*_Char*<br/>
Znak, který má být vložen do vyrovnávací paměti datového proudu.

### <a name="return-value"></a>Návratová hodnota

Odkaz na znak, který vloží do vyrovnávací paměti datového proudu.

### <a name="remarks"></a>Poznámky

Operátor přiřazení používaný k implementaci výrazu výstupního iterátoru \* *můžu* = *x* pro zápis do výstupního proudu.

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

## <a name="ostreambuf_iterator_ostreambuf_iterator"></a>  ostreambuf_iterator::ostreambuf_iterator

Vytvoří `ostreambuf_iterator` , který je inicializován pro zápis znaků do výstupního datového proudu.

```cpp
ostreambuf_iterator(streambuf_type* strbuf) throw();
ostreambuf_iterator(ostream_type& Ostr) throw();
```

### <a name="parameters"></a>Parametry

*strbuf*<br/>
Streambuf – výstupní objekt použitý k inicializaci ukazatele výstupní vyrovnávací paměť datového proudu.

*Ostr*<br/>
Výstupní datový proud objekt použitý k inicializaci ukazatele výstupní vyrovnávací paměť datového proudu.

### <a name="remarks"></a>Poznámky

První konstruktor inicializuje ukazatele výstupní vyrovnávací paměť datového proudu s *strbuf*.

Druhý konstruktor inicializuje ukazatele výstupní vyrovnávací paměť datového proudu s `Ostr`. `rdbuf`. Uložený ukazatel nesmí být nulový ukazatel.

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

## <a name="ostreambuf_iterator_ostream_type"></a>  ostreambuf_iterator::ostream_type

Typ, který poskytuje typ toku pro `ostream_iterator`.

```cpp
typedef basicOstream<CharType, Traits> ostream_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro `basicOstream` \< **CharType**, **osobnostní rysy**>

### <a name="example"></a>Příklad

Zobrazit [ostreambuf_iterator](#ostreambuf_iterator_ostreambuf_iterator) příklad toho, jak deklarace a používání `ostream_type`.

## <a name="streambuf_type"></a>  ostreambuf_iterator::streambuf_type

Typ, který poskytuje typ toku pro `ostreambuf_iterator`.

```cpp
typedef basic_streambuf<CharType, Traits> streambuf_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro `basic_streambuf` \< **CharType**, **osobnostní rysy**>, třída datového proudu pro vstupně-výstupní vyrovnávací paměti, který se stane `streambuf` při zaměřena na typ znaku **char**.

### <a name="example"></a>Příklad

Zobrazit [ostreambuf_iterator](#ostreambuf_iterator_ostreambuf_iterator) příklad toho, jak deklarace a používání `streambuf_type`.

## <a name="traits_type"></a>  ostreambuf_iterator::traits_type

Typ, který poskytuje typ vlastností `ostream_iterator`.

```cpp
typedef Traits traits_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro parametr šablony `Traits`.

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

[\<iterátor >](../standard-library/iterator.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)<br/>
