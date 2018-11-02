---
title: Chyba kompilátoru C2705
ms.date: 11/04/2016
f1_keywords:
- C2705
helpviewer_keywords:
- C2705
ms.assetid: 29249ea3-4ea7-4105-944b-bdb83e8d6852
ms.openlocfilehash: 872471158d3f8c301a271dd68b2ef36839e2b9c5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50616268"
---
# <a name="compiler-error-c2705"></a>Chyba kompilátoru C2705

"štítek": Neplatný skok na obor bloku obsluhy výjimky

Spuštění přejde na popisek v rámci `try` / `catch`, `__try` / `__except`, `__try` / `__finally` bloku. Další informace najdete v tématu [zpracování výjimek](../../cpp/exception-handling-in-visual-cpp.md).

Následující ukázka generuje C2705:

```
// C2705.cpp
int main() {
goto trouble;
   __try {
      trouble: ;   // C2705
   }
   __finally {}

   // try the following line instead
   // trouble: ;
}
```