---
title: Kompilátor upozornění (úroveň 1) C4393
ms.date: 11/04/2016
f1_keywords:
- C4393
helpviewer_keywords:
- C4393
ms.assetid: 353a0539-d1ea-4c1b-8849-c9b321ec9842
ms.openlocfilehash: 21ea45963c7e3d2afe74ebf4aa5207629ec9c8db
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50594246"
---
# <a name="compiler-warning-level-1-c4393"></a>Kompilátor upozornění (úroveň 1) C4393

'příkaz var': const nemá žádný vliv na literální datový člen; Ignorovat

A [literálu](../../windows/literal-cpp-component-extensions.md) datový člen také byla zadána jako konstanta.  Protože literální datový člen znamená const, nepotřebujete přidat const deklarace.

Následující ukázka generuje C4393:

```
// C4393.cpp
// compile with: /clr /W1 /c
ref struct Y1 {
   literal const int staticConst = 10;   // C4393
   literal int staticConst2 = 10;   // OK
};
```