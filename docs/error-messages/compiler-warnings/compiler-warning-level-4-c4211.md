---
title: Upozornění kompilátoru (úroveň 4) C4211
ms.date: 11/04/2016
f1_keywords:
- C4211
helpviewer_keywords:
- C4211
ms.assetid: 3eea3455-6faa-4cdb-8730-73db7026bd1f
ms.openlocfilehash: 6387f58430098e49e7add25e8915bf6b181634e9
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541834"
---
# <a name="compiler-warning-level-4-c4211"></a>Upozornění kompilátoru (úroveň 4) C4211

používá se nestandardní rozšíření: předefinované extern na static.

S výchozími rozšířeními Microsoft (/ze) můžete předefinovat identifikátor `extern` jako **statický**.

## <a name="example"></a>Příklad

```c
// C4211.c
// compile with: /W4
extern int i;
static int i;   // C4211

int main()
{
}
```

Tato předefinování nejsou v rámci kompatibility ANSI ([/za](../../build/reference/za-ze-disable-language-extensions.md)) platná.
