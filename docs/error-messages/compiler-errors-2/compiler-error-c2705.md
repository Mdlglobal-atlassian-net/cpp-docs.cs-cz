---
title: Chyba kompilátoru C2705 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2705
dev_langs:
- C++
helpviewer_keywords:
- C2705
ms.assetid: 29249ea3-4ea7-4105-944b-bdb83e8d6852
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1c0eefd19645ee6ac06664249f7953d904cd5896
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46093698"
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