---
title: Chyba kompilátoru C2015
ms.date: 11/04/2016
f1_keywords:
- C2015
helpviewer_keywords:
- C2015
ms.assetid: 8f40af0a-3a5a-4d6a-8ed7-125966e6bfed
ms.openlocfilehash: 83b78336d74037b9f9f52da8327479f506db1ffc
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74751065"
---
# <a name="compiler-error-c2015"></a>Chyba kompilátoru C2015

příliš mnoho znaků v konstantě

Znaková konstanta obsahuje více než dva znaky. Limit je jeden znak pro standardní znakové konstanty a dva znaky pro dlouhé znakové konstanty.

Řídicí sekvence, jako je například \t, je převedena na jeden znak.

## <a name="example"></a>Příklad

Následující ukázka generuje C2015:

```cpp
// C2015.cpp
// compile with: /c

char test1 = 'error';   // C2015
char test2 = 'e';   // OK
```

## <a name="example"></a>Příklad

K C2015 může také dojít při použití rozšíření společnosti Microsoft, konstanty znaků převedené na celá čísla.  Následující ukázka generuje C2015:

```cpp
// C2015b.cpp
#include <stdio.h>

int main()
{
    int a = 'abcde';   // C2015

    int b = 'a';   // 'a' = ascii 0x61
    printf_s("%x\n", b);
}
```
