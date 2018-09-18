---
title: Upozornění (úroveň 1) C4584 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4584
dev_langs:
- C++
helpviewer_keywords:
- C4584
ms.assetid: ad86582f-cb8c-4d21-8c4c-a6c800059e25
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9db97bf35034f7ca628f860924bfb9a1fccc942f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46036251"
---
# <a name="compiler-warning-level-1-c4584"></a>Kompilátor upozornění (úroveň 1) C4584

'class1': třídy base 'class2' se už má základní třída 'class3.

Třídy, které jste definovali dědí ze dvou tříd, z nichž jeden dědí z druhé. Příklad:

```
// C4584.cpp
// compile with: /W1 /LD
class A {
};

class B : public A {
};

class C : public A, public B { // C4584
};
```

V takovém případě by se objeví upozornění ve třídě C protože dědí i z třídy A a B, který také dědí z třídy A. Toto upozornění slouží jako připomenutí, že musí plnému využívání členy z těchto základních tříd nebo se vygeneruje Chyba kompilátoru z důvodu nejednoznačnosti, které člen třídy můžete odkazovat.