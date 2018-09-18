---
title: Upozornění (úroveň 3) C4018 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4018
dev_langs:
- C++
helpviewer_keywords:
- C4018
ms.assetid: 6e8cbb04-d914-4319-b431-cbc2fbe40eb1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 99ca94a47925a64c91077ad5b363e953def186b1
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46041321"
---
# <a name="compiler-warning-level-3-c4018"></a>Kompilátor upozornění (úroveň 3) C4018

"výraz": podepsané/unsigned – neshoda

Porovnání číslo se znaménkem a bez znaménka vyžaduje kompilátor převede hodnotu podepsaného na nepodepsané.

Toto upozornění může opravit, pokud jeden ze dvou typů přetypování při testování typy se znaménkem a bez znaménka.

Následující ukázka generuje C4018:

```
// C4018.cpp
// compile with: /W3
int main() {
   unsigned int uc = 0;
   int c = 0;
   unsigned int c2 = 0;

   if (uc < c) uc = 0;   // C4018

   // OK
   if (uc == c2) uc = 0;
}
```