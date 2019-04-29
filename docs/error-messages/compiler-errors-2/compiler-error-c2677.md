---
title: Chyba kompilátoru C2677
ms.date: 11/04/2016
f1_keywords:
- C2677
helpviewer_keywords:
- C2677
ms.assetid: 76bc0b65-f52a-45a6-b6d6-0555f89da9a8
ms.openlocfilehash: 1be3701c2befbacc11d6a3dea4b99547375286d5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62395414"
---
# <a name="compiler-error-c2677"></a>Chyba kompilátoru C2677

binární 'operátor': nenašel se žádný globální operátor desetinný na typ 'type' (nebo neexistuje žádný přijatelný převod)

Chcete-li operátor použít, je třeba jej přetížit pro daný typ nebo definovat převod na typ, pro který je operátor definován.

Následující ukázka generuje C2677:

```
// C2677.cpp
class C {
public:
   C(){}
} c;

class D {
public:
   D(){}
   operator int(){return 0;}
} d;

int main() {
   int i = 1 >> c;   // C2677
   int j = 1 >> d;   // OK operator int() defined
}
```