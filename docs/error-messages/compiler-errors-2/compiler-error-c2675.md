---
title: Chyba kompilátoru C2675
ms.date: 11/04/2016
f1_keywords:
- C2675
helpviewer_keywords:
- C2675
ms.assetid: 4b92a12b-bff8-4dd5-a109-620065fc146c
ms.openlocfilehash: 0b7b81ce7314fbad02d6873403fc5cf1bdd54709
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760371"
---
# <a name="compiler-error-c2675"></a>Chyba kompilátoru C2675

Unární operátor: Type nedefinuje Tento operátor nebo převod na typ přijatelný pro předdefinovaný operátor.

K C2675 může také dojít při použití unárního operátoru a typ nedefinuje operátor nebo převod na typ přijatelný pro předdefinovaný operátor. Chcete-li operátor použít, je třeba jej přetížit pro daný typ nebo definovat převod na typ, pro který je operátor definován.

## <a name="example"></a>Příklad

Následující ukázka generuje C2675.

```cpp
// C2675.cpp
struct C {
   C(){}
} c;

struct D {
   D(){}
   void operator-(){}
} d;

int main() {
   -c;   // C2675
   -d;   // OK
}
```
