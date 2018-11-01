---
title: Kompilátor upozornění (úroveň 1) C4186
ms.date: 11/04/2016
f1_keywords:
- C4186
helpviewer_keywords:
- C4186
ms.assetid: caf3f7d8-f305-426b-8d4e-2b96f5c269ea
ms.openlocfilehash: fa5f0c3d3d409384b7cdc3c8a9cbe884732cbf8c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50646573"
---
# <a name="compiler-warning-level-1-c4186"></a>Kompilátor upozornění (úroveň 1) C4186

\#Import atribut 'attribute' vyžaduje argumenty. počet; Ignorovat

A `#import` atributu má chybný počet argumentů.

## <a name="example"></a>Příklad

```
// C4186.cpp
// compile with: /W1 /c
#import "stdole2.tlb" no_namespace("abc") rename("a","b","c")  // C4186
```

`no_namespace` Atribut nepřijímá žádné argumenty. **Přejmenovat** atribut má pouze dva argumenty.