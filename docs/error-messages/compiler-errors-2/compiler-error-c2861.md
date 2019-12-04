---
title: Chyba kompilátoru C2861
ms.date: 11/04/2016
f1_keywords:
- C2861
helpviewer_keywords:
- C2861
ms.assetid: 012bb44d-6c9b-4def-b54e-b19f1f8ddd1b
ms.openlocfilehash: 3d6cab186d4acf229a32620f33c9c86e807459dd
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74751986"
---
# <a name="compiler-error-c2861"></a>Chyba kompilátoru C2861

' function name ': nelze definovat členskou funkci rozhraní

Kompilátor zjistil klíčové slovo rozhraní nebo odvodit strukturu jako rozhraní, ale pak nalezl definici členské funkce.  Rozhraní nemůže obsahovat definici členské funkce.

## <a name="example"></a>Příklad

Následující ukázka generuje C2861:

```cpp
// C2861.cpp
// compile with: /c
#include <objbase.h>   // required for IUnknown definition
[ object, uuid("00000000-0000-0000-0000-000000000001") ]
__interface IMyInterface : IUnknown {
   HRESULT mf(int a);
};

HRESULT IMyInterface::mf(int a) {}   // C2861
```
