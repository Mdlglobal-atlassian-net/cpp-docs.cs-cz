---
title: Upozornění kompilátoru (úroveň 1) C4624
ms.date: 11/04/2016
f1_keywords:
- C4624
helpviewer_keywords:
- C4624
ms.assetid: 14f61769-d92e-482b-9515-debd87b30a66
ms.openlocfilehash: 8ef871f31d5d1d31e6d1d26d46b6f7f99c8fba86
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/13/2019
ms.locfileid: "74051454"
---
# <a name="compiler-warning-level-1-c4624"></a>Upozornění kompilátoru (úroveň 1) C4624

' odvozené třídy ': destruktor byl implicitně definován jako odstraněný, protože destruktor základní třídy je nepřístupný nebo odstraněný.

Destruktor nebyl přístupný nebo odstraněn v základní třídě, a proto nebyl vygenerován pro odvozenou třídu. Jakékoli pokus o vytvoření objektu tohoto typu v zásobníku způsobí chybu kompilátoru.

Následující ukázka generuje C4624 a ukazuje, jak ji opravit:

```cpp
// C4624.cpp
// compile with: /W1 /c
class B {
// Uncomment the following line to fix.
// public:
   ~B();
};

class D : public B {};   // C4624 B's destructor not public
```