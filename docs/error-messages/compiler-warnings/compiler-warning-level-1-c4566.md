---
title: Kompilátor upozornění (úroveň 1) C4566
ms.date: 11/04/2016
f1_keywords:
- C4566
helpviewer_keywords:
- C4566
ms.assetid: 65f40730-e86f-447c-b37b-16caadcfe311
ms.openlocfilehash: c864feb2478e9f99ad6e4c0087dcef72b55de601
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50460265"
---
# <a name="compiler-warning-level-1-c4566"></a>Kompilátor upozornění (úroveň 1) C4566

znak reprezentován universal-character-name 'char' nemůže být reprezentovaný v aktuální znakové stránce (stránky)

Každý znak Unicode lze znázornit v aktuální znakové stránce ANSI.

Úzký řetězce (jeden bajtové znaků), jsou převedeny na vícebajtové znaky vzhledem k tomu jsou velké řetězce (dvoubajtové znaky) není.

Následující ukázka generuje C4566:

```
// C4566.cpp
// compile with: /W1
int main() {
   char c1 = '\u03a0';   // C4566
   char c2 = '\u0642';   // C4566

   wchar_t c3 = L'\u03a0';   // OK
   wchar_t c4 = L'\u0642';   // OK
}
```