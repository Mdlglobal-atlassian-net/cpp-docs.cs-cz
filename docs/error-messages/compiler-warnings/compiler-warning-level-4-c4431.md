---
title: Kompilátor upozornění (úroveň 4) C4431
ms.date: 11/04/2016
f1_keywords:
- C4431
helpviewer_keywords:
- C4431
ms.assetid: 58434ab6-dd8d-427b-953a-602fb7453ae6
ms.openlocfilehash: 1cef70ab02148924bf6a0f29e298b34c54b28bc4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50624325"
---
# <a name="compiler-warning-level-4-c4431"></a>Kompilátor upozornění (úroveň 4) C4431

chybějící specifikátor typu: předpokládá se int Poznámka: C již nepodporuje výchozí int.

Tuto chybu mohou být generovány jako důsledek kompilátoru prací, které bylo provedeno pro Visual C++ 2005: Visual C++ již netypové identifikátory jako int ve výchozím nastavení vytvoří. Typ identifikátoru musí explicitně zadán.

Toto upozornění je vypnuto ve výchozím nastavení. Zobrazit [kompilátoru upozornění, že je vypnuto ve výchozím nastavení](../../preprocessor/compiler-warnings-that-are-off-by-default.md) Další informace.

## <a name="example"></a>Příklad

Následující ukázka generuje C4431.

```
// C4431.c
// compile with: /c /W4
#pragma warning(default:4431)
i;   // C4431
int i;   // OK
```