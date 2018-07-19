---
title: '&lt;bitset –&gt; operátory | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- bitset/std::operator&amp;
- bitset/std::operator&gt;&gt;
- bitset/std::operator&lt;&lt;
- bitset/std::operator^
- bitset/std::operator|
dev_langs:
- C++
ms.assetid: 84fe6a13-6f6e-4cdc-bf8f-6f65ab1134d4
author: corob-msft
ms.author: corob
helpviewer_keywords:
- std::operator&amp; (bitset)
- std::operator&gt;&gt; (bitset)
- std::operator&lt;&lt; (bitset)
ms.workload:
- cplusplus
ms.openlocfilehash: 7d01a9ad5ef0b5cc3198231ae2b361e04856449f
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38955017"
---
# <a name="ltbitsetgt-operators"></a>&lt;bitset –&gt; operátory

||||
|-|-|-|
|[– Operátor&amp;](#op_amp)|[– Operátor&gt;&gt;](#op_gt_gt)|[– Operátor&lt;&lt;](#op_lt_lt)|
|[operátor ^](#op_xor)|[– operátor|](#op_or)|

## <a name="op_amp"></a>  – Operátor&amp;

Provádí logické bitové `AND` mezi dvěma bitsets.

```cpp
template <size_t size>
bitset<size>
operator&(
    const bitset<size>& left,
    const bitset<size>& right);
```

### <a name="parameters"></a>Parametry

*levé* první dva bitsets jehož příslušné prvky mají být kombinované pomocí bitového `AND`.

*správné* druhé dvě valarrays jehož příslušné prvky mají být kombinované pomocí bitového `AND`.

### <a name="return-value"></a>Návratová hodnota

Bitset –, jehož prvky jsou výsledkem provádění `AND` operace na odpovídající prvky *levé* a *správné*.

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

## <a name="op_lt_lt"></a>  – Operátor&lt;&lt;

Vloží textové znázornění sekvence bit do výstupního datového proudu.

```

template <class CharType, class Traits, size_t N>
basic_ostream<CharType, Traits>& operator<<(
    basic_ostream<CharType, Traits>& ostr,
    const bitset<N>& right);
```

### <a name="parameters"></a>Parametry

*správné* objekt typu **bitset –\<N >** , který má být vložen do výstupního datového proudu jako řetězec.

### <a name="return-value"></a>Návratová hodnota

Textové vyjádření pořadí bitů v `ostr`.

### <a name="remarks"></a>Poznámky

Funkce přetížení šablon `operator<<`, což bitset – Chcete-li možné zapsat bez první převodu na řetězec. Funkce šablony efektivně provede:

**ostr** << _ *vpravo*. [to_string](bitset-class.md) < **CharType**, **osobnostní rysy**, **alokátoru** \< **CharType**>>)

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

## <a name="op_gt_gt"></a>  – Operátor&gt;&gt;

Načte řetězec rozšířené znaky do bitset –.

```

template <class CharType, class Traits, size_t Bits>
basic_istream<CharType, Traits>& operator>> (
    basic_istream<CharType, Traits>&
_Istr,
    bitset<N>&
    right);
```

### <a name="parameters"></a>Parametry

*_Istr* řetězec, který se zadá do vstupního datového proudu má být vložen do bitset –.

*správné* bitset –, který přijímá bity ze vstupního datového proudu.

### <a name="return-value"></a>Návratová hodnota

Funkce šablony vrátí řetězec *_Istr*.

### <a name="remarks"></a>Poznámky

Funkce přetížení šablon `operator>>` ukládat v bitset – _ *vpravo* bitset – hodnota (`str`), kde `str` je objekt typu [basic_string](basic-string-class.md)  <  **CharType**, **osobnostní rysy**, **alokátoru** \< **CharType**>> **&** extrahují z *_Istr*.

Funkce šablony extrahuje prvky z *_Istr* a vloží je do bitset – dokud:

- Všechny prvky bit byly extrahovány ze vstupního datového proudu a uložená v bitset –.

- Bitset – je se vyplní bits ze vstupního datového proudu.

- Input element, který není 1 ani 0 narazí.

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

## <a name="op_xor"></a>  operátor ^

Provádí logické bitové `EXCLUSIVE-OR` mezi dvěma bitsets.

```cpp
template <size_t size>
bitset<size>
operator^(
    const bitset<size>& left,
    const bitset<size>& right);
```

### <a name="parameters"></a>Parametry

*levé* první dva bitsets jehož příslušné prvky mají být kombinované pomocí bitového `EXCLUSIVE-OR`.

*správné* druhé dvě valarrays jehož příslušné prvky mají být kombinované pomocí bitového `EXCLUSIVE-OR`.

### <a name="return-value"></a>Návratová hodnota

Bitset –, jehož prvky jsou výsledkem provádění `EXCLUSIVE-OR` operace na odpovídající prvky *levé* a *správné*.

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

## <a name="op_or"></a>  operátor |

Provádí logické bitové `OR` mezi dvěma bitsets.

```cpp
template <size_t size>
bitset<size>
operator|(
    const bitset<size>& left,
    const bitset<size>& right);
```

### <a name="parameters"></a>Parametry

*levé* první dva bitsets jehož příslušné prvky mají být kombinované pomocí bitového `OR`.

*správné* druhé dvě valarrays jehož příslušné prvky mají být kombinované pomocí bitového `OR`.

### <a name="return-value"></a>Návratová hodnota

Bitset –, jehož prvky jsou výsledkem provádění `OR` operace na odpovídající prvky *levé* a *správné*.

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

## <a name="see-also"></a>Viz také:

[\<bitset – >](../standard-library/bitset.md)<br/>
