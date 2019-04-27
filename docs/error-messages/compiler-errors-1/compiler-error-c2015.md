---
title: Chyba kompilátoru C2015
ms.date: 11/04/2016
f1_keywords:
- C2015
helpviewer_keywords:
- C2015
ms.assetid: 8f40af0a-3a5a-4d6a-8ed7-125966e6bfed
ms.openlocfilehash: d761dfde26cce9c99ccd4c3e6fd86ae1d6e16ddc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62351089"
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