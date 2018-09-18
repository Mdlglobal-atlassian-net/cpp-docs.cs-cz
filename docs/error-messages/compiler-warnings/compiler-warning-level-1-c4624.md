---
title: Upozornění (úroveň 1) C4624 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4624
dev_langs:
- C++
helpviewer_keywords:
- C4624
ms.assetid: 14f61769-d92e-482b-9515-debd87b30a66
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dbc482fe693da366a3ba3ce7e53d5e8bbf23618c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46118386"
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