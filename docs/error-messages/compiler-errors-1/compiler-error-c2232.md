---
title: Chyba kompilátoru C2232 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2232
dev_langs:
- C++
helpviewer_keywords:
- C2232
ms.assetid: 76f302b7-30a7-4a81-9a39-b4edde33b54c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c0e7c20de3de097fc09b80459e96158282ef7bba
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46026046"
---
# <a name="compiler-error-c2232"></a>Chyba kompilátoru C2232

"->: levý operand má"klíč třídy "typu, použijte"."

Operand na levé straně `->` operátor není ukazatel. Použití operátoru tečka (.) pro třídy, struktury nebo sjednocení.

Následující ukázka generuje C2232:

```
// C2232.c
struct X {
    int member;
} x, *px;
int main() {
    x->member = 0;   // C2232, x is not a pointer

    px->member = 0;
    x.member = 0;
}
```