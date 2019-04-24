---
title: Chyba kompilátoru C2706
ms.date: 11/04/2016
f1_keywords:
- C2706
helpviewer_keywords:
- C2706
ms.assetid: e18da924-c42d-4b09-8e29-f4e0382d7dc6
ms.openlocfilehash: 9767d36d44b99423d600d299d0803901d3dbfec5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62161105"
---
# <a name="compiler-error-c2706"></a>Chyba kompilátoru C2706

Neplatná možnost __except bez odpovídající \__try (chybějící '}' v \__try bloku?)

Kompilátor nenalezl pravé složené závorky pro `__try` bloku.

Následující ukázka generuje C2706:

```
// C2706.cpp
int main() {
   __try {
      void f();
   // C2706  } missing here
   __except(GetExceptionCode() == 0x0) {
   }
}
```