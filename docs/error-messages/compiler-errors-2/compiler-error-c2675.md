---
title: Chyba kompilátoru C2675 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2675
dev_langs:
- C++
helpviewer_keywords:
- C2675
ms.assetid: 4b92a12b-bff8-4dd5-a109-620065fc146c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1772f6e88516e7c8c1498f84d180ab6c4e0e05ab
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46102397"
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