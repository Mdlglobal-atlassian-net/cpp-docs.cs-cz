---
title: Upozornění kompilátoru (úroveň 4) C4682
ms.date: 11/04/2016
f1_keywords:
- C4682
helpviewer_keywords:
- C4682
ms.assetid: 858ea157-1244-4a61-85df-97b3de43d418
ms.openlocfilehash: 6af1bf2d27c04efb58e7f1af0439ed3d16b7491a
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74990124"
---
# <a name="compiler-warning-level-4-c4682"></a>Upozornění kompilátoru (úroveň 4) C4682

' parametr ': nebyl zadán atribut směrového parametru, je použita výchozí hodnota [in]

Metoda u parametru v rozhraní s atributy nemá jeden ze směrových atributů: [in](../../windows/in-cpp.md) nebo [out](../../windows/out-cpp.md). Parametr má výchozí hodnotu v.

Toto upozornění je ve výchozím nastavení vypnuté. Další informace najdete v tématu [Upozornění kompilátoru, která jsou ve výchozím nastavení vypnutá](../../preprocessor/compiler-warnings-that-are-off-by-default.md) .

Následující ukázka generuje C4682:

```cpp
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
