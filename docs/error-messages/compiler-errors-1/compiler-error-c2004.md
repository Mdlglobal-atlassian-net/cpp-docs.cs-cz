---
title: Chyba kompilátoru C2004
ms.date: 11/04/2016
f1_keywords:
- C2004
helpviewer_keywords:
- C2004
ms.assetid: d81526dd-3a00-4593-87b0-d910d3d29bca
ms.openlocfilehash: fb100d977188cd3a7d5b0ebbb3e29b53942871dc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50452003"
---
# <a name="compiler-error-c2004"></a>Chyba kompilátoru C2004

Očekávalo se: defined(id).

Identifikátor musí být uvedena v závorkách za klíčové slovo preprocesoru.

Tato chyba může být také generovány jako důsledek kompilátoru prací, které bylo provedeno pro Visual Studio .NET 2003: chybějící závorka v direktivě preprocesoru. Pokud chybí pravá závorka direktivy preprocesoru, kompilátor vygeneruje chybu.

## <a name="example"></a>Příklad

Následující ukázka generuje C2004:

```
// C2004.cpp
// compile with: /DDEBUG
#include <stdio.h>

int main()
{
    #if defined(DEBUG   // C2004
        printf_s("DEBUG defined\n");
    #endif
}
```

## <a name="example"></a>Příklad

Možná řešení:

```
// C2004b.cpp
// compile with: /DDEBUG
#include <stdio.h>

int main()
{
    #if defined(DEBUG)
        printf_s("DEBUG defined\n");
    #endif
}
```