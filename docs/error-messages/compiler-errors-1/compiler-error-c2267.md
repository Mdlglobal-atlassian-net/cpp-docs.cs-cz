---
title: Chyba kompilátoru C2267
ms.date: 11/04/2016
f1_keywords:
- C2267
helpviewer_keywords:
- C2267
ms.assetid: ea63bebb-6208-4367-8440-39be07f9c360
ms.openlocfilehash: c897f8e6b38743ee98ec29707b222901ddde9d7c
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758733"
---
# <a name="compiler-error-c2267"></a>Chyba kompilátoru C2267

' function ': statické funkce s oborem bloku jsou neplatné

Místní funkce je deklarována `static`. Statické funkce musí mít globální obor.

Následující ukázka generuje C2267:

```cpp
// C2267.cpp
static int func2();   // OK
int main() {
    static int func1();   // C2267
}
```
