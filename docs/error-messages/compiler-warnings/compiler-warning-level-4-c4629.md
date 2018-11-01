---
title: Kompilátor upozornění (úroveň 4) C4629
ms.date: 11/04/2016
f1_keywords:
- C4629
helpviewer_keywords:
- C4629
ms.assetid: 158cde12-bae5-4d43-b575-b52b35aaa0b9
ms.openlocfilehash: db3f4201dbf5ff925449b0924d08a43ee4283b3e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50651786"
---
# <a name="compiler-warning-level-4-c4629"></a>Kompilátor upozornění (úroveň 4) C4629

použít digraph, sekvence znaků 'digraph' interpretován jako token 'char' (vložení mezery mezi dvěma znaky. Pokud ne, co jste zamýšleli)

V části [/Za](../../build/reference/za-ze-disable-language-extensions.md), kompilátor vás upozorní, když zjistí digraph.

Následující ukázka generuje C4629:

```
// C4629.cpp
// compile with: /Za /W4
int main()
<%   // C4629 <% digraph for {
}
```