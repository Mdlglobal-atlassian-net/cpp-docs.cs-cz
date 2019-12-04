---
title: Chyba kompilátoru C2791
ms.date: 11/04/2016
f1_keywords:
- C2791
helpviewer_keywords:
- C2791
ms.assetid: 938ad1fb-75d9-4ce2-ad92-83d6249005b5
ms.openlocfilehash: d589094f117135474d1a8788867d2d571bbb5f5d
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74739542"
---
# <a name="compiler-error-c2791"></a>Chyba kompilátoru C2791

Neplatné použití metody super: Class nemá žádné základní třídy.

Klíčové slovo [Super](../../cpp/super.md) bylo použito v kontextu členské funkce třídy, která nemá žádné základní třídy.

Následující ukázka generuje C2791:

```cpp
// C2791.cpp
struct D {
   void mf() {
      __super::mf();   // C2791
   }
};
```
