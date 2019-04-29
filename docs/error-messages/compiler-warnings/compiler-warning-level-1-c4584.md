---
title: Kompilátor upozornění (úroveň 1) C4584
ms.date: 11/04/2016
f1_keywords:
- C4584
helpviewer_keywords:
- C4584
ms.assetid: ad86582f-cb8c-4d21-8c4c-a6c800059e25
ms.openlocfilehash: 3c60575e766ea3490a40711fe26c3e402c41fbdd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62397247"
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