---
title: Chyba kompilátoru C2400
ms.date: 11/04/2016
f1_keywords:
- C2400
helpviewer_keywords:
- C2400
ms.assetid: 1ba441ee-73f9-42a5-bfe9-fbeab93808eb
ms.openlocfilehash: 3ede43ec5ddb61b85c48094193d01d18bacae2bc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50667178"
---
# <a name="compiler-error-c2400"></a>Chyba kompilátoru C2400

Chyba syntaxe vloženého assembleru v "context"; Najít "token"

Token, který způsobil chybu syntaxe v zadaném kontextu.

Následující ukázka generuje C2400:

```
// C2400.cpp
// processor: x86
int main() {
   __asm {
      heh ax,bx;   // C2400, heh is not a valid x86 instruction
      mov ax,bx;   // OK
   }
}
```