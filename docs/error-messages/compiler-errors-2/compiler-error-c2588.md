---
title: Chyba kompilátoru C2588
ms.date: 11/04/2016
f1_keywords:
- C2588
helpviewer_keywords:
- C2588
ms.assetid: 19a0cabd-ca13-44a5-9be3-ee676abf9bc4
ms.openlocfilehash: f1f73e2585606e7e86213607a96ef713345419c1
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755405"
---
# <a name="compiler-error-c2588"></a>Chyba kompilátoru C2588

':: ~ identifier ': Neplatný globální destruktor

Destruktor je definován pro jinou než třídu, strukturu nebo sjednocení. Toto není povoleno.

Tato chyba může být způsobena chybějící třídou, strukturou nebo názvem sjednocení na levé straně operátoru překladu oboru (`::`).

Následující ukázka generuje C2588:

```cpp
// C2588.cpp
~F();   // C2588
```
