---
title: Chyba kompilátoru C2474
ms.date: 11/04/2016
f1_keywords:
- C2474
helpviewer_keywords:
- C2474
ms.assetid: 64e6c61e-6e77-480e-bcf0-b30a2fc482ac
ms.openlocfilehash: ed2ba0d80ffcf2ef83abd551026bc6df4939ffbd
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74743728"
---
# <a name="compiler-error-c2474"></a>Chyba kompilátoru C2474

' klíčové slovo ': chybí sousední středník, může být buď klíčové slovo, nebo identifikátor.

Kompilátor očekával, že najde středník a nemohl určit svůj záměr. Chcete-li tuto chybu vyřešit, přidejte středník.

## <a name="example"></a>Příklad

Následující ukázka generuje C2474.

```cpp
// C2474.cpp
// compile with: /clr /c

ref class A {
   ref class B {}
   property int i;   // C2474 error
};

// OK
ref class B {
   ref class D {};
   property int i;
};

ref class E {
   ref class F {} property;
   int i;
};
```
