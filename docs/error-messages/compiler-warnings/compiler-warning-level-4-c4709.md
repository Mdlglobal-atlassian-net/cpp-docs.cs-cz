---
title: Kompilátor upozornění (úroveň 4) C4709
ms.date: 11/04/2016
f1_keywords:
- C4709
helpviewer_keywords:
- C4709
ms.assetid: 8abfdd45-8c70-4c27-b0fb-ca0c3f0fccf9
ms.openlocfilehash: acc74f55a423f1cd18d385cd4dfbec7dfa01c422
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50536103"
---
# <a name="compiler-warning-level-4-c4709"></a>Kompilátor upozornění (úroveň 4) C4709

operátor čárka v rámci výrazu indexu pole

V případě čárku ve výrazu indexu pole kompilátor používá hodnotu za poslední čárkou.

## <a name="example"></a>Příklad

Následující ukázka generuje C4709:

```
// C4709.cpp
// compile with: /W4
#include <stdio.h>

int main()
{
    int arr[2][2];
    arr[0][0] = 10;
    arr[0][1] = 11;

    // Prints 10, not 11
    printf_s("\n%d",arr[0][1,0]);   // C4709
}
```