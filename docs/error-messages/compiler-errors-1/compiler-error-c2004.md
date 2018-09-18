---
title: Chyba kompilátoru C2004 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2004
dev_langs:
- C++
helpviewer_keywords:
- C2004
ms.assetid: d81526dd-3a00-4593-87b0-d910d3d29bca
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b560ef96c4fadcb7c5ce57ece13647032ca9e902
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46118749"
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