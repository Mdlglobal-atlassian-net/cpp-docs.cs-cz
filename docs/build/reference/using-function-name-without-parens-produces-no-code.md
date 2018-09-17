---
title: Použití názvu funkce bez () nevygeneruje žádný kód | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- functions [C++], without parentheses
ms.assetid: edf4a177-a160-44aa-8436-e077b5b27809
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 13ca43386c9ef46f526538781a91fd1a81ade537
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45710577"
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

## <a name="see-also"></a>Viz také

[Optimalizace kódu](../../build/reference/optimizing-your-code.md)