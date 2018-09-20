---
title: Oprava závislostí u interních informací o knihovně | Dokumentace Microsoftu
ms.custom: ''
ms.date: 05/24/2017
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- library internals in an upgraded Visual C++ project
- _Hash_seq in an upgraded Visual C++ project
ms.assetid: 493e0452-6ecb-4edc-ae20-b6fce2d7d3c5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f70ef59ff43e7a8002ce312bd79702e465f52c74
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46385869"
---
# <a name="fix-your-dependencies-on-library-internals"></a>Oprava závislostí u interních informací o knihovně

Společnost Microsoft publikovala zdrojový kód pro standardní knihovnu, většina běhové knihovny jazyka C a další knihovny Microsoft v mnoha verzí sady Visual Studio. Naším záměrem je vám pomůžou pochopit chování knihovny a na ladění vašeho kódu. Jeden vedlejší efekt publikování zdrojový kód knihovny je, že některé interními hodnotami, datové struktury a funkcí jsou přístupné, i když nejsou součástí rozhraní knihovny. Mají obvykle názvy začínající dvěma podtržítky nebo podtržítkem, za nímž následuje velké písmeno, názvy, které standardu jazyka C++ vyhrazuje do implementace. Tyto hodnoty, struktury a funkce jsou podrobnosti implementace, které mohou změnit knihoven v průběhu času vyvíjejí, a proto důrazně nedoporučujeme na nich s ohledem všechny závislosti. Pokud tak učiníte, riskujete, že kód nepřenosné a problémů při pokusu o migrovat kód do nové verze knihoven.  

Ve většině případů co je nového nebo Breaking Changes dokument pro každou verzi sady Visual Studio nebude zmiňovat změny s interními funkcemi knihovny. Koneckonců můžete už by nemělo být ovlivněny tyto podrobnosti implementace. Ale někdy pokušení používat nějaký kód, který se zobrazí v knihovně je příliš velké. Toto téma popisuje závislosti na CRT nebo standardní knihovna interní informace, které můžete mít spoléhal na a tom, jak aktualizovat váš kód k odebrání těchto závislostí, můžete provést větší přenositelnost nebo migrovat na nové verze knihovny.

## <a name="hashseq"></a>_Hash_seq  

Interní hodnota hash funkce `std::_Hash_seq(const unsigned char *, size_t)`, která slouží k implementaci `std::hash` u některých typů řetězce byla zobrazená v nejnovějších verzích standardní knihovny. Tuto funkci implementovat [FNV 1a hash]( https://en.wikipedia.org/wiki/Fowler%E2%80%93Noll%E2%80%93Vo_hash_function) na sekvenci znaků.  
  
Pokud chcete odebrat tuto závislost, máte několik možností.  

- Pokud máte v úmyslu, je vložit `const char *` pořadí do Neseřazený kontejneru pomocí stejné strojů kód hash jako `basic_string`, můžete to udělat pomocí `std::hash` šablony přetížení, která přebírá `std::string_view`, vracející tento kód hash v přenosný způsob. Kód knihovny řetězec může nebo nemusí spoléhat na použití algoritmus hash FNV 1a v budoucnu, tohle je nejlepší způsob, jak se vyhnout se závislostí na konkrétním hashovací algoritmus. 
  
- Pokud máte v úmyslu generovat algoritmus hash FNV 1a prostřednictvím libovolného paměti, zpřístupnili jsme, že kód na Githubu v [VCSamples]( https://github.com/Microsoft/vcsamples) úložiště v souboru hlaviček samostatné [fnv1a.hpp](https://github.com/Microsoft/VCSamples/tree/master/VC2015Samples/_Hash_seq), v části [Licencí MIT](https://github.com/Microsoft/VCSamples/blob/master/license.txt). Přidali jsme také zkopírovat sem pro vaše pohodlí. Tento kód můžete zkopírovat do souboru hlaviček, přidat hlavičku do žádné ovlivněné kód a najít a nahradit `_Hash_seq` podle `fnv1a_hash_bytes`. Zobrazí se stejné chování pro vnitřní implementaci v `_Hash_seq`. 

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
        {   // fold in another byte
        result ^= (size_t)first[next];
        result *= fnv_prime;
        }
    return (result);
}
```  
  
## <a name="see-also"></a>Viz také:  
  
[Upgrade projektů z dřívějších verzí Visual C++](upgrading-projects-from-earlier-versions-of-visual-cpp.md)<br/>
[Přehled potenciálních problémů s upgradem (Visual C++)](overview-of-potential-upgrade-issues-visual-cpp.md)<br/>
[Upgrade kódu na Universal CRT](upgrade-your-code-to-the-universal-crt.md)  