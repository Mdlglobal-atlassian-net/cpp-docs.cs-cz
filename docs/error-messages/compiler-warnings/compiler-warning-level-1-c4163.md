---
title: Upozornění kompilátoru (úroveň 1) C4163
ms.date: 11/04/2016
f1_keywords:
- C4163
helpviewer_keywords:
- C4163
ms.assetid: b08413fd-03fc-4f41-9167-a98976ac12f2
ms.openlocfilehash: 492fe4a75b4ddf9b5f78810226f14aa84ab2b56a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80176127"
---
# <a name="compiler-warning-level-1-c4163"></a>Upozornění kompilátoru (úroveň 1) C4163

' identifier ': není k dispozici jako vnitřní funkce

Zadanou funkci nelze použít jako [vnitřní](../../preprocessor/intrinsic.md) funkci. Kompilátor ignoruje neplatný název funkce.

Následující ukázka generuje C4163:

```cpp
// C4163.cpp
// compile with: /W1 /LD
#include <math.h>
#pragma intrinsic(mysin)   // C4163
// try the following line instead
// #pragma intrinsic(sin)
```
