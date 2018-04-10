---
title: Operátor posunu vlevo a vpravo (&gt; &gt; a &lt; &lt;) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-language
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- <<
- '>>'
dev_langs:
- C++
helpviewer_keywords:
- << operator [C++], with specific objects
- left shift operators [C++]
- right shift operators [C++]
- bitwise-shift operators [C++]
- '>> operator'
- shift operators [C++]
- operators [C++], shift
ms.assetid: 25fa0cbb-5fdd-4657-8745-b35f7d8f1606
caps.latest.revision: 18
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7dece9ac4045fa8b46e5edf8b266312242000229
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="left-shift-and-right-shift-operators-gtgt-and-ltlt"></a>Operátor posunu vlevo a vpravo (&gt; &gt; a &lt; &lt;)
Operátory bitového posunutí jsou operátor posunutí doprava (>>), který přesune bity *shift výraz* operátor posunutí doleva a doprava (<<), který přesune bity *shift výraz* doleva. <sup>1</sup>  
  
## <a name="syntax"></a>Syntaxe  
  
> *SHIFT – výraz* `<<` *doplňkové – výraz*  
> *SHIFT – výraz* `>>` *doplňkové – výraz*  
  
## <a name="remarks"></a>Poznámky  
  
> [!IMPORTANT]
> Následující popisy a příklady platí v systému Windows pro architektury X86 a x64. Implementace operátorů levého a pravého posunutí se výrazně liší v zařízeních se systémem Windows RT a v zařízeních ARM. Další informace najdete v části "Posunutí – operátory" [Hello ARM](http://blogs.msdn.com/b/vcblog/archive/2012/10/25/hello-arm-exploring-undefined-unspecified-and-implementation-defined-behavior-in-c.aspx) příspěvku na blogu.  
  
## <a name="left-shifts"></a>Posun doleva  
 Operátor posunutí doleva způsobí, že bity v *shift výraz* posunutí doleva o počet pozic určeného *doplňkové výraz*. Bitové pozice uvolněné operací posunutí se vyplní nulami. Posun doleva je logický posun (bity posunuté za konec se odstraní, včetně bitu znaku), Další informace o typech bitové posuny najdete v tématu [bitové posuny](http://en.wikipedia.org/wiki/Bitwise_shift).  
  
 Následující příklad ukazuje operace levého posunutí pomocí čísel bez znaménka. Příklad ukazuje, co se děje s bity, znázorněním hodnoty jako bitové sady. Další informace najdete v tématu [bitset – třída](../standard-library/bitset-class.md).  
  
```cpp  
#include <iostream>  
#include <bitset>  
using namespace std;  
  
int main() {  
    unsigned short short1 = 4;      
    bitset<16> bitset1{short1};   // the bitset representation of 4  
    cout << bitset1 << endl;  // 0000000000000100  
  
    unsigned short short2 = short1 << 1;     // 4 left-shifted by 1 = 8  
    bitset<16> bitset2{short2};  
    cout << bitset2 << endl;  // 0000000000001000  
  
    unsigned short short3 = short1 << 2;     // 4 left-shifted by 2 = 16  
    bitset<16> bitset3{short3};  
    cout << bitset3 << endl;  // 0000000000010000  
}  
  
```  
  
 Pokud posunete doleva číslo se znaménkem tak, aby to mělo vliv na znaménko, bude výsledek nedefinovaný. Následující příklad ukazuje, co se stane v jazyce Visual C++, když se 1 bit posune doleva na pozici bitu znaménka.  
  
```cpp  
#include <iostream>  
#include <bitset>  
using namespace std;  
  
int main() {  
    short short1 = 16384;      
    bitset<16> bitset1{short2};  
    cout << bitset1 << endl;  // 0100000000000000   
  
    short short3 = short1 << 1;  
    bitset<16> bitset3{short3};  // 16384 left-shifted by 1 = -32768  
    cout << bitset3 << endl;  // 100000000000000  
  
    short short4 = short1 << 14;  
    bitset<16> bitset4{short4};  // 4 left-shifted by 14 = 0  
    cout << bitset4 << endl;  // 000000000000000    
}  
```  
  
## <a name="right-shifts"></a>Posuny doprava  
 Operátor posunutí doprava způsobí, že bitový v *shift výraz* posunutí doprava o počet pozic určeného *doplňkové výraz*. V případě čísel bez znaménka se bitové pozice uvolněné operací posunutí vyplní nulami. U čísel se znaménkem se bit znaménka použije k vyplnění uvolněných bitových pozic. Platí tedy, že pokud je číslo kladné, použije se 0. Pokud je číslo záporné, použije se 1.  
  
> [!IMPORTANT]
> Výsledek posunu záporného čísla se znaménkem doprava je závislý na implementaci. Přestože jazyk Visual C++ používá bit znaménka k vyplnění uvolněných pozic, není nijak zaručeno, že tak budou činit i další implementace.  
  
 Tento příklad ukazuje operace pravého posunutí pomocí čísel bez znaménka:  
  
```cpp  
#include <iostream>  
#include <bitset>  
using namespace std;  
  
int main() {  
    unsigned short short11 = 1024;  
    bitset<16> bitset11{short11};  
    cout << bitset11 << endl;     // 0000010000000000  
  
    unsigned short short12 = short11 >> 1;  // 512  
    bitset<16> bitset12{short12};  
    cout << bitset12 << endl;     // 0000001000000000  
  
    unsigned short short13 = short11 >> 10;  // 1  
    bitset<16> bitset13{short13};  
    cout << bitset13 << endl;     // 0000000000000001  
  
    unsigned short short14 = short11 >> 11;  // 0  
    bitset<16> bitset14{short14};  
    cout << bitset14 << endl;     // 0000000000000000}  
}  
```  
  
 Další příklad ukazuje operace pravého posunutí pomocí čísel s kladným znaménkem.  
  
```cpp  
#include <iostream>  
#include <bitset>  
using namespace std;  
  
int main() {  
    short short1 = 1024;  
    bitset<16> bitset1{short1};  
    cout << bitset1 << endl;     // 0000010000000000  
  
    short short2 = short1 >> 1;  // 512  
    bitset<16> bitset2{short2};  
    cout << bitset2 << endl;     // 0000001000000000  
  
    short short3 = short1 >> 11;  // 0  
    bitset<16> bitset3{short3};     
    cout << bitset3 << endl;     // 0000000000000000  
}  
```  
  
 Další příklad ukazuje operace pravého posunutí pomocí celých čísel se záporným znaménkem.  
  
```cpp  
#include <iostream>  
#include <bitset>  
using namespace std;  
  
int main() {  
    short neg1 = -16;  
    bitset<16> bn1{neg1};  
    cout << bn1 << endl;  // 1111111111110000  
  
    short neg2 = neg1 >> 1; // -8  
    bitset<16> bn2{neg2};  
    cout << bn2 << endl;  // 1111111111111000  
  
    short neg3 = neg1 >> 2; // -4  
    bitset<16> bn3{neg3};  
    cout << bn3 << endl;  // 1111111111111100  
  
    short neg4 = neg1 >> 4; // -1  
    bitset<16> bn4{neg4};      
    cout << bn4 << endl;  // 1111111111111111  
  
    short neg5 = neg1 >> 5; // -1   
    bitset<16> bn5{neg5};      
    cout << bn5 << endl;  // 1111111111111111  
}  
```  
  
## <a name="shifts-and-promotions"></a>Posunutí a propagace  
 Výrazy na obou stranách operátoru posunutí musí být integrální typy. Zvýšení úrovně celého čísla probíhají podle pravidel popsaných v [standardní převody](standard-conversions.md). Typ výsledku je stejný jako typ propagovaných *shift výraz*.  
  
 V následujícím příkladu, proměnné typu `char` je propagována do `int`.  
  
```cpp  
#include <iostream>  
#include <typeinfo>  
  
using namespace std;  
  
int main() {  
    char char1 = 'a';  
  
    auto promoted1 = char1 << 1;   // 194  
    cout << typeid(promoted1).name() << endl;  // int  
  
    auto promoted2 = char1 << 10;  // 99328  
    cout << typeid(promoted2).name() << endl;  // int  
}  
```  
  
## <a name="additional-details"></a>Další podrobnosti  
 Výsledek operace posunutí není definován, pokud *doplňkové výraz* je záporný nebo, pokud *doplňkové výraz* je větší než nebo rovno počtu bitů v (propagovaných)  *SHIFT – výraz*. Pokud je provedena žádná operace shift *doplňkové výraz* je 0.  
  
```cpp  
#include <iostream>  
#include <bitset>  
using namespace std;  
  
int main() {  
    unsigned int int1 = 4;  
    bitset<32> b1{int1};  
    cout << b1 << endl;    // 00000000000000000000000000000100  
  
    unsigned int int2 = int1 << -3;  // C4293: '<<' : shift count negative or too big, undefined behavior  
    unsigned int int3 = int1 >> -3;  // C4293: '>>' : shift count negative or too big, undefined behavior  
  
    unsigned int int4 = int1 << 32;  // C4293: '<<' : shift count negative or too big, undefined behavior  
  
    unsigned int int5 = int1 >> 32;  // C4293: '>>' : shift count negative or too big, undefined behavior  
  
    unsigned int int6 = int1 << 0;  
    bitset<32> b6{int6};  
    cout << b6 << endl;    // 00000000000000000000000000000100 (no change)}  
}  
```  
  
## <a name="footnotes"></a>Poznámky pod čarou  
 1 následuje popis operátory posunutí specifikací C ++ 11 ISO (INCITS nebo ISO/IEC 14882-2011[2012]), částech 5.8.2 a 5.8.3.  
  
 Hodnota **E1 << E2** je **E1** zapuštěno doleva **E2** bit pozic; vacated bits se naplní nula. Pokud **E1** má typ bez znaménka, je hodnota výsledku **E1 × 2**<sup>**E2**</sup>, snížené modulo jednu vyšší než maximální hodnota reprezentovat Typ výsledku. Jinak Pokud **E1** má typ se znaménkem a nezápornou hodnotu a **E1 × 2**<sup>**E2** </sup> je reprezentovat odpovídající typu bez znaménka výsledek typu pak tuto hodnotu převést na typ výsledku je výsledné hodnoty. chování, jinak hodnota není definován.  
  
 Hodnota **E1 >> E2** je **E1** zapuštěno vpravo **E2** bit pozic. Pokud **E1** má hodnotu typu bez znaménka nebo, pokud **E1** má typ se znaménkem a nezápornou hodnotu, hodnota výsledku je nedílnou součástí podíl **E1/2** <sup> **E2**</sup>. Pokud **E1** má typ se znaménkem a záporná, výsledná hodnota je definované implementací.  
  
## <a name="see-also"></a>Viz také  
 [Výrazy s binárními operátory](../cpp/expressions-with-binary-operators.md)   
 [Integrované operátory C++, jejich priorita a asociativita](../cpp/cpp-built-in-operators-precedence-and-associativity.md)