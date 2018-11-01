---
title: Kompilátor upozornění (úroveň 1) C4624
ms.date: 11/04/2016
f1_keywords:
- C4624
helpviewer_keywords:
- C4624
ms.assetid: 14f61769-d92e-482b-9515-debd87b30a66
ms.openlocfilehash: b1a7d715057f4c6d8ada104ad07f6ad0b9c52fb2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50564632"
---
# <a name="compiler-warning-level-1-c4624"></a>Kompilátor upozornění (úroveň 1) C4624

'derived class': destruktor byl implicitně definovaný jako odstranit, protože destruktor základní třídy je nedostupné nebo odstraněné

Destruktor nebyla přístupná nebo odstraněné v základní třídě a proto se nevygeneroval pro odvozenou třídu. Jakýkoliv pokus o vytvoření objektu tohoto typu v zásobníku způsobí chybu kompilátoru.

Následující ukázka generuje C4624 a ukazuje, jak ho opravit:

```
// C4624.cpp
// compile with: /W1 /c
class B {
// Uncomment the following line to fix.
// public:
   ~B();
};

class D : public B {};   // C4624 B's destructor not public
```