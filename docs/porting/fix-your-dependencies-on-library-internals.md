---
title: Oprava závislostí u C++ interních knihoven
ms.date: 05/24/2017
helpviewer_keywords:
- library internals in an upgraded Visual Studio C++ project
- _Hash_seq in an upgraded Visual Studio C++ project
ms.assetid: 493e0452-6ecb-4edc-ae20-b6fce2d7d3c5
ms.openlocfilehash: 5486cd65a34e3ef69f3b2e948ba0ad020e68b326
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/05/2019
ms.locfileid: "73627002"
---
# <a name="fix-your-dependencies-on-c-library-internals"></a>Oprava závislostí u C++ interních knihoven

Společnost Microsoft publikovala zdrojový kód pro standardní knihovnu, většinu běhové knihovny jazyka C a další knihovny Microsoftu v mnoha verzích sady Visual Studio. Záměrem je pomáhat pochopit chování knihovny a ladit kód. Jedním z vedlejších účinků publikování zdrojového kódu knihovny je, že některé interní hodnoty, datové struktury a funkce jsou vystaveny, i když nejsou součástí rozhraní knihovny. Obvykle mají názvy začínající dvěma podtržítky nebo podtržítkem následovaným velkým písmenem, názvy, které C++ standardní rezervuje na implementace. Tyto hodnoty, struktury a funkce jsou podrobnosti implementace, které se můžou měnit v době, kdy se knihovny vyvíjejí v čase, a proto důrazně doporučujeme, abyste na ně převzali jakékoli závislosti. Pokud tak učiníte, riskujete nepřenosný kód a problémy při pokusu o migraci kódu do nových verzí knihoven.

Ve většině případů nezmiňuje dokument novinky a změny v jednotlivých vydáních sady Visual Studio změny interní knihovny. Po všech případech nebudete mít vliv na tyto podrobnosti implementace. V některých případech však pokušení použít nějaký kód, který vidíte v knihovně, je příliš Skvělé. Toto téma popisuje závislosti na standardech CRT nebo standardní knihovně, na kterých jste se mohli spoléhat, a o tom, jak kód aktualizovat, abyste tyto závislosti odstranili, abyste ho mohli lépe naformátovat nebo migrovat na nové verze knihovny.

## <a name="_hash_seq"></a>_Hash_seq

Vnitřní funkce hash `std::_Hash_seq(const unsigned char *, size_t)`používaná k implementaci `std::hash` na některých typech řetězců byla v posledních verzích standardní knihovny vidět. Tato funkce implementovala [hodnotu hash FNV-1a]( https://en.wikipedia.org/wiki/Fowler%E2%80%93Noll%E2%80%93Vo_hash_function) ve znakové sekvenci.

K odebrání této závislosti máte několik možností.

- Pokud je vaším záměrem vložit `const char *` sekvenci do neuspořádaného kontejneru pomocí stejného strojového kódu hash jako `basic_string`, můžete to provést pomocí přetížení šablony `std::hash`, které přebírá `std::string_view`, který vrací tento kód hash přenosného způsobu. Kód knihovny řetězců může nebo nemusí spoléhat na použití hodnoty hash FNV-1a v budoucnu, takže to je nejlepší způsob, jak se vyhnout závislosti na konkrétním algoritmu hash.

- Pokud je vaším záměrem vygenerovat hodnotu hash FNV-1a přes volnou paměť, provedli jsme tento kód v GitHubu v úložišti [VCSamples]( https://github.com/Microsoft/vcsamples) v samostatném hlavičkovém souboru [fnv1a. HPP](https://github.com/Microsoft/VCSamples/tree/master/VC2015Samples/_Hash_seq)v rámci [licence MIT](https://github.com/Microsoft/VCSamples/blob/master/license.txt). Pro vaše pohodlí jsme také zahrnuli kopii. Tento kód můžete zkopírovat do souboru hlaviček, přidat hlavičku do libovolného ovlivněného kódu a pak vyhledat a nahradit `_Hash_seq` `fnv1a_hash_bytes`. K interní implementaci v `_Hash_seq`se dostanete stejné chování.

```cpp
/*
VCSamples
Copyright (c) Microsoft Corporation
All rights reserved.
MIT License
Permission is hereby granted, free of charge, to any person obtaining a copy of
this software and associated documentation files (the "Software"), to deal in
the Software without restriction, including without limitation the rights to
use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies
of the Software, and to permit persons to whom the Software is furnished to do
so, subject to the following conditions:
The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.
THE SOFTWARE IS PROVIDED *AS IS*, WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
*/
#include <stddef.h>

inline size_t fnv1a_hash_bytes(const unsigned char * first, size_t count) {
#if defined(_WIN64)
    static_assert(sizeof(size_t) == 8, "This code is for 64-bit size_t.");
    const size_t fnv_offset_basis = 14695981039346656037ULL;
    const size_t fnv_prime = 1099511628211ULL;
#else /* defined(_WIN64) */
    static_assert(sizeof(size_t) == 4, "This code is for 32-bit size_t.");
    const size_t fnv_offset_basis = 2166136261U;
    const size_t fnv_prime = 16777619U;
#endif /* defined(_WIN64) */

    size_t result = fnv_offset_basis;
    for (size_t next = 0; next < count; ++next)
    {
        // fold in another byte
        result ^= (size_t)first[next];
        result *= fnv_prime;
    }
    return (result);
}
```

## <a name="see-also"></a>Viz také:

[Upgrade projektů z dřívějších verzí sady VisualC++](upgrading-projects-from-earlier-versions-of-visual-cpp.md)<br/>
[Přehled potenciálních problémů s upgradem (Visual C++)](overview-of-potential-upgrade-issues-visual-cpp.md)<br/>
[Upgrade kódu na Universal CRT](upgrade-your-code-to-the-universal-crt.md)