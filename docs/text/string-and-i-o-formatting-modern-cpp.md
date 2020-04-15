---
title: Formátování řetězců a I/O (moderní verze jazyka C++)
description: Volby pro formátovaný řetězec V/O k dispozici v moderním jazyce C++.
ms.date: 05/30/2019
ms.topic: conceptual
ms.assetid: 3954e8de-a59b-4175-89c9-4ee842ab89ed
ms.openlocfilehash: a3fc93b0baf414759eb50c787c4057fb85dcb370
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375775"
---
# <a name="string-and-io-formatting-modern-c"></a>Formátování řetězců a I/O (moderní verze jazyka C++)

[ \<C++ iostream>](../standard-library/iostream.md) třídy, funkce a operátory podporují formátovaný řetězec V/O. Například následující kód ukazuje, `cout` jak nastavit formátování celé číslo na výstup v šestnáctkové. Nejprve uloží aktuální stav, aby jej později resetoval, `cout`protože jakmile je stav formátu předán , zůstane tímto způsobem, dokud se nezmění. Nevztahuje se pouze na jeden řádek kódu.

```cpp
#include <iostream>
#include <iomanip>

using namespace std;

int main()
{
    ios state(nullptr);

    cout << "The answer in decimal is: " << 42 << endl;

    state.copyfmt(cout); // save current formatting
    cout << "In hex: 0x" // now load up a bunch of formatting modifiers
        << hex
        << uppercase
        << setw(8)
        << setfill('0')
        << 42            // the actual value we wanted to print out
        << endl;
    cout.copyfmt(state); // restore previous formatting
}
```

Tento přístup je typově bezpečný a rozšiřitelný, ale je také složitý a podrobný.

## <a name="alternative-format-options"></a>Možnosti alternativního formátu

Jako alternativu můžete `Boost.Format` použít z knihoven Boost C++, i když je to nestandardní. Z webu Boost si můžete stáhnout libovolnou knihovnu [Boost.](https://www.boost.org/)

Některé výhody `Boost.Format` jsou:

- Bezpečné: Bezpečné: Typově bezpečné a vyvolá výjimku pro chyby, například specifikace příliš málo nebo příliš mnoho položek.

- Rozšiřitelné: Funguje pro libovolný typ, který lze streamovat.

- Pohodlné: Standardní POSIX a podobné formátovací řetězce.

I `Boost.Format` když je postaven na C++ [ \<iostream>](../standard-library/iostream-programming.md) zařízení, které jsou bezpečné a rozšiřitelné, nejsou optimalizované pro výkon. Pokud požadujete optimalizaci výkonu, zvažte C [printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md) a [sprintf](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md), které jsou rychlé a snadné použití. Nejsou však rozšiřitelné nebo bezpečné před chybami zabezpečení. (Existují bezpečné verze, ale hrozí jim mírný výkon. Další informace naleznete [v tématech printf_s, _printf_s_l, wprintf_s, _wprintf_s_l](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md) a [sprintf_s, _sprintf_s_l, swprintf_s, _swprintf_s_l](../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md)).

Následující kód ukazuje některé funkce formátování boost.

```cpp
    string s = str( format("%2% %2% %1%\n") % "world" % "hello" );
    // s contains "hello hello world"

    for( auto i = 0; i < names.size(); ++i )
        cout << format("%1% %2% %|40t|%3%\n") % first[i] % last[i] % tel[i];
    // Georges Benjamin Clemenceau             +33 (0) 123 456 789
    // Jean de Lattre de Tassigny              +33 (0) 987 654 321
```

## <a name="see-also"></a>Viz také

[Vítejte zpět v C++](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[Referenční příručka jazyka C++](../cpp/cpp-language-reference.md)<br/>
[Standardní knihovna C++](../standard-library/cpp-standard-library-reference.md)<br/>
[\<>iostream](../standard-library/iostream.md)<br/>
[\<limity>](../standard-library/limits.md)<br/>
[\<iomanip>](../standard-library/iomanip.md)
