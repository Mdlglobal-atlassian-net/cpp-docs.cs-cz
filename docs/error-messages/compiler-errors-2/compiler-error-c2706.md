---
title: Chyba kompilátoru C2706
ms.date: 11/04/2016
f1_keywords:
- C2706
helpviewer_keywords:
- C2706
ms.assetid: e18da924-c42d-4b09-8e29-f4e0382d7dc6
ms.openlocfilehash: bca86d3c0cf886c64a1d668468c793d0e77b2867
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757459"
---
# <a name="compiler-error-c2706"></a>Chyba kompilátoru C2706

neplatné __except bez odpovídajícího \__try (v bloku \__try chybí znak})

Kompilátor nenalezl pravou složenou závorku pro `__try` blok.

Následující ukázka generuje C2706:

```cpp
// C2706.cpp
int main() {
   __try {
      void f();
   // C2706  } missing here
   __except(GetExceptionCode() == 0x0) {
   }
}
```
