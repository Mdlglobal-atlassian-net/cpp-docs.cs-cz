---
title: Upozornění (úroveň 1) C4822 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4822
dev_langs:
- C++
helpviewer_keywords:
- C4822
ms.assetid: 0f231a30-2eb0-4722-aaa0-e2d19d3e7eea
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 33748a39eae4b6f2a84cadb818570f9a311b1fe1
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46078319"
---
# <a name="compiler-warning-level-1-c4822"></a>Kompilátor upozornění (úroveň 1) C4822

'member': členská funkce lokální třídy nemá tělo.

Členská funkce lokální třídy byla deklarována, ale není definovaný ve třídě. Pokud chcete použít členská funkce lokální třídy, musí být definovat ve třídě. Nelze deklarovat v třídě a definování mimo třídy.

Všechny definice mimo třídu pro členská funkce lokální třídy bude k chybě.

Následující ukázka generuje C4822:

```
// C4822.cpp
// compile with: /W1
int main() {
   struct C {
      void func1(int);   // C4822
      // try the following line instead
      // void func1(int){}
  };
}
```