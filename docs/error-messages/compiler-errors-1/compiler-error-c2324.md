---
title: Chyba kompilátoru C2324
ms.date: 11/04/2016
f1_keywords:
- C2324
helpviewer_keywords:
- C2324
ms.assetid: 215f0544-85b0-452d-825f-17a388b6a61c
ms.openlocfilehash: 694d1b2c9df4830e721af51517044e9734fcf415
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50449826"
---
# <a name="compiler-error-c2324"></a>Chyba kompilátoru C2324

'identifier': neočekávalo se napravo "name"

Destruktoru je volána pomocí nesprávný identifikátor.

Následující ukázka generuje C2324:

```
// C2324.cpp
class A {};
typedef A* pA_t;
int i;

int main() {
   pA_t * ppa = new pA_t;
   ppa->~i;   // C2324
   ppa->~pA_t();   // OK
}
```