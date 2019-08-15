---
title: Upozornění kompilátoru (úroveň 4) C4242
ms.date: 11/04/2016
f1_keywords:
- C4242
helpviewer_keywords:
- C4242
ms.assetid: 8df742e1-fbf1-42f3-8e93-c0e1c222dc7e
ms.openlocfilehash: ed145444d6eec583c448a3a49167ca1f82644f0b
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69510005"
---
# <a name="compiler-warning-level-4-c4242"></a>Upozornění kompilátoru (úroveň 4) C4242

' identifier ': převod z ' typ1 ' na ' typ2 ', možná ztráta dat

Typy se liší. Převod typu může mít za následek ztrátu dat. Kompilátor provede převod typu.

Toto upozornění je ve výchozím nastavení vypnuté. Další informace najdete v tématu [Upozornění kompilátoru, která jsou ve výchozím nastavení vypnutá](../../preprocessor/compiler-warnings-that-are-off-by-default.md) .

Další informace o C4242 najdete v tématu [běžné chyby kompilátoru](/windows/win32/WinProg64/common-compiler-errors).

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