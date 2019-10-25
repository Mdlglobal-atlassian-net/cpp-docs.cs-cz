---
title: '&lt;operátory&gt; bitset'
ms.date: 11/04/2016
f1_keywords:
- bitset/std::operator&amp;
- bitset/std::operator&gt;&gt;
- bitset/std::operator&lt;&lt;
- bitset/std::operator^
- bitset/std::operator|
ms.assetid: 84fe6a13-6f6e-4cdc-bf8f-6f65ab1134d4
helpviewer_keywords:
- std::operator&amp; (bitset)
- std::operator&gt;&gt; (bitset)
- std::operator&lt;&lt; (bitset)
ms.openlocfilehash: cd1dfc035fde06c4be0f90e1bd11b231d64ab811
ms.sourcegitcommit: 4b0928a1a497648d0d327579c8262f25ed20d02e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2019
ms.locfileid: "72890131"
---
# <a name="ltbitsetgt-operators"></a>&lt;operátory&gt; bitset

## <a name="op_amp"></a>operátor&amp;

Provede bitovou `AND` mezi dvěma bitsetsy.

```cpp
template <size_t size>
bitset<size>
operator&(
    const bitset<size>& left,
    const bitset<size>& right);
```

### <a name="parameters"></a>Parametry

*levý* \
První ze dvou Bitsets, jejichž příslušné prvky mají být kombinovány s bitovým `AND`.

*pravé* \
Druhý ze dvou valarrays, jejichž příslušné prvky mají být kombinovány s bitovým `AND`.

### <a name="return-value"></a>Návratová hodnota

Bitset, jehož prvky jsou výsledkem provádění operace `AND` na odpovídajících prvcích *vlevo* a *vpravo*.

### <a name="example"></a>Příklad

```cpp
// bitset_and.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>
#include <string>

using namespace std;

int main()
{
   bitset<4> b1 ( string("0101") );
   bitset<4> b2 ( string("0011") );
   bitset<4> b3 = b1 & b2;
   cout << "bitset 1: " << b1 << endl;
   cout << "bitset 2: " << b2 << endl;
   cout << "bitset 3: " << b3 << endl;
}
```

```Output
bitset 1: 0101
bitset 2: 0011
bitset 3: 0001
```

## <a name="op_lt_lt"></a>operátor&lt;&lt;

Vloží textovou reprezentaci bitové sekvence do výstupního datového proudu.

```
template <class CharType, class Traits, size_t N>
basic_ostream<CharType, Traits>& operator<<(
    basic_ostream<CharType, Traits>& ostr,
    const bitset<N>& right);
```

### <a name="parameters"></a>Parametry

*pravé* \
Objekt typu **bitset\<N >** , který má být vložen do výstupního datového proudu jako řetězec.

### <a name="return-value"></a>Návratová hodnota

Textová reprezentace bitové sekvence v `ostr`.

### <a name="remarks"></a>Poznámky

Funkce šablony přetěžuje `operator<<`, což umožňuje, aby bylo zapsáno bitset bez jeho první konverze na řetězec. Funkce šablony efektivně provede:

`ostr << right.`[to_string](bitset-class.md)`<CharType, Traits, allocator<CharType>>()`

### <a name="example"></a>Příklad

```cpp
// bitset_op_insert.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>
#include <string>

int main( )
{
   using namespace std;

   bitset<5> b1 ( 9 );

   // bitset inserted into output stream directly
   cout << "The ordered set of bits in the bitset<5> b1(9)"
        << "\n can be output with the overloaded << as: ( "
        << b1 << " )" << endl;

   // Compare converting bitset to a string before
   // inserting it into the output steam
   string s1;
   s1 =  b1.template to_string<char,
      char_traits<char>, allocator<char> >( );
   cout << "The string returned from the bitset b1"
        << "\n by the member function to_string( ) is: "
        << s1 << "." << endl;
}
```

## <a name="op_gt_gt"></a>operátor&gt;&gt;

Přečte řetězec bitových znaků do bitset.

```
template <class CharType, class Traits, size_t Bits>
basic_istream<CharType, Traits>& operator>> (
    basic_istream<CharType, Traits>& i_str,
    bitset<N>& right);
```

### <a name="parameters"></a>Parametry

*i_str*\
Řetězec, který je zadán do vstupního datového proudu, který má být vložen do bitset.

*pravé* \
Bitset, který přijímá bity ze vstupního datového proudu.

### <a name="return-value"></a>Návratová hodnota

Funkce šablony vrátí řetězec *i_str*.

### <a name="remarks"></a>Poznámky

Funkce šablony přetěžuje `operator>>` pro uložení *v bitset hodnotu* `bitset(str)`, kde `str` je objekt typu [basic_string](basic-string-class.md)`< CharType, Traits, allocator< CharType > >&` extrakce z *i_str*.

Funkce šablony extrahuje prvky z *i_str* a vloží je do bitset, dokud:

- Všechny bitové prvky byly extrahovány ze vstupního datového proudu a uloženy do bitset.

- Bitset se naplní bity ze vstupního streamu.

- Byl zjištěn vstupní element, který není 0 ani 1.

### <a name="example"></a>Příklad

```cpp
#include <bitset>
#include <iostream>
#include <string>

using namespace std;
int main()
{

   bitset<5> b1;
   cout << "Enter string of (0 or 1) bits for input into bitset<5>.\n"
        << "Try bit string of length less than or equal to 5,\n"
        << " (for example: 10110): ";
   cin >>  b1;

   cout << "The ordered set of bits entered from the "
        << "keyboard\n has been input into bitset<5> b1 as: ( "
        << b1 << " )" << endl;

   // Truncation due to longer string of bits than length of bitset
   bitset<2> b3;
   cout << "Enter string of bits (0 or 1) for input into bitset<2>.\n"
        << " Try bit string of length greater than 2,\n"
        << " (for example: 1011): ";
   cin >>  b3;

   cout << "The ordered set of bits entered from the "
        << "keyboard\n has been input into bitset<2> b3 as: ( "
        << b3 << " )" << endl;

   // Flushing the input stream
   char buf[100];
   cin.getline(&buf[0], 99);

   // Truncation with non-bit value
   bitset<5> b2;
   cout << "Enter a string for input into  bitset<5>.\n"
        << " that contains a character than is NOT a 0 or a 1,\n "
        << " (for example: 10k01): ";
   cin >>  b2;

   cout << "The string entered from the keyboard\n"
        << " has been input into bitset<5> b2 as: ( "
        << b2 << " )" << endl;
}
```

## <a name="op_xor"></a>operátor ^

Provede bitovou `EXCLUSIVE-OR` mezi dvěma bitsetsy.

```cpp
template <size_t size>
bitset<size>
operator^(
    const bitset<size>& left,
    const bitset<size>& right);
```

### <a name="parameters"></a>Parametry

*levý* \
První ze dvou Bitsets, jejichž příslušné prvky mají být kombinovány s bitovým `EXCLUSIVE-OR`.

*pravé* \
Druhý ze dvou valarrays, jejichž příslušné prvky mají být kombinovány s bitovým `EXCLUSIVE-OR`.

### <a name="return-value"></a>Návratová hodnota

Bitset, jehož prvky jsou výsledkem provádění operace `EXCLUSIVE-OR` na odpovídajících prvcích *vlevo* a *vpravo*.

### <a name="example"></a>Příklad

```cpp
// bitset_xor.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>
#include <string>

using namespace std;

int main()
{
   bitset<4> b1 ( string("0101") );
   bitset<4> b2 ( string("0011") );
   bitset<4> b3 = b1 ^ b2;
   cout << "bitset 1: " << b1 << endl;
   cout << "bitset 2: " << b2 << endl;
   cout << "bitset 3: " << b3 << endl;
}
```

```Output
bitset 1: 0101
bitset 2: 0011
bitset 3: 0110
```

## <a name="op_or"></a>podnikatel&#124;

Provede bitovou `OR` mezi dvěma bitsetsy.

```cpp
template <size_t size>
bitset<size>
operator|(
    const bitset<size>& left,
    const bitset<size>& right);
```

### <a name="parameters"></a>Parametry

*levý* \
První ze dvou Bitsets, jejichž příslušné prvky mají být kombinovány s bitovým `OR`.

*pravé* \
Druhý ze dvou valarrays, jejichž příslušné prvky mají být kombinovány s bitovým `OR`.

### <a name="return-value"></a>Návratová hodnota

Bitset, jehož prvky jsou výsledkem provádění operace `OR` na odpovídajících prvcích *vlevo* a *vpravo*.

### <a name="example"></a>Příklad

```cpp
// bitset_or.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>
#include <string>

using namespace std;

int main()
{
   bitset<4> b1 ( string("0101") );
   bitset<4> b2 ( string("0011") );
   bitset<4> b3 = b1 | b2;
   cout << "bitset 1: " << b1 << endl;
   cout << "bitset 2: " << b2 << endl;
   cout << "bitset 3: " << b3 << endl;
}
```

```Output
bitset 1: 0101
bitset 2: 0011
bitset 3: 0111
```
