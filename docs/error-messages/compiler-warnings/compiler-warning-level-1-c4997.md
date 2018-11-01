---
title: Kompilátor upozornění (úroveň 1) C4997
ms.date: 11/04/2016
f1_keywords:
- C4997
helpviewer_keywords:
- C4997
ms.assetid: d39678fd-0c1a-4104-8a45-9e3f20de0407
ms.openlocfilehash: 298653e7ebed272db1baa11514ac5bff27944b3c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50564174"
---
# <a name="compiler-warning-level-1-c4997"></a>Kompilátor upozornění (úroveň 1) C4997

'class': Konstrukt coclass neimplementuje rozhraní modelu COM nebo pseudo rozhraní

Třída označena [coclass](../../windows/coclass.md) atribut neimplementovala rozhraní.

Následující ukázka generuje C4997:

```
// C4997.cpp
// compile with: /WX
// to resolve this C4997, uncomment all code
#include <objbase.h>

[ object ]
__interface I {
   HRESULT func();
};

[ coclass ]
struct C /*: I*/ {
   /*
   HRESULT func() {
      return S_OK;
   }
   */
};   // C4997
```