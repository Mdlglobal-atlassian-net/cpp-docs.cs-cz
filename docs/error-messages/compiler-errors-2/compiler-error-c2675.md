---
title: Chyba kompilátoru C2675
ms.date: 11/04/2016
f1_keywords:
- C2675
helpviewer_keywords:
- C2675
ms.assetid: 4b92a12b-bff8-4dd5-a109-620065fc146c
ms.openlocfilehash: aea79509d0e1ae5c31fcf0cf369c28af39a21154
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62367925"
---
# <a name="compiler-error-c2675"></a>Chyba kompilátoru C2675

Unární 'operator': 'type' nedefinuje tento operátor nebo převod na typ přijatelný pro předdefinovaný operátor

C2675 může dojít také při použití unární operátor a typ nedefinuje operátor nebo převod na typ přijatelný pro předdefinovaný operátor. Chcete-li operátor použít, je třeba jej přetížit pro daný typ nebo definovat převod na typ, pro který je operátor definován.

## <a name="example"></a>Příklad

Následující ukázka generuje C2675.

```
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