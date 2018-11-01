---
title: Kompilátor upozornění (úroveň 1) C4218
ms.date: 11/04/2016
f1_keywords:
- C4218
helpviewer_keywords:
- C4218
ms.assetid: d6c3cd90-4518-49e9-ae86-4ba9e2761d98
ms.openlocfilehash: 36d5de3b1270b41edfc391df960a556aca207709
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50555295"
---
# <a name="compiler-warning-level-1-c4218"></a>Kompilátor upozornění (úroveň 1) C4218

používá se nestandardní rozšíření: musíte zadat alespoň jednu třídu úložiště nebo typu

Pomocí rozšíření výchozí společnosti Microsoft (/Ze) můžete deklarovat proměnné bez zadání třídy typu nebo úložiště. Výchozí typ je `int`.

## <a name="example"></a>Příklad

```
// C4218.c
// compile with: /W4
i;  // C4218

int main()
{
}
```

Těchto prohlášení nejsou platné v rámci kompatibility ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)).