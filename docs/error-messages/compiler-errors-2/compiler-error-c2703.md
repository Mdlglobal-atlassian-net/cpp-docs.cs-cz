---
title: Chyba kompilátoru C2703
ms.date: 11/04/2016
f1_keywords:
- C2703
helpviewer_keywords:
- C2703
ms.assetid: 384295c3-643d-47ae-a9a6-865b3036aa84
ms.openlocfilehash: 7d1f50d7811fd7c54e1236499da36f00add97d70
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757147"
---
# <a name="compiler-error-c2703"></a>Chyba kompilátoru C2703

Neplatný příkaz __leave

Příkaz `__leave` musí být uvnitř bloku `__try`.

Následující ukázka generuje C2703:

```cpp
// C2703.cpp
int main() {
   __leave;   // C2703
   __try {
      // try the following line instead
      __leave;
   }
   __finally {}
}
```
