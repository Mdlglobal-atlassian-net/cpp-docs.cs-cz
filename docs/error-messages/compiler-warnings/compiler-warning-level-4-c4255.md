---
title: Kompilátor upozornění (úroveň 4) C4255
ms.date: 11/04/2016
f1_keywords:
- C4255
helpviewer_keywords:
- C4255
ms.assetid: 2087b635-4b4c-4182-8a01-c26770d2bb88
ms.openlocfilehash: 1796e28e88bbe52c4c21ffdf0a8a96a278a44388
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50566631"
---
# <a name="compiler-warning-level-4-c4255"></a>Kompilátor upozornění (úroveň 4) C4255

'function': zadaný žádný prototyp funkce: převod '(') '(void).

Kompilátor nenalezl explicitní seznam argumentů funkce. Toto upozornění je pro kompilátor jazyka C.

Toto upozornění je vypnuto ve výchozím nastavení. Zobrazit [kompilátoru upozornění, že je vypnuto ve výchozím nastavení](../../preprocessor/compiler-warnings-that-are-off-by-default.md) Další informace.

Následující ukázka generuje C4255:

```
// C4255.c
// compile with: /W4 /WX
#pragma warning (default : 4255)

void f()  { // C4255
// try the following line instead
//void f(void) {
}

int main(int argc, char *argv[]) {
   f();
}
```