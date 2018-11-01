---
title: Kompilátor upozornění (úroveň 1) C4627
ms.date: 09/09/2018
f1_keywords:
- C4627
helpviewer_keywords:
- C4627
ms.assetid: 8840f3e6-b496-423a-8635-eb55d5f854a2
ms.openlocfilehash: e833141020de1aef51a1ea3823dea86b024e077d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50542386"
---
# <a name="compiler-warning-level-1-c4627"></a>Kompilátor upozornění (úroveň 1) C4627

> "*header_file*': při hledání použití předkompilované hlavičky přeskočen

Pokud má aktuálního zdrojového souboru [/Yu \(použijte soubor předkompilované hlavičky)](../../build/reference/yu-use-precompiled-header-file.md) možnosti set, pak Kompilátor ignoruje všechno v souboru dříve, než je zahrnuté předkompilované hlavičky. Upozornění **C4627** generováno v sadě Visual Studio 2015 a starší, pokud *header_file* zahrnuté před předkompilovaného souboru hlaviček, a pokud Předkompilovaná hlavička neobsahuje také *header_file*.

## <a name="example"></a>Příklad

Tato ukázka předvádí, jak k chybě může dojít a ukazuje, jak ho opravit:

```cpp
// c4627.cpp
#include <iostream>       // C4627 - iostream not included by pch.h
#include "pch.h"          // precompiled header file that does not include iostream
// #include <iostream>    // To fix, move the iostream header include here from above
int main()
{
    std::cout << "std::cout is defined!\n";
}
```

## <a name="see-also"></a>Viz také

[Vytváření předkompilovaných hlavičkových souborů](../../build/reference/creating-precompiled-header-files.md)
