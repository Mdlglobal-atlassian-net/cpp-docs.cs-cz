---
title: Chyba kompilátoru C2013
ms.date: 11/04/2016
f1_keywords:
- C2013
helpviewer_keywords:
- C2013
ms.assetid: 6b5c955c-53da-48ee-8533-64ef5b905173
ms.openlocfilehash: b279202b8b32197a99d230040207aa50bc100495
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62351128"
---
# <a name="compiler-error-c2013"></a>Chyba kompilátoru C2013

Chybí ">"

`#include` Direktivu chybí ukončovací lomená závorka. Přidejte pravou hranatou závorku tuto chybu napravíme.

Následující ukázka generuje C2013:

```
// C2013.cpp
#include <stdio.h    // C2013
```

Možná řešení:

```
// C2013b.cpp
// compile with: /c
#include <stdio.h>
```