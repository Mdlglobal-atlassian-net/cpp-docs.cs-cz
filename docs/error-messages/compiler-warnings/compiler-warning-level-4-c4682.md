---
title: Kompilátor upozornění (úroveň 4) C4682
ms.date: 11/04/2016
f1_keywords:
- C4682
helpviewer_keywords:
- C4682
ms.assetid: 858ea157-1244-4a61-85df-97b3de43d418
ms.openlocfilehash: 6566c27999f218b7a214e32dde96bd1cf96fbb12
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50653060"
---
# <a name="compiler-warning-level-4-c4682"></a>Kompilátor upozornění (úroveň 4) C4682

"parametr": žádný parametr směrového atributu zadán, výchozí [v]

Metoda na parametr s atributy rozhraní nemá jeden směrové atributy: [v](../../windows/in-cpp.md) nebo [si](../../windows/out-cpp.md). Parametr výchozí hodnotu v.

Toto upozornění je vypnuto ve výchozím nastavení. Zobrazit [kompilátoru upozornění, že je vypnuto ve výchozím nastavení](../../preprocessor/compiler-warnings-that-are-off-by-default.md) Další informace.

Následující ukázka generuje C4682:

```
// C4682.cpp
// compile with: /W4
#pragma warning(default : 4682)
#include <windows.h>
[module(name="MyModule")];

[ library_block, object, uuid("c54ad59d-d516-41dd-9acd-afda17565c2b") ]
__interface IMyIface : IUnknown
{
   HRESULT f1(int i, int *pi); // C4682
   // try the following line
   // HRESULT f1([in] int i, [in] int *pi);
};

int main()
{
}
```