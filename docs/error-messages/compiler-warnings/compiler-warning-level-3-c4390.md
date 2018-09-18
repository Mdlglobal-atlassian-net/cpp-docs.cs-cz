---
title: Upozornění (úroveň 3) C4390 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4390
dev_langs:
- C++
helpviewer_keywords:
- C4390
ms.assetid: c95c2f1b-9bce-4b1f-a80c-565d4cde0b1e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 83131119e360bcf8193c2d6c8ca5a3cd09341516
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46054184"
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