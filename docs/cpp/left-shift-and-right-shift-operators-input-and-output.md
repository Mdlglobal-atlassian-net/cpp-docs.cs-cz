---
title: Operátory posunutí doleva a doprava (&gt; &gt; a &lt; &lt;)
ms.date: 08/13/2018
f1_keywords:
- <<
- '>>'
helpviewer_keywords:
- << operator [C++], with specific objects
- left shift operators [C++]
- right shift operators [C++]
- bitwise-shift operators [C++]
- '>> operator'
- shift operators [C++]
- operators [C++], shift
ms.assetid: 25fa0cbb-5fdd-4657-8745-b35f7d8f1606
ms.openlocfilehash: 2020c2dbbf8ff91ee692366f55c836be0b3dddb0
ms.sourcegitcommit: 6b749db14b4cf3a2b8d581fda6fdd8cb98bc3207
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/05/2020
ms.locfileid: "82825912"
---
# <a name="left-shift-and-right-shift-operators-gtgt-and-ltlt"></a>Operátory posunutí doleva a doprava (&gt; &gt; a &lt; &lt;)

Bitové operátory posunutí jsou operátor pravého posunutí (**&gt;**), který přesune bity *SHIFT-Expression* doprava a operátor levého posunutí (**&lt;**), který přesune bity *SHIFT-Expression* doleva. <sup>1</sup>

## <a name="syntax"></a>Syntaxe

> *výraz doplňkového* výrazu *SHIFT-Expression* `<<`\
> *výraz doplňkového* výrazu *SHIFT-Expression* `>>`

## <a name="remarks"></a>Poznámky

> [!IMPORTANT]
> Následující popisy a příklady jsou platné ve Windows pro architektury x86 a x64. Implementace operátorů levého a pravého posunutí se v systému Windows pro zařízení ARM podstatně liší. Další informace najdete v části "operátory pro přesun" v příspěvku na blogu [Hello ARM](https://blogs.msdn.com/b/vcblog/archive/2012/10/25/hello-arm-exploring-undefined-unspecified-and-implementation-defined-behavior-in-c.aspx) .

## <a name="left-shifts"></a>Posun doleva

Operátor levého posunutí způsobí posunutí bitů v *SHIFT-Expression* doleva o počet pozic určených *výrazem doplňkového výrazu*. Bitové pozice uvolněné operací posunutí se vyplní nulami. Posun doleva je logický posun (bity posunuté za konec se odstraní, včetně bitu znaku), Další informace o typech bitových posunutí naleznete v tématu [bitové posunutí](https://en.wikipedia.org/wiki/Bitwise_shift).

Následující příklad ukazuje operace levého posunutí pomocí čísel bez znaménka. Příklad ukazuje, co se děje s bity, znázorněním hodnoty jako bitové sady. Další informace naleznete v tématu [Třída bitset](../standard-library/bitset-class.md).

```cpp
#include <iostream>
#include <bitset>

using namespace std;

int main() {
    unsigned short short1 = 4;
    bitset<16> bitset1{short1};   // the bitset representation of 4
    cout << bitset1 << endl;  // 0b00000000'00000100

    unsigned short short2 = short1 << 1;     // 4 left-shifted by 1 = 8
    bitset<16> bitset2{short2};
    cout << bitset2 << endl;  // 0b00000000'00001000

    unsigned short short3 = short1 << 2;     // 4 left-shifted by 2 = 16
    bitset<16> bitset3{short3};
    cout << bitset3 << endl;  // 0b00000000'00010000
}
```

Pokud posunete doleva číslo se znaménkem tak, aby to mělo vliv na znaménko, bude výsledek nedefinovaný. Následující příklad ukazuje, co se stane, když se 1 bit posune doleva na pozici bitového znaménka.

```cpp
#include <iostream>
#include <bitset>

using namespace std;

int main() {
    short short1 = 16384;
    bitset<16> bitset1(short1);
    cout << bitset1 << endl;  // 0b01000000'00000000

    short short3 = short1 << 1;
    bitset<16> bitset3(short3);  // 16384 left-shifted by 1 = -32768
    cout << bitset3 << endl;  // 0b10000000'00000000

    short short4 = short1 << 14;
    bitset<16> bitset4(short4);  // 4 left-shifted by 14 = 0
    cout << bitset4 << endl;  // 0b00000000'00000000
}
```

## <a name="right-shifts"></a>Posuny doprava

Operátor pravého posunutí způsobí posunutí bitového vzoru v *SHIFT-Expression* doprava o počet pozic určených *výrazem doplňkového výrazu*. V případě čísel bez znaménka se bitové pozice uvolněné operací posunutí vyplní nulami. U čísel se znaménkem se bit znaménka použije k vyplnění uvolněných bitových pozic. Platí tedy, že pokud je číslo kladné, použije se 0. Pokud je číslo záporné, použije se 1.

> [!IMPORTANT]
> Výsledek posunu záporného čísla se znaménkem doprava je závislý na implementaci. Přestože kompilátor jazyka Microsoft C++ používá bit znaménka k naplnění uvolněnéch pozic, neexistuje žádná záruka, že to platí i pro jiné implementace.

Tento příklad ukazuje operace pravého posunutí pomocí čísel bez znaménka:

```cpp
#include <iostream>
#include <bitset>

using namespace std;

int main() {
    unsigned short short11 = 1024;
    bitset<16> bitset11{short11};
    cout << bitset11 << endl;     // 0b00000100'00000000

    unsigned short short12 = short11 >> 1;  // 512
    bitset<16> bitset12{short12};
    cout << bitset12 << endl;     // 0b00000010'00000000

    unsigned short short13 = short11 >> 10;  // 1
    bitset<16> bitset13{short13};
    cout << bitset13 << endl;     // 0b00000000'00000001

    unsigned short short14 = short11 >> 11;  // 0
    bitset<16> bitset14{short14};
    cout << bitset14 << endl;     // 0b00000000'00000000
}
```

Další příklad ukazuje operace pravého posunutí pomocí čísel s kladným znaménkem.

```cpp
#include <iostream>
#include <bitset>

using namespace std;

int main() {
    short short1 = 1024;
    bitset<16> bitset1(short1);
    cout << bitset1 << endl;     // 0b00000100'00000000

    short short2 = short1 >> 1;  // 512
    bitset<16> bitset2(short2);
    cout << bitset2 << endl;     // 0b00000010'00000000

    short short3 = short1 >> 11;  // 0
    bitset<16> bitset3(short3);
    cout << bitset3 << endl;     // 0b00000000'00000000
}
```

Další příklad ukazuje operace pravého posunutí pomocí celých čísel se záporným znaménkem.

```cpp
#include <iostream>
#include <bitset>

using namespace std;

int main() {
    short neg1 = -16;
    bitset<16> bn1(neg1);
    cout << bn1 << endl;  // 0b11111111'11110000

    short neg2 = neg1 >> 1; // -8
    bitset<16> bn2(neg2);
    cout << bn2 << endl;  // 0b11111111'11111000

    short neg3 = neg1 >> 2; // -4
    bitset<16> bn3(neg3);
    cout << bn3 << endl;  // 0b11111111'11111100

    short neg4 = neg1 >> 4; // -1
    bitset<16> bn4(neg4);
    cout << bn4 << endl;  // 0b11111111'11111111

    short neg5 = neg1 >> 5; // -1
    bitset<16> bn5(neg5);
    cout << bn5 << endl;  // 0b11111111'11111111
}
```

## <a name="shifts-and-promotions"></a>Posunutí a propagace

Výrazy na obou stranách operátoru posunutí musí být integrální typy. Celočíselné propagační akce se provádějí podle pravidel popsaných v tématu [standardní převody](standard-conversions.md). Typ výsledku je stejný jako typ propagovaného *SHIFT-Expression*.

V následujícím příkladu je proměnná typu **char** povýšena na **int**.

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

Výsledek operace posunutí není definován, pokud je *výraz doplňkového výrazu* záporný nebo pokud je *výraz doplňkového výrazu* větší nebo roven počtu bitů v (povýšen) *SHIFT-Expression*. Pokud je *výraz doplňkového výrazu* 0, neprovede se žádná operace posunutí.

```cpp
#include <iostream>
#include <bitset>

using namespace std;

int main() {
    unsigned int int1 = 4;
    bitset<32> b1{int1};
    cout << b1 << endl;    // 0b00000000'00000000'00000000'00000100

    unsigned int int2 = int1 << -3;  // C4293: '<<' : shift count negative or too big, undefined behavior
    unsigned int int3 = int1 >> -3;  // C4293: '>>' : shift count negative or too big, undefined behavior
    unsigned int int4 = int1 << 32;  // C4293: '<<' : shift count negative or too big, undefined behavior
    unsigned int int5 = int1 >> 32;  // C4293: '>>' : shift count negative or too big, undefined behavior
    unsigned int int6 = int1 << 0;
    bitset<32> b6{int6};
    cout << b6 << endl;    // 0b00000000'00000000'00000000'00000100 (no change)
}
```

## <a name="footnotes"></a>Poznámky pod čarou

<sup>1</sup> níže je popis operátorů posunu ve specifikaci C++ 11 ISO (INCITS/ISO/IEC 14882-2011 [2012]), oddíly 5.8.2 a 5.8.3.

Hodnota `E1 << E2` je `E1` `E2` bitová pozice posunutá doleva; uvolněné bity jsou vyplněny nulou. Pokud `E1` má typ bez znaménka, hodnota výsledku je **E1 × 2**<sup>**E2**</sup>, zmenšení modulo o jednu více než maximální hodnota reprezentovatelné v typu výsledku. Jinak, pokud `E1` má typ se znaménkem a nezápornou hodnotu a **E1 × 2**<sup>**E2**</sup> je reprezentovatelné v odpovídajícím typu bez znaménka typu výsledku, pak tato hodnota, která je převedena na výsledný typ, je výsledná hodnota; v opačném případě chování není definováno.

Hodnota `E1 >> E2` je `E1` `E2` bitová pozice vpravo posunuta. Pokud `E1` má typ bez znaménka nebo `E1` Pokud má podepsaný typ a nezápornou hodnotu, hodnota výsledku je nedílnou součástí podílu **E1/2**<sup>**E2**</sup>. Pokud `E1` má typ signed a zápornou hodnotu, výsledná hodnota je definovaná implementací.

## <a name="see-also"></a>Viz také

[Výrazy s binárními operátory](../cpp/expressions-with-binary-operators.md)<br/>
[Integrované operátory C++, jejich priorita a asociativita](../cpp/cpp-built-in-operators-precedence-and-associativity.md)
