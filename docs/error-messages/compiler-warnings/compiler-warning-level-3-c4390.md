---
title: Kompilátor upozornění (úroveň 3) C4390
ms.date: 11/04/2016
f1_keywords:
- C4390
helpviewer_keywords:
- C4390
ms.assetid: c95c2f1b-9bce-4b1f-a80c-565d4cde0b1e
ms.openlocfilehash: 4ca00f892adc8fe3ac1bffb59a27ea1744249dea
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401979"
---
# <a name="compiler-warning-level-3-c4390"></a>Kompilátor upozornění (úroveň 3) C4390

";': prázdný řízený příkaz nalezen. je to záměr?

Středník bylo zjištěno, po příkazu ovládacího prvku, který neobsahuje žádné instrukce.

Pokud získáte C4390 kvůli makra, měli byste použít [upozornění](../../preprocessor/warning.md) direktivy pragma zakážete C4390 v modulu, který obsahuje makra.

Následující ukázka generuje C4390:

```
// C4390.cpp
// compile with: /W3
int main() {
   int i = 0;
   if (i);   // C4390
      i++;
}
```