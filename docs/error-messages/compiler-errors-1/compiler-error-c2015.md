---
title: Chyba kompilátoru C2015 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2015
dev_langs:
- C++
helpviewer_keywords:
- C2015
ms.assetid: 8f40af0a-3a5a-4d6a-8ed7-125966e6bfed
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5fb9c3ba86224906f749088b96e5daae364d99e2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46076044"
---
# <a name="compiler-error-c2015"></a>Chyba kompilátoru C2015

příliš mnoho znaků – konstanta

Znaková konstanta obsahuje více než dva znaky. Limit je jeden znak pro standardní znakové konstanty a dva znaky dlouhý znakové konstanty.

Sekvence escape, jako je například \t, je převedena na jeden znak.

## <a name="example"></a>Příklad

Následující ukázka generuje C2015:

```
// C2015.cpp
// compile with: /c

char test1 = 'error';   // C2015
char test2 = 'e';   // OK
```

## <a name="example"></a>Příklad

C2015 může vzniknout také při použití rozšíření společnosti Microsoft, znakové konstanty převést na celá čísla.  Následující ukázka generuje C2015:

```
// C2015b.cpp
#include <stdio.h>

int main()
{
    int a = 'abcde';   // C2015

    int b = 'a';   // 'a' = ascii 0x61
    printf_s("%x\n", b);
}
```