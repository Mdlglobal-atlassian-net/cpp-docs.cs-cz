---
title: Upozornění (úroveň 4) C4100 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4100
dev_langs:
- C++
helpviewer_keywords:
- C4100
ms.assetid: 478ed97d-e502-49e4-9afb-ac2a6c61194b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a6ad1b8bab287f4c16b00781e90351bbb204aa91
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46099460"
---
# <a name="compiler-warning-level-4-c4100"></a>Kompilátor upozornění (úroveň 4) C4100

'identifier': formální parametr nevolaný odkazem

Formální parametr se neodkazuje v těle funkce. Neodkazovaný parametr je ignorován.

C4100 může také vydat, když kód volá destruktor na jinak neodkazovaném parametru primitivního typu.  Jedná se omezení kompilátoru jazyka Visual C++.

Následující ukázka generuje upozornění C4100:

```
// C4100.cpp
// compile with: /W4
void func(int i) {   // C4100, delete the unreferenced parameter to
                     //resolve the warning
   // i;   // or, add a reference like this
}

int main()
{
   func(1);
}
```