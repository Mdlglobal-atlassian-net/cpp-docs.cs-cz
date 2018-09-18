---
title: Upozornění (úroveň 1) C4551 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4551
dev_langs:
- C++
helpviewer_keywords:
- C4551
ms.assetid: 458b59bd-e2d7-425f-9ba6-268ff200424f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5dc8852ccaee1d2b07fbf35e57885b863afef921
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46075563"
---
# <a name="compiler-warning-level-1-c4551"></a>Kompilátor upozornění (úroveň 1) C4551

Chybí seznam argumentů funkce volání

Volání funkce musí obsahovat otevírací a uzavírací závorka za názvem funkce, i v případě, funkce nepřebírá žádné parametry.

Následující ukázka generuje C4551:

```
// C4551.cpp
// compile with: /W1
void function1() {
}

int main() {
   function1;   // C4551
   function1();   // OK
}
```