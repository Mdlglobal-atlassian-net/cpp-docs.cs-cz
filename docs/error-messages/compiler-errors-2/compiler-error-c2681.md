---
title: Chyba kompilátoru C2681
ms.date: 11/04/2016
f1_keywords:
- C2681
helpviewer_keywords:
- C2681
ms.assetid: eb42da6d-8d2c-43fd-986b-e73e2b004885
ms.openlocfilehash: 8b311052d3a3525090d954c0dc8cee20e985b1b4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62282137"
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