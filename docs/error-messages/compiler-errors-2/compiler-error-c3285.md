---
title: Chyba kompilátoru C3285
ms.date: 11/04/2016
f1_keywords:
- C3285
helpviewer_keywords:
- C3285
ms.assetid: 04e8f210-d67e-4810-b153-e1efe2986c8f
ms.openlocfilehash: 6bc211fb2394a9a2989702c13e19bd63ea8a5ad7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50444626"
---
# <a name="compiler-error-c3285"></a>Chyba kompilátoru C3285

pro každý příkaz nejde použít pro proměnné typu 'type'

`for each` Příkaz opakuje skupinu integrovaných prohlášení pro každý prvek v poli nebo kolekci objektů.

Zobrazit [u každé v](../../dotnet/for-each-in.md) Další informace.

## <a name="example"></a>Příklad

Následující ukázka generuje C3285.

```
// C3285.cpp
// compile with: /clr
int main() {
   for each (int i in 0) {}   // C3285

   array<int> ^p = { 1, 2, 3 };
   for each (int j in p) {}   // OK
}
```