---
title: Chyba kompilátoru C2705
ms.date: 11/04/2016
f1_keywords:
- C2705
helpviewer_keywords:
- C2705
ms.assetid: 29249ea3-4ea7-4105-944b-bdb83e8d6852
ms.openlocfilehash: 1cd46db8e4cb237bebd9568409ecadf0ff84cdf8
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758304"
---
# <a name="compiler-error-c2705"></a>Chyba kompilátoru C2705

Label: neplatný skok do oboru bloku obslužných rutin výjimek

Provedení přejde na popisek v rámci `try`/`catch`, `__try`/`__except`, `__try`/`__finally` bloku. Další informace naleznete v tématu [zpracování výjimek](../../cpp/exception-handling-in-visual-cpp.md).

Následující ukázka generuje C2705:

```cpp
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
