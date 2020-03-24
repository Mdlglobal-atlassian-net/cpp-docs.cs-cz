---
title: Upozornění kompilátoru (úroveň 1) C4353
ms.date: 11/04/2016
f1_keywords:
- C4353
helpviewer_keywords:
- C4353
ms.assetid: 6e79f186-ed82-4c95-9923-0ad5bb9c4db1
ms.openlocfilehash: 9c91a3d21a16cc8891d6f04db49c3a0f0ec26e2c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187190"
---
# <a name="compiler-warning-level-1-c4353"></a>Upozornění kompilátoru (úroveň 1) C4353

používá se nestandardní rozšíření: konstantní 0 jako výraz funkce. Místo toho použijte vnitřní funkci funkce __noop.

Jako výraz funkce nelze použít konstantu Zero (0). Další informace najdete v tématu [__noop](../../intrinsics/noop.md).

Následující ukázka generuje C4353:

```cpp
// C4353.cpp
// compile with: /W1
void MyPrintf(void){};
#define X 0
#if X
   #define DBPRINT MyPrint
#else
   #define DBPRINT 0   // C4353 expected
#endif
int main(){
DBPRINT();
}
```
