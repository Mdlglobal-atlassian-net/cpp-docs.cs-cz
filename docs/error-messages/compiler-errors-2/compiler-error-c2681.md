---
title: Chyba kompilátoru C2681 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2681
dev_langs:
- C++
helpviewer_keywords:
- C2681
ms.assetid: eb42da6d-8d2c-43fd-986b-e73e2b004885
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7a0f0ab4b9c6a2dd2ae69f0370f808e32e496b97
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46059079"
---
# <a name="compiler-error-c2681"></a>Chyba kompilátoru C2681

'type': Neplatný typ výrazu pro název

Operátor přetypování se pokusil převést z neplatného typu. Například, pokud použijete [dynamic_cast](../../cpp/dynamic-cast-operator.md) operátor převodu výrazu na typ ukazatele, zdrojový výraz musí být ukazatel.

Následující ukázka generuje C2681:

```
// C2681.cpp
class A { virtual void f(); };

void g(int i) {
    A* pa;
    pa = dynamic_cast<A*>(i);  // C2681
}
```