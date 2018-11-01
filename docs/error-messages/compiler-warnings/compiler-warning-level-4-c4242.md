---
title: Kompilátor upozornění (úroveň 4) C4242
ms.date: 11/04/2016
f1_keywords:
- C4242
helpviewer_keywords:
- C4242
ms.assetid: 8df742e1-fbf1-42f3-8e93-c0e1c222dc7e
ms.openlocfilehash: e0582f3dfdd223b4571e361dc69fae1990aeea1c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50498212"
---
# <a name="compiler-warning-level-4-c4242"></a>Kompilátor upozornění (úroveň 4) C4242

'identifier': převod z 'type1' na 'type2', možná ztráta dat

Typy se liší. Převod typu může dojít ke ztrátě dat. Kompilátor provede převod typů.

Toto upozornění je vypnuto ve výchozím nastavení. Zobrazit [kompilátoru upozornění, že je vypnuto ve výchozím nastavení](../../preprocessor/compiler-warnings-that-are-off-by-default.md) Další informace.

Další informace o C4242 najdete v tématu [běžné chyby kompilátoru](/windows/desktop/WinProg64/common-compiler-errors).

Následující ukázka generuje C4242:

```
// C4242.cpp
// compile with: /W4
#pragma warning(4:4242)
int func() {
   return 0;
}

int main() {
   char a;
   a = func();   // C4242, return type and variable type do not match
}
```