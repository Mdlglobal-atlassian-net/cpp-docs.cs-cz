---
title: Chyba kompilátoru C3285 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3285
dev_langs:
- C++
helpviewer_keywords:
- C3285
ms.assetid: 04e8f210-d67e-4810-b153-e1efe2986c8f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 685d83f224cc0b6c259a2fdf6946f28d909a1e6b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46049563"
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