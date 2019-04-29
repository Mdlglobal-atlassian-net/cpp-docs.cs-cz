---
title: Kompilátor upozornění (úroveň 4) C4431
ms.date: 11/04/2016
f1_keywords:
- C4431
helpviewer_keywords:
- C4431
ms.assetid: 58434ab6-dd8d-427b-953a-602fb7453ae6
ms.openlocfilehash: 1cef70ab02148924bf6a0f29e298b34c54b28bc4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62391514"
---
# <a name="compiler-warning-level-4-c4431"></a>Kompilátor upozornění (úroveň 4) C4431

chybějící specifikátor typu: předpokládá se int Poznámka: C už nepodporuje typ default int.

Tato chyba je možné generovat důsledku prací kompilátoru, které bylo provedeno vizuálu C++ 2005: Vizuální C++ už ve výchozím nastavení vytvoří jako int netypové identifikátory. Typ identifikátoru musí explicitně zadán.

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