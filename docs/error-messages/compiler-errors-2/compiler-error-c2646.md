---
title: Chyba kompilátoru C2646
ms.date: 11/04/2016
f1_keywords:
- C2646
helpviewer_keywords:
- C2646
ms.assetid: 92ff1f02-5eaf-40a5-8b7a-a682f149e967
ms.openlocfilehash: c02d7216df42681ae2ec733ae932d22861c1f0ee
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50572001"
---
# <a name="compiler-error-c2646"></a>Chyba kompilátoru C2646

anonymní struktury nebo sjednocení v globálním nebo rozsahu oboru názvů musí být deklarované jako statické.

Anonymní struktury nebo sjednocení měly globální nebo obor názvů ale není deklarována `static`.

Následující ukázka generuje C2646 a ukazuje, jak ho opravit:

```
// C2646.cpp
// compile with: /c
union { int i; };   // C2646 not static

// OK
static union { int j; };
union U { int i; };
```