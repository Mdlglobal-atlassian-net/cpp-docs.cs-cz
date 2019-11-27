---
title: Upozornění kompilátoru (úroveň 4) C4242
ms.date: 11/04/2016
f1_keywords:
- C4242
helpviewer_keywords:
- C4242
ms.assetid: 8df742e1-fbf1-42f3-8e93-c0e1c222dc7e
ms.openlocfilehash: 3123a414dc7a169d2a472dad96d659a9e56c9020
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541751"
---
# <a name="compiler-warning-level-4-c4242"></a>Upozornění kompilátoru (úroveň 4) C4242

' identifier ': převod z ' typ1 ' na ' typ2 ', možná ztráta dat

Typy se liší. Převod typu může mít za následek ztrátu dat. Kompilátor provede převod typu.

Toto upozornění je ve výchozím nastavení vypnuté. Další informace najdete v tématu [Upozornění kompilátoru, která jsou ve výchozím nastavení vypnutá](../../preprocessor/compiler-warnings-that-are-off-by-default.md) .

Další informace o C4242 najdete v tématu [běžné chyby kompilátoru](/windows/win32/WinProg64/common-compiler-errors).

Následující ukázka generuje C4242:

```cpp
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