---
title: "&lt;bitset –&gt; operátory | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
helpviewer_keywords:
- std::operator&amp; (bitset)
- std::operator&gt;&gt; (bitset)
- std::operator&lt;&lt; (bitset)
ms.workload:
- cplusplus
ms.openlocfilehash: 45dab1512054f80d5cec309ca4637b4972d8b555
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="ltbitsetgt-operators"></a>&lt;bitset –&gt; operátory
||||  
|-|-|-|  
|[Operátor&amp;](#op_amp)|[Operátor&gt;&gt;](#op_gt_gt)|[Operátor&lt;&lt;](#op_lt_lt)|  
|[operator^](#op_xor)|[– operátor|](#op_or)|  
  
##  <a name="op_amp"></a>  Operátor&amp;  
 Provede bitové `AND` mezi dvěma bitové sady.  
  
```  
template <size_t size>  
bitset<size>  
operator&(
    const bitset<size>& left,  
    const bitset<size>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `left`  
 První dvě bitové sady, jehož elementy příslušného mají nelze kombinovat s bitové hodnotě `AND`.  
  
 `right`  
 Druhý dva valarray – třídy, jejichž příslušné prvky jsou a nelze jej zkombinovat s bitové hodnotě `AND`.  
  
### <a name="return-value"></a>Návratová hodnota  
 Bitset, jehož elementy jsou výsledkem provádění `AND` operace na odpovídající elementy `left` a `right`.  
  
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
  
##  <a name="op_lt_lt"></a>  Operátor&lt;&lt;  
 Vloží textovou reprezentaci pořadí bit do výstupního datového proudu.  
  
```  
 
template <class CharType, class Traits, size_t N>  
basic_ostream<CharType, Traits>& operator<<(
    basic_ostream<CharType, Traits>& ostr,  
    const bitset<N>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `right`  
 Objekt typu **bitset\<N >** , který má být vložena do výstupního datového proudu jako řetězec.  
  
### <a name="return-value"></a>Návratová hodnota  
 Reprezentace textu bit pořadí v **ostr**.  
  
### <a name="remarks"></a>Poznámky  
 Přetížení funkce šablony **operátor <<**, což bitset k zapsání bez první převádění na řetězce. Funkce šablony efektivně provede:  
  
 **ostr** << _ *vpravo*. [to_string –](bitset-class.md) < **CharType**, **vlastnosti**, **allocator** \< **CharType**>>)  
  
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
  
##  <a name="op_gt_gt"></a>  Operátor&gt;&gt;  
 Načte do bitset řetězec rozšířené znaky.  
  
```  
 
template <class CharType, class Traits, size_t Bits>  
basic_istream<CharType, Traits>& operator>> (
    basic_istream<CharType, Traits>& 
_Istr,  
    bitset<N>& 
    right);
```  
  
### <a name="parameters"></a>Parametry  
 `_Istr`  
 Řetězec, který jste zadali do vstupního datového proudu má být vložen do bitset.  
  
 `right`  
 Bitset –, který přijímá bity ze vstupního datového proudu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Funkce šablony vrátí řetězec `_Istr`.  
  
### <a name="remarks"></a>Poznámky  
 Přetížení funkce šablony **operátor >>** k uložení v bitset _ *vpravo* bitset – hodnota ( `str`), kde `str` je objekt typu [basic_string ](basic-string-class.md)  <  **CharType**, **vlastnosti**, **allocator** \< **CharType**> >  **&**  extrahují z `_Istr`.  
  
 Funkce šablony extrahuje prvky z `_Istr` a vloží je do bitset – dokud:  
  
-   Všechny elementy bit byly extrahovány ze vstupního datového proudu a uložené v bitset.  
  
-   Bitset zaplní s bity ze vstupního datového proudu.  
  
-   Zjistil se input element, který je 1 ani 0.  
  
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
  
##  <a name="op_xor"></a>  Operator ^  
 Provede bitové `EXCLUSIVE-OR` mezi dvěma bitové sady.  
  
```  
template <size_t size>  
bitset<size>  
operator^(
    const bitset<size>& left,  
    const bitset<size>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `left`  
 První dvě bitové sady, jehož elementy příslušného mají nelze kombinovat s bitové hodnotě `EXCLUSIVE-OR`.  
  
 `right`  
 Druhý dva valarray – třídy, jejichž příslušné prvky jsou a nelze jej zkombinovat s bitové hodnotě `EXCLUSIVE-OR`.  
  
### <a name="return-value"></a>Návratová hodnota  
 Bitset, jehož elementy jsou výsledkem provádění `EXCLUSIVE-OR` operace na odpovídající elementy `left` a `right`.  
  
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
  
##  <a name="op_or"></a>  operátor |  
 Provede bitové `OR` mezi dvěma bitové sady.  
  
```  
template <size_t size>  
bitset<size>  
operator|(
    const bitset<size>& left,  
    const bitset<size>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `left`  
 První dvě bitové sady, jehož elementy příslušného mají nelze kombinovat s bitové hodnotě `OR`.  
  
 `right`  
 Druhý dva valarray – třídy, jejichž příslušné prvky jsou a nelze jej zkombinovat s bitové hodnotě `OR`.  
  
### <a name="return-value"></a>Návratová hodnota  
 Bitset, jehož elementy jsou výsledkem provádění `OR` operace na odpovídající elementy `left` a `right`.  
  
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
  
## <a name="see-also"></a>Viz také  
 [\<bitset>](../standard-library/bitset.md)

