---
title: Chyba kompilátoru C2714
ms.date: 11/04/2016
f1_keywords:
- C2714
helpviewer_keywords:
- C2714
ms.assetid: 401a5a42-660c-4bad-9d63-1a2d092bc489
ms.openlocfilehash: feba363a7cd15d92bf850e8cba457ff310d15490
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50556361"
---
# <a name="compiler-error-c2714"></a>Chyba kompilátoru C2714

__alignof(void) není povolený.

Byla předána neplatná hodnota pro operátor.

Zobrazit [__alignof – operátor](../../cpp/alignof-operator.md) Další informace.

## <a name="example"></a>Příklad

Následující ukázka generuje C2714.

```
// C2714.cpp
int main() {
   return __alignof(void);   // C2714
   return __alignof(char);   // OK
}
```