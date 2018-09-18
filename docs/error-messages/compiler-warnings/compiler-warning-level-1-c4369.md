---
title: Upozornění (úroveň 1) C4369 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4369
dev_langs:
- C++
helpviewer_keywords:
- C4369
ms.assetid: ade87e84-36be-4e00-be99-2930af848feb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9c8b292717168f7f6ead676528a5b7769b7c8ec4
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46024148"
---
# <a name="compiler-warning-level-1-c4369"></a>Kompilátor upozornění (úroveň 1) C4369

'čítače výčtu': hodnota výčtu 'value' nemůže být reprezentovaná jako 'type', hodnota je "nová_hodnota"

Enumerátor vypočítal být větší než největší hodnota zadaného základního typu.  To způsobilo přetečení a kompilátor zabalená hodnota enumerátoru na nejnižší možná hodnota pro typ.

## <a name="example"></a>Příklad

Následující ukázka generuje C4369.

```
// C4369.cpp
// compile with: /W1
int main() {
   enum Color: char { red = 0x7e, green, blue };   // C4369
   enum Color2: char { red2 = 0x7d, green2, blue2};   // OK
}
```