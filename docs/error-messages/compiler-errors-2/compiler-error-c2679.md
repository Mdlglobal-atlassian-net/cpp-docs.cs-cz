---
title: Chyba kompilátoru C2679
ms.date: 11/04/2016
f1_keywords:
- C2679
helpviewer_keywords:
- C2679
ms.assetid: 1a5f9d00-9190-4aa6-bc72-949f68ec136f
ms.openlocfilehash: de5613c306eb12bc11d45e868f502ca04d0a62e6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62386821"
---
# <a name="compiler-error-c2679"></a>Chyba kompilátoru C2679

binární 'operátor': nenašel se žádný operátor, který by zpracovával pravý operand typu 'type' (nebo neexistuje žádný přijatelný převod)

Chcete-li operátor použít, je třeba jej přetížit pro daný typ nebo definovat převod na typ, pro který je operátor definován.

Následující ukázka generuje C2679:

```
// C2679.cpp
class C {
public:
   C();   // no constructor with an int argument
} c;

class D {
public:
   D(int) {}
   D(){}
} d;

int main() {
   c = 10;   // C2679
   d = 10;   // OK
}
```