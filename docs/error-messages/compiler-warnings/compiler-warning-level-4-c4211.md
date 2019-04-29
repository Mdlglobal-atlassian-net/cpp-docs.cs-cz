---
title: Kompilátor upozornění (úroveň 4) C4211
ms.date: 11/04/2016
f1_keywords:
- C4211
helpviewer_keywords:
- C4211
ms.assetid: 3eea3455-6faa-4cdb-8730-73db7026bd1f
ms.openlocfilehash: 6d61191c4a7ed950d979158ccdfa3a390439b019
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401134"
---
# <a name="compiler-warning-level-4-c4211"></a>Kompilátor upozornění (úroveň 4) C4211

používá se nestandardní rozšíření: možnost extern se předefinovala na static

Pomocí rozšíření výchozí společnosti Microsoft (/Ze), můžete změnit `extern` identifikátor jako **statické**.

## <a name="example"></a>Příklad

```
// C4211.c
// compile with: /W4
extern int i;
static int i;   // C4211

int main()
{
}
```

Tato redefinice nejsou platné v rámci kompatibility ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)).
