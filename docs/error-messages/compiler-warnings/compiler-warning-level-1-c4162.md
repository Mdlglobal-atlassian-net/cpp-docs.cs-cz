---
title: Kompilátor upozornění (úroveň 1) C4162
ms.date: 11/04/2016
f1_keywords:
- C4162
helpviewer_keywords:
- C4162
ms.assetid: 21ae3c92-501d-4689-ad7d-13753cb65eff
ms.openlocfilehash: 6c6b675fd47cb6e98255515c7cd77c6dd48ea02b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50578262"
---
# <a name="compiler-warning-level-1-c4162"></a>Kompilátor upozornění (úroveň 1) C4162

'identifier': žádná funkce s C-linkage nalezen

Funkce s C-linkage je deklarovaná, ale nebyl nalezen.

Pokud chcete vyřešit toto upozornění, kompilaci v souboru .c (vyvolání kompilátor jazyka C).  Pokud je nutné vyvolat kompilátor C++, umístěte před deklarací funkce extern "C".

Následující ukázka generuje C4162

```
// C4162.cpp
// compile with: /c /W1
unsigned char _bittest(long* a, long b);
#pragma intrinsic (_bittest)   // C4162

int main() {
   bool bit;
   long num = 78002;
   bit = _bittest(&num, 5);
}
```

Možná řešení:

```
// C4162b.cpp
// compile with: /c
extern "C"
unsigned char _bittest(long* a, long b);
#pragma intrinsic (_bittest)

int main() {
   bool bit;
   long num = 78002;
   bit = _bittest(&num, 5);
}
```