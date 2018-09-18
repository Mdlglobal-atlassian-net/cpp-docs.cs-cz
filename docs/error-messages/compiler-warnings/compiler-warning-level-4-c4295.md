---
title: Upozornění (úroveň 4) C4295 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 1/09/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4295
dev_langs:
- C++
helpviewer_keywords:
- C4295
ms.assetid: 20dbff85-9f62-4ca3-8fe9-079d4512006d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 36c6ac4d8c3e2899b744d1c456ae3079ec031698
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46053573"
---
# <a name="compiler-warning-level-4-c4295"></a>Kompilátor upozornění (úroveň 4) C4295

> "*pole*': pole je příliš malá, aby zahrnují ukončujícího znaku null

Pole byl inicializován, ale poslední znak v poli není null; přístup k poli jako řetězec může vést k neočekávaným výsledkům.

## <a name="example"></a>Příklad

Následující ukázka generuje C4295. Chcete-li vyřešit tento problém, můžete deklarovat velikost pole pro uchování větší ukončujícího znaku null z inicializátoru řetězec, nebo můžete použít seznam inicializátorů pole aby záměru vymazat, že je to pole `char`, není řetězec zakončený hodnotou null.

```C
// C4295.c
// compile with: /W4


int main() {
   char a[3] = "abc";           // C4295
   char b[3] = {'d', 'e', 'f'}; // No warning
   a[0] = b[2];
}
```
