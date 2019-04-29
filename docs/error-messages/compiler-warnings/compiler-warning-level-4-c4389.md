---
title: Kompilátor upozornění (úroveň 4) C4389
ms.date: 11/04/2016
f1_keywords:
- c4389
helpviewer_keywords:
- C4389
ms.assetid: fc0e3a8e-f766-437c-b7f1-e61abb2a8765
ms.openlocfilehash: 7490218c0af61ef3b2346fc1bee9806d87d02294
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62391579"
---
# <a name="compiler-warning-level-4-c4389"></a>Kompilátor upozornění (úroveň 4) C4389

'operator': podepsané/unsigned – neshoda

Operace týká proměnné se znaménkem a bez znaménka. To může mít za následek ztrátu dat.

Následující ukázka generuje C4389:

```
// C4389.cpp
// compile with: /W4
#pragma warning(default: 4389)

int main()
{
   int a = 9;
   unsigned int b = 10;
   if (a == b)   // C4389
      return 0;
   else
      return 0;
};
```