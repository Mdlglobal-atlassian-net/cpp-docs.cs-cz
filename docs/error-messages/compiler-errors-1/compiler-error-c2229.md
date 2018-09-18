---
title: Chyba kompilátoru C2229 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2229
dev_langs:
- C++
helpviewer_keywords:
- C2229
ms.assetid: 933c7cf2-a463-4e74-b0b4-59dedad987fb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b235b5fae84ba605ecec5419f9334ccfa0a4be6e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46035588"
---
# <a name="compiler-error-c2229"></a>Chyba kompilátoru C2229

Typ 'identifier' má neplatné pole nulové velikosti

Člen struktury nebo bitové pole obsahuje pole s nulovou velikostí, který není poslední člen.

Protože nemáte nulovou velikostí pole jako poslední člen struktury je nutné zadat velikost při přidělování struktury.

Pokud nulové velikosti pole není poslední člen struktury, kompilátor nemůže vypočítat posunutí pro zbývající pole.

Následující ukázka generuje C2229:

```
// C2229.cpp
struct S {
   int a[0];  // C2229  zero-sized array
   int b[1];
};

struct S2 {
   int a;
   int b[0];
};

int main() {
   // allocate 7 elements for b field
   S2* s2 = (S2*)new int[sizeof(S2) + 7*sizeof(int)];
   s2->b[6] = 100;
}
```