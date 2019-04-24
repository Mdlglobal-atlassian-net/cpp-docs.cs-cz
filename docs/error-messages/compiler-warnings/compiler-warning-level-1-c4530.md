---
title: Kompilátor upozornění (úroveň 1) C4530
ms.date: 11/04/2016
f1_keywords:
- C4530
helpviewer_keywords:
- C4530
ms.assetid: a04dcdb2-84db-459d-9e5e-4e743887465f
ms.openlocfilehash: a542f9b6bb73e561592e1e779aa6ee493612e6ac
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62160715"
---
# <a name="compiler-warning-level-1-c4530"></a>Kompilátor upozornění (úroveň 1) C4530

Obslužná rutina výjimky C++, které používá, ale sémantiku odvíjení nejsou povolené. Zadejte/EHsc

Zpracování výjimek jazyka C++ se použil, ale [/EHsc](../../build/reference/eh-exception-handling-model.md) nebyla vybrána.

Když není povolená možnost/EHsc, nebude objekt s automatickým úložištěm v rámci mezi způsobem throw funkce a funkce zachytávání throw, zničeny. Ale v vytvoří objekt s automatickým úložištěm **zkuste** nebo **catch** zničí bloku.

Následující ukázka generuje C4530:

```
// C4530.cpp
// compile with: /W1
int main() {
   try{} catch(int*) {}   // C4530
}
```

Příklad s/EHsc k vyřešení upozornění kompilace.