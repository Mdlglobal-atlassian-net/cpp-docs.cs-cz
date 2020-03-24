---
title: Upozornění kompilátoru (úroveň 1) C4805
ms.date: 11/04/2016
f1_keywords:
- C4805
helpviewer_keywords:
- C4805
ms.assetid: 99c7b7e2-272e-4ab5-8580-17c42e62e2ef
ms.openlocfilehash: c724af59b0654ae0f212eea038c48cb57f991aa3
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175061"
---
# <a name="compiler-warning-level-1-c4805"></a>Upozornění kompilátoru (úroveň 1) C4805

' operation ': potenciálně nebezpečné kombinace typu ' type ' a typu ' type ' v operaci

Toto upozornění je vygenerováno pro porovnání operací mezi [bool](../../cpp/bool-cpp.md) a [int](../../c-language/integer-types.md). Následující ukázka generuje C4805:

```cpp
// C4805.cpp
// compile with: /W1
int main() {
   int i = 1;
   bool b = true;

   if (i == b) {   // C4805, comparing bool and int variables
   }
}
```
