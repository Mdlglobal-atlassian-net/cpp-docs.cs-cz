---
title: Operátor posunu vlevo a vpravo (&gt; &gt; a &lt; &lt;)
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
ms.openlocfilehash: 2f118c11aab9fb2bbdd6cfa4f23425077b382b23
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50565839"
---
# <a name="left-shift-and-right-shift-operators-gtgt-and-ltlt"></a>Operátor posunu vlevo a vpravo (&gt; &gt; a &lt; &lt;)

Bitové operátory posunutí jsou operátor pravého posunutí (**&gt;&gt;**), který přesune bity *shift-expression* a operátor levého posunutí doprava (**&lt; &lt;**), který přesune bity *shift-expression* vlevo. <sup>1</sup>

## <a name="syntax"></a>Syntaxe

> *SHIFT-expression* `<<` *additive-expression*
> *shift-expression* `>>` *additive-expression*

## <a name="remarks"></a>Poznámky

> [!IMPORTANT]
> Následující popisy a příklady platí ve Windows pro architektury x86 a x64. Implementace operátorů levého a pravého posunutí se výrazně liší ve Windows pro zařízení ARM. Další informace najdete v části "Operátory posunutí" [Hello ARM](https://blogs.msdn.com/b/vcblog/archive/2012/10/25/hello-arm-exploring-undefined-unspecified-and-implementation-defined-behavior-in-c.aspx) blogový příspěvek.

## <a name="left-shifts"></a>Posun doleva

Operátor levého posunutí způsobí posunutí bitů v *shift-expression* vlevo o počet pozic určený *additive-expression*. Bitové pozice uvolněné operací posunutí se vyplní nulami. Posun doleva je logický posun (bity posunuté za konec se odstraní, včetně bitu znaku), Další informace o druzích bitových posunů naleznete v tématu [bitových posunů](https://en.wikipedia.org/wiki/Bitwise_shift).

Následující příklad ukazuje operace levého posunutí pomocí čísel bez znaménka. Příklad ukazuje, co se děje s bity, znázorněním hodnoty jako bitové sady. Další informace najdete v tématu [bitset – třída](../standard-library/bitset-class.md).

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

Pokud posunete doleva číslo se znaménkem tak, aby to mělo vliv na znaménko, bude výsledek nedefinovaný. Následující příklad ukazuje, co se stane v jazyce Visual C++, když se 1 bit posune doleva na pozici bitu znaménka.

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

Operátor pravého posunutí způsobí posunutí bitů v *shift-expression* vpravo o počet pozic určený *additive-expression*. V případě čísel bez znaménka se bitové pozice uvolněné operací posunutí vyplní nulami. U čísel se znaménkem se bit znaménka použije k vyplnění uvolněných bitových pozic. Platí tedy, že pokud je číslo kladné, použije se 0. Pokud je číslo záporné, použije se 1.

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

Výrazy na obou stranách operátoru posunutí musí být integrální typy. Integrální propagace se provádí dle pravidel popsaných v [standardní převody](standard-conversions.md). Typ výsledku je stejný jako typ zvýšeného parametru *shift-expression*.

V následujícím příkladu se proměnná typu **char** je povýšen na **int**.

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

Výsledek operace posunutí není definován, pokud *additive-expression* je záporný nebo, pokud *additive-expression* je větší než nebo roven počtu bitů ve (zvýšeném)  *SHIFT-expression*. Operace posunutí se neprovádí, pokud *additive-expression* je 0.

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

<sup>1</sup> následuje popis operátorů posunutí ve specifikace C ++ 11 ISO (INCITS/ISO/IEC 14882-2011[2012]), oddíly 5.8.2 a 5.8.3.

Hodnota `E1 << E2` je `E1` posunuta doleva o `E2` bitových pozic; uvolněné bity jsou vyplněny nulami. Pokud `E1` má typ bez znaménka, hodnota výsledku je **E1 × 2**<sup>**E2**</sup>, snížené modulo o jedno více než maximální hodnota reprezentovatelná v typu výsledku. Jinak, pokud `E1` má typ se znaménkem a nezápornou hodnotu a **E1 × 2**<sup>**E2** </sup> je reprezentovatelné v odpovídajícím typ bez znaménka typu výsledku, pak Hodnota převedená na typ výsledku je výsledná hodnota; jinak není chování definováno.

Hodnota `E1 >> E2` je `E1` posunuta doprava `E2` bitových pozic. Pokud `E1` má typ bez znaménka nebo pokud `E1` má typ se znaménkem a nezápornou hodnotu, hodnota výsledku je integrální část kvocientu **E1/2**<sup>**E2** </sup>. Pokud `E1` má typ se znaménkem a zápornou hodnotu, je výsledná hodnota definovaná implementací.

## <a name="see-also"></a>Viz také:

[Výrazy s binárními operátory](../cpp/expressions-with-binary-operators.md)<br/>
[Integrované operátory C++, jejich priorita a asociativita](../cpp/cpp-built-in-operators-precedence-and-associativity.md)
