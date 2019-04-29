---
title: Kompilátor upozornění (úroveň 1) C4807
ms.date: 11/04/2016
f1_keywords:
- C4807
helpviewer_keywords:
- C4807
ms.assetid: 089c9f87-fd81-402e-9826-66a8ef1ef1fe
ms.openlocfilehash: a68596136e61aa33176365a4eff818124463b77e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62390461"
---
# <a name="compiler-warning-level-1-c4807"></a>Kompilátor upozornění (úroveň 1) C4807

'operation': potenciálně nebezpečné směšování typu 'type' a podepsaný bitového pole typu 'type'

Toto upozornění se vygeneruje, když jeden bit podepsané bitové pole k porovnání `bool` proměnné. Vzhledem k tomu, že jeden bit, podepsané bitové pole může obsahovat jenom hodnoty -1 nebo 0, je nebezpečné, kterým se má porovnat `bool`. Žádná upozornění se generují o kombinování `bool` a jeden bit, bez znaménka bitová pole vzhledem k tomu, že jsou shodné s `bool` a může obsahovat pouze 0 nebo 1.

## <a name="example"></a>Příklad

Následující ukázka generuje C4807:

```
// C4807.cpp
// compile with: /W1
typedef struct bitfield {
   signed mybit : 1;
} mybitfield;

int main() {
   mybitfield bf;
   bool b = true;

   // try..
   // int b = true;

   bf.mybit = -1;
   if (b == bf.mybit) {   // C4807
      b = false;
   }
}
```