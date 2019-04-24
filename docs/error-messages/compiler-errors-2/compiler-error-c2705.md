---
title: Chyba kompilátoru C2705
ms.date: 11/04/2016
f1_keywords:
- C2705
helpviewer_keywords:
- C2705
ms.assetid: 29249ea3-4ea7-4105-944b-bdb83e8d6852
ms.openlocfilehash: 872471158d3f8c301a271dd68b2ef36839e2b9c5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62161160"
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