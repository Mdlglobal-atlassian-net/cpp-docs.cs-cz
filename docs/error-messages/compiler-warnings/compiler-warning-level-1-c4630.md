---
title: Upozornění (úroveň 1) C4630 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4630
dev_langs:
- C++
helpviewer_keywords:
- C4630
ms.assetid: d8926376-7acc-4fc7-8438-6f0de3468870
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dadfd4cd38d1b1d0e67e49e81102135a8ced1d00
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46054724"
---
# <a name="compiler-warning-level-1-c4630"></a>Kompilátor upozornění (úroveň 1) C4630

'symbol': specifikátor třídy úložiště "extern" není platný pro definici členu

Datový člen nebo členskou funkci je definován jako `extern`. Členové nemohou být externím, i když můžete celé objekty. Kompilátor ignoruje `extern` – klíčové slovo. Následující ukázka generuje C4630:

```
// C4630.cpp
// compile with: /W1 /LD
class A {
   void func();
};

extern void A::func() {   // C4630, remove 'extern' to resolve
}
```