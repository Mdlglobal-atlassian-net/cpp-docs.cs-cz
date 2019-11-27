---
title: Formátování řetězců a I/O (moderní verze jazyka C++)
description: Možnosti pro formátované řetězce v/v jsou dostupné v C++moderních.
ms.date: 05/30/2019
ms.topic: conceptual
ms.assetid: 3954e8de-a59b-4175-89c9-4ee842ab89ed
ms.openlocfilehash: facb0b62cc1e92ed09a9ba729d766e5db7404282
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74308173"
---
# <a name="string-and-io-formatting-modern-c"></a>Formátování řetězců a I/O (moderní verze jazyka C++)

C++[\<iostream – >](../standard-library/iostream.md) třídy, funkce a operátory podporují formátování řetězce v/v. Například následující kód ukazuje, jak nastavit `cout` pro formátování celého čísla na výstup v šestnáctkovém formátu. Nejprve uloží aktuální stav k jeho resetování, protože po předání stavu formátu do `cout`zůstane takovým způsobem až do změny. Neplatí pouze pro jeden řádek kódu.

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

## <a name="alternative-format-options"></a>Možnosti alternativních formátů

Alternativně můžete použít `Boost.Format` z podpůrných C++ knihoven, i když je nestandardní. Všechny knihovny pro zvýšení úrovně si můžete stáhnout z webu pro [zvýšení úrovně](https://www.boost.org/) .

Mezi výhody `Boost.Format` patří:

- Bezpečné: Typově bezpečné typy a vyvolá výjimku pro chyby, například specifikace příliš málo nebo příliš velkého počtu položek.

- Rozšiřitelný: funguje pro jakýkoli typ, který může být datovým proudem.

- Pohodlné: standard POSIX a podobné řetězce formátu.

I když je `Boost.Format` postavená na C++ [\<iostream – >](../standard-library/iostream-programming.md) zařízeních, která jsou bezpečná a rozšiřitelná, nejsou optimalizované pro výkon. Pokud požadujete optimalizaci výkonu, zvažte možnost C [printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md) a [sprintf –](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md), které jsou rychlé a snadno použitelné. Nejsou ale rozšiřitelné ani bezpečné proti chybám zabezpečení. (Existují bezpečné verze, ale účtují mírné snížení výkonu. Další informace najdete v tématu [printf_s, _printf_s_l, wprintf_s, _wprintf_s_l](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md) a [sprintf_s _sprintf_s_l swprintf_s](../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md)_swprintf_s_l).

Následující kód demonstruje některé funkce formátování pro zvýšení úrovně.

```cpp
    string s = str( format("%2% %2% %1%\n") % "world" % "hello" );
    // s contains "hello hello world"

    for( auto i = 0; i < names.size(); ++i )
        cout << format("%1% %2% %|40t|%3%\n") % first[i] % last[i] % tel[i];
    // Georges Benjamin Clemenceau             +33 (0) 123 456 789
    // Jean de Lattre de Tassigny              +33 (0) 987 654 321
```

## <a name="see-also"></a>Viz také:

[Vítejte zpět naC++](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[Referenční dokumentace jazyka C++](../cpp/cpp-language-reference.md)<br/>
[Standardní knihovna C++](../standard-library/cpp-standard-library-reference.md)<br/>
[\<iostream – >](../standard-library/iostream.md)<br/>
[omezení \<>](../standard-library/limits.md)<br/>
[\<iomanip >](../standard-library/iomanip.md)
