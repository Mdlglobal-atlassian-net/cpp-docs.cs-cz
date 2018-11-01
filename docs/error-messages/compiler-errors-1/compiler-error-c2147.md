---
title: Chyba kompilátoru C2147
ms.date: 11/04/2016
f1_keywords:
- C2147
helpviewer_keywords:
- C2147
ms.assetid: d1adb3bf-7ece-4815-922c-ad7492fb6670
ms.openlocfilehash: 0a093bbbaf9cf9f72625226f949a27b681005c35
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50614484"
---
# <a name="compiler-error-c2147"></a>Chyba kompilátoru C2147

Chyba syntaxe: 'identifier' je nové klíčové slovo

Identifikátor se použil, který je teď rezervované klíčové slovo v jazyce.

Následující ukázka generuje C2147:

```
// C2147.cpp
// compile with: /clr
int main() {
   int gcnew = 0;   // C2147
   int i = 0;   // OK
}
```