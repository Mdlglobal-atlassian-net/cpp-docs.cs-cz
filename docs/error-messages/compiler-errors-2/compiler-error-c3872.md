---
title: Chyba kompilátoru C3872
ms.date: 11/04/2016
f1_keywords:
- C3872
helpviewer_keywords:
- C3872
ms.assetid: 519e95be-5641-40cc-894c-da4819506604
ms.openlocfilehash: f4b116729ad3b84014d202deb31ab490435fcef3
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761439"
---
# <a name="compiler-error-c3872"></a>Chyba kompilátoru C3872

char: Tento znak není v identifikátoru povolený.

C++ Kompilátor následuje Standard c++ 11 na znacích povolených v identifikátoru. V identifikátoru jsou povoleny pouze určité rozsahy znaků a názvy univerzálních znaků. Další omezení se vztahují na počáteční znak identifikátoru. Další informace a seznam povolených znaků a univerzální rozsah názvů znaků naleznete v tématu [identifikátory](../../cpp/identifiers-cpp.md).

Rozsah znaků povolených v identifikátoru je méně omezující při kompilování C++kódu/CLI. Identifikátory v kódu zkompilované pomocí/CLR by měly splňovat [Standard ECMA-335: Common Language Infrastructure (CLI)](https://www.ecma-international.org/publications/standards/Ecma-335.htm).

Následující ukázka generuje C3872:

```cpp
// C3872.cpp
int main() {
   int abc_\u0040;   // C3872, U+0040 is in base char set
   int abc_\u3001;   // C3872, U+3001 is not in allowed range
   int \u30A2_abc_\u3042;   // OK, UCNs in allowed range
}
```
