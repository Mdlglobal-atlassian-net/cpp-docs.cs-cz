---
title: Chyba kompilátoru C2537
ms.date: 11/04/2016
f1_keywords:
- C2537
helpviewer_keywords:
- C2537
ms.assetid: aee81d8e-300e-4a8b-b6c4-b3828398b34e
ms.openlocfilehash: 0dfe9f88fcdfda1325150d480670777a4d42d896
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758629"
---
# <a name="compiler-error-c2537"></a>Chyba kompilátoru C2537

' specifikátor ': Neplatná specifikace propojení

Možné příčiny:

1. Specifikátor propojení není podporován. Podporován je pouze specifikátor propojení "C".

1. Propojení "C" je zadáno pro více než jednu funkci v sadě přetížených funkcí. Toto není povoleno.

Následující ukázka generuje C2537:

```cpp
// C2537.cpp
// compile with: /c
extern "c" void func();   // C2537
extern "C" void func2();   // OK
```
