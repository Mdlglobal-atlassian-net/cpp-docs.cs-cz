---
title: Kompilátor upozornění (úroveň 4) C4431
ms.date: 11/04/2016
f1_keywords:
- C4431
helpviewer_keywords:
- C4431
ms.assetid: 58434ab6-dd8d-427b-953a-602fb7453ae6
ms.openlocfilehash: 6a07a9ffa938d9372ebed9676847b3274115d526
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2019
ms.locfileid: "65447018"
---
# <a name="compiler-warning-level-4-c4431"></a>Kompilátor upozornění (úroveň 4) C4431

chybějící specifikátor typu: předpokládá se int Poznámka: C už nepodporuje typ default int.

Tuto chybu mohou být generovány jako důsledek kompilátoru prací, které bylo provedeno pro Visual Studio 2005: Vizuální C++ už ve výchozím nastavení vytvoří jako int netypové identifikátory. Typ identifikátoru musí explicitně zadán.

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