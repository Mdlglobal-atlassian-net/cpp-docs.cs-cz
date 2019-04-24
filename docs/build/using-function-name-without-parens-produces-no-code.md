---
title: Použití názvu funkce bez závorek () nevygeneruje žádný kód
ms.date: 11/04/2016
helpviewer_keywords:
- functions [C++], without parentheses
ms.assetid: edf4a177-a160-44aa-8436-e077b5b27809
ms.openlocfilehash: 51be77dc8f4fe072ea6cc46dd51e38862649feda
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62314595"
---
# <a name="using-function-name-without--produces-no-code"></a>Použití názvu funkce bez závorek () nevygeneruje žádný kód

Při použití názvu funkce deklarované ve svém programu bez závorek kompilátor nevytvoří kódu. K tomu dojde bez ohledu na to, jestli funkce má parametry, protože kompilátor vypočítá adresa funkce; ale vzhledem k tomu, že operátor volání funkce "()" není k dispozici, žádný Přišla žádost. Tento výsledek je podobný následujícímu:

```
// compile with /Wall to generate a warning
int a;
a;      // no code generated here either
```

V jazyce Visual C++ dokonce i pomocí úroveň upozornění 4 generuje žádný výstup diagnostiky. Objeví se bez upozornění; není vytvořen žádný kód.

Níže uvedený ukázkový kód (s upozorněním) zkompiluje a propojí správně bez chyb ale nevygeneruje žádný kód v reference na `funcn( )`. Aby to fungovalo správně přidejte operátor volání funkce "()".

```
#include <stdio.h>
void funcn();

int main() {
   funcn;      /* missing function call operator;
                  call will fail.  Use funcn() */
   }

void funcn() {
   printf("\nHello World\n");
}
```

## <a name="see-also"></a>Viz také:

[Optimalizace kódu](optimizing-your-code.md)
