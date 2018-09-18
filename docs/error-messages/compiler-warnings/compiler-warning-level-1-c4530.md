---
title: Upozornění (úroveň 1) C4530 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4530
dev_langs:
- C++
helpviewer_keywords:
- C4530
ms.assetid: a04dcdb2-84db-459d-9e5e-4e743887465f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bbfbc67377dd48eeb692bdd4cac1f113fbdf7f6a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46110455"
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