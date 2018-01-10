---
title: "Opravte svoje závislosti na knihovně internals | Microsoft Docs"
ms.custom: 
ms.date: 05/24/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- library internals in an upgraded Visual C++ project
- _Hash_seq in an upgraded Visual C++ project
ms.assetid: 493e0452-6ecb-4edc-ae20-b6fce2d7d3c5
caps.latest.revision: "1"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e6bd85de7c5235dcee0547e982d10a7abde954d0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="fix-your-dependencies-on-library-internals"></a>Opravte svoje závislosti na interní informace o knihovny

Microsoft publikuje zdrojový kód pro standardní knihovnu většinu běhové knihovny jazyka C a další knihovny Microsoft v mnoha verzí sady Visual Studio. Účelem je, které vám pomohou pochopit chování knihovny a ladění kódu. Jeden vedlejším účinkem publikování knihovny zdrojový kód je, že některé interní hodnoty, datové struktury a funkce jsou zveřejněné, i když nejsou součástí knihovny rozhraní. Obvykle mají názvy, které začínají dvě podtržítka nebo podtržítkem následuje velké písmeno, názvy, které si vyhrazuje C++ Standard do implementace. Tyto hodnoty, struktur a funkce jsou podrobnosti implementace, které mohou změnit knihovny v průběhu času vyvíjejí, a proto důrazně doporučujeme před přepnutím všechny závislosti na nich. Pokud tak učiníte, riskujete, že kód není přenositelností a problémy při pokusu o migraci kódu do nové verze knihoven.  

Ve většině případů co je nového nebo nejnovější změny dokumentu pro jednotlivé verze sady Visual Studio nepodporuje zmínili změny internals knihovny. Můžete se neměl mít vliv tyto podrobnosti implementace. Ale někdy riziko použít nějaký kód, který se zobrazí v knihovně je příliš velký. Toto téma popisuje závislosti na internals CRT nebo standardní knihovny, které jste se může mít spoléhali na a jak se bude aktualizovat váš kód k odebrání těchto závislostí, můžete provést víc přenosného nebo migrovat na nové verze knihovny.

## <a name="hashseq"></a>_Hash_seq  

Interní hodnota hash funkce `std::_Hash_seq(const unsigned char *, size_t)`používané k implementaci `std::hash` na některé typy řetězce byla viditelná v posledních verzích standardní knihovny. Tuto funkci implementovat [FNV 1a hash]( https://en.wikipedia.org/wiki/Fowler%E2%80%93Noll%E2%80%93Vo_hash_function) na posloupnost znaků.  
  
Chcete-li odebrat tuto závislost, máte několik možností.  

-   Pokud vaše záměr je uvést `const char *` pořadí do kontejner neuspořádaný pomocí stejné stroje kód hash jako `basic_string`, můžete to udělat pomocí `std::hash` šabloně přetížení, které přijímá `std::string_view`, která vrací tento kód hash v přenosný způsob. Kód knihovny řetězec může nebo nemusí spoléhají na použití algoritmus hash FNV 1a v budoucnu, tak toto je nejlepší způsob, jak se vyhnout závislost na konkrétní šifrovací algoritmus, který. 
  
-   Pokud vaše záměrem generovat algoritmus hash FNV 1a přes libovolný paměti, jsme provedli tento kód k dispozici na Githubu v [VCSamples]( https://github.com/Microsoft/vcsamples) úložiště v samostatné záhlaví souboru, [fnv1a.hpp](https://github.com/Microsoft/VCSamples/tree/master/VC2015Samples/_Hash_seq), v části [Licencí MIT](https://github.com/Microsoft/VCSamples/blob/master/license.txt). Také jsme zahrnuli kopie sem pro usnadnění vaší práce. Tento kód můžete zkopírovat do souboru záhlaví, přidat hlavičku do ovlivněného kódu, najít a nahradit `_Hash_seq` podle `fnv1a_hash_bytes`. Získáte stejné chování interní implementaci v `_Hash_seq`. 

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
  
## <a name="see-also"></a>Viz také  
  
[Upgrade projektů z dřívějších verzí Visual C++](upgrading-projects-from-earlier-versions-of-visual-cpp.md)  
[Přehled potenciálních problémů s upgradem (Visual C++)](overview-of-potential-upgrade-issues-visual-cpp.md)  
[Upgrade kódu na Universal CRT](upgrade-your-code-to-the-universal-crt.md)  
