---
title: Formátování řetězců a I/O (moderní verze jazyka C++)
description: Možnosti pro formátovaný řetězec vstupně-výstupní operace k dispozici v moderních C++.
ms.date: 05/30/2019
ms.topic: conceptual
ms.assetid: 3954e8de-a59b-4175-89c9-4ee842ab89ed
ms.openlocfilehash: e22c745798109a2dbef82297c45256593823f806
ms.sourcegitcommit: 28eae422049ac3381c6b1206664455dbb56cbfb6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/31/2019
ms.locfileid: "66450498"
---
# <a name="string-and-io-formatting-modern-c"></a>Formátování řetězců a I/O (moderní verze jazyka C++)

C++[ \<iostream – >](../standard-library/iostream.md) tříd, funkcí a operátorů podporují formátovaný řetězec vstupně-výstupních operací. Například následující kód ukazuje, jak nastavit `cout` k formátování výstupu v šestnáctkové soustavě celého čísla. Nejprve ho uloží aktuální stav resetovat ho později, protože jednou formátu stav je předán `cout`, zůstane tak, jak, dokud se nezmění. Neplatí pouze pro jeden řádek kódu.

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

Tento přístup je typově bezpečné a rozšiřitelné, ale je také komplexní a podrobný.

## <a name="alternative-format-options"></a>Možnosti alternativní formátu

Jako alternativu můžete použít `Boost.Format` z nárůst C++ knihovny, i když je nestandardní. Všechny knihovny Boost můžete stáhnout [Boost](https://www.boost.org/) webu.

Mezi výhody `Boost.Format` jsou:

- Bezpečnost: Typově bezpečný a vyvolá výjimku, například specifikace příliš málo nebo příliš mnoho položek.

- Rozšiřitelné: Funguje pro libovolný typ, který můžete Streamovat.

- Pohodlné: Standard Posix a podobné formátovací řetězce.

I když `Boost.Format` je postavená na C++ [ \<iostream – >](../standard-library/iostream-programming.md) zařízení, které jsou bezpečné a rozšiřitelné, nejsou optimalizovány pro výkon. Pokud požadujete optimalizaci výkonu, zvažte v jazyku C [printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md) a [sprintf](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md), které jsou rychlé a snadné použití. Však nejsou rozšiřitelné nebo bezpečné před chybami zabezpečení. (Existují bezpečné verze, ale způsobují mírné snížení výkonu. Další informace najdete v tématu [printf_s _printf_s_l –, wprintf_s – _wprintf_s_l –](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md) a [sprintf_s – _sprintf_s_l –, swprintf_s – _swprintf_s_l –](../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md)).

Následující kód ukazuje některé funkce formátování Boost.

```cpp
    string s = str( format("%2% %2% %1%\n") % "world" % "hello" );
    // s contains "hello hello world"

    for( auto i = 0; i < names.size(); ++i )
        cout << format("%1% %2% %|40t|%3%\n") % first[i] % last[i] % tel[i];
    // Georges Benjamin Clemenceau             +33 (0) 123 456 789
    // Jean de Lattre de Tassigny              +33 (0) 987 654 321
```

## <a name="see-also"></a>Viz také:

[C++ vás vítá zpět (moderní verze jazyka C++)](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[Referenční dokumentace jazyka C++](../cpp/cpp-language-reference.md)<br/>
[Standardní knihovna C++](../standard-library/cpp-standard-library-reference.md)<br/>
[\<iostream>](../standard-library/iostream.md)<br/>
[\<omezení >](../standard-library/limits.md)<br/>
[\<iomanip>](../standard-library/iomanip.md)
