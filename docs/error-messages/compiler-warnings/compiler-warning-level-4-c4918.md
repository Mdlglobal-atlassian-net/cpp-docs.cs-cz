---
title: Kompilátor upozornění (úroveň 4) C4918
ms.date: 11/04/2016
f1_keywords:
- C4918
helpviewer_keywords:
- C4918
ms.assetid: 1bcf6d35-3467-4aa8-b2ef-cb33f4e70238
ms.openlocfilehash: 9662b561f6ce6c9f41327b267d17082b1eaa21a6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62280344"
---
# <a name="compiler-warning-level-4-c4918"></a>Kompilátor upozornění (úroveň 4) C4918

'znak': neplatný znak v seznamu optimalizací pragma

V seznamu optimalizace byl nalezen neznámý znak [optimalizovat](../../preprocessor/optimize.md) výrazu direktivy pragma.

Například následující příkaz generuje C4918:

```
// C4918.cpp
// compile with: /W4
#pragma optimize("X", on) // C4918 expected
int main()
{
}
```