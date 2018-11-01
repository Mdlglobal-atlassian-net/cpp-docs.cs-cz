---
title: Chyba kompilátoru C2166
ms.date: 11/04/2016
f1_keywords:
- C2166
helpviewer_keywords:
- C2166
ms.assetid: 12789c3a-cc76-48bb-ae2e-64283e0964ed
ms.openlocfilehash: 36b4bcbd3eda213b840194cb635172a241f04b14
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50572793"
---
# <a name="compiler-error-c2166"></a>Chyba kompilátoru C2166

l-value specifikuje objekt const

Kód se pokusí upravit položky deklarované `const`.

Následující ukázka generuje C2166:

```
// C2166.cpp
int f();
int main() {
   ( (const int&) 1 ) = 5;   // C2166
}
```