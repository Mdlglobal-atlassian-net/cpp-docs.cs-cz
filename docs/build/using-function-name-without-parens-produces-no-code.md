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

Pokud je název funkce deklarovaný v programu použit bez závorek, kompilátor nevytvoří kód. K tomu dochází bez ohledu na to, zda funkce přebírá parametry, protože kompilátor vypočítá adresu funkce; Protože však operátor volání funkce "()" není k dispozici, volání není provedeno. Výsledek je podobný následujícímu:

```
// compile with /Wall to generate a warning
int a;
a;      // no code generated here either
```

V Visual C++ ani pomocí úrovně upozornění 4 negeneruje výstup diagnostiky. Není vydáno žádné upozornění; není vytvořen žádný kód.

Vzorový kód níže kompiluje (s upozorněním) a správně odkazuje bez chyb, ale nevytváří v referenci odkaz na `funcn( )`. Aby to fungovalo správně, přidejte operátor volání funkce "()".

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

## <a name="see-also"></a>Viz také

[Optimalizace kódu](optimizing-your-code.md)
