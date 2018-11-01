---
title: Chyba kompilátoru C2710
ms.date: 11/04/2016
f1_keywords:
- C2710
helpviewer_keywords:
- C2710
ms.assetid: a2a6bb5b-86ad-4a6c-acd0-e2bef8464e0e
ms.openlocfilehash: 54d501d43652bb8e54092d44042a9525ef6f708f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50618943"
---
# <a name="compiler-error-c2710"></a>Chyba kompilátoru C2710

"vytvořit": "__declspec(modifier)" může používat jedině pro funkci vracející ukazatel

Pouze konstrukce, ke kterému je funkce, vrácená hodnota je ukazatel `modifier` lze použít.

Následující ukázka generuje C2710:

```
// C2710.cpp
__declspec(restrict) void f();   // C2710
// try the following line instead
__declspec(restrict) int * g();
```