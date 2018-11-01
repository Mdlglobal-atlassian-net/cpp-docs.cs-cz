---
title: Řetězec a formátování I/o (moderní verze jazyka C++)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 3954e8de-a59b-4175-89c9-4ee842ab89ed
ms.openlocfilehash: 0cc0c84a6e4ffac3e6a80425039bfcc1db567911
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50631839"
---
# <a name="string-and-io-formatting-modern-c"></a>Formátování řetězců a I/O (moderní verze jazyka C++)

C++ [iostreams](../standard-library/iostream.md) jsou schopny vstupu a výstupu formátovaných řetězců. Například následující kód ukazuje, jak nastavit cout k formátování výstupu v šestnáctkové soustavě, nejprve uložením mimo aktuální stav a opětovným nastavením později, protože jakmile formátování stavu je předání cout zůstane tak, jak, dokud není změněno, nikoli pouze pro jeden řádek celého čísla kódu.

```cpp
#include <iostream>
#include <iomanip>

using namespace std;

int main() 
{
    ios state(nullptr);

    cout << "The answer in decimal is: " << 42 << endl;

    state.copyfmt(cout); // save current formatting
    cout << "In hex: 0x" // now load up a bunch of formatting modifiers
        << hex 
        << uppercase 
        << setw(8) 
        << setfill('0') 
        << 42            // the actual value we wanted to print out
        << endl;
    cout.copyfmt(state); // restore previous formatting
}
```

To může být v mnoha případech příliš obtížné. Jako alternativu můžete použít metodu Boost.Format z knihoven Boost C++, přestože je nestandardní. Všechny knihovny Boost můžete stáhnout [Boost](http://www.boost.org/) webu.

Některé výhody Boost.Format jsou:

- Bezpečnost: Typově bezpečný a vyvolá výjimku – například specifikace příliš málo nebo příliš mnoho položek.

- Rozšiřitelné: Funguje pro libovolný typ, který můžete Streamovat.

- Pohodlné: Standard Posix a podobné formátovací řetězce.

I když je Boost.Format založen na knihovnách C++ [iostreams](../standard-library/iostream-programming.md), které jsou bezpečné a rozšiřitelné, a proto nejsou optimalizovány pro výkon. Pokud požadujete optimalizaci výkonu, zvažte v jazyku C [printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md) a [sprintf](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md), které jsou rychlé a snadné použití. Však nejsou rozšiřitelné nebo bezpečné před chybami zabezpečení. (Existují bezpečné verze, ale způsobují mírné snížení výkonu. Další informace najdete v tématu [printf_s _printf_s_l –, wprintf_s – _wprintf_s_l –](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md) a [sprintf_s – _sprintf_s_l –, swprintf_s – _swprintf_s_l –](../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md)).

Následující kód ukazuje některé funkce formátování Boost.

```cpp
    string s = str( format("%2% %2% %1%\n") % "world" % "hello" );
    // s contains "hello hello world"  

    for( auto i = 0; i < names.size(); ++i )
        cout << format("%1% %2% %|40t|%3%\n") % first[i] % last[i] % tel[i];
    // Georges Benjamin Clemenceau             +33 (0) 123 456 789
    // Jean de Lattre de Tassigny              +33 (0) 987 654 321
```

## <a name="see-also"></a>Viz také:

[C++ vás vítá zpět](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[Referenční dokumentace jazyka C++](../cpp/cpp-language-reference.md)<br/>
[Standardní knihovna C++](../standard-library/cpp-standard-library-reference.md)<br/>
[\<iostream – >](../standard-library/iostream.md)<br/>
[\<omezení >](../standard-library/limits.md)<br/>
[\<iomanip >](../standard-library/iomanip.md)