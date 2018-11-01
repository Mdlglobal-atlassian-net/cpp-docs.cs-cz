---
title: Kompilátor upozornění (úroveň 1) C4075
ms.date: 11/04/2016
f1_keywords:
- C4075
helpviewer_keywords:
- C4075
ms.assetid: 19a700b6-f210-4b9d-a2f2-76cfe39ab178
ms.openlocfilehash: f739e0363cc08d31bd26b063ef13658a392398bd
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50486382"
---
# <a name="compiler-warning-level-1-c4075"></a>Kompilátor upozornění (úroveň 1) C4075

Inicializátory jsou vložené v nerozpoznané inicializační oblasti.

A [init_seg – #pragma](../../preprocessor/init-seg.md) používá název Neznámá část. Kompilátor ignoruje **– Direktiva pragma** příkazu.

Následující ukázka generuje C4075:

```
// C4075.cpp
// compile with: /W1
#pragma init_seg("mysegg")   // C4075

// try..
// #pragma init_seg(user)

int main() {
}
```