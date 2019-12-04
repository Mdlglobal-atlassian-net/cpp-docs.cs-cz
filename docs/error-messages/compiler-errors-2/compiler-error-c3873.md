---
title: Chyba kompilátoru C3873
ms.date: 11/04/2016
f1_keywords:
- C3873
helpviewer_keywords:
- C3873
ms.assetid: e68fd3be-2391-492b-ac3f-d2428901b2e9
ms.openlocfilehash: e63c3870a60194b72f1be8e1b401bbdef8fa47be
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74736721"
---
# <a name="compiler-error-c3873"></a>Chyba kompilátoru C3873

char: Tento znak není povolený jako první znak identifikátoru.

C++ Kompilátor následuje Standard c++ 11 na znacích povolených v identifikátoru. V identifikátoru jsou povoleny pouze určité rozsahy znaků a názvy univerzálních znaků. Další omezení se vztahují na počáteční znak identifikátoru. Další informace a seznam povolených znaků a univerzální rozsah názvů znaků naleznete v tématu [identifikátory](../../cpp/identifiers-cpp.md).

Rozsah znaků povolených v identifikátoru je méně omezující při kompilování C++kódu/CLI. Identifikátory v kódu zkompilované pomocí/CLR by měly splňovat [Standard ECMA-335: Common Language Infrastructure (CLI)](https://www.ecma-international.org/publications/standards/Ecma-335.htm).

Následující ukázka generuje C3873:

```cpp
// C3873.cpp
int main() {
   int \u036F_abc;   // C3873, not in allowed range for initial character
   int abc_\u036F;   // OK, in allowed range for non-initial character
}
```
