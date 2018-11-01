---
title: Chyba kompilátoru C2312
ms.date: 11/04/2016
f1_keywords:
- C2312
helpviewer_keywords:
- C2312
ms.assetid: c8bcfd06-12c1-4323-bb53-ba392d36daa4
ms.openlocfilehash: 2c8d360be43c46b1a26c833dbb8aa95a7e3740e6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50478777"
---
# <a name="compiler-error-c2312"></a>Chyba kompilátoru C2312

'exception1': se zachycuje prostřednictvím "exception2' na řádku číslo

Dvě obslužné rutiny catch stejný typ výjimky.

Následující ukázka generuje C2312:

```
// C2312.cpp
// compile with: /EHsc
#include <eh.h>
int main() {
    try {
        throw "ooops!";
    }
    catch( signed int ) {}
    catch( int ) {}   // C2312
}
```