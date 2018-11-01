---
title: Upozornění linkerů LNK4254
ms.date: 11/04/2016
f1_keywords:
- LNK4254
helpviewer_keywords:
- LNK4254
ms.assetid: 6f41dfb3-ca21-40d3-bac7-b637e578efa4
ms.openlocfilehash: 2c68e49d58b0fd6b28607eb0ba78c092441f6f4b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50467012"
---
# <a name="linker-tools-warning-lnk4254"></a>Upozornění linkerů LNK4254

část sekci "1" (posun) sloučena sekci "2" (posun) s rozdílnými atributy

Obsah jeden oddíl byly sloučeny do jiné, ale atributy ze dvou částí se liší. Váš program může mít neočekávané výsledky. Například data, která chcete načíst pouze nyní v pravděpodobně oddíl s možností zápisu.

Chcete-li vyřešit LNK4254, změnit nebo odebrat požadavek sloučení.

Při cílení na x86 počítače a cíle Windows CE (ARM, MIPS, architekturu SH4 a Thumb) v jazyce Visual C++. Oddíl CRT je jen pro čtení. Pokud váš kód závisí na předchozím chování (. Oddíly CRT jsou r/w), může docházet k neočekávanému chování.

Další informace najdete v tématu,

- [/MERGE (sloučení oddílů)](../../build/reference/merge-combine-sections.md)

- [comment (C/C++)](../../preprocessor/comment-c-cpp.md)

## <a name="example"></a>Příklad

Následující ukázka generuje LNK4254.

```
// LNK4254.cpp
// compile with: /W1 /link /WX
// LNK4254 expected
#pragma comment(linker, "/merge:.data=.text")
int main() {}
```