---
title: Chyba kompilátoru C2013
ms.date: 11/04/2016
f1_keywords:
- C2013
helpviewer_keywords:
- C2013
ms.assetid: 6b5c955c-53da-48ee-8533-64ef5b905173
ms.openlocfilehash: 3dd8c315351ccf38989fc113e7ee31b25e38a07f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757407"
---
# <a name="compiler-error-c2013"></a>Chyba kompilátoru C2013

chybí ' > '

Direktivě `#include` chybí uzavírací lomená závorka. Chcete-li chybu vyřešit, přidejte pravou závorku.

Následující ukázka generuje C2013:

```cpp
// C2013.cpp
#include <stdio.h    // C2013
```

Možné řešení:

```cpp
// C2013b.cpp
// compile with: /c
#include <stdio.h>
```
